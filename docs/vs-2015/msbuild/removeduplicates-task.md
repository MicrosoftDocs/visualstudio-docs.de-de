---
title: RemoveDuplicates-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73ad829c86305ff4d9a54025467e262d56e24dbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159240"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entfernt doppelte Elemente aus der angegebenen Elementauflistung  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `RemoveDuplicates`-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`Filtered`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält eine Elementauflistung, aus der alle doppelten Elemente entfernt wurden|  
|`Inputs`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Die Elementauflistung, aus der doppelte Elemente entfernt werden sollen|  
  
## <a name="remarks"></a>Bemerkungen  
 Bei dieser Aufgabe wird die Groß- und Kleinschreibung beachtet, und Elementmetadaten werden beim Ermitteln von Duplikaten nicht verglichen.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden mithilfe der `RemoveDuplicates`-Aufgabe doppelte Elemente aus der `MyItems` -Elementauflistung entfernt. Wenn die Aufgabe abgeschlossen ist, enthält die `FilteredItems`-Elementauflistung ein Element.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile.cs"/>  
        <MyItems Include="MyFile.cs">  
            <Culture>fr</Culture>  
        </MyItems>  
        <MyItems Include="myfile.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)   
 [MSBuild-Konzepte](../msbuild/msbuild-concepts.md)   
 [Aufgaben](../msbuild/msbuild-tasks.md)
