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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a04cfc249efa4640df2b2e4b1c5f4b43ed52ace2
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846115"
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
