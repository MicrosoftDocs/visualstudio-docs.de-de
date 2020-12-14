---
title: Fortsetzen der Ausführung nach einer Ausnahme | Microsoft-Dokumentation
description: Hier erfahren Sie, was passiert, wenn der Debugger die Ausführung wegen eines Ausnahmefehlers unterbricht. Möglicherweise können Sie die Ausführung im selben Thread fortsetzen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7475dff2618a1dfcce598f35b57dbe67d80d254
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559380"
---
# <a name="continuing-execution-after-an-exception"></a>Fortfahren mit der Ausführung nach einer Ausnahme
Wenn der Debugger die Ausführung aufgrund einer Ausnahme unterbricht, wird standardmäßig die **Ausnahme-Hilfe** angezeigt. Wenn Sie die **Ausnahme-Hilfe** im Dialogfeld **Optionen** deaktiviert haben, wird der **Ausnahmen-Assistant** (C# oder Visual Basic) oder das Dialogfeld **Ausnahme** (C++) angezeigt.

 Wird das **Ausnahme-Hilfe** angezeigt, können Sie versuchen, das Problem zu beheben, das die Ausnahme verursacht hat.

## <a name="managed-and-native-code"></a>Verwalteter und nativer Code
 In verwaltetem und nativem Code kann die Ausführung nach einem Ausnahmefehler im gleichen Thread fortgesetzt werden. Die **Ausnahmen-Hilfe** entlädt die Aufrufliste bis an den Punkt, an dem die Ausnahme ausgelöst wurde.

## <a name="mixed-code"></a>Gemischter Code
 Wenn beim Debuggen gemischten Codes (systemeigener und verwalteter Code) ein Ausnahmefehler auftritt, verhindern Einschränkungen des Betriebssystems das Entladen der Aufrufliste. Sollten Sie versuchen, die Aufrufliste über das Kontextmenü neu zu laden, erhalten Sie die Fehlermeldung, dass der Debugger beim Debuggen von gemischtem Code keine Entladung aus einer unbehandelten Ausnahme vornehmen kann.

## <a name="see-also"></a>Siehe auch

- [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)