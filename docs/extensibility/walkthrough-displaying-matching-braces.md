---
title: 'Exemplarische Vorgehensweise: Anzeigen von passenden geschweiften Klammern | Microsoft-Dokumentation'
description: In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie geschweifte Klammern im Kontext einer Sprache definieren und entsprechende geschweifte Klammern auf den Text Inhaltstyp anwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce40f5673a8aba4ab3f7714a3aafdc3de4697cc4
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877948"
---
# <a name="walkthrough-display-matching-braces"></a>Exemplarische Vorgehensweise: anzeigen passender geschweifter Klammern
Implementieren Sie sprachbasierte Funktionen, wie z. b. die Klammer Zuordnung, indem Sie die geschweiften Klammern definieren, und fügen Sie den passenden geschweiften Klammern ein textmarkertag hinzu, wenn sich die Einfügemarke in einer der geschweiften Klammern befindet. Sie können geschweifte Klammern im Kontext einer Sprache definieren, eine eigene Dateinamenerweiterung und einen Inhaltstyp definieren und die Tags nur auf diesen Typ anwenden oder die Tags auf einen vorhandenen Inhaltstyp (z. b. "Text") anwenden. In der folgenden exemplarischen Vorgehensweise wird veranschaulicht, wie Sie mit dem Inhaltstyp "Text" übereinstimmende geschweifter Klammern anwenden.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Es ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Erstellen eines Managed Extensibility Framework-Projekts (MEF)

#### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt

1. Erstellen Sie ein Editorklassifiziererprojekt. Nennen Sie die Projektmappe `BraceMatchingTest`.

2. Fügen Sie dem Projekt eine Editor-Klassifizierungs Element Vorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

## <a name="implement-a-brace-matching-tagger"></a>Eine mit Tagger übereinstimmende geschweifter Klammer implementieren
 Wenn Sie einen Effekt hervorheben möchten, der der geschweifter Klammer ähnelt, der in Visual Studio verwendet wird, können Sie einen Tagger vom Typ implementieren <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . Der folgende Code zeigt, wie das Tagger für geschweifter Klammern auf einer beliebigen Schachtelungs Ebene definiert wird. In diesem Beispiel werden die geschweifter Klammer Paare von [] und {} im Tagger-Konstruktor definiert, aber in einer vollständigen sprach Implementierung würden die relevanten geschweifter Klammern in der Sprachspezifikation definiert werden.

### <a name="to-implement-a-brace-matching-tagger"></a>So implementieren Sie eine mit Tagger übereinstimmende Klammer

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie Sie "bracematching".

2. Importieren Sie die folgenden Namespaces.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Definieren Sie eine Klasse `BraceMatchingTagger` , die von vom Typ erbt <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Fügen Sie Eigenschaften für die Textansicht, den Quell Puffer, den aktuellen Momentaufnahme Punkt und auch einen Satz von geschweifter Klammern hinzu.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. Legen Sie im Tagger-Konstruktor die Eigenschaften fest, und abonnieren Sie die Sicht Änderungs Ereignisse <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> und <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . In diesem Beispiel werden die übereinstimmenden Paare zu Veranschaulichung auch im Konstruktor definiert.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. Deklarieren Sie als Teil der- <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Implementierung ein tagscheignis-Ereignis.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Die Ereignishandler aktualisieren die aktuelle Position der Einfügemarke der `CurrentChar` Eigenschaft und rufen das tagscheignis-Ereignis auf.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Methode, um geschweifte Klammern zu finden, wenn das aktuelle Zeichen eine öffnende geschweifte Klammer ist, oder wenn das vorherige Zeichen eine schließende geschweifte Klammer ist, wie in Visual Studio. Wenn die Entsprechung gefunden wird, instanziiert diese Methode zwei Tags, eine für die öffnende geschweifter Klammer und eine für die schließende Klammer.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Die folgenden privaten Methoden suchen nach der passenden geschweifter Klammer auf jeder Ebene der Schachtelung. Die erste Methode findet das schließende Zeichen, das mit dem geöffneten Zeichen übereinstimmt:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. Die folgende Hilfsmethode findet das geöffnete Zeichen, das mit einem Schließ Zeichen übereinstimmt:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Implementieren einer geschweifter Klammer zum Tagger-Anbieter
 Zusätzlich zum Implementieren eines Taggers müssen Sie auch einen Tagger-Anbieter implementieren und exportieren. In diesem Fall ist der Inhaltstyp des Anbieters "Text". Daher wird die Übereinstimmung mit Klammern in allen Textdateien angezeigt, aber eine umfassendere Implementierung wendet geschweifter Klammern nur auf einen bestimmten Inhaltstyp an.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>So implementieren Sie eine Klammer, die dem Tagger-Anbieter entspricht

1. Deklarieren Sie einen Tagger-Anbieter, der von erbt <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , nennen Sie ihn bracematchingtaggerprovider, und exportieren Sie ihn mit <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" und einem <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> Methode, um ein bracematchingtagger zu instanziieren.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die bracematchingtest-Projekt Mappe, und führen Sie Sie in der experimentellen Instanz aus.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>So erstellen und testen Sie die bracematchingtest-Projekt Mappe

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen Sie eine Textdatei, und geben Sie Text ein, der passende geschweifte Klammern enthält.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Wenn Sie die Einfügemarke vor einer öffnenden geschweifter Klammer positionieren, sollten diese geschweifter Klammer und die entsprechende schließende geschweifter Klammer hervorgehoben werden. Wenn Sie den Cursor direkt nach der schließenden geschweifter Klammer positionieren, sollten diese geschweifter Klammer und die entsprechende öffnende geschweifter Klammer hervorgehoben werden.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
