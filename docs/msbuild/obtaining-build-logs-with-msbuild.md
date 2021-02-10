---
title: Erhalten von Buildprotokollen mit MSBuild | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mithilfe von Schaltern in MSBuild angeben können, wie viele Builddaten zu überprüfen sind und ob Sie Builddaten in einer oder mehreren Dateien speichern möchten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7ecfa11122b76bcfef3473ff5d06083c64157a2c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905430"
---
# <a name="obtain-build-logs-with-msbuild"></a>Erhalten von Buildprotokollen mit MSBuild

Indem Sie Schalter mit MSBuild verwenden, können Sie angeben, wie viele Builddaten zu überprüfen sind und ob Sie Builddaten in eine oder mehrere Dateien speichern möchten. Sie können auch eine benutzerdefinierte Protokollierung zum Sammeln von Builddaten angeben. Weitere Informationen zu MSBuild-Befehlszeilenschaltern, die in diesem Thema nicht behandelt werden, finden Sie unter [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> Wenn Sie Projekte mithilfe von Visual Studio-IDE erstellen, können Sie die Probleme diese Builds beheben, indem Sie Buildprotokolle überprüfen. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="set-the-level-of-detail"></a>Festlegen des Detailgrads

 Wenn Sie ein Projekt mithilfe von MSBuild ohne Angabe einer Detailebene erstellen, werden die folgenden Informationen im Ausgabeprotokoll angezeigt:

- Fehler, Warnungen und Nachrichten, die als äußerst wichtig eingestuft werden.

- Einige Statusereignisse.

- Eine Übersicht des Build.

Mithilfe des Schalters **-verbosity** ( **-v**) können Sie steuern, wie viele Daten im Ausgabeprotokoll angezeigt werden. Verwenden Sie für die Problembehandlung entweder den Ausführlichkeitsgrad `detailed` (`d`) oder `diagnostic` (`diag`), der die meisten Informationen bietet.

Der Buildprozess ist möglicherweise langsamer, wenn Sie **-verbosity** auf `detailed` festlegen, und sogar noch langsamer, wenn Sie **-verbosity** auf `diagnostic` festlegen.

```cmd
msbuild MyProject.proj -t:go -v:diag
```

### <a name="verbosity-settings"></a>Einstellungen für die Ausführlichkeit

In der folgenden Tabelle wird gezeigt, wie sich die Ausführlichkeit der Protokolle (Spaltenwerte) darauf auswirkt, welche Nachrichtentypen (Zeilenwerte) protokolliert werden.

| Nachrichtentyp/Ausführlichkeit              | Quiet | Minimal | Normal | Detailliert | Diagnose |
|---------------------------------------|:-----:|:-------:|:------:|:--------:|:----------:|
| Fehler                                |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Warnungen                              |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Nachrichten mit hoher Priorität              |       |    ✅    |    ✅   |     ✅    |      ✅     |
| Nachrichten mit normaler Priorität           |       |         |    ✅   |     ✅    |      ✅     |
| Nachrichten mit niedriger Priorität              |       |         |        |     ✅    |      ✅     |
| Zusätzliche Informationen zur MSBuild-Engine |       |         |        |          |      ✅     |

## <a name="save-the-build-log-to-a-file"></a>Speichern des Buildprotokolls in einer Datei

Sie können den Schalter **-fileLogger** (**fl**) verwenden, um Builddaten in einer Datei zu speichern. Im folgenden Beispiel werden die Builddaten in einer Datei mit dem Namen *msbuild.log* gespeichert.

```cmd
msbuild MyProject.proj -t:go -fileLogger
```

 Im folgenden Beispiel heißt die Protokolldatei *MyProjectOutput.log*, und der Ausführlichkeitsgrad der Protokollausgabe ist auf `diagnostic` festgelegt. Geben Sie diese beiden Einstellungen mithilfe des Schalters **-fileLoggerParameters** (`flp`) an.

```cmd
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic
```

 Weitere Informationen finden Sie unter [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md).

## <a name="save-the-log-output-to-multiple-files"></a>Speichern der Protokollausgabe in mehreren Dateien

 Im folgenden Beispiel wird das gesamte Protokoll in *msbuild1.log*, nur die Fehler in *JustErrors.log* und nur die Warnungen in *JustWarnings.log* gespeichert. Im Beispiel werden Dateinummern für jede der drei Dateien verwendet. Die Dateinummern werden nach den Schaltern **-fl** und **-flp** angegeben (z.B. `-fl1` und `-flp1`).

 Die Schalter **-fileLoggerParameters** (`flp`) für die Dateien 2 und 3 gibt an, wie jede Datei benannt werden und was sie enthalten soll. Es wird kein Name für die Datei 1 angegeben, deshalb wird der Standardname *msbuild1.log* verwendet.

```cmd
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly
```

 Weitere Informationen finden Sie unter [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md).

## <a name="save-a-binary-log"></a>Speichern eines binären Protokolls

Sie können das Protokoll mit dem Parameter **-binaryLogger** (**bl**) in einem komprimierten, binären Format speichern. Dieses Protokoll enthält eine ausführliche Beschreibung vom Buildprozess und kann mithilfe von bestimmten Protokollanalysetools gelesen werden.

Im folgenden Beispiel wird eine binäre Protokolldatei mit dem Namen *binarylogfilename* erstellt.

```cmd
-bl:binarylogfilename.binlog
```

Weitere Informationen finden Sie unter [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md).

## <a name="use-a-custom-logger"></a>Verwenden einer benutzerdefinierten Protokollierung

 Sie können eine eigene Protokollierung schreiben, indem Sie einen verwalteten Typ erstellen, der die <xref:Microsoft.Build.Framework.ILogger>-Schnittstelle implementiert. Sie können eine benutzerdefinierte Protokollierung verwenden, um z.B. Buildfehler per E-Mail zu versenden, sie in einer Datenbank oder einer XML-Datei zu protokollieren. Weitere Informationen finden Sie unter [Buildprotokollierungen](../msbuild/build-loggers.md).

 In der MSBuild-Befehlszeile geben Sie die benutzerdefinierte Protokollierung mithilfe des Schalters **-logger** an. Sie können auch den Schalter **-noconsolelogger** verwenden, um die Standardkonsole zu deaktivieren.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.Build.Framework.LoggerVerbosity>
- [Buildprotokollierungen](../msbuild/build-loggers.md)
- [Protokollierung in einer Multiprozessorumgebung](../msbuild/logging-in-a-multi-processor-environment.md)
- [Erstellen von Weiterleitungsprotokollierungen](../msbuild/creating-forwarding-loggers.md)
- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
