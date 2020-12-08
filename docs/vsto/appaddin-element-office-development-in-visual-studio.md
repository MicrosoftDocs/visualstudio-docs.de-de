---
title: '&lt;appAddin- &gt; Element (Office-Entwicklung in Visual Studio)'
description: Erfahren Sie, wie das appAddin-Element des vstov4-Namespace Anpassungs spezifische Informationen für VSTO-Add-ins speichert.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a22015fe6183dfd74fff54c34bc6896e1d33d217
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844750"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin- &gt; Element (Office-Entwicklung in Visual Studio)
  Im **appAddin** -Element des- `vstov4` Namespace werden Anpassungs spezifische Informationen für VSTO-Add-Ins gespeichert.

## <a name="syntax"></a>Syntax

```xml
<appAddin
  application
  loadBehavior
  keyName>
  <friendlyName>
  <description>
  <formRegions></formRegions>
</appAddin>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das **appAddin** -Element ist erforderlich und befindet sich im- `vstov4` Namespace. In einem Anwendungs Manifest ist nur ein **appAddin** -Element definiert.

 Das **appAddin** -Element verfügt über die folgenden Attribute.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|**application**|Erforderlich. Identifiziert die Microsoft Office-Anwendung. Einer der folgenden Werte ist möglich: Excel, InfoPath, Outlook, PowerPoint, Project, Visio oder Word.|
|**LoadBehavior**|Dies ist optional. Standardmäßig wird **LoadBehavior** aktiviert, indem dieser Wert auf festgelegt wird. Zum Debuggen kann das VSTO-Add-In deaktiviert werden, indem der Wert auf 2 festgelegt wird. Weitere Informationen finden Sie in der Tabelle mit dem Namen LoadBehavior-Werte in [Registrierungs Einträgen für VSTO-Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).|
|**keyName**|Erforderlich. Dieser Wert ist der Name des Registrierungsschlüssels, der von der Anwendung zum Laden des VSTO-Add-Ins verwendet wird. Weitere Informationen finden Sie unter [Registrierungseinträge für VSTO-Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).|

 Das **appAddin** -Element verfügt über die folgenden untergeordneten Elemente.

### <a name="friendlyname"></a>friendlyName
 Dies ist optional. Das **FriendlyName** -Element wird in [&#60;FriendlyName&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)erläutert.

### <a name="description"></a>description
 Dies ist optional. Das **Description** -Element wird in [&#60;Description&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)erläutert.

### <a name="formregions"></a>formRegions
 Nur für Outlook-VSTO-Add-Ins erforderlich, die Formularbereiche enthalten. Das **FormRegions** -Element wird in [&#60;FormRegions&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)erläutert.

## <a name="vsto-add-in-example"></a>Beispiel für ein VSTO-Add-in

### <a name="description"></a>BESCHREIBUNG
 Im folgenden Codebeispiel werden **appAddin** -Elemente in einer mit bereitgestellten Outlook-Projekt Mappe veranschaulicht [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

### <a name="code"></a>Code

```xml
<vstov4:appAddIn
  application="Outlook"
  loadBehavior="3"
  keyName="ContosoOutlookAddIn">
  <vstov4:friendlyName>
    ContosoOutlookAddIn
  </vstov4:friendlyName>
  <vstov4:description>
    ContosoOutlookAddIn - Outlook VSTO Add-in
    created with Visual Studio Tools for Office
  </vstov4:description>
  <vstov4:formRegions>
    <vstov4:formRegion
        name="OutlookAddIn1.FormRegion1">
      <vstov4:messageClass name="IPM.Note" />
      <vstov4:messageClass name="IPM.Contact" />
      <vstov4:messageClass name="IPM.Appointment" />
    </vstov4:formRegion>
  </vstov4:formRegions>
</vstov4:appAddIn>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)