---
title: Bereitstellen von Gliederungs Unterstützung in einem Sprachdienst | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie erweiterte Gliederungs Unterstützung in einem Legacy Sprachdienst bereitstellen, indem Sie durch den Editor gesteuerte Gliederungs Bereiche und Client gesteuerte Gliederungs Bereiche
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9397ff17ba80368a86ba03260b3c5af3759bfe8d
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761360"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Vorgehensweise: Bereitstellen erweiterter Gliederungs Unterstützung in einem Legacy Sprachdienst
Es gibt zwei Optionen für die Erweiterung der Gliederungs Unterstützung für Ihre Sprache über die Unterstützung des Befehls Reduzierungs **Definitionen** . Sie können vom Editor gesteuerte Gliederungs Bereiche hinzufügen und Client gesteuerte Gliederungs Bereiche hinzufügen.

## <a name="adding-editor-controlled-outline-regions"></a>Hinzufügen von durch Editor kontrollierten Gliederungs Bereichen
 Verwenden Sie diese Vorgehensweise, um einen Gliederungs Bereich zu erstellen und dem Editor zu ermöglichen, zu behandeln, ob der Bereich erweitert, reduziert usw. ist. Mit den beiden Optionen zum Bereitstellen von Gliederungs Unterstützung ist diese Option die geringste Stabilität. Bei dieser Option erstellen Sie mithilfe von einen neuen Gliederungs Bereich für einen angegebenen Textabschnitt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> . Nachdem dieser Bereich erstellt wurde, wird sein Verhalten vom Editor gesteuert. Verwenden Sie das folgende Verfahren, um durch Editor gesteuerte Gliederungs Bereiche zu implementieren.

### <a name="to-implement-an-editor-controlled-outline-region"></a>So implementieren Sie einen vom Editor kontrollierten Gliederungs Bereich

1. Aufrufe `QueryService` für <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Dies gibt einen Zeiger auf zurück <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Ruft <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> auf und übergibt einen Zeiger für einen angegebenen Text Puffer. Dadurch wird ein Zeiger auf das- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Objekt für den Puffer zurückgegeben.

3. Ruft <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> für einen Zeiger auf auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> .

4. Ruft auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> , um eine oder mehrere neue Gliederungs Bereiche gleichzeitig hinzuzufügen.

     Diese Methode ermöglicht es Ihnen, den Textbereich anzugeben, der dargestellt werden soll, ob vorhandene Gliederungs Bereiche entfernt oder beibehalten werden und ob der Gliederungs Bereich standardmäßig erweitert oder reduziert wird.

## <a name="add-client-controlled-outline-regions"></a>Client gesteuerte Gliederungs Bereiche hinzufügen
 Verwenden Sie diesen Ansatz, um eine Client gesteuerte (oder intelligente) Gliederung zu implementieren, die von den [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Sprachdiensten und verwendet wird [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . Ein Sprachdienst, der seine eigene Gliederung verwaltet, überwacht den Text Pufferinhalt, um alte Gliederungs Bereiche zu zerstören, wenn Sie ungültig werden, und um nach Bedarf neue Gliederungs Bereiche zu erstellen.

### <a name="to-implement-a-client-controlled-outline-region"></a>So implementieren Sie einen Client gesteuerten Gliederungs Bereich

1. Wird `QueryService` für aufgerufen <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> . Dies gibt einen Zeiger auf zurück <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Ruft <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> auf und übergibt einen Zeiger für einen angegebenen Text Puffer. Hiermit wird bestimmt, ob für den Puffer bereits eine ausgeblendete Text Sitzung vorhanden ist.

3. Wenn bereits eine Text Sitzung vorhanden ist, müssen Sie keine erstellen, und es wird ein Zeiger auf das vorhandene <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Objekt zurückgegeben. Verwenden Sie diesen Zeiger, um Gliederungs Bereiche aufzulisten und zu erstellen. Andernfalls rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Sie auf, um eine ausgeblendete Text Sitzung für den Puffer zu erstellen. Ein Zeiger auf das- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Objekt wird zurückgegeben.

    > [!NOTE]
    > Wenn Sie aufgerufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> haben, können Sie einen ausgeblendeten Text Client angeben (d. h. ein- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> Objekt). Dieser Client benachrichtigt Sie, wenn ein ausgeblendeter Text-oder Gliederungs Bereich vom Benutzer erweitert oder reduziert wird.

4. Parameter aufrufen- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> Struktur): geben <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> Sie den Wert im- `iType` Member der- <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Struktur an, um anzugeben, dass Sie einen Gliederungs Bereich anstelle eines ausgeblendeten Bereichs erstellen. Geben Sie an, ob der Bereich im-Member der-Struktur vom Client gesteuert oder vom Editor gesteuert wird `dwBehavior` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> . Ihre intelligente Gliederungs Implementierung kann eine Mischung aus Editor-und Client gesteuerten Gliederungs Bereichen enthalten. Geben Sie den Banner Text an, der angezeigt wird, wenn Ihr Gliederungs Bereich reduziert wird, z. b. "...", im- `pszBanner` Member der- <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Struktur. Der Standard Banner Text des Editors für einen ausgeblendeten Bereich ist "...".
