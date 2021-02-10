---
title: ProjectExtensions-Element (MSBuild) | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Element „MSBuildProjectExtensions“, durch das MSBuild-Projektdateien nicht MSBuild-bezogene Informationen enthalten können.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b7b186fa1d7a5ecb8297045d4b0bbb111d136d1d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905284"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions-Element (MSBuild)

Ermöglicht es, dass MSBuild-Projektdateien nicht MSBuild-bezogene Informationen enthalten. Der gesamte Inhalt eines `ProjectExtensions`-Elements wird von MSBuild ignoriert.

 \<Project> \<ProjectExtensions>

## <a name="syntax"></a>Syntax

```xml
<ProjectExtensions>
    Non-MSBuild information to include in file.
</ProjectExtensions>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

 Keine

### <a name="child-elements"></a>Untergeordnete Elemente

 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

| Element | Beschreibung |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Erforderliches Stammelement einer MSBuild-Projektdatei. |

## <a name="remarks"></a>Hinweise

 In einer MSBuild-Datei kann nur ein `ProjectExtensions`-Element verwendet werden.

## <a name="example"></a>Beispiel

 Das folgende Codebeispiel zeigt Informationen aus der IDE, die in einem `ProjectExtensions`-Element gespeichert werden.

```xml
<ProjectExtensions>
    <VSIDE>
        <External>
            <!--
            Raw XML passed to the IDE by an external source
            -->
        </External>
    </VSIDE>
</ProjectExtensions>
```

## <a name="see-also"></a>Siehe auch

- [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
