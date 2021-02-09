---
title: Ensurevstocomponent-Funktion
description: Erfahren Sie, wie die ensurevstocomponent-API die Office-Infrastruktur unterstützt und nicht für die direkte Verwendung im Code vorgesehen ist.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 17f52a469d93a843ef776c125e15a37db22277e8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910483"
---
# <a name="ensurevstocomponent-function"></a>Ensurevstocomponent-Funktion
  Diese API unterstützt die Office-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```csharp
HRESULT EnsureVSTOComponent(
    IVSTProject *pProject
);
```

#### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*pproject*|Verwenden Sie nicht.|

## <a name="return-value"></a>Rückgabewert
 Wenn die Funktion erfolgreich ausgeführt wird, wird **S_OK** zurückgegeben. Wenn die Ausführung der Funktion fehlschlägt, wird ein Fehlercode zurückgegeben.
