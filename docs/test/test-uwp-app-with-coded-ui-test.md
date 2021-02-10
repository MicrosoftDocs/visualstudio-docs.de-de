---
title: Testen einer UWP-App mit einem Test der programmierten UI
description: Hier erfahren Sie, wie Sie einen Test der programmierten UI für eine App der Universellen Windows-Plattform (UWP) erstellen, indem Sie eine UWP-App zum Testen und Erstellen eines Tests der programmierten UI erstellen.
ms.custom: SEO-VS-2020
ms.date: 05/31/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: 0fb60de87fa98e4715d872512c120a408ec8339e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911523"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>Erstellen eines Tests der programmierten UI zum Testen einer UWP-App

In diesem Artikel wird erläutert, wie Sie einen Test der programmierten UI für eine UWP-App (Universelle Windows-Plattform) erstellen.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>Erstellen einer zu testenden UWP-App

Zunächst müssen Sie eine einfache UWP-App erstellen, die getestet werden kann.

1. Erstellen Sie in Visual Studio ein neues Projekt mithilfe der Vorlage **Leere App (Universelle Windows-App)** für Visual C# oder Visual Basic.

   ::: moniker range="vs-2017"

   ![Vorlage „Leere App (Universelle Windows-App)“](../test/media/blank-uwp-app-template.png)

   ::: moniker-end

1. Klicken Sie im Dialogfeld **Neues UWP-Projekt (Universelle Windows-Plattform)** auf **OK**, um die Standardplattformversionen zu akzeptieren.

1. Öffnen Sie im **Projektmappen-Explorer** die Datei *MainPage.xaml*.

   Die Datei wird im **XAML-Designer** geöffnet.

1. Ziehen Sie aus der **Toolbox** ein Schaltflächen- und ein Textfeld-Steuerelement auf die Entwurfsoberfläche.

     ![Entwerfen der UWP-App](../test/media/toolbox-controls.png)

1. Benennen Sie die Steuerelemente. Wählen Sie das Textfeld-Steuerelement aus, und geben Sie im **Eigenschaftenfenster** im Feld **Name****textBox** ein. Wählen Sie das Schaltflächen-Steuerelement aus, und geben Sie im **Eigenschaftenfenster** im Feld **Name****button** ein.

