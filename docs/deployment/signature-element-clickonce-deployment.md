---
title: '&lt;Signature- &gt; Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
description: Das Signature-Element enthält die erforderlichen Informationen zum digitalen Signieren dieses Bereitstellungs Manifests. Das Signieren eines Bereitstellungs Manifests ist optional, wird jedoch empfohlen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5d95398285d9106719f3c2444d54202b81cfee4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877498"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Signature- &gt; Element (ClickOnce-Bereitstellung)
Enthält die notwendigen Informationen, um dieses Bereitstellungsmanifest digital zu signieren.

## <a name="syntax"></a>Syntax

```xml

<Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>Bemerkungen
 Das Signieren eines Bereitstellungs Manifests mithilfe einer Umschlag Signatur ist optional, wird jedoch empfohlen. Weitere Informationen zum Signieren von XML-Dateien finden Sie in der World Wide Web Consortium Empfehlung "Syntax und Verarbeitung von XML-Signaturen" unter [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/) .

 Wenn Sie das Manifest signieren möchten, müssen Sie Hashes für alle Dateien bereitstellen. Ein Manifest mit Dateien, die nicht als Hash verwendet werden, kann nicht signiert werden, da Benutzer den Inhalt von Dateien ohne Hash überprüfen können.

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht ein- `Signature` Element in einem Bereitstellungs Manifest, das in einer- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung verwendet wird.

```xml
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
  <SignedInfo>
    <CanonicalizationMethod Algorithm=
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />
    <SignatureMethod Algorithm=
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />
    <Reference URI="">
      <Transforms>
        <Transform Algorithm=
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
      </Transforms>
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <DigestValue>d2z5AE...</DigestValue>
    </Reference>
  </SignedInfo>
  <SignatureValue>
4PHj6SaopoLp...
  </SignatureValue>
  <KeyInfo>
    <X509Data>
      <X509Certificate>
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...
      </X509Certificate>
    </X509Data>
  </KeyInfo>
</Signature>
```

## <a name="see-also"></a>Weitere Informationen
- [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md)
