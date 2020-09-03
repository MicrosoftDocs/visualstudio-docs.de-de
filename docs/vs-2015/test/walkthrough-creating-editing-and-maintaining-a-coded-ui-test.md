---
title: 'Exemplarische Vorgehensweise: Erstellen, Bearbeiten und Verwalten von Tests der programmierten UI | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f7c25ba7-5c9c-455b-9242-701cda56f90c
caps.latest.revision: 43
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 900a241549cd499437ee25d8f57ed66c0c958a17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586902"
---
# <a name="walkthrough-creating-editing-and-maintaining-a-coded-ui-test"></a>Exemplarische Vorgehensweise: Erstellen, Bearbeiten und Verwalten von Tests der programmierten UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise erstellen Sie eine einfache Windows Presentation Foundation (WPF)-Anwendung, um das Erstellen, Bearbeiten und Verwalten eines Tests der programmierten UI zu veranschaulichen. Die exemplarische Vorgehensweise umfasst Lösungen zum Korrigieren von Tests, die aufgrund verschiedener Probleme mit den Zeitabläufen und des Steuerelementrefactorings nicht mehr funktionieren.

## <a name="prerequisites"></a>Voraussetzungen
 Für diese exemplarische Vorgehensweise benötigen Sie:

- Visual Studio Enterprise

### <a name="create-a-simple-wpf-application"></a>Erstellen einer einfachen WPF-Anwendung

1. Zeigen Sie im Menü **Datei** auf **neu**, und wählen Sie dann **Projekt**aus.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Erweitern Sie im Bereich **Installiert** den Eintrag **Visual C#**, und wählen Sie **Windows Desktop** aus.

3. Stellen Sie sicher, dass die Dropdownliste für das Zielframework über dem mittleren Bereich auf **.NET Framework 4.5** festgelegt ist.

4. Wählen Sie im mittleren Bereich die Vorlage **WPF-Anwendung** aus.

5. Geben Sie im Textfeld **Name** den Namen **SimpleWPFApp** ein.

6. Wählen Sie einen Ordner zum Speichern des Projekts aus. Geben Sie im Textfeld **Speicherort** den Namen des Ordners ein.

7. Klicken Sie auf **OK**.

     Der WPF-Designer für Visual Studio wird geöffnet und zeigt das MainWindow-Element des Projekts an.

8. Öffnen Sie die Toolbox, sofern sie nicht geöffnet ist. Wählen Sie das Menü **Ansicht** und dann **Toolbox**aus.

9. Ziehen Sie unter dem Abschnitt **Alle WPF-Steuerelemente** ein **Button**-, ein **CheckBox**- und ein **ProgressBar**-Steuerelement auf das MainWindow-Element in der Entwurfsoberfläche.

10. Wählen Sie das Button-Steuerelement aus. Ändern Sie in der Eigenschaftenfenster den Wert für die **Name** -Eigenschaft von \<No Name> in button1. Ändern Sie den Wert für die Eigenschaft **Content** von „Button“ in „Start“.

11. Wählen Sie das ProgressBar-Steuerelement aus. Ändern Sie in der Eigenschaftenfenster den Wert für den Wert für die **Name** -Eigenschaft von \<No Name> in "progressBar1". Ändern Sie dann den Wert für die Eigenschaft **Maximum** von **100** auf **10000**.

12. Wählen Sie das Checkbox-Steuerelement aus. Ändern Sie in der Eigenschaftenfenster den Wert für die **Name** -Eigenschaft von \<No Name> in CheckBox1, und löschen Sie die **isaktivierte** -Eigenschaft.

     ![Einfache WPF-Anwendung](../test/media/codedui-wpfapp.png "CodedUI_WPFApp")

13. Doppelklicken Sie auf das Schaltflächen-Steuerelement, um einen Click-Ereignishandler hinzuzufügen.

     "MainWindow.xmal.cs" wird im Code-Editor angezeigt, und der Cursor ist in der neuen button1_Click-Methode positioniert.

