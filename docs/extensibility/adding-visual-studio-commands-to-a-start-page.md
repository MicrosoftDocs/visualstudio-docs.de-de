---
title: Hinzufügen von Visual Studio-Befehlen zu einer Start Seite | Microsoft-Dokumentation
description: Erfahren Sie mehr über die verschiedenen Möglichkeiten, Visual Studio-Befehle auf einer benutzerdefinierten Start Seite in Visual Studio an XAML-Objekte zu binden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 7784b077093660eb5f9c9a0bf471a8965811ba72
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597521"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Hinzufügen von Visual Studio-Befehlen zu einer Start Seite

Wenn Sie eine benutzerdefinierte Start Seite erstellen, können Sie Ihr Visual Studio-Befehle hinzufügen. In diesem Dokument werden die verschiedenen Möglichkeiten erläutert, Visual Studio-Befehle auf einer Start Seite an XAML-Objekte zu binden.

Weitere Informationen zu Befehlen in XAML finden Sie unter [Befehls Übersicht](/dotnet/framework/wpf/advanced/commanding-overview) .

## <a name="add-commands-from-the-command-well"></a>Befehle aus Befehls Quelle hinzufügen

Die in [Erstellen einer benutzerdefinierten Start](../extensibility/creating-a-custom-start-page.md) Seite erstellte Startseite <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> hat die <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> Namespaces und wie folgt hinzugefügt.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Fügen Sie aus dem AssemblyMicrosoft.VisualStudio.Shell.Immutable.11.0.dlleinen weiteren Namespace für Microsoft. ** VisualStudio. Shell hinzu. (Möglicherweise müssen Sie im Projekt einen Verweis auf diese Assembly hinzufügen.)

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

Sie können den- `vscom:` Alias verwenden, um Visual Studio-Befehle an XAML-Steuerelemente auf der Seite zu binden, indem Sie die- <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> Eigenschaft des Steuer Elements auf festlegen `vscom:VSCommands.ExecuteCommand` . Anschließend können Sie die- <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> Eigenschaft auf den Namen des auszuführenden Befehls festlegen, wie im folgenden Beispiel gezeigt.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> Der `x:` Alias, der sich auf das XAML-Schema bezieht, ist am Anfang aller Befehle erforderlich.

 Sie können den Wert der- `Command` Eigenschaft auf einen beliebigen Befehl festlegen, auf den über das **Befehls** Fenster zugegriffen werden kann. Eine Liste der verfügbaren Befehle finden Sie unter [Visual Studio-Befehls Aliase](../ide/reference/visual-studio-command-aliases.md).

 Wenn für den hinzu zufügenden Befehl ein zusätzlicher Parameter erforderlich ist, können Sie ihn dem Wert der-Eigenschaft hinzufügen `CommandParameter` . Trennen Sie Parameter von Befehlen mithilfe von Leerzeichen, wie im folgenden Beispiel gezeigt.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Aufrufe von Erweiterungen aus der Befehlszeile
 Sie können Befehle aus registrierten VSPackages mithilfe derselben Syntax, die zum Abrufen anderer Visual Studio-Befehle verwendet wird, abrufen. Wenn beispielsweise ein installiertes VSPackage dem Menü **Ansicht** einen **Startseiten** Befehl hinzufügt, können Sie diesen Befehl durch Festlegen von `CommandParameter` auf Abrufen `View.HomePage` .

> [!NOTE]
> Wenn Sie einen Befehl aufrufen, der einem VSPackage zugeordnet ist, muss das Paket geladen werden, wenn der Befehl aufgerufen wird.

## <a name="add-commands-from-assemblies"></a>Befehle aus Assemblys hinzufügen
 Zum Aufrufen eines Befehls aus einer Assembly oder zum Zugreifen auf Code in einem VSPackage, das keinem Menübefehl zugeordnet ist, müssen Sie einen Alias für die Assembly erstellen und dann den Alias aufrufen.

### <a name="to-call-a-command-from-an-assembly"></a>So greifen Sie einen Befehl aus einer Assembly an

1. Fügen Sie in der Projekt Mappe einen Verweis auf die Assembly hinzu.

2. Fügen Sie am Anfang der Datei " *StartPage. XAML* " eine Namespace-Direktive für die Assembly hinzu, wie im folgenden Beispiel gezeigt.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Rufen Sie den Befehl auf, indem Sie die- `Command` Eigenschaft eines XAML-Objekts festlegen, wie im folgenden Beispiel gezeigt.

     XAML

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Sie müssen die Assembly kopieren und anschließend in *. \\ einfügen. {Visual Studio-Installationsordner} \common7\ide\privateassemblys \* , um sicherzustellen, dass er geladen wird, bevor er aufgerufen wird.

## <a name="add-commands-with-the-dte-object"></a>Hinzufügen von Befehlen mit dem DTE-Objekt
 Sie können auf das DTE-Objekt von einer Start Seite aus zugreifen, sowohl in Markup als auch im Code.

 In Markup können Sie darauf zugreifen, indem Sie die Syntax der [Bindungs Markup Erweiterung](/dotnet/framework/wpf/advanced/binding-markup-extension) zum Aufrufen des- <xref:EnvDTE.DTE> Objekts verwenden. Sie können diesen Ansatz verwenden, um eine Bindung an einfache Eigenschaften wie z. b. die zurückgegebenen Auflistungen herzustellen Das folgende Beispiel zeigt ein <xref:System.Windows.Controls.TextBlock> Steuerelement, das an die-Eigenschaft gebunden wird <xref:EnvDTE._DTE.Name%2A> , und ein-Steuerelement, <xref:System.Windows.Controls.ListBox> das die Eigenschaften der Auflistung auflistet, die <xref:EnvDTE.Window.Caption%2A> von der-Eigenschaft zurückgegeben wird <xref:EnvDTE._DTE.Windows%2A> .

```xml
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>
<ListBox ItemsSource="{Binding Path=DTE.Windows}">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding Path=Caption}"/>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox
```

 Ein Beispiel finden Sie unter Exemplarische Vorgehensweise [: Speichern von Benutzereinstellungen auf einer Start Seite](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).

## <a name="see-also"></a>Siehe auch

- [Hinzufügen des Benutzer Steuer Elements zur Start Seite](../extensibility/adding-user-control-to-the-start-page.md)
