---
title: Hallo Welt-App mit WPF in C#
description: Erstellen Sie eine einfache Windows Desktop.NET-App in C# mit Visual Studio mit dem Windows Presentation Foundation (WPF) UI-Framework.
ms.custom: seodec18, get-started
ms.date: 02/10/2021
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: tutorial
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 1f3232ad0a8b7cc34abbe6d49c05944c066226da
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101682857"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Tutorial: Erstellen einer einfachen Anwendung mit C\#

Beim Durcharbeiten dieses Tutorial machen Sie sich mit vielen Tools, Dialogfeldern und Designern vertraut, die Sie für die Entwicklung von Anwendungen in Visual Studio verwenden können. Sie erstellen eine Anwendung „Hello, World“, entwerfen die Benutzeroberfläche, fügen Code hinzu und debuggen Fehler. Gleichzeitig erfahren Sie mehr über das Arbeiten in der integrierten Entwicklungsumgebung ([IDE](visual-studio-ide.md)).

## <a name="prerequisites"></a>Voraussetzungen

::: moniker range="vs-2017"
Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?) kostenlos herunterladen.
::: moniker-end
::: moniker range=">=vs-2019"

- Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) kostenlos herunterladen.
- Sie können entweder .NET Framework oder .NET Core für dieses Tutorial verwenden. .NET Core ist das neuere, modernere Framework. Für .NET Core ist mindestens Visual Studio 2019 Version 16.3 erforderlich.
::: moniker-end

## <a name="configure-the-ide"></a>Konfigurieren der IDE

::: moniker range="vs-2017"

Wenn Sie Visual Studio zum ersten Mal öffnen, werden Sie zur Anmeldung aufgefordert. Dieser Schritt ist für dieses Tutorial nicht unbedingt notwendig. Als Nächstes wird Ihnen möglicherweise ein Dialogfeld angezeigt, in dem Sie aufgefordert werden, Ihre Entwicklungseinstellungen und Farbdesigns festzulegen. Behalten Sie die Standardeinstellungen bei, und klicken Sie auf **Visual Studio starten**.

![Dialogfeld „Einstellungen auswählen“](../media/exploreide-settings.png)

Wenn sich Visual Studio öffnet, werden Toolfenster, die Menüs, Symbolleisten und der Hauptfensterbereich angezeigt. Mit **Schnellstart** werden Toolfenster auf der linken und rechten Seite des Anwendungsfensters und die Menüleiste und die Standardsymbolleiste oben angedockt. In der Mitte des Anwendungsfensters befindet sich die **Startseite**. Wenn Sie eine Projektmappe oder ein Projekt laden, werden Editoren und Designer dort angezeigt, wo sich die **Startseite** befindet. Wenn Sie eine Anwendung entwickeln, verbringen Sie die meiste Zeit in diesem zentralen Bereich.

![Visual Studio 2017-IDE mit übernommenen allgemeinen Einstellungen](../media/exploreide-idewithgeneralsettings.png "Screenshot: Visual Studio 2017-IDE mit übernommenen allgemeinen Einstellungen")

::: moniker-end

::: moniker range=">=vs-2019"

Wenn Sie Visual Studio starten, wird zunächst das Startfenster geöffnet. Klicken Sie auf **Ohne Code fortfahren**, um die Entwicklungsumgebung zu öffnen. Ihnen werden Toolfenster, Menüs und Symbolleisten sowie das Hauptfenster angezeigt. Toolfenster werden auf der linken und rechten Seite des Anwendungsfensters angedockt und enthalten oben ein Suchfeld, die Menüleiste und die Standardsymbolleiste. Wenn Sie eine Projektmappe oder ein Projekt laden, werden Editoren und Designer im zentralen Bereich des Anwendungsfensters angezeigt. Wenn Sie eine Anwendung entwickeln, verbringen Sie die meiste Zeit in diesem zentralen Bereich.

::: moniker-end

## <a name="create-the-project"></a>Erstellen eines Projekts

