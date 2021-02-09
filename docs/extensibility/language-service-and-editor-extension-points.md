---
title: Sprachdienst-und Editor-Erweiterungs Punkte | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Erweiterungs Punkte im Visual Studio-Code-Editor, die Sie erweitern können, einschließlich der meisten Sprachdienst Features.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 925bc0f123649bd0d5d29f5a7bec83227829b8af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915226"
---
# <a name="language-service-and-editor-extension-points"></a>Sprachdienst-und Editor-Erweiterungs Punkte
Der-Editor stellt Erweiterungs Punkte bereit, die Sie als Managed Extensibility Framework Komponenten (MEF), einschließlich der meisten Sprachdienst Features, erweitern können. Dies sind die Hauptkategorien der Erweiterungs Punkte:

- Inhaltstypen

- Klassifizierungs Typen und Klassifizierungs Formate

- Ränder und Bild Lauf leisten

- Tags

- Zusatzelemente

- Maus Prozessoren

- Drop Handler

- Optionen

- IntelliSense

## <a name="extend-content-types"></a>Erweitern von Inhaltstypen
 Inhaltstypen sind die Definitionen der Arten von Text, die vom Editor behandelt werden, z. b. "Text", "Code" oder "CSharp". Sie definieren einen neuen Inhaltstyp, indem Sie eine Variable des Typs deklarieren <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> und dem neuen Inhaltstyp einen eindeutigen Namen geben. Um den Inhaltstyp mit dem Editor zu registrieren, exportieren Sie ihn mit den folgenden Attributen:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> der Name des Inhaltstyps.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> der Name des Inhaltstyps, von dem dieser Inhaltstyp abgeleitet wird. Ein Inhaltstyp kann von mehreren anderen Inhaltstypen erben.

  Da die- <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> Klasse versiegelt ist, können Sie Sie ohne Typparameter exportieren.

  Das folgende Beispiel zeigt Export Attribute für eine Inhaltstyp Definition.

```
[Export]
[Name("test")]
[BaseDefinition("code")]
[BaseDefinition("projection")]
internal static ContentTypeDefinition TestContentTypeDefinition;
```

 Inhaltstypen können auf 0 (null) oder mehr bereits vorhandenen Inhaltstypen basieren. Dabei handelt es sich um die integrierten Typen:

- Beliebig: der grundlegende Inhaltstyp. Übergeordnetes Element aller anderen Inhaltstypen.

- Text: der Basistyp für nicht Projektions Inhalte. Erbt von "Any".

- Klartext: für nicht-Codetext. Erbt von "Text".

- Code: für Code aller Art. Erbt von "Text".

- Inert: schließt den Text von keiner Art von Behandlung aus. Auf den Text dieses Inhaltstyps wird nie eine Erweiterung angewendet.

- Projektion: für den Inhalt von Projektions Puffern. Erbt von "Any".

- IntelliSense: für den Inhalt von IntelliSense. Erbt von "Text".

- Sighelp: Signatur Hilfe. Erbt von "IntelliSense".

- Sighelp-doc: Hilfe Dokumentation zur Signatur. Erbt von "IntelliSense".

  Dies sind einige der Inhaltstypen, die von Visual Studio definiert werden, und einige der Sprachen, die in Visual Studio gehostet werden:

- Basic

- C/C++

- ConsoleOutput

- CSharp

- CSS

- ENC

- FindResults

- F#

- HTML

- JScript

- XAML

- XML

  Um die Liste der verfügbaren Inhaltstypen zu ermitteln, importieren Sie den <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> , der die Sammlung der Inhaltstypen für den Editor beibehält. Mit dem folgenden Code wird dieser Dienst als Eigenschaft importiert.

```
[Import]
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }
```

 Um einen Inhaltstyp einer Dateinamenerweiterung zuzuordnen, verwenden Sie <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> .

> [!NOTE]
> In Visual Studio werden Dateinamen Erweiterungen mithilfe von in <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> einem Sprachdienst Paket registriert. Der ordnet <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> einen MEF-Inhaltstyp einer Dateinamenerweiterung zu, die auf diese Weise registriert wurde.

 Wenn Sie die Dateinamenerweiterung in die Inhaltstyp Definition exportieren möchten, müssen Sie die folgenden Attribute einschließen:

- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: gibt die Dateinamenerweiterung an.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: gibt den Inhaltstyp an.

  Da die- <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> Klasse versiegelt ist, können Sie Sie ohne Typparameter exportieren.

  Das folgende Beispiel zeigt das Exportieren von Attributen in einer Dateinamenerweiterung in eine Inhaltstyp Definition.

```
[Export]
[FileExtension(".test")]
[ContentType("test")]
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;
```

 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>Verwaltet die Zuordnungen zwischen Dateinamen Erweiterungen und Inhaltstypen.

## <a name="extend-classification-types-and-classification-formats"></a>Klassifizierungs Typen und Klassifizierungs Formate erweitern
 Mithilfe von Klassifizierungs Typen können Sie die Arten von Text definieren, für die Sie unterschiedliche Verarbeitungsmöglichkeiten bereitstellen möchten (z. b. das "Schlüsselwort" "blau" und "comment" Text grün). Definieren Sie einen neuen Klassifizierungstyp, indem Sie eine Variable des Typs deklarieren <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> und ihr einen eindeutigen Namen geben.

 Um den Klassifizierungstyp beim Editor zu registrieren, exportieren Sie ihn mit den folgenden Attributen:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Klassifizierungs Typs.

- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: der Name des Klassifizierungs Typs, von dem dieser Klassifizierungstyp erbt. Alle Klassifizierungs Typen erben von "Text", und ein Klassifizierungstyp kann von mehreren anderen Klassifizierungs Typen erben.

  Da die- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> Klasse versiegelt ist, können Sie Sie ohne Typparameter exportieren.

  Das folgende Beispiel zeigt Export Attribute für eine Klassifikations Typdefinition.

```
[Export]
[Name("csharp.test")]
[BaseDefinition("test")]
internal static ClassificationTypeDefinition CSharpTestDefinition;
```

 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>Ermöglicht den Zugriff auf Standard Klassifizierungen. Folgende Klassifizierungs Typen sind integriert:

- "text"

- "Natural Language" (abgeleitet von "Text")

- "formale Sprache" (abgeleitet von "Text")

- "String" (abgeleitet von "Literal")

- "Character" (abgeleitet von "Literal")

- "Numerisch" (abgeleitet von "Literal")

  Ein Satz unterschiedlicher Fehlertypen erbt von <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition> . Sie enthalten die folgenden Fehlertypen:

- "Syntax Fehler"

- "Compilerfehler"

- "anderer Fehler"

- davor

  Zum Ermitteln der Liste der verfügbaren Klassifizierungs Typen importieren Sie den <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> , der die Auflistung der Klassifizierungs Typen für den Editor beibehält. Mit dem folgenden Code wird dieser Dienst als Eigenschaft importiert.

```
[Import]
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }
```

 Sie können eine Klassifizierungs Format Definition für den neuen Klassifizierungstyp definieren. Leiten Sie eine Klasse von ab <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> , und exportieren Sie Sie mit dem-Typ und <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> den folgenden Attributen:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Formats.

- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: der Anzeige Name des Formats.

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: gibt an, ob das Format auf der Seite **Schriftarten und Farben** des Dialog Felds **Optionen** angezeigt wird.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Priorität des Formats. Gültige Werte sind von <xref:Microsoft.VisualStudio.Text.Classification.Priority> .

- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: der Name des Klassifizierungs Typs, dem dieses Format zugeordnet ist.

  Das folgende Beispiel zeigt Export Attribute für eine Klassifizierungs Format Definition.

```
[Export(typeof(EditorFormatDefinition))]
[ClassificationType(ClassificationTypeNames = "test")]
[Name("test")]
[DisplayName("Test")]
[UserVisible(true)]
[Order(After = Priority.Default, Before = Priority.High)]
internal sealed class TestFormat : ClassificationFormatDefinition
```

 Zum Ermitteln der Liste der verfügbaren Formate importieren Sie den <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> , der die Auflistung der Formate für den Editor beibehält. Mit dem folgenden Code wird dieser Dienst als Eigenschaft importiert.

```
[Import]
internal IEditorFormatMapService FormatMapService { get; set; }
```

