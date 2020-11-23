---
title: Verwenden von Entwurfszeitdaten mit dem XAML-Designer in Visual Studio
description: Hier erfahren Sie, wie Sie Entwurfszeitdaten in XAML verwenden.
ms.date: 11/10/2020
ms.topic: overview
author: alihamie
ms.author: tglee
manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: bda4af3a3985ec6fc3aae1e991b7f5f622d67965
ms.sourcegitcommit: e8a13978131f257d91ce37c5a2e0d153a4c400ef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704000"
---
# <a name="use-design-time-data-with-the-xaml-designer-in-visual-studio"></a>Verwenden von Entwurfszeitdaten mit dem XAML-Designer in Visual Studio

Einige Layouts sind ohne Daten schwer zu visualisieren. In diesem Dokument lernen Sie einen der Ansätze kennen, die Entwickler, die an Desktopprojekten arbeiten, zum Simulieren von Daten im XAML-Designer verwenden können. Hierfür wird der vorhandene ignorierbare Namespace „d:“ verwendet. Mit diesem Ansatz können Sie Ihren Seiten oder Steuerelementen schnell Entwurfszeitdaten hinzufügen, ohne dass ein vollständiges simuliertes ViewModel erstellt werden muss. Außerdem können Sie einfach testen, wie eine Eigenschaftsänderung sich auf Ihre Anwendung auswirken kann, ohne befürchten zu müssen, dass sie sich auf die Releasebuilds auswirkt. Alle d:-Daten werden nur vom XAML-Designer verwendet, und es werden keine Werte aus ignorierbaren Namespaces in die Anwendung kompiliert.

> [!NOTE]
> Wenn Sie Xamarin.Forms verwenden, finden Sie weitere Informationen im Artikel zu [Entwurfszeitdaten in Xamarin.Forms](/xamarin/xamarin-forms/xaml/xaml-previewer/design-time-data).

## <a name="design-time-data-basics"></a>Grundlegende Informationen zu Entwurfszeitdaten

Entwurfszeitdaten sind simulierte Daten, die Sie festlegen, um die Steuerelemente im XAML-Designer besser visualisieren zu können. Fügen Sie zunächst dem Header Ihres XAML-Dokuments die folgenden Codezeilen hinzu, wenn sie nicht bereits vorhanden sind:

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Nach dem Hinzufügen der Namespaces können Sie vor alle Attribute oder Steuerelemente `d:` schreiben, um sie nur im XAML-Designer anzuzeigen und nicht zur Laufzeit.

Beispielsweise können Sie Text in einem TextBlock-Element hinzufügen, an das normalerweise Daten gebunden sind.

```xml
<TextBlock Text="{Binding Name}" d:Text="Name!" />
```