Wenn Sie eine Anwendung in Visual Studio erstellen, erstellen Sie zunächst ein Projekt und eine Projektmappe. In diesem Beispiel erstellen Sie eine Windows Presentation Foundations-Projektmappe (WPF).

::: moniker range="vs-2017"

1. Erstellen Sie ein neues Projekt. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.

     ![Wählen Sie in der Menüleiste „Datei > Neu > Projekt“ aus.](../media/exploreide-filenewproject.png "Screenshot: Menüleiste, in der Sie auf „Datei“ > „Neu“ > „Projekt“ klicken")

1. Klicken Sie im Dialogfeld **Neues Projekt** auf **Installiert** > **Visual C#**  > **Windows-Desktop**, und wählen Sie anschließend die Vorlage **WPF-App (.NET Framework)** aus. Nennen Sie das Projekt **HelloWPFApp**, und wählen Sie **OK** aus.

     ![Vorlage für eine WPF-App im Visual Studio-Dialogfeld „Neues Projekt“](media/exploreide-newprojectcsharp.png "Screenshot: WPF-App-Vorlage im Dialogfeld „Neues Projekt“")

::: moniker-end

::: moniker range="vs-2019"

1. Öffnen Sie Visual Studio 2019.

1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   ![Fenster „Neues Projekt erstellen“ anzeigen](../../get-started/media/vs-2019/start-window-create-new-project.png "Screenshot: Fenster „Neues Projekt erstellen“")

1. Suchen Sie im Bildschirm **Neues Projekt erstellen** nach „WPF“, und wählen Sie dann **WPF-App** und anschließend **Weiter** aus.

   :::image type="content" source="media/vs-2019/explore-ide-new-project-csharp-vs-2019.png" alt-text="WPF-Anwendungsvorlage im Dialogfeld „Neues Projekt erstellen“":::

1. Geben Sie dem Projekt im nächsten Bildschirm den Namen **HelloWPFApp**, und wählen Sie **Erstellen** aus.

   :::image type="content" source="./media/vs-2019/explore-ide-name-project.png" alt-text="Projekt „HelloWPFApp“ nennen":::

1. Im Fenster **Zusätzliche Informationen** sollte **.NET Core 3.1** bereits als Zielframework ausgewählt sein. Falls nicht, wählen Sie **.NET Core 3.1** aus. Wählen Sie anschließend **Erstellen** aus.

   :::image type="content" source="./media/vs-2019/wpf-target-framework.png" alt-text="Sicherstellen, dass im Fenster „Zusätzliche Informationen“ .NET Core 3.1 ausgewählt ist":::

::: moniker-end

Visual Studio erstellt das „HelloWPFApp“-Projekt und die Projektmappe, woraufhin im **Projektmappen-Explorer** verschiedene Dateien angezeigt werden. Der **WPF-Designer** zeigt eine Entwurfsansicht und eine XAML-Ansicht der Datei *MainWindow.xaml* in einer geteilten Ansicht an. Ziehen Sie den Teiler, um mehr oder weniger der jeweiligen Ansichten anzuzeigen. Sie können auch nur die visuelle Ansicht oder nur die XAML-Ansicht anzeigen.

![WPF-Projekt und -Projektmappe in der IDE](media/exploreide-wpfproject-cs.png "Screenshot: WPF-Projekt und -Projektmappe in der IDE")

> [!NOTE]
> Weitere Informationen zu XAML (eXtensible Application Markup Language) finden Sie auf der Seite [Übersicht über XAML für WPF](/dotnet/framework/wpf/advanced/xaml-overview-wpf).

Nachdem Sie das Projekt erstellt haben, können Sie es anpassen. Wählen Sie dazu im Menü **Ansicht** die Option **Eigenschaftenfenster** aus, oder drücken Sie auf **F4**. Sie können dann die Optionen für Projektelemente, Steuerelemente und andere Elemente in einer Anwendung anzeigen lassen und ändern.

   ![Eigenschaftenfenster](../media/exploreide-hellowpfappfiles.png "Screenshot: Eigenschaftenfenster mit WPF-Datei-App-Namen")   

### <a name="change-the-name-of-mainwindowxaml"></a>Ändern des Namens der Datei „MainWindow.xaml“

