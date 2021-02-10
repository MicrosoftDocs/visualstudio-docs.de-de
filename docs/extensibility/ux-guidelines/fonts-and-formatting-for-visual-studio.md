---
title: Schriftarten und Formatierungen für Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie mehr Überschrift Arten und Formatierungen für neue Features, die Sie für Visual Studio entwerfen, einschließlich der Verwendung der Umgebungs Schriftart.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f1b9b7e7f20c93cd2067d1210245da8ef6ce8813
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952030"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Schriftarten und Formatierung für Visual Studio
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a> Die Schriftart der Umgebung
 Alle Schriftarten in Visual Studio müssen dem Benutzer zur Anpassung zur Verfügung gestellt werden. Dies erfolgt hauptsächlich über die Seite **Schriftarten und Farben** im Dialogfeld Extras **> Optionen** . Die drei Hauptkategorien der Schriftart Einstellungen lauten wie folgt:

- **Umgebungs Schriftart** : die primäre Schriftart für die IDE (integrierte Entwicklungsumgebung), die für alle Schnittstellen Elemente, einschließlich Dialogfeldern, Menüs, Tool Fenstern und Dokument Fenster, verwendet wird. Standardmäßig ist die Umgebungs Schriftart an eine System Schriftart gebunden, die in den aktuellen Versionen von Windows als 9 pt Segoe UI angezeigt wird. Durch die Verwendung einer Schriftart für alle Schnittstellen Elemente wird eine konsistente Schriftart Darstellung in der gesamten IDE sichergestellt.

- **Text-Editor** -Elemente, die sich im Code und anderen textbasierten Editoren befinden, können auf der Seite Text-Editor in Extras **> Optionen** angepasst werden.

- **Bestimmte** Auflistungen: Designer Fenster, die Benutzeranpassungen ihrer Schnittstellen Elemente bieten, können Schriftarten, die für Ihre Entwurfs Oberfläche spezifisch sind, auf Ihrer eigenen Einstellungsseite unter Extras **> Optionen** verfügbar machen.

### <a name="editor-font-customization-and-resizing"></a>Schriftart Anpassung von Editoren und Ändern der Größe
 Benutzer vergrößern oder verkleinern die Größe und/oder Farbe des Texts im Editor, unabhängig von der allgemeinen Benutzeroberfläche. Da die Umgebungs Schriftart für Elemente verwendet wird, die möglicherweise innerhalb von oder als Teil eines Editors/Designers angezeigt werden, ist es wichtig, das erwartete Verhalten zu beachten, wenn eine dieser Schriftart Klassifizierungen geändert wird.

 Beim Erstellen von UI-Elementen, die im Editor angezeigt werden, aber nicht Teil des *Inhalts* sind, ist es wichtig, die Umgebungs Schriftart und nicht die Text Schriftart zu verwenden, damit die Größe der Elemente auf vorhersagbare Weise geändert wird.

1. Ändern Sie für Code Text im Editor die Größe mit der Schriftart für den Code Text, und reagieren Sie auf die Zoomstufe des Editor Texts.

2. Alle anderen Elemente der-Schnittstelle sollten an die Schriftart Einstellung der Umgebung gebunden sein und auf alle globalen Änderungen in der Umgebung reagieren. Dies umfasst u. a.:

    - Text in Kontextmenüs

    - Text in einem Editor-Zusatzelement, wie z. b. Glühbirnen-Menütext, Bereich "Schnellsuche-Editor" und navigieren zu Bereich

    - Beschriftungs Text in Dialogfeldern, z. b. **in Dateien suchen** oder **umgestalten**

### <a name="accessing-the-environment-font"></a>Zugreifen auf die Umgebungs Schriftart
 In nativem oder WinForms-Code kann auf die Umgebungs Schriftart durch Aufrufen der-Methode zugegriffen werden, nachdem die- `IUIHostLocale::GetDialogFont` Schnittstelle vom Dienst abgefragt wurde `SID_SUIHostLocale` .

 Leiten Sie für Windows Presentation Foundation (WPF) die Dialogfenster Klasse von der-Klasse der Shell `DialogWindow` anstelle von WPF- `Window` Klasse ab.

 In XAML sieht der Code wie folgt aus:

