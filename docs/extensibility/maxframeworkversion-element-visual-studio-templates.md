---
title: Maxframeworkversion-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
description: Erfahren Sie mehr über das maxframeworkversion-Element und wie es die maximale Version des .NET Framework angibt, die für die Vorlage erforderlich ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44345b712f448bd7eedf288d7c58cb4193e1b020
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672424"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Maxframeworkversion-Element (Visual Studio-Vorlagen)

Gibt die maximale Version der .NET Framework an, die für die Vorlage erforderlich ist. Es bestimmt den höchsten Wert, der in der Dropdown Liste **Ziel Framework-Version** des Dialog Felds **Neues Projekt** verfügbar ist. Damit Benutzer eine Framework-Version auswählen können, müssen Sie auch "Requirements [dframeworkversion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) " als minimale .NET Framework Version für die Vorlage angeben.

> [!IMPORTANT]
> Ab Visual Studio 2017 Version 15,6 ist die Dropdown Liste **Ziel Framework-Version** kein Filter für angezeigte Vorlagen im Abschnitt **Vorlagen** des Dialog Felds **Neues Projekt** . Stattdessen fungiert die Dropdown Liste **Ziel Framework-Version** als frameworkauswahl für die ausgewählte Vorlage.

 \<VSTemplate> \<TemplateData>
 \<MaxFrameworkVersion>

## <a name="syntax"></a>Syntax

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie Sie im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Der Text muss die höchste Versionsnummer des .NET Framework sein, der von der Vorlage zugelassen wird.

## <a name="remarks"></a>Hinweise

`MaxFrameworkVersion` ist ein optionales Element. Das `MaxFrameworkVersion` Element sollte weggelassen werden, es sei denn, es ist erforderlich, damit der unterstützte Bereich von .NET Framework Versionen für die Vorlage nicht versehentlich beschränkt wird. Er sollte auch weggelassen werden, wenn .NET Framework nicht auf die Vorlage anwendbar ist.

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden die Metadaten für eine Standard [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Klassen Vorlage veranschaulicht.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

In diesem Beispiel ist die maximale Version der .NET Framework, die für die Vorlage erforderlich ist, die durch dargestellt wird, `MaxFrameworkVersion` 4.7.1. Ein Projekt, das mit dieser Vorlage erstellt wird, kann .NET Framework Versionen bis 4.7.1 als Ziel haben.

## <a name="see-also"></a>Siehe auch

- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
