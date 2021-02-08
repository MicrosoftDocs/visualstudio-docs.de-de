---
title: RequiredPlatformVersion-Element (Visual Studio-Vorlagen)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d182d308f852dda05f20f4ea30d3536850e20e90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837020"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Requirements dplatformversion-Element (Visual Studio-Vorlagen)

Gibt die Mindestversion des Betriebssystems an, die vorliegen muss, damit die Projektvorlage ordnungsgemäß funktioniert. Dieses Element wird für Projektvorlagen verwendet, die [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Apps erstellen.

 Der Wert `RequiredPlatformVersion` wird unmittelbar mit der Version des Betriebssystems verglichen. Wenn die `RequiredPlatformVersion` höher als die Betriebssystemversion ist, wird die Vorlage nicht im Dialogfeld **Neues Projekt** angezeigt. Um eine Vorlage für [!INCLUDE[win8](../debugger/includes/win8_md.md)] oder höher anzugeben, legen Sie `RequiredPlatformVersion` auf 6.2.0 fest. [!INCLUDE[win81](../debugger/includes/win81_md.md)]Legen Sie auf 6.3.0 fest, um eine Vorlage für oder höher anzugeben `RequiredPlatformVersion` .

 Vorlagen, die `RequiredPlatformVersion`=8 angeben, sind mit früheren [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Kundenvorlagen kompatibel.

 VSTEMPLATE TemplateData.... Targetplatformname "Requirements dplatformversion"

## <a name="syntax"></a>Syntax

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

 Keine

### <a name="attributes"></a>Attribute

 Keine

### <a name="child-elements"></a>Untergeordnete Elemente

 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Gibt die Plattform an, auf die die Projektvorlage abzielt.|

## <a name="text-value"></a>Textwert

 Ein Textwert ist erforderlich.

## <a name="remarks"></a>Bemerkungen

 Dieser Text gibt die Mindestversion des Betriebssystems an, die für die Vorlage erforderlich ist.

## <a name="example"></a>Beispiel

 In diesem Beispiel wird angegeben, dass die Projektvorlage auf [!INCLUDE[win8](../debugger/includes/win8_md.md)] oder höher abzielt.

```xml
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>

    </TemplateData>
    <TemplateContent>

    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Weitere Informationen

- [Targetplatformname-Element (Visual Studio-Vorlagen)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
