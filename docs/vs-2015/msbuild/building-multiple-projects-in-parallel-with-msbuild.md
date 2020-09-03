---
title: Paralleles Erstellen von mehreren Projekten mit MSBuild | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f80f0898167de133d78d27d26f97d0ab8ced0b31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75843951"
---
# <a name="building-multiple-projects-in-parallel-with-msbuild"></a>Paralleles Erstellen von mehreren Projekten mit MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können MSBuild verwenden, um mehrere Projekte schneller zu erstellen, indem Sie sie parallel ausführen. Um Builds parallel auszuführen, verwenden Sie die folgenden Einstellungen auf einem Mehrkern- oder Mehrprozessorcomputer:  
  
- den Schalter `/maxcpucount` in einer Eingabeaufforderung  
  
- den <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A>-Aufgabenparameter in einer MSBuild-Aufgabe  
  
> [!NOTE]
> Der Schalter **/verbosity** (**/v**) in einer Befehlszeile kann sich auch auf die Buildleistung auswirken. Die Buildleistung verringert sich möglicherweise, wenn die Ausführlichkeit der Buildprotokollinformationen auf die Einstellung "Detailliert" oder "Diagnose" festgelegt ist, die beide für die Problembehandlung verwendet werden. Weitere Informationen finden Sie unter Abrufen von [buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md) und [Befehlszeilen Referenz](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="maxcpucount-switch"></a>Schalter "/maxcpucount"  
 Wenn Sie den Schalter `/maxcpucount` oder die kurze Form `/m` verwenden, kann MSBuild die angegebene Anzahl von MSBuild.exe-Prozessen erstellen, die parallel ausgeführt werden können. Diese Prozesse werden auch als "Arbeitsprozesse" bezeichnet. Jeder Arbeitsprozess verwendet einen anderen Kern oder Prozessor, soweit verfügbar, um ein Projekt zu der gleichen Zeit zu erstellen wie andere verfügbare Prozessoren. Wenn Sie zum Beispiel diesen Schalter auf den Wert "4" festlegen, erstellt MSBuild vier Arbeitsprozesse zum Erstellen des Projekts.  
  
 Wenn Sie den Schalter `/maxcpucount` verwenden, ohne einen Wert anzugeben, verwendet MSBuild alle Prozessoren des Computers.  
  
 Weitere Informationen zu diesem Switch, der in MSBuild 3,5 eingeführt wurde, finden Sie unter [Befehlszeilen Referenz](../msbuild/msbuild-command-line-reference.md).  
  
 Das folgende Beispiel weist MSBuild an, drei Arbeitsprozesse zu verwenden. Wenn Sie diese Konfiguration verwenden, kann MSBuild drei Projekte gleichzeitig erstellen.  
  
```  
msbuild.exe myproj.proj /maxcpucount:3  
```  
  
## <a name="buildinparallel-task-parameter"></a>BuildInParallel-Aufgabenparameter  
 `BuildInParallel` ist ein optionaler boolescher Parameter für eine [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Aufgabe. Wenn `BuildInParallel` auf `true` (der Standardwert) festgelegt ist, werden mehrere Arbeitsprozesse erzeugt, um so viele Projekte wie möglich gleichzeitig zu erstellen. Damit dies ordnungsgemäß funktioniert, muss der `/maxcpucount`-Schalter auf einen Wert größer 1 festgelegt sein, und das System muss mindestens ein Dualcore-System sein oder über mindestens zwei Prozessoren verfügen.  
  
 Nachfolgend ist ein Beispiel aus microsoft.common.targets aufgeführt, das veranschaulicht, wie der `BuildInParallel`-Parameter festgelegt wird.  
  
```  
<PropertyGroup>  
    <BuildInParallel Condition="'$(BuildInParallel)' ==   
        ''">true</BuildInParallel>  
</PropertyGroup>  
<MSBuild  
    Projects="@(_MSBuildProjectReferenceExistent)"  
    Targets="GetTargetPath"  
    BuildInParallel="$(BuildInParallel)"  
    Properties="%(_MSBuildProjectReferenceExistent.SetConfiguration);   
        %(_MSBuildProjectReferenceExistent.SetPlatform)"  
    Condition="'@(NonVCProjectReference)'!='' and   
        ('$(BuildingSolutionFile)' == 'true' or   
        '$(BuildingInsideVisualStudio)' == 'true' or   
        '$(BuildProjectReferences)' != 'true') and     
        '@(_MSBuildProjectReferenceExistent)' != ''"  
    ContinueOnError="!$(BuildingProject)">  
    <Output TaskParameter="TargetOutputs"   
        ItemName="_ResolvedProjectReferencePaths"/>  
</MSBuild>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden mehrerer Prozessoren zum Erstellen von Projekten](../msbuild/using-multiple-processors-to-build-projects.md)   
 [Schreiben von multiprozessorfähigen Protokollierungen](../msbuild/writing-multi-processor-aware-loggers.md)   
 [Optimieren C++ Build parallelism-Blog](https://blogs.msdn.com/b/visualstudio/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx)
