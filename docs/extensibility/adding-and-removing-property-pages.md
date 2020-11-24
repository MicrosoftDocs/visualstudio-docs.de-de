---
title: Hinzufügen und Entfernen von Eigenschaften Seiten | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Eigenschaften Seiten im Projekt-Designer hinzufügen und entfernen, die einen zentralisierten Speicherort zum Verwalten von Projekteigenschaften in Visual Studio bereitstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- property pages, adding
- property pages, project subtypes
- property pages, removing
ms.assetid: 34853412-ab8a-4caa-9601-7d0727b2985d
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 5bcd97b39d623a74eeebc26ae9e3c479530a1345
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597794"
---
# <a name="add-and-remove-property-pages"></a>Hinzufügen und Entfernen von Eigenschaften Seiten

Der Projekt-Designer stellt einen zentralisierten Speicherort zum Verwalten von Projekteigenschaften,-Einstellungen und-Ressourcen in bereit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Es wird als ein einzelnes Fenster in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) angezeigt und enthält eine Reihe von Bereichen auf der rechten Seite, auf die über die Registerkarten auf der linken Seite zugegriffen wird. Die Bereiche (häufig als Eigenschaften Seiten bezeichnet) im Projekt-Designer variieren je nach Projekttyp und-Sprache. Der Zugriff auf den Projekt-Designer ist über den Befehl " **Eigenschaften** " im Menü " **Projekt** " möglich.

In einem Projekt Untertyp müssen häufig zusätzliche Eigenschaften Seiten im Projekt-Designer angezeigt werden. Ebenso können einige Projekt Untertypen erfordern, dass integrierte Eigenschaften Seiten entfernt werden. Zu diesem Zweck muss der Projekt Untertyp die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> -Schnittstelle implementieren und die-Methode überschreiben <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Wenn Sie diese Methode überschreiben und `propId` einen Parameter verwenden, der einen der Werte der- <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> Enumeration enthält, können Sie Projekteigenschaften filtern, hinzufügen oder entfernen. Beispielsweise müssen Sie möglicherweise eine Seite zu den Konfigurations abhängigen Eigenschaften Seiten hinzufügen. Zu diesem Zweck müssen Sie Konfigurations abhängige Eigenschaften Seiten Filtern und dann der vorhandenen Liste eine neue Seite hinzufügen.

## <a name="add-and-remove-property-pages-in-project-designer"></a>Hinzufügen und Entfernen von Eigenschaften Seiten im Projekt-Designer

### <a name="remove-a-property-page"></a>Entfernen einer Eigenschaften Seite

1. Überschreiben `GetProperty(uint itemId, int propId, out object property)` Sie die-Methode, um Eigenschaften Seiten zu filtern und eine `clsids` Liste abzurufen.

    ```vb
    Protected Overrides int GetProperty(uint itemId, int propId, out object property)
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer
        'Use propId to filter configuration-independent property pages.
        Select Case propId
            ....
            Case CInt(Fix(__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList))
                'Get a semicolon-delimited list of clsids of the configuration-independent property pages
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))
                   Dim propertyPagesList As String = ((String)[property]).ToUpper(CultureInfo.InvariantCulture)
                'Remove the property page here
                   ....
            ....
        End Select
            ....
        Return MyBase.GetProperty(itemId, propId, [property])
    End Function

    ```

    ```csharp
    protected override int GetProperty(uint itemId, int propId, out object property)
    {
        //Use propId to filter configuration-independent property pages.
        switch (propId)
        {
            . . . .

            case (int)__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList:
                {
                    //Get a semicolon-delimited list of clsids of the configuration-independent property pages
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));
                    string propertyPagesList = ((string)property).ToUpper(CultureInfo.InvariantCulture);
                    //Remove the property page here
                    . . . .
                }
             . . . .
         }
            . . . .
        return base.GetProperty(itemId, propId, out property);
    }
    ```

