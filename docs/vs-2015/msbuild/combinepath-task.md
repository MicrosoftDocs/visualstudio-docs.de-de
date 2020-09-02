---
title: CombinePath-Aufgabe | Microsoft-Dokumentation
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
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b97714fc707d8f9174a01dcc1fe7b3b59176de2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160381"
---
# <a name="combinepath-task"></a>CombinePath-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kombiniert die angegebenen Pfade zu einem einzigen Pfad.  
  
## <a name="task-parameters"></a>Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der [CombinePath-Aufgabe](../msbuild/combinepath-task.md)beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`BasePath`|Erforderlicher `String` -Parameter.<br /><br /> Der Basispfad, der mit den anderen Pfaden kombiniert werden soll. Der Pfad kann relativ, absolut oder nicht angegeben sein.|  
|`Paths`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Eine Liste einzelner Pfade, die mit BasePath zu einem kombinierten Pfad kombiniert werden können. Pfade können relativ oder absolut sein.|  
|`CombinedPaths`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Der kombinierte Pfad, der durch diese Aufgabe erstellt wurde|  
  
## <a name="remarks"></a>Hinweise  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erfüllen](../msbuild/msbuild-tasks.md)   
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)
