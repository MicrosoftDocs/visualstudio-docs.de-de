---
title: Elementmetadaten bei der Batchverarbeitung von Zielen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9dd6c297e00a305fbd1b13cf0fe0bd4a4f151f6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192872"
---
# <a name="item-metadata-in-target-batching"></a>Elementmetadaten bei der Batchverarbeitung von Zielen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] kann eine Abhängigkeitsanalyse für die Ein- und Ausgaben eines Buildziels durchführen. Wenn ermittelt wird, dass die Ein- oder Ausgaben des Ziels auf dem neuesten Stand sind, wird das Ziel übersprungen, und der Build wird fortgesetzt. `Target`-Elemente verwenden die `Inputs`- und `Outputs`-Attribute, um die Elemente festzulegen, die bei der Abhängigkeitsanalyse überprüft werden.  
  
 Wenn ein Ziel eine Aufgabe enthält, die Batchelemente als Eingaben oder Ausgaben verwendet, sollte in den `Inputs`- oder `Outputs`-Attributen des `Target`-Zielelements die Batchverarbeitung genutzt werden, sodass [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Batchelemente übersprungen werden, die bereits auf dem neuesten Stand sind.  
  
## <a name="batching-targets"></a>Batchverarbeitung von Zielen  
 Das folgende Beispiel enthält die Elementliste `Res`, die mithilfe der `Culture`-Elementmetadaten in zwei Batches aufgeteilt wird. Jeder Batch wird der `AL`-Aufgabe übergeben, die jeweils eine Ausgabeassembly erstellt. Durch die Batchverarbeitung von `Outputs`-Attributen des `Target`-Elements kann [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vor dem Ausführen des Ziels ermitteln, ob jeder Batch aktuell ist. Ohne die Batchverarbeitung von Zielen würden beide Elementbatches immer dann von der Aufgabe ausgeführt werden, wenn das Ziel ausgeführt wird.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Res Include="Strings.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Strings.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
    </ItemGroup>  
  
    <Target Name="Build"  
        Inputs="@(Res)"  
        Outputs="%(Culture)\MyApp.resources.dll">  
  
        <AL Resources="@(Res)"  
            TargetType="library"  
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gewusst wie: Inkrementelles Erstellen](../msbuild/how-to-build-incrementally.md)   
 [Batch Verarbeitung](../msbuild/msbuild-batching.md)   
 [Target-Element (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Element Metadaten in der Batch Verarbeitung von Aufgaben](../msbuild/item-metadata-in-task-batching.md)
