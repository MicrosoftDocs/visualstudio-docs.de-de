---
title: Projectitemfile-Element | Microsoft-Dokumentation
description: Hier finden Sie Referenzinformationen zum projectitemfile-Element, das eine Projekt Element Datei in der XML-Schema Referenz des SharePoint-Projekt Elements darstellt.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 099f20926487b09240219f04d9bce4a79709f6e6
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440804"
---
# <a name="projectitemfile-element"></a>ProjectItemFile-Element
  Stellt eine SharePoint-Datei (z. b. eine featureelementdatei) dar, die beim Bereitstellen in SharePoint in das Projekt Element eingeschlossen werden soll.

## <a name="syntax"></a>Syntax

```xml
<ProjectItemFile Source = "Name of the file"
    Target = "Deployment path of the file"
    Type = "Type of deployment for the file" />
```

## <a name="type"></a>type
 **Projectitemfiletype**

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|**Quelle**|Erforderliches **xs: String** -Attribut.<br /><br /> Der Name der Datei, die mit dem Projekt Element bereitgestellt werden soll.|
|**Target**|Optionales **xs: String** -Attribut.<br /><br /> Der Pfad, in dem die Datei in SharePoint in Relation zum Stamm Ordner der Bereitstellung bereitgestellt wird. Der Stamm Ordner der Bereitstellung wird durch den Bereitstellungstyp bestimmt, der durch das **Type** -Attribut angegeben wird. Wenn das **Ziel** Attribut nicht angegeben ist, wird die Datei in einem Ordner mit dem Namen bereitgestellt, der im **Quell** Attribut angegeben ist.<br /><br /> Weitere Informationen finden Sie in den Beschreibungen für den **Bereitstellungs Pfad** und die **Bereitstellungs** Stamm Eigenschaften von SharePoint-Projekt Elementen in [entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|
|**Type**|Erforderliches **xs: String** -Attribut.<br /><br /> Der Bereitstellungstyp für die Datei. Weitere Informationen zu den möglichen Werten finden Sie in der Beschreibung der Eigenschaft " **Bereitstellungstyp** " von SharePoint-Projekt Elementen in [entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Dateien](../sharepoint/files-element.md)|Gibt die Dateien an, die mit dem SharePoint-Projekt Element beim Bereitstellung in SharePoint eingeschlossen werden sollen.|

## <a name="remarks"></a>Bemerkungen
 Zu SharePoint-Dateien, auf die in der Regel in **projectitemfile** -Elementen verwiesen wird, gehören featureelementdateien (*Elements.xml*), Schema Dateien für Listen Definitionen (*Schema.xml*) und webpartdefinitions Dateien für Webparts (*. WebPart*).

## <a name="element-information"></a>Elementinformationen

|Eigenschaft|Wert|
|-|-|
|**Namespace**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/sharepointtools/sharepointprojectitemmodel|
|**Schemaname**|SharePoint-Projekt Element Schema|
|**Validierungs Datei**|Projectitemmodelschema. xsd|
|**Kann leer sein**|Nein|

## <a name="see-also"></a>Weitere Informationen
- [Schema Referenz für SharePoint-Projekt Elemente](../sharepoint/sharepoint-project-item-schema-reference.md)