14. Fügen Sie am oberen Rand der MainWindow-Klasse einen Delegaten hinzu. Der Delegat wird für die Statusanzeige verwendet. Fügen Sie den Delegaten mit dem folgenden Code hinzu:

    ```csharp
    public partial class MainWindow : Window
    {
            private delegate void ProgressBarDelegate(System.Windows.DependencyProperty dp, Object value);

        public MainWindow()
        {

            InitializeComponent();
        }

    ```

15. Fügen Sie folgenden Code in die button1_Click-Methode ein:

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        double progress = 0;

        ProgressBarDelegate updatePbDelegate =
            new ProgressBarDelegate(progressBar1.SetValue);

        do
        {
            progress ++;

            Dispatcher.Invoke(updatePbDelegate,
                System.Windows.Threading.DispatcherPriority.Background,
                new object[] { ProgressBar.ValueProperty, progress });
            progressBar1.Value = progress;
        }
        while (progressBar1.Value != progressBar1.Maximum);

        checkBox1.IsEnabled = true;
    }

    ```

16. Speichern Sie die Datei.

### <a name="verify-the-wpf-application-runs-correctly"></a>Überprüfen der ordnungsgemäßen Ausführung der WPF-Anwendung

1. Wählen Sie im Menü **Debuggen** die Option **Debugging starten** aus, oder drücken Sie **F5**.

2. Beachten Sie, dass das Steuerelement Kontrollkästchen deaktiviert ist. Wählen Sie **Start** aus.

     Die Statusanzeige sollte innerhalb einiger Sekunden vollständig abgeschlossen sein.

3. Sie können jetzt das Steuerelement Kontrollkästchen auswählen.

4. Schließen Sie "SimpleWPFApp".

### <a name="create-and-run-a-coded-ui-test-for-simplewpfapp"></a>Erstellen und Ausführen eines Tests der codierten UI für "SimpleWPFApp"

1. Suchen Sie die zuvor erstellte Anwendung "SimpleWPFApp". Standardmäßig befindet sich die Anwendung unter c:\Users \\<username \> \Documents\Visual Studio \<version>\Projects\SimpleWPFApp\SimpleWPFApp\bin\Debug\SimpleWPFApp.exe

2. Erstellen Sie eine Desktopverknüpfung zur SimpleWPFApp-Anwendung. Klicken Sie mit der rechten Maustaste auf SimpleWPFApp.exe, und wählen Sie **Kopieren** aus. Klicken Sie auf dem Desktop mit der rechten Maustaste, und wählen Sie die Option **Verknüpfung einfügen** aus.

    > [!TIP]
    > Über eine Verknüpfung zur Anwendung können Tests der programmierten UI für die Anwendung leichter hinzugefügt und geändert werden, da die Anwendung schnell gestartet werden kann.

3. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf die Projekt Mappe, und wählen Sie **Hinzufügen** und dann **Neues Projekt**aus.

     Das Dialogfeld **Neues Projekt hinzufügen** wird angezeigt.

4. Erweitern Sie im Bereich **Installiert** den Eintrag **Visual C#**, und wählen Sie **Test** aus.

5. Wählen Sie im mittleren Bereich die Vorlage **Testprojekt der programmierten UI** aus.

6. Klicken Sie auf **OK**.

     In Projektmappen-Explorer wird das neue Testprojekt der programmierten UI mit der Bezeichnung **CodedUITestProject1** der Lösung hinzugefügt.

     Das Dialogfeld **Code für den Test der programmierten UI generieren** wird angezeigt.

7. Wählen Sie die Option **Aktionen aufzeichnen, UI-Zuordnung bearbeiten oder Assertionen hinzufügen** aus, und klicken Sie auf **OK**.

     Der UIMap – Test-Generator der programmierten UI wird angezeigt, und das Visual Studio-Fenster wird minimiert.

     Weitere Informationen zu den Optionen im Dialogfeld finden Sie unter [Erstellen von Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

8. Klicken Sie auf dem „UIMap – Test-Generator der programmierten UI“ auf **Aufzeichnung starten**.

     ![Aufzeichnung starten](../test/media/cuit-builder-record.png "CUIT_Builder_Record")

     Sie können die Aufzeichnung bei Bedarf anhalten, etwa wenn Sie eine eingehende E-Mail lesen möchten.

     ![Aufzeichnung anhalten](../test/media/cuit.png "CUIT_")

    > [!WARNING]
    > Alle auf dem Desktop ausgeführten Aktionen werden aufgezeichnet. Halten Sie die Aufzeichnung an, wenn Sie Aktionen ausführen, bei denen sensible Daten in die Aufzeichnung gelangen könnten.

9. Starten Sie SimpleWPFApp mithilfe der Desktopverknüpfung.

     Beachten Sie wie bereits zuvor, dass das Steuerelement Kontrollkästchen deaktiviert ist.

10. Klicken Sie in SimpleWPFApp auf **Start**.

     Die Statusanzeige sollte innerhalb einiger Sekunden vollständig abgeschlossen sein.

11. Aktivieren Sie das Kontrollkästchen-Steuerelement, das jetzt aktiviert ist.

12. Schließen Sie die SimpleWPFApp-Anwendung.

13. Wählen Sie im UIMap-Coded UI-Test-Generator **Code generieren**aus.

14. Geben Sie im Feld "Methodenname" den Namen **SimpleAppTest** ein, und klicken Sie auf **Hinzufügen und generieren**. Der Test der programmierten UI wird nach wenigen Sekunden angezeigt und der Projektmappe hinzugefügt.

15. Schließen Sie den UIMap – Test-Generator für codierte UI.

     Die Datei "CodedUITest1.cs" wird im Code-Editor geöffnet.

16. Speichern Sie das Projekt.

### <a name="run-the-coded-ui-test"></a>Ausführen des Tests der programmierten UI

1. Wählen Sie im Menü **Test** die Option **Fenster** aus, und wählen Sie dann **Test-Explorer**aus.

2. Wählen Sie im Menü **Erstellen** die Option Projekt Mappe **Erstellen**aus.

3. Suchen Sie in der Datei CodedUITest1.cs die **codeduitestmethod** -Methode, klicken Sie mit der rechten Maustaste, und wählen Sie **Tests ausführen**aus, oder führen Sie den Test im Test-Explorer aus.

     Während der Test der programmierten UI ausgeführt wird, wird „SimpleWPFApp“ angezeigt. Die Schritte, die Sie in der vorherigen Prozedur ausgeführt haben, werden ausgeführt. Beim Versuch, das Kontrollkästchen für das Kontrollkästchen-Steuerelement zu aktivieren, wird jedoch im Fenster "Testergebnisse" angezeigt, dass der Test fehlgeschlagen ist. Dies liegt daran, dass beim Test versucht wird, das Kontrollkästchen zu aktivieren, obwohl das Kontrollkästchen-Steuerelement deaktiviert ist, bis die Statusanzeige 100 Prozent abgeschlossen ist. Sie können dieses und ähnliche Probleme mit den `UITestControl.WaitForControlXXX()`-Methoden korrigieren, die für Tests der codierten UI verfügbar sind. Bei der nächsten Prozedur wird veranschaulicht, wie Sie das Problem, das bei diesem Test zu einem Fehler geführt hat, mit der `WaitForControlEnabled()`-Methode korrigieren können. Weitere Informationen finden Sie unter festlegen, dass Tests der programmierten UI bei der [Wiedergabe auf bestimmte Ereignisse warten](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

### <a name="edit-and-rerun-the-coded-ui-test"></a>Bearbeiten und erneutes Ausführen des Tests der programmierten UI

1. Wählen Sie im Test-Explorer den fehlgeschlagenen Test aus, und klicken Sie im Abschnitt **StackTrace** auf den ersten Link zu **UIMap.SimpleAppTest()**.

2. Die Datei "UIMap.Designer.cs" wird geöffnet. Die fehlerhafte Stelle wird im Code hervorgehoben:

    ```csharp

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3. Um dieses Problem zu korrigieren, können Sie mithilfe der `WaitForControlEnabled()`-Methode festlegen, dass beim Test der codierten UI gewartet werden soll, bis das CheckBox-Steuerelement aktiviert ist, bevor mit dieser Zeile fortgefahren wird.

    > [!WARNING]
    > Ändern Sie die Datei "UIMap.Designer.cs" nicht. Alle Codeänderungen, die Sie an der Datei "UIMapDesigner.cs" vornehmen, werden jedes Mal überschrieben, wenn Sie Code mit dem UIMap – Test-Generator für codierte UI generieren. Wenn Sie eine aufgezeichnete Methode ändern müssen, müssen Sie sie in die UIMap.cs-Datei kopieren und umbenennen. Die Datei "UIMap.cs" kann verwendet werden, um Methoden und Eigenschaften in der Datei "UIMapDesigner.cs" zu überschreiben. Sie müssen den Verweis auf die ursprüngliche Methode in der Datei "Coded UITest.cs" entfernen und ihn durch den umbenannten Methodennamen ersetzen.