## <a name="extend-margins-and-scrollbars"></a>Erweitern von Rändern und Bild Lauf leisten
 Ränder und Bild Lauf leisten sind die Haupt Ansichts Elemente des Editors, zusätzlich zur Textansicht. Sie können eine beliebige Anzahl von Rändern zusätzlich zu den Standard Rändern bereitstellen, die in der Textansicht angezeigt werden.

 Implementieren <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> Sie eine Schnittstelle, um einen Rand zu definieren. Sie müssen auch die- <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> Schnittstelle implementieren, um den Rand zu erstellen.

 Um den Margin-Anbieter beim Editor zu registrieren, müssen Sie den Anbieter mit den folgenden Attributen exportieren:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Randes.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge, in der der Rand relativ zu den anderen Rändern angezeigt wird.

   Dabei handelt es sich um die integrierten Ränder:

  - "Horizontale WPF-Scrollleiste"

  - "Vertikale Scrollleiste von WPF"

  - "WPF-Zeilennummern Rand"

    Horizontale Ränder mit einem Order-Attribut von `After="Wpf Horizontal Scrollbar"` werden unterhalb des integrierten Rands angezeigt, und horizontale Ränder mit einem Order-Attribut von `Before ="Wpf Horizontal Scrollbar"` werden über dem integrierten Rand angezeigt. Rechte vertikale Ränder mit einem Order-Attribut von `After="Wpf Vertical Scrollbar"` werden rechts von der Scrollleiste angezeigt. Linke vertikale Ränder mit einem Order-Attribut von `After="Wpf Line Number Margin"` werden links neben dem Zeilennummern Rand angezeigt (sofern sichtbar).

- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: die Art des Randes (Links, rechts, oben oder unten).

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. b. "Text" oder "Code"), für den der Rand gültig ist.

  Im folgenden Beispiel werden die Export Attribute eines Margin-Anbieters für einen Rand angezeigt, der rechts neben dem Zeilennummern Rand angezeigt wird.

```
[Export(typeof(IWpfTextViewMarginProvider))]
[Name("TestMargin")]
[Order(Before = "Wpf Line Number Margin")]
[MarginContainer(PredefinedMarginNames.Left)]
[ContentType("text")]
```

## <a name="extend-tags"></a>Tags erweitern
 Mithilfe von Tags können Sie Daten verschiedenen Arten von Text zuordnen. In vielen Fällen werden die zugeordneten Daten als visueller Effekt angezeigt, aber nicht alle Tags verfügen über eine visuelle Darstellung. Sie können eine eigene tagart definieren, indem Sie implementieren <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . Sie müssen auch implementieren, <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> um die Tags für eine bestimmte Menge von Text spannen bereitzustellen, und ein, <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> um das Tagger bereitzustellen. Sie müssen den Tagger-Anbieter mit den folgenden Attributen exportieren:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. b. "Text" oder "Code"), für den das Tag gültig ist.

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: die Art des Tags.

  Das folgende Beispiel zeigt Export Attribute für einen Tagger-Anbieter.

\<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> die folgenden Arten von Tags sind integriert:

- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: ist einem zugeordnet <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> .

- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: ist mit Fehlertypen verknüpft.

- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: einem Zusatzelement zugeordnet.

  > [!NOTE]
  > Ein Beispiel für einen <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> finden Sie unter der highlightwordtag-Definition in Exemplarische Vorgehensweise [: Markieren von Text](../extensibility/walkthrough-highlighting-text.md).

- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: zugeordnet mit Regionen, die in Gliederung erweitert oder reduziert werden können.

- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: definiert den Leerraum, den ein Zusatzelement in einer Textansicht einnimmt. Weitere Informationen zu Zusatzelementen für das Speicherplatz aushandeln finden Sie im folgenden Abschnitt.

- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: stellt automatischen Abstand und Größenanpassung für das Zusatzelement bereit.

  Wenn Sie Tags für Puffer und Sichten suchen und verwenden möchten, importieren <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> Sie das oder das <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService> , das eine <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> vom angeforderten Typ erhält. Mit dem folgenden Code wird dieser Dienst als Eigenschaft importiert.

```
[Import]
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }
```

#### <a name="tags-and-markerformatdefinitions"></a>Tags und markerformatdefinitions
 Sie können die- <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> Klasse erweitern, um die Darstellung eines Tags zu definieren. Sie müssen die Klasse (als <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition> ) mit den folgenden Attributen exportieren:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name, der zum Verweisen auf dieses Format verwendet wird

- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Dies bewirkt, dass das Format in der Benutzeroberfläche angezeigt wird.

  Im Konstruktor definieren Sie den anzeigen Amen und die Darstellung des Tags. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> definiert die Füllfarbe und <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> definiert die Rahmenfarbe. Der <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> ist der lokalisierbare Name der Format Definition.

  Im folgenden finden Sie ein Beispiel für eine Format Definition:

```
[Export(typeof(EditorFormatDefinition))]
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
[UserVisible(true)]
internal class HighlightWordFormatDefinition : MarkerFormatDefinition
{
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
}

```

 Wenn Sie diese Format Definition auf ein Tag anwenden möchten, verweisen Sie auf den Namen, den Sie im Name-Attribut der-Klasse (nicht auf den anzeigen Amen) festgelegt haben.

> [!NOTE]
> Ein Beispiel für einen <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> finden Sie unter der highlightwordformatdefinition-Klasse in Exemplarische Vorgehensweise [: Markieren von Text](../extensibility/walkthrough-highlighting-text.md).

## <a name="extend-adornments"></a>Erweitern von Zusatzelementen
 Zusatzelemente definieren visuelle Effekte, die entweder dem Text hinzugefügt werden können, der in einer Textansicht oder in der Textansicht angezeigt wird. Sie können ein eigenes Zusatzelement als jeden beliebigen Typ von definieren <xref:System.Windows.UIElement> .

 In ihrer Zusatzelement-Klasse müssen Sie einen deklarieren <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> . Um Ihre Zusatzelement-Schicht zu registrieren, exportieren Sie Sie mit den folgenden Attributen:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Zusatz Elements.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge des Zusatz Elements in Bezug auf andere Zusatzelement-Ebenen. Die-Klasse <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> definiert vier Standard Schichten: Auswahl, Gliederung, Einfügemarke und Text.

  Das folgende Beispiel zeigt Export Attribute für eine Zusatzelement-Ebenendefinition.

```
[Export]
[Name("TestEmbeddedAdornment")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
internal AdornmentLayerDefinition testLayerDefinition;
```

 Sie müssen eine zweite Klasse erstellen, die implementiert <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> und das zugehörige-Ereignis behandelt, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> indem das Zusatzelement instanziiert wird. Sie müssen diese Klasse mit den folgenden Attributen exportieren:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. b. "Text" oder "Code"), für den das Zusatzelement gültig ist.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: die Art der Textansicht, für die dieses Zusatzelement gültig ist. Die-Klasse <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> verfügt über den Satz vordefinierter Text Ansichts Rollen. Beispielsweise <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> wird hauptsächlich für Text Ansichten von-Dateien verwendet. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> wird für Text Ansichten verwendet, die ein Benutzer mit einer Maus und Tastatur bearbeiten oder navigieren kann. Beispiele für <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Ansichten sind die Editor-Textansicht und das Fenster **Ausgabe** .

  Das folgende Beispiel zeigt Export Attribute für den Zusatzelement Anbieter.

```
[Export(typeof(IWpfTextViewCreationListener))]
[ContentType("csharp")]
[TextViewRole(PredefinedTextViewRoles.Document)]
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener
```

 Bei einem Zusatzelement mit Platz Ausgleich handelt es sich um einen Wert, der Platz auf derselben Ebene wie der Text einnimmt. Um diese Art von Zusatzelement zu erstellen, müssen Sie eine Tagklasse definieren, die von erbt <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> . Dadurch wird die Menge des Speicherplatzes definiert, den das Zusatzelement einnimmt.

 Wie bei allen Zusatzelementen müssen Sie die Definition der Zusatzelement-Schicht exportieren.

```
[Export]
[Name("TestAdornment")]
[Order(After = DefaultAdornmentLayers.Text)]
internal AdornmentLayerDefinition testAdornmentLayer;
```

 Zum Instanziieren des Zusatz Elements mit Platz Ausgleich müssen Sie eine Klasse erstellen, die implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , zusätzlich zu der Klasse, die implementiert <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (wie bei anderen Arten von Zusatzelementen).

 Um den Tagger-Anbieter zu registrieren, müssen Sie ihn mit den folgenden Attributen exportieren:

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. b. "Text" oder "Code"), für den das Zusatzelement gültig ist.

- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: die Art der Textansicht, für die dieses Tag oder Zusatzelement gültig ist. Die-Klasse <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> verfügt über den Satz vordefinierter Text Ansichts Rollen. Beispielsweise <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> wird hauptsächlich für Text Ansichten von-Dateien verwendet. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> wird für Text Ansichten verwendet, die ein Benutzer mit einer Maus und Tastatur bearbeiten oder navigieren kann. Beispiele für <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Ansichten sind die Editor-Textansicht und das Fenster **Ausgabe** .

- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: die Art von Tag oder Zusatzelement, die Sie definiert haben. Sie müssen ein zweites für hinzufügen <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> .

  Das folgende Beispiel zeigt Export Attribute auf dem Tagger-Anbieter für ein Zusatzelement-Tag mit Raum Aushandlung.

```
[Export(typeof(ITaggerProvider))]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Document)]
[TagType(typeof(SpaceNegotiatingAdornmentTag))]
[TagType(typeof(TestSpaceNegotiatingTag))]
internal sealed class TestTaggerProvider : ITaggerProvider
```

## <a name="extending-mouse-processors"></a>Erweitern von Maus Prozessoren
 Sie können eine spezielle Behandlung für Maus Eingaben hinzufügen. Erstellen Sie eine Klasse, die von erbt, <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> und überschreiben Sie die Mausereignisse für die Eingabe, die Sie verarbeiten möchten. Außerdem müssen Sie <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> in einer zweiten Klasse implementieren und Sie mit dem Exportieren <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> , der die Art des Inhalts (z. b. "Text" oder "Code") angibt, für den der Maus Handler gültig ist.

 Das folgende Beispiel zeigt Export Attribute für einen Maus Prozessor Anbieter.

```
[Export(typeof(IMouseProcessorProvider))]
[Name("test mouse processor")]
[ContentType("text")]
[TextViewRole(PredefinedTextViewRoles.Interactive)]
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider
```

## <a name="extend-drop-handlers"></a>Löschen von Lösch Handlern
 Sie können das Verhalten von Drop-Handlern für bestimmte Arten von Text anpassen, indem Sie eine Klasse erstellen, die implementiert, <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> und eine zweite Klasse, die implementiert <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> , um den Drop-Handler zu erstellen. Sie müssen den Drop-Handler mit den folgenden Attributen exportieren:

- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: das Textformat, für das dieser Drop-Handler gültig ist. Die folgenden Formate werden in der Reihenfolge der Priorität von der höchsten zum niedrigsten verarbeitet:

  1. Beliebige benutzerdefinierte Formate

  2. FileDrop

  3. Enhancedmetadatendatei

  4. Waveaudiodatei

  5. FF

  6. DIF

  7. Gebietsschema

  8. Palette

  9. Daten

  10. Serialisierbar

  11. SymbolicLink

  12. XAML

  13. XamlPackage

  14. TIFF

  15. Bitmap

  16. DIB

  17. MetafilePicture

  18. CSV

  19. System.String

  20. HTML-Format

  21. UnicodeText

  22. OemText

  23. Text

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Drop-Handlers.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge des Drop-Handlers vor oder nach dem standardmäßigen Drop-Handler. Der Standard Ablage Handler für Visual Studio heißt "defaultfiledrophandler".

  Das folgende Beispiel zeigt Export Attribute für einen Drop Handler-Anbieter.

```
[Export(typeof(IDropHandlerProvider))]
[DropFormat("Text")]
[Name("TestDropHandler")]
[Order(Before="DefaultFileDropHandler")]
internal class TestDropHandlerProvider : IDropHandlerProvider
```

## <a name="extending-editor-options"></a>Erweitern von Editor Optionen
 Sie können Optionen definieren, die nur in einem bestimmten Bereich gültig sind, z. b. in einer Textansicht. Der-Editor bietet diese vordefinierten Optionen: Editor-Optionen, Ansichtsoptionen und Windows Presentation Foundation Optionen (WPF). Diese Optionen finden Sie unter <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions> , <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions> und <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions> .

 Um eine neue Option hinzuzufügen, leiten Sie eine Klasse von einer der folgenden Options Definitions Klassen ab:

- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>

- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>

  Im folgenden Beispiel wird gezeigt, wie eine Options Definition mit einem booleschen Wert exportiert wird.

```
[Export(typeof(EditorOptionDefinition))]
internal sealed class TestOption : EditorOptionDefinition<bool>
```

