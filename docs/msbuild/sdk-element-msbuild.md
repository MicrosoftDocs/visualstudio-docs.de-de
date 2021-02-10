---
title: SDK-Element (MSBuild) | Microsoft-Dokumentation
description: Erfahren Sie mehr über Syntax, Attribute und Elemente für das MSBuild-Element „Sdk“, das auf das SDK einer MSBuild-Projekt verweist.
ms.custom: SEO-VS-2020
ms.date: 01/25/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cd5f66cc6500a3320e0da962985f5b7fff1e86dc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937900"
---
# <a name="sdk-element-msbuild"></a>SDK-Element (MSBuild)

Verweist auf ein MSBuild-Projekt SDK.

 \<Project> \<Sdk>

## <a name="syntax"></a>Syntax

```xml
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|`Name`|Erforderliches Attribut.<br /><br /> Der Name des Projekt-SDK.|
|`Version`|Optionales Attribut.<br /><br /> Die Version des Projekt-SDK.|

### <a name="child-elements"></a>Untergeordnete Elemente

 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

| Element | Beschreibung |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Erforderliches Stammelement einer MSBuild-Projektdatei. |

## <a name="see-also"></a>Weitere Informationen

- [Gewusst wie: Verweis auf ein MSBuild-Projekt-SDK](../msbuild/how-to-use-project-sdk.md)
- [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
