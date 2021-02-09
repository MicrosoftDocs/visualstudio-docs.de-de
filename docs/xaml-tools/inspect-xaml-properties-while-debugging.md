---
title: Prüfen von XAML-Eigenschaften beim Debuggen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie beim Debuggen die Visual Tree-und Live Property Explorer-Tools verwenden, um XAML-Eigenschaften zu überprüfen und eine Strukturansicht der Benutzeroberflächen Elemente zu erhalten
ms.custom: SEO-VS-2020
ms.date: 11/12/2019
ms.topic: how-to
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: d9033921c9e9863e5210721fb2c1244c326802d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881372"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Überprüfen von XAML-Eigenschaften beim Debuggen

Sie können über **Visuelle Echtzeitstruktur** und **Live-Eigenschaften-Explorer** eine Echtzeitansicht Ihres ausgeführten XAML-Codes abrufen. Diese Tools bieten Ihnen eine Strukturansicht der Benutzeroberflächenelemente Ihrer ausgeführten XAML-Anwendung, und Sie zeigen Ihnen Runtime-Eigenschaften der von Ihnen ausgewählten Benutzeroberflächenelemente an.

Sie können diese Tools in den folgenden Konfigurationen verwenden:

|Anwendungstyp|Betriebssystem und Tools|
|-----------------|--------------------------------|
|Windows Presentation Foundation-Anwendungen (4.0 und höher)|Windows 7 und höher|
|Universelle Windows-Apps|Windows 10 und höher mit dem [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)|

## <a name="look-at-elements-in-the-live-visual-tree"></a>Elemente in der visuellen echt Zeitstruktur ansehen

Wir beginnen mit einer sehr einfachen WPF-Anwendung, die über eine Listenansicht und eine Schaltfläche verfügt. Bei jedem Klick auf die Schaltfläche wird der Liste ein anderes Element hinzugefügt. Gerade nummerierte Elemente sind grau, und ungerade nummerierte Elemente sind gelb.

### <a name="create-the-project"></a>Erstellen des Projekts

1. Erstellen Sie eine neue c#-WPF-Anwendung (**Datei**  >  **"New**  >  **Project**", geben Sie "c# WPF" ein, und wählen Sie entweder **WPF-App (.net Core)** oder **WPF-App (.NET Framework)**) aus. Nennen Sie sie **TestXAML**.

1. Ändern Sie „MainWindow.xaml“ wie folgt:

   ```xaml
   <Window x:Class="TestXAML.MainWindow"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
      xmlns:local="clr-namespace:TestXAML"
      mc:Ignorable="d"
      Title="MainWindow" Height="350" Width="525">
      <Grid>
         <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>
         <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>
      </Grid>
   </Window>
   ```

1. Fügen Sie der Datei „MainWindow.xaml.cs“ den folgenden Befehlshandler hinzu:

   ```csharp
   int count;

   private void button_Click(object sender, RoutedEventArgs e)
   {
      ListBoxItem item = new ListBoxItem();
      item.Content = "Item" + ++count;
      if (count % 2 == 0)
      {
         item.Background = Brushes.LightGray;
      }
      else
      {
         item.Background = Brushes.LightYellow;
      }
      listBox.Items.Add(item);
   }
   ```

1. Erstellen Sie das Projekt, und starten Sie das Debugging. (Bei der Buildkonfiguration muss es sich um „Debug“ und nicht um „Release“ handeln. Weitere Informationen zu Buildkonfigurationen finden Sie Untergrund Legendes zu [Buildkonfigurationen](../ide/understanding-build-configurations.md).)

   Wenn das Fenster angezeigt wird, sehen Sie, dass die in-App-Symbolleiste in der laufenden Anwendung angezeigt wird.

   ::: moniker range=">= vs-2019"
   ![Hauptfenster der App](../debugger/media/vs-2019/livevisualtree-app.png "LiveVIsualTree-App")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Hauptfenster der App](../debugger/media/livevisualtree-app.png "LiveVIsualTree-App")
   ::: moniker-end

1. Klicken Sie nun mehrmals auf die Schaltfläche **Element hinzufügen** , um der Liste neue Elemente hinzuzufügen.

### <a name="inspect-xaml-properties"></a>Überprüfen von XAML-Eigenschaften

1. Öffnen Sie als nächstes das Fenster **Live** -Struktur, indem Sie auf die Schaltfläche ganz links der in-App-Symbolleiste klicken (oder indem Sie zu **Debuggen > Fenster > Live Visual Tree**) wechseln. Nachdem das Fenster geöffnet ist, ziehen Sie es von der Andock Position Weg, damit wir dieses Fenster und das Fenster **Live Properties** nebeneinander betrachten können.

