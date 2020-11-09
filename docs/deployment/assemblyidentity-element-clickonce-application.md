---
title: '&lt;AssemblyIdentity- &gt; Element (ClickOnce-Anwendung) | Microsoft-Dokumentation'
description: Das assemblyIdentity-Element ist in der ClickOnce-Anwendung erforderlich. Sie enthält keine untergeordneten Elemente und verfügt über die in diesem Artikel beschriebenen Attribute.
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
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c86d5d1fd1e25b498405197b68efd9553ed64f16
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383208"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;AssemblyIdentity- &gt; Element (ClickOnce-Anwendung)
Identifiziert die in einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung bereitgestellte Anwendung.

## <a name="syntax"></a>Syntax

```xml

      <assemblyIdentity
   name
   version
   publicKeyToken
   processorArchitecture
   language
/>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `assemblyIdentity`-Element ist erforderlich. Sie enthält keine untergeordneten Elemente und weist die folgenden Attribute auf.

|attribute|Beschreibung|
|---------------|-----------------|
|`Name`|Erforderlich. Identifiziert den Namen der Anwendung.<br /><br /> Wenn `Name` Sonderzeichen (z. b. einfache oder doppelte Anführungszeichen) enthält, kann die Anwendung möglicherweise nicht aktiviert werden.|
|`Version`|Erforderlich. Gibt die Versionsnummer der Anwendung im folgenden Format an: `major.minor.build.revision`|
|`publicKeyToken`|Optional. Gibt eine hexadezimale Zeichenfolge mit 16 Zeichen an, die die letzten 8 Bytes des `SHA-1` Hashwerts des öffentlichen Schlüssels darstellt, unter dem die Anwendung oder Assembly signiert ist. Der öffentliche Schlüssel, der zum Signieren des Katalogs verwendet wird, muss 2048 Bit oder größer sein.<br /><br /> Das Signieren einer Assembly wird zwar empfohlen, ist aber optional, aber dieses Attribut ist erforderlich. Wenn eine Assembly nicht signiert ist, sollten Sie einen Wert aus einer selbst signierten Assembly kopieren oder einen "Dummy"-Wert aller Nullen verwenden.|
|`processorArchitecture`|Erforderlich. Gibt den Prozessor an. Gültige Werte sind `msil` für alle Prozessoren, `x86` für 32-Bit-Windows, `IA64` für 64-Bit-Windows und `Itanium` für Intel 64-Bit-Itanium-Prozessoren.|
|`language`|Erforderlich. Gibt die zwei teiligen Sprachcodes (z. b `en-US` .) der Assembly an. Dieses Element befindet sich im- `asmv2` Namespace. Wenn nicht angegeben, ist der Standardwert `neutral` .|

## <a name="examples"></a>Beispiele

### <a name="description"></a>BESCHREIBUNG
 Das folgende Codebeispiel veranschaulicht ein- `assemblyIdentity` Element in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungs Manifest. Dieses Codebeispiel ist Teil eines größeren Beispiels, das im [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)bereitgestellt wird.

### <a name="code"></a>Code

```xml
<asmv1:assemblyIdentity
  name="My Application Deployment.exe"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  type="win32" />
```

## <a name="see-also"></a>Siehe auch
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)
- [\<assemblyIdentity> gewisses](../deployment/assemblyidentity-element-clickonce-deployment.md)