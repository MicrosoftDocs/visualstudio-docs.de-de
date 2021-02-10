---
title: Seite "benutzerdefinierte Master Seite & Site" mit Image importieren
description: Importieren Sie in dieser exemplarischen Vorgehensweise eine benutzerdefinierte SharePoint-Master Seite und eine Website Seite, die ein Bild in ein Visual Studio SharePoint-Projekt enthält.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 503ffc733a408787e7ecf188d893039759819c6d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952576"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Exemplarische Vorgehensweise: Importieren einer benutzerdefinierten Master Seite und Website Seite mit einem Image
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie eine benutzerdefinierte SharePoint-Master Seite und eine Website Seite mit einem Bild in ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekt importiert werden.

 In dieser exemplarischen Vorgehensweise wird erläutert, wie die folgenden Aufgaben ausgeführt werden:

- Erstellen Sie eine benutzerdefinierte Master Seite und eine Website Seite mithilfe eines Bilds in SharePoint Designer.

- Exportieren Sie eine benutzerdefinierte Master Seite, ein Bild und eine Website Seite in eine SharePoint-Lösungs Datei (*wsp*-Datei).

- Importieren Sie die *wsp* -Datei, und stellen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sie Sie in einem SharePoint-Projekt mithilfe des Projekts SharePoint-Lösungspaket importieren bereit.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Sie müssen über die folgenden Komponenten verfügen, um diese exemplarische Vorgehensweise abzuschließen:

- Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.

- Visual Studio.

- SharePoint Designer 2010.

## <a name="create-items-in-sharepoint-designer"></a>Erstellen von Elementen in SharePoint Designer
 In diesem Beispiel wird gezeigt, wie drei Elemente in SharePoint Designer für den Export erstellt werden: eine benutzerdefinierte Master Seite, eine Website Seite, die auf die benutzerdefinierte Master Seite verweist, und eine Bilddatei, die auf der Website Seite angezeigt wird. Das Bild wird dem Ordner/Images/in SharePoint hinzugefügt.

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>So erstellen Sie eine benutzerdefinierte Master Seite in SharePoint Designer

1. Wählen Sie im Navigationsbereich von SharePoint Designer das Standort Objekt **Master Seiten** aus.

2. Wählen Sie auf dem Menüband **Masterseiten** die Option **leere Master Seite** aus.

3. Wählen Sie die neue Master Seite aus, und wählen Sie dann auf dem Menüband **Masterseiten** die Option **Datei bearbeiten** aus.

4. Wählen Sie am unteren Rand von SharePoint Designer die Registerkarte **Code** aus.

5. Ersetzen Sie das vorhandene Markup durch das folgende Markup.

    ```aspx-csharp
    <%@ Master Language="C#" %>
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <html dir="ltr">
    <head runat="server">
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>
    <title>Web Page</title>
    </head>
    <body>
    <form id="form1" runat="server">
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"
            runat="server">
          </asp:ContentPlaceHolder>
    </form>
    </body>
    </html>
    ```

6. Speichern Sie die Seite, wählen Sie die Registerkarte **Masterseiten** aus, und benennen Sie die Master Seite in **mybasic1. Master** um.

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Hinzufügen eines Bilds zur Inhalts Datenbank in SharePoint Designer
 Nun können Sie ein Bild hinzufügen, das auf der Seite Website angezeigt werden soll. Das Image wird in der SharePoint-Inhalts Datenbank bereitgestellt.

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>So fügen Sie der Inhalts Datenbank in SharePoint Designer ein Bild hinzu

1. Wählen Sie im Navigationsbereich das Standort Objekt **alle Dateien** aus, und wählen Sie dann in der Strukturansicht den Ordner **Images** aus.

2. Wählen Sie im Menüband **alle Dateien** die Option **Dateien importieren** aus, wählen Sie eine Datei Ihrer Wahl aus, und klicken Sie dann auf die Schaltfläche **OK** . In diesem Beispiel hat die Datei den Namen **myimg1.png**.

     Optional können Sie einen Unterordner erstellen, um die Bilder zu organisieren.

3. Schließen Sie das Dialogfeld **importieren** .

## <a name="create-a-site-page"></a>Seite "Website erstellen"
 Diese grundlegende Website Seite verwendet die benutzerdefinierte Master Seite und zeigt das Image an, das Sie im vorherigen Schritt hinzugefügt haben.

#### <a name="to-create-a-site-page"></a>So erstellen Sie eine Website Seite

1. Wählen Sie im Navigationsbereich das Objekt **Standort Seiten** aus.

2. Wählen Sie im Menüband **Seiten** die Schaltfläche **Page** aus, wählen Sie den Typ **aspx** -Seite aus, und nennen Sie die neue Datei **mycontentpage1. aspx**.

     Optional können Sie einen Unterordner erstellen, um die Website Seiten zu organisieren.

3. Wählen Sie in der Liste Website Seiten die Option **MyContentPage1. aspx** aus, um die Eigenschaften Seite zu öffnen, und wählen Sie dann unten auf der Seite den Link **Datei bearbeiten** aus.

     Wenn eine Meldung angezeigt wird, die besagt, dass diese Seite keine Bereiche enthält, die im abgesicherten Modus bearbeitet werden können, und gefragt wird, ob Sie diese Seite im erweiterten Modus öffnen möchten, wählen Sie die Schaltfläche **Ja** aus.

