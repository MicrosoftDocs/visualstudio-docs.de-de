---
title: CreateItem-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateItem
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateItem task [MSBuild]
- MSBuild, CreateItem task
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 758491a068fe2c2c7318717f5481b41839c49a3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841304"
---
# <a name="createitem-task"></a>CreateItem-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Füllt Elementauflistungen mit den Eingabeelementen aus. Dadurch können Elemente aus einer Liste in eine andere kopiert werden.  
  
> [!NOTE]
> Diese Aufgabe ist veraltet. Seit .NET Framework 3.5 können Elementgruppen innerhalb von [Ziel](../msbuild/target-element-msbuild.md)-Elementen platziert werden. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).  
  
## <a name="attributes"></a>Attribute  
 In der folgenden Tabelle werden die Parameter der `CreateItem`-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`AdditionalMetadata`|Optionaler `String`-Arrayparameter.<br /><br /> Gibt zusätzliche Metadaten an, die an die Ausgabeelemente angefügt werden sollen.  Geben Sie den Metadatennamen und -wert für das Element mit der folgenden Syntax an:<br /><br /> *MetadataName* `=` *MetadataValue*<br /><br /> Mehrere Metadaten-Name/Wert-Paare sollten mit einem Semikolon getrennt werden. Wenn entweder der Name oder der Wert ein Semikolon oder andere Sonderzeichen enthält, müssen sie mit einem Escapezeichen versehen werden. Weitere Informationen finden Sie unter Gewusst [wie: Escapezeichen für Sonderzeichen in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).|  
|`Exclude`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Gibt die Elemente an, die aus der Ausgabeelementauflistung ausgeschlossen werden sollen. Dieser Parameter kann Platzhalter enthalten. Weitere Informationen finden Sie unter [Items](../msbuild/msbuild-items.md) und Gewusst [wie: Ausschließen von Dateien aus dem Build](../msbuild/how-to-exclude-files-from-the-build.md).|  
|`Include`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>-`[]`-Parameter<br /><br /> Gibt die Elemente an, die in die Ausgabeelementauflistung einbezogen werden sollen. Dieser Parameter kann Platzhalter enthalten.|  
|`PreserveExistingMetadata`|Optionaler `Boolean`-Parameter.<br /><br /> Bei `True` gelten nur die zusätzlichen Metadaten, wenn sie nicht bereits vorhanden sind.|  
  
## <a name="remarks"></a>Bemerkungen  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird eine neue Elementauflistung namens `MySourceItemsWithMetadata` aus der Elementauflistung `MySourceItems` erstellt. Die `CreateItem`-Aufgabe füllt die neuen Elementauflistungen mit den Elementen im `MySourceItems`-Element auf. Anschließend fügt es jedem Element in der neuen Sammlung einen zusätzlichen Metadateneintrag namens `MyMetadata` mit dem Wert `Hello` hinzu.  
  
 Nachdem die Aufgabe ausgeführt wurde, enthält die `MySourceItemsWithMetadata`-Elementauflistung die Elemente `file1.resx` und `file2.resx`, und beide verfügen über Metadateneinträge für `MyMetadata`. Die `MySourceItems`-Elementauflistung bleibt unverändert.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceItems Include="file1.resx;file2.resx" />  
    </ItemGroup>  
  
    <Target Name="NewItems">  
        <CreateItem  
            Include="@(MySourceItems)"  
            AdditionalMetadata="MyMetadata=Hello">  
           <Output  
               TaskParameter="Include"  
               ItemName="MySourceItemsWithMetadata"/>  
        </CreateItem>  
  
    </Target>  
  
</Project>  
```  
  
 In der folgenden Tabelle wird der Wert des Ausgabeelements nach der Ausführung der Aufgabe beschrieben. Elementmetadaten werden in Klammern nach dem Element angezeigt.  
  
|Elementauflistung|Inhalt|  
|---------------------|--------------|  
|`MySourceItemsWithMetadata`|`file1.resx` (`MyMetadata="Hello"`)<br /><br /> `file2.resx` (`MyMetadata="Hello"`)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)   
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)
