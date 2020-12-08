---
title: '&lt;customhostspezifiziertes- &gt; Element (Office-Entwicklung in Visual Studio)'
description: Erfahren Sie, wie das customhostangegebene-Element angibt, dass diese Lösung keine eigenständige Anwendung ist.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e8327c6e154f051f5ce79d41ceaa696e330c794f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848130"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customhostspezifiziertes- &gt; Element (Office-Entwicklung in Visual Studio)
  Das- `customHostSpecified` Element gibt an, dass diese Lösung keine eigenständige Anwendung ist. Office-Projektmappen enthalten Komponenten, die in Microsoft Office Anwendungen gehostet werden.

## <a name="syntax"></a>Syntax

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das- `customHostSpecified` Element ist für Office-Projektmappen erforderlich. Dieses Element befindet sich im `co.v1` -Namespace und gibt an, dass diese Bereitstellung eine Komponente enthält, die in einem benutzerdefinierten Host bereitgestellt wird und keine eigenständige Anwendung ist.

 Dieses Element ist ein untergeordnetes Element des ersten `<entrypoint>` Elements im Anwendungs Manifest. Es dürfen keine weiteren untergeordneten Elemente in diesem Element vorhanden sein, `<entrypoint>` oder es [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] wird während der Installation ein Validierungs Fehler ausgegeben.

 Dieses Element hat keine Attribute und keine untergeordneten Elemente.

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht das- `customHostSpecified` Element in einem Anwendungs Manifest für eine Office-Projekt Mappe. Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)