Geben Sie „MainWindow“ einen genaueren Namen. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf *MainWindow.xaml*, und wählen Sie dann **Umbenennen** aus. Benennen Sie die Datei in *Greetings.xaml* um.

## <a name="design-the-user-interface-ui"></a>Entwerfen der Benutzeroberfläche (UI)

Wenn der Designer nicht geöffnet ist, wählen Sie die Datei *Greetings.xaml* aus, und drücken Sie **UMSCHALT**+**F7**, um den Designer zu öffnen.

Nun fügen wir der Anwendung drei Arten von Steuerelementen hinzu: ein <xref:System.Windows.Controls.TextBlock>-Steuerelement, zwei <xref:System.Windows.Controls.RadioButton>-Steuerelemente und ein <xref:System.Windows.Controls.Button>-Steuerelement.

### <a name="add-a-textblock-control"></a>Hinzufügen eines TextBlock-Steuerelements

1. Drücken Sie **STRG**+**Q**, um das Suchfeld zu aktivieren, und geben Sie dort den Begriff **Toolbox** ein. Wählen Sie in der Ergebnisliste **Ansicht > Toolbox** aus.

1. Erweitern Sie in der **Toolbox** den Knoten **Häufig verwendete WPF-Steuerelemente**, damit das TextBlock-Steuerelement angezeigt wird.

     ![Toolbox mit hervorgehobenem TextBlock-Steuerelement](../media/exploreide-textblocktoolbox.png "Screenshot: Toolbox-Fenster mit hervorgehobenem TextBlock-Steuerelement")

1. Fügen Sie auf der Entwurfsoberfläche ein TextBlock-Steuerelement hinzu, indem Sie das **TextBlock**-Element auswählen und in das Fenster auf der Entwurfsoberfläche ziehen. Zentrieren Sie das Steuerelement im oberen Bereich des Fensters. Ab Visual Studio 2019 können Sie das Steuerelement an den roten Hilfslinien ausrichten.

    Das Fenster sollte der folgenden Abbildung entsprechen:

    ![TextBlock-Steuerelement im Formular „Greetings“](../media/exploreide-greetingswithtextblockonly.png "Screenshot: TextBlock-Steuerelement im Formular „Greetings“")

   Das XAML-Markup sollte in etwa dem folgenden Beispiel entsprechen:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

### <a name="customize-the-text-in-the-text-block"></a>Anpassen des Texts im Textblock

1. Suchen Sie in der XAML-Ansicht das Markup für **TextBlock**, und ändern Sie das **Textattribut** von `TextBox` in `Select a message option and then choose the Display button.`.

   Das XAML-Markup sollte in etwa dem folgenden Beispiel entsprechen:

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. Zentrieren Sie TextBlock ggf. erneut, und speichern Sie Ihre Änderungen mit **STRG+S** oder mit dem Menüelement **Datei**.

Anschließend fügen Sie dem Formular zwei [RadioButton](/dotnet/framework/wpf/controls/radiobutton)-Steuerelemente hinzu.

### <a name="add-radio-buttons"></a>Hinzufügen von Optionsfeldern

1. Suchen Sie in der **Toolbox** nach dem **Optionsfeld**-Steuerelement.

     ![Toolboxfenster mit aktiviertem RadioButton-Steuerelement](../media/exploreide-radiobuttontoolbox.png "Screenshot: Toolbox-Fenster mit ausgewähltem RadioButton-Steuerelement")

1. Fügen Sie auf der Entwurfsoberfläche zwei Optionsfeld-Steuerelemente hinzu, indem Sie auf das **Optionsfeld**-Element klicken und in das Fenster auf der Entwurfsoberfläche ziehen. Verschieben Sie die Schaltflächen (indem Sie darauf klicken und die Pfeiltasten drücken), sodass sie nebeneinander unter dem TextBlock-Steuerelement erscheinen. Richten Sie die Steuerelemente an den roten Hilfslinien aus.

   Das Fenster sieht wie folgt aus:

   ![Formular „Greetings“ mit TextBlock und zwei Optionsfeldern](../media/exploreide-greetingswithradiobuttons.png "Screenshot: Formular „Greetings“ mit TextBlock und zwei Optionsfeldern")

