---
title: Protokollierung in einer Multiprozessorumgebung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35184f6ef724a9f0e803a10c9bda2c6981313ed6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205971"
---
# <a name="logging-in-a-multi-processor-environment"></a>Protokollierung in einer Multiprozessorumgebung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Fähigkeit von MSBuild 3.5, mehrere Prozessoren zu verwenden, kann die Dauer der Projekterstellung deutlich verringern, jedoch auch die Komplexität der Protokollierung erhöhen. In einer Umgebung mit nur einem Prozessor kann die Protokollierung eingehende Ereignisse, Meldungen, Warnungen und Fehler auf vorhersehbare, geordnete Weise verarbeiten. In einer Umgebung mit mehreren Prozessoren können jedoch Ereignisse aus verschiedenen Quellen gleichzeitig und ungeordnet eintreffen. MSBuild bietet eine neue mehrprozessorfähige Protokollierung und ermöglicht die Erstellung benutzerdefinierter „weiterleitender Protokollierungen“.  
  
## <a name="logging-multiple-processor-builds"></a>Protokollierung von Multiprozessorbuilds  
 Wenn Sie ein oder mehrere Projekte in einer Umgebung mit mehreren Prozessoren oder mehreren Prozessorkernen erstellen, werden die MSBuild-Buildereignisse für alle Projekte gleichzeitig erzeugt. Angenommen, die Protokollierung empfängt eine große Menge von Ereignisdaten gleichzeitig oder ohne bestimmte Reihenfolge. Dies kann die Protokollierung überlasten und zu einer erhöhten Buildzeit, falschen Protokollierungsausgaben oder sogar einem beschädigten Build führen. Um dieses Problem zu beheben, kann die MSBuild-Protokollierung ungeordnete Ereignisse verarbeiten und Ereignisse ihren Quellen zuordnen.  
  
 Sie können die Protokollierungseffizienz noch erhöhen, indem Sie eine benutzerdefinierte Weiterleitungsprotokollierung erstellen. Eine benutzerdefinierte Weiterleitungsprotokollierung funktioniert wie ein Filter, der Ihnen vor der Builderstellung ermöglicht, die zu überwachenden Ereignisse auszuwählen. Durch die Verwendung einer benutzerdefinierten Weiterleitungsprotokollierung wird vermieden, dass die Protokollierung durch nicht benötigte Ereignisse überlastet, die Protokolle mit überflüssigen Daten gefüllt oder die Builderstellung verlangsamt wird.  
  
### <a name="central-logging-model"></a>Zentrales Protokollierungsmodell  
 MSBuild verwendet für Multiprozessorbuilds ein "zentrales Protokollierungsmodell". Im zentralen Protokollierungsmodell fungiert eine Instanz von MSBuild.exe als der primäre Buildprozess oder "zentrale Knoten". Sekundäre Instanzen von MSBuild.exe oder "sekundäre Knoten" werden an den zentralen Knoten angefügt. Auf ILogger basierende Protokollierungen, die an den zentralen Knoten angehängt sind, werden als "zentrale Protokollierungen" bezeichnet; an sekundäre Knoten angehängte Protokollierungen werden als "sekundäre Protokollierungen" bezeichnet.  
  
 Bei der Builderstellung leiten die sekundären Protokollierungen ihre Ereignisdaten an die zentralen Protokollierungen weiter. Da Ereignisse an mehreren sekundären Knoten auftreten, treffen die Daten gleichzeitig, jedoch überlappend beim zentralen Knoten ein. Um Ereignis-zu-Projekt-Verweise und Ereignis-zu-Ziel-Verweise zu lösen, enthalten die Ereignisargumente zusätzliche Informationen zum Buildereigniskontext.  
  
 Obwohl nur <xref:Microsoft.Build.Framework.ILogger> von der zentralen Protokollierung implementiert werden muss, wird empfohlen, auch <xref:Microsoft.Build.Framework.INodeLogger> zu implementieren, wenn die zentrale Protokollierung mit der Anzahl der Knoten, die am Build beteiligt sind, initialisiert werden soll. Die folgende Überladung der <xref:Microsoft.Build.Framework.ILogger.Initialize%2A>-Methode wird aufgerufen, wenn die Engine die Protokollierung initialisiert:  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### <a name="distributed-logging-model"></a>Verteiltes Protokollierungsmodell  
 Beim zentralen Protokollierungsmodell kann ein zu hohes Aufkommen von eingehenden Meldungen wie bei der gleichzeitigen Erstellung mehrerer Projekte zu einer Überlastung des zentralen Knotens führen, wodurch das System belastet und die Buildleistung reduziert wird.  
  
 Um dieses Problem zu verringern, stellt MSBuild auch ein "verteiltes Protokollierungsmodell" bereit, mit dem das zentrale Protokollierungsmodell durch die Möglichkeit erweitert wird, Weiterleitungsprotokollierungen zu erstellen. Eine Weiterleitungsprotokollierung wird an einen sekundären Knoten angefügt und empfängt eingehende Buildereignisse von diesem Knoten. Die Weiterleitungsprotokollierung ist eine normale Protokollierung, außer dass sie Ereignisse filtern kann und nur die gewünschten Ereignisse an den zentralen Knoten weiterleitet. Hierdurch wird das Meldungsaufkommen am zentralen Knoten verringert und so eine bessere Leistung erzielt.  
  
 Sie können Weiterleitungsprotokollierungen erstellen, indem Sie die <xref:Microsoft.Build.Framework.IForwardingLogger>-Schnittstelle implementieren, die von <xref:Microsoft.Build.Framework.ILogger> abgeleitet ist. Die Schnittstelle wird wie folgt definiert:  
  
```  
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 Um Ereignisse in einer Weiterleitungsprotokollierung weiterzuleiten, rufen Sie die <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A>-Methode der <xref:Microsoft.Build.Framework.IEventRedirector>-Schnittstelle auf. Übergeben Sie entsprechende <xref:Microsoft.Build.Framework.BuildEventArgs> oder eine Ableitung als Parameter.  
  
 Weitere Informationen finden Sie unter [Erstellen von Weiterleitungs Protokollierungen](../msbuild/creating-forwarding-loggers.md).  
  
### <a name="attaching-a-distributed-logger"></a>Anfügen einer verteilten Protokollierung  
 Verwenden Sie zum Anfügen einer verteilten Protokollierung in einem Befehlszeilenbuild den `/distributedlogger`-Schalter (abgekürzt `/dl`). Das Format zum Angeben der Namen von Protokollierungstypen und -klassen ist mit denen für den `/logger`-Schalter identisch, mit der Ausnahme, dass eine verteilte Protokollierung aus zwei Protokollierungsklassen besteht: eine Weiterleitungsprotokollierung und eine zentrale Protokollierung. Nachfolgend ist ein Beispiel für eine verteilte Protokollierung aufgeführt:  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 Ein Sternchen (*) trennt die beiden Protokollierungsnamen im `/dl`-Schalter.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Buildprotokollierungen](../msbuild/build-loggers.md)   
 [Erstellen von Weiterleitungs Protokollierungen](../msbuild/creating-forwarding-loggers.md)
