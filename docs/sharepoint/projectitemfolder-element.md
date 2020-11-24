---
title: Projectitemfolder-Element | Microsoft-Dokumentation
description: Hier finden Sie Referenzinformationen zum projectitemfolder-Element, das einen zugeordneten Ordner in der XML-Schema Referenz des SharePoint-Projekt Elements darstellt.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 99a27f8e255aa17e8b9fa604b504109976c5d36a
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440791"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder-Element
  Stellt einen zugeordneten Ordner dar.

## <a name="syntax"></a>Syntax

```xml
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"
    Type = "Type of deployment for the mapped folder" />
```

## <a name="type"></a>type
 **Projectitemfoldertype**

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|**Ziel**|Erforderliches **xs: String** -Attribut.<br /><br /> Der Pfad des Ordners in der SharePoint-Installation, dem der zugeordnete Ordner entspricht, relativ zum Stamm Ordner der Bereitstellung. Der Stamm Ordner der Bereitstellung wird durch den Bereitstellungstyp bestimmt, der durch das **Type** -Attribut angegeben wird.<br /><br /> Weitere Informationen finden Sie in den Beschreibungen für den **Bereitstellungs Pfad** und die **Bereitstellungs** Stamm Eigenschaften von SharePoint-Projekt Elementen in [entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|
|**Type**|Erforderliches **xs: String** -Attribut.<br /><br /> Der Bereitstellungstyp für den zugeordneten Ordner. Weitere Informationen zu den möglichen Werten finden Sie in der Beschreibung der Eigenschaft " **Bereitstellungstyp** " von SharePoint-Projekt Elementen in [entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projekt Element dar. Dieses Element ist das erforderliche Stamm Element der *spdata* -Datei.|

## <a name="remarks"></a>Bemerkungen
 Weitere Informationen zu zugeordneten Ordnern finden Sie unter Gewusst [wie: Hinzufügen und entfernen](../sharepoint/how-to-add-and-remove-mapped-folders.md)von zugeordneten Ordnern.

## <a name="element-information"></a>Elementinformationen

|Eigenschaft|Wert|
|-|-|
|**Namespace**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/2010/<br>Sharepointtools/sharepointprojectitemmodel|
|**Schemaname**|SharePoint-Projekt Element Schema|
|**Validierungs Datei**|Projectitemmodelschema. xsd|
|**Kann leer sein**|Nein|

## <a name="see-also"></a>Weitere Informationen
- [Schema Referenz für SharePoint-Projekt Elemente](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Gewusst wie: Hinzufügen und entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md)
