---
title: 'Exemplarische Vorgehensweise: Hinzufügen einer Anwendungsseite zu einem Workflow | Microsoft-Dokumentation'
description: Fügen Sie in dieser exemplarischen Vorgehensweise eine Anwendungsseite zu einer SharePoint-Workflow-Projekt Mappe hinzu. Ändern Sie den Workflow Code. Erstellen, codieren und testen Sie die Anwendungsseite.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c862c1de3b0630b3a5144f821e6266c34a88a5db
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915660"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Exemplarische Vorgehensweise: Hinzufügen einer Anwendungsseite zu einem Workflow
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie eine Anwendungsseite hinzufügen, die von einem Workflow abgeleitete Daten einem Workflow Projekt anzeigt. Es baut auf dem Projekt auf, das im Thema Exemplarische Vorgehensweise [: Erstellen eines Workflows mit Zuordnungs-und Initiierungs Formularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)beschrieben wird.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Hinzufügen einer aspx-Anwendungsseite zu einem SharePoint-Workflow Projekt.

- Abrufen von Daten aus dem Workflow Projekt und deren Bearbeitung.

- Anzeigen von Daten in einer Tabelle auf der Anwendungsseite.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.

- Visual Studio.

- Sie müssen das Projekt auch im Thema Exemplarische Vorgehensweise [: Erstellen eines Workflows mit Zuordnungs-und Initiierungs Formularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)ausführen.

## <a name="amend-the-workflow-code"></a>Ändern des Workflow Codes
 Fügen Sie zunächst dem Workflow eine Codezeile hinzu, um den Wert der Spalte Ergebnis auf den Betrag des Ausgaben Berichts festzulegen. Dieser Wert wird später in der Zusammenfassungs Berechnung für Ausgaben Berichte verwendet.

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>So legen Sie den Wert der Ergebnisspalte im Workflow fest

