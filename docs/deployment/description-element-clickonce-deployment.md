---
title: '&lt;Description- &gt; Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
description: Das Description-Element identifiziert Anwendungsinformationen, die zum Erstellen einer shellpräsenz und eines Elements "Software" in der Systemsteuerung verwendet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4eb1de8f5692eedc9673f1a22cb448ac8d102ae5
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382831"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Description- &gt; Element (ClickOnce-Bereitstellung)
Identifiziert Anwendungsinformationen, die verwendet werden, um in der Systemsteuerung eine shellpräsenz und **ein Element "** Software" zu erstellen.

## <a name="syntax"></a>Syntax

```xml

      <description 
   publisher 
   product
   suiteName
   supportUrl
/>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `description` -Element ist erforderlich und befindet sich im `urn:schemas-microsoft-com:asm.v1` -Namespace. Sie enthält keine untergeordneten Elemente und weist die folgenden Attribute auf.

|attribute|Beschreibung|
|---------------|-----------------|
|`publisher`|Erforderlich. Identifiziert den Firmennamen, der für die Symbolplatzierung im **Windows-Startmenü** und **das Element Software in der System** Steuerung verwendet wird, wenn die Bereitstellung für die Installation konfiguriert ist.|
|`product`|Erforderlich. Identifiziert den vollständigen Produktnamen. Wird als Titel für das Symbol verwendet, das im Windows- **Startmenü** installiert ist.|
|`suiteName`|Optional. Identifiziert einen Unterordner innerhalb des `publisher` Ordners im Windows- **Startmenü** .|
|`supportUrl`|Optional. Gibt eine Support-URL an **, die im Element Software** in der Systemsteuerung angezeigt wird. Eine Verknüpfung zu dieser URL wird auch für die Anwendungsunterstützung im Windows- **Startmenü** erstellt, wenn die Bereitstellung für die Installation konfiguriert ist.|

## <a name="remarks"></a>Hinweise
 Das Description-Element ist in allen Bereitstellungs Konfigurationen erforderlich.

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht ein- `description` Element in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungs Manifest. Dieses Codebeispiel ist Teil eines größeren Beispiels, das für das [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md) -Thema bereitgestellt wird.

```xml
<description
  asmv2:publisher="My Company Name"
  asmv2:product="My Application"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>Siehe auch
- [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md)