```xaml
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>
```

Code Behind:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (Ersetzen Sie dies `Microsoft.VisualStudio.Shell.11.0` durch die aktuelle Version der MPF-dll.)

 Um das Dialogfeld anzuzeigen, müssen Sie " `ShowModal()` " für die-Klasse über aufrufen `ShowDialog()` . `ShowModal()` Legt den korrekten modalen Zustand in der Shell fest, stellt sicher, dass das Dialogfeld im übergeordneten Fenster zentriert ist, usw.

 Der Code lautet wie folgt:

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal` Gibt einen booleschen Wert zurück? (boolescher Wert, der NULL-Werte zulässt) mit dem `DialogResult` , der bei Bedarf verwendet werden kann. Der Rückgabewert ist "true", wenn das Dialogfeld mit " **OK**" geschlossen wurde.

 Wenn Sie eine WPF-Benutzeroberfläche anzeigen möchten, bei der es sich nicht um ein Dialogfeld handelt und die eigenständig gehostet werden, z. b. `HwndSource` ein Popup Fenster oder ein untergeordnetes WPF-Fenster eines übergeordneten Win32/WinForms-Fensters, müssen Sie `FontFamily` und `FontSize` für das Stamm Element des WPF-Elements festlegen. (Die Shell legt die Eigenschaften im Hauptfenster fest, aber Sie werden nicht über ein geerbt `HWND` ). Die Shell stellt Ressourcen bereit, an die die Eigenschaften gebunden werden können, wie folgt:

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a> Referenz zum Formatieren (Skalieren/stärken)
 In einigen Dialogfeldern ist es erforderlich, dass ein bestimmter Text fett oder eine andere als die Umgebungs Schriftart ist. Zuvor waren Schriftarten, die größer als die Umgebungs Schriftart waren, als " `environment font +2` " oder ähnlich codiert. Mithilfe der bereitgestellten Code Ausschnitte werden High-dpi-Monitore unterstützt, und es wird sichergestellt, dass Anzeige Text immer mit der richtigen Größe und Gewichtung (z. b. Light oder semilight) angezeigt wird

> [!NOTE]
> Bevor Sie die Formatierung anwenden, stellen Sie sicher, dass Sie die Anleitungen im [Textformat](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)befolgen. * *

 Um die Schriftart der Umgebung zu skalieren, legen Sie den Stil des TextBlock oder der Bezeichnung wie angegeben fest. Jeder dieser Code Ausschnitte, ordnungsgemäß verwendet, generiert die richtige Schriftart, einschließlich der entsprechenden Größen-und Gewichtungs Variationen.

 Dabei `vsui` ist "" ein Verweis auf den-Namespace `Microsoft.VisualStudio.Shell` :

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>375% Umgebungs Schriftart + hell

**Angezeigt als:** 34 PT Segoe UI Light

::: moniker range="vs-2017"

**Verwenden Sie für:** (seltene) Benutzeroberfläche für einmalige Marken, wie auf der Start Seite.

::: moniker-end

::: moniker range=">=vs-2019"

**Verwenden für:** (seltene) Benutzeroberfläche mit einmaligem Branding

::: moniker-end

**Prozeduraler Code:** Dabei `textBlock` ist ein zuvor definiertes TextBlock, das `label` eine zuvor definierte Bezeichnung ist:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** Legen Sie den Stil des TextBlock oder der Bezeichnung wie dargestellt fest.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>310% Umgebungs Schriftart + hell
 **Angezeigt als:** 28 PT Segoe UI einfache **Verwendung für:** Dialog Titel für große Signaturen, Hauptüberschrift in Berichten

 **Prozeduraler Code:** Dabei `textBlock` ist ein zuvor definiertes TextBlock, das `label` eine zuvor definierte Bezeichnung ist:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** Legen Sie den Stil des TextBlock oder der Bezeichnung wie dargestellt fest.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>200% Umgebungs Schriftart +-Aktivität
 **Angezeigt als:** 18 PT Segoe UI die **Verwendung für:** unter Überschriften, Titel in kleinen und mittleren Dialogfeldern

 **Prozeduraler Code:** Dabei `textBlock` ist ein zuvor definiertes TextBlock, das `label` eine zuvor definierte Bezeichnung ist:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** Legen Sie den Stil des TextBlock oder der Bezeichnung wie dargestellt fest:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>155% Umgebungs Schriftart
 **Erscheint wie folgt:** 14 PT Segoe UI **Verwendung für:** Abschnittsüberschriften in Dokument-Well-UI oder-Berichten

 **Prozeduraler Code:** Dabei `textBlock` ist ein zuvor definiertes TextBlock, das `label` eine zuvor definierte Bezeichnung ist:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** Legen Sie den Stil des TextBlock oder der Bezeichnung wie dargestellt fest:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>133% Umgebungs Schriftart
 **Angezeigt als:** 12 pt Segoe UI **Verwendung für:** kleinere unter Überschriften in den Signatur Dialogfeldern und in der Dokument-Well-UI

 **Prozeduraler Code:** Dabei `textBlock` ist ein zuvor definiertes TextBlock, das `label` eine zuvor definierte Bezeichnung ist:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** Legen Sie den Stil des TextBlock oder der Bezeichnung wie dargestellt fest:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>122% Umgebungs Schriftart
 **Angezeigt als:** 11 PT Segoe UI **Verwendung für:** Abschnittsüberschriften in den Signatur Dialogfeldern, obere Knoten in der Strukturansicht, vertikale Registerkarten Navigation

 **Prozeduraler Code:** Dabei `textBlock` ist ein zuvor definiertes TextBlock, das `label` eine zuvor definierte Bezeichnung ist:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** Legen Sie den Stil des TextBlock oder der Bezeichnung wie dargestellt fest:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>Umgebungs Schriftart + fett
 **Angezeigt als:** Fett formatierte 9 pt-Segoe UI **verwenden für:** Bezeichnungen und unterköpfe in den Signatur Dialogfeldern, Berichten und der Dokument-Well-Benutzeroberfläche

 **Prozeduraler Code:** Dabei `textBlock` ist ein zuvor definiertes TextBlock, das `label` eine zuvor definierte Bezeichnung ist:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** Legen Sie den Stil des TextBlock oder der Bezeichnung wie dargestellt fest:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>Lokalisierbare Stile
 In einigen Fällen müssen lokalisierungssoren Schriftart Stile für verschiedene Gebiets Schemas ändern, z. b. das Entfernen von Fett Formatierungen aus Text für ostasiatische Sprachen. Um die Lokalisierung von Schriftarten zu ermöglichen, müssen sich diese Stile in der RESX-Datei befinden. Die beste Möglichkeit, dies zu erreichen und weiterhin Schriftart Stile im Visual Studio-Formular-Designer zu bearbeiten, besteht darin, die Schriftart Stile zur Entwurfszeit explizit festzulegen. Obwohl dadurch ein vollständiges Font-Objekt erstellt wird und die Vererbung von übergeordneten Schriftarten möglicherweise unterbrechen wird, wird nur die FontStyle-Eigenschaft verwendet, um die Schriftart festzulegen.

 Die Lösung besteht darin, das-Ereignis des Dialog Formulars zu schließen `FontChanged` . Führen `FontChanged` Sie im-Ereignis alle Steuerelemente aus, und überprüfen Sie, ob Ihre Schriftart festgelegt ist. Wenn Sie festgelegt ist, ändern Sie Sie in eine neue Schriftart, die auf der Schriftart des Formulars und dem vorherigen Schrift Schnitt des Steuer Elements basiert. Ein Beispiel hierfür ist:

```csharp
private void Form1_FontChanged(object sender, System.EventArgs e)
{
          SetFontStyles();
}

