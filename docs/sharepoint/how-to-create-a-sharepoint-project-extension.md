---
title: 'Vorgehensweise: Erstellen einer SharePoint-Projekt Erweiterung | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie eine Projekt Erweiterung erstellen, damit Sie jedem SharePoint-Projekt, das in Visual Studio geöffnet ist, Funktionalität hinzufügen können.
ms.custom: SEO-VS-2020
ms.date: 04/28/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 88d2a7b411097bdf2a90ec04456bfc4419e31c30
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923339"
---
# <a name="how-to-create-a-sharepoint-project-extension"></a>Vorgehensweise: Erstellen einer SharePoint-Projekt Erweiterung
  Erstellen Sie eine Projekt Erweiterung, wenn Sie einem SharePoint-Projekt, das in Visual Studio geöffnet ist, Funktionalität hinzufügen möchten. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="to-create-a-project-extension"></a>So erstellen Sie eine Projekt Erweiterung

1. Erstellen Sie ein Klassenbibliotheksprojekt.

2. Fügen Sie Verweise auf die folgenden Assemblys hinzu:

    - Microsoft.VisualStudio.SharePoint

    - System.ComponentModel.Composition

3. Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>-Schnittstelle implementiert.

4. Fügen Sie der- <xref:System.ComponentModel.Composition.ExportAttribute> Klasse hinzu. Mit diesem Attribut kann Visual Studio Ihre Implementierung ermitteln und laden <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> . Übergeben <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Sie den Typ an den Attributkonstruktor.

5. Verwenden Sie in ihrer Implementierung der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> Methode Member des *ProjectService* -Parameters, um das Verhalten der Erweiterung zu definieren. Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> Objekt, das den Zugriff auf die in der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> Schnittstelle definierten Ereignisse ermöglicht.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie eine einfache Projekt Erweiterung erstellt wird, die den größten Teil der SharePoint-Projekt Ereignisse behandelt, die von der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> Schnittstelle definiert werden. Um den Code zu testen, erstellen Sie in ein SharePoint-Projekt, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und fügen Sie der Projekt Mappe weitere Projekte hinzu, ändern Sie die Projekt Eigenschaftswerte, oder löschen oder schließen Sie ein Projekt aus. Die Erweiterung benachrichtigt Sie über die Ereignisse, indem Nachrichten in das **Ausgabe** Fenster und **Fehlerliste** Fenster geschrieben werden.

  ```vb
    Imports Microsoft.VisualStudio.SharePoint
    Imports System.ComponentModel
    Imports System.ComponentModel.Composition

    Namespace Contoso.ExampleProjectExtension
      <Export(GetType(ISharePointProjectExtension))> _
      Class ExampleProjectExtension
        Implements ISharePointProjectExtension

        Private WithEvents projectService As ISharePointProjectService

        Public Sub Initialize(ByVal projectService As ISharePointProjectService) _
            Implements ISharePointProjectExtension.Initialize
            Me.projectService = projectService
        End Sub

        ' A project was added.
        Private Sub projectService_ProjectAdded(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectAdded
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was added: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was loaded in the IDE.
        Private Sub projectService_ProjectInitialized(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectInitialized
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being initialized: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' The name of a property was changed.
        Private Sub projectService_ProjectNameChanged(ByVal sender As Object, ByVal e As NameChangedEventArgs) _
            Handles projectService.ProjectNameChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project property value was changed.
        Private Sub ProjectPropertyChanged(ByVal sender As Object, ByVal e As PropertyChangedEventArgs) _
            Handles projectService.ProjectPropertyChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project is being removed or unloaded.
        Private Sub projectService_ProjectRemoved(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectRemoved
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was removed or unloaded.
        Private Sub projectService_ProjectDisposing(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectDisposing
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub
      End Class
    End Namespace
    ```

    ```csharp
    using Microsoft.VisualStudio.SharePoint;
    using System;
    using System.ComponentModel;
    using System.ComponentModel.Composition;

    namespace Contoso.ExampleProjectExtension
    {
      [Export(typeof(ISharePointProjectExtension))]
      internal class ExampleProjectExtension : ISharePointProjectExtension
      {
        public void Initialize(ISharePointProjectService projectService)
        {
            projectService.ProjectAdded += projectService_ProjectAdded;
            projectService.ProjectInitialized += projectService_ProjectInitialized;
            projectService.ProjectNameChanged += projectService_ProjectNameChanged;
            projectService.ProjectPropertyChanged += projectService_ProjectPropertyChanged;
            projectService.ProjectRemoved += projectService_ProjectRemoved;
            projectService.ProjectDisposing += projectService_ProjectDisposing;
        }

        // A project was added.
        void projectService_ProjectAdded(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was added: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is loaded in the IDE.
        void projectService_ProjectInitialized(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being initialized: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // The name of a project was changed.
        void projectService_ProjectNameChanged(object sender, NameChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project property value was changed.
        private void projectService_ProjectPropertyChanged(object sender, PropertyChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is being removed or unloaded.
        void projectService_ProjectRemoved(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project was removed or unloaded.
        void projectService_ProjectDisposing(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }
     }
  }
  ```

In diesem Beispiel wird der SharePoint-Projekt Dienst verwendet, um die Nachricht in das **Ausgabe** Fenster und **Fehlerliste** Fenster zu schreiben. Weitere Informationen finden Sie unter [Verwenden des SharePoint-Projekt Dienstanbieter](../sharepoint/using-the-sharepoint-project-service.md).

 Beispiele, die veranschaulichen, wie das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> -Ereignis und das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> Ereignis behandelt werden, finden Sie unter Gewusst [wie: Hinzufügen eines Kontextmenü Elements zu SharePoint-Projekten](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md) und Gewusst [wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekten](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sie ein Erweiterungspaket (VSIX) für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen
- [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md)
- [Gewusst wie: Hinzufügen eines Kontextmenü Elements zu SharePoint-Projekten](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Gewusst wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekten](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Exemplarische Vorgehensweise: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
