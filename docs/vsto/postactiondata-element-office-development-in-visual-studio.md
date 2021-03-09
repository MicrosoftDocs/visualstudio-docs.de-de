---
title: '&lt;postaktiondata- &gt; Element (Office-Entwicklung)'
description: Das postAction Data-Element des vstav3-Namespace gibt die Daten an, die jeder Aktion nach der Bereitstellung zugeordnet sind, die nach der Installation von Office-Lösungen ausgeführt wird.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a75f61c6d1f80a127f49d96c4e3f4910c66dd8aa
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470065"
---
# <a name="ltpostactiondatagt-element-office-development"></a>&lt;postaktiondata- &gt; Element (Office-Entwicklung)
  Das `postActionData` -Element des `vstav3` -Namespace gibt die Daten an, die jeder Aktion nach der Bereitstellung zugeordnet sind, die nach der Installation von Office-Projektmappen ausgeführt wird.

## <a name="syntax"></a>Syntax

```xml
<postActionData>
</postActionData>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `postActionData` -Element ist optional und befindet sich im `vstav3` -Namespace. In einem Anwendungsmanifest ist für jede Aktion nach der Bereitstellung ein `postActionData` -Element definiert.

 Das `postActions` -Element weist keine Attribute auf.

 `postActions` hat keine untergeordneten Elemente.

## <a name="post-deployment-action-example"></a>Beispiel für eine Aktion nach der Bereitstellung

### <a name="description"></a>BESCHREIBUNG
 Das folgende Codebeispiel veranschaulicht das `postAction` -Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe. Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

### <a name="code"></a>Code

```xml
<vstav3:postActionData>
  data in any format
</vstav3:postActionData>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)
