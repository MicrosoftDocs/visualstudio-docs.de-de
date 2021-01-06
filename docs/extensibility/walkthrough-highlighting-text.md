---
title: 'Exemplarische Vorgehensweise: Markieren von Text | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie jedes Vorkommen des aktuellen Worts in einer Textdatei hervorheben, indem Sie dem Editor in dieser exemplarischen Vorgehensweise visuelle Effekte hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32af7033eb29d223a5ecfafaccb0a3123ab88d06
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877129"
---
# <a name="walkthrough-highlight-text"></a>Exemplarische Vorgehensweise: Markieren von Text
Sie können dem Editor andere visuelle Effekte hinzufügen, indem Sie Managed Extensibility Framework Komponenten Teile (MEF) erstellen. In dieser exemplarischen Vorgehensweise wird gezeigt, wie jedes Vorkommen des aktuellen Worts in einer Textdatei hervorgehoben wird. Wenn ein Wort mehr als einmal in einer Textdatei vorkommt und Sie die Einfügemarke in einem Vorkommen positionieren, wird jedes Vorkommen hervorgehoben.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Es ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts

1. Erstellen Sie ein c#-VSIX-Projekt. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual c#/Erweiterbarkeit** und dann **VSIX-Projekt** aus.) Benennen Sie die Projekt Mappe `HighlightWordTest` .

2. Fügen Sie dem Projekt eine Editor-Klassifizierungs Element Vorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

## <a name="define-a-textmarkertag"></a>Definieren eines textmarkertag
 Der erste Schritt bei der Hervorhebung von Text besteht in der Unterklasse und der Definition des Erscheinungs Bilds <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>So definieren Sie ein textmarkertag und eine markerformatdefinition

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie Sie **highlightwordtag**.

2. Fügen Sie die folgenden Verweise hinzu:

    1. Microsoft. VisualStudio. coreutility

    2. Microsoft. VisualStudio. Text. Data

    3. Microsoft. VisualStudio. Text. Logic

    4. Microsoft. VisualStudio. Text. UI

    5. Microsoft. VisualStudio. Text. UI. WPF

    6. System.ComponentModel.Composition

    7. Präsentation. Core

    8. Präsentation. Framework

3. Importieren Sie die folgenden Namespaces.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using System.Threading;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Text.Tagging;
    using Microsoft.VisualStudio.Utilities;
    using System.Windows.Media;
    ```

4. Erstellen Sie eine Klasse, die von erbt, <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> und benennen Sie Sie `HighlightWordTag` .

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Erstellen Sie eine zweite Klasse, die von erbt <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> , und benennen Sie Sie `HighlightWordFormatDefinition` . Um diese Format Definition für das Tag zu verwenden, müssen Sie Sie mit den folgenden Attributen exportieren:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Tags verwenden diese, um auf dieses Format zu verweisen.

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Dies bewirkt, dass das Format in der Benutzeroberfläche angezeigt wird.

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. Definieren Sie im Konstruktor für highlightwordformatdefinition ihren anzeigen Amen und die Darstellung. Die Background-Eigenschaft definiert die Füllfarbe, während die Vordergrund Eigenschaft die Rahmenfarbe definiert.

    ```csharp
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. Übergeben Sie im Konstruktor für highlightwordtag den Namen der Format Definition, die Sie erstellt haben.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Implementieren eines itagger
 Der nächste Schritt besteht darin, die- <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Schnittstelle zu implementieren. Diese Schnittstelle weist einem angegebenen Text Puffer Tags zu, die Text Hervorhebungen und andere visuelle Effekte bereitstellen.

### <a name="to-implement-a-tagger"></a>So implementieren Sie einen Tagger

1. Erstellen Sie eine Klasse, die <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> vom Typ implementiert `HighlightWordTag` , und benennen Sie Sie `HighlightWordTagger` .

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Fügen Sie der-Klasse die folgenden privaten Felder und Eigenschaften hinzu:

    - Ein <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , der der aktuellen Textansicht entspricht.

    - Ein <xref:Microsoft.VisualStudio.Text.ITextBuffer> , der dem Text Puffer entspricht, der der Textansicht zugrunde liegt.

    - Ein <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> , der verwendet wird, um nach Text zu suchen.

    - Ein <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> , das über Methoden zum Navigieren innerhalb von Text spannen verfügt.

    - Ein <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> , der den zu markierenden Satz von Wörtern enthält.

    - Ein <xref:Microsoft.VisualStudio.Text.SnapshotSpan> , der dem aktuellen Wort entspricht.

    - Eine <xref:Microsoft.VisualStudio.Text.SnapshotPoint> , die der aktuellen Position der Einfügemarke entspricht.

    - Ein Lock-Objekt.

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. Fügen Sie einen Konstruktor hinzu, der die zuvor aufgeführten Eigenschaften initialisiert und die <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> -und- <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> Ereignishandler hinzufügt.

    ```csharp
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,
    ITextStructureNavigator textStructureNavigator)
    {
        this.View = view;
        this.SourceBuffer = sourceBuffer;
        this.TextSearchService = textSearchService;
        this.TextStructureNavigator = textStructureNavigator;
        this.WordSpans = new NormalizedSnapshotSpanCollection();
        this.CurrentWord = null;
        this.View.Caret.PositionChanged += CaretPositionChanged;
        this.View.LayoutChanged += ViewLayoutChanged;
    }

    ```

