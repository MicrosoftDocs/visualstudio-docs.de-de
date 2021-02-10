---
title: Erstellen & Debuggen einer SharePoint-Workflow Lösung
description: Erstellen und Debuggen Sie in dieser exemplarischen Vorgehensweise eine SharePoint-Workflow Projekt Mappe. Erstellen Sie eine grundlegende Vorlage für einen sequenziellen Workflow. Erstellen von Workflow Aktivitäten und behandeln von Ereignissen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 637d46eaa9ac9306d63befed1c011c278b46af24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952719"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>Exemplarische Vorgehensweise: Erstellen und Debuggen einer Projektmappe für einen SharePoint-Workflow
  Diese exemplarische Vorgehensweise veranschaulicht, wie eine grundlegende sequenzielle Workflow Vorlage erstellt wird. Der Workflow überprüft eine Eigenschaft einer freigegebenen Dokumentbibliothek, um zu bestimmen, ob ein Dokument überprüft wurde. Wenn das Dokument überprüft wurde, wird der Workflow beendet.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines sequenziellen Workflow Projekts für eine SharePoint-Listen Definition in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Erstellen von Workflow Aktivitäten.

- Verarbeiten von Workflow Aktivitäts Ereignissen.

> [!NOTE]
> Obwohl in dieser exemplarischen Vorgehensweise ein sequenzielles Workflow Projekt verwendet wird, ist der Prozess für ein Zustands Automaten Workflow-Projekt identisch.
>
> Der Computer kann auch unterschiedliche Namen oder Speicherorte für einige der Visual Studio-Benutzeroberflächen Elemente in den folgenden Anweisungen anzeigen. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Unterstützte Editionen von Microsoft Windows und SharePoint.

- Visual Studio.

## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>Hinzufügen von Eigenschaften zur SharePoint-Bibliothek für freigegebene Dokumente
 Um den Überprüfungs Status von Dokumenten in der Bibliothek für frei **gegebene Dokumente** zu verfolgen, erstellen wir drei neue Eigenschaften für freigegebene Dokumente auf unserer SharePoint-Website: `Status` , `Assignee` und `Review Comments` . Diese Eigenschaften werden in der Bibliothek für frei **gegebene Dokumente** definiert.

#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>So fügen Sie der SharePoint-Bibliothek für freigegebene Dokumente Eigenschaften hinzu

1. Öffnen Sie eine SharePoint-Website, z \<system name> . b. http:///SitePages/Home.aspx, in einem Webbrowser.

2. Wählen Sie auf der Schnellstartleiste **SharedDocuments** aus.

3. Wählen Sie im Menüband **Bibliothek Tools** die Option **Bibliothek** aus, und wählen Sie dann im Menüband die Schaltfläche **Spalte erstellen** , um eine neue Spalte zu erstellen.

4. Benennen Sie die Spalte **Dokument Status**, legen Sie den Typ auf " **Choice" (Menü zum auswählen aus)** fest, geben Sie die folgenden drei Optionen an, und wählen Sie dann die Schaltfläche **OK** aus:

    - **Review erforderlich**

    - **Review ist beendet**

    - **Angeforderte Änderungen**

5. Erstellen Sie zwei weitere Spalten **, und benennen** Sie Sie in den **Kommentaren**. Legen Sie den Typ der Zuweisungs Spalte als einzelne Textzeile fest, und überprüfen Sie die Spalte Kommentare als mehrere Textzeilen.

## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Aktivieren der Bearbeitung von Dokumenten, ohne dass ein Auschecken erforderlich ist
 Es ist einfacher, die Workflow Vorlage zu testen, wenn Sie die Dokumente bearbeiten können, ohne Sie auschecken zu müssen. Im nächsten Verfahren konfigurieren Sie die SharePoint-Website, um dies zu aktivieren.

#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>So aktivieren Sie die Bearbeitung von Dokumenten, ohne Sie auszuchecken

1. Wählen Sie auf der Schnellstartleiste den Link frei **gegebene Dokumente** aus.

