---
title: ProvideDefaultName-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 192716198f605a5f6b4f62730e84dcf83b4229cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701716"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName-Element (Visual Studio-Vorlagen)
Gibt an, ob das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt System im Dialogfeld **Neues Element** oder **Neues Projekt** hinzufügen einen Standardnamen für die Vorlage generiert.

 \<VSTemplate> \<TemplateData>
 \<ProvideDefaultName>

## <a name="syntax"></a>Syntax

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Der Text muss entweder `true` oder sein `false` , um anzugeben, ob im Dialogfeld **Neues Element hinzufügen** oder **Neues Projekt** ein Standardname für die Vorlage generiert werden soll.

## <a name="remarks"></a>Bemerkungen
 `ProvideDefaultName` ist ein optionales Element. Standardwert: `true`.

 Wenn das `ProvideDefaultName` -Element ist `false` , enthalten die Felder " **Name** " in den Dialogfeldern **Neues Element hinzufügen** und **Neues Projekt** den Wert `<Enter_name>` .

 Verwenden Sie das [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) -Element, um den Standardnamen des Projekts oder Elements in den Dialogfeldern **Neues Element hinzufügen** und **Neues Projekt** anzugeben. Wenn der Wert des- `ProvideDefaultName` Elements ist `true` , füllt das- `DefaultName` Element für Projekte das Dialogfeld mit dem Namen der Vorlage, d. h. dem Wert aus dem [Name](../extensibility/name-element-visual-studio-templates.md) -Element, auf.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird das- `ProvideDefaultName` Element auf festgelegt `false` .

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProvideDefaultName>false</ProvideDefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Siehe auch
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