1. Erweitern Sie im Fenster **Visuelle Echtzeitstruktur** den Knoten **ContentPresenter**. Es sollte Knoten für die Schaltfläche und das Listenfeld enthalten. Erweitern Sie das Listenfeld (**ScrollContentPresenter** und **ItemsPresenter**), um die Listenfeldelemente zu suchen.

   ::: moniker range=">= vs-2019"
   Wenn der **ContentPresenter** -Knoten nicht angezeigt wird, schalten Sie das Symbol **nur eigenen XAML** -Code auf der Symbolleiste ein. Ab Visual Studio 2019 Version 16,4 wird die Ansicht der XAML-Elemente standardmäßig mit der Funktion "nur mein XAML" vereinfacht. Sie können [Diese Einstellung](../debugger/general-debugging-options-dialog-box.md) auch in Optionen deaktivieren, um alle XAML-Elemente immer anzuzeigen.
   ::: moniker-end

   Das Fenster sieht wie folgt aus:

   ::: moniker range=">= vs-2019"
   ![ListBoxItems in der visuellen Echtzeitstruktur](../debugger/media/vs-2019/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![ListBoxItems in der visuellen Echtzeitstruktur](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end

1. Kehren Sie zum Anwendungsfenster zurück, und fügen Sie ein paar weitere Elemente hinzu. In **Visuelle Echtzeitstruktur** sollten mehr Listenfeldelemente angezeigt werden.

1. Sehen wir uns nun die Eigenschaften eines der Listenfeld Elemente an.

   Wählen Sie das erste Listenfeldelement in **Visuelle Echtzeitstruktur** aus, und klicken Sie auf das Symbol **Eigenschaften anzeigen** auf der Symbolleiste. Der **Live-Eigenschaften-Explorer** wird angezeigt. Beachten Sie, dass das Feld " **Content** " den Wert "item1" hat und das Feld **Hintergrund**  >  **Farbe** **#FFFFFFE0** ist.

1. Wechseln Sie zurück zu **Visuelle Echtzeitstruktur**, und wählen Sie das zweite Listenfeldelement aus. Der **Live Property Explorer** sollte anzeigen, dass das **Inhalts** Feld "item2" ist, und das Feld **Hintergrund**  >  **Farbe** ist **#FFD3D3D3** (abhängig vom Design).

   > [!NOTE]
   > Ein gelber Rahmen um eine Eigenschaft im **Live-Eigenschaften-Explorer** bedeutet, dass der Eigenschafts Wert über eine Bindung festgelegt wird, z. b `Color = {BindingExpression}` .. Ein grüner Rahmen bedeutet, dass der Wert mit einer Ressource wie festgelegt wird, z `Color = {StaticResource MyBrush}` . b..

   Die tatsächliche Struktur der XAML weist eine Menge Elemente auf, an denen Sie möglicherweise nicht direkt interessiert sind. Wenn Sie sich darüber hinaus nicht gut mit dem Code auskennen, ist die Navigation in der Struktur zum Suchen des gewünschten Elements möglicherweise kompliziert. Daher bietet **Visuelle Echtzeitstruktur** mehrere Möglichkeiten zum Verwenden der Benutzeroberfläche der Anwendung, damit Sie die zu prüfenden Elemente finden können.

   ::: moniker range=">= vs-2019"
   **Wählen Sie ein Element in der ausgelaufenden Anwendung aus**. Sie können diesen Modus aktivieren, wenn Sie die Schaltfläche ganz links auf der Symbolleiste in **Visuelle Echtzeitstruktur** auswählen. Wenn dieser Modus aktiviert ist, können Sie ein Benutzeroberflächenelement in der Anwendung auswählen, und **Visuelle Echtzeitstruktur** (gilt auch für den **Live-Eigenschaften-Explorer**) wird automatisch aktualisiert, um den Knoten in der Struktur anzuzeigen, die diesem Element und der zugehörigen Eigenschaften entspricht. Ab Visual Studio 2019 Version 16,4 können Sie [das Verhalten der Elementauswahl konfigurieren](../debugger/general-debugging-options-dialog-box.md).

   **Zeigen Sie Layoutadorner in der ausgeführten Anwendung an**. Sie können diesen Modus aktivieren, wenn Sie die Schaltfläche auswählen, die sich direkt rechts neben der Schaltfläche „Auswahl aktivieren“ befindet. Wenn die Option zum **Anzeigen der Layoutadorner** aktiviert ist, zeigt das Anwendungsfenster horizontale und vertikale Linien entlang der Grenzen des ausgewählten Objekts an, sodass Sie sehen können, woran es ausgerichtet wird. Außerdem werden Rechtecke zur Darstellung der Ränder angezeigt. Aktivieren Sie z. b. die Optionen **SELECT-Element** und **Layout anzeigen** , und wählen Sie in der Anwendung den Block **Element Text hinzufügen** aus. Der Textblockknoten sollte in **Visuelle Echtzeitstruktur** und die Textblockeigenschaften sollten im **Live-Eigenschaften-Explorer** angezeigt werden. Ferner sehen Sie die horizontalen und vertikalen Linien auf den Grenzen des Textblocks.

   ![LivePropertyViewer in DisplayLayout](../debugger/media/vs-2019/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **Vorschau für Auswahl**. Sie können diesen Modus aktivieren, indem Sie die dritte Schaltfläche von links auf der Live Visual Tree-Symbolleiste auswählen. Dieser Modus zeigt die XAML an, in der das Element deklariert wurde, wenn Sie über Zugriff auf den Quellcode der Anwendung verfügen. Wählen Sie **Element auswählen** und **Vorschau Auswahl** aus, und wählen Sie dann die Schaltfläche in der Testanwendung aus. Die Datei „MainWindow.xaml“ wird in Visual Studio geöffnet, und der Cursor wird auf der Zeile platziert, auf der die Schaltfläche definiert ist.
   ::: moniker-end

   ::: moniker range="vs-2017"
   **Aktivieren Sie die Auswahl in der ausgeführten Anwendung**. Sie können diesen Modus aktivieren, wenn Sie die Schaltfläche ganz links auf der Symbolleiste in **Visuelle Echtzeitstruktur** auswählen. Wenn dieser Modus aktiviert ist, können Sie ein Benutzeroberflächenelement in der Anwendung auswählen, und **Visuelle Echtzeitstruktur** (gilt auch für den **Live-Eigenschaften-Explorer**) wird automatisch aktualisiert, um den Knoten in der Struktur anzuzeigen, die diesem Element und der zugehörigen Eigenschaften entspricht.

   **Zeigen Sie Layoutadorner in der ausgeführten Anwendung an**. Sie können diesen Modus aktivieren, wenn Sie die Schaltfläche auswählen, die sich direkt rechts neben der Schaltfläche „Auswahl aktivieren“ befindet. Wenn die Option zum **Anzeigen der Layoutadorner** aktiviert ist, zeigt das Anwendungsfenster horizontale und vertikale Linien entlang der Grenzen des ausgewählten Objekts an, sodass Sie sehen können, woran es ausgerichtet wird. Außerdem werden Rechtecke zur Darstellung der Ränder angezeigt. Aktivieren Sie beispielsweise **Auswahl aktivieren** und **Layout anzeigen**, und wählen Sie den Textblock **Element hinzufügen** in der Anwendung aus. Der Textblockknoten sollte in **Visuelle Echtzeitstruktur** und die Textblockeigenschaften sollten im **Live-Eigenschaften-Explorer** angezeigt werden. Ferner sehen Sie die horizontalen und vertikalen Linien auf den Grenzen des Textblocks.

   ![LivePropertyViewer in DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **Vorschau für Auswahl**. Sie können diesen Modus aktivieren, indem Sie die dritte Schaltfläche von links auf der Live Visual Tree-Symbolleiste auswählen. Dieser Modus zeigt die XAML an, in der das Element deklariert wurde, wenn Sie über Zugriff auf den Quellcode der Anwendung verfügen. Wählen Sie **Auswahl aktivieren** und **Vorschau für Auswahl** und dann die Schaltfläche in der Testanwendung aus. Die Datei „MainWindow.xaml“ wird in Visual Studio geöffnet, und der Cursor wird auf der Zeile platziert, auf der die Schaltfläche definiert ist.
   ::: moniker-end

## <a name="use-xaml-tools-with-running-applications"></a>Verwenden von XAML-Tools mit laufenden Anwendungen

Sie können diese XAML-Tools sogar dann verwenden, wenn Sie nicht über den Quellcode verfügen. Beim Anfügen an eine ausgeführte XAML-Anwendung können Sie **Visuelle Echtzeitstruktur** auch für die Benutzeroberflächenelemente der Anwendung verwenden. Im Folgenden finden Sie ein Beispiel unter Verwendung derselben WPF-Testanwendung, die wir zuvor verwendet haben.

1. Starten Sie die **TestXaml**-Anwendung in der Releasekonfiguration. Das Anfügen an einen in einer **Debug**-Konfiguration ausgeführten Prozess ist nicht möglich.

2. Öffnen Sie eine zweite Instanz von Visual Studio, und klicken Sie auf **Debuggen > An den Prozess anhängen**. Suchen Sie in der Liste der verfügbaren Prozesse nach der Datei **TestXaml.exe**, und klicken Sie auf **Anfügen**.

3. Die Anwendung wird ausgeführt.

4. Öffnen Sie in der zweiten Visual Studio-Instanz **Visuelle Echtzeitstruktur** (**Debuggen > Fenster > Visuelle Echtzeitstruktur**). Es sollten die **TestXaml**-Benutzeroberflächenelemente angezeigt werden, und Sie sollten sie bearbeiten können, während Sie die Anwendung direkt debuggen.

## <a name="see-also"></a>Weitere Informationen

[Schreiben und Debuggen von XAML-Code mit XAML Hot Neuladen](xaml-hot-reload.md)
