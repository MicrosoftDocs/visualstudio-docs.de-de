---
title: Choose-Element (MSBuild) | Microsoft-Dokumentation
description: Verwenden Sie das MSBuild-Element „Choose“, um untergeordnete Elemente auszuwerten und eine Gruppe von ItemGroup- oder PropertyGroup-Elementen für die Auswertung auszuwählen.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Choose
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ad83bc215c70389dbb9383e1cb9562b99be7106
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796627"
---
# <a name="choose-element-msbuild"></a>Choose-Element (MSBuild)

Bewertet untergeordnete Elemente, um einen Satz von auszuwertenden `ItemGroup`-Elementen und/oder `PropertyGroup`-Elementen auszuwählen.

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

## <a name="syntax"></a>Syntax

```xml
<Choose>
    <When Condition="'StringA'=='StringB'">... </When>
    <Otherwise>... </Otherwise>
</Choose>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

 Keine

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Otherwise](../msbuild/otherwise-element-msbuild.md)|Optionales Element.<br /><br /> Gibt den Codeblock mit `PropertyGroup`- und `ItemGroup`-Elementen an, die ausgewertet werden sollen, wenn die Bedingungen aller `When`-Elemente als `false` ausgewertet werden. Ein `Choose`-Element kann kein oder ein `Otherwise`-Element enthalten, und es muss das letzte Element sein.|
|[When](../msbuild/when-element-msbuild.md)|Erforderliches Element.<br /><br /> Gibt einen möglichen Codeblock an, den das `Choose`-Element auswählen kann. Ein `Choose`-Element kann ein oder mehrere `When`-Elemente enthalten.|

### <a name="parent-elements"></a>Übergeordnete Elemente

| Element | Beschreibung |
| - | - |
| [Otherwise](../msbuild/otherwise-element-msbuild.md) | Gibt den Codeblock an, der ausgeführt wird, wenn die Bedingungen aller `When`-Elemente als `false` ausgewertet werden. |
| [Projekt](../msbuild/project-element-msbuild.md) | Erforderliches Stammelement einer MSBuild-Projektdatei. |
| [When](../msbuild/when-element-msbuild.md) | Gibt einen möglichen Codeblock an, den das `Choose`-Element auswählen kann. |

## <a name="remarks"></a>Bemerkungen

 Die Elemente `Choose`, `When` und `Otherwise` werden zusammen verwendet, um eine Möglichkeit zu bieten, einen Codeabschnitt aus einer Reihe von möglichen Alternativen zur Ausführung auszuwählen. Weitere Informationen finden Sie unter [Conditional Constructs (Bedingte Konstrukte)](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a>Beispiel

 Das folgende Projekt verwendet das `Choose`-Element, um auszuwählen, welche Gruppe von Eigenschaftswerten in den `When`-Elementen festgelegt werden soll. Wenn die `Condition`-Attribute beider `When`-Elemente `false` ergeben, werden die Eigenschaftswerte im `Otherwise`-Element festgelegt.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='debug' ">
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <DebugType>full</DebugType>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\Debug\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
            <ItemGroup>
                <Compile Include="UnitTesting\*.cs" />
                <Reference Include="NUnit.dll" />
            </ItemGroup>
        </When>
        <When Condition=" '$(Configuration)'=='retail' ">
            <PropertyGroup>
                <DebugSymbols>false</DebugSymbols>
                <Optimize>true</Optimize>
                <OutputPath>.\bin\Release\</OutputPath>
                <DefineConstants>TRACE</DefineConstants>
            </PropertyGroup>
        </When>
        <Otherwise>
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\$(Configuration)\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
        </Otherwise>
    </Choose>
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [Bedingte Konstrukte](../msbuild/msbuild-conditional-constructs.md)
- [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)