2. Wählen Sie im Menüband **Bibliotheks Tools** die Registerkarte **Bibliothek** aus, und klicken Sie dann auf die Schaltfläche **Bibliotheks Einstellungen** , um die Seite **Dokument Bibliotheks Einstellungen** anzuzeigen.

3. Wählen Sie im Abschnitt **Allgemeine Einstellungen** den Link **Versions Verwaltungs Einstellungen** aus, um die Seite Einstellungen für die **Versions** Verwaltung anzuzeigen.

4. Vergewissern Sie sich, dass die Einstellung für das  **Auschecken von Dokumenten erforderlich ist, bevor Sie bearbeitet werden können** . Wenn dies nicht der Fall ist, ändern Sie den Wert in **Nein** , und wählen Sie dann die Schaltfläche **OK** .

5. Schließen Sie den Browser.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Erstellen eines sequenziellen SharePoint-Workflow Projekts
 Ein sequenzieller Workflow ist eine Reihe von Schritten, die nacheinander ausgeführt werden, bis die letzte Aktivität abgeschlossen ist. In diesem Verfahren wird ein sequenzieller Workflow erstellt, der auf die Liste der freigegebenen Dokumente angewendet wird. Mit dem Workflow-Assistenten können Sie den Workflow entweder der Site Definition oder der Listen Definition zuordnen und ermitteln, wann der Workflow gestartet wird.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>So erstellen Sie ein sequenzielles SharePoint-Workflow Projekt

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Wählen Sie in der Menüleiste **Datei**  >  **neu**  >  **Projekt** aus, um das Dialogfeld **Neues Projekt** anzuzeigen.

3. Erweitern Sie den **SharePoint** -Knoten entweder unter **Visual c#** oder **Visual Basic**, und wählen Sie dann den Knoten **2010** aus.

4. Wählen Sie im Bereich **Vorlagen** die **SharePoint 2010-Projekt** Vorlage aus.

5. Geben Sie im Feld **Name den Namen** **MySharePointWorkflow** ein, und klicken Sie dann auf die Schaltfläche **OK** .

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt.

6. Wählen Sie auf der Seite **Standort und Sicherheit für Debugging angeben** das Optionsfeld **als Farm Lösung** bereitstellen aus, und klicken Sie dann auf die Schaltfläche **Fertig** stellen, um die Vertrauens Ebene und die Standard Website zu akzeptieren.

     In diesem Schritt wird die Vertrauens Ebene für die Lösung als Farm Lösung festgelegt, die einzige verfügbare Option für Workflow Projekte. Weitere Informationen finden Sie unter [Überlegungen zu Sandkasten Lösungen](../sharepoint/sandboxed-solution-considerations.md).

7. Wählen Sie in **Projektmappen-Explorer** den Projekt Knoten aus, und klicken Sie dann in der Menüleiste auf **Projekt**  >  **Neues Element hinzufügen**.

8. Erweitern Sie unter **Visual c#** oder **Visual Basic** den Knoten **SharePoint** , und wählen Sie dann den Knoten **2010** aus.

9. Wählen Sie im Bereich **Vorlagen** die Vorlage **sequenzieller Workflow (nur Farm Lösung)** aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt.

10. Übernehmen Sie auf der Seite **Geben Sie den Workflow Namen für das Debuggen** an den Standardnamen (**MySharePointWorkflow-Workflow1**). Behalten Sie den Standardwert Workflow Template Type, **List Workflow**, und wählen Sie dann die Schaltfläche **weiter** aus.

11. Wählen Sie in der Seite möchten **Sie, dass Visual Studio den Workflow automatisch einer Debugsitzung zuordnen?** die Schaltfläche **weiter** aus, um alle Standardeinstellungen zu akzeptieren.

     Durch diesen Schritt wird der Workflow automatisch der freigegebenen Dokumentbibliothek zugeordnet.