1. Laden Sie das abgeschlossene Projekt aus dem Thema Exemplarische Vorgehensweise [: Erstellen eines Workflows mit Zuordnungs-und Initiierungs Formularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Öffnen Sie den Code für *Workflow1.cs* oder *Workflow1. vb* (abhängig von ihrer Programmiersprache).

3. Fügen Sie am Ende der `createTask1_MethodInvoking` Methode den folgenden Code hinzu:

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>Erstellen einer Anwendungsseite
 Fügen Sie dem Projekt als nächstes ein ASPX-Formular hinzu. In diesem Formular werden Daten angezeigt, die aus dem Workflow Projekt für Ausgaben Berichte abgerufen wurden. Hierzu fügen Sie eine Anwendungsseite hinzu. Auf einer Anwendungsseite wird dieselbe Master Seite wie andere SharePoint-Seiten verwendet, was bedeutet, dass Sie anderen Seiten auf der SharePoint-Website ähnelt.

#### <a name="to-add-an-application-page-to-the-project"></a>So fügen Sie dem Projekt eine Anwendungsseite hinzu

1. Wählen Sie das Projekt ExpenseReport aus, und klicken Sie dann in der Menüleiste auf **Projekt**  >  **Neues Element hinzufügen**.

2. Wählen Sie im Bereich **Vorlagen** die Vorlage **Anwendungsseite** aus, verwenden Sie den Standardnamen für das Projekt Element (**ApplicationPage1. aspx**), und klicken Sie auf die Schaltfläche **Hinzufügen** .

3. Ersetzen Sie im [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] von ApplicationPage1. aspx den `PlaceHolderMain` Abschnitt durch Folgendes:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
        <asp:Label ID="Label1" runat="server" Font-Bold="True"
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>
        <br />
        <asp:Table ID="Table1" runat="server">
        </asp:Table>
    </asp:Content>
    ```

     Mit diesem Code wird der Seite eine Tabelle mit einem Titel hinzugefügt.

4. Fügen Sie der Anwendungsseite einen Titel hinzu, indem Sie den `PlaceHolderPageTitleInTitleArea` Abschnitt durch Folgendes ersetzen:

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>Programmieren der Anwendungsseite
 Fügen Sie als nächstes der Seite Zusammenfassung der Ausgaben Berichte Code hinzu. Wenn Sie die Seite öffnen, scannt der Code die Aufgabenliste in SharePoint auf Ausgaben, die das zugewiesene Ausgabenlimit überschritten haben. Im Bericht werden alle Elemente zusammen mit der Summe der Ausgaben aufgelistet.

#### <a name="to-code-the-application-page"></a>So codieren Sie die Anwendungsseite

1. Wählen Sie den Knoten " **ApplicationPage1. aspx** " aus, und wählen Sie dann in der Menüleiste Code **anzeigen** aus,  >  **Code** um den Code hinter der Anwendungsseite anzuzeigen.

2. Ersetzen **Sie die using** -Anweisung oder die **Import** -Anweisung (abhängig von ihrer Programmiersprache) am Anfang der Klasse mit folgendem:

    ```vb
    Imports System
    Imports Microsoft.SharePoint
    Imports Microsoft.SharePoint.WebControls
    Imports System.Collections
    Imports System.Data
    Imports System.Web.UI
    Imports System.Web.UI.WebControls
    Imports System.Web.UI.WebControls.WebParts
    Imports System.Drawing
    Imports Microsoft.SharePoint.Navigation
    ```

    ```csharp
    using System;
    using Microsoft.SharePoint;
    using Microsoft.SharePoint.WebControls;
    using System.Collections;
    using System.Data;
    using System.Web.UI;
    using System.Web.UI.WebControls;
    using System.Web.UI.WebControls.WebParts;
    using System.Drawing;
    using Microsoft.SharePoint.Navigation;
    ```

3. Fügen Sie der `Page_Load`-Methode folgenden Code hinzu:

    ```vb
    Try
        ' Reference the Tasks list on the SharePoint site.
        ' Replace "TestServer" with a valid SharePoint server name.
        Dim site As SPSite = New SPSite("http://TestServer")
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")
        ' string text = "";
        Dim sum As Integer = 0
        Table1.Rows.Clear()
        ' Add table headers.
        Dim hr As TableHeaderRow = New TableHeaderRow
        hr.BackColor = Color.LightBlue
        Dim hc1 As TableHeaderCell = New TableHeaderCell
        Dim hc2 As TableHeaderCell = New TableHeaderCell
        hc1.Text = "Expense Report Name"
        hc2.Text = "Amount Exceeded"
        hr.Cells.Add(hc1)
        hr.Cells.Add(hc2)
        ' Add the TableHeaderRow as the first item
        ' in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr)
        ' Iterate through the tasks in the Task list and collect those
        ' that have values in the "Related Content" and "Outcome" fields
        ' - the fields written to when expense approval is required.
        For Each item As SPListItem In list.Items
            Dim s_relContent As String = ""
            Dim s_outcome As String = ""
            Try
                ' Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related Content")
                s_outcome = item.GetFormattedValue("Outcome")
            Catch erx As System.Exception
                ' Task does not have fields - skip it.
                Continue For
            End Try
            ' Convert amount to an int and keep a running total.
            If (Not String.IsNullOrEmpty(s_relContent) And Not
              String.IsNullOrEmpty(s_outcome)) Then
                sum = (sum + Convert.ToInt32(s_outcome))
                Dim relContent As TableCell = New TableCell
                relContent.Text = s_relContent
                Dim outcome As TableCell = New TableCell
                outcome.Text = ("$" + s_outcome)
                Dim dataRow2 As TableRow = New TableRow
                dataRow2.Cells.Add(relContent)
                dataRow2.Cells.Add(outcome)
                Table1.Rows.Add(dataRow2)
            End If
        Next
        ' Report the sum of the reports in the table footer.
        Dim tfr As TableFooterRow = New TableFooterRow
        tfr.BackColor = Color.LightGreen
        ' Create a TableCell object to contain the
        ' text for the footer.
        Dim ftc1 As TableCell = New TableCell
        Dim ftc2 As TableCell = New TableCell
        ftc1.Text = "TOTAL: "
        ftc2.Text = ("$" + Convert.ToString(sum))
        ' Add the TableCell object to the Cells
        ' collection of the TableFooterRow.
        tfr.Cells.Add(ftc1)
        tfr.Cells.Add(ftc2)
        ' Add the TableFooterRow to the Rows
        ' collection of the table.
        Table1.Rows.Add(tfr)
    Catch errx As Exception
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))
    End Try
    ```

    ```csharp
    try
    {
        // Reference the Tasks list on the SharePoint site.
        // Replace "TestServer" with a valid SharePoint server name.
        SPSite site = new SPSite("http://TestServer");
        SPList list = site.AllWebs[0].Lists["Tasks"];

        // string text = "";
        int sum = 0;

        Table1.Rows.Clear();

        // Add table headers.
        TableHeaderRow hr = new TableHeaderRow();
        hr.BackColor = Color.LightBlue;
        TableHeaderCell hc1 = new TableHeaderCell();
        TableHeaderCell hc2 = new TableHeaderCell();
        hc1.Text = "Expense Report Name";
        hc2.Text = "Amount Exceeded";
        hr.Cells.Add(hc1);
        hr.Cells.Add(hc2);
        // Add the TableHeaderRow as the first item
        // in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr);

        // Iterate through the tasks in the Task list and collect those
        // that have values in the "Related Content" and "Outcome"
        // fields - the fields written to when expense approval is
        // required.
        foreach (SPListItem item in list.Items)
        {
            string s_relContent = "";
            string s_outcome = "";

            try
            {
                // Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related
                  Content");
                s_outcome = item.GetFormattedValue("Outcome");
            }
            catch
            {
                // Task does not have fields - skip it.
                continue;
            }

            if (!String.IsNullOrEmpty(s_relContent) &&
              !String.IsNullOrEmpty(s_outcome))
            {
                // Convert amount to an int and keep a running total.
                sum += Convert.ToInt32(s_outcome);
                TableCell relContent = new TableCell();
                relContent.Text = s_relContent;
                TableCell outcome = new TableCell();
                outcome.Text = "$" + s_outcome;
                TableRow dataRow2 = new TableRow();
                dataRow2.Cells.Add(relContent);
                dataRow2.Cells.Add(outcome);
                Table1.Rows.Add(dataRow2);
            }
        }

        // Report the sum of the reports in the table footer.
           TableFooterRow tfr = new TableFooterRow();
        tfr.BackColor = Color.LightGreen;

        // Create a TableCell object to contain the
        // text for the footer.
        TableCell ftc1 = new TableCell();
        TableCell ftc2 = new TableCell();
        ftc1.Text = "TOTAL: ";
        ftc2.Text = "$" + Convert.ToString(sum);

        // Add the TableCell object to the Cells
        // collection of the TableFooterRow.
        tfr.Cells.Add(ftc1);
        tfr.Cells.Add(ftc2);

        // Add the TableFooterRow to the Rows
        // collection of the table.
        Table1.Rows.Add(tfr);
    }

    catch (Exception errx)
    {
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());
    }
    ```

    > [!WARNING]
    > Stellen Sie sicher, dass Sie "Testserver" im Code durch den Namen eines gültigen Servers ersetzen, auf dem SharePoint ausgeführt wird.

## <a name="test-the-application-page"></a>Testen der Anwendungsseite
 Überprüfen Sie als nächstes, ob die Abrechnungsdaten auf der Anwendungsseite ordnungsgemäß angezeigt werden.

#### <a name="to-test-the-application-page"></a>So testen Sie die Anwendungsseite

1. Drücken Sie die Taste **F5** , um das Projekt auszuführen und in SharePoint bereitzustellen.

2. Klicken Sie auf die Schaltfläche **Home** , und wählen Sie dann den Link frei **gegebene Dokumente** auf der Schnellstartleiste aus, um die Liste der freigegebenen Dokumente auf der SharePoint-Website anzuzeigen.

3. Um Ausgaben Berichte für dieses Beispiel darzustellen, laden Sie neue Dokumente in die Liste Dokumente hoch, indem Sie auf der Registerkarte **librarytools** oben auf der Seite auf den Link **Dokumente** klicken und dann im Menüband auf die Schaltfläche **Dokument hochladen** klicken.

4. Nachdem Sie einige Dokumente hochgeladen haben, instanziieren Sie den Workflow, indem Sie auf der Registerkarte **librarytools** oben auf der Seite den Link **Bibliothek** auswählen und dann im Menüband auf die Schaltfläche **Bibliotheks Einstellungen** klicken.

5. Wählen Sie auf der Seite " **Dokument Bibliotheks Einstellungen** " im Abschnitt " **Berechtigungen und Verwaltung** " den Link **Workflow Einstellungen** aus.

6. Wählen Sie auf der Seite **Workflow Einstellungen** den Link **Workflow hinzufügen** aus.

7. Wählen Sie auf der Seite **Workflow hinzufügen** den **ExpenseReport-Workflow1-** Workflow aus, geben Sie einen Namen für den Workflow ein, z. b. **expensetest**, und klicken Sie dann auf die Schaltfläche **weiter** .

    Das Formular für die Workflow Zuordnung wird angezeigt. Verwenden Sie es, um den Betrag der Ausgabenbeschränkung zu melden.

8. Geben Sie im Formular Association den Wert **1000** in das Feld **automatische Genehmigung** ein, und wählen Sie dann die Schaltfläche **Workflow zuordnen** aus.

9. Wählen Sie die **Start** Schaltfläche, um zur SharePoint-Startseite zurückzukehren.

10. Wählen Sie auf der Schnellstartleiste den Link frei **gegebene Dokumente** aus.

11. Wählen Sie eines der hochgeladenen Dokumente aus, um einen Dropdown Pfeil anzuzeigen, wählen Sie es aus, und wählen Sie dann das Element **Workflows** aus.

12. Wählen Sie das Bild neben dem expensetest aus, um das Workflow Initiierungs Formular anzuzeigen.

13. Geben Sie im Textfeld **Ausgaben gesamt** einen Wert ein, der größer als 1000 ist, und wählen Sie dann die Schaltfläche **Workflow starten** aus.

     Wenn eine gemeldete Ausgaben den zugeordneten Ausgabenbetrag überschreitet, wird dem Aufgabenliste eine Aufgabe hinzugefügt. Eine Spalte mit dem Namen **expensetest** mit dem Wert **abgeschlossen** wird auch dem Ausgaben Berichts Element in der Liste der freigegebenen Dokumente hinzugefügt.

14. Wiederholen Sie die Schritte 11-13 mit anderen Dokumenten in der Liste freigegebene Dokumente. (Die genaue Anzahl von Dokumenten ist nicht wichtig.)

15. Zeigen Sie die Anwendungsseite Zusammenfassung der Ausgaben Berichte an, indem Sie die folgende URL in einem Webbrowser öffnen: **http://**<em>Systemname</em>**/_layouts/ExpenseReport/ApplicationPage1.aspx**.

     Auf der Seite Zusammenfassung der Ausgaben Berichte werden alle Ausgaben Berichte aufgelistet, die den zugeordneten Betrag überschritten haben, den Betrag, um den Sie den Betrag überschritten haben, und den Gesamtbetrag für alle Berichte.

## <a name="next-steps"></a>Nächste Schritte
 Weitere Informationen zu SharePoint-Anwendungs Seiten finden Sie unter [Erstellen von Anwendungs Seiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

 In den folgenden Themen erfahren Sie mehr über das Entwerfen von SharePoint-Seiten Inhalten mithilfe des visuellen Web-Designers in Visual Studio:

- [Erstellen Sie Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Erstellen Sie wiederverwendbare Steuerelemente für Webparts oder Anwendungs Seiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Weitere Informationen

- [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [How to: Erstellen einer Anwendungsseite](../sharepoint/how-to-create-an-application-page.md)
- [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)