4. Suchen Sie in Projektmappen-Explorer nach **UIMap. UITest** im Testprojekt der programmierten UI.

5. Öffnen Sie das Kontextmenü **UIMap.uitest**, und wählen Sie **Öffnen** aus.

     Der Test der codierten UI wird im Editor für den Test der codierten UI angezeigt. Sie können nun den Test der programmierten UI anzeigen und bearbeiten.

6. Wählen Sie im Bereich **UI-Aktion** die Testmethode(SimpleAppTest) aus, die Sie in die Datei „UIMap.cs“ oder „UIMap.vb“ verschieben möchten. Dadurch vereinfachen Sie die Funktion für benutzerdefinierten Code, die beim erneuten Kompilieren des Tests nicht überschrieben wird.

7. Klicken Sie auf der Symbolleiste des Editors für den Test der programmierten UI auf die Schaltfläche **Code verschieben**.

8. Ein Microsoft Visual Studio-Dialogfeld wird angezeigt. Sie werden darauf hingewiesen, dass die Methode aus der UIMap.uitest-Datei in die Datei „UIMap.cs“ verschoben wird, und dass die Methode mit dem Editor für Tests der programmierten UI nicht mehr bearbeitet werden kann. Klicken Sie auf **Ja**.

     Die Testmethode wird aus der UIMap.uitest-Datei entfernt und nicht mehr im Bereich der UI-Aktionen angezeigt. Öffnen Sie zum Bearbeiten der verschobenen Testdatei die Datei "UIMap.cs" mit Projektmappen-Explorer.

9. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Wählen Sie auf der Symbolleiste **Speichern**aus.

     Die Aktualisierungen der Testmethode werden in der UIMap.Designer-Datei gespeichert.

    > [!CAUTION]
    > Nach dem Verschieben der Methode kann sie mit dem Editor für Tests der codierten UI nicht mehr bearbeitet werden. Sie müssen den benutzerdefinierten Code hinzufügen und ihn mit dem Code-Editor verwalten.

10. Benennen Sie die Methode von `SimpleAppTest()` in `ModifiedSimpleAppTest()` um.

11. Fügen Sie der Datei die folgende using-Anweisung hinzu:

    ```csharp

    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;

    ```

12. Fügen Sie die folgende `WaitForControlEnabled()`-Methode vor der Codezeile ein, die zuvor als Fehlerquelle ermittelt wurde:

    ```csharp

              uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;

    ```

13. Suchen Sie in der Datei CodedUITest1.cs die Methode **CodedUITestMethod**, und kommentieren Sie den Verweis auf die ursprüngliche Methode „SimpleAppTest()“ aus, oder benennen Sie ihn um. Ersetzen Sie ihn dann durch die neue Methode „ModifiedSimpleAppTest()“:

    ```csharp
    [TestMethod]
            public void CodedUITestMethod1()
            {
                // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
                // For more information on generated code, see http://go.microsoft.com/fwlink/?LinkId=179463
                //this.UIMap.SimpleAppTest();
                this.UIMap.ModifiedSimpleAppTest();
            }

    ```

14. Wählen Sie im Menü **Erstellen** die Option Projekt Mappe **Erstellen**aus.

15. Klicken Sie mit der rechten Maustaste auf die **CodedUITestMethod**-Methode, und wählen Sie **Tests ausführen** aus.

16. Dieses **Mal führt der** Test der programmierten UI alle Schritte im Test erfolgreich aus, und die Ausführung wird im Fenster "Test-Explorer" angezeigt.

### <a name="refactor-a-control-in-the-simplewpfapp"></a>Umgestalten eines Steuerelements in "SimpleWPFApp"

