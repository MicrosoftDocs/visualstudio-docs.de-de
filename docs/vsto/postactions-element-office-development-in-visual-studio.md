---
title: '&lt;postActions- &gt; Element (Office-Entwicklung)'
description: Das postActions-Element des vstav3-Namespace enthält alle postAction-Elemente, die Aktionen nach der Bereitstellung beschreiben, die nach der Installation von Office-Projektmappen ausgeführt werden.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5c4a66e270cd446996884262d380df0f7384f54f
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470039"
---
# <a name="ltpostactionsgt-element-office-development"></a>&lt;postActions- &gt; Element (Office-Entwicklung)
  Das `postActions` -Element des `vstav3` -Namespace enthält alle `postAction` -Elemente, die Aktionen nach der Bereitstellung beschreiben, die ausgeführt werden, nachdem Office-Projektmappen installiert sind.

## <a name="syntax"></a>Syntax

```xml
<postActions>
  <postAction>
    <entryPoint>
    </entryPoint>
    <postActionData>
    </postActionData>
  </postAction>
</postActions>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `postActions` -Element ist optional und befindet sich im `vstav3` -Namespace. In einem Anwendungsmanifest ist nur ein `postActions` -Element definiert.

 Das `postActions` -Element weist keine Attribute auf.

 `postActions` weist das folgende Element auf:

### <a name="postaction"></a>postAction
 Optional. Die Rolle des- `postAction` Elements im- `vstav3` Namespace wird in [&#60;postAction&#62;-Elements &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)definiert.

## <a name="post-deployment-action-example"></a>Beispiel für eine Aktion nach der Bereitstellung

### <a name="description"></a>BESCHREIBUNG
 Das folgende Codebeispiel veranschaulicht das `postActions` -Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe. Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

### <a name="code"></a>Code

```xml
<vstav3:postActions>
  <vstav3:postAction>
    <vstav3:entryPoint
      class="PostDeploymentAction.PostDeploymentActionSample">
      <assemblyIdentity
        name="PostDeploymentAction"
        version="1.0.0.0"
        language="neutral"
        processorArchitecture="msil" />
    </vstav3:entryPoint>
    <vstav3:postActionData>
    </vstav3:postActionData>
  </vstav3:postAction>
</vstav3:postActions>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)
