---
title: Erhalten von Buildprotokollen mit MSBuild | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c88288a7bed453ca14e9c14fd43706b97be04044
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840917"
---
# <a name="obtaining-build-logs-with-msbuild"></a>Erhalten von Buildprotokollen mit MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Indem Sie Schalter mit MSBuild verwenden, können Sie angeben, wie viele Builddaten zu überprüfen sind und ob Sie Builddaten in eine oder mehrere Dateien speichern möchten. Sie können auch eine benutzerdefinierte Protokollierung zum Sammeln von Builddaten angeben. Informationen zu MSBuild-Befehlszeilen Schaltern, die in diesem Thema nicht behandelt werden, finden Sie unter [Befehlszeilen Referenz](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
> Wenn Sie Projekte mithilfe von Visual Studio-IDE erstellen, können Sie die Probleme diese Builds beheben, indem Sie Buildprotokolle überprüfen. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## <a name="setting-the-level-of-detail"></a>Festlegen des Detailgrads  
 Wenn Sie ein Projekt mithilfe von MSBuild ohne Angabe einer Detailebene erstellen, werden die folgenden Informationen im Ausgabeprotokoll angezeigt:  
  
- Fehler, Warnungen und Nachrichten, die als äußerst wichtig eingestuft werden.  
  
- Einige Statusereignisse.  
  
- Eine Übersicht des Build.  
  
  Mit dem Schalter **/verbosity** (**/v**) können Sie steuern, wie viele Daten im Ausgabeprotokoll angezeigt werden. Verwenden Sie für die Problembehandlung entweder den Ausführlichkeitsgrad `detailed` (`d`) oder `diagnostic` (`diag`), der die meisten Informationen bietet.  
  
  Der Buildprozess ist möglicherweise langsamer, wenn Sie die **/verbosity** auf `detailed` und noch langsamer festlegen, wenn Sie **/verbosity** auf festlegen `diagnostic` .  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## <a name="saving-the-build-log-to-a-file"></a>Speichern des Buildprotokolls in einer Datei  
 Sie können den Schalter **/FileLogger** (**FL**) verwenden, um Builddaten in einer Datei zu speichern. Im folgenden Beispiel werden die Builddaten in einer Datei mit dem Namen `msbuild.log` gespeichert.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 Im folgenden Beispiel heißt die Protokolldatei `MyProjectOutput.log` und der Ausführlichkeitsgrad der Protokollausgabe ist auf `diagnostic` festgelegt. Sie geben diese beiden Einstellungen mithilfe des **/filelogparameters** ( `flp` )-Schalters an.  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Weitere Informationen finden Sie unter [Befehlszeilen Referenz](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="saving-the-log-output-to-multiple-files"></a>Speichern der Protokollausgabe in mehreren Dateien  
 Im folgenden Beispiel wird das gesamte Protokoll in `msbuild1.log`, nur die Fehler in `JustErrors.log` und nur die Warnungen in `JustWarnings.log` gespeichert. Im Beispiel werden Dateinummern für jede der drei Dateien verwendet. Die Datei Nummern werden direkt nach den **/FL** -und **/FLP** -Switches (z `/fl1` . b `/flp1` . und) angegeben.  
  
 Die Schalter **/filelogparameters** ( `flp` ) für die Dateien 2 und 3 geben an, wie die einzelnen Dateien und was in jeder Datei enthalten sein soll. Es wird kein Name für die Datei 1 angegeben, deshalb wird der Standardname `msbuild1.log` verwendet.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Weitere Informationen finden Sie unter [Befehlszeilen Referenz](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="using-a-custom-logger"></a>Verwenden einer benutzerdefinierten Protokollierung  
 Sie können eine eigene Protokollierung schreiben, indem Sie einen verwalteten Typ erstellen, der die <xref:Microsoft.Build.Framework.ILogger>-Schnittstelle implementiert. Sie können eine benutzerdefinierte Protokollierung verwenden, um z.B. Buildfehler per E-Mail zu versenden, sie in einer Datenbank oder einer XML-Datei zu protokollieren. Weitere Informationen finden Sie unter [buildprotokollierungen](../msbuild/build-loggers.md).  
  
 In der MSBuild-Befehlszeile geben Sie die benutzerdefinierte Protokollierung mithilfe des **/Logger** -Schalters an. Sie können auch den **/noconsolelogger** -Schalter verwenden, um die standardmäßige Konsolen Protokollierung zu deaktivieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Buildprotokollierungen](../msbuild/build-loggers.md)   
 [Protokollierung in einer Umgebung mit mehreren Prozessoren](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Erstellen von Weiterleitungs Protokollierungen](../msbuild/creating-forwarding-loggers.md)   
 [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
