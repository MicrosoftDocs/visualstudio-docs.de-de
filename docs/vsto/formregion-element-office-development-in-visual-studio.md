---
description: Das formRegion-Element des vstov4-Namespace identifiziert einen Microsoft Office Outlook-Formular Bereich, der einem VSTO-Add-in zugeordnet ist.
title: '&lt;FormRegion- &gt; Element (Office-Entwicklung in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0851ba9e117b464d3a2fbb9ad9903af17ceda0c4
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221079"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;FormRegion- &gt; Element (Office-Entwicklung in Visual Studio)
  Das- `formRegion` Element des- `vstov4` Namespace identifiziert einen Microsoft Office Outlook-Formular Bereich, der einem VSTO-Add-in zugeordnet ist.

## <a name="syntax"></a>Syntax

```xml
<formRegion
  name>
  <messageClass
    name/>
</formRegion>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `formRegion` -Element des `vstov4` -Namespace identifiziert einen Formularbereich, der einem VSTO-Add-In für Outlook zugeordnet ist. Es ist nur für Outlook-VSTO-Add-Ins erforderlich, die Formularbereiche beinhalten.

 Es können mehrere `formRegion` -Elemente in einem `formRegions` -Element für ein einzelnes VSTO-Add-In definiert sein.

 Das `formRegion` -Element hat das folgende Attribut.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`name`|Erforderlich. Gibt den Namen des Formularbereichs an.|

 Das `formRegion` -Element weist die folgenden untergeordneten Elemente auf:

### <a name="messageclass"></a>messageClass
 Das `messageClass` -Element identifiziert das Outlook-Formular, das dem Formularbereich zugeordnet ist.

 Das `messageClass` -Element hat das folgende Attribut.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`name`|Erforderlich. Identifiziert das Formular, das dem Formularbereich zugeordnet ist.|

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht ein `formRegion` -Element in einem Anwendungsmanifest für ein mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestelltes Outlook-VSTO-Add-In. Es gibt drei Nachrichtenklassen, die diesem einen Formularbereich zugeordnet sind. Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>Weitere Informationen

- [Erstellen von Outlook-Formular Bereichen](../vsto/creating-outlook-form-regions.md)
- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)
