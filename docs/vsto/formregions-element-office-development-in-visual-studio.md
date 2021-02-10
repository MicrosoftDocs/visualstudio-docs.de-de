---
title: '&lt;FormRegions- &gt; Element (Office-Entwicklung in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a1a718c6a247528788d91e9c1f30ad636acb7ab9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970334"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;FormRegions- &gt; Element (Office-Entwicklung in Visual Studio)
  Das- `formRegions` Element des- `vstov4` Namespace enthält die Microsoft Office Outlook-Formular Bereiche, die einem VSTO-Add-in zugeordnet sind.

## <a name="syntax"></a>Syntax

```xml
<formRegions>
  <formRegion>
  </formRegion>
</formRegions>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `formRegions` -Element des `vstov4` -Namespace enthält alle `formRegion` -Elemente für ein Outlook-VSTO-Add-In. Es ist nur für Outlook-VSTO-Add-Ins erforderlich, die Formularbereiche beinhalten.

 In einem Anwendungsmanifest kann nur ein `formRegions` -Element definiert sein.

 Das `formRegions` -Element weist keine Attribute auf.

 Das `formRegions` -Element hat das folgende Element.

### <a name="formregion"></a>formRegion
 Erforderlich für Outlook-VSTO-Add-Ins, die Formularbereiche beinhalten. Das- `formRegion` Element wird in [&#60;FormRegion-&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)definiert.

## <a name="vsto-add-in-example"></a>Beispiel für ein VSTO-Add-in

### <a name="description"></a>BESCHREIBUNG
 Das folgende Codebeispiel veranschaulicht ein `formRegions` -Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

### <a name="code"></a>Code

```xml
<vstov4:formRegions>
  <vstov4:formRegion
      name="OutlookAddIn1.FormRegion1">
    <vstov4:messageClass name="IPM.Note" />
    <vstov4:messageClass name="IPM.Contact" />
    <vstov4:messageClass name="IPM.Appointment" />
  </vstov4:formRegion>
</vstov4:formRegions>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)