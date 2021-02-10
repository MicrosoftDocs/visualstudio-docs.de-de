---
title: Console | Microsoft-Dokumentation
description: Verwenden Sie die VSPerfCmd.exe-Option „Console“, um die angegebene Anwendung in einem neuen Eingabeaufforderungsfenster zu starten. Sie müssen diese Option zusammen mit der Option „Launch“ verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 242a5234c2b7368a992676e12ecbdcd5ea36219f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955410"
---
# <a name="console"></a>Konsole
Die VSPerfCmd.exe-Option **Console** startet die angegebene Anwendung in einem neuen Eingabeaufforderungsfenster. **Console** kann nur mit der VSPerfCmd-Option **Launch** verwendet werden. Wenn die Anwendung keine Befehlszeilenanwendung ist, hat **Console** keine Auswirkungen.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parameter
 Keine

## <a name="required-options"></a>Erforderliche Optionen
 **Console** kann nur in einer Befehlszeile angegeben werden, die auch die Option **Launch** enthält.

 **Launch:** `AppName` startet den Profiler und die von `AppName` festgelegte Anwendung.

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)
