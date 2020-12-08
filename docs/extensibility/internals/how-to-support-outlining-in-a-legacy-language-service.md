---
title: 'Gewusst wie: unterstützen von Gliederung in einem Legacy Sprachdienst | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie Unterstützung für das gliedern, erweitern oder reduzieren verschiedener Textbereiche in einem Legacy Sprachdienst bereitstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c9d1d7b7a74b6565c666e4d5e3293caaef3c7732
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761321"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Gewusst wie: unterstützen von Gliederung in einem Legacy Sprachdienst
Gliederung wird zum Erweitern oder reduzieren verschiedener Textbereiche verwendet. Die Verwendung der Gliederung kann in verschiedenen Sprachen unterschiedlich definiert werden. Weitere Informationen finden Sie unter [Gliedern](../../ide/outlining.md).

 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen zur neuen Methode zum Implementieren von Gliederung finden Sie unter Exemplarische Vorgehensweise [:](../../extensibility/walkthrough-outlining.md)Gliederung.

> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.

 Im folgenden wird veranschaulicht, wie dieser Befehl für Ihren Sprachdienst unterstützt wird.

## <a name="to-support-outlining"></a>Unterstützung der Gliederung

1. Implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> Sie für Ihr Sprachdienst Objekt.

2. Ruft <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> das aktuelle Gliederungs Sitzungs Objekt auf, um neue Gliederungs Bereiche hinzuzufügen.

## <a name="robust-programming"></a>Stabile Programmierung
 Wenn ein Benutzer im Gliederungs **Menü** **auf Definitionen** reduzieren klickt, ruft die IDE den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> Sprachdienst auf.

 Wenn diese Methode aufgerufen wird, übergibt die IDE einen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> Zeiger (einen Zeiger auf einen Text Puffer) und einen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (einen Zeiger auf die aktuelle Gliederungs Sitzung).

 Sie können die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> Methode für mehrere Gliederungs Bereiche aufrufen, indem Sie diese Bereiche im- `rgOutlnReg` Parameter angeben. Der- `rgOutlnReg` Parameter ist eine- <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> Struktur. Mit diesem Prozess können Sie verschiedene Eigenschaften des ausgeblendeten Bereichs angeben, z. b. ob eine bestimmte Region erweitert oder reduziert wird.

> [!NOTE]
> Gehen Sie vorsichtig vor, wenn Sie neue Zeilen ausblenden. Ausgeblendeter Text sollte vom Anfang der ersten Zeile bis zum letzten Zeichen der letzten Zeile in einem Abschnitt erweitert werden, sodass das abschließende Zeichen für die neue Zeile sichtbar bleibt.

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Bereitstellen von ausgeblendeter Textunterstützung in einem Legacy Sprachdienst](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Vorgehensweise: Bereitstellen erweiterter Gliederungs Unterstützung in einem Legacy Sprachdienst](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
