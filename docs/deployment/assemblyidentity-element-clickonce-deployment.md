---
title: '&lt;AssemblyIdentity- &gt; Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
description: Das assemblyIdentity-Element ist bei der ClickOnce-Bereitstellung erforderlich. Sie enthält keine untergeordneten Elemente und verfügt über die in diesem Artikel beschriebenen Attribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a692d37771070f1835fc791515d5dbc24ce6b1b
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383182"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;AssemblyIdentity- &gt; Element (ClickOnce-Bereitstellung)
Identifiziert die primäre Assembly der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.

## <a name="syntax"></a>Syntax

```xml

      <assemblyIdentity  
   name 
   version
   publicKeyToken
   processorArchitecture
    type
/>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `assemblyIdentity`-Element ist erforderlich. Sie enthält keine untergeordneten Elemente und weist die folgenden Attribute auf.

|attribute|Beschreibung|
|---------------|-----------------|
|`name`|Erforderlich. Identifiziert den lesbaren Namen der Bereitstellung zu Informationszwecken.<br /><br /> Wenn `name` Sonderzeichen (z. b. einfache oder doppelte Anführungszeichen) enthält, kann die Anwendung möglicherweise nicht aktiviert werden.|
|`version`|Erforderlich. Gibt die Versionsnummer der Assembly im folgenden Format an: `major.minor.build.revision` .<br /><br /> Dieser Wert muss in einem aktualisierten Manifest inkrementiert werden, um ein Anwendungs Update zu initiieren.|
|`publicKeyToken`|Erforderlich. Gibt eine hexadezimale Zeichenfolge mit 16 Zeichen an, die die letzten 8 Bytes des SHA-1-Hashwerts des öffentlichen Schlüssels darstellt, unter dem das Bereitstellungs Manifest signiert ist. Der öffentliche Schlüssel, der zum Signieren verwendet wird, muss 2048 Bit oder größer sein.<br /><br /> Das Signieren einer Assembly wird zwar empfohlen, ist aber optional, aber dieses Attribut ist erforderlich. Wenn eine Assembly nicht signiert ist, sollten Sie einen Wert aus einer selbst signierten Assembly kopieren oder einen "Dummy"-Wert aller Nullen verwenden.|
|`processorArchitecture`|Erforderlich. Gibt den Prozessor an. Gültige Werte sind `msil` für alle Prozessoren, `x86` für 32-Bit-Windows, `IA64` für 64-Bit-Windows und `Itanium` für Intel 64-Bit-Itanium-Prozessoren.|
|`type`|Erforderlich. Aus Gründen der Kompatibilität mit der parallelen Installation von Windows. Der einzige zulässige Wert ist `win32` .|

## <a name="remarks"></a>Bemerkungen

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht ein- `assemblyIdentity` Element in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungs Manifest. Dieses Codebeispiel ist Teil eines größeren Beispiels, das für das [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md) -Thema bereitgestellt wird.

```xml
<!-- Identify the deployment. -->
<assemblyIdentity
  name="My Application Deployment.app"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>Siehe auch
- [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md)
- [\<assemblyIdentity> gewisses](../deployment/assemblyidentity-element-clickonce-application.md)