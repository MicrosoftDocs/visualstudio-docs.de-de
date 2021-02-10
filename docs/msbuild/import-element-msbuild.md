---
title: Import-Element (MSBuild) | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild das Import-Element verwendet, um die Inhalte einer Projektdatei in eine andere Projektdatei zu importieren.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c3a0d22019a0c7722b135392c53c7f9bfbcaab69
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914109"
---
# <a name="import-element-msbuild"></a>Import-Element (MSBuild)

Importiert die Inhalte einer Projektdatei in eine andere Projektdatei.

\<Project>
\<Import>

## <a name="syntax"></a>Syntax

```xml
<Import Project="ProjectPath"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|`Project`|Erforderliches Attribut.<br /><br /> Der Pfad der zu importierenden Projektdatei. Der Pfad kann Platzhalter enthalten. Die entsprechenden Dateien werden in sortierter Reihenfolge importiert. Mit dieser Funktion können Sie Code einem Projekt hinzufügen, indem Sie einfach die Codedatei einem Verzeichnis hinzufügen.|
|`Condition`|Optionales Attribut.<br /><br /> Eine auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|
|`Sdk`| Optionales Attribut.<br /><br /> Verweist auf ein Projekt-SDK.|

### <a name="child-elements"></a>Untergeordnete Elemente

 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

| Element | Beschreibung |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Erforderliches Stammelement einer MSBuild-Projektdatei. |
| [ImportGroup](../msbuild/importgroup-element.md) | Enthält eine Sammlung von `Import` -Elementen, die unter einer optionalen Bedingung gruppiert sind. |

## <a name="remarks"></a>Bemerkungen

 Mithilfe des `Import` -Elements können Sie Code wiederverwenden, der in vielen Projektdateien verwendet wird. Dies erleichtert die Verwaltung des Codes, da jedes von Ihnen ausgeführte Update für den freigegebenen Code an alle Projekte weitergegeben wird, die ihn importieren.

 Gemäß Konvention werden freigegebene importierte Projektdateien als *TARGETS*-Dateien gespeichert, es handelt sich jedoch um MSBuild-Standardprojektdateien. MSBuild hindert Sie nicht daran, ein Projekt zu importieren, das eine andere Dateinamenerweiterung aufweist. Es wird jedoch empfohlen, aus Konsistenzgründen die Erweiterung *TARGETS* zu verwenden.

 Relative Pfade in importierten Projekten werden relativ zum Verzeichnis des importierenden Projekts interpretiert (mit einigen wenigen Ausnahmen, die weiter unten beschrieben werden). Wenn eine Projektdatei in verschiedene Projektdateien an unterschiedliche Speicherorte importiert wird, werden daher die relativen Pfade in der importierten Projektdatei unterschiedlich für jedes importierte Projekt interpretiert. Dazu gibt es zwei Ausnahmen: In `Import`-Elementen wird der Pfad immer relativ zum Projekt interpretiert, das das `Import`-Element enthält. `UsingTask` interpretiert den relativen Pfad für das `AssemblyFile`-Attribut immer relativ zur Datei, die das `UsingTask`-Element enthält.

 Allen für MSBuild reservierten Eigenschaften, die sich auf die Projektdatei beziehen, z. B. `MSBuildProjectDirectory` und `MSBuildProjectFile`, und auf die in einem importierten Projekt verwiesen wird, werden basierend auf der importierenden Projektdatei Werte zugewiesen.

 Wenn das importierte Projekt über kein `DefaultTargets` -Attribut verfügt, werden importierte Projekte in der Reihenfolge untersucht, in der Sie importiert wurden und der Wert des ersten gefundenen `DefaultTargets` -Attributs wird daraufhin verwendet. Wenn beispielsweise ProjektA ProjektB und ProjektC (in dieser Reihenfolge) importiert, und ProjectB importiert ProjektD, prüft MSBuild zuerst, ob `DefaultTargets` in ProjektA angegeben ist, durchsucht dann ProjektB und ProjektD und schließlich ProjektC.

 Das Schema eines importierten Projekts ist identisch mit dem Schema eines Standardprojekts. Obwohl MSBuild möglicherweise ein importiertes Projekt erstellen kann, ist es unwahrscheinlich, da ein importiertes Projekt normalerweise keine Informationen enthält, wie Eigenschaften festzulegen sind oder die Reihenfolge, in der Ziele ausgeführt werden. Das importierte Projekt ist abhängig vom Projekt in das es importiert wird, um diese Information bereitzustellen.

## <a name="wildcards"></a>Platzhalter

 In .NET Framework 4 erlaubt MSBuild Platzhalter im Attribut „Projekt“. Wenn Platzhalter vorhanden sind, werden alle gefundenen Übereinstimmungen (für die Reproduzierbarkeit) sortiert und dann werden sie in dieser Reihenfolge importiert, so als ob diese explizit festgelegt wurde.

 Dies ist hilfreich, wenn Sie einen Erweiterungspunkt zur Verfügung stellen möchten, sodass jemand anderes eine Datei importieren kann, ohne dass Sie explizit der zu importierenden Datei den Dateinamen hinzufügen müssen. Zu diesem Zweck enthält *Microsoft.Common.Targets* die folgende Zeile am Anfang der Datei.

```xml
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>
```

## <a name="example"></a>Beispiel

 Das folgende Beispiel zeigt ein Projekt, das über mehrere Elemente und Eigenschaften verfügt und eine allgemeine Projektdatei importiert.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <resourcefile>Strings.resx</resourcefile>

        <compiledresources>
            $(O)\$(MSBuildProjectName).Strings.resources
        </compiledresources>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs" />

        <Reference Include="System" />
        <Reference Include="System.Data" />
    </ItemGroup>

    <Import Project="$(CommonLocation)\General.targets" />
</Project>
```

## <a name="see-also"></a>Siehe auch

- [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)
- [How to: Verwenden desselben Ziels in mehreren Projektdateien](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
