---
title: '&lt;vstoRuntime- &gt; Element (Office-Entwicklung in Visual Studio)'
titleSuffix: ''
description: Das vstoRuntime-Element des vstav3-Namespace enthält eine unterstützte Version der Visual Studio-Tools für Office-Laufzeit für eine bestimmte Office-Projekt Mappe.
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7c856836bd2ba107a2fa6c3017c5ecb2694fcf6b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102468571"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoRuntime- &gt; Element (Office-Entwicklung in Visual Studio)
  Das `vstoRuntime` -Element des `vstav3` -Namespace enthält eine unterstützte Version der Visual Studio Tools for Office-Laufzeit für eine bestimmte Office-Projektmappe.

## <a name="syntax"></a>Syntax

```xml
<vstoRuntime
    release
    version
    supportUrl />
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `vstoRuntime` -Element ist erforderlich und befindet sich im `vstav3` -Namespace. Wenn eine Office-Projektmappe zwei Versionen der Visual Studio-Tools für Office-Laufzeit unterstützt, gibt es zwei `vstoRuntime` -Elemente im Anwendungsmanifest.

 Das `vstoRuntime` -Element weist folgende Attribute auf.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`release`|Erforderlich. Die Releaseversion der Visual Studio Tools for Office-Laufzeit.|
|`version`|Erforderlich. Versionsnummer der Visual Studio Tools for Office-Laufzeit.|
|`supportUrl`|Optional. Link zum Installationspfad der Visual Studio Tools for Office-Laufzeit.|

 `vstoRuntime` enthält keine Elemente.

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht das `vstoRuntime` -Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe. Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>Siehe auch

- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)
