---
title: Files-Element | Microsoft-Dokumentation
description: Anzeigen von Verweis Informationen über das Files-Element, bei dem es sich um ein Element im SharePoint-Projekt Element Schema handelt.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 653e48a2e9b6a68db94fd66660da85f4dec20927
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876646"
---
# <a name="files-element"></a>Files-Element
  Gibt die Dateien an, die mit dem SharePoint-Projekt Element bereitgestellt werden sollen, z. b. featureelementdateien und die Ausgabe abhängiger nicht-SharePoint-Projekte.

## <a name="syntax"></a>Syntax

```xml
<Files>
  <ProjectItemFile.../>
  <ProjectOutputFile.../>
</Files>
```

## <a name="type"></a>type
 **Filecollectiontype**

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Optionales **projectitemfiletype** -Element.<br /><br /> Stellt eine SharePoint-Datei (z. b. eine featureelementdatei) dar, die beim Bereitstellen in SharePoint in das Projekt Element eingeschlossen werden soll.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Optionales **projectoutputfiletype** -Element.<br /><br /> Stellt die Ausgabe eines Projekts dar, das in das Projekt Element aufgenommen werden soll, wenn es in SharePoint bereitgestellt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projekt Element dar. Dieses Element ist das erforderliche Stamm Element der `.spdata` Datei.|

## <a name="element-information"></a>Elementinformationen

|Eigenschaft|Wert|
|-|-|
|**Namespace**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/sharepointtools/sharepointprojectitemmodel|
|**Schemaname**|SharePoint-Projekt Element Schema|
|**Validierungs Datei**|Projectitemmodelschema. xsd|
|**Kann leer sein**|Nein|

## <a name="see-also"></a>Weitere Informationen
- [Schema Referenz für SharePoint-Projekt Elemente](../sharepoint/sharepoint-project-item-schema-reference.md)
