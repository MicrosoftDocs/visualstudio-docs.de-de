---
title: Erstellen eines Add-Ins für den Webleistungstest-Ergebnisviewer
description: Lernen Sie, ein Visual Studio-Add-In zum Erweitern der Benutzeroberfläche des Webleistungstest-Ergebnisviewers zu erstellen und die zum Erweitern der Benutzeroberfläche erforderlichen Klassen zu implementieren.
ms.custom: SEO-VS-2020
ms.date: 10/20/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b8fa3b83fb9a92be0118f4222e92364767affcda
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441077"
---
# <a name="how-to-create-an-add-in-for-the-web-performance-test-results-viewer"></a>Vorgehensweise: Erstellen eines Add-Ins für den Webleistungstest-Ergebnisviewer

Sie können die Benutzeroberfläche für den **Webleistungstest-Ergebnisviewer** mit den folgenden Namespaces erweitern:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>

Darüber hinaus müssen Sie einen Verweis auf die LoadTestPackage-DLL hinzufügen, die sich im Ordner *%ProgramFiles(x86)%\Microsoft Visual Studio\\\<version>\Enterprise\Common7\IDE\PrivateAssemblies* befindet.

Erstellen Sie zum Erweitern der Benutzeroberfläche des **Webleistungstest-Ergebnisviewers** ein Visual Studio-Add-In und ein Benutzersteuerelement. In den folgenden Prozeduren wird erläutert, wie das Add-In und das Benutzersteuerelement erstellt und die zum Erweitern der Benutzeroberfläche des **Webleistungstest-Ergebnisviewers** erforderlichen Klassen implementiert werden.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>Erstellen oder Öffnen einer Projektmappe, die eine ASP.NET-Webanwendung und ein Webleistungs- und Auslastungstestprojekt enthält

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>So bereiten Sie die Erweiterung des Webleistungstest-Ergebnisviewers vor

Erstellen oder öffnen Sie eine Projektmappe, bei der es sich nicht um eine Produktionsprojektmappe handelt, und mit der Sie experimentieren können. Diese Projektmappe sollte eine ASP.NET-Webanwendung und ein Webleistungs- und Auslastungstestprojekt mit mindestens einem Webleistungstest für die ASP.NET-Webanwendung enthalten.

> [!NOTE]
> Sie können eine ASP.NET-Webanwendung und ein Webleistungs- und Auslastungstestprojekt erstellen, das Webleistungstests enthält, indem Sie die Prozeduren unter [Vorgehensweise: Erstellen eines Webdiensttests](../test/how-to-create-a-web-service-test.md) und [Generieren und Ausführen eines codierten Webleistungstests](../test/generate-and-run-a-coded-web-performance-test.md) ausführen.

## <a name="create-a-visual-studio-add-in"></a>Erstellen eines Add-Ins für Visual Studio

Ein Add-In ist eine kompilierte DLL, die in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio ausgeführt wird. Durch die Kompilierung wird Ihr geistiges Eigentum geschützt und die Leistung verbessert. Sie können Add-Ins zwar manuell erstellen, aber es ist einfacher, dazu den **Add-In-Assistenten** zu verwenden. Mit diesem Assistenten wird ein voll funktionsfähiges und zugleich einfaches Add-In erstellt, das sofort nach dem Erstellen ausgeführt werden kann. Nachdem vom **Add-In-Assistenten** das grundlegende Programm erstellt wurde, können Sie Code hinzufügen und das Add-In anpassen.

Im **Add-In-Assistenten** können Sie einen Anzeigenamen und eine Beschreibung für das Add-In angeben. Beide werden im **Add-In-Manager** angezeigt. Sie können auch festlegen, dass der Assistent Code generiert, um dem Menü **Extras** einen Befehl zum Öffnen des Add-Ins hinzuzufügen. Sie können für das Add-In auch das benutzerdefinierte Dialogfeld **Info** anzeigen. Wenn der Assistent beendet ist, verfügen Sie über ein neues Projekt mit nur einer Klasse, über die das Add-In implementiert wird. Diese Klasse heißt "Connect".

Am Ende dieses Artikels verwenden Sie den **Add-In-Manager**.

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>So erstellen Sie mithilfe des Add-In-Assistenten ein Add-In

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, und wählen Sie **Hinzufügen** und anschließend **Neues Projekt** aus.

