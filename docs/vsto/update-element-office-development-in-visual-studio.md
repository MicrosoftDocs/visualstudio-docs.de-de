---
title: '&lt;Update- &gt; Element (Office-Entwicklung in Visual Studio)'
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5712be9e12ede3338856955e00a34a7565d733ee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968761"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;Update- &gt; Element (Office-Entwicklung in Visual Studio)
  Das- `update` Element gibt das Intervall an, in dem die Projekt Mappe nach Updates sucht.

## <a name="syntax"></a>Syntax

```xml
<update
  enabled>
  <expiration
    maximumAge
    unit
  />
</update>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `update` -Element ist erforderlich und befindet sich im `vstav3` -Namespace.

 Das `update` -Element weist folgende Attribute auf.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`enabled`|Erforderlich. Legen Sie den Wert auf einen der folgenden Werte fest:<br /><br /> -   " **true** ", um nach Updates zu suchen.<br />-   **false** , um die Suche nach Updates zu verhindern.|

 Das `update` -Element weist die folgenden untergeordneten Elemente auf:

### <a name="expiration"></a>expiration
 Das `expiration` -Element ist erforderlich und befindet sich im `vstav3` -Namespace. Dieses Element gibt das Intervall an, in dem die Projekt Mappe nach Updates sucht.

 Das `expiration` -Element weist folgende Attribute auf.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`maximumAge`| Erforderlich. Legen Sie diesen Wert auf eine ganze Zahl fest.|
|`unit`|Erforderlich. Legen `unit` Sie einen der folgenden Werte fest:<br /><br /> -   **Hours**<br />-   **tagelang**<br />-   **Wochen**|

## <a name="example-of-always-checking-for-updates"></a>Beispiel für die immer Überprüfung auf Updates

### <a name="description"></a>BESCHREIBUNG
 Das folgende Codebeispiel veranschaulicht ein- `update` Element, das so festgelegt ist, dass es immer nach Updates in Office-Projektmappen sucht

### <a name="code"></a>Code

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>Beispiel für das Festlegen eines standardmäßigen Update Intervalls

### <a name="description"></a>BESCHREIBUNG
 Das folgende Codebeispiel veranschaulicht ein- `update` Element in einem Anwendungs Manifest für Office-Projektmappen. Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

### <a name="code"></a>Code

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>Siehe auch

- [Bereitstellen einer Office-Projekt Mappe mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)
