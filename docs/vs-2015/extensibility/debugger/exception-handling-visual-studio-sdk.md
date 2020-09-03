---
title: Ausnahmebehandlung (Visual Studio SDK) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 38e646f032a12de48bbfb55b089462c7f8a4dd26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152792"
---
# <a name="exception-handling-visual-studio-sdk"></a>Ausnahmebehandlung (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden wird der Prozess beschrieben, der auftritt, wenn Ausnahmen ausgelöst werden.  
  
## <a name="exception-handling-process"></a>Ausnahme Behandlungsprozess  
  
1. Wenn eine Ausnahme zuerst ausgelöst wird, aber bevor Sie vom Ausnahmehandler im debuggten Programm behandelt wird, sendet die Debug-Engine (de) ein [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) als anhalteereignis an den Sitzungs-Debug-Manager (SDM). `IDebugExceptionEvent2`Wird gesendet, wenn nur die Einstellungen für die Ausnahme (die im Dialogfeld Ausnahmen im Debugpaket angegeben sind) angeben, dass der Benutzer bei Ausnahme Benachrichtigungen der ersten Chance angehalten werden soll.  
  
2. Der SDM ruft [IDebugExceptionEvent2:: GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) auf, um die Eigenschaft der Ausnahme zu erhalten.  
  
3. Das Debugpaket ruft [IDebugExceptionEvent2:: canpasstodebuggens](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) auf, um zu bestimmen, welche Optionen für den Benutzer vorhanden sind.  
  
4. Das Debugpaket fordert den Benutzer auf, die Ausnahme zu behandeln, indem das Dialogfeld "Ausnahme der ersten Chance" geöffnet wird.  
  
5. Wenn sich der Benutzer entscheidet, den Vorgang fortzusetzen, ruft der SDM [IDebugExceptionEvent2:: canpasstodebuggende](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)auf.  
  
    - Wenn die Methode S_OK zurückgibt, ruft die [IDebugExceptionEvent2::P asstodebuggende](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)auf.  
  
         - oder -  
  
         Wenn die Methode S_FALSE zurückgibt, erhält das Programm, das deentschlgt wird, eine zweite Möglichkeit, die Ausnahme zu behandeln.  
  
6. Wenn das Deaktivierung des Programms keinen Handler für eine Ausnahme der zweiten Chance hat, sendet de ein-an `IDebugExceptionEvent2` die SDM- **EVENT_SYNC_STOP**.  
  
7. Das Debugpaket fordert den Benutzer auf, die Ausnahme zu behandeln, indem das Dialogfeld "Ausnahme der ersten Chance" geöffnet wird.  
  
8. Das Debugpaket ruft [IDebugExceptionEvent2:: canpasstodebuggens](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) auf, um zu bestimmen, welche Optionen für den Benutzer vorhanden sind.  
  
9. Das Debugpaket fordert den Benutzer auf, die Ausnahme zu behandeln, indem er eine Ausnahme im Dialogfeld der zweiten Chance öffnet.  
  
10. Wenn die Methode S_OK zurückgibt, ruft auf `IDebugExceptionEvent2::PassToDebuggee` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
