---
title: Projectoutputfile-Element | Microsoft-Dokumentation
description: Hier finden Sie Referenzinformationen zum projectoutputfile-Element, das die Ausgabe eines separaten Projekts in der XML-Schema Referenz des SharePoint-Projekt Elements darstellt.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ffe6f95bdfd7795c837aaaa25ec7ef2a35a7ae76
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442027"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile-Element
  Stellt die Ausgabe eines separaten Projekts dar, das in das Projekt Element aufgenommen werden soll, wenn es in SharePoint bereitgestellt wird.

## <a name="syntax"></a>Syntax

```xml
<ProjectOutputFile ProjectId = "GUID of the project"
    ProjectPath = "Relative path of the project"
    Target = "Deployment path of the project output"
    Type = "Type of deployment for the project output" />
```

## <a name="type"></a>type
 **Projectoutputfiletype**

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|**ProjectId**|Erforderliches **xs: String** -Attribut.<br /><br /> Die GUID des abhängigen Projekts mit der Ausgabe, die Sie einschließen möchten. Dies entspricht dem **ProjectGuid** -Element in der abhängigen Projektdatei.|
|**ProjectPath**|Erforderliches **xs: String** -Attribut.<br /><br /> Der relative Pfad, einschließlich des Projekt Dateinamens, des abhängigen Projekts mit der Ausgabe, die Sie einschließen möchten. Dieser Pfad ist relativ zum Stamm Ordner des SharePoint-Projekts, das das SharePoint-Projekt Element enthält.|
|**Target**|Optionales **xs: String** -Attribut.<br /><br /> Der Pfad, in dem die abhängige Projekt Ausgabe auf dem SharePoint-Server relativ zum Stamm Ordner der Bereitstellung bereitgestellt werden soll. Der Stamm Ordner der Bereitstellung wird durch den Bereitstellungstyp bestimmt, der durch das **Type** -Attribut angegeben wird.<br /><br /> Weitere Informationen finden Sie in den Beschreibungen für den **Bereitstellungs Pfad** und die **Bereitstellungs** Stamm Eigenschaften von SharePoint-Projekt Elementen in [entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|
|**Type**|Erforderliches **xs: String** -Attribut.<br /><br /> Der Bereitstellungstyp, der für die Ausgabe des abhängigen Projekts verwendet werden soll. Weitere Informationen zu den möglichen Werten finden Sie in der Beschreibung der Eigenschaft " **Bereitstellungstyp** " von SharePoint-Projekt Elementen in [entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Dateien](../sharepoint/files-element.md)|Gibt die Dateien an, die mit dem SharePoint-Projekt Element beim Bereitstellung in SharePoint eingeschlossen werden sollen.|

## <a name="remarks"></a>Bemerkungen
 Verwenden Sie das **projectoutputfile** -Element, um die Ausgabe eines Projekts in die Bereitstellung des SharePoint-Projekt Elements einzubeziehen. Sie können ein anderes Projekt oder das gleiche Projekt angeben, das das Projekt Element enthält. Weitere Informationen finden Sie unter [Bereitstellen von Verpackungs-und Bereitstellungs Informationen in Projekt Elementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

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
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
