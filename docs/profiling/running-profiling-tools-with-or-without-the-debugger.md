---
title: Ausführen von Profilerstellungstools mit oder ohne Debugger | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Unterschiede zwischen den verschiedenen verfügbaren Modi für Profilerstellungstools.
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0bd8f90c586366a298ba96009dfe5d87a042141b
ms.sourcegitcommit: ae9145b32fc8e1e663e504c315a5df5dd302fee9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92918109"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Ausführen von Profilerstellungstools mit oder ohne Debugger

Visual Studio bietet eine Auswahl an Tools für Leistungsmessung und Profilerstellung. Einige Tools, wie z. B. „CPU-Auslastung“ und „Speicherauslastung“, können mit oder ohne Debugger und in den Release- oder Debugbuildkonfigurationen ausgeführt werden. Im [Fenster „Diagnosetools“](../profiling/profiling-feature-tour.md#measure-performance-while-debugging) angezeigte Tools werden nur während einer Debugsitzung ausgeführt. Tools im [Leistungs-Profiler](../profiling/profiling-feature-tour.md#post_mortem) werden ohne den Debugger ausgeführt, und Sie analysieren die Ergebnisse, nachdem Sie die Option zum Beenden und Erfassen von Daten ausgewählt haben (für eine Post-Mortem-Analyse).

>[!NOTE]
>Sie können die nicht in den Debugger integrierten Leistungstools unter Windows 7 und höher verwenden. Windows 8 oder höher ist erforderlich, um die in den Debugger integrierten Profilerstellungstools auszuführen.

Der nicht in den Debugger integrierte Leistungs-Profiler und die in den Debugger integrierten Diagnosetools bieten verschiedene Informationen und Funktionen. In den Debugger integrierte Tools zeigen Variablenwerte an und ermöglichen Ihnen, Breakpoints zu verwenden. Nicht in den Debugger integrierte Tools bieten Ihnen Ergebnisse, die sich näher an der Endbenutzeroberfläche befinden.

Berücksichtigen Sie bei der Entscheidung, welche Tools und Ergebnisse Sie nutzen möchten, Folgendes:

- In den Debugger integrierte Tools im Vergleich zu nicht in den Debugger integrierten Tools
  - Externe Leistungsprobleme, wie z.B. Datei-E/A oder die Reaktionszeit des Netzwerks, werden in den Debuggertools ähnlich angezeigt wie in den nicht in den Debugger integrierten Tools.
  - Der Debugger selbst ändert Leistungszeiten, während er erforderliche Debuggervorgänge durchführt, wie z. B. das Abfangen von Ausnahmen und Modulladeereignissen.
  - Leistungsangaben zu Releasebuilds im Leistungs-Profiler sind am präzisesten und genauesten. In den Debugger integrierte Toolergebnisse sind besonders nützlich, wenn es um den Vergleich mit anderen debuggingbezogenen Messungen oder die Verwendung von Debuggerfeatures geht.
  - Einige Tool, darunter z. B. das Tool für die .NET-Objektzuordnung, steht nur in Szenarien ohne Debugger zur Verfügung.
- Debug- im Vergleich zu Releasebuilds
  - Bei Problemen, die durch CPU-intensive Aufrufe ausgelöst werden, kann es möglicherweise zu erheblichen Leistungsunterschieden zwischen Release- und Debugbuilds kommen. Überprüfen Sie, ob das Problem in Releasebuilds vorhanden ist.
  - Wenn das Problem nur bei Debugbuilds auftritt, ist es wahrscheinlich, dass Sie die nicht in den Debugger integrierten Tools nicht ausführen müssen. Entscheiden Sie bei Releasebuildproblemen, ob die Features zum Ermitteln des Problems beitragen, die von den Tools bereitgestellt werden, die in den Debugger integriert sind.
  - Releasebuilds bieten Optimierungen wie Inlinefunktionsaufrufe und -konstanten, die ungenutzte Codepfade bereinigen und Variablen mit bestimmten Methoden speichern, sodass sie vom Debugger nicht genutzt werden können. Leistungsangaben in den Debugbuilds sind weniger genau, da Debugbuilds diese Optimierungen fehlen.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Sammeln von Profilerstellungsdaten während des Debuggens

Wenn Sie mit dem Debuggen in Visual Studio beginnen, indem Sie **Debuggen** > **Debuggen starten** wählen oder **F5** drücken, wird das Fenster **Diagnosetools** standardmäßig angezeigt. Klicken Sie auf **Debuggen** > **Fenster** > **Diagnosetools anzeigen** , um dieses Fenster manuell zu öffnen. Das Fenster **Diagnosetools** enthält Informationen über Ereignisse, den Prozessarbeitsspeicher und die CPU-Auslastung.

![Screenshot des Fensters „Diagnosetools“](../profiling/media/diagnostictoolswindow.png "Fenster „Diagnosetools“")

- Klicken Sie auf das Symbol für **Einstellungen** in der Symbolleiste, um die **Arbeitsspeicherauslastung** , die **UI-Analyse** , und die **CPU-Auslastung** zu anzuzeigen.

- Wählen Sie **Einstellungen** in der Dropdownliste **Einstellungen** aus, um die **Eigenschaftenseiten der Diagnosetools** mit weiteren Optionen zu öffnen.

- Wenn Sie Visual Studio Enterprise ausführen, können Sie IntelliTrace unter **Extras** > **Optionen** > **IntelliTrace** aktivieren oder deaktivieren.

Die Diagnosesitzung endet, wenn Sie das Debugging beenden.

Weitere Informationen finden Sie in folgenden Quellen:

- [Messen der Anwendungsleistung durch Analyse der CPU-Nutzung](../profiling/beginners-guide-to-performance-profiling.md)
- [Messen der Speicherauslastung in Visual Studio](../profiling/memory-usage.md)

### <a name="the-events-tab"></a>Die Registerkarte „Ereignisse“

Während einer Debugsitzung werden die auftretenden Diagnoseereignisse im Fenster „Diagnosetools“ auf der Registerkarte „Ereignisse“ aufgelistet. Mit den Kategoriepräfixen *Haltepunkt* , *Datei* u. a. können Sie schnell die Liste nach einer Kategorie durchsuchen oder die Kategorien überspringen, die für Sie gerade nicht relevant sind.

Verwenden Sie in der Dropdownliste **Filter** , um Ereignisse anzuzeigen oder auszublenden, indem Sie bestimmte Ereigniskategorien auswählen oder abwählen.

![Screenshot des Filters „Diagnoseereignis“](../profiling/media/diagnosticeventfilter.png "Filtern von Diagnoseereignissen")

Verwenden Sie das Suchfeld, um eine bestimmte Zeichenfolge in der Ereignisliste zu suchen. Dies sind die Suchergebnisse für die Zeichenfolge *name* , die mit vier Ereignissen übereinstimmt:

![Screenshot der Suche „Diagnoseereignis“](../profiling/media/diagnosticseventsearch.png "Suchen nach Diagnoseereignissen")

Weitere Informationen finden Sie unter [Suchen und Filtern auf der Registerkarte "Ereignisse" im Fenster "Diagnosetools"](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Sammeln von Profilerstellungsdaten ohne das Debuggen

Sie können zum Erfassen von Leistungsdaten ohne Debuggen die Leistungs-Profiler-Tools ausführen.

1. Legen Sie mit einem in Visual Studio geöffneten Projekt die Konfiguration der Projektmappe auf **Release** fest, und wählen Sie als Bereitstellungsziel **Lokaler Windows-Debugger** (oder **Lokaler Computer** ) aus.

1. Klicken Sie auf **Debuggen** > **Leistungs-Profiler** , oder drücken Sie **ALT**+**F2**.

1. Wählen Sie auf der Startseite der Diagnosetools mindestens ein Tools aus, das ausgeführt werden soll. Es werden nur die Tools gezeigt, die für den Projekttyp, das Betriebssystem und die Programmiersprache infrage kommen. Wählen Sie **Alle Tools anzeigen** , um auch Tools anzuzeigen, die für diese Diagnosesitzung deaktiviert sind.

   ![Screenshot der Diagnosetools](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. Klicken Sie zum Starten der Diagnosesitzung auf **Start**.

   Während Sie die Sitzung ausführen, zeigen einige Tools auf der Seite der Diagnosetools Diagramme mit Echtzeitdaten sowie Steuerelemente zum Anhalten und Fortsetzen der Datensammlung.

    ![Screenshot der Datensammlung auf dem Leistungs-Profiler](../profiling/media/diaghubcollectdata.png "Sammeln von Daten im Hub")

1. Klicken Sie zum Beenden der Diagnosesitzung auf **Sammlung beenden**.

   Die analysierten Daten werden auf der Seite **Bericht** angezeigt.

Sie können die Berichte auch speichern und über die Liste der **zuletzt geöffneten Sitzungen** auf der Startseite der Diagnosetools öffnen.

![Screenshot der Liste der zuletzt geöffneten Sitzungen in den Diagnosetools](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

Weitere Informationen finden Sie in folgenden Quellen:

- [Analysieren der CPU-Auslastung](../profiling/cpu-usage.md)
- [Analysieren der Speicherauslastung für .NET-Code](../profiling/dotnet-alloc-tool.md)
- [Analysieren der Speicherauslastung](../profiling/memory-usage-without-debugging2.md)
- [Analysieren der Leistung von asynchronem .NET-Code](../profiling/analyze-async.md)
- [Analysieren der Datenbankleistung](../profiling/analyze-database.md)
- [Analysieren der GPU-Nutzung](../profiling/gpu-usage.md)

## <a name="collect-profiling-data-from-the-command-line"></a>Sammeln von Profilerstellungsdaten über die Befehlszeile

Um Leistungsdaten über die Befehlszeile zu messen, können Sie das Tool „VSDiagnostics.exe“ verwenden, das entweder in Visual Studio oder den Remotetools enthalten ist. Es ist nützlich für die Erfassung von Leistungsüberwachungen auf Systemen, auf denen Visual Studio nicht installiert ist, oder für die Erstellung von Skripts für die Sammlung von Leistungsüberwachungen. Ausführliche Anweisungen finden Sie unter [Messen der Anwendungsleistung über die Befehlszeile](../profiling/profile-apps-from-command-line.md).