---
title: TemplateGroupID-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
description: Informieren Sie sich über das TemplateGroupID-Element und darüber, wie es angibt, in welcher Art von Projekt eine Element Vorlage angezeigt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d9db0d2744648901a9389bd2d2805d8c6a4073ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895361"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID-Element (Visual Studio-Vorlagen)
Gibt an, in welcher Art von Projekt eine Elementvorlage angezeigt wird. Dieses Element ist wichtig, wenn [ShowByDefault (Visual Studio-Vorlagen)](../extensibility/showbydefault-visual-studio-templates.md) auf festgelegt ist `false` . Wenn [ShowByDefault (Visual Studio-Vorlagen)](../extensibility/showbydefault-visual-studio-templates.md) auf festgelegt ist `true` , ist eine Element Vorlage in allen Projekttypen verfügbar.

 \<VSTemplate> \<TemplateData>
 \<TemplateGroupID>

## <a name="syntax"></a>Syntax

```
<TemplateGroupID> ... </TemplateGroupID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Der Text gibt einen Bezeichner für eine Kategorie von Elementvorlagen an.

## <a name="remarks"></a>Bemerkungen
 `TemplateGroupID` ist ein Element.

 Der Wert des- `TemplateGroupID` Elements wird zusammen mit der Projekt Systemregistrierung (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<version number>* \projects \\ ) zum Filtern von Vorlagen verwendet, die im Dialogfeld **Neues Element hinzufügen** angezeigt werden.

|Visual C++-Wert|Bedeutung|
|------------------------|-------------|
|VC-systemeigen|Für systemeigene Projekte verwendet. Auch die Standardeinstellung, wenn ein Projekttyp nicht bestimmt werden kann.|
|VC-verwaltet|Für verwaltete Projekte (/clr) verwendet.|
|VC-Windows|Für alle Projekte verwendet, die auf die Windows-Plattform abzielen (systemeigen/verwaltet/Speicher).|
|WinRT-systemeigen-UAP|Für Windows 10-Store-Projekte verwendet.|
|CodeSharing-systemeigen|Für freigegebene Elementprojekte verwendet.|
|WinRT-systemeigen-6.3|Für Windows 8.1-Store-Projekte verwendet.|
|WinRT-systemeigen-Phone-6.3|Für Windows Phone 8.1-Projekte verwendet.|
|WinRT-systemeigen|Für Windows 8.0-Store-Projekte verwendet.|
|VC-Android|Für Android-Projekte verwendet.|

## <a name="see-also"></a>Weitere Informationen
- [Schema Referenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md)
