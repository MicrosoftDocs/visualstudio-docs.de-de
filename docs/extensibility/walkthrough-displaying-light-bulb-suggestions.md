---
title: 'Exemplarische Vorgehensweise: Anzeigen von Glühbirnen Vorschlägen | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie eine Glühbirne im Visual Studio-Editor erstellen, die auf dem aktuellen Wort angezeigt wird und zwei Empfohlene Aktionen enthält, indem Sie diese exemplarische Vorgehensweise verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e1c906b96f3bd20b72cf2b5eca92190e0ad42916
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931291"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Exemplarische Vorgehensweise: Anzeigen von Glühbirnen Vorschlägen
Glühbirnen sind Symbole im Visual Studio-Editor, die erweitert werden, um eine Reihe von Aktionen anzuzeigen, z. b. Fehlerbehebungen für Probleme, die von den integrierten Code Analysemodulen oder der Code Umgestaltung identifiziert werden.

 In den Visual c#-und Visual Basic-Editoren können Sie auch die .NET Compiler Platform ("Roslyn") verwenden, um eigene Code Analysen mit Aktionen zu schreiben und zu verpacken, die automatisch Glühbirnen anzeigen. Weitere Informationen finden Sie unter

- [Gewusst wie: Schreiben einer c#-Diagnose und-Code Korrektur](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix.md)

- [Gewusst wie: Schreiben einer Visual Basic Diagnose und Code Korrektur](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix.md)

  Andere Sprachen, wie z. b. C++, stellen auch Glühbirnen für einige schnelle Aktionen bereit, wie z. b. einen Vorschlag, eine Stubimplementierung dieser Funktion zu erstellen.

  Eine Glühbirne sieht wie folgt aus: In einem Visual Basic-oder Visual c#-Projekt wird eine rote Wellenlinie unter einem Variablennamen angezeigt, wenn Sie ungültig ist. Wenn Sie den Mauszeiger über den ungültigen Bezeichner bewegen, wird eine Glühbirne in der Nähe des Cursors angezeigt.

  ![Glühbirne](../extensibility/media/lightbulb.png "LightBulb")

  Wenn Sie mit der Glühbirne auf den Pfeil nach unten klicken, wird eine Reihe von empfohlenen Aktionen zusammen mit einer Vorschau der ausgewählten Aktion angezeigt. In diesem Fall werden die Änderungen angezeigt, die an Ihrem Code vorgenommen werden, wenn Sie die Aktion ausführen.

  ![Vorschau für Glühbirne](../extensibility/media/lightbulbpreview.png "Lightbulbpreview")

  Sie können Glühbirnen verwenden, um Ihre eigenen empfohlenen Aktionen bereitzustellen. Beispielsweise können Sie Aktionen zum Verschieben von öffnenden geschweiften Klammern in eine neue Zeile oder zum Verschieben an das Ende der vorherigen Zeile bereitstellen. In der folgenden exemplarischen Vorgehensweise wird veranschaulicht, wie Sie eine Glühbirne erstellen, die auf dem aktuellen Wort angezeigt wird und zwei Empfohlene Aktionen hat: **Konvertieren in Großbuchstaben** und **Konvertieren in Kleinbuchstaben**.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Es ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Erstellen eines Managed Extensibility Framework-Projekts (MEF)

1. Erstellen Sie ein c#-VSIX-Projekt. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual c#/Erweiterbarkeit** und dann **VSIX-Projekt** aus.) Benennen Sie die Projekt Mappe `LightBulbTest` .

2. Fügen Sie dem Projekt eine **Editor-Klassifizierungs** Element Vorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

4. Fügen Sie den folgenden Verweis auf das Projekt hinzu, und legen Sie **lokale Kopie** auf fest `False` :

     *Microsoft.VisualStudio.Language.Intellisense*

5. Fügen Sie eine neue Klassendatei hinzu, und nennen Sie Sie " **lightbulbtest**".

6. Fügen Sie die folgenden using-Direktiven hinzu:

    ```csharp
    using System;
    using System.Linq;
    using System.Collections.Generic;
    using System.Threading.Tasks;
    using Microsoft.VisualStudio.Language.Intellisense;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Utilities;
    using System.ComponentModel.Composition;
    using System.Threading;

    ```

## <a name="implement-the-light-bulb-source-provider"></a>Implementieren des Glühbirnen-Quell Anbieters

1. Löschen Sie in der *LightBulbTest.cs* -Klassendatei die lightbulbtest-Klasse. Fügen Sie eine Klasse mit dem Namen " **testvorschlags stedactionssourceprovider** " hinzu, die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> . Exportieren Sie die Datei mit dem Namen der **vorgeschlagenen Aktionen** und <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> der Zeichenfolge "Text".

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. Importieren Sie in der Quell Anbieter Klasse das, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> und fügen Sie es als Eigenschaft hinzu.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Implementieren Sie die- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> Methode, um ein Objekt zurückzugeben <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> . Die Quelle wird im nächsten Abschnitt erläutert.

    ```csharp
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)
    {
        if (textBuffer == null || textView == null)
        {
            return null;
        }
        return new TestSuggestedActionsSource(this, textView, textBuffer);
    }
    ```

## <a name="implement-the-isuggestedactionsource"></a>Implementieren von ivorschlags stedactionsource
 Die vorgeschlagene Aktions Quelle ist dafür verantwortlich, den Satz der vorgeschlagenen Aktionen zu erfassen und im richtigen Kontext hinzuzufügen. In diesem Fall ist der Kontext das aktuelle Wort, und die vorgeschlagenen Aktionen sind **uppercasesuggestedaction** und **lowercasesuggestedaction**, die im folgenden Abschnitt erläutert werden.

1. Fügen Sie eine **testvorschlags stedactionssource** -Klasse hinzu, die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Fügen Sie private, schreibgeschützte Felder für den vorgeschlagenen Aktions Quellen Anbieter, den Text Puffer und die Textansicht hinzu.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. Fügen Sie einen Konstruktor hinzu, der die privaten Felder festlegt.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. Fügen Sie eine private Methode hinzu, die das Wort zurückgibt, das sich zurzeit unter dem Cursor befindet. Die folgende Methode untersucht die aktuelle Position des Cursors und fordert den Text Struktur Navigator für das Wort an. Wenn sich der Cursor auf einem Wort befindet, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> wird der im out-Parameter zurückgegeben. andernfalls `out` ist der `null` -Parameter, und die-Methode gibt zurück `false` .

    ```csharp
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)
    {
        ITextCaret caret = m_textView.Caret;
        SnapshotPoint point;

        if (caret.Position.BufferPosition > 0)
        {
            point = caret.Position.BufferPosition - 1;
        }
        else
        {
            wordExtent = default(TextExtent);
            return false;
        }

        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);

        wordExtent = navigator.GetExtentOfWord(point);
        return true;
    }
    ```

5. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>-Methode. Der Editor ruft diese Methode auf, um herauszufinden, ob die Glühbirne angezeigt werden soll. Dieser Aufruf wird häufig durchgeführt, z. b. wenn der Cursor von einer Zeile zu einer anderen bewegt wird oder wenn mit der Maus auf eine Fehler Wellenlinie gezeigt wird. Es ist asynchron, damit andere UI-Vorgänge durchgeführt werden können, während diese Methode funktioniert. In den meisten Fällen muss diese Methode eine Analyse und Analyse der aktuellen Zeile ausführen, sodass die Verarbeitung einige Zeit in Anspruch nehmen kann.

     In dieser Implementierung ruft Sie asynchron den <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> ab und bestimmt, ob der Block signifikant ist, wie in, ob er einen anderen Text als Leerraum hat.

    ```csharp
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)
    {
        return Task.Factory.StartNew(() =>
        {
            TextExtent extent;
            if (TryGetWordUnderCaret(out extent))
            {
                // don't display the action if the extent has whitespace
                return extent.IsSignificant;
              }
            return false;
        });
    }
    ```

6. Implementieren Sie die- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> Methode, die ein Array von-Objekten zurückgibt, die <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> die verschiedenen- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> Objekte enthalten. Diese Methode wird aufgerufen, wenn die Glühbirne erweitert wird.

    > [!WARNING]
    > Sie sollten sicherstellen, dass die Implementierungen von `HasSuggestedActionsAsync()` und `GetSuggestedActions()` konsistent sind, d. h., wenn `HasSuggestedActionsAsync()` zurückgibt `true` , `GetSuggestedActions()` sollten einige anzuzeigende Aktionen aufweisen. In vielen Fällen `HasSuggestedActionsAsync()` wird direkt vor aufgerufen `GetSuggestedActions()` , dies ist jedoch nicht immer der Fall. Wenn der Benutzer z. b. die Glühbirnen Aktionen durch Drücken von (**STRG +** .) aufruft, `GetSuggestedActions()` wird nur aufgerufen.

    ```csharp
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)
    {
        TextExtent extent;
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)
        {
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };
        }
        return Enumerable.Empty<SuggestedActionSet>();
    }
    ```

7. Definieren Sie ein- `SuggestedActionsChanged` Ereignis.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Um die Implementierung abzuschließen, fügen Sie Implementierungen für die `Dispose()` -Methode und die- `TryGetTelemetryId()` Methode hinzu. Sie möchten keine Telemetriedaten verwenden. Geben Sie daher einfach zurück, `false` und legen Sie die GUID auf fest `Empty` .

    ```csharp
    public void Dispose()
    {
    }

    public bool TryGetTelemetryId(out Guid telemetryId)
    {
        // This is a sample provider and doesn't participate in LightBulb telemetry
        telemetryId = Guid.Empty;
        return false;
    }
    ```

## <a name="implement-light-bulb-actions"></a>Implementieren von Glühbirnen Aktionen

1. Fügen Sie im Projekt einen Verweis auf *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* hinzu, und legen Sie **lokale Kopie** auf fest `False` .

2. Erstellen Sie zwei Klassen, die erste mit dem Namen `UpperCaseSuggestedAction` und die zweite mit dem Namen `LowerCaseSuggestedAction`. Beide Klassen implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Beide Klassen sind bis auf eine Ausnahme identisch: Die eine ruft <xref:System.String.ToUpper%2A> und die andere <xref:System.String.ToLower%2A> auf. In den folgenden Schritten wird nur die Klasse für die Umwandlung in Großbuchstaben behandelt; Sie müssen aber beide Klassen implementieren. Verwenden Sie diese Schritte als Muster für die Implementierung der Aktion zur Umwandlung in Kleinbuchstaben.

3. Fügen Sie die folgenden using-Direktiven für diese Klassen hinzu:

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4. Deklarieren Sie einen Satz privater Felder.

    ```csharp
    private ITrackingSpan m_span;
    private string m_upper;
    private string m_display;
    private ITextSnapshot m_snapshot;
    ```

5. Fügen Sie einen Konstruktor hinzu, der die Felder festlegt.

    ```csharp
    public UpperCaseSuggestedAction(ITrackingSpan span)
    {
        m_span = span;
        m_snapshot = span.TextBuffer.CurrentSnapshot;
        m_upper = span.GetText(m_snapshot).ToUpper();
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));
    }
    ```

6. Implementieren Sie die- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> Methode, sodass die Aktions Vorschau angezeigt wird.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Implementieren Sie die- <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> Methode, sodass Sie eine leere- <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> Enumeration zurückgibt.

    ```csharp
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)
    {
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);
    }
    ```

8. Implementieren Sie die Eigenschaften wie folgt:

    ```csharp
    public bool HasActionSets
    {
        get { return false; }
    }
    public string DisplayText
    {
        get { return m_display; }
    }
    public ImageMoniker IconMoniker
    {
       get { return default(ImageMoniker); }
    }
    public string IconAutomationText
    {
        get
        {
            return null;
        }
    }
    public string InputGestureText
    {
        get
        {
            return null;
        }
    }
    public bool HasPreview
    {
        get { return true; }
    }
    ```

9. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>-Methode, indem Sie den Text im Bereich durch entsprechende Großbuchstaben ersetzen.

    ```csharp
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > Die Methode zum **aufrufen** der Glühbirnen Aktion erwartet nicht, dass die Benutzeroberfläche angezeigt wird. Wenn Ihre Aktion eine neue Benutzeroberfläche (z. b. ein Vorschau-oder Auswahl Dialogfeld) aufruft, zeigen Sie die Benutzeroberfläche nicht direkt in der **Aufruf** Methode an, sondern planen Sie die Anzeige der Benutzeroberfläche **nach der Rückgabe** des Aufrufs.

10. Fügen Sie zum Durchführen der-Implementierung die `Dispose()` Methoden und hinzu `TryGetTelemetryId()` .

    ```csharp
    public void Dispose()
    {
    }

    public bool TryGetTelemetryId(out Guid telemetryId)
    {
        // This is a sample action and doesn't participate in LightBulb telemetry
        telemetryId = Guid.Empty;
        return false;
    }
    ```

11. Vergessen Sie nicht, das gleiche zu tun, wenn Sie `LowerCaseSuggestedAction` den Anzeige Text auf "konvertieren" {0} in Kleinbuchstaben und den Aufrufen <xref:System.String.ToUpper%2A> von ändern möchten <xref:System.String.ToLower%2A> .

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die lightbulbtest-Projekt Mappe, und führen Sie Sie in der experimentellen Instanz aus.

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen Sie eine Textdatei, und geben Sie Text ein. Links neben dem Text sollte eine Glühbirne angezeigt werden.

     ![Die Glühbirne testen](../extensibility/media/testlightbulb.png "Testlightbulb")

4. Zeigen Sie auf die Glühbirne. Ein Pfeil nach unten sollte angezeigt werden.

5. Wenn Sie auf die Glühbirne klicken, sollten zwei Empfohlene Aktionen sowie die Vorschau der ausgewählten Aktion angezeigt werden.

     ![Glühbirne testen, erweitert](../extensibility/media/testlightbulbexpanded.gif "Testlightbulbexpanded")

6. Wenn Sie auf die erste Aktion klicken, sollte der gesamte Text im aktuellen Wort in Großbuchstaben konvertiert werden. Wenn Sie auf die zweite Aktion klicken, sollte der gesamte Text in Kleinbuchstaben konvertiert werden.