[![Entwurfszeitdaten mit Text in einem TextBlock-Element](media\xaml-design-time-textblock.png "Entwurfszeitdaten mit Text in einer Bezeichnung")](media\xaml-design-time-textblock.png#lightbox)

In diesem Beispiel würde der XAML-Designer ohne `d:Text` für das TextBlock-Element nichts anzeigen. Stattdessen wird dort „Name!“ angezeigt, wo das TextBlock-Element zur Laufzeit echte Daten enthält.

Sie können `d:` mit Attributen für jedes beliebige UWP- oder WPF-.NET Core-Steuerelement verwenden, z. B. für Farben, Schriftgrade und Abstände. Sie können „d:“ sogar dem Steuerelement selbst hinzufügen.

```xml
<d:Button Content="Design Time Button" />
```

[![Entwurfszeitdaten mit einem Schaltflächen-Steuerelement](media\xaml-design-time-button.png "Entwurfszeitdaten mit einem Schaltflächen-Steuerelement")](media\xaml-design-time-button.png#lightbox)

In diesem Beispiel wird die Schaltfläche nur zur Entwurfszeit angezeigt. Verwenden Sie diese Methode, um einen Platzhalter für ein benutzerdefiniertes Steuerelement anzuzeigen oder um verschiedene Steuerelemente zu testen. Alle `d:`-Attribute und -Steuerelemente werden zur Laufzeit ignoriert.

## <a name="preview-images-at-design-time"></a>Anzeigen von Vorschaubildern zur Entwurfszeit

Sie können für Bilder, die an die Seite gebunden sind oder dynamisch geladen werden, eine Quelle für die Entwurfszeit festlegen. Fügen Sie das Bild, das Sie im XAML-Designer anzeigen möchten, dem Projekt hinzu. Sie können dieses Bild dann zur Entwurfszeit im XAML-Designer anzeigen:

```xml
<Image Source={Binding ProfilePicture} d:Source="DesignTimePicture.jpg" />
```

> [!NOTE]
> Das Bild in diesem Beispiel muss sich in der Projektmappe befinden.

## <a name="design-time-data-for-listviews"></a>Entwurfszeitdaten für ListView-Elemente

ListView-Elemente sind eine beliebte Möglichkeit zum Anzeigen von Daten in Desktop-Apps. Allerdings sind sie ohne Daten schwer zu visualisieren. Sie können dieses Feature verwenden, um ein Inline-ItemsSource-Element für die Entwurfszeitdaten zu erstellen. Der XAML-Designer zeigt den Inhalt dieses Arrays in Ihrem ListView-Element zur Entwurfszeit an. Dies ist ein Beispiel für WPF für .NET Core. Wenn Sie den Typ „system:String“ verwenden möchten, denken Sie daran, `xmlns:system="clr-namespace:System;assembly=mscorlib` in den XAML-Header aufzunehmen.

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type system:String}">
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </x:Array>
        </d:ListView.ItemsSource>
    <ListView.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding ItemName}" d:Text="{Binding .}" />
        </DataTemplate>
    </ListView.ItemTemplate>
   </ListView>
</StackPanel>
```

[![Entwurfszeitdaten mit einem ListView-Element](media\xaml-design-time-listview-strings.png "Entwurfszeitdaten mit einem ListView-Element")](media\xaml-design-time-listview-strings.png#lightbox)

Das obige Beispiel zeigt ein ListView-Element mit drei TextBlock-Elementen im XAML-Designer.

Sie können auch ein Array von Datenobjekten erstellen. Beispielsweise können öffentliche Eigenschaften eines `City`-Datenobjekts als Entwurfszeitdaten erstellt werden.

```csharp
namespace Cities.Models
{
    public class City
    {
        public string Name { get; set; }
        public string Country { get; set; }
    }
}
```

Wenn Sie die Klasse in XAML verwenden möchten, müssen Sie den Namespace in den Stammknoten importieren.

```xaml
xmlns:models="clr-namespace:Cities.Models"
```

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type models:City}">
                <models:City Name="Seattle" Country="United States"/>
                <models:City Name="London" Country="United Kingdom"/>
                <models:City Name="Panama City" Country="Panama"/>
            </x:Array>
        </d:ListView.ItemsSource>
        <ListView.ItemTemplate>
            <DataTemplate>
                 <StackPanel Orientation="Horizontal" >
                    <TextBlock Text="{Binding Name}" Margin="0,0,5,0" />
                    <TextBlock Text="{Binding Country}" />
                 </StackPanel>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
</StackPanel>
```

