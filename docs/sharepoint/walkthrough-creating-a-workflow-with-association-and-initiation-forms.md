---
title: Erstellen eines Workflows mit Zuordnungs-und Initiierungs Formularen
description: Erstellen Sie in dieser SharePoint-exemplarischen Vorgehensweise einen grundlegenden sequenziellen Workflow, der die Verwendung von Zuordnungs-und Initiierungs Formularen integriert
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62501a23695b81ee0437d3210dced7c81f9b054e
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970441"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen
  Diese exemplarische Vorgehensweise veranschaulicht das Erstellen eines grundlegenden sequenziellen Workflows, der die Verwendung von Zuordnungs-und Initiierungs Formularen einschließt. Hierbei handelt es sich um ASPX-Formulare, die das Hinzufügen von Parametern zu einem Workflow ermöglichen, wenn er dem SharePoint-Administrator (dem Zuordnungs Formular) zuerst zugeordnet ist, und wenn der Workflow vom Benutzer gestartet wird (Initiierungs Formular).

 In dieser exemplarischen Vorgehensweise wird ein Szenario beschrieben, in dem ein Benutzer einen Genehmigungs Workflow für Ausgaben Berichte erstellen möchte, die die folgenden Anforderungen erfüllen:

- Wenn der Workflow einer Liste zugeordnet ist, wird der Administrator mit einem Zuordnungs Formular aufgefordert, bei dem Sie ein Dollar Limit für Ausgaben Berichte eingeben.

- Mitarbeiter laden ihre Ausgaben Berichte in die Liste der freigegebenen Dokumente hoch, starten den Workflow und geben dann die Summe der Ausgaben im Workflow Initiierungs Formular ein.

- Wenn ein Mitarbeiter Ausgaben Bericht den voreingestellten Grenzwert des Administrators überschreitet, wird eine Aufgabe für den Vorgesetzten des Mitarbeiters erstellt, um den Spesen Betrag zu genehmigen. Wenn allerdings der Ausgaben Bericht eines Mitarbeiters kleiner oder gleich dem Ausgabenlimit ist, wird eine automatisch genehmigte Nachricht in die Verlaufs Liste des Workflows geschrieben.

  In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines sequenziellen Workflow Projekts für eine SharePoint-Listen Definition in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Erstellen eines Workflow Zeitplans

- Verarbeiten von Workflow Aktivitäts Ereignissen.

- Erstellen von Workflow Zuordnungs-und Initiierungs Formularen

- Zuordnen des Workflows.

- Manuelles Starten des Workflows.

