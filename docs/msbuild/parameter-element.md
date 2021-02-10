---
title: Parameter-Element | Microsoft-Dokumentation
description: Erfahren Sie mehr über das MSBuild-Element „Parameter“, das Informationen zu einem bestimmten Parameter für eine Aufgabe enthält, die durch eine UsingTask TaskFactory generiert wird.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 728618a6d9ff174d4d4bf7cdc20516433d06036b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918862"
---
# <a name="parameter-element"></a>Parameter-Element

Enthält Informationen über einen bestimmten Parameter für eine Aufgabe, die von einer `UsingTask` `TaskFactory` generiert wird.  Der Name des Elements ist der Name des Parameters.  Weitere Informationen finden Sie unter [UsingTask-Element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask>
 \<ParameterGroup>
 \<Parameter>

## <a name="syntax"></a>Syntax

```xml
<ParameterGroup ParameterType="SystemType"
    Output="true/false"
    Required="true/false" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|`ParameterType`|Optionales Attribut.<br /><br /> Der .NET-Typ des Parameters, z.B. „`System.String`“.|
|`Output`|Optionales boolesches Attribut.<br /><br /> Wenn `true`, ist dieser Parameter ein Ausgabeparameter für die Aufgabe. In der Standardeinstellung ist der Wert `false`.|
|`Required`|Optionales boolesches Attribut.<br /><br /> Wenn `true`, ist dieser Parameter ein erforderlicher Parameter für die Aufgabe. In der Standardeinstellung ist der Wert `false`.|

### <a name="child-elements"></a>Untergeordnete Elemente

 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Enthält eine optionale Liste von Parametern, die für die Aufgabe vorhanden sein werden, die von `UsingTask` `TaskFactory` generiert wird.|

## <a name="example"></a>Beispiel

 Im folgenden Beispiel wird die Verwendung des `Parameter`-Elements veranschaulicht.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
             ...
</ParameterGroup>
       <Task Evaluate="true">
       ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)
