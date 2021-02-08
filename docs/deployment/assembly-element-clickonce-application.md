---
title: '&lt;Assembly- &gt; Element (ClickOnce-Anwendung) | Microsoft-Dokumentation'
description: Das Assembly-Element ist das root-Element und ist in der ClickOnce-Anwendung erforderlich. Das erste enthaltene Element muss ein assemblyIdentity-Element sein.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f86ed604ae6b893f02da1d4f65a816bd05f34f94
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837787"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;Assembly- &gt; Element (ClickOnce-Anwendung)
Das Element der obersten Ebene für das Anwendungs Manifest.

## <a name="syntax"></a>Syntax

```xml

      <assembly
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `assembly` -Element ist das root-Element und ist erforderlich. Das erste enthaltene Element muss ein `assemblyIdentity` Element sein. Die Manifest-Elemente müssen einen der folgenden Namespaces aufweisen:

 `urn:schemas-microsoft-com:asm.v1`

 `urn:schemas-microsoft-com:asm.v2`

 `http://www.w3.org/2000/09/xmldsig#`

 Untergeordnete Elemente der Assembly müssen sich auch in diesen Namespaces befinden, durch Vererbung oder durch Tagging.

 Das `assembly` -Element hat das folgende Attribut.

|attribute|Beschreibung|
|---------------|-----------------|
|`manifestVersion`|Erforderlich. Das- `manifestVersion` Attribut muss auf festgelegt werden `1.0` .|

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht ein- `assembly` Element in einem Anwendungs Manifest für eine- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Dieses Codebeispiel ist Teil eines größeren Beispiels, das im [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)bereitgestellt wird.

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
```

## <a name="see-also"></a>Weitere Informationen
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)
- [\<assembly>-Element](../deployment/assembly-element-clickonce-deployment.md)
