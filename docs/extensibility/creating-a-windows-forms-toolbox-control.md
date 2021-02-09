---
title: Erstellen eines Windows Forms Toolbox-Steuer Elements | Microsoft-Dokumentation
description: In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie mithilfe der Vorlage "Windows Forms Toolbox-Steuerelement" mit dem Visual Studio SDK ein einfaches Counter-Steuerelement erstellen
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4bb9505ab475da7919a39eb03e7c84b92857db4e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902184"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Erstellen eines Windows Forms Toolbox-Steuer Elements

Mit der Windows Forms Toolbox-Steuerelement Vorlage, die in der Visual Studio-Erweiterungstools (vs SDK) enthalten ist, können Sie ein **Toolbox** -Steuerelement erstellen, das automatisch hinzugefügt wird, wenn die Erweiterung installiert wird. In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie die Vorlage verwenden, um ein einfaches Counter-Steuerelement zu erstellen, das Sie an andere Benutzer verteilen.

## <a name="prerequisites"></a>Voraussetzungen

Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Erstellen des Toolbox-Steuer Elements

Mit der Windows Forms Toolbox-Steuerelement Vorlage wird ein nicht definiertes Benutzer Steuerelement erstellt und die gesamte Funktionalität bereitstellt, die zum Hinzufügen des Steuer Elements zur **Toolbox** erforderlich ist.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Erstellen einer Erweiterung mit einem Windows Forms Toolbox-Steuerelement

1. Erstellen Sie ein VSIX-Projekt mit dem Namen `MyWinFormsControl` . Sie finden die VSIX-Projektvorlage im Dialogfeld " **Neues Projekt** ", indem Sie nach "VSIX" suchen.

2. Wenn das Projekt geöffnet wird, fügen Sie eine **Windows Forms Toolbox-Steuer** Element Vorlage mit dem Namen hinzu `Counter` . Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie   >  **Neues Element** hinzufügen aus. Wechseln Sie im Dialogfeld **Neues Element hinzufügen** zu **Visual c#**  >  -**Erweiterbarkeit** , und wählen Sie **Windows Forms Toolbox-Steuer** Element aus.

