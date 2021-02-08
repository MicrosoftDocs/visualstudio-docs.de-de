---
title: RequiredFrameworkVersion-Element (Visual Studio-Vorlagen)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 211393ea65f7ca31f80134c48863b0092478b3f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836981"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Requirements dframeworkversion-Element (Visual Studio-Vorlagen)

Gibt die Mindestversion des .NET Framework an, die für die Vorlage erforderlich ist. Dadurch wird die Dropdown Liste **Ziel Framework-Version** im Dialogfeld " **Neues Projekt** " angezeigt. Das- `RequiredFrameworkVersion` Element bestimmt auch den niedrigsten Wert, der in der Dropdown Liste verfügbar ist.

> [!IMPORTANT]
> Ab Visual Studio 2017 Version 15,6 ist die Dropdown Liste **Ziel Framework-Version** kein Filter für angezeigte Vorlagen im Abschnitt **Vorlagen** des Dialog Felds **Neues Projekt** . Stattdessen fungiert die Dropdown Liste als frameworkauswahl für die ausgewählte Vorlage.

 \<VSTemplate> \<TemplateData>
 \<RequiredFrameworkVersion>

## <a name="syntax"></a>Syntax

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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

 Der Text muss die minimale Versionsnummer der .NET Framework sein, die für die Vorlage erforderlich ist.

## <a name="remarks"></a>Bemerkungen

`RequiredFrameworkVersion` ist ein optionales Element. Verwenden Sie dieses Element nur, wenn die Vorlage eine bestimmte Mindestversion (und höhere Versionen) der .NET Framework unterstützt. Wenn Sie das `RequiredFrameworkVersion` -Element angeben und die Vorlage keine bestimmte Mindestversion der .NET Framework unterstützt, wird die Dropdown Liste **Ziel Framework-Version** angezeigt, wenn Sie nicht anwendbar ist.

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

In diesem Beispiel ist die Mindestversion der .NET Framework, die für die Vorlage erforderlich ist, die durch dargestellt wird, `RequiredFrameworkVersion` 3,0. Ein Projekt, das mit dieser Vorlage erstellt wurde, kann auf .NET Framework Versionen ab 3,0 abzielen.

## <a name="see-also"></a>Siehe auch

- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Übersicht über Frameworkziele](../ide/visual-studio-multi-targeting-overview.md)
