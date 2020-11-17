---
title: DefaultName-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
description: Informieren Sie sich über das DefaultName-Element und darüber, wie es den Namen angibt, den das Visual Studio-Projekt System für das Projekt oder das Element generiert, wenn es erstellt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23defc424d3e7ed5095f0e29d673c191c755f9ce
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672729"
---
# <a name="defaultname-element-visual-studio-templates"></a>DefaultName-Element (Visual Studio-Vorlagen)
Gibt den Namen an, den das Visual Studio-Projekt System für das Projekt oder Element generiert, wenn es erstellt wird.

 \<VSTemplate> \<TemplateData>
 \<DefaultName>

## <a name="syntax"></a>Syntax

```
<DefaultName>
    Default Project Name
</DefaultName>
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

 Dieser Text gibt den Standardnamen des Projekts oder Elements an.

## <a name="remarks"></a>Hinweise
 `DefaultName` ist ein optionales Element.

 Bei-Projekten gibt dieses Element den Namen des Verzeichnisses an, in dem das Projekt auf dem Datenträger gespeichert wird. Für-Elemente wird der Dateiname der Quelldatei angegeben.

 Wenn Sie ein Projekt oder Element erstellen, können Sie den Standardnamen mithilfe der Option **Name** ändern. diese Option ist entweder im Dialogfeld **Neues Projekt** oder im Dialogfeld **Neues Element hinzufügen** verfügbar.

 Wenn Sie nicht möchten, dass das Projekt System den Standardnamen für das Projekt oder Element generiert, legen Sie das [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) -Element auf fest `False` .

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die Metadaten für die Standardelement Vorlage für eine- [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Klasse veranschaulicht.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Siehe auch
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
