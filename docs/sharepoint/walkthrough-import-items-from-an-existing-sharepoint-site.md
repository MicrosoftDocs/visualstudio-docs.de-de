---
title: 'Exemplarische Vorgehensweise: Importieren von Elementen aus einer vorhandenen SharePoint-Website | Microsoft-Dokumentation'
titleSuffix: ''
description: In dieser exemplarischen Vorgehensweise importieren Sie Elemente aus einer vorhandenen SharePoint-Website in ein Visual Studio SharePoint-Projekt.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7eeff880538d98f997f48f82c49d01045e834031
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970119"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Exemplarische Vorgehensweise: Importieren von Elementen aus einer vorhandenen SharePoint-Website
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Elemente aus einer vorhandenen SharePoint-Website in ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekt importiert werden.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Anpassen einer SharePoint-Website durch Hinzufügen einer benutzerdefinierten Website Spalte (auch als *Feld* bezeichnet).

- Exportieren einer SharePoint-Website in eine wsp-Datei.

- Importieren der wsp-Datei in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint mithilfe des. wsp-Import Projekts.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.

- Visual Studio.

## <a name="customize-a-sharepoint-site"></a>Anpassen einer SharePoint-Website
 In diesem Beispiel erstellen Sie eine SharePoint-unter Website und passen Sie an, indem Sie Ihr eine neue Website Spalte hinzufügen, und Sie erstellen eine weitere unter Website für die spätere Verwendung. Später exportieren Sie die erste unter Website in eine wsp-Datei und importieren dann die benutzerdefinierte Website Spalte mithilfe des WSP-Import Projekts in die zweite unter Website.

### <a name="to-create-and-customize-a-sharepoint-site"></a>So erstellen Sie eine SharePoint-Website und passen diese an

1. Öffnen Sie eine SharePoint-Website mithilfe eines Webbrowsers, z. b. http://<em>Systemname</em>/SitePages/Home.aspx.

2. Erstellen Sie eine unter Website außerhalb der SharePoint-Hauptwebsite, indem Sie das Menü **Website Aktionen** öffnen und dann **neue Website** auswählen.

3. Wählen Sie im Dialogfeld **Erstellen** des Standorts den **leeren** Standorttyp aus.

4. Geben Sie im Feld **Titel den Text** **Site Column Test 1; ein**. Geben Sie im Feld **URL** -Name **columntest1** ein. überlassen Sie die anderen Einstellungen auf die Standardwerte. und klicken Sie dann auf die Schaltfläche **Erstellen** .

5. Nachdem der Standort erstellt wurde, navigieren Sie im Browser zurück zum Hauptstandort http://<em>Systemname</em>/SitePages/Home.aspx.

6. Erstellen Sie erneut eine leere unter Website außerhalb der SharePoint-Hauptwebsite, indem Sie das Menü **Website Aktionen** öffnen, **neue Website** auswählen und dann den **leeren** Standorttyp auswählen.

7. Geben Sie im Feld **Titel den Text** **Site Column Test 2**; ein. Geben Sie im Feld **URL** -Name **columntest2** ein. überlassen Sie die anderen Einstellungen auf die Standardwerte. und klicken Sie dann auf die Schaltfläche **Erstellen** .

8. Navigieren Sie zurück zur ersten unter Website http://<em>Systemname</em>/columntest1/default.aspx.

9. Klicken Sie im Menü **Website Aktionen** auf **Website Einstellungen** , um die Seite Site Einstellungen anzuzeigen.

10. Wählen Sie im Abschnitt **Galerien** den Link **Site Columns** aus.

11. Wählen Sie oben auf der Seite " **Site Column Gallery** " die Schaltfläche **Erstellen** aus.

12. Geben Sie im Feld **Spaltenname** die Option **Test Spalte** ein, behalten Sie die anderen Standardwerte bei, und klicken Sie dann auf die Schaltfläche **OK** .

13. Die Spalte **Test Spalte** wird unter der Überschrift benutzerdefinierte Spalten in der Site Column Gallery angezeigt.

## <a name="exporting-the-sharepoint-site"></a>Exportieren der SharePoint-Website
 Rufen Sie als nächstes eine SharePoint-Setup Datei (. wsp) ab, die die SharePoint-Elemente und-Elemente enthält, die Sie in Ihr [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekt importieren möchten. Wenn Sie noch nicht über eine wsp-Datei verfügen, müssen Sie eine Datei aus einer vorhandenen SharePoint-Website erstellen. In diesem Beispiel exportieren Sie die SharePoint-Standard Website in eine wsp-Datei.

> [!IMPORTANT]
> Wenn Sie mit dem folgenden Verfahren einen Laufzeitfehler erhalten, müssen Sie das Verfahren in einem System ausführen, das Zugriff auf die SharePoint-Website hat.

### <a name="to-export-an-existing-sharepoint-site"></a>So exportieren Sie eine vorhandene SharePoint-Website

1. Wählen Sie auf der SharePoint-Website auf der Registerkarte **Website Aktionen** die Option **Website Einstellungen** aus, um die Seite Site Einstellungen anzuzeigen.

2. Wählen Sie auf der Seite "Site Einstellungen" im Abschnitt **Website Aktionen** den Link **Site als Vorlage speichern** aus.

3. Geben Sie im Feld **Dateiname den Namen** **ExampleSite** ein, und geben Sie im Feld **Vorlagen Name die Bezeichnung** **Beispiel Website** ein.

4. Lassen Sie für dieses Beispiel das Kontrollkästchen **Inhalt einschließen** deaktiviert.

     Wenn Sie dieses Kontrollkästchen aktivieren, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] speichert alle Listen und Dokument Bibliotheken sowie deren Inhalt in der wsp-Datei. Obwohl dies in einigen Fällen nützlich ist, ist es für dieses Beispiel nicht erforderlich.

