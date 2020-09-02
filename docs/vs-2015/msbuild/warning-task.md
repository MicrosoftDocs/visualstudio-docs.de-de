---
title: Warnungsaufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: adbddc2fb36e5036e535dfc1049945187fe14ed0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62558488"
---
# <a name="warning-task"></a>Warning-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Protokolliert während eines Builds eine Warnung, die auf einer ausgewerteten Bedingungsanweisung basiert  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter des `Warning`-Tasks beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`Code`|Optionaler `String`-Parameter.<br /><br /> Der Warncode, der der Warnung zugeordnet werden soll.|  
|`File`|Optionaler `String`-Parameter.<br /><br /> Gibt die relevante Datei an, falls vorhanden. Wenn keine Datei angegeben wird, wird die Datei verwendet, die die Warnungsaufgabe enthält.|  
|`HelpKeyword`|Optionaler `String`-Parameter.<br /><br /> Das der Warnung zuzuordnende Hilfeschlüsselwort.|  
|`Text`|Optionaler `String`-Parameter.<br /><br /> Der Warnungstext, den [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] protokolliert, wenn der `Condition`-Parameter `true` ergibt.|  
  
## <a name="remarks"></a>Hinweise  
 Die `Warning`-Aufgabe ermöglicht es [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projekten, zu prüfen, ob eine erforderliche Konfiguration oder Eigenschaft vorhanden ist, bevor Sie mit dem nächsten Schritt des Buildvorgangs fortfahren.  
  
 Wenn der `Condition`-Parameter der `Warning`-Aufgabe `true` ergibt, wird der Wert des `Text`-Parameters protokolliert und der Build weiter ausgeführt. Wenn kein `Condition`-Parameter vorhanden ist, wird der Warnungstext protokolliert. Weitere Informationen zur Protokollierung finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Mithilfe des folgenden Codebeispiels können Sie nach Eigenschaften suchen, die in der Befehlszeile festgelegt sind. Wenn keine Eigenschaften festgelegt sind, löst das Projekt ein Warnungsereignis aus und protokolliert den Wert des `Text`-Parameters der `Warning`-Aufgabe.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Referenz zum Projektdatei Schema](../msbuild/msbuild-project-file-schema-reference.md)