## <a name="extend-intellisense"></a>Erweitern von IntelliSense
 IntelliSense ist ein allgemeiner Begriff für eine Gruppe von Funktionen, die Informationen zu strukturiertem Text und Anweisungs Vervollständigung bereitstellen. Zu diesen Funktionen zählen Anweisungs Vervollständigung, Signatur Hilfe, Quick Infos und Glühbirnen. Mithilfe der Anweisungs Vervollständigung können Benutzer ein sprach Schlüsselwort oder einen Elementnamen richtig eingeben Signatur Hilfe zeigt die Signatur oder Signaturen für die Methode an, die der Benutzer soeben eingegeben hat. QuickInfo zeigt eine komplette Signatur für einen Typ oder einen Elementnamen an, wenn der Mauszeiger darauf liegt. Glühbirnen stellen zusätzliche Aktionen für bestimmte Bezeichner in bestimmten Kontexten bereit, z. b. das Umbenennen aller Vorkommen einer Variablen, nachdem ein Vorkommen umbenannt wurde.

 Der Entwurf einer IntelliSense-Funktion ist in allen Fällen ähnlich:

- Ein IntelliSense- *Broker* ist für den gesamten Prozess verantwortlich.

- Eine IntelliSense- *Sitzung* stellt die Abfolge der Ereignisse zwischen dem Auslösen des Präsentators und dem Commit oder Abbruch der Auswahl dar. Die Sitzung wird in der Regel durch eine Benutzer Geste ausgelöst.

- Ein IntelliSense- *Controller* ist verantwortlich für die Entscheidung, wann die Sitzung gestartet und beendet werden soll. Außerdem wird die Entscheidung getroffen, wann für die Informationen ein Commit ausgeführt werden soll und wann die Sitzung abgebrochen werden soll.

- Eine IntelliSense- *Quelle* stellt den Inhalt bereit und entscheidet die beste Entsprechung.

- Ein IntelliSense- *Presenter* ist für die Anzeige des Inhalts verantwortlich.

  In den meisten Fällen wird empfohlen, mindestens eine Quelle und einen Controller bereitzustellen. Sie können auch einen Presenter bereitstellen, wenn Sie die Anzeige anpassen möchten.

### <a name="implement-an-intellisense-source"></a>Implementieren einer IntelliSense-Quelle
 Zum Anpassen einer Quelle müssen Sie mindestens eine der folgenden Quell Schnittstellen implementieren:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> wurde als veraltet markiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

 Außerdem müssen Sie einen Anbieter derselben Art implementieren:

- <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>

- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>

> [!IMPORTANT]
> <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> wurde als veraltet markiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> .

 Sie müssen den Anbieter mit den folgenden Attributen exportieren:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name der Quelle.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. b. "Text" oder "Code"), für den die Quelle gilt.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge, in der die Quelle angezeigt werden soll (in Bezug auf andere Quellen).

- Das folgende Beispiel zeigt Export Attribute für einen Vervollständigungs Quell Anbieter.

```
Export(typeof(ICompletionSourceProvider))]
[Name(" Test Statement Completion Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestCompletionSourceProvider : ICompletionSourceProvider
```

 Weitere Informationen zum Implementieren von IntelliSense-Quellen finden Sie in den folgenden exemplarischen Vorgehensweisen:

- [Exemplarische Vorgehensweise: Anzeigen von Quick Infos](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Exemplarische Vorgehensweise: Anzeigen der Signatur Hilfe](../extensibility/walkthrough-displaying-signature-help.md)

- [Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md)

### <a name="implement-an-intellisense-controller"></a>Implementieren eines IntelliSense-Controllers
 Zum Anpassen eines Controllers müssen Sie die- <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> Schnittstelle implementieren. Außerdem müssen Sie einen Controller Anbieter mit den folgenden Attributen implementieren:

- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: der Name des Controllers.

- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: die Art des Inhalts (z. b. "Text" oder "Code"), auf den der Controller angewendet wird.

- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: die Reihenfolge, in der der Controller angezeigt werden soll (in Bezug auf andere Controller).

  Das folgende Beispiel zeigt Export Attribute für einen Vervollständigungs Controller Anbieter.

```
Export(typeof(IIntellisenseControllerProvider))]
[Name(" Test Controller Provider")]
[Order(Before = "default")]
[ContentType("text")]
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider
```

 Weitere Informationen zur Verwendung von IntelliSense-Controllern finden Sie in den folgenden exemplarischen Vorgehensweisen:

- [Exemplarische Vorgehensweise: Anzeigen von Quick Infos](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)
