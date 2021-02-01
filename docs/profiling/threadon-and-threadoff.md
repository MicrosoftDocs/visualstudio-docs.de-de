---
title: ThreadOn und ThreadOff | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Unterbefehle ThreadOff und ThreadOn von VSPerfCmd.exe, die nur in Profilerstellungssitzungen in der Befehlszeile verfügbar sind, bei denen die Instrumentierungsmethode verwendet wird.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f8b2e51857fc799c7b60f7650b823b77c9c6a283
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718771"
---
# <a name="threadon-and-threadoff"></a>ThreadOn und ThreadOff
Die *VSPerfCmd.exe-Unterbefehle* **ThreadOff** und **ThreadOn** sind nur in Befehlszeilensitzungen zur Profilerstellung verfügbar, in denen die Instrumentierungsmethode verwendet wird. **ThreadOff** und **ThreadOn** halten die Profilerstellung für den angegebenen Thread an oder setzen diese fort. **ThreadOff** hält die Profilerstellung für den Thread an, und **ThreadOn** setzt diese fort.

 In den meisten Fällen geben Sie **ThreadOn** oder **ThreadOff** als einzige Option in einer *VSPerfCmd.exe*-Befehlszeile an. Sie können aber auch mit den Unterbefehlen **GlobalOn**, **GlobalOff**, **ProcessOn** und **ProcessOff** kombiniert werden.

 Die Unterbefehle **ThreadOn** und **ThreadOff** interagieren mit den Unterbefehlen **GlobalOn** und **GlobalOff**, die die Datensammlung für alle Prozesse in einer Befehlszeilen-Profilerstellungssitzung steuern. Sie interagieren außerdem mit den Unterbefehlen **ProcessOn** und **ProcessOff**, die die Datensammlung für einen angegebenen Thread steuern.

 Die Unterbefehle **ThreadOff** und **ThreadOn** haben außerdem Auswirkungen auf die Start/Stop-Zähler von Threads, die von den Profiler-API-Funktionen bearbeitet wird.

- **ThreadOff** legt die globale Start/Stop-Zähler der Threads sofort auf 0 (null) fest und hält die Profilerstellung daher an.

- **ThreadOn** legt die globale Start/Stop-Zähler sofort auf 1 fest und setzt die Profilerstellung daher fort.

  Weitere Informationen finden Sie unter [APIs für Profilerstellungstools](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]

```

#### <a name="parameters"></a>Parameter
 `TID`: der ganzzahlige Bezeichner des Threads zum Starten oder Beenden.

## <a name="valid-options"></a>Gültige Optionen
 **ThreadOn** und **ThreadOff** können in Befehlszeilen angegeben werden, die auch die folgenden Unterbefehle enthalten.

 **Start:** `Method` initialisiert die Profilerstellungssitzung in der Befehlszeile und legt die angegebene Profilerstellungsmethode fest.

 **GlobalOff**&#124;**GlobalOn** beendet oder startet die Profilerstellung für alle Prozesse in einer Befehlszeilen-Profilerstellungssitzung.

 {**ProcessOff**|**ProcessOn**} **:** `TID` Beendet oder startet die Profilerstellung für den angegebenen Prozess

## <a name="example"></a>Beispiel
 In diesem Beispiel wird der Unterbefehl **ThreadOff** verwendet, um das Erfassen der Profilerstellungsdaten anzuhalten, damit nur Daten zum Starten von Anwendungen erfasst werden.

```cmd
; Initialize the profiler.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp
; Start the instrumented application.
; Stop profiling the thread after startup.
VSPerfCmd.exe /ThreadOff:12345
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)
