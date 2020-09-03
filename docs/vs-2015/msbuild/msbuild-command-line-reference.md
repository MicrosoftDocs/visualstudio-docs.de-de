---
title: MSBuild-Befehlszeilenreferenz | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, msbuild.exe
- MSBuild, command line reference
- msbuild.exe
ms.assetid: edaa65ec-ab8a-42a1-84cb-d76d5b2f4584
caps.latest.revision: 61
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8d40bfefb1f89496b538612dfa1819cc6d65c76c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181056"
---
# <a name="msbuild-command-line-reference"></a>MSBuild-Befehlszeilenreferenz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie mithilfe von MSBUILD.EXE ein Projekt oder eine Projektmappendatei erstellen, können Sie diverse Schalter verwenden, um verschiedene Aspekte des Prozesses festzulegen.  
  
## <a name="syntax"></a>Syntax  
  
```  
MSBuild.exe [Switches] [ProjectFile]  
```  
  
## <a name="arguments"></a>Argumente  
  
|Argument|Beschreibung|  
|--------------|-----------------|  
|`ProjectFile`|Erstellt die Ziele in der von Ihnen angegebenen Projektdatei. Wenn Sie keine Projektdatei angeben, durchsucht MSBuild das aktuelle Arbeitsverzeichnis nach einer Dateinamenerweiterung, die mit "proj" endet, und verwendet diese. Sie können hier auch eine Visual Studio-Projektmappendatei als Argument angeben.|  
  
## <a name="switches"></a>Schalter  
  
