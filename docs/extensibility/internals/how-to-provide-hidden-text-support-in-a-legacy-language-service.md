---
title: Unterstützung für ausgeblendeten Text im Legacy Sprachdienst
description: Erfahren Sie, wie Sie eine ausgeblendete Textunterstützung in einem Legacy Sprachdienst bereitstellen, indem Sie Editor-gesteuerte oder Client gesteuerte ausgeblendete Textbereiche
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0c4951e1f3fbaf63bf0638965a7dee2db7be8830
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965251"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Gewusst wie: Bereitstellen von ausgeblendeter Textunterstützung in einem Legacy Sprachdienst
Sie können neben Gliederungs Bereiche auch ausgeblendete Textbereiche erstellen. Ausgeblendete Textbereiche können vom Client gesteuert oder Editor gesteuert werden, und Sie werden verwendet, um einen Textbereich vollständig auszublenden. Der Editor zeigt einen ausgeblendeten Bereich als horizontale Linien an. Ein Beispiel hierfür ist die **Nur Skript** Ansicht im HTML-Editor.

## <a name="to-implement-a-hidden-text-region"></a>So implementieren Sie einen ausgeblendeten Textbereich

1. Wird `QueryService` für aufgerufen <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> .

     Dies gibt einen Zeiger auf zurück <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Ruft <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> auf und übergibt einen Zeiger für einen angegebenen Text Puffer. Hiermit wird bestimmt, ob für den Puffer bereits eine ausgeblendete Text Sitzung vorhanden ist.

3. Wenn bereits eine vorhanden ist, müssen Sie keine erstellen, und es wird ein Zeiger auf das vorhandene <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Objekt zurückgegeben. Verwenden Sie diesen Zeiger, um ausgeblendete Textbereiche aufzulisten und zu erstellen. Andernfalls rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Sie auf, um eine ausgeblendete Text Sitzung für den Puffer zu erstellen.

     Ein Zeiger auf das- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Objekt wird zurückgegeben.

    > [!NOTE]
    > Wenn Sie aufgerufen `CreateHiddenTextSession` haben, können Sie einen ausgeblendeten Text Client angeben (d <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> . h.). Der verborgene Text Client benachrichtigt Sie, wenn ausgeblendeter Text oder Gliederung vom Benutzer erweitert oder reduziert wird.

4. Aufrufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> , um eine oder mehrere neue Gliederungs Bereiche gleichzeitig hinzuzufügen. dabei werden die folgenden Informationen im `reHidReg` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Parameter () angegeben:

    1. Geben `hrtConcealed` Sie den Wert im- `iType` Member der- <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Struktur an, um anzugeben, dass Sie einen ausgeblendeten Bereich anstelle eines Gliederungs Bereichs erstellen.

        > [!NOTE]
        > Wenn verborgene Bereiche ausgeblendet sind, zeigt der Editor automatisch Zeilen um die ausgeblendeten Bereiche an, um deren Anwesenheit anzuzeigen.

    2. Geben Sie an, ob der Bereich in den Elementen der Struktur vom Client gesteuert oder vom Editor gesteuert wird `dwBehavior` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> . Ihre intelligente Gliederungs Implementierung kann eine Mischung aus Editor-und Client gesteuerter Kontur und ausgeblendeten Textbereichen enthalten.
