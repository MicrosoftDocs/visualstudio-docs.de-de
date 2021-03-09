---
title: '&lt;postAction- &gt; Element (Office-Entwicklung in Visual Studio)'
description: Das postAction-Element des vstav3-Namespace enthält die entryPoint-Elemente und alle postAction Data-Elemente, die den Aktionen nach der Bereitstellung zugeordnet sind, die nach der Installation von Office-Projektmappen ausgeführt werden.
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 04f8c92c52aeee9f7f1dd5ab67b3dcef3a295474
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470052"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction- &gt; Element (Office-Entwicklung in Visual Studio)
  Das `postAction` -Element des `vstav3` -Namespace enthält alle `entrypoint` -Elemente und alle `postActionData` -Elemente, die Aktionen nach der Bereitstellung zugeordnet sind, die ausgeführt werden, sobald Office-Projektmappen installiert sind.

## <a name="syntax"></a>Syntax

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `postAction` -Element ist optional und befindet sich im `vstav3` -Namespace. In einem Anwendungsmanifest ist für jede Aktion nach der Bereitstellung ein `postAction` -Element definiert.

 Das `postAction` -Element weist keine Attribute auf.

 `postAction` hat die folgenden Elemente:

### <a name="entrypoint"></a>entryPoint
 Optional. Die Rolle des- `entryPoint` Elements im- `vstav3` Namespace wird in [&#60;entryPoints&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)definiert.

### <a name="postactiondata"></a>postActionData
 Optional. Die Rolle des- `postActionData` Elements im- `vstav3` Namespace wird in [&#60;postaktiondata&#62;-Elements &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)definiert.

## <a name="post-deployment-action-example"></a>Beispiel für eine Aktion nach der Bereitstellung

### <a name="description"></a>BESCHREIBUNG
 Das folgende Codebeispiel veranschaulicht das `postAction` -Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe. Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

### <a name="code"></a>Code

```xml
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
```

## <a name="see-also"></a>Siehe auch

- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)
