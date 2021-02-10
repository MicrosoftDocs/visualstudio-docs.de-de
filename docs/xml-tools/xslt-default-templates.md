---
title: XSLT-Standardvorlagen
description: In diesem Artikel lernen Sie die XSLT-Standardvorlagen kennen, die während der XSLT-Verarbeitung verwendet werden, wenn keine übereinstimmende explizite Vorlagenregel im Stylesheet enthalten ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 74b4cfebc7a6160577f1e817c9171f2eae69533c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874755"
---
# <a name="xslt-default-templates"></a>XSLT-Standardvorlagen

Eine Standardvorlage wird bei der XSLT-Verarbeitung verwendet, wenn im Stylesheet keine passende explizite Vorlagenregel vorhanden ist. Die Standardvorlage (oder integrierte Vorlagenregel) wird in Abschnitt 5.8 der W3C XSLT 1.0 Recommendation definiert. Mithilfe der Standardvorlage kann der XSLT-Prozessor einen Knoten verarbeiten, auch wenn keine passende Vorlagenregel explizit angegeben wurde. Da die integrierte Vorlagenregel nicht explizit im Stylesheet definiert ist, kann dies jedoch zu unerwarteten oder widersprüchlichen Ergebnissen bei der XSL-Transformation führen.

Der XSLT-Debugger zeigt jetzt den Code von XSLT-Standardvorlagen an. Bei den einzelnen Schritten einer XSL-Transformation zeigt der Debugger, sofern eine Standardvorlage verwendet wird, diese in einem Fenster an. Dadurch können der Code der Standardvorlage schrittweise ausgeführt werden und Haltepunkte für dessen Anweisungen festgelegt werden.

## <a name="see-also"></a>Siehe auch

- [Debuggen von XSLT](../xml-tools/debugging-xslt.md)