2. Erstellen Sie ein neues **Visual Studio-Add-In**-Projekt.

    Der **Add-In-Assistent** von Visual Studio wird geöffnet.

3. Wählen Sie **Weiter** aus.

4. Wählen Sie auf der Seite **Wählen Sie eine Programmiersprache aus** die Programmiersprache aus, die Sie zum Schreiben des Add-Ins verwenden möchten.

   > [!NOTE]
   > Dieses Thema verwendet Visual C# für den Beispielcode.

5. Wählen Sie auf der Seite **Wählen Sie einen Anwendungshost aus** die Option **Visual Studio** aus, und deaktivieren Sie **Visual Studio-Makros**.

6. Wählen Sie **Weiter** aus.

7. Geben Sie auf der Seite **Geben Sie einen Namen und eine Beschreibung ein** den Namen und die Beschreibung für das Add-In ein.

     Nachdem das Add-In erstellt wurde, werden Name und Beschreibung im **Add-In-Manager** in der Liste **Verfügbare Add-Ins** angezeigt. Geben Sie eine ausführliche Beschreibung an, sodass Benutzer direkt feststellen können, wozu das Add-In verwendet werden kann, wie es funktioniert usw.

8. Wählen Sie **Weiter** aus.

9. Wählen Sie auf der Seite **Wählen Sie die Add-In-Optionen aus** die Option **Das Add-In laden, wenn die Hostanwendung gestartet wird** aus.

10. Deaktivieren Sie die übrigen Kontrollkästchen.

11. Auf der Seite **Auswählen der Informationen unter „Info“ im Hilfemenü** können Sie angeben, ob im Dialogfeld **Info** Informationen zum Add-In angezeigt werden sollen. Wenn die Informationen angezeigt werden sollen, aktivieren Sie das Kontrollkästchen **Ja, für das Add-In sollen Informationen im Dialogfeld „Info“ angezeigt werden**.

     Zu den Informationen, die dem Dialogfeld **Info** von Visual Studio hinzugefügt werden können, zählen u.a. die Versionsnummer, Informationen zum Support und Lizenzangaben.

12. Wählen Sie **Weiter** aus.

13. Die von Ihnen ausgewählten Optionen werden auf der Seite **Zusammenfassung** angezeigt, damit Sie diese überprüfen können. Wenn Sie zufrieden sind, klicken Sie auf **Fertig stellen**, um das Add-In zu erstellen. Wenn Sie Änderungen vornehmen möchten, klicken Sie auf die Schaltfläche **Zurück**.

     Die neue Projektmappe und das neue Projekt werden erstellt, und die Datei *Connect.cs* für das neue Add-In wird im **Code-Editor** angezeigt.

     Sie fügen der Datei *Connect.cs* Code wie im folgenden Verfahren hinzu. Bei diesem Verfahren wird ein Benutzersteuerelement erstellt, auf das durch dieses WebPerfTestResultsViewerAddin-Projekt verwiesen wird.

    Nachdem ein Add-In erstellt wurde, müssen Sie es unter Visual Studio registrieren, bevor es im **Add-In-Manager** aktiviert werden kann. Dies wird mit einer XML-Datei mit der Erweiterung *.addin* erreicht.

    Diese *.addin*-Datei beschreibt die Informationen, die Visual Studio benötigt, um das Add-In im **Add-In-Manager** anzuzeigen. Beim Start von Visual Studio wird am Speicherort der *.addin*-Datei nach verfügbaren *.addin*-Dateien gesucht. Wenn eine solche XML-Datei gefunden wird, wird sie gelesen, und dem **Add-In-Manager** werden alle Informationen zur Verfügung gestellt, die nach einem entsprechenden Mausklick zum Starten des Add-Ins benötigt werden.

    Die *.addin*-Datei wird automatisch erstellt, wenn Sie ein Add-In mit dem **Add-In-Assistenten** erstellen.

### <a name="add-in-file-locations"></a>Speicherorte der Add-In-Datei

Zwei Kopien der *.addin*-Datei werden wie folgt automatisch vom **Add-In-Assistenten** erstellt:

|**Speicherort der ADDIN-Datei**|**Beschreibung**|
|-|----------------------------|-|
|Stammprojektordner|Wird zur Bereitstellung des Add-In-Projekts verwendet. Ist im Projekt enthalten, um die Bearbeitung zu erleichtern, und verfügt für die XCopy-Bereitstellung über den lokalen Pfad.|
|Add-In-Ordner|Wird zum Ausführen des Add-Ins in der Debugumgebung verwendet. Sollte immer auf den Ausgabepfad der aktuellen Buildkonfiguration zeigen.|

