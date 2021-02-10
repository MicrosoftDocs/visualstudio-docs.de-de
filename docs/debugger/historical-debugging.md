---
title: Verlaufsbezogenes Debuggen | Microsoft-Dokumentation
description: Problembehandlung einer App durch Untersuchen ihres Zustands, während Sie sich in ihrer Ausführung zurück und nach vorn bewegen. IntelliTrace erfasst die Informationen für diese Funktion.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c4a6bf07cc7905fc48bcc82c8b38fa5b6f6e7cfa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904419"
---
# <a name="historical-debugging-c-visual-basic-c"></a>Verlaufsbezogenes Debuggen (C#, Visual Basic, C++)

Das verlaufsbezogene Debuggen ist ein Debug-Modus, der von den durch IntelliTrace erfassten Informationen abhängig ist. Dadurch können Sie die Ausführung Ihrer Anwendung rückwärts und vorwärts durchlaufen und ihren Status überprüfen.

 Sie können IntelliTrace in der Visual Studio Enterprise Edition verwenden(jedoch nicht in der Professional oder Community Edition).

## <a name="why-use-historical-debugging"></a>Warum verlaufsbezogenes Debuggen?

 Das Festlegen von Haltepunkten zum Auffinden von Fehlern ist eher eine unsichere Angelegenheit. Sie legen einen Haltepunkt in der Nähe der Stelle im Code fest, an der Sie einen Fehler vermuten, führen dann die Anwendung im Debugger aus, hoffen, dass der Haltepunkt erreicht wird, und dass die Stelle, an der die Ausführung unterbrochen wurde, die Ursache des Fehlers aufdeckt. Wenn dies nicht der Fall ist, müssen Sie versuchen, einen Haltepunkt an anderer Stelle im Code festzulegen und den Debugger erneut auszuführen. Diese Testschritte müssen Sie so oft wiederholen, bis Sie das Problem gefunden haben.

 ![Festlegen eines Breakpoints](../debugger/media/breakpointprocesa.png "BreakpointProcesa")

 Mit IntelliTrace und dem verlaufsbezogenen Debugging können Sie Ihre Anwendung durchgehen und den Status überprüfen (Aufrufliste und lokale Variablen), ohne Haltepunkte festzulegen, den Debugvorgang neu zu starten und die Testschritte zu wiederholen. Dadurch sparen Sie viel Zeit, besonders wenn der Fehler sich tief in einem Testszenario verbirgt, das azum Ausführen viel Zeit erfordert.

## <a name="how-do-i-start-using-historical-debugging"></a>Wie beginne ich mit dem verlaufsbezogenen Debuggen?

IntelliTrace ist standardmäßig aktiviert. Sie müssen lediglich entscheiden, welche Ereignisse und Funktionsaufrufe für Sie von Interesse sind und ob Sie Momentaufnahmen des vollständigen Anwendungszustands anzeigen möchten. Weitere Informationen zum Definieren von Elementen, die Sie suchen möchten, finden Sie unter [IntelliTrace-Funktionen](../debugger/intellitrace-features.md). Die Funktionsunterstützung variiert je nach Sprache und App-Typ.

- Wenn Sie beim verlaufsbezogenes Debuggen Momentaufnahmen anzeigen möchten, finden Sie weitere Informationen unter [Untersuchen von vorherigen App-Zuständen mithilfe von IntelliTrace](../debugger/view-historical-application-state.md).
- Informationen zum Untersuchen von Variablen und Navigieren in Code finden Sie unter [Untersuchen der App mit verlaufsbezogenem Debuggen](../debugger/historical-debugging-inspect-app.md).
- Weitere Informationen zum Debuggen mit IntelliTrace-Ereignissen finden Sie unter [Exemplarische Vorgehensweise: Verwenden von IntelliTrace](../debugger/walkthrough-using-intellitrace.md).