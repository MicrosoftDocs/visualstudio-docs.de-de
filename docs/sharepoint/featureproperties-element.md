---
title: FeatureProperties-Element | Microsoft-Dokumentation
description: Anzeigen von Verweis Informationen über das FeatureProperties-Element, das ein Element im SharePoint-Projekt Element Schema ist.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9ee2bddec02263a889fb1f69088a8a50b3d8b57d
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672599"
---
# <a name="featureproperties-element"></a>FeatureProperties-Element
  Eine Auflistung von Eigenschafts Werten, die in einer Funktion enthalten sind, wenn Sie in SharePoint bereitgestellt wird. Nachdem eine Funktion bereitgestellt wurde, können Sie auf die Eigenschaftswerte im Code zugreifen.

## <a name="syntax"></a>Syntax

```xml
<FeatureProperties>
  <FeatureProperty.../>
</FeatureProperties>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Optionales Element.<br /><br /> Stellt eine benutzerdefinierte Eigenschaft im Schlüssel-Wert-Format dar.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projekt Element dar. Dieses Element ist das erforderliche Stamm Element der `.spdata` Datei.|

## <a name="remarks"></a>Hinweise
 Weitere Informationen zu Featureeigenschaften finden Sie unter [Bereitstellen von Verpackungs-und Bereitstellungs Informationen in Projekt Elementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Elementinformationen

|Element|Beschreibung|
|-------------|-----------------|
|**Namespace**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/sharepointtools/sharepointprojectitemmodel|
|**Schemaname**|SharePoint-Projekt Element Schema|
|**Validierungs Datei**|Projectitemmodelschema. xsd|
|**Kann leer sein**|Nein|

## <a name="see-also"></a>Weitere Informationen
- [Schema Referenz für SharePoint-Projekt Elemente](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
