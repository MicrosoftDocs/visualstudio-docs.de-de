---
title: Farben und Stile für Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie, wie die Visual Studio-Benutzer Darstellung Farben als Kommunikations Tool verwendet, anstatt aus rein ästhetischen Gründen.
ms.custom: SEO-VS-2020
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99e33ae67e0fd18ecd9a1a40a8b8075cd22d4bf7
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715664"
---
# <a name="colors-and-styling-for-visual-studio"></a>Farben und Stile für Visual Studio

## <a name="use-color-in-visual-studio"></a>Verwenden von Farben in Visual Studio

In Visual Studio wird die Farbe hauptsächlich als Kommunikations Tool verwendet, nicht nur als Ergänzung. Verwenden Sie die Farbe minimal, und reservieren Sie Sie für Situationen, in denen Sie Folgendes wünschen:

- Bedeutung oder Zugehörigkeit (z. b. Plattform-oder sprachenmodifiziererer)

- Aufmerksamkeit berücksichtigen (z. b. eine Statusänderung)

- Verbesserung der Lesbarkeit und Bereitstellen von Funktionen für die Navigation in der Benutzeroberfläche

- Steigerung der begehrbarkeit

Zum Zuweisen von Farben zu Benutzeroberflächen Elementen in Visual Studio gibt es mehrere Optionen. Manchmal kann es schwierig sein, herauszufinden, welche Option Sie verwenden möchten, oder wie Sie diese ordnungsgemäß verwenden. In diesem Thema erhalten Sie folgende Hilfe:

- Verstehen Sie die verschiedenen Dienste und Systeme, die zum Definieren von Farben in Visual Studio verwendet werden.

- Wählen Sie die richtige Option für ein bestimmtes Element aus.

- Verwenden Sie die von Ihnen gewählte Option ordnungsgemäß.

> [!NOTE]
> Niemals hart codieren Sie die Farben Hex, RGB oder System für Ihre Benutzeroberflächen Elemente. Die Verwendung der Dienste ermöglicht Flexibilität beim Optimieren von Hue. Außerdem können Sie ohne den Dienst nicht die Funktionen zum Wechseln von Funktionen des [vscolor-Dienstanbieter](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)nutzen.

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Methoden zum Zuweisen von Farben zu Visual Studio-Schnittstellen Elementen

Wählen Sie die Methode aus, die für Ihre Benutzeroberflächen Elemente am besten geeignet

