---
title: Gemischter Code und fehlende Informationen im Fenster „Aufrufliste“
description: In Programmen im gemischten Modus (nativ und verwaltet) kann der Debugger nicht immer die gesamte Aufrufliste anzeigen. In diesem Artikel werden die möglichen Diskrepanzen vorgestellt, die auftreten können, wenn nativer Code verwalteten Code aufruft.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 793d60c9bc550b0f29ac48e50a95dab601750ad4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885104"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Gemischter Code und fehlende Daten im Fenster "Aufrufliste"
Da es zwischen den Aufruflisten von verwaltetem Code und systemeigenen Code Unterschiede gibt, kann der Debugger bei vermischten Codetypen nicht immer die vollständige Aufrufliste anzeigen. Wenn verwalteter Code durch nativen Code aufgerufen wird, sind im Fenster **Aufrufliste** unter Umständen folgende Abweichungen festzustellen:

- Es kann vorkommen, dass der native Rahmen direkt über dem verwalteten Code im Fenster **Aufrufliste** fehlt. Weitere Informationen finden Sie unter [Vorgehensweise: Ausführen von verwaltetem Code bis zum Rücksprung, wenn native Frames im Aufruflistenfenster fehlen](how-to-use-the-call-stack-window.md).

- Für außerhalb des Debuggers gestartete Anwendungen mit gemischtem Code wird im Fenster **Aufrufliste** unter Umständen keiner der nativen Rahmen, sondern nur der verwaltete Code angezeigt.

  Beide Fälle treten relativ selten ein. In den meisten Fällen, in denen verwalteter Code durch systemeigenen Code aufgerufen wird, werden die Aufruflisten richtig angezeigt.

## <a name="see-also"></a>Siehe auch
- [How to: Use the Call Stack Window (Vorgehensweise: Verwenden des Fensters Aufrufliste)](../debugger/how-to-use-the-call-stack-window.md)