1. Wählen Sie in der Datei "MainWindow.xaml" im Designer das Schaltflächen-Steuerelement aus.

2. Ändern Sie am oberen Rand der Eigenschaftenfenster den **Name** -Eigenschafts Wert von button1 in buttona.

3. Wählen Sie im Menü **Erstellen** die Option Projekt Mappe **Erstellen**aus.

4. Führen Sie **CodedUITestMethod1**in Test-Explorer aus.

     Der Test schlägt fehl, da der Test der programmierten UI das Schaltflächen-Steuerelement, das ursprünglich im UIMap als „button1“ zugeordnet wurde, nicht finden kann. Auf diese Weise kann sich die Umgestaltung auf Tests der programmierten UI auswirken.

5. Wählen Sie im Fenster „Test-Explorer“ im Abschnitt **StackTrace** den ersten Link zu **UIMpa.ModifiedSimpleAppTest()** aus.

     Die Datei "UIMap.cs" wird geöffnet. Die fehlerhafte Stelle wird im Code hervorgehoben:

    ```csharp

    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Beachten Sie, dass in der Codezeile dieser Prozedur zuvor `UiStartButton` verwendet wurde. Dies war der UIMap-Name vor der Umgestaltung.

     Zur Behebung des Problems können Sie dem UIMap das umgestaltete Steuerelement mit dem Test-Generator für codierte UI hinzufügen. Sie können den Code des Tests wie in der nächsten Prozedur veranschaulicht aktualisieren.

### <a name="map-refactored-control-and-edit-and-rerun-the-coded-ui-test"></a>Zuordnen des umgestalteten Steuerelements und Bearbeiten und erneutes Ausführen des Tests der programmierten UI

1. Klicken Sie in der Datei CodedUITest1.cs in der Methode **CodedUITestMethod1()** mit der rechten Maustaste, wählen Sie **Code für den Test der programmierten UI generieren** aus, und klicken Sie dann auf **Use Coded UI Test Builder** (Generator für Tests der programmierten UI verwenden).

     Der UIMap – Test-Generator der programmierten UI wird angezeigt.

2. Führen Sie mithilfe der zuvor erstellten Desktopverknüpfung die Anwendung "SimpleWPFApp" aus, die Sie ebenfalls zuvor erstellt haben.

3. Ziehen Sie auf dem UIMap – Test-Generator für programmierte UI das Fadenkreuztool auf die Schaltfläche **Start** in „SimpleWPFApp“.

     Die Schaltfläche **Start** ist mit einem blauen Rahmen versehen, und der Test-Generator der programmierten UI braucht einige Sekunden, um die Daten für das ausgewählte Steuerelement zu verarbeiten. Dann werden die Steuerelementeigenschaften angezeigt. Beachten Sie, dass **AutomationUId** die Bezeichnung **buttonA** trägt.

4. Klicken Sie in den Eigenschaften für das Steuerelement auf den Pfeil in der linken oberen Ecke, um die UI-Steuerelementzuordnung zu erweitern. Beachten Sie, dass **UIStartButton1** ausgewählt ist.

5. Klicken Sie auf der Symbolleiste auf **Steuerelement zu UI-Steuerelementzuordnung hinzufügen**.

     Durch den Status am unteren Rand des Fensters wird die Aktion bestätigt, indem **Das ausgewählte Steuerelement wurde der UI-Steuerelementzuordnung hinzugefügt** angezeigt wird.

6. Klicken Sie auf dem „UIMap – Test-Generator der programmierten UI“ auf **Code generieren**.

     Das Dialogfeld „Test-Generator der programmierten UI – Code generieren“ wird mit einem Hinweis angezeigt, dass keine neue Methode erforderlich ist und dass Code nur für die Änderungen an der UI-Steuerelementzuordnung generiert wird.

7. Wählen Sie **Generieren** aus.

8. Schließen Sie "SimpleWPFApp.exe".

9. Schließen Sie "UIMap – Test-Generator für codierte UI".

     "UIMap – Test-Generator für codierte UI" benötigt einige Sekunden für die Verarbeitung der Änderungen an den UI-Steuerelementzuordnungen.

10. Öffnen Sie im Projektmappen-Explorer die Datei "UIMap.Designer.cs".

11. Suchen Sie in der Datei "UIMap.Designer.cs" die Eigenschaft "UIStartButton1". Beachten Sie, dass `SearchProperties` auf `"buttonA"` festgelegt ist:

    ```csharp

    public WpfButton UIStartButton1
            {
                get
                {
                    if ((this.mUIStartButton1 == null))
                    {
                        this.mUIStartButton1 = new WpfButton(this);
                        #region Search Criteria
                        this.mUIStartButton1.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
                        this.mUIStartButton1.WindowTitles.Add("MainWindow");
                        #endregion
                    }
                    return this.mUIStartButton1;
                }
            }

    ```

     Jetzt können Sie den Test der codierten UI ändern, um das neu zugeordnete Steuerelement zu verwenden. Wie in der vorherigen Prozedur angemerkt wurde, können Sie Methoden oder Eigenschaften im Test der codierten UI nur in der Datei "UIMap.cs" überschreiben.

12. Fügen Sie in der Datei "UIMap.cs" einen Konstruktor hinzu, und geben Sie die `SearchProperties`-Eigenschaft der `UIStartButton`-Eigenschaft an, um die `AutomationID`-Eigenschaft mit dem Wert `"buttonA":` zu verwenden.

    ```csharp

    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }

    ```

13. Wählen Sie im Menü **Erstellen** die Option Projekt Mappe **Erstellen**aus.

14. Führen Sie CodedUITestMethod1 in Test-Explorer aus.

     Dieses Mal führt der Test der programmierten UI alle Schritte im Test erfolgreich aus.  Im Fenster „Testergebnisse“ wird der Status **Erfolgreich** angezeigt.

## <a name="external-resources"></a>Externe Ressourcen

### <a name="videos"></a>Videos
 ![Link zu Video](../data-tools/media/playvideo.gif "Wiedergeben") [Coded UI Tests-deepdive-Episode1-GettingStarted](https://skydrive.live.com/?cid=2db0e1efe1c1d3b8&id=2DB0E1EFE1C1D3B8%21118)

 ![Link zu Video](../data-tools/media/playvideo.gif "Wiedergeben") [Coded UI Tests-deepdive-Episode2-wart-ceanddebugging](https://skydrive.live.com/?cid=2db0e1efe1c1d3b8&id=2DB0E1EFE1C1D3B8%21116)

 ![Link zu Video](../data-tools/media/playvideo.gif "Wiedergeben") [Coded UI Tests-deepdive-Episode3-handcoding](https://skydrive.live.com/?cid=2db0e1efe1c1d3b8&id=2DB0E1EFE1C1D3B8%21117)

### <a name="hands-on-lab"></a>Praktische Übungseinheiten
 [MSDN Virtual Lab: Introduction to Creating Coded UI Tests with Visual Studio 2010 (MSDN Virtual Lab: Einführung in die Erstellung programmierter UI-Tests mit Visual Studio 2010)](https://windows.microsoft.com/en-US/windows/products/windows-media-player)

### <a name="faq"></a>Häufig gestellte Fragen
 [Tests der codierten UI – FAQ 1](https://docs.microsoft.com/archive/blogs/mathew_aniyan/content-index-for-coded-ui-test)

 [Tests der codierten UI – FAQ 2](https://social.msdn.microsoft.com/Forums/en-US/vsautotest/thread/3a74dd2c-cef8-4923-abbf-7a91f489e6c4)

### <a name="forum"></a>Forum
 [Tests der Benutzeroberflächenautomatisierung (einschließlich programmierte UI) in Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/vsautotest)

## <a name="see-also"></a>Weitere Informationen
 [Verwenden von Benutzeroberflächen Automatisierung zum Testen](../test/use-ui-automation-to-test-your-code.md) [des Codes Einstieg in den WPF-Designer](https://msdn.microsoft.com/18e61d03-b96a-4058-a166-8ec6b3f6116b) [unterstützte Konfigurationen und Plattformen für Tests der programmierten UI und Aktions Aufzeichnungen](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) [Bearbeiten von Tests der programmierten UI mit dem Editor](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md) für Tests
