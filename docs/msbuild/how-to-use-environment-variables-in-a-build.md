---
title: 'Vorgehensweise: Verwenden von Umgebungsvariablen in einem Build | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie auf Umgebungsvariablen in MSBuild-Projektdateien zugreifen und Umgebungsvariablen verwenden, um Buildoptionen festzulegen, ohne die Projektdatei zu ändern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c7c81f36d37d071593a013067f661451b8916caa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914196"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Vorgehensweise: Verwenden von Umgebungsvariablen in einem Build

Wenn Sie Projekte erstellen, ist es oft erforderlich, Buildoptionen mithilfe der Informationen festzulegen, die sich nicht in der Projektdatei oder in den Dateien befinden, aus denen Ihr Projekt besteht. Diese Informationen werden normalerweise in Umgebungsvariablen gespeichert.

## <a name="reference-environment-variables"></a>Verweisen auf Umgebungsvariablen

 Alle Umgebungsvariablen stehen der Microsoft-Build-Engine (MSBuild)-Projektdatei als Eigenschaften zur Verfügung.

> [!NOTE]
> Wenn das Projekt eine Eigenschaftsdefinition enthält, die denselben Namen wie eine Umgebungsvariable hat, wird der Wert der Umgebungsvariablen von der Eigenschaft im Projekt überschrieben.

#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Verwenden einer Umgebungsvariable in einem MSBuild-Projekt

- Verweisen Sie auf die gleiche Art auf Umgebungsvariablen wie auf eine Variable, die in der Projektdatei deklariert ist. Beispielsweise verweist der folgende Code auf die Umgebungsvariable BIN_PATH:

   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`

  Sie können ein `Condition`-Attribut verwenden, um einen Standardwert für eine Eigenschaft anzugeben, wenn die Umgebungsvariable nicht festgelegt wurde.

#### <a name="to-provide-a-default-value-for-a-property"></a>Gibt den Standardwert für eine Eigenschaft an

- Verwenden eines `Condition`-Attributs für eine Eigenschaft, um einen Wert festzulegen, nur wenn die Eigenschaft keinen Wert hat. Im folgenden Code wird z.B. die `ToolsPath`-Eigenschaft nur auf *c:\tools* festgelegt, wenn die `ToolsPath`-Umgebungsvariable nicht festgelegt ist:

     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`

    > [!NOTE]
    > Eigenschaftennamen unterscheiden keine Groß-/Kleinschreibung, sodass jeweils `$(ToolsPath)` und `$(TOOLSPATH)` auf die gleiche Eigenschaft oder Umgebungsvariable verweisen.

## <a name="example"></a>Beispiel

 Die folgende Projektdatei verwendet Umgebungsvariablen, um den Speicherort von Verzeichnissen anzugeben.

```xml
<Project DefaultTargets="FakeBuild">
    <PropertyGroup>
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">
            C:\Tools
        </ToolsPath>
    </PropertyGroup>
    <Target Name="FakeBuild">
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [MSBuild](../msbuild/msbuild.md)
- [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md)
- [How to: Erstellen identischer Quelldateien mit unterschiedlichen Optionen](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
