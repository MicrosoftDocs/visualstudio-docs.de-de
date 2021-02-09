---
title: '&lt;publisherIdentity- &gt; Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
description: Das publisherIdentity-Element enthält Informationen zum Verleger, von dem ein Bereitstellungs Manifest signiert wurde. Das-Element ist für signierte Manifeste erforderlich.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65f225f8e3dd3f6d2b3afb2d2a5284d172d4fab1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891292"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity- &gt; Element (ClickOnce-Bereitstellung)
Enthält Informationen zum Herausgeber, der dieses Bereitstellungsmanifest signiert hat.

## <a name="syntax"></a>Syntax

```xml
<publisherIdentity
   name
   issuerKeyHash
/>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das- `publisherIdentity` Element ist für signierte Manifeste erforderlich. In der folgenden Tabelle sind die Attribute aufgeführt, die das- `publisherIdentity` Element unterstützt.

|attribute|Beschreibung|
|---------------|-----------------|
|`name`|Erforderlich. Beschreibt die Identität der Partei, die diese Anwendung veröffentlicht hat.|
|`issuerKeyHash`|Erforderlich. Enthält den SHA-1-Hash des öffentlichen Schlüssels des Zertifikat Ausstellers.|

#### <a name="parameters"></a>Parameter

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

## <a name="exceptions"></a>Ausnahmen

## <a name="remarks"></a>Bemerkungen

## <a name="requirements"></a>Requirements (Anforderungen)

## <a name="subhead"></a>Untertitel