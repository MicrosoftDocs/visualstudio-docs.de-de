---
title: XslTransformation-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe der Aufgabe „XslTransformation“ eine XML-Eingabe unter Verwendung von XSLT transformiert und an ein Ausgabegerät oder eine Ausgabedatei ausgibt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f779fc5d222fdd0985adef203f0bb20fc601a429
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847945"
---
# <a name="xsltransformation-task"></a>XslTransformation-Aufgabe

Transformiert eine XML-Eingabe mithilfe von XSLT oder kompiliertem XSLT-Code und gibt an ein Ausgabegerät oder eine Ausgabedatei aus

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `XslTransformation` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`OutputPaths`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die Ausgabedateien für die XML-Transformation an|
|`Parameters`|Optionaler `String`-Parameter.<br /><br /> Gibt die Parameter für das XSLT-Eingabedokument an  Stellt unformatierte XML-Daten bereit, die jeden Parameter als `<Parameter Name="" Value="" Namespace="" />` enthalten.|
|`XmlContent`|Optionaler `String`-Parameter.<br /><br /> Gibt die XML-Eingabe als Zeichenfolge an|
|`XmlInputPaths`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die XML-Eingabedateien an|
|`XslCompiledDllPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt den kompilierten XSLT-Code an|
|`XslContent`|Optionaler `String`-Parameter.<br /><br /> Gibt die XSLT-Eingabe als Zeichenfolge an|
|`XslInputPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt die XSLT-Eingabedatei an|

## <a name="remarks"></a>Hinweise

 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die XML-Datei `$(XmlInputFileName)` durch die XSL-Transformationsdatei *transform.xslt* geändert. Die transformierte XML-Datei wird in `$(IntermediateOutputPath)output.xml` geschrieben. Die XSL-Transformationsdatei verwendet `$(Parameter1)` als Eingabeparameter.

```xml
    <XslTransformation XslInputPath="transform.xslt"
                       XmlInputPaths="$(XmlInputFileName)"
                       OutputPaths="$(IntermediateOutputPath)output.xml"
                       Parameters="&lt;Parameter Name='Parameter1' Value='$(Parameter1)'/&gt;"/>
```

## <a name="see-also"></a>Weitere Informationen

- [XSLT-Parameter](/dotnet/standard/data/xml/xslt-parameters)
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