## <a name="create-a-windows-form-control-library-project"></a>Erstellen eines neuen Windows Forms-Steuerelementbibliothek-Projekts

Das in der vorherigen Prozedur erstellte Visual Studio-Add-In verweist auf ein Windows Forms-Steuerelementbibliothek-Projekt zum Erstellen einer Instanz einer <xref:System.Windows.Forms.UserControl>-Klasse.

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>So erstellen Sie ein Steuerelement, das im Webleistungstest-Ergebnisviewer verwendet werden soll

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, und wählen Sie **Hinzufügen** und anschließend **Neues Projekt** aus.

2. Erstellen Sie ein neues **Windows Forms-Steuerelementbibliothek**-Projekt.

3. Ziehen Sie <xref:System.Windows.Forms.DataGridView> aus der **Toolbox** auf die userControl1-Oberfläche.

4. Klicken Sie auf das Aktionstagsymbol (![Smarttag-Glyphe](../test/media/vs_winformsmttagglyph.gif)) in der oberen rechten Ecke von <xref:System.Windows.Forms.DataGridView>, und führen Sie die folgenden Schritte aus:

    1. Klicken Sie auf **In übergeordnetem Container andocken**.

    2. Deaktivieren Sie die Kontrollkästchen **Hinzufügen aktivieren**, **Bearbeiten aktivieren**, **Löschen aktivieren** und **Neuanordnung von Spalten aktivieren**.

    3. Klicken Sie auf **Spalte hinzufügen**.

         Das Dialogfeld **Spalte hinzufügen** wird angezeigt.

    4. Wählen Sie in der Dropdownliste **Typ** den Eintrag **DataGridViewTextBoxColumn** aus.

    5. Löschen Sie den Text „Column1“ in **Headertext**.

    6. Wählen Sie **Hinzufügen** aus.

    7. Klicken Sie auf **Schließen**.

5. Ändern Sie im **Eigenschaftenfenster** die Eigenschaft **(Name)** von <xref:System.Windows.Forms.DataGridView> in **resultControlDataGridView**.

6. Klicken Sie mit der rechten Maustaste auf der Designoberfläche, und wählen Sie **Code anzeigen** aus.

     Die Datei *UserControl1.cs* wird im **Code-Editor** angezeigt.

7. Ändern Sie den Namen der instanziierten <xref:System.Windows.Forms.UserControl>-Klasse von "UserContro1" zu "resultControl":

    ```csharp
    namespace WebPerfTestResultsViewerControl
    {
        public partial class resultControl : UserControl
        {
            public resultControl()
            {
                InitializeComponent();
            }
    ```

     In der nächsten Vorgehensweise fügen Sie Code zur Datei *Connect.cs* des WebPerfTestResultsViewerAddin-Projekts hinzu, die auf die resultControl-Klasse verweist.

     Sie fügen der Datei *Connect.cs* später weiteren Code hinzu.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>Hinzufügen von Code zu „WebPerfTestResultsViewerAddin“

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste im WebPerfTestResultsViewerAddin-Projekt auf den Knoten **Verweise**, und wählen Sie **Verweis hinzufügen** aus.

2. Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **.NET**.

3. Scrollen Sie nach unten, und wählen Sie **Microsoft.VisualStudio.QualityTools.WebTestFramework** und **System.Windows.Forms** aus.

4. Klicken Sie auf **OK**.

5. Klicken Sie mit der rechten Maustaste erneut auf den Knoten **Verweise**, und wählen Sie die Option **Verweis hinzufügen** aus.

6. Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **Durchsuchen**.

7. Klicken Sie auf die Dropdownschaltfläche für **Suchen in**, navigieren Sie zu *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*, und wählen Sie die Datei *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll* aus.

8. Klicken Sie auf **OK**.

9. Klicken Sie mit der rechten Maustaste auf den Knoten des WebPerfTestResultsViewerAddin-Projekts, und wählen Sie **Verweis hinzufügen** aus.

10. Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **Projekte**.

11. Wählen Sie unter **Projektname** das **Projekt WebPerfTestResultsViewerControl** aus, und klicken Sie auf **OK**.