4. Klicken Sie am unteren Rand der Seite auf die Schaltfläche **Code** .

5. Ersetzen Sie das vorhandene Markup durch das folgende Markup.

    ```aspx-csharp
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>
    <%@ Import Namespace="Microsoft.SharePoint" %>
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>

    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />
    </asp:Content>
    ```

6. Speichern Sie die aktualisierte Website Seite.

## <a name="export-the-items-from-sharepoint"></a>Exportieren der Elemente aus SharePoint
 Exportieren Sie die Elemente aus SharePoint in eine SharePoint-Lösungs Datei (*wsp*-Datei).

#### <a name="to-export-items-from-sharepoint-designer"></a>So exportieren Sie Elemente aus SharePoint Designer

1. Wählen Sie im Navigationsbereich von SharePoint Designer das **Team Site** Objekt aus, und wählen Sie dann auf dem Menüband **Website** die Option **als Vorlage speichern** aus.

2. Geben Sie im Dialogfeld **als Vorlage speichern** einen Dateinamen und einen Vorlagen Namen ein, aktivieren Sie das Kontrollkästchen **Inhalt einbeziehen** , und klicken Sie dann auf die Schaltfläche **OK** .

     Dadurch wird der Inhalt der Website in der *wsp* -Datei gespeichert.

3. Nachdem die Projekt Mappe exportiert wurde, wählen Sie den Link **Solution Gallery** aus, um die Liste der verfügbaren Projektmappendateien anzuzeigen.

4. Öffnen Sie das Kontextmenü für die neue *wsp* -Datei, und wählen Sie dann **Ziel speichern als** aus, um es auf dem System zu speichern.

## <a name="import-the-items-into-visual-studio"></a>Importieren der Elemente in Visual Studio
 Importieren Sie die *wsp* -Datei in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Nachdem Sie den Inhalt importiert haben, können Sie ihn anpassen, weitere Elemente hinzufügen und diese dann bereitstellen.

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>So importieren Sie Elemente aus der wsp-Datei in Visual Studio

1. Erstellen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein Projekt zum **Importieren eines SharePoint 2010-Lösungs Pakets** .

2. Aktivieren Sie auf der Seite **zu importierende Elemente auswählen** unter **Modul** in der Spalte **Typ** die Kontrollkästchen nur für die in der folgenden Tabelle aufgeführten Dateien zum Importieren.

   | Dateiname | Beschreibung |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | Die benutzerdefinierte Master Seite. |
   | images_ | Die Bilddatei im SharePoint-Dateisystem. |
   | SitePages_ | Die Seite "Site". |

3. Wählen Sie die Schaltfläche **Fertig** stellen, um die ausgewählten Elemente zu importieren.

4. Wählen Sie in **Projektmappen-Explorer** den \_ Knoten catalogsmasterpage aus \_ , und legen Sie den Wert seiner Eigenschaft **Bereitstellungs Konfliktlösung** auf **automatisch** fest.

    Dadurch wird sichergestellt, dass Bereitstellungs Konflikte automatisch aufgelöst werden.

5. Wenn die neue Master Seite den gleichen Namen wie eine vorhandene Seite hat, stellen Sie sicher, dass die vorhandene Seite weder als Standard Master Seite noch als benutzerdefinierte Master Seite in SharePoint Designer gekennzeichnet ist.

    Wenn eine vorhandene Master Seite entweder als Standard Master Seite oder als benutzerdefinierte Master Seite gekennzeichnet ist, wird ein Bereitstellungs Fehler angezeigt, der besagt, dass die Master Seite nicht gelöscht werden kann. Um dieses Problem zu vermeiden, gehen Sie wie folgt vor:

   - Wenn die vorhandene Master Seite als Standard Master Seite festgelegt ist, legen Sie vorübergehend eine andere Master Seite als Standard Master Seite fest. Nachdem Sie die Dateien in SharePoint bereitgestellt haben, legen Sie die neue Master Seite als Standard Master Seite fest.

   - Wenn die vorhandene Master Seite als benutzerdefinierte Master Seite festgelegt ist, legen Sie vorübergehend eine andere Master Seite als benutzerdefinierte Master Seite fest. Nachdem Sie die Dateien in SharePoint bereitgestellt haben, legen Sie die neue Master Seite als benutzerdefinierte Master Seite fest.

6. Wählen Sie in der Menüleiste **Erstellen** Projekt Mappe erstellen aus  >  .

7. Öffnen Sie die SharePoint-Website, um die bereitgestellten Elemente anzuzeigen.

   Eine alternative Möglichkeit zum Importieren von Dateien in und zur Bereitstellung in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint besteht darin, die Dateien in den Modulen in hinzuzufügen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)]Vorgehens [Weise: Importieren einer Master Seite oder eines Master](../sharepoint/how-to-import-a-master-page-or-theme.md) -Designs und [Verwenden von Modulen zum Einschließen von Dateien in die](../sharepoint/using-modules-to-include-files-in-the-solution.md)Projekt Mappe.

## <a name="see-also"></a>Weitere Informationen
- [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
