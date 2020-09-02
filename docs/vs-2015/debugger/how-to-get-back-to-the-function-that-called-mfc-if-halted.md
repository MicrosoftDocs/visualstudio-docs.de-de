---
title: 'Gewusst wie: zurückkehren zur Funktion, die MFC aufgerufen hat, wenn angehalten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c19cbf6e892ba8b35f2b92ad9b86aa0b74a64810
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685882"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Vorgehensweise: Zurückkehren zur Funktion, die MFC aufgerufen hat, wenn angehalten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

HINWEIS]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Wenn Sie zum Anhalten des Programms im Menü **Debuggen** den Befehl **Unterbrechen** verwendet haben, sich jetzt in MFC befinden und sicher sind, dass das Problem in Ihrem Code liegt, können Sie mithilfe des Fensters „Aufrufliste“ zu Ihrer Funktion zurücknavigieren. Weitere Informationen finden Sie unter [Vorgehensweise: Use the Call Stack Window (Vorgehensweise: Verwenden des Fensters Aufrufliste)](../debugger/how-to-use-the-call-stack-window.md).  
  
 Manchmal wird der Code in der Meldungsverteilschleife unterbrochen. In diesem Fall ist kein Benutzercode in der Aufrufliste vorhanden. Um diesen Fehler zu vermeiden, können Haltepunkte (möglicherweise mit Bedingungen und Trefferanzahl) anstelle des Befehls **Unterbrechen** verwendet werden. Weitere Informationen finden Sie unter [Breakpoints and Tracepoints](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>So navigieren Sie zu der Funktion, von der MFC aufgerufen wurde  
  
- Verwenden Sie das Fenster **Aufrufliste**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Häufig gestellte Fragen zum Debuggen](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)
