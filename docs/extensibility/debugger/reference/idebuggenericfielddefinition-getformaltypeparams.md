---
title: 'Idebuggenericfielddefinition:: getformaltypeparameams | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetFormalTypeParams
- IDebugGenericFieldDefinition::GetFormalTypeParams
ms.assetid: cadbd6a1-bc7c-4aff-8777-5396b7a23c3e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aa1401181f844be2e1fa3dfd9e45b627e2daae19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904589"
---
# <a name="idebuggenericfielddefinitiongetformaltypeparams"></a>IDebugGenericFieldDefinition::GetFormalTypeParams
Ruft die Typparameter ab, wenn die Anzahl der Parameter angegeben ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetFormalTypeParams(
   ULONG32                   cParams,
   IDebugGenericParamField** ppParams,
   ULONG32*                  pcParams
);
```

```csharp
int GetFormalTypeParams(
   uint                          cParams,
   out IDebugGenericParamField[] ppParams,
   ref uint                      pcParams
);
```

## <a name="parameters"></a>Parameter
`cParams`\
in Anzahl von Parametern.

`ppParams`\
vorgenommen Array von Typparametern.

`pcParams`\
[in, out] Anzahl der Parameter im `ppParams` Array.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Gibt die Typparameter in der Reihenfolge von links nach rechts zurück. Das Wörterbuch gibt beispielsweise " \<K,V> idebugformalgenericparameters {K, V}" zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