2. Entfernen Sie die Seite **Buildereignisse** aus der `clsids` Liste abgerufen.

    ```vb
    Private buildEventsPageGuid As String = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}"
    Private index As Integer = propertyPagesList.IndexOf(buildEventsPageGuid)
    If index <> -1 Then
        ' GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'
        Dim index2 As Integer = index + buildEventsPageGuid.Length + 1
        If index2 >= propertyPagesList.Length Then
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(";"c)
        Else
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2)
        End If
    End If
    'New property value
    property = propertyPagesList
    ```

    ```csharp
    string buildEventsPageGuid = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}";
    int index = propertyPagesList.IndexOf(buildEventsPageGuid);
    if (index != -1)
    {
        // GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'
        int index2 = index + buildEventsPageGuid.Length + 1;
        if (index2 >= propertyPagesList.Length)
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(';');
        else
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2);
    }
    //New property value
    property = propertyPagesList;
    ```

### <a name="add-a-property-page"></a>Eigenschaften Seite hinzufügen

1. Erstellen Sie eine Eigenschaften Seite, die Sie hinzufügen möchten.

    ```vb
    Class DeployPropertyPage
            Inherits Form
            Implements Microsoft.VisualStudio.OLE.Interop.IPropertyPage
        'Summary: Return a stucture describing your property page.
        ....
        Public Sub GetPageInfo(ByVal pPageInfo As Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO())
            Dim info As PROPPAGEINFO = New PROPPAGEINFO()
            info.cb = CUInt(Marshal.SizeOf(GetType(PROPPAGEINFO)))
            info.dwHelpContext = 0
            info.pszDocString = Nothing
            info.pszHelpFile = Nothing
            info.pszTitle = "Deployment" 'Assign tab name
            info.SIZE.cx = Me.Size.Width
            info.SIZE.cy = Me.Size.Height
            If Not pPageInfo Is Nothing AndAlso pPageInfo.Length > 0 Then
                pPageInfo(0) = info
            End If
        End Sub
    End Class
    ```

    ```csharp
    class DeployPropertyPage : Form, Microsoft.VisualStudio.OLE.Interop.IPropertyPage
    {
        . . . .
        //Summary: Return a stucture describing your property page.
        public void GetPageInfo(Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO[] pPageInfo)
        {
            PROPPAGEINFO info = new PROPPAGEINFO();
            info.cb = (uint)Marshal.SizeOf(typeof(PROPPAGEINFO));
            info.dwHelpContext = 0;
            info.pszDocString = null;
            info.pszHelpFile = null;
            info.pszTitle = "Deployment";  //Assign tab name
            info.SIZE.cx = this.Size.Width;
            info.SIZE.cy = this.Size.Height;
            if (pPageInfo != null && pPageInfo.Length > 0)
                pPageInfo[0] = info;
        }
    }
    ```

2. Registrieren Sie die neue Eigenschaften Seite.

    ```vb
    <MSVSIP.ProvideObject(GetType(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)>
    ```

    ```csharp
    [MSVSIP.ProvideObject(typeof(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)]
    ```

3. Überschreiben `GetProperty(uint itemId, int propId, out object property)` Sie die-Methode zum Filtern von Eigenschaften Seiten, zum Abrufen einer `clsids` Liste und zum Hinzufügen einer neuen Eigenschaften Seite.

    ```vb
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer
        'Use propId to filter configuration-dependent property pages.
        Select Case propId
            ....
            case CInt(Fix(__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList)):
                'Get a semicolon-delimited list of clsids of the configuration-dependent property pages.
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))
                'Add the Deployment property page.
                [property] &= ";"c + GetType(DeployPropertyPage).GUID.ToString("B")
        End Select
            ....
            Return MyBase.GetProperty(itemId, propId, [property])
    End Function
    ```

    ```csharp
    protected override int GetProperty(uint itemId, int propId, out object property)
    {
        //Use propId to filter configuration-dependent property pages.
        switch (propId)
        {
            . . . .
            case (int)__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList:
                {
                    //Get a semicolon-delimited list of clsids of the configuration-dependent property pages.
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));
                    //Add the Deployment property page.
                    property += ';' + typeof(DeployPropertyPage).GUID.ToString("B");
                }
         }
            . . . .
        return base.GetProperty(itemId, propId, out property);
    }
    ```

## <a name="see-also"></a>Siehe auch

- [Projekt Untertypen](../extensibility/internals/project-subtypes.md)
