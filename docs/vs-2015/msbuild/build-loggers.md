---
title: Buildprotokollierungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2908c8217070196de1b2d3cd4f1c5f8d8f2868a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160429"
---
# <a name="build-loggers"></a>Buildprotokollierungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Protokollierungen bieten eine Möglichkeit, die Ausgabe des Builds anzupassen und Meldungen, Fehler oder Warnungen als Reaktion auf bestimmte Buildereignisse anzuzeigen. Jede Protokollierung wird als .NET- Klasse implementiert, die die <xref:Microsoft.Build.Framework.ILogger>-Schnittstelle implementiert, die in der Assembly „Microsoft.Build.Framework.dll“ definiert ist.  
  
 Es gibt zwei Ansätze, die Sie verwenden können, wenn Sie eine Protokollierung implementieren:  
  
- Implementieren Sie die <xref:Microsoft.Build.Framework.ILogger>-Schnittstelle direkt.  
  
- Leiten Sie Ihre Klasse von der Hilfsklasse <xref:Microsoft.Build.Utilities.Logger> ab, die in der Assembly „Microsoft.Build.Utilities.dll“ definiert ist. <xref:Microsoft.Build.Utilities.Logger> implementiert <xref:Microsoft.Build.Framework.ILogger> und bietet standardmäßig Implementierungen einiger <xref:Microsoft.Build.Framework.ILogger>-Elemente.  
  
  In diesem Thema wird erläutert, wie Sie eine einfache Protokollierung schreiben, die von <xref:Microsoft.Build.Utilities.Logger> abgeleitet ist und Meldungen in der Konsole als Reaktion auf bestimmte Buildereignisse anzeigt.  
  
## <a name="registering-for-events"></a>Registrieren für Ereignisse  
 Der Zweck einer Protokollierung ist das Sammeln von Informationen über den Fortschritt des Builds gemäß Meldung durch die Build-Engine und Berichten dieser Informationen auf nützliche Weise. Alle Protokollierungen müssen die <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>-Methode überschreiben, wo sich die Protokollierung für Ereignisse registriert. In diesem Beispiel registriert sich die Protokollierung für die <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>-, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>- und <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>-Ereignisse.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#2](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#2)]  
  
## <a name="responding-to-events"></a>Reagieren auf Ereignisse  
 Weil die Protokollierung nun für bestimmte Ereignisse registriert ist, muss sie diese Ereignisse bei ihrem Auftreten behandeln. Für die <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>- und <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>-Ereignisse schreibt die Protokollierung einfach einen kurzen Ausdruck und den Namen der am Ereignis beteiligten Projektdatei. Alle Meldungen aus der Protokollierung werden im Konsolenfenster ausgegeben.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#3](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#3)]  
  
## <a name="responding-to-logger-verbosity-values"></a>Reagieren auf Ausführlichkeitswerte der Protokollierung  
 In einigen Fällen möchten Sie möglicherweise nur Informationen von einem Ereignis protokollieren, wenn der MSBuild.exe **/verbosity** -Schalter einen bestimmten Wert enthält. In diesem Beispiel protokolliert der <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> Ereignishandler nur dann eine Meldung, wenn die <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> Eigenschaft, die durch den Schalter **/verbosity** festgelegt wird, gleich ist <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed` .  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#4](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#4)]  
  
## <a name="specifying-a-logger"></a>Festlegen einer Protokollierung  
 Nachdem die Protokollierung in eine Assembly kompiliert worden ist, müssen Sie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] mitteilen, diese Protokollierung während der Builderstellung zu verwenden. Dies erfolgt mithilfe des **/Logger** -Schalters mit MSBuild.exe. Weitere Informationen zu den für MSBuild.exe verfügbaren Switches finden Sie unter [Befehlszeilen Referenz](../msbuild/msbuild-command-line-reference.md).  
  
 Die folgende Befehlszeile erstellt das Projekt `MyProject.csproj` und verwendet die in `SimpleLogger.dll` implementierte Protokollierungsklasse. Der Schalter **/nologo** blendet das Banner und die Copyright Meldung aus, und der Schalter **/noconsolelogger** deaktiviert die standardmäßige Konsolen Protokollierung [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll  
```  
  
 Die folgende Befehlszeile erstellt das Projekt mit der gleichen Protokollierung, jedoch mit dem `Verbosity`-Grad `Detailed`.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll /verbosity:Detailed  
```  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
 Das folgende Beispiel enthält den vollständigen Code für die Protokollierung.  
  
### <a name="code"></a>Code  
 [!code-csharp[msbuild_SimpleConsoleLogger#1](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#1)]  
  
### <a name="comments"></a>Kommentare  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
 Das folgende Beispiel zeigt das Implementieren einer Protokollierung, die das Protokoll in eine Datei schreibt, anstatt es im Konsolenfenster anzuzeigen.  
  
### <a name="code"></a>Code  
 [!code-csharp[msbuild_BasicLogger#1](../snippets/csharp/VS_Snippets_Misc/msbuild_BasicLogger/CS/msbuild_BasicLogger.cs#1)]  
  
### <a name="comments"></a>Kommentare  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [MSBuild-Konzepte](../msbuild/msbuild-concepts.md)