/// <summary>
/// SetFontStyles - This function will iterate all controls on a page
/// and recreate their font with the desired fontstyle.
/// It should be called in the OnFontChanged handler (and also in the constructor
/// in case the IUIService is not available so OnFontChange doesn't fire).
/// This way, when the VS shell font is given to us the controls that have
/// a different style for the font (bolded for example) will recreate their font
/// and use the VS shell font but with a style variation (bolded ...).
/// </summary>
protected void SetFontStyles()
{
     SetFontStyles(this, this, this.Font);
}

protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)
{
     foreach(Control c in parent.Controls)
     {
          if (c.Controls != null && c.Controls.Count > 0) {
               SetFontStyles(topControl, c, referenceFont);
          }
          if (c.Font != topControl.Font) {
               c.Font = new Font(referenceFont, c.Font.Style);
          }
     }
}
```

 Mit diesem Code wird sichergestellt, dass bei der Aktualisierung der Formular Schriftart die Schriftarten von Steuerelementen ebenfalls aktualisiert werden. Diese Methode sollte auch aus dem Konstruktor des Formulars aufgerufen werden, da das Dialogfeld möglicherweise keine Instanz von erhält `IUIService` und das `FontChanged` Ereignis nie ausgelöst wird. Durch das Verknüpfen `FontChanged` von Dialogfeldern kann die neue Schriftart auch dann dynamisch übernommen werden, wenn das Dialogfeld bereits geöffnet ist.

### <a name="testing-the-environment-font"></a>Testen der Umgebungs Schriftart
 Um sicherzustellen, dass die Benutzeroberfläche die Umgebungs Schriftart verwendet und die Größen Einstellungen respektiert, öffnen Sie Extras **> Optionen > Umgebung > Schriftarten und Farben** , und wählen Sie "Umgebungs Schriftart" im Dropdown Menü "Einstellungen anzeigen für:" aus.

 ![Einstellungen für Schriftarten und Farben im &gt; Dialogfeld "Optionen"](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />Einstellungen für Schriftarten und Farben im &gt; Dialogfeld "Optionen"

 Legen Sie für die Schriftart etwas anderes als die Standardeinstellung fest. Um zu verdeutlichen, welche Benutzeroberfläche nicht aktualisiert wird, wählen Sie eine Schriftart mit Serifen an (z. b. "Times New Roman") aus, und legen Sie eine sehr große Größe fest. Testen Sie dann die Benutzeroberfläche, um sicherzustellen, dass Sie die Umgebung respektiert Hier ist ein Beispiel für die Verwendung des Lizenz Dialogfelds:

 ![Beispiel für UI-Text, der die Umgebungs Schriftart nicht beachtet](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />Beispiel für UI-Text, der die Umgebungs Schriftart nicht beachtet

 In diesem Fall wird die Schriftart von "Benutzerinformationen" und "Produktinformationen" nicht beachtet. In manchen Fällen könnte dies eine explizite Entwurfs Auswahl sein, aber es kann ein Fehler sein, wenn die explizite Schriftart nicht als Teil der Redline-Spezifikationen angegeben wird.

 Klicken Sie zum Zurücksetzen der Schriftart unter Extras **> Optionen > Umgebung > Schriftarten und Farben** auf "Standardwerte verwenden".

## <a name="text-style"></a><a name="BKMK_TextStyle"></a> Textstil
 Der Textstil bezieht sich auf Schrift Grad, Gewichtung und Groß-/Kleinschreibung. Implementierungs Leit Fäden finden Sie in [der Umgebungs Schriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Text Schreibweise

#### <a name="all-caps"></a>Alle Obergrenzen
 Verwenden Sie in Visual Studio nicht alle Caps für Titel oder Bezeichnungen.

#### <a name="all-lowercase"></a>Alle Kleinbuchstaben
 Verwenden Sie in Visual Studio nicht alle Kleinbuchstaben für Titel oder Bezeichnungen.

#### <a name="sentence-and-title-case"></a>Satz und titelfall
 Der Text in Visual Studio sollte je nach Situation entweder die Groß-/Kleinschreibung oder den Satz Fall verwenden.

|Titel Fall verwenden für:|Satz Buchstaben verwenden für:|
|-------------------------|----------------------------|
|Dialog Titel|Bezeichnungen|
|Gruppen Felder|Kontrollkästchen|
|Menüelemente|Optionsfelder|
|Kontextmenüelemente|Listenfeld Elemente|
|Schaltflächen|Statusleisten|
|Tabellen Bezeichnungen||
|Spaltenüberschriften||
|QuickInfos||

##### <a name="title-case"></a>Großschreibung
 Der titelfall ist ein Stil, bei dem die ersten Buchstaben der meisten oder aller Wörter innerhalb eines Ausdrucks groß geschrieben werden. In Visual Studio wird die Groß-/Kleinschreibung für viele Elemente verwendet, einschließlich:

- **Quick Infos.** Beispiel: "Vorschau ausgewählter Elemente"

- **Spaltenüberschriften.** Beispiel: "System Antwort"

- **Menü Elemente.** Beispiel: "Alle speichern"

  Bei der Verwendung von Title Case sind dies die Richtlinien für die Groß-/Kleinschreibung von Wörtern und die Verwendung von Kleinbuchstaben:

|Großbuchstaben|Kommentare und Beispiele|
|---------------|---------------------------|
|Alle Nomen||
|Alle Verben|Einschließen von "is" und anderen Formen von "to be"|
|Alle adversb|Einschließen von "than" und "When"|
|Alle Adjektiven|Einschließlich "This" und "This"|
|Alle Pronomen|Einschließlich der besitzenden "its" und "IT es", eine Kontraktion der Pronomen "IT" und des Verbs "is"|
|Das erste und letzte Wort, unabhängig von den Teilen der Sprache||
|Präpositionen, die Teil eines Verb Ausdrucks sind|"Schließen aller Fenster" oder "Herunterfahren des Systems"|
|Alle Buchstaben eines Akronyms|HTML, XML, URL, IDE, RGB|
|Das zweite Wort in einem zusammengesetzten Wort, wenn es ein Substantiv oder ein richtiges Adjektiv ist, oder, wenn die Wörter die gleiche Gewichtung aufweisen|Querverweise, Software vor Microsoft, Lese-/Schreibzugriff, Run-Time|

|Kleinbuchstaben|Beispiele|
|---------------|--------------|
|Das zweite Wort in einem zusammengesetzten Wort, wenn es ein anderer Teil der Sprache ist, oder ein Teilnehmer, das das erste Wort ändert.|Vorgehensweise, Take-Off|
|Artikel, es sei denn, es handelt sich um das erste Wort im Titel|a, an, the|
|Koordinaten Koordinaten|und, aber, für, und oder|
|Präpositionen mit Wörtern von vier oder weniger Buchstaben außerhalb eines Verb Ausdrucks|in, auf, wie für, von, oben auf|
|"To" bei Verwendung in einem unendliche Ausdruck|"Vorgehensweise beim Formatieren der Festplatte"|

##### <a name="sentence-case"></a>Satz Fall
 Die Groß-/kleinschreibungsmethode ist die standardmäßige groß-/kleinschreibungsmethode zum Schreiben, bei der nur das erste Wort des Satzes mit allen richtigen Nomen und dem Wort "I" groß geschrieben wird. Im Allgemeinen ist der Satz Fall für ein weltweites Publikum einfacher zu lesen, insbesondere dann, wenn der Inhalt von einem Computer übersetzt wird. Satz Buchstaben verwenden für:

1. **Status leisten Meldungen.** Dabei handelt es sich um einfache, kurze und nur Statusinformationen. Beispiel: "Laden der Projektdatei"

2. **Alle anderen Benutzeroberflächen Elemente**, einschließlich Bezeichnungen, Kontrollkästchen, Options Felder und Listenfeld Elemente. Beispiel: "alle Elemente in der Liste auswählen"

### <a name="text-formatting"></a>Textformatierung
 Die Standardtext Formatierung in Visual Studio 2013 wird von [der Umgebungs Schriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)gesteuert. Mit diesem Dienst wird eine konsistente Schriftart Darstellung in der gesamten IDE (integrierte Entwicklungsumgebung) sichergestellt, und Sie müssen Sie verwenden, um eine konsistente Benutzerumgebung zu gewährleisten.

 Die vom Visual Studio-Schriftart Dienst verwendete Standardgröße stammt aus Windows und wird als 9 pt angezeigt.

 Sie können die Formatierung auf die Umgebungs Schriftart anwenden. In diesem Thema wird erläutert, wie und wo Stile verwendet werden. Informationen zur Implementierung finden Sie in [der Umgebungs Schriftart](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

#### <a name="bold-text"></a>Fett formatierter Text
 Fett formatierter Text wird in Visual Studio sparsam verwendet und sollte für Folgendes reserviert werden:

- Frage Bezeichnungen in Assistenten

- Festlegen des aktiven Projekts in Projektmappen-Explorer

- überschriebene Werte im Tool Fenster "Eigenschaften"

- bestimmte Ereignisse in den Visual Basic-Editor-Dropdown Listen

- vom Server generierter Inhalt in der Dokument Gliederung für Webseiten

- Abschnitts Header im komplexen Dialogfeld oder in der Designer Benutzeroberfläche

#### <a name="italics"></a>Kursiv
 Visual Studio verwendet weder kursiv noch kursiv formatierten Text.

#### <a name="color"></a>Color

- Blue ist für Hyperlinks (Navigation und Befehls Richtung) reserviert und sollte nie für die Ausrichtung verwendet werden.

- Größere Überschriften (Umgebungs Schriftart x 155% oder größer) können für folgende Zwecke gefärbt werden:

  - So sorgen Sie für eine visuelle Benutzeroberfläche für die Signatur von Visual Studio

  - So greifen Sie auf einen bestimmten Bereich zu

  - So bieten Sie die Textfarbe der standardmäßigen dunkelgrauen/schwarzen Umgebung an

- Farben in Überschriften sollten vorhandene Visual Studio-Markenfarben, primär die Haupt-lila #FF68217A, nutzen.

- Wenn Sie Farbe in Überschriften verwenden, müssen Sie die [Windows-Farb Richtlinien](/windows/desktop/uxguide/vis-color)einhalten, einschließlich des Kontrastverhältnisses und anderer Überlegungen zur Barrierefreiheit.

### <a name="font-size"></a>Schriftgrad
 Der Visual Studio-Benutzeroberflächen Entwurf bietet eine hellere Darstellung mit mehr Leerraum. Nach Möglichkeit wurden Chrome-und Titelleisten reduziert oder entfernt. Obwohl die Informationsdichte in Visual Studio eine Voraussetzung ist, ist die Typografie weiterhin wichtig, wobei der Fokus auf mehr öffnenden Zeilen Abstände und auf eine Variation von Schriftgrößen und Gewichtungen liegt.

 Die folgenden Tabellen enthalten Entwurfs Details und visuelle Beispiele für die in Visual Studio verwendeten Anzeige Schriftarten. Einige Anzeige Schriftart Variationen verfügen sowohl über die Größe als auch über die Gewichtung (z. b. "an", "an" oder "Light").

 Implementierungs Code Ausschnitte für alle Anzeige Schriftarten finden Sie unter [formatieren (Skalieren/stärken)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).

#### <a name="375-environment-font--light"></a>375% Umgebungs Schriftart + hell

|Verbrauch|Darstellung|
|-|-|
|**Verwendung:** Ere. Nur eindeutige Marken-Benutzeroberfläche.<br /><br /> **Können**<br /><br /> -Use Satz Case<br />-Immer leichte Gewichtung verwenden<br /><br /> **Tue nicht:**<br /><br /> -Verwendung für die Benutzeroberfläche außer der Signatur Benutzeroberfläche, z. b. Start Seite<br />-Fett, kursiv oder Fett kursiv<br />-Für Textkörper Text verwenden<br />-Verwendung in Tool Fenstern|**Angezeigt als:** 34 PT Segoe UI Light<br /><br /> **Visuelles Beispiel:**<br /><br /> *Wird derzeit nicht verwendet. Kann auf der Start Seite von Visual Studio 2017 verwendet werden.*|

#### <a name="310-environment-font--light"></a>310% Umgebungs Schriftart + hell

::: moniker range="vs-2017"

|Verbrauch|Darstellung|
|-|-|
|**Syntax:**<br /><br /> -Größere Überschrift in den Signatur Dialogfeldern<br />-Hauptberichts Überschrift<br /><br /> **Können**<br /><br /> -Use Satz Case<br />-Immer leichte Gewichtung verwenden<br /><br /> **Tue nicht:**<br /><br /> -Verwendung für die Benutzeroberfläche außer der Signatur Benutzeroberfläche, z. b. Start Seite<br />-Fett, kursiv oder Fett kursiv<br />-Für Textkörper Text verwenden<br />-Verwendung in Tool Fenstern|**Angezeigt als:** 28 PT Segoe UI hell<br /><br /> **Visuelles Beispiel:**<br /><br /> ![Beispiel für Umgebungs Schriftart mit 310% &#43; helle Überschrift](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|Verbrauch|Darstellung|
|-|-|
|**Syntax:**<br /><br /> -Größere Überschrift in den Signatur Dialogfeldern<br />-Hauptberichts Überschrift<br /><br /> **Können**<br /><br /> -Use Satz Case<br />-Immer leichte Gewichtung verwenden<br /><br /> **Tue nicht:**<br /><br /> -Verwendung für die Benutzeroberfläche außer der Signatur Benutzeroberfläche<br />-Fett, kursiv oder Fett kursiv<br />-Für Textkörper Text verwenden<br />-Verwendung in Tool Fenstern|**Angezeigt als:** 28 PT Segoe UI hell<br /><br /> **Visuelles Beispiel:**<br /><br /> ![Beispiel für Umgebungs Schriftart mit 310% &#43; helle Überschrift](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>200% Umgebungs Schriftart +-Aktivität

|Verbrauch|Darstellung|
|-|-|
|**Syntax:**<br /><br /> -Unter Überschriften<br />-Titel in kleinen und mittleren Dialogfeldern<br /><br /> **Können**<br /><br /> -Use Satz Case<br />-Immer "nur ein"-Gewicht verwenden<br /><br /> **Tue nicht:**<br /><br /> -Fett, kursiv oder Fett kursiv<br />-Für Textkörper Text verwenden<br />-Verwendung in Tool Fenstern|**Angezeigt als:** 18 PT Segoe UI-millight<br /><br /> **Visuelles Beispiel:**<br /><br /> ![Beispiel für Umgebungs Schriftart &#43; von 200%](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>155% Umgebungs Schriftart

|Verbrauch|Darstellung|
|-|-|
|**Syntax:**<br /><br /> -Abschnittsüberschriften in Dokument-Well-UI<br />-Berichte<br /><br /> Ausführen **:** Verwenden Sie Satz Buchstaben.<br /><br /> **Tue nicht:**<br /><br /> -Fett, kursiv oder Fett kursiv<br />-Für Textkörper Text verwenden<br />-Verwendung in standardmäßigen Visual Studio-Steuerelementen<br />-Verwendung in Tool Fenstern|**Angezeigt als:** 14 PT Segoe UI<br /><br /> **Visuelles Beispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart mit 155 %, Überschrift](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>133% Umgebungs Schriftart

|Verbrauch|Darstellung|
|-|-|
|**Syntax:**<br /><br /> -Kleinere unter Überschriften in den Signatur Dialogfeldern<br />-Kleinere unter Überschriften in Dokument-Well-UI<br /><br /> Ausführen **:** Verwenden Sie Satz Buchstaben.<br /><br /> **Tue nicht:**<br /><br /> -Fett, kursiv oder Fett kursiv<br />-Für Textkörper Text verwenden<br />-Verwendung in standardmäßigen Visual Studio-Steuerelementen<br />-Verwendung in Tool Fenstern|**Angezeigt als:** 12 pt Segoe UI<br /><br /> **Visuelles Beispiel:**<br /><br /> ![Beispiel für Beispiel für Umgebungsschriftart mit 133 %, Überschrift](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>122% Umgebungs Schriftart

|Verbrauch|Darstellung|
|-|-|
|**Syntax:**<br /><br /> -Abschnittsüberschriften in den Signatur Dialogfeldern<br />-Obere Knoten in der Strukturansicht<br />-Vertikale Registerkarten Navigation<br /><br /> Ausführen **:** Verwenden Sie Satz Buchstaben.<br /><br /> **Tue nicht:**<br /><br /> -Fett, kursiv oder Fett kursiv<br />-Für Textkörper Text verwenden<br />-Verwendung in standardmäßigen Visual Studio-Steuerelementen<br />-Verwendung in Tool Fenstern|**Angezeigt als:** 11 PT Segoe UI<br /><br /> **Visuelles Beispiel:**<br /><br /> ![Beispiel für Beispiel für Umgebungsschriftart mit 122 %, Überschrift](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Umgebungs Schriftart + fett

|Verbrauch|Darstellung|
|-|-|
|**Syntax:**<br /><br /> -Bezeichnungen und unterköpfe in den Signatur Dialogfeldern<br />-Bezeichnungen und Teil Köpfe in Berichten<br />-Bezeichnungen und unterköpfe in Dokument-Well-UI<br /><br /> **Können**<br /><br /> -Use Satz Case<br />-Fett Gewichtung verwenden<br /><br /> **Tue nicht:**<br /><br /> Kursiv formatiert oder fett formatiert<br />-Für Textkörper Text verwenden<br />-Verwendung in standardmäßigen Visual Studio-Steuerelementen<br />-Verwendung in Tool Fenstern|**Angezeigt als:** 9 pt Segoe UI<br /><br /> **Visuelles Beispiel:**<br /><br /> ![Beispiel für Umgebungs Schriftart &#43; Fett formatierte Überschrift](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Umgebungs Schriftart

|Verbrauch|Darstellung|
|-|-|
|**Verwendung:** Sämtlicher anderer Text<br /><br /> Ausführen **:** Verwenden Sie Satz Buchstaben.<br /><br /> **Nicht:** Kursiv oder fett formatiert|**Angezeigt als:** 9 pt Segoe UI<br /><br /> **Visuelles Beispiel:**<br /><br /> ![Beispiel für Umgebungsschriftart](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Abstand und Abstände
 Überschriften benötigen Platz, um Ihnen den passenden Fokus zu verschaffen. Dieser Speicherplatz variiert abhängig von der Punktgröße und der Nähe der Überschrift, z. b. eine horizontale Regel oder eine Textzeile in der Umgebungs Schriftart.

- Die ideale Auffüll Fläche für eine Überschrift muss 90% des Großbuchstaben der Großbuchstaben sein. Beispielsweise hat die Überschrift 28 PT Segoe UI Light eine Obergrenze von 26 PT, und der Abstand sollte ungefähr 23 PT oder ungefähr 31 Pixel betragen.

- Der minimale Speicherplatz um eine Überschrift sollte 50% der Höhe des Haupt Zeichens betragen. Weniger Speicherplatz kann verwendet werden, wenn eine Überschrift von einer Regel oder einem anderen Element mit passender Anpassung begleitet wird.

- Der Schriftart Text der fett formatierten Umgebung sollte dem Standardabstand der Zeilenhöhe und der Auffüll Schlange folgen.

## <a name="see-also"></a>Weitere Informationen

- [Schriftarten (Windows)](/windows/desktop/uxguide/vis-fonts)
- [Text der Benutzeroberfläche (Windows)](/windows/desktop/uxguide/text-ui)