1. Ändern Sie im Fenster **Eigenschaften** für das linke RadioButton-Steuerelement die Eigenschaft **Name** (die Eigenschaft oben im Fenster **Eigenschaften** ) in `HelloButton`.

    ![Eigenschaftenfenster „RadioButton“](../media/exploreide-buttonproperties.png "Screenshot: RadioButton-Eigenschaftenfenster")

1. Ändern Sie im Fenster **Eigenschaften** zum rechten RadioButton-Steuerelement die Eigenschaft **Name** in `GoodbyeButton`. Speichern Sie dann die Änderungen.

Als nächstes können Sie jetzt Anzeigetext für jedes RadioButton-Steuerelement hinzufügen. Die folgende Prozedur aktualisiert die Eigenschaft **Inhalt** für ein RadioButton-Steuerelement.

### <a name="add-display-text-for-each-radio-button"></a>Hinzufügen von Anzeigetext für jedes Optionsfeld

1. Ändern Sie das **Content**-Attribut im XAML-Code von `HelloButton` und `GoodbyeButton` in `"Hello"` und `"Goodbye"`. Das XAML-Markup sollte in etwa wie im folgenden Beispiel aussehen:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Festlegen eines standardmäßig zu aktivierenden Optionsfelds

In diesem Schritt legen Sie fest, dass „HelloButton“ standardmäßig aktiviert wird, sodass eines der beiden Optionsfelder immer aktiviert ist.

1. Suchen Sie in der XAML-Ansicht das Markup für „HelloButton“.

1. Fügen Sie ein **IsChecked**-Attribut hinzu und setzen Sie es auf **True**. Fügen Sie insbesondere `IsChecked="True"` hinzu.

   Das XAML-Markup sollte in etwa wie im folgenden Beispiel aussehen:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

Das letzte Benutzeroberflächenelement, das Sie hinzufügen, ist ein [Button](/dotnet/framework/wpf/controls/button)-Steuerelement.

### <a name="add-the-button-control"></a>Hinzufügen des Button-Steuerelements

1. Suchen Sie in der **Toolbox** nach dem **Schaltflächen**-Steuerelement, und fügen Sie es auf der Entwurfsoberfläche dem Optionsfeld-Steuerelement hinzu, indem Sie es in der Entwurfsansicht in das Formular ziehen. Wenn Sie Visual Studio 2019 oder höher verwenden, hilft Ihnen eine rote Linie beim Zentrieren des Steuerelements.

1. Ändern Sie in der XAML-Ansicht den Wert von **Inhalt** für das Schaltflächen-Steuerelement von `Content="Button"` in `Content="Display"`. Speichern Sie dann die Änderungen.

     Das Fenster sollte der folgenden Abbildung entsprechen.

     ![Formular „Greetings“ mit Steuerelementbezeichnungen](media/exploreide-greetingswithcontrollabels-cs.png "Screenshot: Greetings-Formular mit Steuerelementbezeichnungen")

   Das XAML-Markup sollte in etwa wie im folgenden Beispiel aussehen:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

### <a name="add-code-to-the-display-button"></a>Hinzufügen von Code zur Anzeigeschaltfläche

Wenn die Anwendung ausgeführt wird, wird ein Meldungsfeld angezeigt, nachdem ein Benutzer zunächst ein Optionsfeld aktiviert und anschließend die Schaltfläche **Anzeigen** ausgewählt hat. Ein Meldungsfeld wird für die Begrüßung ("Hello") und ein anderes für die Verabschiedung ("Goodbye") angezeigt. Um dieses Verhalten zu erstellen, fügen Sie Code zum `Button_Click`-Ereignis in *Greetings.xaml.cs* hinzu.

