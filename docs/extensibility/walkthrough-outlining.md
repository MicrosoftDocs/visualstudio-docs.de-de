---
title: 'Exemplarische Vorgehensweise: Gliederung | Microsoft-Dokumentation'
description: Erfahren Sie, wie Gliederungs Bereiche im Kontext eines sprach diensdienstanens oder ihrer eigenen Dateinamenerweiterung und ihres Inhaltstyps definiert und angezeigt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: aa66d3b32f6992cb3a5db13bc2b7ee4d5cd9294c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951185"
---
# <a name="walkthrough-outlining"></a>Exemplarische Vorgehensweise: Gliedern
Richten Sie sprachbasierte Funktionen wie Gliederung ein, indem Sie die Arten von Textbereichen definieren, die Sie erweitern oder reduzieren möchten. Sie können Bereiche im Kontext eines sprach diensdienstanbieter definieren oder eigene Dateinamen Erweiterungen und Inhaltstyp definieren und die Regions Definition nur auf diesen Typ anwenden oder die Regions Definitionen auf einen vorhandenen Inhaltstyp (z. b. "Text") anwenden. Diese exemplarische Vorgehensweise zeigt, wie Gliederungs Bereiche definiert und angezeigt werden.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Es ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Erstellen eines Managed Extensibility Framework-Projekts (MEF)

### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt

1. Erstellen eines VSIX-Projekts Nennen Sie die Projektmappe `OutlineRegionTest`.

2. Fügen Sie dem Projekt eine Editor-Klassifizierungs Element Vorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

## <a name="implement-an-outlining-tagger"></a>Implementieren eines Gliederungs Tags
 Gliederungs Bereiche werden durch eine Art von Tag ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ) markiert. Dieses Tag stellt das standardmäßige Gliederungs Verhalten bereit. Der dargestellte Bereich kann erweitert oder reduziert werden. Der dargestellte Bereich wird durch ein Plus Zeichen ( **+** ) gekennzeichnet, wenn er reduziert ist, oder ein Minus Zeichen ( **-** ), wenn er erweitert wird, und der erweiterte Bereich wird durch eine vertikale Linie abgegrenzt.

 In den folgenden Schritten wird gezeigt, wie ein Tagger definiert wird, der Gliederungs Bereiche für alle Regionen erstellt, die durch die Klammern (**[**,**]**) getrennt sind.

### <a name="to-implement-an-outlining-tagger"></a>So implementieren Sie einen Gliederungs Tagger

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `OutliningTagger`.

2. Importieren Sie die folgenden Namespaces.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Erstellen Sie eine Klasse mit dem Namen `OutliningTagger` , und implementieren Sie Folgendes <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Fügen Sie einige Felder hinzu, um den Text Puffer und die Momentaufnahme zu verfolgen und die Zeilen Sätze zu sammeln, die als Gliederungs Bereiche markiert werden sollen. Dieser Code enthält eine Liste von Regions Objekten (die später definiert werden müssen), die die Gliederungs Bereiche darstellen.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Fügen Sie einen Tagger-Konstruktor hinzu, der die Felder initialisiert, den Puffer analysiert und dem Ereignis einen Ereignishandler hinzufügt <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Methode, die die tagspannen instanziiert. In diesem Beispiel wird davon ausgegangen, dass die Spannen in der, die <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> an die-Methode geleitet werden, zusammenhängend sind, obwohl dies möglicherweise nicht immer der Fall ist. Diese Methode instanziiert eine neue tagspanne für jeden der Gliederungs Bereiche.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Deklarieren Sie einen- `TagsChanged` Ereignishandler.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Fügen Sie einen `BufferChanged` Ereignishandler hinzu, <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> der auf Ereignisse reagiert, indem Sie den Text Puffer auswerten.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Fügen Sie eine Methode hinzu, die den Puffer analysiert. Das hier angegebene Beispiel dient nur der Veranschaulichung. Sie analysiert den Puffer synchron in geschsted Gliederungs Bereiche.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. Die folgende Hilfsmethode Ruft eine Ganzzahl ab, die die Ebene der Gliederung darstellt, sodass 1 das äußteste linke Klammer Paar ist.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. Mit der folgenden Hilfsmethode wird ein (später in diesem Artikel definiertes) Bereich in eine snapshotspan übersetzt.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. Der folgende Code dient nur der Veranschaulichung. Es definiert eine partialregion-Klasse, die die Zeilennummer und den Offset des Starts eines Gliederungs Bereichs sowie einen Verweis auf den übergeordneten Bereich (sofern vorhanden) enthält. Dieser Code ermöglicht es dem Parser, eingefügte Gliederungs Bereiche einzurichten. Eine abgeleitete Regions Klasse enthält einen Verweis auf die Zeilennummer des Endes eines Gliederungs Bereichs.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Implementieren eines Tagger-Anbieters
 Exportieren Sie einen Tagger-Anbieter für Ihr tagger. Der Tagger-Anbieter erstellt einen `OutliningTagger` für einen Puffer mit dem Inhaltstyp "Text" oder gibt einen zurück, `OutliningTagger` Wenn der Puffer bereits einen besitzt.

### <a name="to-implement-a-tagger-provider"></a>So implementieren Sie einen Tagger-Anbieter

1. Erstellen Sie eine Klasse `OutliningTaggerProvider` mit dem Namen, die implementiert <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , und exportieren Sie Sie mit den Attributen ContentType und TagType.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Methode `OutliningTagger` , indem Sie eine zu den Eigenschaften des Puffers hinzufügen.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die Projekt Mappe "outlineregiontest", und führen Sie Sie in der experimentellen Instanz aus.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>So erstellen und testen Sie die Projekt Mappe "outlineregiontest"

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen einer Textdatei Geben Sie Text ein, der die öffnenden und schließenden Klammern enthält.

    ```
    [
       Hello
    ]
    ```

4. Es sollte ein Gliederungs Bereich vorhanden sein, der beide eckige Klammern enthält. Sie sollten in der Lage sein, auf das Minus Zeichen links neben der öffnenden eckige Klammer zu klicken, um den Gliederungs Bereich zu reduzieren. Wenn der Bereich reduziert ist, sollte das Symbol mit den Auslassungs Zeichen (*...*) links neben dem reduzierten Bereich angezeigt werden, und es sollte ein Popup Fenster angezeigt werden, das den Text für den **Maus** Zeiger enthält, wenn Sie den Mauszeiger auf die Auslassungs Zeichen bewegen.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
