---
title: Dialogfeld „Beim Erreichen eines Haltepunktes“ | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie das Dialogfeld „Beim Erreichen eines Haltepunktes“ verwenden, um eine Aktion festzulegen, die ausgeführt wird, wenn ein Breakpoint erreicht wird. Sie können beispielsweise festlegen, dass eine Meldung ausgegeben werden soll und die Ausführung anschließend fortgesetzt werden soll.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a528709769f599219a7b3df2b8157b0ee3a605b1
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149312"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Dialogfeld "Beim Erreichen eines Haltepunktes"
In diesem Dialogfeld können Sie die Aktion anpassen, die beim Erreichen eines Haltepunkts ausgeführt wird.

## <a name="uielement-list"></a>UIElement-Liste
 **Meldung drucken** druckt eine Meldung mithilfe der DebuggerDisplay-Syntax. Weitere Informationen finden Sie unter [Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md).

 Dieses Textfeld unterstützt auch spezielle Schlüsselwörter (z. B. $ADDRESS), die alleine oder innerhalb der geschweiften Klammern eines DebuggerDisplay-Ausdrucks verwendet werden können. Die verfügbaren Schlüsselwörter werden im Dialogfeld aufgelistet.

 Das Steuerelement **Ausführung fortsetzen** ist nur aktiviert, wenn **Meldung drucken** ausgewählt ist. Durch Auswählen dieses Steuerelements können Sie einen Haltepunkt als Ablaufverfolgungspunkt verwenden, um die Programmausführung zu verfolgen, statt beim Erreichen des Haltepunkts zu unterbrechen.

## <a name="see-also"></a>Siehe auch
- [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)
- [Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)