---
title: '&lt;vstoRuntime- &gt; Element (Office-Entwicklung in Visual Studio)'
titleSuffix: ''
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
ms.openlocfilehash: c866db5f691db56e68f6980c9c07d21ee15c0ae5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921748"
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

|attribute|Beschreibung|
|---------------|-----------------|
|`release`|Erforderlich. Die Releaseversion der Visual Studio Tools for Office-Laufzeit.|
|`version`|Erforderlich. Versionsnummer der Visual Studio Tools for Office-Laufzeit.|
|`supportUrl`|Dies ist optional. Link zum Installationspfad der Visual Studio Tools for Office-Laufzeit.|

 `vstoRuntime` enthält keine Elemente.

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht das `vstoRuntime` -Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe. Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>Weitere Informationen

- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)
