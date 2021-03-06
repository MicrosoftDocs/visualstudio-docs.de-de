---
description: Das FriendlyName-Element des vstov4-Namespace speichert den Namen, der in der Liste der installierten Programme angezeigt wird.
title: '&lt;FriendlyName- &gt; Element (Office-Entwicklung in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: adcf46a2c232176026181283549c0c59fc713603
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223445"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;FriendlyName- &gt; Element (Office-Entwicklung in Visual Studio)
  Das `friendlyName` -Element des `vstov4` Namespace speichert den angezeigten Namen in der Liste der installierten Programme.

## <a name="syntax"></a>Syntax

```xml
<friendlyName>
</friendlyName>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `friendlyName` -Element befindet sich im `vstov4` Namespace. Der Wert wird in der Liste der installierten Programme auf dem Computer und im Dialogfeld der COM-VSTO-Add-Ins von Microsoft Office-Anwendungen angezeigt.

 Das `friendlyName` Element weist keine Attribute oder untergeordnete Elemente auf.

## <a name="vsto-add-in-example"></a>Beispiel für ein VSTO-Add-in

### <a name="description"></a>BESCHREIBUNG
 Das folgende Codebeispiel veranschaulicht das `friendlyName` -Element in einer mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellten Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

### <a name="code"></a>Code

```xml
<vstov4:friendlyName>
  ContosoOutlookAddIn
</vstov4:friendlyName>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)