4. Die Ereignishandler bezeichnen beide die- `UpdateAtCaretPosition` Methode.

    ```csharp
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        // If a new snapshot wasn't generated, then skip this layout 
        if (e.NewSnapshot != e.OldSnapshot)
        {
            UpdateAtCaretPosition(View.Caret.Position);
        }
    }

    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)
    {
        UpdateAtCaretPosition(e.NewPosition);
    }
    ```

5. Außerdem müssen Sie ein- `TagsChanged` Ereignis hinzufügen, das von der Update-Methode aufgerufen wird.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. Die- `UpdateAtCaretPosition()` Methode sucht jedes Wort im Text Puffer, das mit dem Wort identisch ist, in dem der Cursor positioniert ist, und erstellt eine Liste von- <xref:Microsoft.VisualStudio.Text.SnapshotSpan> Objekten, die den Vorkommen des Worts entsprechen. Anschließend wird aufgerufen `SynchronousUpdate` , wodurch das- `TagsChanged` Ereignis ausgelöst wird.

    ```csharp
    void UpdateAtCaretPosition(CaretPosition caretPosition)
    {
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);

        if (!point.HasValue)
            return;

        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it 
        if (CurrentWord.HasValue
            && CurrentWord.Value.Snapshot == View.TextSnapshot
            && point.Value >= CurrentWord.Value.Start
            && point.Value <= CurrentWord.Value.End)
        {
            return;
        }

        RequestedPoint = point.Value;
        UpdateWordAdornments();
    }

    void UpdateWordAdornments()
    {
        SnapshotPoint currentRequest = RequestedPoint;
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();
        //Find all words in the buffer like the one the caret is on
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);
        bool foundWord = true;
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
        if (!WordExtentIsValid(currentRequest, word))
        {
            //Before we retry, make sure it is worthwhile 
            if (word.Span.Start != currentRequest
                 || currentRequest == currentRequest.GetContainingLine().Start
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))
            {
                foundWord = false;
            }
            else
            {
                // Try again, one character previous.  
                //If the caret is at the end of a word, pick up the word.
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);

                //If the word still isn't valid, we're done 
                if (!WordExtentIsValid(currentRequest, word))
                    foundWord = false;
            }
        }

        if (!foundWord)
        {
            //If we couldn't find a word, clear out the existing markers
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);
            return;
        }

        SnapshotSpan currentWord = word.Span;
        //If this is the current word, and the caret moved within a word, we're done. 
        if (CurrentWord.HasValue && currentWord == CurrentWord)
            return;

        //Find the new spans
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;

        wordSpans.AddRange(TextSearchService.FindAll(findData));

        //If another change hasn't happened, do a real update 
        if (currentRequest == RequestedPoint)
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);
    }
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. `SynchronousUpdate`Führt ein synchrones Update für die `WordSpans` Eigenschaften und aus und löst das-Ereignis aus `CurrentWord` `TagsChanged` .

    ```csharp
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)
    {
        lock (updateLock)
        {
            if (currentRequest != RequestedPoint)
                return;

            WordSpans = newSpans;
            CurrentWord = newCurrentWord;

            var tempEvent = TagsChanged;
            if (tempEvent != null)
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));
        }
    }
    ```

8. Sie müssen die- <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Methode implementieren. Diese Methode nimmt eine Auflistung von <xref:Microsoft.VisualStudio.Text.SnapshotSpan> -Objekten an und gibt eine Enumeration von tagspannen zurück.

     Implementieren Sie diese Methode in c# als Yield-Iterator, der eine verzögerte Auswertung ermöglicht (d. h. die Auswertung der Menge nur, wenn auf einzelne Elemente zugegriffen wird) der Tags. Fügen Sie in Visual Basic die Tags einer Liste hinzu, und geben Sie die Liste zurück.

     Hier gibt die Methode ein-Objekt zurück, <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> das über ein "blaues" verfügt <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> , das einen blauen Hintergrund bereitstellt.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot 
        if (spans[0].Snapshot != wordSpans[0].Snapshot)
        {
            wordSpans = new NormalizedSnapshotSpanCollection(
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));

            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);
        }

        // First, yield back the word the cursor is under (if it overlaps) 
        // Note that we'll yield back the same word again in the wordspans collection; 
        // the duplication here is expected. 
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>Erstellen eines Tagger-Anbieters
 Um einen Tagger zu erstellen, müssen Sie einen implementieren <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> . Bei dieser Klasse handelt es sich um einen MEF-Komponenten Teil, sodass Sie die richtigen Attribute festlegen müssen, damit diese Erweiterung erkannt wird.

> [!NOTE]
> Weitere Informationen zu MEF finden Sie unter [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-create-a-tagger-provider"></a>So erstellen Sie einen Tagger-Anbieter

1. Erstellen Sie eine Klasse mit dem Namen, `HighlightWordTaggerProvider` die implementiert <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , und exportieren Sie Sie mit <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" und einem <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. Sie müssen zwei Editor-Dienste, <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> und importieren <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , um das Tagger zu instanziieren.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> Methode, um eine Instanz von zurückzugeben `HighlightWordTagger` .

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die Projekt Mappe highlightwordtest, und führen Sie Sie in der experimentellen Instanz aus.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>So erstellen und testen Sie die Projekt Mappe "highlightwordtest"

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen Sie eine Textdatei, und geben Sie Text ein, in dem die Wörter wiederholt werden, z. b. "Hello Hello Hello".

4. Positionieren Sie den Cursor in einem der Vorkommen von "Hello". Jedes Vorkommen sollte blau hervorgehoben werden.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