12. Übernehmen Sie auf der Seite **Geben Sie die Bedingungen für die Funktionsweise des Workflows** an die Standardoptionen, die im Abschnitt **wie soll der Workflow** gestartet werden? die Standardoptionen, und klicken Sie auf die Schaltfläche **Fertig** stellen.

     Auf dieser Seite können Sie angeben, wann der Workflow gestartet wird. Der Workflow wird standardmäßig entweder gestartet, wenn ein Benutzer ihn manuell in SharePoint startet oder wenn ein Element erstellt wird, dem der Workflow zugeordnet ist.

## <a name="create-workflow-activities"></a>Erstellen von Workflow Aktivitäten
 Workflows enthalten mindestens eine *Aktivität* , die auszuführende Aktionen darstellt. Mit dem Workflow-Designer können Sie Aktivitäten für einen Workflow anordnen. In diesem Verfahren werden dem Workflow zwei Aktivitäten hinzugefügt: "Lenker externaleventactivity" und "onWorkflowItemChanged". Diese Aktivitäten überwachen den Überprüfungs Status von Dokumenten in der Liste der frei **gegebenen Dokumente** .

#### <a name="to-create-workflow-activities"></a>So erstellen Sie Workflow Aktivitäten

1. Der Workflow sollte im Workflow-Designer angezeigt werden. Wenn dies nicht der Fall ist, öffnen Sie entweder **Workflow1.cs** oder **Workflow1. vb** in **Projektmappen-Explorer**.

2. Wählen Sie im Designer die **onWorkflowActivated1** -Aktivität aus.

3. Geben Sie im **Eigenschaften** Fenster **onworkflowaktivierte** neben der **aufgerufenen** Eigenschaft ein, und drücken Sie dann die EINGABETASTE.

     Der Code-Editor wird geöffnet, und der Workflow1-Codedatei wird eine Ereignishandlermethode mit dem Namen "onworkflowaktivierung" hinzugefügt.

4. Wechseln Sie zurück zum Workflow-Designer, öffnen Sie die Toolbox, und erweitern Sie dann den Knoten **Windows Workflow v 3.0** .

5. Führen Sie im Knoten **Windows Workflow v 3.0** der **Toolbox** einen der folgenden Schritte aus:

    1. Öffnen Sie das Kontextmenü für die **while** -Aktivität, und wählen Sie dann **Kopieren** aus. Öffnen Sie im Workflow-Designer das Kontextmenü für die Zeile unter der **onWorkflowActivated1** -Aktivität, und wählen Sie dann **Einfügen** aus.

    2. Ziehen Sie die **while** -Aktivität aus der **Toolbox** in den Workflow-Designer, und verbinden Sie die Aktivität mit der Zeile unter der **onWorkflowActivated1** -Aktivität.

6. Wählen Sie die **whileActivity1** -Aktivität aus.

7. Legen Sie im **Eigenschaften** Fenster **Bedingung** auf Code Bedingung fest.

8. Erweitern Sie die **Condition** -Eigenschaft, geben Sie **isWorkflowPending** neben der Eigenschaft untergeordnete **Bedingung** ein, und drücken Sie dann die EINGABETASTE.

     Der Code-Editor wird geöffnet, und der Workflow1-Codedatei wird eine Methode mit dem Namen "isWorkflowPending" hinzugefügt.

9. Wechseln Sie zurück zum Workflow-Designer, öffnen Sie die Toolbox, und erweitern Sie dann den Knoten **SharePoint-Workflow** .

10. Führen Sie im **SharePoint-Workflow** Knoten der **Toolbox** einen der folgenden Schritte aus:

    - Öffnen Sie das Kontextmenü für die **onWorkflowItemChanged** -Aktivität, und wählen Sie dann **Kopieren** aus. Öffnen Sie im Workflow-Designer das Kontextmenü für die Zeile in der **whileActivity1** -Aktivität, und wählen Sie dann **Einfügen** aus.

    - Ziehen Sie die Aktivität **onWorkflowItemChanged** aus der **Toolbox** in den Workflow-Designer, und verbinden Sie die Aktivität mit der Zeile in der **whileActivity1** -Aktivität.

