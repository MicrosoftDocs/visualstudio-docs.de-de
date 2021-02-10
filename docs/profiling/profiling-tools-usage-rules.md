---
title: Verwendungsregeln für Profilerstellungstools | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zu Leistungsregeln in der Nutzungskategorie der Profilerstellungstools. Diese bieten eine Anleitung für die Verwendung des Profiler zur effektivsten Datensammlung.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2514d6893c205a1c48c76983c859528be6ad938b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861620"
---
# <a name="profiling-tools-usage-rules"></a>Verwendungsregeln für Profilerstellungstools
Leistungsregeln in der Kategorie Verwendung der Profilerstellungstools bieten eine Anleitung für die Verwendung des Profiler zur effektivsten Datensammlung.

| Regel | Beschreibung |
| - | - |
| [DA0002: „VSPerfCorProf.dll“ fehlt](../profiling/da0002-vsperfcorprof-dll-is-missing.md) | Die Profilerstellung über die Befehlszeile enthält möglicherweise unvollständige Daten für .NET Framework-Binärdateien. Dies ist möglicherweise auf die inkorrekte Einstellung der Umgebungsvariablen zurückzuführen. |
| [DA0003: Zahlreiche Kernelbeispiele](../profiling/da0003-many-kernel-samples.md) | Viele Profilerstellungsbeispiele, die außerhalb der Ausführung der Zielbinärdatei aufgetreten sind, wurden aufgezeichnet. Um genauere Daten zu sammeln, sollten Sie die Instrumentationsmethode verwenden. |
| [DA0004: Hohe Prozessorauslastung](../profiling/da0004-high-processor-usage.md) | Die Profilerstellungsdaten lassen vermuten, dass Ihre Prozessoren während der Profilerstellung durchgängig ausgelastet waren. Um genauere Daten zu sammeln, sollten Sie die Samplingmethode verwenden. |
| [DA0008: Es wurden nur wenige Beispiele aufgelistet](../profiling/da0008-few-samples-collected.md) | Die Anzahl der bei der Profilerstellungsausführung erfassten Beispiele war nicht hoch genug, um statistisch signifikant zu sein. Sie sollten möglicherweise erneut ein Profil erstellen und die Anwendung für einen längeren Zeitraum ausführen. Sie können auch die Instrumentationsmethode verwenden, um Daten zu sammeln. |
| [DA0026: Übermäßige CPU-Zeit für die Kernelverarbeitung](../profiling/da0026-excessive-kernel-cpu-time-processing.md) | Ein längerer Zeitraum der Profilerstellungsausführung trat im Prozessorkernelmodus auf. Erwägen Sie Sampling, indem Sie Systemaufrufe anstatt Zeit als Kennzahl verwenden. |
| [DA0029: Nicht unterstützte CLR-Version](../profiling/da0029-unsupported-clr-version.md) | Die profilierte Binärdatei verwendet eine .NET Framework-Version, die nicht vom Profiler unterstützt wird. Die Profilerberichte können keine Symbolnamen auflösen. |
| [DA0030: Sammeln von Ebeneninteraktions-Messdaten für Datenbankprojekte](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md) | Es wurde eine hohe Anzahl von Methodenaufrufen im Namespace <xref:System.Data?displayProperty=fullName> gesammelt. Um Daten über die Datenbankaufrufe einzuschließen, sollten Sie Ebeneninteraktionsdaten in Ihren Profilausführungen sammeln. |