12. Wenn die Datei *Connect.cs* im **Projektmappen-Explorer** immer noch nicht geöffnet ist, klicken Sie mit der rechten Maustaste im Projekt „WebPerfTestResultsViewerAddin“ auf die Datei **Connect.cs**, und wählen Sie **Code anzeigen** aus.

13. Fügen Sie der Datei *Connect.cs* die folgenden using-Anweisungen hinzu:

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. Scrollen Sie zum Ende der Datei *Connect.cs* herunter. Sie müssen eine Liste von GUIDs für <xref:System.Windows.Forms.UserControl> hinzufügen, falls mehrere Instanzen des **Webleistungstest-Ergebnisviewers** geöffnet sind. Sie fügen später Code hinzu, der diese Liste verwendet.

     Eine zweite Liste mit Zeichenfolgen wird in der OnDiscconection-Methode verwendet, die Sie später codieren werden.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. Die Datei *Connect.cs* instanziiert die Klasse „Connect“ in der <xref:Extensibility.IDTExtensibility2>-Klasse. Außerdem enthält sie einige Methoden zum Implementieren des Visual Studio-Add-Ins. Bei einer der Methoden handelt es sich um die OnConnections-Methode, die eine Benachrichtigung empfängt, dass das Add-In geladen wird. In der OnConnections-Methode erstellen Sie mithilfe der LoadTestPackageExt-Klasse das Erweiterbarkeitspaket für den **Webleistungstest-Ergebnisviewer**. Fügen Sie die folgenden Code zur Methode „OnConnection“ hinzu:

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. Fügen Sie der Connect-Klasse den folgenden Code hinzu, um die WebTestResultViewerExt_WindowCreated-Methode für den loadTestPackageExt.WebTestResultViewerExt.WindowCreated-Ereignishandler, den Sie in der OnConnections-Methode hinzugefügt haben, und für die WindowCreated-Methode, die von der WebTestResultViewerExt_WindowCreated-Methode aufgerufen wird, zu erstellen.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. Fügen Sie der Connect-Klasse den folgenden Code hinzu, um die WebTestResultViewer_SelectedChanged-Methode für den loadTestPackageExt.WebTestResultViewerExt.SelectionChanged-Ereignishandler zu erstellen, den Sie in der OnConnections-Methode hinzugefügt haben:

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. Fügen Sie der Connect-Klasse den folgenden Code hinzu, um die WebTesResultViewer_WindowClosed-Methode für den loadTestPackageExt.WebTestResultViewerExt.WindowClosed-Ereignishandler zu erstellen, den Sie in der OnConnections-Methode hinzugefügt haben:

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     Der Code für das Visual Studio-Add-In ist nun abgeschlossen. Sie müssen die Update-Methode zu resultControl im WebPerfTestResultsViewerControl-Projekt hinzufügen.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>Hinzufügen von Code WebPerfTestResultsViewerControl

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten des Projekts „WebPerfTestResultsViewerControl“, und wählen Sie **Eigenschaften** aus.

2. Klicken Sie auf die Registerkarte **Anwendung**, dann auf die Dropdownliste **Zielframework**, und wählen Sie **.NET Framework 4** (oder höher) aus. Schließen Sie das Fenster **Eigenschaften**.

   Dies ist erforderlich, damit die DLL-Verweise unterstützt werden, die zum Erweitern des **Webleistungstestergebnis-Viewers** erforderlich sind.

3. Klicken Sie im **Projektmappen-Explorer** im Projekt „WebPerfTestResultsViewerControl“ mit der rechten Maustaste auf den Knoten **Verweise**, und wählen Sie **Verweis hinzufügen** aus.

4. Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **.NET**.

5. Scrollen Sie nach unten, und wählen Sie **Microsoft.VisualStudio.QualityTools.WebTestFramework** aus.

6. Klicken Sie auf **OK**.

