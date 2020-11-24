---
title: Hinzufügen des Benutzer Steuer Elements zur Start Seite | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie der Start Seite in Visual Studio ein Windows Presentation Foundation (WPF)-Benutzer Steuerelement hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: fa812b477f88b03b8f0d4bdcba6c69f009ec2894
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597547"
---
# <a name="add-user-control-to-the-start-page"></a>Hinzufügen eines Benutzer Steuer Elements zur Start Seite

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie einer benutzerdefinierten Start Seite einen dll-Verweis hinzufügen. Im Beispiel wird der Projekt Mappe ein Benutzer Steuerelement hinzugefügt, das Benutzer Steuerelement erstellt und anschließend aus der *XAML* -Datei der Start Seite auf die Assembly verwiesen. Eine neue Registerkarte hostet das Benutzer Steuerelement, das als grundlegender Webbrowser fungiert.

Sie können denselben Prozess zum Hinzufügen beliebiger Assemblys verwenden, die aus einer *XAML* -Datei aufgerufen werden können.

## <a name="add-a-wpf-user-control-to-the-solution"></a>Hinzufügen eines WPF-Benutzer Steuer Elements zur Projekt Mappe

Fügen Sie zunächst der Projekt Mappe Start Seite ein Windows Presentation Foundation (WPF)-Benutzer Steuerelement hinzu.

1. Erstellen Sie eine Start Seite mithilfe von, die Sie in [Erstellen einer benutzerdefinierten Startseite](../extensibility/creating-a-custom-start-page.md)erstellt haben.

2. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf die Projekt Mappe, klicken Sie auf **Hinzufügen** und dann auf **Neues Projekt**.

3. Erweitern Sie im linken Bereich des Dialog Felds **Neues Projekt** entweder den Knoten **Visual Basic** oder **Visual c#** , und klicken Sie auf **Windows**. Wählen Sie im mittleren Bereich **WPF-Benutzer Steuerelement Bibliothek** aus.

4. Benennen Sie das Steuerelement, `WebUserControl` und klicken Sie auf **OK**.

## <a name="implement-the-user-control"></a>Implementieren des Benutzer Steuer Elements

Um ein WPF-Benutzer Steuerelement zu implementieren, erstellen Sie die Benutzeroberfläche (UI) in XAML, und schreiben Sie dann die Code Behind-Ereignisse in c# oder eine andere .NET-Sprache.

### <a name="to-write-the-xaml-for-the-user-control"></a>So schreiben Sie den XAML-Code für das Benutzer Steuerelement

1. Öffnen Sie die XAML-Datei für das Benutzer Steuerelement. Fügen Sie im-Element dem- `<Grid>` Steuerelement die folgenden Zeilen Definitionen hinzu.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. `<Grid>`Fügen Sie im Hauptelement das folgende neue `<Grid>` Element hinzu, das ein Textfeld zum Eingeben von Webadressen und eine Schaltfläche zum Festlegen der neuen Adresse enthält.

    ```xml
    <Grid Grid.Row="0">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>
        <TextBox x:Name="UserSource" Grid.Column="0" />
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
    </Grid>
    ```

3. Fügen Sie den folgenden Frame dem Element der obersten Ebene `<Grid>` direkt nach dem- `<Grid>` Element hinzu, das die Schaltfläche und das Textfeld enthält.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. Im folgenden Beispiel wird der abgeschlossene XAML-Code für das Benutzer Steuerelement gezeigt.

    ```xml
    <UserControl x:Class="WebUserControl.UserControl1"
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                 mc:Ignorable="d"
                 d:DesignHeight="300" d:DesignWidth="300">
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid Grid.Row="0">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
                <TextBox x:Name="UserSource" Grid.Column="0" />
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
            </Grid>
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
        </Grid>
    </UserControl>

    ```

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>So schreiben Sie Code Behind-Ereignisse für das Benutzer Steuerelement

1. Doppelklicken Sie im XAML-Designer auf die Schaltfläche **Adresse festlegen** , die Sie dem Steuerelement hinzugefügt haben.

    Die Datei *UserControl1.cs* wird im Code-Editor geöffnet.

