---
title: Ausgabe | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur Option „Ausgabe“. Diese gibt den Namen der Profilerstellungsdatendatei für die Leistungssitzung an. Ausgabe muss zusammen mit der Option Start verwendet werden.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6067e13e33875be778ff59739f5511c4116937ed
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722801"
---
# <a name="output"></a>Output
Die Option **Ausgabe** gibt den Namen der Profilerstellungsdaten für die Leistungssitzung an. **Ausgabe** muss zusammen mit der Option **Start** verwendet werden.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parameter
 `FileName`: der Name der Datendatei. Es werden vollständige und partielle Pfade angenommen. Wenn kein Pfad angegeben ist, wird die Datei im aktuellen Verzeichnis erstellt.

## <a name="required-options"></a>Erforderliche Optionen
 Die Option **Ausgabe** muss zusammen mit der Option **Start** verwendet werden.

 **Start:** `Method` gibt den Ausgabedateinamen an.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Profilerstellungs-Datendatei im aktuellen Verzeichnis erstellt.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
```

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)
