---
title: 'Exemplarische Vorgehensweise: Erstellen eines Rand Symbols | Microsoft-Dokumentation'
description: In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie die Darstellung von Editor-Rändern mithilfe von benutzerdefinierten Editor-Erweiterungen anpassen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a2a1857edb8032d12cd23da5e2686ad90f15b574
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892462"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Exemplarische Vorgehensweise: Erstellen eines Rand Symbols
Sie können die Darstellung der Editor Ränder anpassen, indem Sie benutzerdefinierte Editor-Erweiterungen verwenden. In dieser exemplarischen Vorgehensweise wird ein benutzerdefiniertes Symbol auf den Indikator Rand eingefügt, wenn das Wort "ToDo" in einem Code Kommentar angezeigt wird.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Es ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts

1. Erstellen Sie ein c#-VSIX-Projekt. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual c#/Erweiterbarkeit** und dann **VSIX-Projekt** aus.) Benennen Sie die Projekt Mappe `TodoGlyphTest` .

2. Fügen Sie ein Editor-Klassifizierungs Projekt Element hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

## <a name="define-the-glyph"></a>Definieren des Symbols
 Definieren Sie ein Symbol, indem Sie die- <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> Schnittstelle ausführen.

### <a name="to-define-the-glyph"></a>So definieren Sie das Symbol

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TodoGlyphFactory`.

2. Fügen Sie den folgenden Code mithilfe von Deklarationen hinzu.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. Fügen Sie eine Klasse mit dem Namen hinzu `TodoGlyphFactory` , die implementiert <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. Fügen Sie ein privates Feld hinzu, das die Dimensionen des Symbols definiert.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. Implementieren Sie, `GenerateGlyph` indem Sie das Glyphe-Benutzeroberflächen Element definieren. `TodoTag` wird später in dieser exemplarischen Vorgehensweise definiert.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. Fügen Sie eine Klasse mit dem Namen hinzu `TodoGlyphFactoryProvider` , die implementiert <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Exportieren Sie diese Klasse mit <xref:Microsoft.VisualStudio.Utilities.NameAttribute> der Zeichenfolge "", "", "" <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> nach "vstextmarker", <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" und "" <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von "dedotag".

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> Methode, indem Sie die instanziieren `TodoGlyphFactory` .

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Definieren eines ToDo-Tags und Taggers
 Definieren Sie die Beziehung zwischen dem Benutzeroberflächen Element, das Sie in den vorherigen Schritten definiert haben, und dem Indikator Rand. Erstellen Sie einen Tagtyp und einen Tagger, und exportieren Sie ihn mithilfe eines Tagger-Anbieters.

### <a name="to-define-a-todo-tag-and-tagger"></a>So definieren Sie ein TODO-Tag und einen Tagger

1. Fügen Sie dem Projekt eine neue Klassendatei hinzu, und benennen Sie Sie `TodoTagger` .

2. Fügen Sie die folgenden Importe hinzu.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. Fügen Sie eine Klasse namens `TodoTag`hinzu.

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. Ändern Sie die Klasse `TodoTagger` mit dem Namen, die <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> vom Typ implementiert `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. `TodoTagger`Fügen Sie der-Klasse private Felder für ein <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> und für den Text hinzu, der in den Klassifizierungs spannen gesucht werden soll.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. Fügen Sie einen Konstruktor hinzu, der den Klassifizierer festlegt.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Methode, indem Sie alle Klassifizierungs spannen ermitteln, deren Namen das Wort "comment" enthalten und dessen Text den Suchtext enthält. Wenn der Suchtext gefunden wird, wird ein neuer <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> des Typs zurückgeben `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. Deklarieren Sie ein- `TagsChanged` Ereignis.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. Fügen Sie eine Klasse mit dem Namen hinzu `TodoTaggerProvider` , die implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , und exportieren Sie Sie mit <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" und einem <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> von "dedotag".

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. Importieren Sie <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Methode, indem Sie die instanziieren `TodoTagger` .

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die Projekt Mappe "Projekt Mappe", und führen Sie Sie in der experimentellen Instanz aus.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>So erstellen und testen Sie die Projekt Mappe "tdoglyphtest"

1. Erstellen Sie die Projektmappe.

2. Führen Sie das Projekt aus, indem Sie **F5** drücken. Eine zweite Instanz von Visual Studio wird gestartet.

3. Stellen Sie sicher, dass der Indikator Rand angezeigt wird. (Klicken Sie **im Menü Extras** auf **Optionen**. Vergewissern Sie sich, dass auf der Seite **Text-Editor** die Option **Indikator Rand** ausgewählt ist.)

4. Öffnen Sie eine Codedatei, die Kommentare enthält. Fügen Sie einem der Kommentar Abschnitte das Wort "ToDo" hinzu.

5. Ein heller blauer Kreis mit einem dunkelblauen Umriss wird im Indikator Rand links neben dem Code Fenster angezeigt.
