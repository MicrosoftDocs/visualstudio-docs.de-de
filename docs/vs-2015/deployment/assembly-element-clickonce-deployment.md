---
title: '&lt;Assembly- &gt; Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b77cfacf3dca2c2cc20d674f79929e9958a16d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155740"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;Assembly- &gt; Element (ClickOnce-Bereitstellung)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Element der obersten Ebene für das Bereitstellungs Manifest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `assembly` -Element ist das root-Element und ist erforderlich. Das erste enthaltene Element muss ein `assemblyIdentity` Element sein. Die Manifest-Elemente müssen sich in den folgenden Namespaces befinden: `urn:schemas-microsoft-com:asm.v1` , `urn:schemas-microsoft-com:asm.v2` und `http://www.w3.org/2000/09/xmldsig#` . Untergeordnete Elemente der Assembly müssen sich auch in diesen Namespaces befinden, durch Vererbung oder durch Tagging.  
  
 Das `assembly` -Element hat das folgende Attribut.  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`manifestVersion`|Erforderlich. Dieses Attribut muss auf festgelegt werden `1.0` .|  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht ein- `assembly` Element in einem Bereitstellungs Manifest für eine mit bereitgestellte Anwendung [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Dieses Codebeispiel ist Teil eines größeren Beispiels, das für das [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md) -Thema bereitgestellt wird.  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md)   
 [\<assembly>-Element](../deployment/assembly-element-clickonce-application.md)