11. Wählen Sie die **onWorkflowItemChanged1** -Aktivität aus.

12. Legen Sie im **Eigenschaften** Fenster die Eigenschaften fest, wie in der folgenden Tabelle dargestellt.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**CorrelationToken**|**Workflow Token**|
    |**Aufgerufen**|**"onWorkflowItemChanged"**|

## <a name="handle-activity-events"></a>Behandeln von Aktivitäts Ereignissen
 Überprüfen Sie schließlich den Status des Dokuments aus jeder Aktivität. Wenn das Dokument überprüft wurde, ist der Workflow abgeschlossen.

#### <a name="to-handle-activity-events"></a>So verarbeiten Sie Aktivitäts Ereignisse

1. Fügen Sie in *Workflow1.cs* oder *Workflow1. vb* das folgende Feld am Anfang der Klasse hinzu `Workflow1` . Dieses Feld wird in einer-Aktivität verwendet, um zu bestimmen, ob der Workflow abgeschlossen ist.

    ```vb
    Dim workflowPending As Boolean = True
    ```

    ```csharp
    Boolean workflowPending = true;
    ```

2. Füge der `Workflow1`-Klasse die folgende Methode hinzu. Diese Methode überprüft den Wert der- `Document Status` Eigenschaft der Liste Dokumente, um zu bestimmen, ob das Dokument überprüft wurde. Wenn die- `Document Status` Eigenschaft auf festgelegt ist `Review Complete` , `checkStatus` legt die-Methode das- `workflowPending` Feld auf **false** fest, um anzugeben, dass der Workflow fertig zu Ende ist.

    ```vb
    Private Sub checkStatus()
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then
            workflowPending = False
        End If
    End Sub
    ```

    ```csharp
    private void checkStatus()
    {
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")
        workflowPending = false;
    }
    ```

3. Fügen Sie den folgenden Code in die `onWorkflowActivated` -und- `onWorkflowItemChanged` Methoden ein, um die-Methode aufzurufen `checkStatus` Wenn der Workflow gestartet wird, `onWorkflowActivated` Ruft die-Methode die- `checkStatus` Methode auf, um zu bestimmen, ob das Dokument bereits überprüft wurde. Wenn Sie nicht überprüft wurde, wird der Workflow fortgesetzt. Wenn das Dokument gespeichert wird, ruft die- `onWorkflowItemChanged` Methode die- `checkStatus` Methode erneut auf, um zu bestimmen, ob das Dokument überprüft wurde. Obwohl das `workflowPending` Feld auf **true** festgelegt ist, wird der Workflow weiterhin ausgeführt.

    ```vb
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)
        checkStatus()
    End Sub

    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)
        checkStatus()
    End Sub
    ```

    ```csharp
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)
    {
        // Check the status.
        checkStatus();
    }

    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)
    {
        // Check the status.
        checkStatus();
    }
    ```

4. Fügen Sie der-Methode den folgenden Code hinzu `isWorkflowPending` , um den Status der-Eigenschaft zu überprüfen `workflowPending` . Jedes Mal, wenn das Dokument gespeichert wird, ruft die **whileActivity1** -Aktivität die- `isWorkflowPending` Methode auf. Diese Methode untersucht die- <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> Eigenschaft des- <xref:System.Workflow.Activities.ConditionalEventArgs> Objekts, um zu bestimmen, ob die **whileActivity1** -Aktivität fortgesetzt oder beendet werden soll. Wenn die-Eigenschaft auf **true** festgelegt ist, wird die-Aktivität fortgesetzt. Andernfalls wird die-Aktivität abgeschlossen, und der Workflow wird beendet.

    ```vb
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)
        e.Result = workflowPending
    End Sub
    ```

    ```csharp
    private void isWorkflowPending(object sender, ConditionalEventArgs e)
    {
        e.Result = workflowPending;
    }
    ```

5. Speichern Sie das Projekt.

