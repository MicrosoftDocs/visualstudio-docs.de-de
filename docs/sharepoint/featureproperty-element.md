---
title: FeatureProperty-Element | Microsoft-Dokumentation
description: Anzeigen von Verweis Informationen über das FeatureProperty-Element, das ein Element im SharePoint-Projekt Element Schema ist.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 070866b9dd14d974eb976b22bf7a79907e2c5d9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876666"
---
# <a name="featureproperty-element"></a>FeatureProperty-Element
  Stellt eine benutzerdefinierte Eigenschaft dar, die in einer Funktion enthalten ist, wenn Sie in SharePoint bereitgestellt wird. Nachdem eine Funktion bereitgestellt wurde, können Sie auf die-Eigenschaft im Code zugreifen.

## <a name="syntax"></a>Syntax

```xml
<FeatureProperty Key = "Key of the property value"
    Value = "Property value" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|**Schlüssel**|Erforderliches **xs: String** -Attribut.<br /><br /> Der Schlüssel, der zum Speichern und Abrufen des Eigenschafts Werts verwendet wird. Jede Eigenschaft muss über einen Schlüssel verfügen, der innerhalb des Features eindeutig ist.|
|**Wert**|Erforderliches **xs: String** -Attribut.<br /><br /> Der Eigenschaftswert.|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Stellt eine Auflistung von Eigenschafts Werten dar, die in einer Funktion enthalten sind, wenn Sie in SharePoint bereitgestellt wird.|

## <a name="remarks"></a>Bemerkungen
 Weitere Informationen zu Featureeigenschaften finden Sie unter [Bereitstellen von Paket-und Bereitstellungs Informationen in Projekt Elementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

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
