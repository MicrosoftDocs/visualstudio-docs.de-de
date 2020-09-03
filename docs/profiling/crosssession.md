---
title: CrossSession | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 019a7b74deb70176f214aefdcec4db86cec86829
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331164"
---
# <a name="crosssession"></a>CrossSession
Über die *VSPerfCmd.exe*-Option **CrossSession** kann der Profiler Daten aus jeder Konsolensitzung sammeln. Die Option **CrossSession** muss zusammen mit der Option **Start** verwendet werden.

 Anstelle von **CrossSession** können Sie die Abkürzung **CS** verwenden.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe /Start:Method /CrossSession [Options]
```

#### <a name="parameters"></a>Parameter
 Keine

## <a name="valid-options"></a>Gültige Optionen
 Um die Profilerstellung in einer anderen Sitzung zu aktivieren, muss die Option **CrossSession** mit der Option **Start** angegeben werden. **CrossSession** muss außerdem in allen nachfolgenden **VSPerfCmd Attach**- und **Detach**-Befehlen angegeben werden.

 **Start:** `Method`: Die Option **Start** initialisiert den Profiler mit der angegebenen Profilerstellungsmethode.

 **Attach:** _PID_[ **,** _PID_] startet die Profilerstellung für die angegebenen Prozesse.

 **Detach**[ **:** _PID_[,_PID_]] beendet die Profilerstellung für die angegebenen Prozesse.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird mit der Option **CrossSession** eine Anwendung angefügt, die in einer anderen Konsolensitzung gestartet wurde.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession
VSPerfCmd.exe /Attach:12345 /CS
```

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)
