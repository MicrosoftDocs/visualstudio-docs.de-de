---
title: Beibehalten des Fokus beim Durchlaufen der App | Microsoft-Dokumentation
Description: Verwenden von Remotedebuggen, um zu verhindern, dass das Programm den Fokus verliert, wenn Sie ein Fensteraktivierungsproblem debuggen.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.stepping
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], stepping
- focus, keeping
- stepping, focus
- windows, troubleshooting activation
ms.assetid: 11a30580-3a1a-4be8-a241-0abdc758302e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d533d524effe5ba055116d926d7cc5ba9632a6b
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398323"
---
# <a name="how-can-i-keep-focus-when-stepping-through-my-app"></a>Wie kann der Fokus beim Durchlaufen der App beibehalten werden?
## <a name="description"></a>Beschreibung
 Das Programm hat Probleme mit der Aktivierung von Fenstern. Beim Durchlaufen des Programms mit dem Debugger kann das Problem nicht reproduziert werden, da das Programm den Fokus verliert. Wie kann dies vermieden werden?

## <a name="solution"></a>Lösung
 Wenn Sie über einen zweiten Computer verfügen, verwenden Sie das Remotedebuggen. Sie können das Programm auf dem Remotecomputer verwenden, während der Debugger auf dem Host ausgeführt wird. Weitere Informationen finden Sie unter [Vorgehensweise: Auswählen eines Remotecomputers](/previous-versions/visualstudio/visual-studio-2010/w8wtw2f3(v=vs.100)).

## <a name="see-also"></a>Siehe auch
- [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)
- [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)