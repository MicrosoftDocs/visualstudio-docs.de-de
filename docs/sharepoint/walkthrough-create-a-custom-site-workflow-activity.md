---
title: 'Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Site Workflow-Aktivität | Microsoft-Dokumentation'
description: In dieser exemplarischen Vorgehensweise finden Sie Informationen zum Erstellen einer benutzerdefinierten Aktivität für einen SharePoint-Workflow auf Website Ebene mithilfe von Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f2b722ccef084286287b9825c43fa9069f64dcc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937718"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Website-Workflowaktivität
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie eine benutzerdefinierte Aktivität für einen Workflow auf Website Ebene mithilfe von erstellt wird [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . (Workflows auf Website Ebene gelten für den gesamten Standort, nicht nur für eine Liste auf der Website.) Die benutzerdefinierte Aktivität erstellt eine Sicherungs Ankündigungsliste und kopiert dann den Inhalt der Ankündigungsliste in diese.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen eines Workflows auf Website Ebene.

- Erstellen einer benutzerdefinierten Workflow Aktivität.

- Erstellen und Löschen einer SharePoint-Liste.

- Elemente werden aus einer Liste in eine andere kopiert.

- Anzeigen einer Liste auf der Schnellstartleiste.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.

- Visual Studio.

## <a name="create-a-site-workflow-custom-activity-project"></a>Erstellen eines benutzerdefinierten Site Workflow-Aktivitäts Projekts
 Erstellen Sie zunächst ein Projekt, um die benutzerdefinierte Workflow Aktivität zu speichern und zu testen.

#### <a name="to-create-a-site-workflow-custom-activity-project"></a>So erstellen Sie ein benutzerdefiniertes Website Workflow-Aktivitäts Projekt

1. Wählen Sie in der Menüleiste **Datei**  >  **neu**  >  **Projekt** aus, um das Dialogfeld **Neues Projekt** anzuzeigen.

2. Erweitern Sie den **SharePoint** -Knoten entweder unter **Visual c#** oder **Visual Basic**, und wählen Sie dann den Knoten **2010** aus.

3. Wählen Sie im Bereich **Vorlagen** die **SharePoint 2010-Projekt** Vorlage aus.

4. Geben Sie im Feld **Name den Namen** " **instancementbackup**" ein, und klicken Sie dann auf die Schaltfläche **OK** .

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt.

5. Wählen Sie auf der Seite **Standort und Sicherheitsebene für Debugging angeben** das Optionsfeld **als Farm Lösung** bereitstellen aus, und klicken Sie dann auf die Schaltfläche **Fertig** stellen, um die Vertrauens Ebene und die Standard Website zu akzeptieren.

     In diesem Schritt wird die Vertrauens Ebene für die Lösung als Farm Lösung festgelegt, die einzige verfügbare Option für Workflow Projekte.

6. Wählen Sie in **Projektmappen-Explorer** den Projekt Knoten aus, und klicken Sie dann in der Menüleiste auf **Projekt**  >  **Neues Element hinzufügen**.

7. Erweitern Sie unter **Visual c#** oder **Visual Basic** den Knoten **SharePoint** , und wählen Sie dann den Knoten **2010** aus.

8. Wählen Sie im Bereich **Vorlagen** die Vorlage **sequenzieller Workflow (nur Farm Lösung)** aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt.

9. Übernehmen Sie auf der Seite **Geben Sie den Workflow Namen für das Debuggen** an den Standardnamen ("Workflow1"). Ändern Sie den Typ der Workflow Vorlage in **Website Workflow**, und wählen Sie dann die Schaltfläche **weiter** aus.

10. Wählen Sie die Schaltfläche **Fertig** stellen, um die restlichen Standardeinstellungen zu übernehmen

## <a name="add-a-custom-workflow-activity-class"></a>Hinzufügen einer benutzerdefinierten Workflow Aktivitäts Klasse
 Als Nächstes fügen Sie dem Projekt eine Klasse hinzu, die den Code für die benutzerdefinierte Workflow Aktivität enthält.

#### <a name="to-add-a-custom-workflow-activity-class"></a>So fügen Sie eine benutzerdefinierte Workflow Aktivitäts Klasse hinzu

1. Klicken Sie in der Menüleiste auf **Projekt**  >  **Neues Element hinzufügen** , um das Dialogfeld **Neues Element hinzufügen** anzuzeigen.

2. Wählen Sie in der Strukturansicht **installierte Vorlagen** den **Code** Knoten aus, und wählen Sie dann die **Klassen** Vorlage in der Liste der Projekt Element Vorlagen aus. Verwenden Sie den Standardnamen Class1. Wählen Sie die Schaltfläche **Hinzufügen** aus.

3. Ersetzen Sie den gesamten Code in Class1 durch Folgendes:

     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]