2. Füllen Sie den SetButton_Click-Ereignis Handler wie folgt aus.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
    {
        try
        {
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);
        }
        catch (Exception error)
        {
            MessageBox.Show(error.Message);
        }
    }
    ```

    Mit diesem Code wird die im Textfeld typisierte Webadresse als Ziel für den Webbrowser festgelegt. Wenn die Adresse nicht gültig ist, löst der Code einen Fehler aus.

3. Außerdem müssen Sie das WebFrame_Navigated-Ereignis behandeln:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Erstellen Sie die Projektmappe.

## <a name="add-the-user-control-to-the-start-page"></a>Hinzufügen des Benutzer Steuer Elements zur Start Seite

Um dieses Steuerelement für das Startseiten Projekt verfügbar zu machen, fügen Sie in der Projektdatei der Startseite einen Verweis auf die neue Steuerelement Bibliothek hinzu. Anschließend können Sie das Steuerelement dem XAML-Markup der Start Seite hinzufügen.

1. Klicken Sie in **Projektmappen-Explorer** im Projekt Start Seite mit der rechten Maustaste auf **Verweise** , und klicken Sie dann auf **Verweis hinzufügen**.

2. Wählen Sie auf der Registerkarte **Projekte** die Option **WebUserControl** aus, und klicken Sie dann auf **OK**.

3. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

    Durch die Projekt Mappe wird das Benutzer Steuerelement für andere Dateien in der Projekt Mappe IntelliSense zur Verfügung gestellt.

    Fügen Sie der Assembly einen Namespace Verweis hinzu, und platzieren Sie das Steuerelement auf der Seite, um das Steuerelement dem XAML-Markup der Start Seite hinzuzufügen.

### <a name="to-add-the-control-to-the-markup"></a>So fügen Sie dem Markup das Steuerelement hinzu

1. Öffnen Sie in **Projektmappen-Explorer** die Datei Start Page *. XAML* .

2. Fügen Sie im **XAML** -Bereich die folgende Namespace Deklaration dem Element der obersten Ebene hinzu <xref:System.Windows.Controls.Grid> .

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. Scrollen Sie im **XAML** -Bereich zum- \<Grid> Abschnitt.

    Der-Abschnitt enthält ein- <xref:System.Windows.Controls.TabControl> Element in einem- <xref:System.Windows.Controls.Grid> Element.

4. Fügen Sie ein- \<TabControl> Element mit einem hinzu \<TabItem> , das einen Verweis auf das Benutzer Steuerelement enthält.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Nun können Sie das Steuerelement testen.

## <a name="test-a-manually-created-custom-start-page"></a>Testen einer manuell erstellten benutzerdefinierten Start Seite

1. Kopieren Sie die XAML-Datei und alle unterstützenden Textdateien oder Markup Dateien in den Ordner *%UserProfile%\My Documents\Visual Studio 2015 \ \\ StartPages* .

2. Wenn die Startseite auf Steuerelemente oder Typen in Assemblys verweist, die nicht von Visual Studio installiert werden, kopieren Sie die Assemblys, und fügen Sie Sie in den _Visual Studio-Installationsordner_**\\ \common7\ide\privateassemblys** ein.

3. Geben Sie an einer Visual Studio-Eingabeaufforderung **devenv/rootsuffix Exp** ein, um eine experimentelle Instanz von Visual Studio zu öffnen.

4. Wechseln Sie in der experimentellen Instanz zur Seite **Tools** Extras  >  **Optionen**  >  **Umgebung**  >  **Start** , und wählen Sie die XAML-Datei aus der Dropdown Liste **Start Seite anpassen** aus.

5. Klicken Sie im Menü **Ansicht** auf **Startseite**.

    Die benutzerdefinierte Startseite sollte angezeigt werden. Wenn Sie Dateien ändern möchten, müssen Sie die experimentelle Instanz schließen, die Änderungen durchführen, die geänderten Dateien kopieren und einfügen und dann die experimentelle Instanz erneut öffnen, um die Änderungen anzuzeigen.

## <a name="see-also"></a>Siehe auch

- [WPF-Container Steuerelemente](/previous-versions/bb675291(v=vs.110))
- [Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Start Seite](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)