|Schalter|Kurzform|Beschreibung|  
|------------|----------------|-----------------|  
|/help|/? oder /h|Zeigt Nutzungsinformationen an. Der folgende Befehl ist ein Beispiel:<br /><br /> `msbuild.exe /?`|  
|/detailedsummary|/ds|Zeigt am Ende des Buildprotokolls ausführliche Informationen zu den erstellten Konfigurationen und deren Planung in Knoten an.|  
|/ignoreprojectextensions: `extensions`|/ignore: `extensions`|Ignoriert beim Bestimmen der zu erstellenden Projektdatei die angegebenen Erweiterungen. Mehrere Erweiterungen werden mit einem Semikolon oder einem Komma getrennt, wie im folgenden Beispiel gezeigt:<br /><br /> `/ignoreprojectextensions:.vcproj,.sln`|  
|/maxcpucount[:`number`]|/m[:`number`]|Gibt die maximale Anzahl gleichzeitiger Prozesse beim Buildvorgang an. Wenn Sie diesen Schalter nicht angeben, wird der Standardwert 1 verwendet. Wenn Sie diesen Schalter ohne Angabe eines Werts verwenden, nutzt MSBuild alle Prozessoren des Computers. Weitere Informationen finden Sie unter [paralleles gleichzeitige aufbauen von mehreren Projekten](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).<br /><br /> Im folgenden Beispiel wird MSBuild angewiesen, drei MSBuild-Prozesse für Buildvorgänge zu nutzen, sodass drei Projekte gleichzeitig erstellt werden können:<br /><br /> `msbuild myproject.proj /maxcpucount:3`|  
|/noautoresponse|/noautorsp|Es werden keine MSBUILD.RSP-Dateien automatisch eingeschlossen.|  
|/nodeReuse:`value`|/nr:`value`|Aktiviert oder deaktiviert die Wiederverwendung von MSBuild-Knoten. Sie können folgende Werte angeben:<br /><br /> -   **TRUE**. Nach Abschluss des Buildvorgangs bleiben die Knoten bestehen, sodass sie von nachfolgenden Buildvorgängen genutzt werden können (Standardeinstellung).<br />-   **FALSE**. Nach Abschluss des Buildvorgangs bleiben die Knoten nicht bestehen.<br /><br /> Ein Knoten entspricht einem Projekt, das ausgeführt wird. Wenn Sie den Schalter **/maxcpucount** einschließen, können mehrere Knoten gleichzeitig ausgeführt werden.|  
|/nologo||Unterdrückt die Anzeige von Startbanner und Copyrightmeldung.|  
|/preprocess[:`filepath`]|/pp[:`filepath`]|Erstellt eine einzelne, aggregierte Projektdatei durch Einbeziehen ("Inlining") sämtlicher Dateien, die während eines Builds importiert werden, unter Angabe ihrer Grenzen. Mithilfe dieses Schalters können Sie leichter feststellen, welche Dateien importiert werden, woher diese Dateien importiert werden und welche Dateien an dem Buildvorgang beteiligt sind. Wenn Sie diesen Schalter verwenden, wird das Projekt nicht erstellt.<br /><br /> Wenn Sie einen `filepath` angeben, wird die aggregierte Projektdatei in die Datei ausgegeben. Andernfalls wird die Ausgabe im Konsolenfenster angezeigt.<br /><br /> Informationen dazu, wie Sie das- `Import` Element verwenden, um eine Projektdatei in eine andere Projektdatei einzufügen, finden Sie unter [Import-Element (MSBuild)](../msbuild/import-element-msbuild.md) und Gewusst [wie: Verwenden desselben Ziels in mehreren Projektdateien](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).|  
|/property:`name`=`value`|/p:`name`=`value`|Dient zum Festlegen oder Überschreiben der angegebenen Eigenschaften auf Projektebene. Dabei ist `name` der Name und `value` der Wert der Eigenschaft. Geben Sie jede Eigenschaft einzeln an oder verwenden Sie ein Semikolon oder ein Komma, um mehrere Eigenschaften zu trennen (siehe Beispiel):<br /><br /> `/property:WarningLevel=2;OutDir=bin\Debug`|  
|/target:`targets`|/t:`targets`|Erstellt die angegebenen Ziele im Projekt. Geben Sie jedes Ziel einzeln an oder verwenden Sie ein Semikolon oder ein Komma, um mehrere Ziele zu trennen (siehe Beispiel):<br /><br /> `/target:Resources;Compile`<br /><br /> Wenn Sie über diesen Schalter Ziele angeben, werden diese anstelle der im `DefaultTargets`-Attribut in der Projektdatei angegebenen Ziele ausgeführt. Weitere Informationen finden Sie unter [Buildreihenfolge für Ziele](../msbuild/target-build-order.md) und Gewusst [wie: Angeben des zuerst zu erstmalig erstellungsziels](../msbuild/how-to-specify-which-target-to-build-first.md).<br /><br /> Als Ziel wird eine Gruppe von Aufgaben bezeichnet. Weitere Informationen finden Sie unter [Ziele](../msbuild/msbuild-targets.md).|  
|/toolsversion:`version`|/tv:`version`|Gibt die Version des Toolsets an, mit dem das Projekt erstellt werden soll, wie zum Beispiel: `/toolsversion:3.5`<br /><br /> Wenn Sie diesen Schalter verwenden, können Sie ein Projekt erstellen und eine Version angeben, die sich von der im [Project-Element (MSBuild)](../msbuild/project-element-msbuild.md)angegebenen Version unterscheidet. Weitere Informationen finden Sie unter Überschreiben von [ToolsVersion-Einstellungen](../msbuild/overriding-toolsversion-settings.md).<br /><br /> Bei MSBuild 4.5 können Sie für `version` die folgenden Werte angeben: 2.0, 3.5 und 4.0. Wenn Sie 4.0 angeben, gibt die Buildeigenschaft `VisualStudioVersion` an, welches Unter-Toolset verwendet werden soll. Weitere Informationen finden Sie im Abschnitt zu Unter-Toolsets unter [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).<br /><br /> Ein Toolset besteht aus Aufgaben, Zielen und Tools, die beim Erstellen einer Anwendung verwendet werden. Zu den Tools zählen Compiler wie "csc.exe" und "vbc.exe". Weitere Informationen zu Toolsets finden Sie unter [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), [Standard mäßige und benutzerdefinierte Toolsetkonfigurationen](../msbuild/standard-and-custom-toolset-configurations.md)und Festlegung von [Ziel](../msbuild/msbuild-multitargeting-overview.md)Versionen. **Hinweis:**  Die Toolsetversion ist nicht das gleiche wie das Ziel Framework, d. h. die Version der .NET Framework, für deren Ausführung ein Projekt erstellt wurde. Weitere Informationen finden Sie unter [Ziel Framework und Zielplattform](../msbuild/msbuild-target-framework-and-target-platform.md).|  
|/validate:[`schema`]|/val[`schema`]|Überprüft die Projektdatei und erstellt bei erfolgreicher Überprüfung das Projekt.<br /><br /> Wenn Sie `schema` nicht angeben, wird das Projekt anhand des Standardschemas überprüft.<br /><br /> Wenn Sie `schema` angeben, wird das Projekt anhand des angegebenen Schemas überprüft.<br /><br /> Die folgende Einstellung ist ein Beispiel: `/validate:MyExtendedBuildSchema.xsd`|  
|/verbosity:`level`|/v:`level`|Gibt den Umfang an Informationen an, die im Buildprotokoll angezeigt werden sollen. Jede Protokollierung zeigt Ereignisse gemäß des Ausführlichkeitsgrads an, den Sie für diese Protokollierung festlegen.<br /><br /> Für den Ausführlichkeitsgrad können Sie die folgenden Werte angeben: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` und `diag[nostic]`.<br /><br /> Die folgende Einstellung ist ein Beispiel: `/verbosity:quiet`|  
|/version|/ver|Zeigt nur Versionsinformationen an. Das Projekt wird nicht erstellt.|  
|@`file`||Fügt Befehlszeilenschalter aus einer Textdatei ein. Wenn Sie mehrere Dateien haben, müssen Sie diese separat angeben. Weitere Informationen finden Sie unter [Antwort Dateien](../msbuild/msbuild-response-files.md).|  
  
### <a name="switches-for-loggers"></a>Schalter für Protokollierungen  
  
|Schalter|Kurzform|Beschreibung|  
|------------|----------------|-----------------|  
|/consoleloggerparameters:<br /><br /> `parameters`|/clp:`parameters`|Übergibt die angegebenen Parameter an die Konsolenprotokollierung, die Buildinformationen im Konsolenfenster anzeigt. Sie können die folgenden Parameter angeben:<br /><br /> -   **PerformanceSummary**. Zeigt die Zeitdauer bei der Arbeit an Aufgaben, Zielen und Projekten an.<br />-   **Summary**. Zeigt am Ende eine Zusammenfassung zu aufgetretenen Fehlern und Warnungen an.<br />-   **NoSummary**. Am Ende wird keine Zusammenfassung zu aufgetretenen Fehlern und Warnungen angezeigt.<br />-   **ErrorsOnly**. Nur Fehler werden angezeigt.<br />-   **WarningsOnly**. Nur Warnungen werden angezeigt.<br />-   **NoItemAndPropertyList**. Unterdrückt die Anzeige der Liste von Elementen und Eigenschaften, die zu Beginn jedes Projekts angezeigt wird, wenn der Ausführlichkeitsgrad auf `diagnostic` festgelegt ist.<br />-   **ShowCommandLine**. Zeigt `TaskCommandLineEvent`-Meldungen an.<br />-   **ShowTimestamp**. Stellt jeder Meldung den zugehörigen Zeitstempel voran.<br />-   **ShowEventId**. Zeigt zu jedem Ereignis vom Typ "Gestartet" und "Abgeschlossen" sowie zu jeder Meldung die Ereignis-ID an.<br />-   **ForceNoAlign**. Hierbei wird der Text nicht der Größe des Konsolenpuffers angeglichen.<br />-   **DisableConsoleColor**. Verwendet bei allen Protokollierungsmeldungen die Standardkonsolenfarben.<br />-   **DisableMPLogging**. Deaktiviert bei Ausführung im Einzelprozessormodus das Multiprozessor-Protokollierungsformat der Ausgabe.<br />-   **EnableMPLogging**. Aktiviert das Multiprozessor-Protokollierungsformat auch bei Ausführung im Einzelprozessormodus. Dieses Protokollierungsformat ist standardmäßig aktiviert.<br />-   **Verbosity**. Überschreiben Sie die **/verbosity** -Einstellung für diese Protokollierung.<br /><br /> Mehrere Parameter sind mit einem Semikolon oder Komma zu trennen, wie im folgenden Beispiel gezeigt:<br /><br /> `/consoleloggerparameters:PerformanceSummary;NoSummary /verbosity:minimal`|  
|/distributedFileLogger|/dfl|Protokolliert die Buildausgabe jedes MSBuild-Knotens in dessen eigene Datei. In der Standardeinstellung werden diese Dateien im aktuellen Verzeichnis gespeichert. Standardmäßig haben die Dateien den Namen "MSBuild*NodeId*. log". Sie können den **Schalter/fileLoggerParameters** -Schalter verwenden, um den Speicherort der Dateien und anderer Parameter für den FileLogger anzugeben.<br /><br /> Wenn Sie eine Protokolldatei mit dem Schalter **Schalter/fileLoggerParameters** benennen, verwendet die verteilte Protokollierung diesen Namen als Vorlage und fügt die Knoten-ID an diesen Namen an, wenn für jeden Knoten eine Protokolldatei erstellt wird.|  
|/distributedlogger:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|/dl:`central logger`*`forwarding logger`|Protokolliert Ereignisse von MSBuild und hängt an jeden Knoten eine andere Protokollierungsinstanz an. Wenn Sie mehrere Protokollierungen angeben möchten, müssen Sie jede Protokollierung einzeln angeben.<br /><br /> Zum Angeben einer Protokollierung verwenden Sie die Protokollierungssyntax. Die Protokollierungs Syntax finden Sie unten im **/Logger** -Schalter.<br /><br /> Das folgende Beispiel zeigt, wie dieser Schalter verwendet wird:<br /><br /> `/dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|  
|/fileLogger<br /><br /> *[number]*|/fl[`number`]|Protokolliert die Buildausgabe in einer einzelnen Datei im aktuellen Verzeichnis. Wenn Sie `number` nicht angeben, erhält die Ausgabedatei den Namen MSBUILD.LOG. Wenn Sie `number` angeben, erhält die Ausgabedatei den Namen MSBUILD`n`.LOG (wobei "n" für die in `number` angegebene Nummer steht). `Number` kann eine Ziffer von 1 bis 9 sein.<br /><br /> Sie können den **Schalter/fileLoggerParameters** -Schalter verwenden, um den Speicherort der Datei und andere Parameter für den FileLogger anzugeben.|  
|/fileloggerparameters:[Zahl]<br /><br /> `parameters`|/flp:[ `number`] `parameters`|Dient zur Angabe aller sonstigen Parameter für die Dateiprotokollierung und die verteilte Dateiprotokollierung. Das vorhanden sein dieses Schalters impliziert, dass der entsprechende Schalter/**FileLogger [** `number` **]** vorhanden ist. `Number` kann eine Ziffer von 1 bis 9 sein.<br /><br /> Sie können alle Parameter verwenden, die für **/consoleloggerparameters**aufgelistet sind. Sie können auch einen oder mehrere der folgenden Parameter verwenden:<br /><br /> -   **LogFile**. Gibt den Pfad zu der Protokolldatei an, in die das Buildprotokoll geschrieben wird. Die verteilte Dateiprotokollierung stellt diesen Pfad den Namen seiner Protokolldateien voran.<br />-   **Append**. Bestimmt, ob das Buildprotokoll an die Protokolldatei angefügt wird oder diese überschreibt. Wenn Sie den Schalter setzen, wird das Buildprotokoll an die Protokolldatei angefügt. Wenn der Schalter nicht angegeben ist, wird der Inhalt einer vorhandenen Protokolldatei überschrieben.<br />     Wenn Sie den "append"-Schalter angeben – wobei es keine Rolle spielt, ob Sie ihn auf "true" oder "false" stellen – wird das Protokoll angefügt. Wenn der Schalter nicht vorhanden ist, wird das Protokoll überschrieben.<br />     In diesem Fall wird die Datei überschrieben: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log`<br />     In diesem Fall wird die Datei angefügt: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=true`<br />     In diesem Fall wird die Datei angefügt: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=false`<br />-   **Encoding**. Gibt die Codierung für die Datei an (z. B. UTF-8, Unicode oder ASCII).<br /><br /> Das folgende Beispiel generiert separate Protokolldateien für Warnungen und Fehler:<br /><br /> `/flp1:logfile=errors.txt;errorsonly /flp2:logfile=warnings.txt;warningsonly`<br /><br /> Die folgenden Beispiele zeigen weitere Möglichkeiten:<br /><br /> `/fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `/flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `/flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `/flp2:errorsonly;logfile=msbuild.err`|  
|/logger:<br /><br /> `logger`|/l:`logger`|Gibt die Protokollierung an, mit der Ereignisse aus MSBuild protokolliert werden sollen. Wenn Sie mehrere Protokollierungen angeben möchten, müssen Sie jede Protokollierung einzeln angeben.<br /><br /> Verwenden Sie bei `logger` die folgende Syntax: `[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> Verwenden Sie bei `LoggerClass` die folgende Syntax: `[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> Wenn die Assembly genau eine Protokollierung enthält, muss die Protokollierungsklasse nicht angegeben werden.<br /><br /> Verwenden Sie bei `LoggerAssembly` die folgende Syntax: `{``AssemblyName``[,``StrongName``] &#124;` `AssemblyFile``}`<br /><br /> Protokollierungsparameter sind optional und werden so an die Protokollierung übergeben, wie Sie sie eingegeben würden.<br /><br /> In den folgenden Beispielen wird der Schalter **/Logger** verwendet.<br /><br /> `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|  
|/noconsolelogger|/noconlog|Deaktiviert die standardmäßige Konsolenprotokollierung und protokolliert keine Ereignisse in der Konsole.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das Ziel `rebuild` des Projekts `MyProject.proj` erstellt.  
  
```  
MSBuild.exe MyProject.proj /t:rebuild  
```  
  
## <a name="example"></a>Beispiel  
 Mit MSBUILD.EXE sind auch komplexere Builds möglich. So können Sie das Tool zum Beispiel verwenden, um bestimmte Ziele von bestimmten Projekten in einer Projektmappe zu erstellen. Im folgenden Beispiel wird das Projekt `NotInSolutionFolder` neu erstellt, und das Projekt `InSolutionFolder` im `NewFolder`-Projektmappenordner wird gelöscht.  
  
```  
msbuild SlnFolders.sln /t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)   
 [Allgemeine MSBuild-Projekteigenschaften](../msbuild/common-msbuild-project-properties.md)