4. Speichern Sie das Projekt, und wählen Sie dann in der Menüleiste **Build**-Projekt Mappe erstellen aus  >  .

     Class1 wird als benutzerdefinierte Aktion in der **Toolbox** auf der Registerkarte "" der " **kündigt-Sicherung** " angezeigt.

## <a name="add-the-custom-activity-to-the-site-workflow"></a>Hinzufügen der benutzerdefinierten Aktivität zum Website Workflow
 Fügen Sie als nächstes dem Workflow eine-Aktivität hinzu, die den benutzerdefinierten Code enthält.

#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>So fügen Sie dem Website Workflow eine benutzerdefinierte Aktivität hinzu

1. Öffnen Sie Workflow1 in der Entwurfs Ansicht im Workflow-Designer.

2. Ziehen Sie Class1 aus der **Toolbox** , sodass es unter der `onWorkflowActivated1` Aktivität angezeigt wird, oder öffnen Sie das Kontextmenü für Class1, wählen Sie **Kopieren** aus, öffnen Sie das Kontextmenü für die Zeile unter der `onWorkflowActivated1` Aktivität, und wählen Sie dann **Einfügen** aus.

3. Speichern Sie das Projekt.

## <a name="test-the-site-workflow-custom-activity"></a>Testen der benutzerdefinierten Aktivität "Website Workflow"
 Führen Sie als nächstes das Projekt aus, und starten Sie den Website Workflow. Die benutzerdefinierte Aktivität erstellt eine Sicherungs Ankündigungsliste und kopiert den Inhalt aus der aktuellen Ankündigungsliste hinein. Der Code überprüft auch, ob bereits eine Sicherungsliste vorhanden ist, bevor Sie erstellt wird. Wenn bereits eine Sicherungsliste vorhanden ist, wird Sie gelöscht. Der Code fügt der neuen Liste auch einen Link auf der Schnellstartleiste der SharePoint-Website hinzu.

#### <a name="to-test-the-site-workflow-custom-activity"></a>So testen Sie die benutzerdefinierte Aktivität "Website Workflow"

1. Drücken Sie die Taste **F5** , um das Projekt auszuführen und in SharePoint bereitzustellen.

2. Wählen Sie auf der Schnellstartleiste den Link **Listen** aus, um alle Listen anzuzeigen, die auf der SharePoint-Website verfügbar sind. Beachten Sie, dass es nur eine Liste für Ankündigungen namens **Ankündigungen** gibt.

3. Klicken Sie oben auf der SharePoint-Webseite auf den Link **Site Workflows** .

4. Wählen Sie im Abschnitt neuen Workflow starten den Link " **verküncementbackup-Workflow1** " aus. Dadurch wird der Website Workflow gestartet, und der Code wird in der benutzerdefinierten Aktion ausgeführt.

5. Wählen Sie auf der Schnellstartleiste den Link **Ankündigungen-Sicherung** aus. Beachten Sie, dass alle in der **Ankündigungs** Liste enthaltenen Ankündigungen in diese neue Liste kopiert wurden.

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