| Ihre Benutzeroberfläche | Methode | Welche sind dies? |
| --- | --- | --- |
| Sie verfügen über eingebettete oder eigenständige Dialogfelder. | **System Farben** | System Namen, mit denen das Betriebssystem die Farbe und Darstellung der Benutzeroberflächen Elemente, wie z. b. allgemeine Dialogfeld Steuerelemente, definieren kann. |
| Sie haben benutzerdefinierte Benutzeroberfläche, die mit der gesamten vs-Umgebung konsistent sein soll, und Sie verfügen über Benutzeroberflächen Elemente, die mit der Kategorie und der semantischen Bedeutung der freigegebenen Token übereinstimmen. | **Gemeinsame gemeinsame Farben** | Vorhandene vordefinierte farbtokennamen für bestimmte Elemente der Benutzeroberfläche |
| Sie verfügen über ein einzelnes Feature oder eine Gruppe von Features, und für ähnliche Elemente gibt es keine gemeinsame Farbe. | **Benutzerdefinierte Farben** | Farbtokennamen, die spezifisch für einen Bereich sind und nicht für die gemeinsame Verwendung mit anderen Benutzeroberflächen vorgesehen sind |
| Sie möchten, dass der Endbenutzer die Benutzeroberfläche oder den Inhalt anpassen kann (z. b. für Text-Editoren oder spezielle Designer Fenster). | **Anpassung des Endbenutzers**<br /><br />**(Tools &gt; Dialogfeld "Optionen"** | Einstellungen, die auf der Seite "Schriftarten und Farben" des Dialog Felds "Extras **&gt; Optionen** " oder einer speziellen, speziell für ein UI-Feature spezifischen Seite definiert sind. |

### <a name="visual-studio-themes"></a>Visual Studio-Designs

Visual Studio bietet drei verschiedene Farbschemas: hell, dunkel und blau. Außerdem wird hoher Kontrast Modus erkannt, bei dem es sich um ein systemweites Farbschema handelt, das für die Barrierefreiheit konzipiert ist.

Benutzer werden bei der ersten Verwendung von Visual Studio aufgefordert, ein Design auszuwählen. Sie können die Designs später ändern, indem Sie zu Extras **&gt; Optionen &gt; Umgebung &gt; Allgemein** wechseln und ein neues Design aus dem Dropdown Menü "Farbschema" auswählen.

Benutzer können auch die Systemsteuerung verwenden, um Ihre gesamten Systeme in eines von mehreren hoher Kontrast Designs zu wechseln. Wenn ein Benutzer ein hoher Kontrast Design auswählt, wirkt sich das Visual Studio Color Design Selector nicht mehr auf die Farben in Visual Studio aus. es werden jedoch alle Designänderungen gespeichert, wenn der Benutzer hoher Kontrast Modus verlässt. Weitere Informationen zum hoher Kontrast Modus finden Sie unter [auswählen hoher Kontrast Farben](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Der vscolor-Dienst

Visual Studio stellt einen Umgebungs Farb Dienst bereit, der als vscolor-Dienst bezeichnet wird, mit dem Sie die Farbwerte der Benutzeroberflächen Elemente an einen benannten Eintrag binden können, der Farbwerte für jedes Visual Studio-Design enthält. Dadurch wird sichergestellt, dass Ihre Farben automatisch geändert werden, um das aktuelle vom Benutzer ausgewählte Design oder den System hoher Kontrast Modus widerzuspiegeln. Die Verwendung des-dienstanseins bedeutet, dass die Implementierung aller designbezogenen Farbänderungen an einem Ort behandelt wird, und wenn Sie gemeinsame freigegebene Farben aus dem Dienst verwenden, spiegelt die Benutzeroberfläche automatisch neue Designs in zukünftigen Versionen von Visual Studio wider.

### <a name="implementation"></a>Implementierung

Der Quellcode von Visual Studio enthält mehrere Paket Definitions Dateien, die Listen von Tokennamen und die entsprechenden Farbwerte für jedes Design enthalten. Der Color-Dienst liest die in diesen Paket Definitions Dateien definierten vscolors. Auf diese Farben wird in XAML-Markup oder Code verwiesen und anschließend entweder über die- `IVsUIShell5.GetThemedColor` Methode oder eine dynamikresource-Zuordnung geladen.

### <a name="system-colors"></a>System Farben

Allgemeine Steuerelemente verweisen standardmäßig auf die Systemfarben. Wenn Sie möchten, dass die Benutzeroberfläche Systemfarben verwendet, z. b. Wenn Sie ein eingebettetes oder eigenständiges Dialogfeld erstellen, müssen Sie nichts tun.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Gemeinsame gemeinsame Farben im vscolor-Dienst

Ihre Schnittstellen Elemente sollten die gesamte Visual Studio-Umgebung widerspiegeln. Indem Sie die gemeinsamen gemeinsam genutzten Farben wieder verwenden, die für die Benutzeroberflächen Komponente geeignet sind, die Sie entwerfen, stellen Sie sicher, dass Ihre Schnittstelle mit anderen Visual Studio-Schnittstellen konsistent ist und dass Ihre Farben automatisch aktualisiert werden, wenn Designs hinzugefügt oder aktualisiert werden.

Vergewissern Sie sich vor der Verwendung gemeinsamer gemeinsamer Farben, dass Sie wissen, wie Sie richtig verwendet werden. Eine falsche Verwendung von gemeinsamen gemeinsam genutzten Farben führt möglicherweise zu einer inkonsistenten, frustrierend oder unübersichtlichen Benutzer Leistung.

### <a name="user-customizable-colors"></a>Benutzer anpassbare Farben

Siehe: verfügbar machen [von Farben für Endbenutzer](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Manchmal empfiehlt es sich, den Endbenutzern das Anpassen Ihrer Benutzeroberfläche zu ermöglichen, z. b. Wenn Sie einen Code-Editor oder eine Entwurfs Oberfläche erstellen. Anpassbare UI-Komponenten finden Sie im Abschnitt **Schriftarten und Farben** des Dialog Felds Extras **&gt; Optionen** , in dem Benutzer die Vordergrundfarbe, die Hintergrundfarbe oder beides ändern können.

![Dialogfeld " &gt; Optionen"](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Dialogfeld " &gt; Optionen"

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a> Der vscolor-Dienst

Visual Studio stellt einen Umgebungs Farb Dienst bereit, der auch als vscolor-Dienst oder shellfarbdienst bezeichnet wird. Dieser Dienst ermöglicht es Ihnen, die Farbwerte der Benutzeroberflächen Elemente an einen Name-Wert-Farbsatz zu binden, der Farben für jedes Design enthält. Der vscolor-Dienst muss für alle Elemente der Benutzeroberfläche verwendet werden, sodass Farben automatisch geändert werden, um das aktuelle vom Benutzer ausgewählte Design widerzuspiegeln, und damit die Benutzeroberfläche, die an den Umgebungs Farb Dienst gebunden ist, in zukünftigen Versionen von Visual Studio in neue Designs integriert werden kann.

### <a name="how-the-service-works"></a>Funktionsweise des Diensts

Der Umgebungs Farb Dienst liest vscolors, die in der pkgdef-Datei für die Benutzeroberflächen Komponente definiert sind. Auf diese vscolors wird dann in XAML-Markup oder-Code verwiesen, und Sie werden entweder über die- `IVsUIShell5.GetThemedColor` oder eine- `DynamicResource` Zuordnung geladen.

![Umgebungsfarbe – Dienstarchitektur](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Umgebungsfarbe – Dienstarchitektur

### <a name="accessing-the-service"></a>Zugreifen auf den Dienst

Es gibt verschiedene Möglichkeiten, auf den vscolor-Dienst zuzugreifen, je nachdem, welche Art von farbtoken Sie verwenden und welche Art von Code Sie haben.

#### <a name="predefined-environment-colors"></a>Vordefinierte Umgebungs Farben

##### <a name="from-native-code"></a>Aus nativem Code

Die Shell stellt einen Dienst bereit, der den Zugriff auf die `COLORREF` der Farben ermöglicht. Der Dienst bzw. die Schnittstelle ist:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

In der Datei VSShell80. idl hat die-Enumeration `__VSSYSCOLOREX` shellfarbkonstanten. Um es zu verwenden, übergeben Sie als Indexwert entweder einen der Werte aus der `enum __VSSYSCOLOREX` in MSDN dokumentierten oder eine reguläre Indexnummer, die von der Windows-System-API `GetSysColor` akzeptiert wird. Dadurch wird der RGB-Wert der Farbe zurückgenommen, die im zweiten Parameter verwendet werden soll.

Wenn Sie einen Stift oder Pinsel mit einer neuen Farbe speichern, müssen Sie `AdviseBroadcastMessages` (aus der Visual Studio-Shell) und nach `WM_SYSCOLORCHANGE` `WM_THEMECHANGED` richten lauschen.

Um auf den Color-Dienst in nativem Code zuzugreifen, führen Sie einen-Befehl aus, der dem folgenden ähnelt:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> Die `COLORREF` von zurückgegebenen Werte `GetVSSysColorEx()` enthalten nur R-, G-, B-Komponenten einer Design Farbe. Wenn ein Design Eintrag Transparenz verwendet, wird der Alphakanal Wert vor der Rückgabe verworfen. Daher sollten Sie `IVsUIShell5.GetThemedColor` anstelle von verwenden `IVsUIShell2::GetVSSysColorEx` , wie weiter unten in diesem Thema beschrieben, wenn die gewünschte Umgebungs Farbe an einem Ort verwendet werden muss, an dem der Transparenz Kanal wichtig ist.

##### <a name="from-managed-code"></a>Aus verwaltetem Code

Der Zugriff auf den vscolor-Dienst über nativen Code ist recht unkompliziert. Wenn Sie verwalteten Code verwenden, kann es jedoch schwierig sein, den Dienst zu verwenden. Der folgende Code zeigt einen c#-Code Ausschnitt, der diesen Prozess veranschaulicht:

```csharp
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell2.GetVSSysColorEx((int)__VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

Wenn Sie in Visual Basic arbeiten, verwenden Sie Folgendes:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Von WPF-Benutzeroberfläche

Sie können über Werte, die in die der Anwendung exportiert werden, an Visual Studio-Farben binden `ResourceDictionary` . Im folgenden finden Sie ein Beispiel für die Verwendung von Ressourcen aus der Farbtabelle und die Bindung an die Umgebungs Schriftart Daten in XAML.

```xml
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>Hilfsklassen und Methoden für verwalteten Code

Bei verwaltetem Code enthält die verwaltete Paket Framework-Bibliothek ( `Microsoft.VisualStudio.Shell.12.0.dll` ) der Shell einige Hilfsklassen, die die Verwendung von Design Farben vereinfachen.

Zu den Hilfsmethoden in der `Microsoft.VisualStudio.Shell.VsColors` -Klasse in MPF zählen `GetThemedGDIColor()` und `GetThemedWPFColor()` . Diese Hilfsmethoden geben den Farbwert eines Design Eintrags als `System.Drawing.Color` oder zurück `System.Windows.Media.Color` , der in der WinForms-oder WPF-Benutzeroberfläche verwendet werden soll.

```csharp
IVsUIShell5 shell5;
Button button = new Button();
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);

/// <summary>
/// Gets a System.Drawing.Color value from the current theme for the given color key.
/// </summary>
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>
/// <param name="themeResourceKey">The key to find the color for.</param>
/// <returns>The current theme's value of the named color.</returns>
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);

   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Guid category = themeResourceKey.Category;
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)
   {
      colorType = __THEMEDCOLORTYPE.TCT_Background;
   }

   // This call will throw an exception if the color is not found
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);
   return BitConverter.GetBytes(rgbaColor);
}
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);

    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}
```

Die-Klasse kann auch verwendet werden, um vscolor-Bezeichner für einen bestimmten WPF-Farb Ressourcen Schlüssel oder umgekehrt zu erhalten.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Die Methoden der- `VsColors` Klasse Fragen den vscolor-Dienst ab, um den Farbwert jedes Mal zurückzugeben, wenn Sie aufgerufen werden. Um einen Farbwert als zu erhalten `System.Drawing.Color` , besteht eine Alternative mit besserer Leistung darin, stattdessen die Methoden der-Klasse zu verwenden `Microsoft.VisualStudio.PlatformUI.VSThemeColor` , die die vom vscolor-Dienst abzurufenden Farbwerte zwischenspeichert. Die-Klasse abonniert in der Shell Broadcast-Nachrichten Ereignisse intern und verwirft den zwischengespeicherten Wert, wenn ein Design veränderliches Ereignis auftritt. Außerdem stellt die-Klasse eine bereit. Netzwerk freundliches Ereignis zum Abonnieren von Designänderungen. Verwenden `ThemeChanged` Sie das-Ereignis, um einen neuen Handler hinzuzufügen, und verwenden Sie die- `GetThemedColor()` Methode zum Abrufen von Farbwerten für die `ThemeResourceKeys` von Interesse. Ein Beispielcode könnte wie folgt aussehen:

```csharp
public MyWindowPanel()
{
    InitializeComponent();

    // Subscribe to theme changes events so we can refresh the colors
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;

    RefreshColors();
}

private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)
{
    RefreshColors();

    // Also post a message to all the children so they can apply the current theme appropriately
    foreach (System.Windows.Forms.Control child in this.Controls)
    {
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);
    }
}

private void RefreshColors()
{
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);
}

protected override void Dispose(bool disposing)
{
    if (disposing)
    {
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;
        base.Dispose(disposing);}
}
```

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a> Auswählen hoher Kontrast Farben

### <a name="overview"></a>Übersicht

Windows verwendet mehrere kontrastreiche Systemdesigns, die den Farbkontrast von Text, Hintergründen und Bildern vergrößern, sodass die Elemente auf dem Bildschirm genauer angezeigt werden. Aus Gründen der Barrierefreiheit ist es wichtig, dass Visual Studio-Schnittstellen Elemente ordnungsgemäß reagieren, wenn Benutzer zu einem hoher Kontrast Design wechseln.

Nur eine Handvoll Systemfarben können für hoher Kontrast Designs verwendet werden. Beachten Sie beim Auswählen der System Farbnamen die folgenden Tipps:

- **Wählen Sie Systemfarben aus, die dieselbe semantische Bedeutung haben** wie das Element, das Sie färben. Wenn Sie beispielsweise eine Kontrastfarbe für Text in einem Fenster auswählen, verwenden Sie WindowText und nicht ControlText.

- **Wählen Sie die Vordergrund-/hintergrundpaare** aus, oder Sie werden nicht sicher sein, dass Ihre Farbe in allen hoher Kontrast Designs funktioniert.

- **Legen Sie fest, welche Teile der Benutzeroberfläche am wichtigsten sind, und stellen Sie sicher, dass Inhaltsbereiche auftreten.** Sie verlieren eine Menge Detailinformationen, die in der Regel durch feine Unterschiede in farbfarbton unterschieden werden. Daher wird die Verwendung von starken Rahmenfarben häufig zum Definieren von Inhalts Bereichen verwendet, da keine Farbvarianten für verschiedene Inhaltsbereiche vorhanden sind.

### <a name="system-color-set"></a>System Farbsatz

Die Tabelle im [WPF-Teamblog: SystemColors Reference](/archive/blogs/wpf/systemcolors-reference) gibt den kompletten Satz von System Farbnamen und die entsprechenden Schattierungen an, die in jedem Design angezeigt werden.

Wenn Sie diese begrenzte Anzahl von Farben auf die Benutzeroberfläche anwenden, wird *davon ausgegangen, dass Sie die in den "normalen" Designs enthaltenen*, geringfügigen Details verlieren. Im folgenden finden Sie ein Beispiel für eine Benutzeroberfläche mit subtilen grauen Farben, die zur Unterscheidung von Bereichen in einem Tool Fenster verwendet werden. Wenn Sie mit dem gleichen Fenster gekoppelt sind, das im hoher Kontrast Modus angezeigt wird, können Sie sehen, dass alle Hintergründe denselben Farbton haben und die Rahmen dieser Bereiche allein durch Border angegeben werden:

![Beispiel für den Verlust von geringfügigen Details in hoher Kontrast](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Beispiel für den Verlust von geringfügigen Details in hoher Kontrast

#### <a name="choosing-text-colors-in-an-editor"></a>Auswählen von Textfarben in einem Editor

Der farbige Text wird in einem Editor oder auf einer Entwurfs Oberfläche verwendet, um Bedeutungen anzugeben, wie z. b. die einfache Identifizierung von Gruppen ähnlicher Elemente. In einem hoher Kontrast Design haben Sie jedoch nicht die Möglichkeit, zwischen mehr als drei Textfarben zu unterscheiden. WindowText, GrayText und hottracktext sind die einzigen Farben, die auf windowbackground-Oberflächen verfügbar sind. Da Sie nicht mehr als drei Farben verwenden können, sollten Sie die wichtigsten Unterschiede, die Sie im hoher Kontrast Modus anzeigen möchten, sorgfältig auswählen.

Farben für die einzelnen Tokennamen, die auf einer Editor-Oberfläche zulässig sind, wie Sie in jedem hoher Kontrast Design angezeigt werden:

![Editor im Design "Hoher Kontrast", Vergleich](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Editor im Design "Hoher Kontrast", Vergleich

Beispiele für die Editor-Oberfläche im Design "Blue":

![Editor im Design "Blau"](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Editor im Design "Blau"

![Editor in hoher Kontrast #1 Design](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Editor in hoher Kontrast #1 Design

### <a name="usage-patterns"></a>Verwendungsmuster

Viele allgemeine Benutzeroberflächen Elemente haben bereits hoher Kontrast Farben definiert. Sie können auf diese Verwendungs Muster verweisen, wenn Sie Ihre eigenen System Farbnamen auswählen, damit die Elemente der Benutzeroberfläche mit ähnlichen Komponenten konsistent sind.

| System Farbe | Verbrauch |
| --- | --- |
| ActiveCaption | -Aktive IDE und Fenster Schaltflächen Symbole auf dem Mauszeiger und drücken<br />-Titelleisten Hintergrund für IDE und unregelmäßige Fenster<br />-Standardstatus leisten-Hintergrund |
| ActiveCaptionText | -Aktive IDE und gezogene Fenster für den Vordergrund der Titelleiste (Text und Symbole)<br />-Hintergrund und Rahmen der aktiven Fenster Schaltflächen bei Hover und drücken |
| Control | -Kombinations Feld, Dropdown Liste und Such Steuerelement Standard und deaktivierter Hintergrund, einschließlich der Dropdown Schaltfläche<br />-Schaltflächen Hintergrund des Andock Ziels<br />-Befehls leisten Hintergrund<br />-Tool Fenster Hintergrund |
| ControlDark | -IDE-Hintergrund<br />-Menü-und Befehls leisten Trennzeichen<br />-Befehls leisten Rahmen<br />-Menü Schatten<br />-Tool Fenster Registerkarte Standard und Hover-Rahmen und Trennzeichen<br />-Der Hintergrund für den Hintergrund der Dokument Überläufe<br />-Ziel Symbol Rahmen Andocken |
| ControlDarkDark |-Ohne Fokus, ausgewähltes Dokument Registerkarten Fenster |
| ControlLight |-Registerkarten Rahmen automatisch ausblenden<br />-Kombinations Feld und Dropdown-Listen Rahmen<br />-Ziel Hintergrund und-Rahmen Andocken |
| ControlLightLight | -Ausgewählt, zentrierter provisorischer Rahmen |
| ControlText | -Kombinations Feld und Dropdown-Listen Symbol<br />-Tool Fenster: nicht ausgewählter Registerkarten Text |
| GrayText |-Kombinations Feld und Dropdown Liste deaktivierter Rahmen, Dropdown Symbol, Text und Menü Element Text<br />-Deaktivierter Menütext<br />-Such Steuerelement-Header Text ' Suchoptionen '<br />-Such Steuerelement Abschnitts Trennzeichen |
| Markierung | -Alle Hover und gedrückten Hintergründe und Rahmen, außer Kombinations Feld-Dropdown-Schaltflächen Hintergrund und Dokument-Well-Überlauf-Schaltflächen Rahmen<br />-Ausgewählte Element Hintergründe |
| HighlightText | -Alle auf Vordergrund-und gedrückten Vordergrund (Text und Symbole)<br />-Fokus Tool Fenster und Dokument Register Steuerelement-Vordergrund<br />-Der Titelleisten Rahmen des Tool Fensters mit Fokus<br />-Fokussiert, ausgewählte vorläufige Registerkarte im Vordergrund<br />-Die Schaltfläche "Dokument gut Überlauf" bei Hover und drücken<br />-Ausgewählter Symbol Rahmen|
| HotTrack | : Hintergrund und Rahmen des Zieh Punkts der Bild Lauf Leiste<br />-Bild Lauf leisten Pfeilsymbol beim Drücken |
| InactiveCaption | -Inaktive IDE und Fenster Schaltflächen Symbole beim Hover<br />-Titelleisten Hintergrund für IDE und unregelmäßige Fenster<br />-Deaktivierter Such Steuerungs Hintergrund |
| InactiveCaptionText | -Inaktive IDE und vorgezogene Windows-Titelleisten Vordergrund (Text und Symbole)<br />-Inaktive Fenster Schaltflächen Hintergrund und Rahmen bei Hover<br />-Schaltflächen-Hintergrund und Rahmen für Tool Fenster ohne Fokus<br />-Deaktivierte Such Steuerelemente |
| Menü | -Dropdown Menühintergrund<br />-Aktivierter und deaktivierter häkchenhintergrund |
| MenuText | -Dropdown Menü Rahmen<br />-Häkchen<br />-Menü Symbole<br />-Dropdown Menü Text<br />-Ausgewählter Symbol Rahmen |
| Bildlaufleiste | -Bild Lauf Leiste und Pfeil Hintergrund der Bild Lauf Leiste, alle Zustände |
| Fenster | -Automatisches Ausblenden des Registerkarten Hintergrunds<br />-Menüleiste und Befehls Regal Hintergrund<br />-Ohne Fokus oder nicht ausgewähltes Dokument Fenster Registerkarte Hintergrund und Dokument Rahmen, für offene und vorläufige Registerkarten<br />-Der Titelleisten Hintergrund des Tool Fensters ohne Fokus<br />-Tool Fenster-Registerkarten Hintergrund, sowohl ausgewählt als auch nicht ausgewählt |
| WindowFrame | -IDE-Rahmen |
| Windowtext | -Automatische Ausblenden der Registerkarte im Vordergrund<br />-Ausgewählte Tool Fenster-Registerkarte im Vordergrund<br />-Nicht fokussierte Dokument Fenster Registerkarte und ohne Fokus oder nicht ausgewählte vorläufige Registerkarten Vordergrund<br />-Strukturansicht Standard Vordergrund und Mauszeiger auf nicht ausgewähltes Symbol<br />-Tool Fenster hat Registerkarten Rahmen ausgewählt<br />: Hintergrund, Rahmen und Symbol der Bild Lauf Leiste |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a> Verfügbar machen von Farben für Endbenutzer

### <a name="overview"></a>Übersicht

Manchmal empfiehlt es sich, den Endbenutzern das Anpassen Ihrer Benutzeroberfläche zu ermöglichen, z. b. Wenn Sie einen Code-Editor oder eine Entwurfs Oberfläche erstellen. Die gängigste Methode hierfür ist die Verwendung des Dialog Felds Extras- **&gt; Optionen** . Wenn Sie nicht über eine hochgradig spezialisierte Benutzeroberfläche verfügen, die spezielle Steuerelemente erfordert, ist die einfachste Möglichkeit zur Darstellung der Anpassung über die Seite **Schriftarten und Farben** im Abschnitt **Umgebung** des Dialog Felds. Für jedes Element, das Sie für die Anpassung verfügbar machen, kann der Benutzer die Vordergrundfarbe, die Hintergrundfarbe oder beides ändern.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Ein VSPackage für Ihre anpassbaren Farben wird aufgebaut

Ein VSPackage kann die Schriftarten und Farben mithilfe von benutzerdefinierten Kategorien steuern und Elemente auf der Eigenschaften Seite Schriftarten und Farben anzeigen. Bei Verwendung dieses Mechanismus müssen VSPackages die [ivsfontandcolordefaultsprovider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) -Schnittstelle und die zugehörigen Schnittstellen implementieren.

Im Prinzip kann dieser Mechanismus verwendet werden, um alle vorhandenen Anzeigeelemente und die Kategorien zu ändern, in denen Sie enthalten sind. Es sollte jedoch nicht zum Ändern der Kategorie Text-Editor oder seiner Anzeigeelemente verwendet werden. Weitere Informationen zur Kategorie Text-Editor finden Sie unter [Übersicht über Schriftart und Farben](/previous-versions/visualstudio/visual-studio-2015/extensibility/font-and-color-overview?preserve-view=true&view=vs-2015).

Ein VSPackage muss Folgendes durchführen, um benutzerdefinierte Kategorien oder Elemente anzuzeigen:

- **Erstellen oder identifizieren Sie Kategorien in der Registrierung.** Diese Informationen werden von der IDE-Implementierung der **Schriftarten und Farben** -Eigenschaften Seite verwendet, um den Dienst, der eine bestimmte Kategorie unterstützt, ordnungsgemäß abzufragen.

- **Erstellen oder identifizieren Sie Gruppen in der Registrierung (optional).** Es kann sinnvoll sein, eine Gruppe zu definieren, die die Union von zwei oder mehr Kategorien darstellt. Wenn eine Gruppe definiert ist, führt die IDE automatisch Unterkategorien zusammen und verteilt Anzeigeelemente in der Gruppe.

- **Implementieren Sie IDE-Unterstützung.**

- **Bearbeiten von Schriftart-und Farbänderungen.**

#### <a name="to-create-or-identify-categories"></a>So erstellen oder identifizieren Sie Kategorien

Erstellen Sie einen besonderen Typ von kategorieregistrierungs Eintrag unter, `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` wobei `<Category>` der nicht lokalisierte Name der Kategorie ist.

Füllen Sie die Registrierung mit zwei Werten auf:

| Name | Typ | Daten | BESCHREIBUNG |
| --- | --- | --- | --- |
| Category | REG_SZ | GUID | Eine GUID, die zur Identifizierung der Kategorie erstellt wurde. |
| Paket | REG_SZ | GUID | Die GUID des VSPackage-Dienstanbieter, der die Kategorie unterstützt. |

 Der in der Registrierung angegebene Dienst muss eine Implementierung von [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) für die entsprechende Kategorie bereitstellen.

#### <a name="to-create-or-identify-groups"></a>So erstellen oder identifizieren Sie Gruppen

Erstellen Sie eine besondere Art von Kategorisierungs Eintrag unter, `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` wobei `<group>` der nicht lokalisierte Name der Gruppe ist.

Füllen Sie die Registrierung mit zwei Werten auf:

| Name | Typ | Daten | BESCHREIBUNG |
|--- | --- | --- | --- |
| Category | REG_SZ | GUID | Eine GUID, die zur Identifizierung der Kategorie erstellt wurde. |
| Paket | REG_SZ | GUID | Die GUID des VSPackage-Dienstanbieter, der die Kategorie unterstützt. |

Der in der Registrierung angegebene Dienst muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> für die zugehörige Gruppe eine Implementierung von bereitstellen.

![Implementierung von IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Implementierung von `IVsFontAndColorGroup`.

### <a name="to-implement-ide-support"></a>So implementieren Sie IDE-Unterstützung

Implementieren Sie [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject), das entweder eine [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) -Schnittstelle oder eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> Schnittstelle zur IDE für jede angegebene Kategorie oder Gruppen-GUID zurückgibt.

Für jede unterstützte Kategorie implementiert ein VSPackage eine separate Instanz der [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) -Schnittstelle.

Die durch [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) implementierten Methoden müssen die IDE wie folgt bereitstellen:

- Listen der Anzeigeelemente in der Kategorie

- Lokalisierbare Namen für Anzeigeelemente

- Anzeigen von Informationen für jedes Mitglied der Kategorie

> [!NOTE]
> Jede Kategorie muss mindestens ein Anzeigeelement enthalten.

Die IDE verwendet die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> Schnittstelle, um eine Union mehrerer Kategorien zu definieren.

Die-Implementierung stellt die IDE mit bereit:

- Eine Liste der Kategorien, die eine bestimmte Gruppe bilden.

- Zugriff auf Instanzen von [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) , die jede Kategorie innerhalb der Gruppe unterstützen

- Lokalisierbare Gruppennamen

#### <a name="updating-the-ide"></a>Aktualisieren der IDE

Die IDE speichert Informationen zu Schriftart-und Farbeinstellungen zwischen. Daher ist es eine bewährte Vorgehensweise, nach jeder Änderung der IDE-Schriftart-und Farbkonfiguration sicherzustellen, dass der Cache auf dem neuesten Stand ist.

Das Aktualisieren des Caches erfolgt über die [ivsfontandcolorcachemanager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) -Schnittstelle und kann global oder nur für ausgewählte Elemente ausgeführt werden.

### <a name="handling-font-and-color-changes"></a>Behandeln von Schriftart-und Farbänderungen

Um die farbliche Farbgebung von Text, den ein VSPackage anzeigt, ordnungsgemäß zu unterstützen, muss der für das VSPackage unterstützende Farb Erfassungs Dienst auf die vom Benutzer initiierten Änderungen reagieren, die über die Eigenschaften Seite Schriftarten und Farben vorgenommen wurden.

Zu diesem Zweck muss ein VSPackage folgende Aktionen ausführen:

- **behandeln Sie von IDE generierte Ereignisse** , indem Sie die [ivsfontandcolorevents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) -Schnittstelle implementieren. Die IDE Ruft die entsprechende Methode auf, die auf die Benutzer Änderungen der Seite Schriftarten und Farben folgt. Beispielsweise wird die [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) -Methode aufgerufen, wenn eine neue Schriftart ausgewählt wird.

  **OR**

- **Abfragen der IDE auf Änderungen**. Dies kann über die vom System implementierte [ivsfontandcolorstorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) -Schnittstelle durchgeführt werden. Obwohl die [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) -Methode in erster Linie zur Unterstützung der Persistenz dient, kann Sie Schriftart-und Farbinformationen für Anzeigeelemente abrufen. Weitere Informationen zu Schriftart-und Farbeinstellungen finden Sie im MSDN-Artikel [zugreifen auf gespeicherte Schriftart-und Farbeinstellungen](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-stored-font-and-color-settings?preserve-view=true&view=vs-2015).

> [!NOTE]
> Um sicherzustellen, dass die Abruf Ergebnisse richtig sind, verwenden Sie die [ivsfontandcolorcachemanager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) -Schnittstelle, um zu bestimmen, ob eine Cache Leerung und ein Update erforderlich sind, bevor die Abruf Methoden der [ivsfontandcolorstorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) -Schnittstelle aufgerufen werden.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Registrieren der benutzerdefinierten Schriftart-und Farb Kategorie ohne Implementieren von Schnittstellen

Im folgenden Codebeispiel wird veranschaulicht, wie Sie die benutzerdefinierte Schriftart-und Farb Kategorie registrieren, ohne Schnittstellen zu implementieren:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Für dieses Codebeispiel:

- `"NameID"` = die Ressourcen-ID des lokalisierten Kategorienamens in Ihrem Paket
- `"ToolWindowPackage"` = Paket-GUID
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` ist nur ein Beispiel, und der tatsächliche Wert kann eine neue GUID sein, die vom Implementierer bereitgestellt wird.

### <a name="set-the-font-and-color-property-category-guid"></a>Festlegen der Schriftart-und Farbeigenschaften Kategorie-GUID

Im folgenden Codebeispiel wird das Festlegen der Kategorie-GUIDs veranschaulicht.

```csharp
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
IVsTextEditorPropertyContainer spPropContainer;
Guid GUID_EditPropCategory_View_MasterSettings =
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
hr = spPropCatContainer.GetPropertyCategory(
ref GUID_EditPropCategory_View_MasterSettings,
out spPropContainer);
if(hr == 0)
{
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,
catGUID);
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,
catGUID);
}
}
```