## <a name="test-the-sharepoint-workflow-template"></a>Testen der SharePoint-Workflow Vorlage
 Wenn Sie den Debugger starten, wird [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Workflow Vorlage für den SharePoint-Server bereitgestellt, und der Workflow wird der Liste der frei **gegebenen Dokumente** zugeordnet. Um den Workflow zu testen, starten Sie eine Instanz des Workflows aus einem Dokument in der Liste der frei **gegebenen Dokumente** .

#### <a name="to-test-the-sharepoint-workflow-template"></a>So testen Sie die SharePoint-Workflow Vorlage

1. Legen Sie in *Workflow1.cs* oder *Workflow1. vb* einen Haltepunkt neben der **onworkflowaktivierten** -Methode fest.

2. Drücken Sie die Taste **F5** , um die Projekt Mappe zu erstellen und auszuführen.

     Die SharePoint-Website wird angezeigt.

3. Wählen Sie im Navigationsbereich von SharePoint den Link frei **gegebene Dokumente** aus.

4. Wählen Sie auf der Seite frei **gegebene Dokumente** den Link **Dokumente** auf der Registerkarte **Bibliotheks Tools** aus, und klicken Sie dann auf die Schaltfläche **Dokument hochladen** .

5. Wählen Sie im Dialogfeld **Dokument hochladen** die Schaltfläche **Durchsuchen** aus, wählen Sie eine beliebige Dokument Datei aus, klicken Sie auf die Schaltfläche **Öffnen** , und wählen Sie dann die Schaltfläche **OK** .

     Dadurch wird das ausgewählte Dokument in die Liste der frei **gegebenen Dokumente** hochgeladen, und der Workflow wird gestartet.

6. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Überprüfen Sie in, ob der Debugger am Haltepunkt neben der-Methode angehalten wird `onWorkflowActivated` .

7. Drücken Sie die Taste **F5** , um die Ausführung fortzusetzen.

8. Sie können die Einstellungen für das Dokument hier ändern, aber Sie können die Standardwerte vorerst überlassen, indem Sie auf die Schaltfläche **Speichern** klicken.

     Dadurch werden Sie zur Seite "frei **gegebene Dokumente** " der SharePoint-Standard Website zurückgegeben.

9. Überprüfen Sie auf der Seite frei **gegebene Dokumente** , ob der Wert unterhalb der Spalte **MySharePointWorkflow-Workflow1** auf **in** Bearbeitung festgelegt ist. Dies gibt an, dass der Workflow ausgeführt wird und dass das Dokument auf den Review wartet.

10. Wählen Sie auf der Seite frei **gegebene Dokumente** das Dokument aus, wählen Sie den angezeigten Pfeil aus, und wählen Sie dann das Menü Element **Eigenschaften bearbeiten** aus.

11. Legen Sie den **Dokument Status** auf **Review Complete** fest, und klicken Sie dann auf die Schaltfläche **Speichern** .

     Dadurch werden Sie zur Seite "frei **gegebene Dokumente** " der SharePoint-Standard Website zurückgegeben.

12. Überprüfen Sie auf der Seite frei **gegebene Dokumente** , ob der Wert unterhalb der Spalte **Dokument Status** auf **Review Complete** festgelegt ist. Aktualisieren Sie die Seite frei **gegebene Dokumente** , und überprüfen Sie, ob der Wert unterhalb der Spalte **MySharePointWorkflow-Workflow1** auf **abgeschlossen** festgelegt ist. Dies gibt an, dass der Workflow abgeschlossen ist und dass das Dokument überprüft wurde.

## <a name="next-steps"></a>Nächste Schritte
 Weitere Informationen zum Erstellen von Workflow Vorlagen finden Sie in den folgenden Themen:

- Weitere Informationen zu SharePoint-Workflow Aktivitäten finden Sie unter [Workflow Aktivitäten für SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

- Weitere Informationen zu Windows Workflow Foundation Aktivitäten finden Sie unter [System. Workflow. Activities-Namespace](/dotnet/api/system.windows.media.color).

## <a name="see-also"></a>Weitere Informationen
- [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [SharePoint-Projekt-und Projekt Element Vorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md)
- [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)