> [!NOTE]
> Obwohl in dieser exemplarischen Vorgehensweise ein sequenzielles Workflow Projekt verwendet wird, ist der Prozess für Zustandsautomatworkflows identisch.
>
> Außerdem kann der Computer in den folgenden Anweisungen verschiedene Namen oder Speicherorte für einige der [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Benutzeroberflächen Elemente anzeigen. Diese Elemente werden in der von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ihnen verwendeten Edition und den von Ihnen verwendeten Einstellungen festgelegt. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.

- Visual Studio.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Erstellen eines sequenziellen SharePoint-Workflow Projekts
 Erstellen Sie zunächst in ein sequenzielles Workflow Projekt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Ein sequenzieller Workflow ist eine Reihe von Schritten, die nacheinander ausgeführt werden, bis die letzte Aktivität abgeschlossen ist. In diesem Verfahren erstellen Sie einen sequenziellen Workflow, der auf die Liste der freigegebenen Dokumente in SharePoint angewendet wird. Mit dem Assistenten für den-Workflow können Sie den Workflow entweder der Website oder der Listen Definition zuordnen und ermitteln, wann der Workflow gestartet wird.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>So erstellen Sie ein sequenzielles SharePoint-Workflow Projekt

1. Wählen Sie in der Menüleiste **Datei**  >  **neu**  >  **Projekt** aus, um das Dialogfeld **Neues Projekt** anzuzeigen.

2. Erweitern Sie den **SharePoint** -Knoten entweder unter **Visual c#** oder **Visual Basic**, und wählen Sie dann den Knoten **2010** aus.

3. Wählen Sie im Bereich **Vorlagen** die Vorlage **SharePoint 2010 Project** Project aus.

4. Geben Sie im Feld **Name den Namen** **ExpenseReport** ein, und klicken Sie dann auf die Schaltfläche **OK** .

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt.

5. Wählen Sie auf der Seite **Standort und Sicherheit für Debugging angeben** das Optionsfeld **als Farm Lösung** bereitstellen aus, und klicken Sie dann auf die Schaltfläche **Fertig** stellen, um die Vertrauens Ebene und die Standard Website zu akzeptieren.

     In diesem Schritt wird auch die Vertrauens Ebene für die Lösung als Farm Lösung festgelegt, die die einzige verfügbare Option für Workflow Projekte ist.

6. Wählen Sie im **Projektmappen-Explorer** den Projektknoten aus.

7. Wählen Sie in der Menüleiste **Projekt**  >  **Neues Element hinzufügen** aus.

8. Erweitern Sie unter **Visual c#** oder **Visual Basic** den Knoten **SharePoint** , und wählen Sie dann den Knoten **2010** aus.

9. Wählen Sie im Bereich **Vorlagen** die Vorlage **sequenzieller Workflow (nur Farm Lösung)** aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt.

10. Übernehmen Sie auf der Seite **Geben Sie den Workflow Namen für das Debuggen** an den Standardnamen (**ExpenseReport-Workflow1**). Behalten Sie den Standardwert Workflow Template Type (**Workflow auflisten)** bei. Klicken Sie auf **Weiter**.

11. Deaktivieren Sie in der Seite möchten Sie, dass **Visual Studio den Workflow automatisch einer Debugsitzung** zuordnet? das Feld, das die Workflow Vorlage automatisch zuordnet, wenn Sie aktiviert ist.

     Mit diesem Schritt können Sie den Workflow der Liste der freigegebenen Dokumente später manuell zuordnen, wodurch das Zuordnungs Formular angezeigt wird.

12. Klicken Sie auf die Schaltfläche **Fertig stellen**.

## <a name="add-an-association-form-to-the-workflow"></a>Hinzufügen eines Zuordnungs Formulars zum Workflow
 Erstellen Sie als nächstes eine. Aspx-Zuordnungs Formular, das angezeigt wird, wenn der SharePoint-Administrator den Workflow zunächst einem Ausgaben Berichts Dokument zuordnet.

#### <a name="to-add-an-association-form-to-the-workflow"></a>So fügen Sie dem Workflow ein Zuordnungs Formular hinzu

1. Wählen Sie in **Projektmappen-Explorer** den Knoten **Workflow1** aus.

2. Klicken Sie in der Menüleiste auf **Projekt**  >  **Neues Element hinzufügen** , um das Dialogfeld **Neues Element hinzufügen** anzuzeigen.

3. Erweitern Sie in der Strukturansicht des Dialog Felds entweder **Visual c#** oder **Visual Basic** (abhängig von der Projektsprache), erweitern Sie den **SharePoint** -Knoten, und wählen Sie dann den Knoten **2010** aus.

4. Wählen Sie in der Liste der Vorlagen die Vorlage **Workflow Association-Formular** aus.

5. Geben Sie im Textfeld **Name den Namen** **ExpenseReportAssocForm. aspx** ein.

6. Wählen Sie die Schaltfläche **Hinzufügen** aus, um das Formular dem Projekt hinzuzufügen.

## <a name="designing-and-coding-the-association-form"></a>Entwerfen und Codieren des Zuordnungs Formulars
 In diesem Verfahren stellen Sie Funktionen für das Zuordnungs Formular bereit, indem Sie Steuerelemente und Code hinzufügen.

#### <a name="to-design-and-code-the-association-form"></a>So entwerfen und codieren Sie das Zuordnungs Formular

1. Suchen Sie im Zuordnungs Formular (ExpenseReportAssocForm. aspx) das- `asp:Content` Element, das hat `ID="Main"` .

2. Fügen Sie direkt nach der ersten Zeile in diesem Inhalts Element den folgenden Code hinzu, um eine Bezeichnung und ein Textfeld zu erstellen, die zur Eingabe des Genehmigungs Limits für Ausgaben (*AutoApproveLimit*) aufgefordert werden:

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. Erweitern Sie in **Projektmappen-Explorer** die Datei **ExpenseReportAssocForm. aspx** , um die abhängigen Dateien anzuzeigen.

    > [!NOTE]
    > Wenn das Projekt in ist [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] , müssen Sie die Schaltfläche **alle Dateien anzeigen** auswählen, um diesen Schritt auszuführen.

4. Öffnen Sie das Kontextmenü für die Datei ExpenseReportAssocForm. aspx, und wählen Sie **Code anzeigen** aus.

5. Ersetzen Sie die- `GetAssociationData` Methode durch:

    ```vb
    Private Function GetAssociationData() As String
        ' TODO: Return a string that contains the association data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return Me.AutoApproveLimit.Text
    End Function
    ```

    ```csharp
    private string GetAssociationData()
    {
        // TODO: Return a string that contains the association data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.AutoApproveLimit.Text;
    }
    ```

## <a name="add-an-initiation-form-to-the-workflow"></a>Hinzufügen eines Initiierungs Formulars zum Workflow
 Erstellen Sie als nächstes das Initiierungs Formular, das angezeigt wird, wenn Benutzer den Workflow für Ihre Ausgaben Berichte ausführen.

#### <a name="to-create-an-initiation-form"></a>So erstellen Sie ein Initiierungs Formular

1. Wählen Sie in **Projektmappen-Explorer** den Knoten **Workflow1** aus.

2. Klicken Sie in der Menüleiste auf **Projekt**  >  **Neues Element hinzu** fügen, um das Dialogfeld **Neues Element hinzufügen** anzuzeigen.

3. Erweitern Sie in der Strukturansicht des Dialog Felds entweder **Visual c#** oder **Visual Basic**  (abhängig von der Projektsprache), erweitern Sie den **SharePoint** -Knoten, und wählen Sie dann den Knoten **2010** aus.

4. Wählen Sie in der Liste der Vorlagen die Vorlage **Workflow Initiierungs Formular aus** .

5. Geben Sie im Textfeld **Name den Namen** **ExpenseReportInitForm. aspx** ein.

6. Wählen Sie die Schaltfläche **Hinzufügen** aus, um das Formular dem Projekt hinzuzufügen.

## <a name="designing-and-coding-the-initiation-form"></a>Entwerfen und Codieren des Initiierungs Formulars
 Im nächsten Schritt stellen Sie dem Initiierungs Formular Funktionen bereit, indem Sie Steuerelemente und Code hinzufügen.

#### <a name="to-code-the-initiation-form"></a>So codieren Sie das Initiierungs Formular

1. Suchen Sie im Initialisierungs Formular (ExpenseReportInitForm. aspx) das- `asp:Content` Element, das enthält `ID="Main"` .

2. Fügen Sie direkt nach der ersten Zeile in diesem Inhalts Element den folgenden Code hinzu, um eine Bezeichnung und ein Textfeld-Element zu erstellen, das das im Zuordnungs Formular eingegebene Limit für die Kosten Genehmigung (*AutoApproveLimit*) anzeigt, und eine weitere Bezeichnung und Textfeld, um die Summe der Ausgaben (*ExpenseTotal*) aufzuräumen:

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. Erweitern Sie in **Projektmappen-Explorer** die Datei **ExpenseReportInitForm. aspx** , um die abhängigen Dateien anzuzeigen.

4. Öffnen Sie das Kontextmenü für die Datei ExpenseReportInitForm. aspx, und wählen Sie **Code anzeigen** aus.

5. Ersetzen Sie die- `Page_Load` Methode durch das folgende Beispiel:

    ```vb
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As
      EventArgs) Handles Me.Load
        InitializeParams()
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New
          Guid(associationGuid)).AssociationData
        ' Optionally, add code here to pre-populate your form fields.
    End Sub
    ```

    ```csharp
    protected void Page_Load(object sender, EventArgs e)
    {
        InitializeParams();
        this.AutoApproveLimit.Text =
          workflowList.WorkflowAssociations[new
          Guid(associationGuid)].AssociationData;
    }
    ```

6. Ersetzen Sie die- `GetInitiationData` Methode durch das folgende Beispiel:

    ```vb
    ' This method is called when the user clicks the button to start the workflow.
    Private Function GetInitiationData() As String
        Return Me.ExpenseTotal.Text
        ' TODO: Return a string that contains the initiation data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return String.Empty
    End Function
    ```

    ```csharp
    // This method is called when the user clicks the button to start the workflow.
    private string GetInitiationData()
    {
        // TODO: Return a string that contains the initiation data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.ExpenseTotal.Text;
    }
    ```

## <a name="cutomize-the-workflow"></a>Cutomize the Workflow
 Passen Sie den Workflow anschließend an. Später ordnen Sie zwei Formulare dem Workflow zu.

#### <a name="to-customize-the-workflow"></a>So passen Sie den Workflow an

1. Zeigen Sie den Workflow im Workflow-Designer an, indem Sie Workflow1 im Projekt öffnen.

2. Erweitern Sie in der **Toolbox** den **Windows Workflow v 3.0** -Knoten, und suchen Sie die **IfElse** -Aktivität.

3. Fügen Sie dem Workflow diese Aktivität hinzu, indem Sie einen der folgenden Schritte ausführen:

    - Öffnen Sie das Kontextmenü für die **IfElse** -Aktivität, wählen Sie **Kopieren** aus, öffnen Sie das Kontextmenü für die Zeile unter der **onWorkflowActivated1** -Aktivität im Workflow-Designer, und wählen Sie dann **Einfügen** aus.

    - Ziehen Sie die **IfElse** -Aktivität aus der **Toolbox**, und verbinden Sie Sie mit der Zeile unter der **onWorkflowActiviated1** -Aktivität im Workflow-Designer.

4. Erweitern Sie in der Toolbox den **SharePoint-Workflow** Knoten, und suchen Sie die Aktivität " **kreatetask** ".

5. Fügen Sie dem Workflow diese Aktivität hinzu, indem Sie einen der folgenden Schritte ausführen:

    - Öffnen Sie das Kontextmenü für die Aktivität " **kreatetask** ", wählen Sie **Kopieren** aus, öffnen Sie das Kontextmenü für eine der beiden Ablage **Aktivitäten hier** Bereiche innerhalb von **IfElseActivity1** im Workflow-Designer, und wählen Sie dann **Einfügen** aus.

    - Ziehen Sie die Aktivität " **kreatetask** " aus der **Toolbox** auf eine der beiden Bereiche " **Drop Activities here** " in **IfElseActivity1**.

6. Geben Sie im Fenster **Eigenschaften** den Eigenschafts Wert *taskToken* für die **CorrelationToken** -Eigenschaft ein.

7. Erweitern Sie die **CorrelationToken** -Eigenschaft, indem Sie das Pluszeichen (![TreeView Plus](../sharepoint/media/plus.gif "TreeView-Plus")) Daneben auswählen.

8. Wählen Sie den Dropdown Pfeil in der untergeordneten Eigenschaft Besitzer **ActivityName** aus, und legen Sie den Wert *Workflow1* fest.

9. Wählen Sie die **TaskID** -Eigenschaft aus, und klicken Sie dann auf die Schaltfläche mit den Auslassungs Punkten (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")), um das Dialogfeld **Eigenschaft binden** anzuzeigen.

10. Wählen Sie die Registerkarte **an einen neuen Member binden** aus, wählen Sie das options **Feld Feld erstellen** , und klicken Sie dann auf die Schaltfläche **OK** .

11. Wählen Sie die Eigenschaft **TaskProperties** aus, und klicken Sie dann auf die Schaltfläche mit den Auslassungs Punkten (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")), um das Dialogfeld **Eigenschaft binden** anzuzeigen.

12. Wählen Sie die Registerkarte **an einen neuen Member binden** aus, wählen Sie das options **Feld Feld erstellen** , und klicken Sie dann auf die Schaltfläche **OK** .

13. Erweitern Sie in der **Toolbox** den Knoten **SharePoint-Workflow** , und suchen Sie die Aktivität **logdehistorylistactivity** .

14. Fügen Sie dem Workflow diese Aktivität hinzu, indem Sie einen der folgenden Schritte ausführen:

    - Öffnen Sie das Kontextmenü für die **LogToHistoryListActivity** -Aktivität, wählen Sie **Kopieren** aus, öffnen Sie das Kontextmenü für den anderen Bereich Ablage **Aktivitäten hier** in **IfElseActivity1** im Workflow-Designer, und wählen Sie dann **Einfügen** aus.

    - Ziehen Sie die **logrehistorylistactivity** -Aktivität aus der **Toolbox**, und legen Sie Sie auf dem anderen Bereich Ablage **Aktivitäten hier** in **IfElseActivity1** ab.

## <a name="add-code-to-the-workflow"></a>Hinzufügen von Code zum Workflow
 Fügen Sie dann dem Workflow Code hinzu, um ihm Funktionalität zu geben.

#### <a name="to-add-code-to-the-workflow"></a>So fügen Sie dem Workflow Code hinzu

1. Öffnen Sie das Kontextmenü für die **createTask1** -Aktivität im Workflow-Designer, und wählen Sie dann **Code anzeigen** aus.

2. Fügen Sie die folgende Methode hinzu:

    ```vb
    Private Sub createTask1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        createTask1_TaskId1 = Guid.NewGuid
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"
        createTask1_TaskProperties1.Description = "Please approve the
          expense report"
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed"
    End Sub
    ```

    ```csharp
    private void createTask1_MethodInvoking(object sender, EventArgs e)
    {
        createTask1_TaskId1 = Guid.NewGuid();
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";
        createTask1_TaskProperties1.Description = "Please approve the
          expense report";
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed";
    }
    ```

    > [!NOTE]
    > Ersetzen Sie im Code `somedomain\\someuser` durch einen Domänen-und Benutzernamen, für den eine Aufgabe erstellt wird, z. b `Office\\JoeSch` . "". Zum Testen ist es am einfachsten, das Konto zu verwenden, mit dem Sie entwickeln.

3. Fügen Sie unter der- `MethodInvoking` Methode das folgende Beispiel hinzu:

    ```vb
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As
      ConditionalEventArgs)
        Dim approval As Boolean = False
        If (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData)) Then
            approval = True
        End If
        e.Result = approval
    End Sub
    ```

    ```csharp
    private void checkApprovalNeeded(object sender, ConditionalEventArgs
      e)
    {
        bool approval = false;
        if (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData))
        {
            approval = true;
        }
        e.Result = approval;
    }
    ```

4. Wählen Sie im Workflow-Designer die **ifElseBranchActivity1** -Aktivität aus.

5. Wählen Sie im Fenster **Eigenschaften** den Dropdown Pfeil der **Condition** -Eigenschaft aus, und legen Sie dann den Wert für die *Code Bedingung* fest.

6. Erweitern Sie die **Condition** -Eigenschaft, indem Sie neben dem Pluszeichen (TreeView Plus) das Pluszeichen (![TreeView Plus](../sharepoint/media/plus.gif "TreeView-Plus")) auswählen, und legen Sie dessen Wert auf *checkapprovalbenö*

7. Öffnen Sie im Workflow-Designer das Kontextmenü für die **logToHistoryListActivity1** -Aktivität, und wählen Sie dann **Handler generieren** aus, um eine leere Methode für das Ereignis zu generieren `MethodInvoking` .

8. Ersetzen Sie den `MethodInvoking` Code durch Folgendes:

    ```vb
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto
          approved for " + workflowProperties.InitiationData)
    End Sub
    ```

    ```csharp
    private void logToHistoryListActivity1_MethodInvoking(object sender,
      EventArgs e)
    {
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was
          auto approved for " + workflowProperties.InitiationData;
    }
    ```

9. Drücken Sie die Taste **F5** , um das Programm zu debuggen.

     Dadurch wird die Anwendung kompiliert, verpackt, bereitgestellt, die Funktionen werden aktiviert, der [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] Anwendungs Pool wird wieder verwendet, und anschließend wird der Browser an dem Speicherort gestartet, der in der **Website-URL** -Eigenschaft angegeben ist.

## <a name="associating-the-workflow-to-the-documents-list"></a>Zuordnen des Workflows zur Liste "Dokumente"
 Als Nächstes zeigen Sie das Workflow Zuordnungs Formular an, indem Sie den Workflow der **SharedDocuments** -Liste auf der SharePoint-Website zuordnen.

#### <a name="to-associate-the-workflow"></a>So ordnen Sie den Workflow zu

1. Wählen Sie auf der Schnellstartleiste den Link frei **gegebene Dokumente** aus.

2. Wählen Sie auf der Registerkarte **Bibliotheks Tools** den Link **Bibliothek** aus, und klicken Sie dann auf die Schaltfläche **Bibliotheks Einstellungen** .

3. Wählen Sie im Abschnitt **Berechtigungen und Verwaltung** den Link **Workflow Einstellungen** aus, und wählen Sie dann auf der Seite **Workflows** den Link **Workflow hinzufügen** aus.

4. Wählen Sie in der oberen Liste auf der Seite Workflow Einstellungen die Vorlage **ExpenseReport-Workflow1** aus.

5. Geben Sie im nächsten Feld **ExpenseReportWorkflow** ein, und wählen Sie dann die Schaltfläche **weiter** aus.

     Dadurch wird der Workflow der Liste der frei **gegebenen Dokumente** zugeordnet, und das Workflow Zuordnungs Formular wird angezeigt.

6. Geben Sie im Textfeld **automatische Genehmigung** den Wert **1200** ein, und wählen Sie dann die Schaltfläche **Workflow zuordnen** aus.

## <a name="start-the-workflow"></a>Starten des Workflows
 Ordnen Sie anschließend den Workflow einem der Dokumente in der Liste frei **gegebene Dokumente** zu, um das Workflow Initiierungs Formular anzuzeigen.

#### <a name="to-start-the-workflow"></a>So starten Sie den Workflow

1. Wählen Sie auf der SharePoint-Seite die **Start** Schaltfläche aus.

2. Wählen Sie auf der Schnellstartleiste den Link frei **gegebene Dokumente** aus, um die Liste mit den frei **gegebenen Dokumenten** anzuzeigen.

3. Klicken Sie oben auf der Seite auf der Registerkarte **Bibliotheks Tools** auf den Link **Dokumente** , und wählen Sie dann im Menüband die Schaltfläche **Dokument hochladen** aus, um ein neues Dokument in die Liste der frei **gegebenen Dokumente** hochzuladen.

4. Wählen Sie im Dialogfeld **Dokument hochladen** die Schaltfläche **Durchsuchen** aus, wählen Sie eine beliebige Dokument Datei aus, klicken Sie auf die Schaltfläche **Öffnen** , und wählen Sie dann die Schaltfläche **OK** .

     Sie können die Einstellungen für das Dokument in diesem Dialogfeld ändern, aber die Standardwerte überlassen, indem Sie auf die Schaltfläche **Speichern** klicken.

5. Wählen Sie das hochgeladene Dokument aus, wählen Sie den angezeigten Dropdown Pfeil aus, und wählen Sie dann das Element **Workflows** aus.

6. Wählen Sie das Bild neben ExpenseReportWorkflow aus.

     Dadurch wird das Workflow Initiierungs Formular angezeigt. (Beachten Sie, dass der im Feld für die **automatische Genehmigung** angezeigte Wert schreibgeschützt ist, weil er im Zuordnungs Formular eingegeben wurde.)

7. Geben Sie im Textfeld **Ausgaben gesamt** den Wert **1600** ein, und wählen Sie dann die Schaltfläche **Workflow starten** aus.

     Dadurch wird die Liste der frei **gegebenen Dokumente** erneut angezeigt. Dem soeben gestarteten Workflow wird eine neue Spalte mit dem Namen **ExpenseReportWorkflow** mit dem Wert **abgeschlossen** hinzugefügt.

8. Wählen Sie den Dropdown Pfeil neben dem hochgeladenen Dokument aus, und wählen Sie dann das Element **Workflows** aus, um die Seite Workflow Status anzuzeigen. Wählen Sie unter **abgeschlossene Workflows** den **voll** ständigen Wert aus. Der Task ist im Abschnitt **Tasks** aufgeführt.

9. Wählen Sie den Titel der Aufgabe aus, um die zugehörigen Aufgaben Details anzuzeigen.

10. Wechseln Sie zurück zur Liste **SharedDocuments** , und starten Sie den Workflow mit dem gleichen oder einem anderen Dokument neu.

11. Geben Sie eine Menge auf der Initiierungs Seite ein, die kleiner oder gleich dem auf der Zuordnungs Seite eingegebenen Betrag (**1200**) ist.

     In diesem Fall wird ein Eintrag in der Verlaufs Liste anstelle einer Aufgabe erstellt. Der Eintrag wird im Abschnitt **Workflow Verlauf** der Seite Workflow Status angezeigt. Beachten Sie die Meldung in der Spalte **Ergebnis** des Verlaufs Ereignisses. Sie enthält den Text, der in das `logToHistoryListActivity1.MethodInvoking` Ereignis eingegeben wurde, das die automatisch genehmigte Menge enthält.

## <a name="next-steps"></a>Nächste Schritte
 Weitere Informationen zum Erstellen von Workflow Vorlagen finden Sie in den folgenden Themen:

- Weitere Informationen zu SharePoint-Workflows finden Sie unter [Workflows in Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms416312(v=office.14)).

## <a name="see-also"></a>Weitere Informationen
- [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Exemplarische Vorgehensweise: Hinzufügen einer Anwendungsseite zu einem Workflow](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
