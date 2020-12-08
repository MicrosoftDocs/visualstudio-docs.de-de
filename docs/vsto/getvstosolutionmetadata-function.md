---
title: Getvstosolutionmetadata-Funktion
description: Erfahren Sie, wie die getvstosolutionmetadata-API die Office-Infrastruktur unterstützt und nicht für die direkte Verwendung im Code vorgesehen ist.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 205bde9352e2a037b4a08108d8cfce3460034e66
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845036"
---
# <a name="getvstosolutionmetadata-function"></a>Getvstosolutionmetadata-Funktion
  Diese API unterstützt die Office-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```csharp
HRESULT WINAPI GetVstoSolutionMetadata(
    LPCWSTR lpwszSolutionMetadataKey,
    ISolutionMetadata** ppSolutionInfo
);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*lpwszSolutionMetadataKey*|Verwenden Sie nicht.|
|*ppsolutioninfo*|Verwenden Sie nicht.|

## <a name="return-value"></a>Rückgabewert
 Wenn die Funktion erfolgreich ausgeführt wird, wird **S_OK** zurückgegeben. Wenn die Ausführung der Funktion fehlschlägt, wird ein Fehlercode zurückgegeben.
