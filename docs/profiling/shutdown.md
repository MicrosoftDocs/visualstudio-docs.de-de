---
title: Shutdown | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Option Shutdown. Diese wartet, bis ein aktuell geprofileter Prozess beendet oder getrennt wird. Anschließend schaltet sie den Profiler aus und schließt die Profilerstellungs-Datendatei.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 455278f7fccbc9e4f80ce4f11a167e5b433ca8ab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950038"
---
# <a name="shutdown"></a>Shutdown
Die Option **Shutdown** (Herunterfahren) wartet darauf, dass ein aktueller Profilerstellungsprozess beendet oder getrennt wird. Anschließend deaktiviert die Option die Profilerstellung und schließt die Profilerstellungs-Datendatei. Die **Shutdown**-Option muss der letzte Befehl einer Profilerstellung sein.

 Wenn kein Timeoutparameter angegeben ist, ist für die **Shutdown**-Option eine unbegrenzte Wartezeit festgelegt. Wenn ein Timeoutparameter angegeben ist, wird die Option nach der angegebenen Zeit in Sekunden zurückgegeben, ohne dass die Profilerstellung deaktiviert oder die Datendatei geschlossen wird.

 Die Option **Shutdown** darf als einzige Option in der Befehlszeile angegeben werden.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe /Shutdown[:Timeout]
```

#### <a name="parameters"></a>Parameter
`Timeout`
- (Optional) Die Option wird, wenn angegeben, nach der angegebenen Zeit in Sekunden zurückgegeben, ohne dass der Profiler deaktiviert oder die Profilerstellungs-Datendatei geschlossen wird.

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)