3. Dadurch wird ein Benutzer Steuerelement, ein `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> zum Platzieren des Steuer Elements in der **Toolbox** und ein **Microsoft. VisualStudio. ToolboxControl** -Asset-Eintrag im VSIX-Manifest für die Bereitstellung hinzugefügt.

### <a name="build-a-user-interface-for-the-control"></a>Erstellen einer Benutzeroberfläche für das Steuerelement

Das `Counter` -Steuerelement erfordert zwei untergeordnete Steuerelemente: a <xref:System.Windows.Forms.Label> zum Anzeigen der aktuellen Anzahl und ein, <xref:System.Windows.Forms.Button> um die Anzahl auf 0 zurückzusetzen. Es sind keine weiteren untergeordneten Steuerelemente erforderlich, da Aufrufer den Counter Programm gesteuert erhöhen.

#### <a name="to-build-the-user-interface"></a>So erstellen Sie die Benutzeroberfläche

1. Doppelklicken Sie in **Projektmappen-Explorer** auf *counter.cs* , um Sie im Designer zu öffnen.

2. **Klicken Sie hier.** Schaltfläche, die standardmäßig eingeschlossen ist, wenn Sie die Windows Forms Toolbox-Steuerelement Vorlage hinzufügen.

3. Ziehen Sie aus der **Toolbox** ein `Label` -Steuerelement und dann ein `Button` Steuerelement unterhalb der Entwurfs Oberfläche.

4. Ändern Sie die Größe des gesamten Benutzer Steuer Elements auf 150, 50 Pixel, und ändern Sie die Größe des Schaltflächen-Steuer Elements auf 50, 20 Pixel.

5. Legen Sie im Fenster **Eigenschaften** die folgenden Werte für die Steuerelemente auf der Entwurfs Oberfläche fest.

    |Control|Eigenschaft|Wert|
    |-------------|--------------|-----------|
    |`Label1`|**Text**|""|
    |`Button1`|**Name**|btnReset|
    |`Button1`|**Text**|Reset|

### <a name="code-the-user-control"></a>Codieren des Benutzer Steuer Elements

Das-Steuerelement macht `Counter` eine Methode verfügbar, um den Zähler zu erhöhen, ein Ereignis, das ausgelöst wird, wenn der Zähler inkrementiert wird, eine Schaltfläche **Zurücksetzen** und drei Eigenschaften zum Speichern der aktuellen Anzahl, den Anzeige Text und ob die Schaltfläche **Zurücksetzen** angezeigt oder ausgeblendet wird. Das `ProvideToolboxControl` -Attribut bestimmt, an welcher Stelle in der **Toolbox** das `Counter` -Steuerelement angezeigt wird.

#### <a name="to-code-the-user-control"></a>So codieren Sie das Benutzer Steuerelement

1. Doppelklicken Sie auf das Formular, um den Lade Ereignishandler im Code Fenster zu öffnen.

2. Erstellen Sie oberhalb der Ereignishandlermethode in der Steuerelement Klasse eine Ganzzahl, um den Leistungswert und eine Zeichenfolge zum Speichern des Anzeige Texts zu speichern, wie im folgenden Beispiel gezeigt.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Erstellen Sie die folgenden öffentlichen Eigenschaften Deklarationen.

    ```csharp
    public int Value {
        get { return currentValue; }
    }

    public string Message {
        get { return displayText; }
        set { displayText = value; }
    }

    public bool ShowReset {
        get { return btnReset.Visible; }
        set { btnReset.Visible = value; }
    }

    ```

    Aufrufer können auf diese Eigenschaften zugreifen, um den Anzeige Text des Zählers zu erhalten und festzulegen und um die Schaltfläche **Zurücksetzen** anzuzeigen oder auszublenden. Aufrufer können den aktuellen Wert der schreibgeschützten `Value` Eigenschaft abrufen, aber Sie können den Wert nicht direkt festlegen.

4. Fügen Sie den folgenden Code in das- `Load` Ereignis für das-Steuerelement ein.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    Wenn Sie den Bezeichnungs **Text im** <xref:System.Windows.Forms.UserControl.Load> Ereignis festlegen, können die Zieleigenschaften geladen werden, bevor ihre Werte angewendet werden. Das Festlegen **des** Bezeichnungs Texts im Konstruktor führt zu einer leeren **Bezeichnung**.

5. Erstellen Sie die folgende öffentliche Methode, um den-Wert zu erhöhen.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Fügen Sie der Steuerelement Klasse eine Deklaration für das- `Incremented` Ereignis hinzu.

    ```csharp
    public event EventHandler Incremented;
    ```

    Aufrufer können diesem Ereignishandler hinzufügen, um auf Änderungen im Wert des Zählers zu reagieren.

7. Kehren Sie zur Entwurfs Ansicht zurück, und doppelklicken Sie auf die Schaltfläche **Zurücksetzen** , um den `btnReset_Click` Ereignishandler zu generieren Füllen Sie ihn dann wie im folgenden Beispiel gezeigt aus.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Ändern Sie direkt oberhalb der Klassendefinition in der `ProvideToolboxControl` -Attributdeklaration den Wert des ersten Parameters von `"MyWinFormsControl.Counter"` in `"General"`. Dadurch wird der Name der Elementgruppe festgelegt, die das Steuerelement in der **Toolbox** hostet.

    Das folgende Beispiel zeigt das `ProvideToolboxControl` -Attribut und die angepasste Klassendefinition.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Testen des Steuerelements

 Zum Testen eines **Toolbox** -Steuer Elements testen Sie es zunächst in der Entwicklungsumgebung, und testen Sie es dann in einer kompilierten Anwendung.

#### <a name="to-test-the-control"></a>So testen Sie das Steuerelement

1. Drücken Sie **F5** , um das **Debugging zu starten**.

    Mit diesem Befehl wird das Projekt erstellt und eine zweite experimentelle Instanz von Visual Studio geöffnet, in der das-Steuerelement installiert ist.

2. Erstellen Sie in der experimentellen Instanz von Visual Studio ein **Windows Forms-Anwendungs** Projekt.

3. Doppelklicken Sie in **Projektmappen-Explorer** auf *Form1.cs* , um Sie im Designer zu öffnen, wenn Sie nicht bereits geöffnet ist.

4. In der **Toolbox** sollte das `Counter` Steuerelement im Abschnitt **Allgemein** angezeigt werden.

5. Ziehen `Counter` Sie ein-Steuerelement auf das Formular, und wählen Sie es aus. Die `Value` `Message` Eigenschaften, und werden `ShowReset` im Fenster **Eigenschaften** sowie in den Eigenschaften, die von geerbt werden, angezeigt <xref:System.Windows.Forms.UserControl> .

6. Legen Sie die `Message` -Eigenschaft auf `Count:`fest.

7. Ziehen <xref:System.Windows.Forms.Button> Sie ein-Steuerelement auf das Formular, und legen Sie dann die Eigenschaften Name und Text der Schaltfläche auf fest `Test` .

8. Doppelklicken Sie auf die Schaltfläche, um *Form1.cs* in der Code Ansicht zu öffnen, und erstellen Sie einen Klick Handler.

9. Klicken Sie im Click-Handler auf `counter1.Increment()` .

10. Geben Sie in der Konstruktorfunktion nach dem-Befehl ein `InitializeComponent` , `counter1``.``Incremented +=` und drücken Sie dann zweimal die **Tab** -Taste.

    Visual Studio generiert einen Handler auf Formular Ebene für das- `counter1.Incremented` Ereignis.

11. Markieren `Throw` Sie die Anweisung im Ereignishandler, geben `mbox` Sie ein, und drücken Sie dann zweimal die **Tab** -Taste, um ein Meldungs Feld aus dem mbox-Code Ausschnitt zu generieren.

12. Fügen Sie in der nächsten Zeile den folgenden-Block hinzu, `if` / `else` um die Sichtbarkeit der Schaltfläche **Zurücksetzen** festzulegen.

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Drücken Sie **F5**.

    Das Formular wird geöffnet. Das- `Counter` Steuerelement zeigt den folgenden Text an.

    **Anzahl: 0**

14. Klicken Sie auf **Test**.

    Die-Wert Inkremente und Visual Studio zeigen ein Meldungs Feld an.

15. Schließen Sie das Meldungs Feld.

    Die Schaltfläche **Zurücksetzen** wird ausgeblendet.

16. Wählen Sie **Test** aus, bis der Wert **5** jedes Mal zum Schließen der Meldungs Felder erreicht wird.

    Die Schaltfläche **Zurücksetzen** wird erneut angezeigt.

17. Klicken Sie auf **Zurücksetzen**.

    Der Indikatorensatz wird auf **0** zurückgesetzt.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie ein **Toolbox** -Steuerelement erstellen, erstellt Visual Studio eine Datei namens *Projektname. vsix* im Ordner "" \bin\debug\ "des Projekts. Sie können das-Steuerelement bereitstellen, indem Sie die *VSIX* -Datei in ein Netzwerk oder auf eine Website hochladen. Wenn ein Benutzer die *VSIX* -Datei öffnet, wird das Steuerelement installiert und der Visual Studio- **Toolbox** auf dem Computer des Benutzers hinzugefügt. Alternativ dazu können **Sie die** *VSIX* -Datei in [Visual Studio Marketplace](https://marketplace.visualstudio.com/) hochladen, damit Benutzer Sie finden können, indem Sie im Dialogfeld Extras  >  **Erweiterungen und Updates** suchen.

## <a name="see-also"></a>Weitere Informationen

- [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Erstellen eines WPF-Toolbox-Steuer Elements](../extensibility/creating-a-wpf-toolbox-control.md)
- [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Grundlagen zur Windows Forms Steuerung der Entwicklung](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
