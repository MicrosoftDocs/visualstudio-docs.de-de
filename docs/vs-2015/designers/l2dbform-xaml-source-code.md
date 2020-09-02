---
title: L2DBForm.xaml-Quellcode | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 624e96d4-6d27-4195-8ac2-2f3835f6c57e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc0ec53c35f87751efe78359f582e5f4297143c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664274"
---
# <a name="l2dbformxaml-source-code"></a>L2DBForm.xaml-Quellcode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieses Thema enthält und beschreibt die XAML-Quelldatei für die in [Beispiel für die WPF-Datenbindung mit LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)verwendete Datei L2DBForm.xaml.

## <a name="overall-ui-structure"></a>Allgemeine Struktur der Benutzeroberfläche
 Diese Datei enthält, typisch für ein WPF-Projekt, ein übergeordnetes Element, und zwar ein <xref:System.Windows.Window> -XML-Element, das mit der hergeleiteten `L2XDBFrom` -Klasse im `LinqToXmlDataBinding` -Namespace verknüpft ist.

 Der Clientbereich befindet sich innerhalb eines <xref:System.Windows.Controls.StackPanel> -Steuerelements, das mit einem hellblauen Hintergrund versehen ist. Dieses Steuerelement enthält vier <xref:System.Windows.Controls.DockPanel> -Benutzeroberflächenabschnitte, die durch <xref:System.Windows.Controls.Separator> -Balken voneinander getrennt sind. Der Zweck dieser Abschnitte wird im **vorherigen Thema** unter [Hinweise](../designers/walkthrough-linqtoxmldatabinding-example.md)beschrieben.

 Jeder Abschnitt enthält eine Bezeichnung, mit dem er identifiziert wird. In den ersten beiden Abschnitten wird diese Bezeichnung durch die Verwendung eines <xref:System.Windows.FrameworkElement.LayoutTransform%2A>-Elements um 90° gedreht. Der restliche Teil des Abschnitts enthält für den Zweck des Abschnitts passende Benutzeroberflächenelemente wie Textblöcke, Textfelder, Schaltflächen usw. Mitunter wird zur Ausrichtung dieser untergeordneten Steuerelemente ein untergeordnetes <xref:System.Windows.Controls.StackPanel> -Steuerelement verwendet.

## <a name="window-resource-section"></a>Abschnitt "Window.Resources"
 Das `<Window.Resources>` -Starttag in Zeile 9 gibt den Anfang des Abschnitts &lt;legacyBold&gt;Window.Resources&lt;/legacyBold&gt; an. Der Abschnitt endet mit dem Endtag in Zeile 35.

 Das `<ObjectDataProvider>` -Tag, das sich über die Zeilen 11 bis 25 erstreckt, deklariert einen <xref:System.Windows.Data.ObjectDataProvider>mit dem Namen `LoadedBooks`, der als Quelle ein <xref:System.Xml.Linq.XElement> verwendet. Dieses <xref:System.Xml.Linq.XElement> wird initialisiert, indem ein eingebettetes XML-Dokument (ein `CDATA` -Element) analysiert wird. Beachten Sie, dass Leerraum beim Deklarieren des eingebetteten XML-Dokuments und auch beim Analysieren des Dokuments beibehalten wird. Der Grund: Das <xref:System.Windows.Controls.TextBlock> -Steuerelement, das zum Anzeigen des unformatierten XML verwendet wird, besitzt keine speziellen XML-Formatierungsfunktionen.

 Schließlich wird in den Zeilen 28 bis 34 eine <xref:System.Windows.DataTemplate> mit dem Namen `BookTemplate` definiert. Diese Vorlage wird zum Anzeigen der Einträge im Abschnitt **Book List** der Benutzeroberfläche verwendet. Sie verwendet die Datenbindung und dynamische LINQ to XML-Eigenschaften, um über die folgenden Zuweisungen die Buch-ID und den Buchnamen abzurufen:

```
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"
```

## <a name="data-binding-code"></a>Code für die Datenbindung
 Zusätzlich zum <xref:System.Windows.DataTemplate> -Element wird die Datenbindung auch an einer Reihe anderer Stellen in der Datei verwendet.

 Im `<StackPanel>` -Starttag in Zeile 38 wird die <xref:System.Windows.FrameworkElement.DataContext%2A> -Eigenschaft dieses Elements auf den `LoadedBooks` -Datenanbieter gesetzt.

```
DataContext="{Binding Source={StaticResource LoadedBooks}}
```

 Damit ist der <xref:System.Windows.Controls.TextBlock> mit dem Namen `tbRawXml` (in Zeile 46) in der Lage, durch Bindung dieser Daten an die `Xml` -Eigenschaft des Datenanbieters das unformatierte XML anzuzeigen:

```
Text="{Binding Path=Xml}"
```

 Das <xref:System.Windows.Controls.ListBox> -Steuerelement in den Zeilen 58 bis 62 im Abschnitt **Book List** der Benutzeroberfläche legt als Vorlage für ihre Anzeigeelemente die im &lt;legacyBold&gt;Window.Resources&lt;/legacyBold&gt;-Abschnitt definierte `BookTemplate` -Vorlage fest:

```
ItemTemplate ="{StaticResource BookTemplate}"
```

 Anschließend werden die tatsächlichen Werte der Bücher in den Zeilen 59 bis 62 an dieses Listenfeld gebunden:

```
<ListBox.ItemsSource>
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
</ListBox.ItemsSource>
```

 Der dritte Abschnitt der Benutzeroberfläche, **Edit Selected Book**, bindet zuerst das <xref:System.Windows.FrameworkElement.DataContext%2A> -Element des übergeordneten <xref:System.Windows.Controls.StackPanel> -Steuerelements an den aktuell ausgewählten Eintrag im Abschnitt **Book List** der Benutzeroberfläche (Zeile 82):

```
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"
```

 Anschließend verwendet der Abschnitt die bidirektionale Datenbindung, sodass die aktuellen Werte der Buchelemente in den beiden Textfeldern in diesem Abschnitt angezeigt und entsprechend aktualisiert werden. Die Datenbindung an dynamische Eigenschaften ähnelt der Datenbindung, die in der `BookTemplate` -Datenvorlage verwendet wird:

```
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"
```

 Der letzte Abschnitt der Benutzeroberfläche, **Add New Book**, verwendet in seinem XAML-Code keine Datenbindung. Stattdessen findet sich solcher Code in seinem Ereignishandlercode in der Datei &lt;legacyBold&gt;L2DBForm.xaml.cs&lt;/legacyBold&gt;.

## <a name="example"></a>Beispiel

### <a name="description"></a>BESCHREIBUNG

> [!NOTE]
> Wir empfehlen, den folgenden Code in einen Code-Editor, z. B. den C#-Quellcode-Editor in Visual Studio, zu kopieren, weil dort die Zeilennummern einfacher zu verfolgen sind.

### <a name="code"></a>Code

```xml
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:system="clr-namespace:System;assembly=mscorlib"
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"
    xmlns:local="clr-namespace:LinqToXmlDataBinding"
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">

    <Window.Resources>
        <!-- Books provider and inline data -->
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">
            <ObjectDataProvider.MethodParameters>
                <system:String xml:space="preserve">
<![CDATA[
<books xmlns="http://www.mybooks.com">
  <book id="0">book zero</book>
  <book id="1">book one</book>
  <book id="2">book two</book>
  <book id="3">book three</book>
</books>
]]>
                </system:String>
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>
            </ObjectDataProvider.MethodParameters>
        </ObjectDataProvider>

        <!-- Template for use in Books List listbox. -->
        <DataTemplate x:Key="BookTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>
                <TextBlock Margin="3" Text="-"/>
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>
            </StackPanel>
        </DataTemplate>
    </Window.Resources>

    <!-- Main visual content container -->
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">
        <!-- Raw XML display section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML
            <Label.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Label.LayoutTransform>
            </Label>
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- List box to display all books section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List
                <Label.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Label.LayoutTransform>
            </Label>
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">
                <ListBox.ItemsSource>
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
                </ListBox.ItemsSource>
            </ListBox>
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">
            <Button.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Button.LayoutTransform>
            </Button>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Edit current selection section -->
        <DockPanel Margin="5">
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">
                    Changes are live!
                <TextBlock.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </TextBlock.LayoutTransform>
            </TextBlock>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book ID and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book Value and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Add new book section -->
        <DockPanel Margin="5">
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book
                <Button.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Button.LayoutTransform>
            </Button>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>
                <StackPanel Margin="1">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="tbAddID" Width="410">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="tbAddValue" Width="410" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>
    </StackPanel>
</Window>

```

### <a name="comments"></a>Kommentare
 Informationen zu den c#-Quellcode für die den WPF-Benutzeroberflächen Elementen zugeordneten Ereignishandler finden Sie unter [L2DBForm.XAML.cs Source Code](../designers/l2dbform-xaml-cs-source-code.md).

## <a name="see-also"></a>Weitere Informationen
 Exemplarische Vorgehens [Weise: LinqToXmlDataBinding-Beispiel](../designers/walkthrough-linqtoxmldatabinding-example.md) [L2DBForm.XAML.cs Quellcode](../designers/l2dbform-xaml-cs-source-code.md)