1. Doppelklicken Sie auf das Schaltflächen-Steuerelement, und fügen Sie folgenden Code zur `Button_Click`-Methode hinzu. Dieser Code legt den Text im Textfeld auf den Namen des Schaltflächen-Steuerelements fest. Dies kann mit dem Test der programmierten UI überprüft werden, der noch erstellt wird.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. Drücken Sie **STRG**+**F5**, um die App auszuführen. Folgendes sollte angezeigt werden:

   ![UWP-App mit Schaltfläche und Textfeld](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>Test der codierten UI erstellen

1. Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf die Projektmappe und dann auf **Hinzufügen** > **Neues Projekt**, um ein Testprojekt zur Projektmappe hinzuzufügen.

1. Suchen Sie die Vorlage **Testprojekt der programmierten UI (Universelles Windows)**, und wählen Sie sie aus.

   ::: moniker range="vs-2017"

   ![Neues Testprojekt der programmierten UI](../test/media/coded-ui-test-project-uwp-template.png)

   ::: moniker-end

   > [!NOTE]
   > Wenn Ihnen die Vorlage **Testprojekt der programmierten UI (Universelles Windows)** nicht angezeigt wird, müssen Sie die Komponente [Test der programmierten UI](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component) installieren.

1. Klicken Sie im Dialogfeld **Generate Code for Coded UI Test** (Code für Tests der programmierten UI generieren) auf **Test manuell bearbeiten**.

   ![Dialogfeld „Code für Tests der programmierten UI generieren“](../test/media/manually-edit-the-test.png)

1. Wenn Ihre UWP-App noch nicht ausgeführt wird, starten Sie diese, indem Sie **STRG**+**F5** drücken.

1. Öffnen Sie das Dialogfeld **Coded UI Test Builder** (Generator für Tests der programmierten UI), indem Sie den Cursor in die `CodedUITestMethod1`-Methode steuern und anschließend auf **Test** > **Generate Code for Coded UI Test** > **Use Coded UI Test Builder** (Test > Code für Tests der programmierten UI generieren > Generator für Tests der programmierten UI verwenden) klicken.

1. Fügen Sie die Steuerelemente zur UI-Steuerelementzuordnung hinzu. Verwenden Sie das Fadenkreuztool **Coded UI Test Builder** (Generator für Tests der programmierten UI), um das Schaltflächen-Steuerelement in der UWP-App auszuwählen. Erweitern Sie im Dialogfeld **Assertionen hinzufügen** bei Bedarf den Bereich **UI-Steuerelementzuordnung**, und klicken Sie anschließend auf **Steuerelement zu UI-Steuerelementzuordnung hinzufügen**.

     ![UI-Zuordnung ein Steuerelement hinzufügen](../test/media/add-control-to-ui-control-map.png)

1. Wiederholen Sie den vorangehenden Schritt, um das Textfeld-Steuerelements zur UI-Steuerelementzuordnung hinzuzufügen.

1. Klicken Sie im Dialogfeld **Coded UI Test Builder** (Generator für Tests der programmierten UI) auf **Code generieren**, oder drücken Sie **STRG**+**G**. Klicken Sie dann auf **Generieren**, um Code für Änderungen an der UI-Steuerelementzuordnung zu erstellen.

     ![Code für die UI-Zuordnung generieren](../test/media/generate-code-dialog.png)

1. Klicken Sie auf die Schaltfläche, um zu überprüfen, der Text im Textfeld sich in **button** ändert, wenn auf die Schaltfläche geklickt wird.

     ![Zum Festlegen des Werts im Textfeld auf das Schaltflächen-Steuerelement klicken](../test/media/uwp-app-button-textbox.png)

1. Fügen Sie eine Assertion hinzu, um den Text im Textfeld-Steuerelement zu überprüfen. Wählen Sie das Textfeld-Steuerelement mit dem Fadenkreuztool aus, und klicken Sie im Dialogfeld **Assertionen hinzufügen** auf die Eigenschaft **Text**. Klicken Sie dann auf **Assertion hinzufügen**, oder drücken Sie **ALT**+**A**. Geben Sie **Textbox value is unexpected.** (Unerwarteter Textfeld-Wert) im Feld **Meldung bei Assertionsfehler** ein. Klicken Sie anschließend auf **OK**.

     ![Textfeld mit Fadenkreuztool auswählen und Assertion hinzufügen](../test/media/add-assertion-for-text.png)

1. Generieren Sie Testcode für die Assertion. Klicken Sie im Dialogfeld **Coded UI Test Builder** (Generator für Tests der programmierten UI) auf **Code generieren**. Klicken Sie im Dialogfeld **Code generieren** auf **Hinzufügen und generieren**.

     ![Code für die Textfeld-Assertion generieren](../test/media/add-and-generate-assert-method.png)

   Öffnen Sie im **Projektmappen-Explorer** die Datei *UIMap.Designer.cs*, um den hinzugefügten Code für die Assert-Methode und die Steuerelemente anzuzeigen.

   > [!TIP]
   > Wenn Sie Visual Basic verwenden, öffnen Sie *CodedUITest1.vb*. Klicken Sie dann im Code der `CodedUITestMethod1()`-Testmethode auf den Aufruf der Assert-Methode `Me.UIMap.AssertMethod1()`, und wählen Sie **Gehe zu Definition** aus. Die Datei *UIMap.Designer.vb* wird im Code-Editor geöffnet, um den hinzugefügten Code für die Assert-Methode und die Steuerelemente anzuzeigen.

    > [!WARNING]
    > Die Dateien *UIMap.designer.cs* oder *UIMap.Designer.vb* sollten nicht direkt geändert werden. Wenn Sie dies tun, werden Ihre Änderungen überschrieben, wenn der Test generiert wird.

    Die Assert-Methode sieht folgendermaßen aus:

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIUWPAppWindow.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.");
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.")
    End Sub
    ```

1. Anschließend muss die **AutomationID** der [UWP-App](#create-a-uwp-app-to-test) abgerufen werden, die getestet werden soll. Öffnen Sie das **Windows-Startmenü**, um die Kachel der App zu sehen. Ziehen Sie dann das Fadenkreuztool ![Zielsymbol](media/target-icon.png) vom Dialogfeld **Coded UI Test Builder** (Generator für Tests der programmierten UI) zur Kachel Ihrer App. Wenn ein blauer Rahmen die Kachel umgibt, lassen Sie die Maus los.

   ![Fadenkreuztool](media/cross-hair-tool.png)

   Das Dialogfeld **Assertionen hinzufügen** wird geöffnet und zeigt die **AutomationID** Ihrer App an. Klicken Sie mit der rechten Maustaste auf **AutomationID**, und wählen Sie **Wert in Zwischenablage kopieren** aus.

   ![AutomationID im Dialogfeld „Assertion hinzufügen“](../test/media/automation-id.png)

1. Fügen Sie Code zur Testmethode hinzu, um die UWP-App zu starten. Öffnen Sie im **Projektmappen-Explorer** die Datei *CodedUITest1.cs* oder *CodedUITest1.vb*. Fügen Sie über dem Aufruf von `AssertMethod1` Code hinzu, um die UWP-App zu starten:

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   Ersetzen Sie die AutomationID im Beispielcode durch den Wert, den Sie im vorherigen Schritt in die Zwischenablage kopiert haben.

   > [!IMPORTANT]
   > Kürzen Sie den Anfang der AutomationID, um Zeichen wie **P~** zu entfernen. Wenn Sie diese Zeichen nicht entfernen, löst der Test `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException` aus, wenn er versucht, die App zu starten.

1. Fügen Sie anschließend den Code für die Schaltfläche zur Testmethode hinzu. Fügen Sie in der Zeile nach `XamlWindow.Launch` eine Geste zum Tippen auf das Schaltflächen-Steuerelement hinzu:

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   Nach dem Hinzufügen des Codes sollte die vollständige `CodedUITestMethod1`-Testmethode folgendermaßen aussehen:

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");

       Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);

       // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
       this.UIMap.AssertMethod1();
   }
   ```

   ```vb
   <CodedUITest(CodedUITestType.WindowsStore)>
   Public Class CodedUITest1

       <TestMethod()>
       Public Sub CodedUITestMethod1()

           ' Launch the app.
           XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")

           '// Tap the button.
           Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)

           Me.UIMap.AssertMethod1()
       End Sub
   ```

1. Erstellen Sie das Testprojekt, und öffnen Sie anschließend den **Test-Explorer**, indem Sie auf **Test** > **Windows** > **Test-Explorer** klicken.

1. Klicken Sie auf **Alle ausführen**, um den Test auszuführen.

   Die App wird geöffnet, es wird auf die Schaltfläche getippt, und die **Text**-Eigenschaft des Textfelds wird aufgefüllt. Die Assert-Methode überprüft die **Text**-Eigenschaft des Textfelds.

   Nach Abschluss des Tests wird im **Test-Explorer** das erfolgreiche Ergebnis angezeigt.

   ![Der erfolgreiche Test wird im Test-Explorer angezeigt](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>Fragen und Antworten

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>F: Warum wird im Dialogfeld „Test der programmierten UI“ unter „Code generieren“ nicht die Option zum Aufzeichnen des Tests der programmierten UI angezeigt?

**A:** Die Option zum Aufzeichnen wird für UWP-Apps nicht unterstützt.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>F: Kann ich einen Test der programmierten UI für UWP-Apps auf Grundlage von WinJS erstellen?

**A**: Nein, nur XAML-basierte Apps werden unterstützt.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>F: Warum kann ich den Code in der Datei „UIMap.Designer“ nicht ändern?

**A**: Alle Codeänderungen, die Sie an der Datei *UIMapDesigner.cs* vornehmen, werden jedes Mal überschrieben, wenn Sie Code mit dem **Coded UI Test Builder** (Generator für Tests der programmierten UI) generieren. Wenn Sie eine aufgezeichnete Methode ändern müssen, kopieren Sie sie in die Datei *UIMap.cs*, und benennen Sie sie um. Die Datei *UIMap.cs* kann verwendet werden, um Methoden und Eigenschaften in der Datei *UIMapDesigner.cs* zu überschreiben. Entfernen Sie den Verweis auf die ursprüngliche Methode in der Datei *CodedUITest.cs*, und ersetzen Sie ihn durch den umbenannten Methodennamen.

## <a name="see-also"></a>Siehe auch

- [Verwenden der Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)
- [Festlegen einer eindeutigen Automatisierungseigenschaft für UWP-Steuerelemente für Tests](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)
