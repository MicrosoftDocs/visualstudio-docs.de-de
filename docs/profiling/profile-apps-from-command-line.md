---
title: Messen der Leistung über die Befehlszeile
description: Messen Sie die CPU-Leistung und die Nutzung des verwalteten Speichers in Ihrer Anwendung über die Befehlszeile.
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, command-line
- Diagnostics Tools, command-line
- CPU Usage, command-line
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 0b1d5906213b148605e35c483b377280dc942515
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936547"
---
# <a name="measure-application-performance-from-the-command-line"></a>Messen der Anwendungsleistung über die Befehlszeile

Über die Befehlszeilentools können Sie Leistungsinformationen zu einer Anwendung sammeln.

In dem Beispiel, das in diesem Artikel beschrieben wird, sammeln Sie Leistungsinformationen zum Microsoft Notepad. Dieselbe Methode kann aber auch verwendet werden, um jeden anderen Prozess zu profilen.

## <a name="prerequisites"></a>Voraussetzungen

* Visual Studio 2019 oder höher

* Kenntnisse im Umgang mit Befehlszeilentools

* Installieren Sie die [Remotetools für Visual Studio](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019) auf dem Remotecomputer, um Leistungsinformationen auf einem Remotecomputer zu erfassen, auf dem Visual Studio nicht installiert ist. Die Version der Tools muss mit Ihrer Version von Visual Studio übereinstimmen.

## <a name="collect-performance-data"></a>Sammeln von Leistungsdaten

Bei der Profilerstellung mithilfe der CLI-Diagnosetools von Visual Studio wird das Profilerstellungstool zusammen mit einem der Collector-Agenten an einen Prozess angefügt. Wenn Sie das Profilerstellungstool anfügen, beginnen Sie eine Diagnosesitzung, die solange Profilerstellungsdaten aufnimmt und speichert, bis das Tool beendet wird. Dann werden die Daten in eine *.diagsession*-Datei exportiert. Diese Datei können Sie dann in Visual Studio öffnen, um die Ergebnisse zu analysieren.

1. Starten Sie das Notepad, und öffnen Sie dann den Taskmanager, um seine Prozess-ID (PID) zu erhalten. Im Taskmanager finden Sie die PID in der Registerkarte **Details**.

1. Öffnen Sie eine Eingabeaufforderung, und wechseln Sie zum Verzeichnis mit dem ausführbaren Sammlungs-Agent, das sich normalerweise hier (für Visual Studio Enterprise) befindet:

   ```<Visual Studio installation folder>\2019\Enterprise\Team Tools\DiagnosticsHub\Collector\```

1. Starten Sie *VSDiagnostics.exe*, indem Sie den folgenden Befehl ausführen.

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Folgende Argumente müssen eingeschlossen werden:

   * \<*id*>: bestimmt die Sammlungssitzung. Die ID muss eine Zahl im Bereich von 1 bis 255 sein.
   * \<*pid*>: Die PID des Prozesses, den Sie profilen möchten. Hier also die PID, die Sie in Schritt 1 abgerufen haben.
   * \<*configFile*>: Konfigurationsdatei des Sammlungs-Agents, den Sie starten möchten. Weitere Informationen finden Sie unter [Runtime Configuration Files (Konfigurationsdateien der Runtime)](#config_file).

   Beispielsweise können Sie den folgenden Befehl für den CPUUsageBase-Agent verwenden, indem Sie die *pid* wie zuvor beschrieben ersetzen.

   ```cmd
   VSDiagnostics.exe start 1 /attach:<pid> /loadConfig:AgentConfigs\CPUUsageLow.json
   ```

1. Ändern Sie die Größe des Notepads, oder geben Sie etwas ein, damit einige aussagekräftige Profilerstellungsinformationen gesammelt werden können.

1. Halten Sie die Sammlungssitzung an, und senden Sie die Ausgabe an eine Datei, indem Sie den folgenden Befehl eingeben.

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. Wechseln Sie zur Ausgabe der *DIAGSESSION*-Datei aus dem vorherigen Befehl, und öffnen Sie sie in Visual Studio (**Datei** > **Öffnen**), um die erfassten Informationen zu untersuchen.

   Informationen zum Analysieren der Ergebnisse finden Sie in der Dokumentation zum entsprechenden Leistungstool. Dies kann z. B. [CPU-Auslastung](../profiling/cpu-usage.md), das [.NET-Objektzuordnungstool](../profiling/dotnet-alloc-tool.md) oder das [Datenbanktool](../profiling/analyze-database.md) sein.

## <a name="agent-configuration-files"></a><a name="config_file"></a> Agent-Konfigurationsdateien

Sammlungs-Agents sind austauschbare Komponenten, die verschiedene Datentypen sammeln, je nachdem, was gemessen werden soll.

Der Bequemlichkeit halber können Sie diese Informationen in einer Agent-Konfigurationsdatei speichern. Die Konfigurationsdatei ist eine *.json*-Datei, die mindestens den Namen der *.dll*-Datei und deren COM-CLSID enthält. Hier sehen Sie die Beispielkonfigurationsdateien, die Sie im folgenden Ordner finden können:

```<Visual Studio installation folder>Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

Unter den folgenden Links können Sie die Konfigurationsdateien für den Agent herunterladen und anzeigen:

- https://aka.ms/vs/diaghub/agentconfig/cpubase
- https://aka.ms/vs/diaghub/agentconfig/cpuhigh
- https://aka.ms/vs/diaghub/agentconfig/cpulow
- https://aka.ms/vs/diaghub/agentconfig/database
- https://aka.ms/vs/diaghub/agentconfig/dotnetasyncbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetallocbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetalloclow
- https://aka.ms/vs/diaghub/agentconfig/dotnetcountersbase

Konfigurationen für die CPU-Nutzung (CpuUsage) (Standard/Hoch/Niedrig). entsprechen den Daten, die für das Profilerstellungstool für die [CPU-Auslastung](../profiling/cpu-usage.md) gesammelt wurden.
DotNetObjectAlloc-Konfigurationen (Standard/Niedrig) entsprechen den Daten, die für das [.NET-Objektzuteilungstool](../profiling/dotnet-alloc-tool.md) gesammelt wurden.

Die Konfigurationen „Standard“, „Niedrig“ und „Hoch“ beziehen sich auf die Stichprobenentnahmerate. So bedeutet „Niedrig“ z.B. 100 Stichproben pro Sekunde, und „Hoch“ 4000 Stichproben pro Sekunde.

Damit das *VSDiagnostics.exe*-Tool mit einem Sammlungs-Agent zusammenarbeitet, werden für den entsprechenden Agent sowohl eine DLL als auch eine COM-CLSID benötigt, und für den Agent gibt es möglicherweise auch zusätzliche Konfigurationsoptionen. Wenn Sie einen Agent ohne Konfigurationsdatei verwenden, verwenden Sie das Format im folgenden Befehl.

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>Berechtigungen

Um eine Anwendung zu profilen, die erweiterte Berechtigungen benötigt, müssen Sie eine Eingabeaufforderung mit erhöhten Rechten verwenden.
