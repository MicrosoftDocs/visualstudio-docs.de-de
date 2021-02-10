---
title: XmlPeek-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe der Aufgabe „XmlPeek“ die Werte aus einer XML-Datei gemäß Angabe in einer XPath-Abfrage zurückgibt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9d387d44ba06bb3a5a8ef5e73e2d8900b356996e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964861"
---
# <a name="xmlpeek-task"></a>XmlPeek-Aufgabe

Gibt die Werte wie von der XPath-Abfrage angegeben aus einer XML-Datei zurück

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `XmlPeek` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`Namespaces`|Optionaler `String`-Parameter.<br /><br /> Gibt die Namespaces für die Präfixe der XPath-Abfrage an|
|`Query`|Optionaler `String`-Parameter.<br /><br /> Gibt die XPath-Abfrage an|
|`Result`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Ergebnisse, die von dieser Aufgabe zurückgegeben werden|
|`XmlContent`|Optionaler `String`-Parameter.<br /><br /> Gibt die XML-Eingabe als Zeichenfolge an|
|`XmlInputPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt die XML-Eingabe als Dateipfad an|

## <a name="remarks"></a>Hinweise

 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die XML-Datei `settings.config`:

```xml
<appSettings>
  <add key="ProjectFolder" value="S1" />
</appSettings>
```

Verwenden Sie in diesem Beispiel zum Lesen von `value` etwa folgenden Code:

```xml
<Target Name="BeforeBuild">
    <XmlPeek XmlInputPath="settings.config" Query="appSettings/add[@key='ProjectFolder']/@value">
        <Output TaskParameter="Result" ItemName="value" />
    </XmlPeek>
    <Message Text="Using project folder @(value)." Importance="high" />
    <PropertyGroup>
        <ProjectFolder>@(value)</ProjectFolder>
    </PropertyGroup>
    <ItemGroup>
        <Compile Include="Projects\$(ProjectFolder)\Controls\Control1.ascx.cs">
            <SubType>ASPXCodeBehind</SubType>
        </Compile>
    </ItemGroup>
</Target>
```

Bei XML-Namespaces verwenden Sie den Parameter `Namespaces`, wie im folgenden Beispiel gezeigt. Mit der XML-Eingabedatei `XMLFile1.xml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<class AccessModifier='public' Name='test' xmlns:s='http://nsurl'>
  <s:variable Type='String' Name='a'>This</s:variable>
  <s:variable Type='String' Name='b'>is</s:variable>
  <s:variable Type='String' Name='c'>Sparta!</s:variable>
  <method AccessModifier='public static' Name='GetVal' />
</class>
```

Und dem folgenden `Target` in einer Projektdatei definiert:

```xml
  <Target Name="TestPeek" BeforeTargets="Build">
    <!-- Find the Name attributes -->
    <XmlPeek XmlInputPath="XMLFile1.xml"
             Query="//s:variable/@Name"
             Namespaces="&lt;Namespace Prefix='s' Uri='http://nsurl' /&gt;">
      <Output TaskParameter="Result" ItemName="value1" />
    </XmlPeek>
    <Message Text="@(value1)"/>
    <!-- Find 'variable' nodes (XPath query includes ".") -->
    <XmlPeek XmlInputPath="XMLFile1.xml"
             Query="//s:variable/."
             Namespaces="&lt;Namespace Prefix='s' Uri='http://nsurl' /&gt;">
      <Output TaskParameter="Result" ItemName="value2" />
    </XmlPeek>
    <Message Text="@(value2)"/>
  </Target>
```

Die Ausgabe enthält Folgendes aus dem Ziel von `TestPeek`:

```output
  TestPeek output:
  a;b;c
  <s:variable Type="String" Name="a" xmlns:s="http://nsurl">This</s:variable>;<s:variable Type="String" Name="b" xmlns:s="http://nsurl">is</s:variable>;<s:variable Type="String" Name="c" xmlns:s="http://nsurl">Sparta!</s:variable>
```

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [XPath-Abfragesyntax](https://wikipedia.org/wiki/XPath)