7. Fügen Sie der Datei *UserControl1.cs* die folgenden using-Anweisungen hinzu:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8. Fügen Sie die aufgerufene Update-Methode hinzu, die ein WebTestRequestResult-Objekt von der WebPerfTestResultsViewerAddin WebTestResultViewer_SelectedChanged-Methode in der Datei *Connect.cs* übergeben hat. Die Update-Methode füllt DataGridView mit verschiedenen Eigenschaften auf, die in WebTestRequestResult übergeben wurden.

    ```csharp
    public void Update(WebTestRequestResult WebTestResults)
            {
                // Clear the DataGridView when a request is selected.
                resultControlDataGridView.Rows.Clear();
                // Populate the DataGridControl with properties from the WebTestResults.
                this.resultControlDataGridView.Rows.Add("Request: " + WebTestResults.Request.Url.ToString());
                this.resultControlDataGridView.Rows.Add("Response: " + WebTestResults.Response.ResponseUri.ToString());
                foreach (RuleResult ruleResult in WebTestResults.ExtractionRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Extraction rule results: " + ruleResult.Message.ToString());
                }
                foreach (RuleResult ruleResult in WebTestResults.ValidationRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Validation rule results: " + ruleResult.Message.ToString());
                }
                foreach (WebTestError webTestError in WebTestResults.Errors)
                {
                    this.resultControlDataGridView.Rows.Add("Error: " + webTestError.ErrorType.ToString() + " " + webTestError.ErrorSubtype.ToString() + " " + webTestError.ExceptionText.ToString());
                }
            }
    ```

## <a name="build-the-solution"></a>Erstellen der Projektmappe

- Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>Registrieren des WebPerfTestResultsViewerAddin-Add-Ins

1. Klicken Sie im Menü **Extras** auf **Add-In-Manager**.

2. Das Dialogfeld **Add-In-Manager** wird angezeigt.

3. Aktivieren Sie in der Spalte **Verfügbare Add-Ins** das Kontrollkästchen des Add-Ins „WebPerfTestResultsViewerAddin“, und deaktivieren Sie die Kontrollkästchen in den Spalten **Start** und **Befehlszeile**.

4. Klicken Sie auf **OK**.

## <a name="run-the-web-performance-test-using-the-web-test-results-viewer"></a>Ausführen des Webleistungstest mit dem Webleistungstest-Ergebnisviewer

1. Führen Sie den Webleistungstest aus. Im **Webleistungstest-Ergebnisviewer** wird die neue Registerkarte „Beispiel“ des WebPerfTestResultsViewerAddin-Add-Ins angezeigt.

2. Wählen Sie die Registerkarte, um die in DataGridView enthaltenen Eigenschaften anzuzeigen.

## <a name="net-security"></a>.NET-Sicherheit

Um die Sicherheit dadurch zu optimieren, dass böswillige Add-Ins nicht automatisch aktiviert werden können, stellt Visual Studio im Menü **Extras** auf der Optionsseite **Add-In/Makrosicherheit** entsprechende Einstellungen bereit.

Außerdem können Sie auf dieser Seite die Ordner festlegen, in denen Visual Studio nach *.AddIn*-Registrierungsdateien suchen soll. Dadurch wird die Sicherheit erhöht, da Sie die Speicherorte beschränken können, an denen *.AddIn*-Registrierungsdateien gelesen werden können. Dadurch wird die unabsichtliche Verwendung schädlicher *.AddIn*-Dateien verhindert.

**Einstellungen für die Add-In-Sicherheit**

Folgende Einstellungen befinden sich auf der Optionsseite für die Sicherheit von Add-Ins:

- **Allow Add-in components to load.** (Laden von Add-In-Komponenten zulassen.) Standardmäßig ausgewählt. Wenn das Kontrollkästchen aktiviert ist, können Add-Ins in Visual Studio geladen werden. Wenn das Kontrollkästchen deaktiviert ist, können keine Add-Ins in Visual Studio geladen werden.

- **Allow Add-in components to load from a URL.** (Laden von Add-In-Komponenten von einer URL zulassen.) Standardmäßig nicht ausgewählt. Wenn das Kontrollkästchen aktiviert ist, können Add-Ins von externen Websites geladen werden. Wenn das Kontrollkästchen deaktiviert ist, können keine Remote-Add-Ins in Visual Studio geladen werden. Wenn aus irgendeinem Grund ein Add-In nicht geladen werden kann, dann kann es auch nicht aus dem Web geladen werden. Diese Einstellung steuert lediglich das Laden der Add-In-DLL. Die *.Addin*-Registrierungsdateien müssen sich immer auf dem lokalen System befinden.

## <a name="see-also"></a>Siehe auch

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Erstellen von benutzerdefiniertem Code und benutzerdefinierten Plug-Ins für Auslastungstests](../test/create-custom-code-and-plug-ins-for-load-tests.md)
