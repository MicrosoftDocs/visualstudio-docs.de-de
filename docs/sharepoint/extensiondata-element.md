---
title: ExtensionData-Element | Microsoft-Dokumentation
description: Anzeigen von Verweis Informationen über das ExtensionData-Element, bei dem es sich um ein Element im SharePoint-Projekt Element Schema handelt.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionData element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3131aca3664e37198b0a32bdc0ade0499c12a1e6
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672534"
---
# <a name="extensiondata-element"></a>ExtensionData-Element
  Stellt eine Auflistung benutzerdefinierter Datenelemente dar, die dem SharePoint-Projekt Element zugeordnet sind.

## <a name="syntax"></a>Syntax

```xml
<ExtensionData>
  <ExtensionDataItem.../>
</ExtensionData>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Optionales Element.<br /><br /> Stellt ein benutzerdefiniertes Datenelement dar, das dem SharePoint-Projekt Element im Schlüssel-Wert-Format zugeordnet ist. Sowohl der Schlüssel als auch der Wert müssen Zeichen folgen sein.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projekt Element dar. Dieses Element ist das erforderliche Stamm Element der `.spdata` Datei.|

## <a name="remarks"></a>Hinweise
 Wenn Sie einem SharePoint-Projekt Element mithilfe der-Eigenschaft eines-Objekts benutzerdefinierte Daten zuordnen <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> , speichert Visual Studio die Daten im **ExtensionData** -Element in der- `.spdata` Datei für das Projekt Element. Weitere Informationen finden Sie unter [Speichern von Daten in Erweiterungen des SharePoint-Projekt Systems](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Elementinformationen

|Eigenschaft|Wert|
|-|-|
|**Namespace**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/sharepointtools/sharepointprojectitemmodel|
|**Schemaname**|SharePoint-Projekt Element Schema|
|**Validierungs Datei**|Projectitemmodelschema. xsd|
|**Kann leer sein**|Nein|

## <a name="see-also"></a>Weitere Informationen
- [Schema Referenz für SharePoint-Projekt Elemente](../sharepoint/sharepoint-project-item-schema-reference.md)