5. Wenn der Vorgang erfolgreich abgeschlossen wurde, klicken Sie auf den Link **Solution Gallery** , um die wsp-Datei anzuzeigen.

     Um die Lösungs Galerieseite zu einem späteren Zeitpunkt anzuzeigen, öffnen Sie das Menü **Website Aktionen** , wählen Sie **Website Einstellungen** aus, klicken Sie im Abschnitt **Website Sammlungsverwaltung** auf den Link **zum Standort der obersten Ebene** , und wählen Sie dann im Abschnitt **Galerien** den Link **Lösungen** aus.

6. Wählen Sie in der Lösungs Galerie den Link **ExampleSite** aus.

7. Wählen Sie im Dialogfeld **Datei Download** die Schaltfläche **Speichern** aus, um die Datei standardmäßig in Ihrem Downloadordner auf Ihrem lokalen System zu speichern.

## <a name="import-the-wsp-file"></a>Importieren der wsp-Datei
 Nun, da Sie über eine *wsp* -Datei verfügen, die ein Element enthält, das Sie wieder verwenden möchten (die Test Spalte für benutzerdefinierte Websites), importieren Sie die *wsp* -Datei, um darauf zuzugreifen.

### <a name="to-import-a-wsp-file"></a>So importieren Sie eine wsp-Datei

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Wählen Sie in in der Menüleiste **Datei**  >  **neu**  >  **Projekt** aus, um das Dialogfeld **Neues Projekt** anzuzeigen. Wenn die IDE für die Verwendung Visual Basic Entwicklungseinstellungen festgelegt ist, wählen Sie in der Menüleiste **Datei**  >  **neu Projekt** aus.

2. Erweitern Sie den **SharePoint** -Knoten entweder unter **Visual c#** oder **Visual Basic**, und wählen Sie dann den Knoten **2010** aus.

3. Wählen Sie im Bereich **Vorlagen** die Vorlage **SharePoint 2010-Lösungspaket importieren** aus, belassen Sie den Namen des Projekts als WspImportProject1, und klicken Sie dann auf die Schaltfläche **OK** .

    Der Assistent zum Anpassen von **SharePoint** wird angezeigt.

4. Geben Sie auf der Seite **Geben Sie die Website und die Sicherheitsstufe für das Debugging** an den [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] für die zweite SharePoint-unter Website ein, die Sie zuvor erstellt haben. Sie fügen das neue benutzerdefinierte Feld Element http://<em>Systemname</em>/columntest2 zu dieser unter Website hinzu.

5. Belassen Sie im Abschnitt **Was ist die Vertrauens Ebene für diese SharePoint-Lösung?** die Auswahl als **Sandkasten Lösung** bereitstellen.

6. Navigieren Sie auf der Seite **neue Projekt Quelle angeben** zum Speicherort auf dem System, in dem Sie die *wsp* -Datei zuvor gespeichert haben, und klicken Sie dann auf die Schaltfläche **weiter** .

   > [!NOTE]
   > Wenn Sie auf dieser Seite die Schaltfläche **Fertig** stellen auswählen, werden alle verfügbaren Elemente in der *wsp* -Datei importiert.

7. Deaktivieren Sie im Feld **zu importierende Elemente auswählen** alle Kontrollkästchen in der Liste mit Ausnahme von **Test Spalte**, und wählen Sie dann die Schaltfläche **Fertig** stellen aus.

    Da die Liste viele Elemente enthält, können Sie die Tastenkombination **STRG** + **A** drücken, um alle Elemente in der Liste auszuwählen. Wählen Sie die Leertaste aus, um alle Kontrollkästchen zu deaktivieren, und aktivieren Sie dann nur das Kontrollkästchen neben dem Element **Test Spalte** .

    Nachdem der Import Vorgang abgeschlossen ist, wird ein neues Projekt mit dem Namen **WspImportProject1** erstellt, das einen Ordner mit dem Namen **Fields** enthält. In diesem Ordner befindet sich die **Test Spalte** für benutzerdefinierte Websites und deren Definitionsdatei *Elements.xml*.

## <a name="deploy-the-project"></a>Bereitstellen des Projekts
 Stellen Sie schließlich **WspImportProject1** auf der zweiten SharePoint-unter Website bereit, die Sie zuvor erstellt haben, um die Spalte benutzerdefinierte Websites anzuzeigen.

### <a name="to-deploy-the-project"></a>So stellen Sie das Projekt bereit

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Wählen Sie in die Taste **F5** aus, um das *. wsp* -Import Projekt bereitzustellen und auszuführen.

2. Öffnen Sie auf der SharePoint-Website das Menü **Website Aktionen** , und wählen Sie dann **Website Einstellungen** aus, um die Seite Site Einstellungen anzuzeigen.

3. Wählen Sie im Abschnitt **Galerien** den Link **Site Columns** aus.

4. Scrollen Sie nach unten zum Abschnitt **benutzerdefinierte Spalten** .

     Beachten Sie, dass die benutzerdefinierte Website Spalte, die Sie von der ersten SharePoint-Website importiert haben, in der Liste angezeigt wird.

## <a name="see-also"></a>Weitere Informationen
- [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
