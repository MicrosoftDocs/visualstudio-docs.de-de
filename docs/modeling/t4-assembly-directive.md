---
title: T4-Assemblydirektive
description: Erfahren Sie, dass die Assembly-Direktive in einer Visual Studio-Entwurfszeit-Textvorlage eine Assembly lädt, sodass der Vorlagen Code seine Typen verwenden kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0d214764e8067e1165eeacc044bddc1994230562
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899674"
---
# <a name="t4-assembly-directive"></a>T4-Assemblydirektive

In einer Visual Studio-Textvorlage für die Entwurfszeit `assembly` lädt die-Direktive eine Assembly, sodass der Vorlagen Code seine Typen verwenden kann. Der Effekt ähnelt dem Hinzufügen eines Assemblyverweises in einem Visual Studio-Projekt.

 Eine allgemeine Übersicht über das Schreiben von Textvorlagen finden Sie unter [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> Die `assembly`-Anweisung ist in einer Laufzeitvorlage (vorverarbeiteten Vorlage) nicht erforderlich. Fügen Sie stattdessen die erforderlichen Assemblys zu den **verweisen** Ihres Visual Studio-Projekts hinzu.

## <a name="using-the-assembly-directive"></a>Verwenden der Assemblyanweisung
 Die Syntax der Anweisung lautet wie folgt:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Folgende Optionen stehen zum Angeben des Assemblynamens zur Verfügung:

- Der starke Name einer Assembly im GAC, z. B. `System.Xml.dll`. Sie können auch das lange Formular verwenden, z. B. `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Weitere Informationen finden Sie unter <xref:System.Reflection.AssemblyName>.

- Absoluter Pfad der Assembly

  Sie können die `$(variableName)` -Syntax verwenden, um auf die Visual Studio `$(SolutionDir)` -Variablen, z. b., und `%VariableName%` auf Umgebungsvariablen zu verweisen. Beispiel:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 Die assembly-Anweisung hat in einer vorverarbeiteten Textvorlage keinerlei Auswirkungen. Fügen Sie stattdessen die erforderlichen Verweise in den **Verweis** Bereich Ihres Visual Studio-Projekts ein. Weitere Informationen finden Sie unter [Laufzeittextgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="standard-assemblies"></a>Standardassemblys
 Die folgenden Assemblys werden automatisch geladen, damit Sie keine Assemblyanweisungen dafür schreiben müssen:

- `Microsoft.VisualStudio.TextTemplating.1*.dll`

- `System.dll`

- `WindowsBase.dll`

  Wenn Sie eine benutzerdefinierte Direktive verwenden, lädt der Direktivenprozessor möglicherweise zusätzliche Assemblys. Wenn Sie z. B. Vorlagen für eine domänenspezifische Sprache (DSL) schreiben, müssen Sie keine Assemblyanweisungen für die folgenden Assemblys schreiben:

- `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`

- `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`

- `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`

- Die Assembly mit der DSL.

## <a name="using-project-properties-in-both-msbuild-and-visual-studio"></a><a name="msbuild"></a> Verwenden von Projekteigenschaften in MSBuild und Visual Studio
 Visual Studio-Makros wie $ (SolutionDir) funktionieren nicht in MSBuild. Wenn Sie Vorlagen im Buildcomputer transformieren möchten, müssen Sie dies mithilfe von Projekteigenschaften tun.

 Bearbeiten Sie die CSPROJ- oder VBPROJ-Datei, und definieren Sie eine Projekteigenschaft. In folgendem Beispiel wird eine Eigenschaft mit dem Namen `myLibFolder` definiert:

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 Nun können Sie die Projekteigenschaft in Textvorlagen verwenden, die sowohl in Visual Studio als auch in MSBuild ordnungsgemäß transformiert werden:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
```

## <a name="see-also"></a>Weitere Informationen

- [T4-Include-Direktive](../modeling/t4-include-directive.md)
