---
title: SafeControl-Element | Microsoft-Dokumentation
description: Abrufen von Informationen über das SafeControl-Element, das ein aspx-Steuerelement oder Webpart darstellt, das als sicher gekennzeichnet ist, damit ein Benutzer auf der ASPX-Seite einer SharePoint-Website darauf zugreifen kann.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 36a8b0ed45fbdb8d2dfe8e93a027a47adf407587
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440622"
---
# <a name="safecontrol-element"></a>SafeControl-Element
  Stellt ein aspx-Steuerelement oder Webpart dar, das für jeden Benutzer auf einer beliebigen ASPX-Seite auf der SharePoint-Website als sicher eingestuft wird.

## <a name="syntax"></a>Syntax

```xml
<SafeControl Assembly = "Name of assembly that contains the safe control"
    IsSafe = "true/false"
    IsSafeAgainstScript = "true/false"
    Name = "Name of this safe control entry"
    Namespace = "Namespace of the safe control"
    TypeName = "Type of the safe control" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|**Assembly**|Optionales **xs: String** -Attribut.<br /><br /> Der Name der Assembly, in der das aspx-Steuerelement oder Webpart definiert ist. Standardmäßig verwendet dieses Attribut den ersetzbaren Parameter **$SharePoint. Project. AssemblyFullName $ für den Assemblynamen** . Weitere Informationen finden Sie unter [Ersetzbare Parameter](../sharepoint/replaceable-parameters.md).|
|**Issafe**|Optionales **xs: Boolean** -Attribut.<br /><br /> Gibt an, ob das aspx-Steuerelement oder Webpart sicher ist, dass nicht vertrauenswürdige Benutzer darauf zugreifen können.|
|**Issafeagainstscript**|Optionales **xs: Boolean** -Attribut.<br /><br /> Gibt an, ob nicht vertrauenswürdige Benutzer die Eigenschaften des aspx-Steuer Elements oder Webparts anzeigen oder bearbeiten können.|
|**Name**|Optionales **xs: String** -Attribut.<br /><br /> Der Name des Eintrags für sicheres Steuerelement in der Auflistung.|
|**Namespace**|Optionales **xs: String** -Attribut.<br /><br /> Der Namespace des aspx-Steuer Elements oder Webparts.|
|**TypeName**|Optionales **xs: String** -Attribut.<br /><br /> Der Typname des aspx-Steuer Elements oder Webparts.|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|["SafeControls](../sharepoint/safecontrols-element.md)|Stellt eine Auflistung von ASPX-Steuerelementen und Webparts dar, die für jeden Benutzer auf einer beliebigen ASPX-Seite auf der SharePoint-Website als sicher gekennzeichnet sind.|

## <a name="remarks"></a>Bemerkungen
 Weitere Informationen zu sicheren Steuerelementen finden Sie unter [Bereitstellen von Verpackungs-und Bereitstellungs Informationen in Projekt Elementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Elementinformationen

|Eigenschaft|Wert|
|-|-|
|**Namespace**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/sharepointtools/sharepointprojectitemmodel|
|**Schemaname**|SharePoint-Projekt Element Schema|
|**Validierungs Datei**|Projectitemmodelschema. xsd|
|**Kann leer sein**|Nein|

## <a name="see-also"></a>Weitere Informationen
- [Schema Referenz für SharePoint-Projekt Elemente](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
