---
title: 'IDebugExpressionEvaluator2:: GetService | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb0f822011a5f54cf97e58f53ec1cf03b5d26a23
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926337"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Ruft ein Dienst Objekt unter Berücksichtigung des eindeutigen Bezeichners ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetService (
   GUID        uid,
   IUnknown ** ppService
);
```

```csharp
int GetService (
   Guid       uid,
   out object ppService
);
```

## <a name="parameters"></a>Parameter
`uid`\
in Eindeutiger Bezeichner des abzurufenden Dienstes.

`ppService`\
vorgenommen Gibt ein Objekt zurück, das den Dienst darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Dies kann von der Ausdrucks Auswertung eines Drittanbieters genutzt werden, um Dienste von einer anderen Ausdrucks Auswertung abzurufen. Diese Methode kann z. b. verwendet werden, um die Schnittstelle für den schnell Ansichts Dienst aus der Standard Ausdrucks Auswertung abzurufen. Die Ausdrucks Auswertung von Drittanbietern ist unwahrscheinlich, dass diese Schnittstelle implementiert werden muss.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