1. Doppelklicken Sie auf der Entwurfsoberfläche auf die Schaltfläche **Anzeigen** .

     *Greetings.xaml.cs* wird geöffnet, der Cursor steht im `Button_Click`-Ereignis.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {

    }
    ```

1. Geben Sie den folgenden Code ein:

    ```csharp
    if (HelloButton.IsChecked == true)
    {
         MessageBox.Show("Hello.");
    }
    else if (GoodbyeButton.IsChecked == true)
    {
        MessageBox.Show("Goodbye.");
    }
    ```

1. Speichern Sie die Anwendung.

## <a name="debug-and-test-the-application"></a>Debuggen und Testen der Anwendung

Als Nächstes debuggen Sie die Anwendung, um nach Fehlern zu suchen und zu testen, ob beide Meldungsfelder ordnungsgemäß angezeigt werden. Die folgenden Anweisungen beschreiben, wie Sie den Debugger erstellen und starten. Lesen Sie jedoch später für weitere Informationen [Erstellen einer WPF-Anwendung (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) und [Debuggen von WPF](../../debugger/debugging-wpf.md).

### <a name="find-and-fix-errors"></a>Suchen und Beheben von Fehlern

In diesem Schritt suchen Sie den Fehler, den Sie zuvor verursacht haben, indem Sie den Namen der Datei *MainWindow.xaml* geändert haben.

#### <a name="start-debugging-and-find-the-error"></a>Starten des Debuggings und Suchen des Fehlers

1. Starten Sie den Debugger, indem Sie **F5** drücken oder **Debuggen** auswählen und anschließend **Debugging starten** auswählen.

   Ein **Haltemodus**-Fenster wird angezeigt, und das **Ausgabe**-Fenster gibt an, dass eine IOException-Klasse aufgetreten ist: Cannot locate resource 'mainwindow.xaml' (Die Ressource „mainwindow.xaml“ kann nicht gefunden werden).

   ![IOException-Meldung](../media/exploreide-ioexception.png "Screenshot der IOException-Meldung")

1. Beenden Sie den Debugger, indem Sie **Debuggen** > **Debuggen beenden** auswählen.

Zu Beginn dieses Tutorials wurde *MainWindow.xaml* in *Greetings.xaml* umbenannt. Da der Code jedoch weiterhin auf *MainWindow.xaml* als Start-URI für die Anwendung verweist, kann das Projekt nicht gestartet werden.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Angeben von „Greetings.xaml“ als Start-URI

1. Öffnen Sie im **Projektmappen-Explorer** die Datei *App.xaml*.

1. Ändern Sie `StartupUri="MainWindow.xaml"` zu `StartupUri="Greetings.xaml"`, und speichern Sie dann die Änderungen.

Starten Sie den Debugger erneut (drücken Sie auf **F5**). Sie sollten das **Greetings**-Fenster der Anwendung sehen.

::: moniker range="vs-2017"
![Screenshot der ausgeführten App](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Screenshot der ausgeführten App](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

Schließen Sie nun das Anwendungsfenster, um das Debuggen zu beenden.

### <a name="debug-with-breakpoints"></a>Debuggen mit Haltepunkten

Wenn Sie einige Haltepunkte hinzufügen, können Sie den Code während des Debuggens testen. Sie können Haltepunkte durch Auswählen von **Debuggen** > **Haltepunkt umschalten** hinzufügen, indem Sie am linken Rand des Editors neben die Codezeile klicken, in der die Unterbrechung stattfinden soll, oder indem Sie **F9** drücken.

#### <a name="add-breakpoints"></a>Hinzufügen von Haltepunkten

1. Öffnen Sie *Greetings.xaml.cs*, und wählen Sie die folgende Zeile aus: `MessageBox.Show("Hello.")`

1. Fügen Sie einen Haltepunkt hinzu, indem Sie im Menü **Debuggen** und dann **Haltepunkt umschalten** auswählen.

     Am äußeren linken Rand des Editorfensters wird ein roter Kreis neben der Codezeile angezeigt.

1. Wählen Sie folgende Zeile aus: `MessageBox.Show("Goodbye.")`.

1. Drücken Sie die Taste **F9**, um einen Haltepunkt hinzuzufügen, und drücken Sie anschließend **F5**, um das Debuggen zu starten.

1. Aktivieren Sie im Fenster **Greetings** das Optionsfeld **Hello** , und wählen Sie dann die Schaltfläche **Anzeigen** aus.

    Die Zeile wird `MessageBox.Show("Hello.")` gelb hervorgehoben. Am unteren Rand der IDE werden die Fenster „Auto“, „Lokal“ und „Überwachen“ auf der linken Seite zusammen angedockt, und die Fenster „Aufrufliste“, „Haltepunkte", „Ausnahmeeinstellungen“, „Befehl“, „Direkt“ und „Ausgabe“ werden auf der rechten Seite zusammen angedockt.

    ![Erreichen eines Breakpoints im Debugger](media/exploreide-debugbreakpoint.png "Screenshot eines Haltepunkts im Debugger")

1. Wählen Sie in der Menüleiste **Debuggen** > **Rücksprung** aus.

     Die Anwendung wird weiter ausgeführt, und ein Meldungsfeld mit dem Wort „Hello“ wird angezeigt.

1. Wählen Sie die Schaltfläche **OK** im Meldungsfeld, um es zu schließen.

1. Aktivieren Sie im Fenster **Greetings** das Optionsfeld **Goodbye** , und wählen Sie dann die Schaltfläche **Anzeigen** aus.

     Die Zeile wird `MessageBox.Show("Goodbye.")` gelb hervorgehoben.

1. Drücken Sie die Taste **F5**, um das Debuggen fortzusetzen. Wenn das Meldungsfeld angezeigt wird, wählen Sie die Schaltfläche **OK** im Meldungsfeld, um es zu schließen.

1. Schließen Sie das Anwendungsfenster, um das Debuggen zu beenden.

1. Wählen Sie in der Menüleiste **Debuggen** > **Alle Haltepunkte deaktivieren** aus.

### <a name="view-a-representation-of-the-ui-elements"></a>Anzeigen einer Darstellung der Benutzeroberflächenelemente

In der ausgeführten App sollte ein Widget angezeigt werden, das am oberen Rand des Fensters angezeigt wird. Dies ist eine Runtimehilfsfunktion, die Schnellzugriff auf einige hilfreiche Debugfeatures bereitstellt. Klicken Sie auf die erste Schaltfläche **Zur visuellen Echtzeitstruktur wechseln**. Daraufhin sollte ein Fenster mit einer Struktur angezeigt werden, die alle visuelle Elemente Ihrer Seite enthält. Erweitern Sie die Knoten, um die hinzugefügten Schaltflächen zu finden.

![Screenshot: Fenster mit visueller Echtzeitstruktur](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Version der Anwendung erstellen

Nachdem Sie überprüft haben, dass alles funktioniert, können Sie einen Releasebuild der Anwendung vorbereiten.

1. Wählen Sie im Hauptmenü **Erstellen** > **Projektmappe bereinigen** aus, um Zwischendateien und Ausgabedateien zu löschen, die bei vorherigen Builds erstellt wurden. Dies ist nicht erforderlich, bereinigt jedoch die Ausgaben des Builddebugvorgangs.

1. Ändern Sie die Build-Konfiguration für HelloWPFApp über das Dropdown-Steuerelement in der Symbolleiste (derzeit „Debug“) von **Debug** in **Release**.

1. Erstellen Sie die Projektmappe, indem Sie auf **Erstellen** > **Projektmappe erstellen** klicken.

Damit haben Sie das Tutorial erfolgreich abgeschlossen. Sie finden die *EXE*-Datei, die Sie erstellt haben, in Ihrer Projektmappe und im Projektverzeichnis ( *...\HelloWPFApp\HelloWPFApp\bin\Release*).

## <a name="next-steps"></a>Nächste Schritte

Damit haben Sie das Tutorial erfolgreich abgeschlossen. Wenn Sie weitere Informationen erhalten möchten, fahren Sie mit den folgenden Tutorials fort.

> [!div class="nextstepaction"]
> [Fahren Sie mit weiteren C#-Tutorials fort](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>Siehe auch

- [Produktivitätstipps](../../ide/productivity-features.md)