[![Tatsächliches Modell in Entwurfszeitdaten mit einem ListView-Element](media\xaml-design-time-listview-models.png "Tatsächliches Modell in Entwurfszeitdaten mit einem ListView-Element")](media\xaml-design-time-listview-models.png#lightbox)

Der Vorteil dieser Vorgehensweise ist, dass Sie Ihre Steuerelemente an eine statische Entwurfszeitversion Ihres Modells binden können.

## <a name="use-design-time-data-with-custom-types-and-properties"></a>Verwenden von Entwurfszeitdaten mit benutzerdefinierten Typen und Eigenschaften

Dieses Feature funktioniert standardmäßig nur mit Plattformsteuerelementen und -eigenschaften. In diesem Abschnitt werden die Schritte beschrieben, die erforderlich sind, damit Sie Ihre eigenen benutzerdefinierten Steuerelemente als Designzeit-Steuerelemente verwenden können. Dies ist eine neue Funktion, die Kunden in der Version [16.8](/visualstudio/releases/2019/release-notes/) oder höher von Visual Studio 2019 zur Verfügung steht. Es gibt drei Anforderungen, um diese Funktion nutzen zu können:

- benutzerdefinierter xmlns-Namespace

    ```xml
    xmlns:myControls="http://MyCustomControls"
    ```

- Entwurfszeitversion des Namespace: Fügen Sie hierzu einfach „/design“ an das Ende an.

     ```xml
    xmlns:myDesignTimeControls="http://MyCustomControls/design"
    ```

- Hinzufügen des Entwurfszeitpräfixes zu „mc:Ignorable“

    ```xml
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d myDesignTimeControls"
    ```

Nachdem Sie alle Schritte ausgeführt haben, können Sie das Präfix `myDesignTimeControls` verwenden, um die Designzeit-Steuerelemente zu erstellen.

```xml
<myDesignTimeControls:MyButton>I am a design time Button</myDesignTimeControls:MyButton>
```

### <a name="creating-a-custom-xmlns-namespace"></a>Erstellen eines benutzerdefinierten xmlns-Namespace

Sie müssen den benutzerdefinierten XML-Namespace dem CLR-Namespace zuordnen, in dem sich die Steuerelemente befinden, um einen benutzerdefinierten xmlns-Namespace in WPF .NET Core zu erstellen. Dies erreichen Sie, indem Sie das `XmlnsDefinition`-Attribut auf Assemblyebene in Ihrer `AssemblyInfo.cs`-Datei hinzufügen. Die Datei befindet sich im Stammverzeichnis des Projekts.

   ```C#
[assembly: XmlnsDefinition("http://MyCustomControls", "MyViews.MyButtons")]
   ```

## <a name="troubleshooting"></a>Problembehandlung

Wenn ein Problem auftritt, das in diesem Abschnitt nicht aufgeführt ist, informieren Sie uns über das Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio.md).

### <a name="requirements"></a>Anforderungen

- Für Entwurfszeitdaten ist Visual Studio 2019, Version [16.7](/visualstudio/releases/2019/release-notes) oder höher erforderlich.

- Windows-Desktopprojekte für Windows Presentation Foundation (WPF) für .NET Core und für UWP werden unterstützt. Dieses Feature ist auch im [Vorschaukanal](/visualstudio/releases/2019/release-notes-preview) für .NET Framework verfügbar. Navigieren Sie zu **Extras** > **Optionen** > **Umgebung** > **Vorschaufeatures**, klicken Sie auf **New WPF XAML Designer for .NET Framework** (Neuer WPF-XAML-Designer für .NET Framework), und starten Sie anschließend Visual Studio neu, um das Feature zu aktivieren.

- Ab Visual Studio 2019, Version 16.7 funktioniert dieses Feature für alle Standardsteuerelemente aus WPF- und UWP-Frameworks. Unterstützung für Steuerelemente von Drittanbietern ist jetzt im Previewrelease 16.8 verfügbar.

### <a name="the-xaml-designer-stopped-working"></a>Der XAML-Designer funktioniert nicht mehr

Schließen Sie die XAML-Datei, und öffnen Sie sie wieder. Bereinigen Sie außerdem das Projekt, und erstellen Sie es neu.

## <a name="see-also"></a>Siehe auch

- [Entwurfszeitdaten mit dem Xamarin.Forms-Previewer](/xamarin/xamarin-forms/xaml/xaml-Designer/design-time-data/)
- [XAML in WPF-Apps](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML in UWP-Apps](/windows/uwp/xaml-platform/xaml-overview)
- [XAML in Xamarin.Forms-Apps](/xamarin/xamarin-forms/xaml/)