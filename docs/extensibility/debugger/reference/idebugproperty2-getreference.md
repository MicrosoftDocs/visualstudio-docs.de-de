---
description: Gibt einen Verweis auf den Wert der Eigenschaft zurück.
title: 'IDebugProperty2:: getreferenzierung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c103e8826266ddbaaa5b96f4a9aa32067893e45f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166786"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
Gibt einen Verweis auf den Wert der Eigenschaft zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetReference(
   IDebugReference2** ppReference
);
```

```csharp
int GetReference(
   out IDebugReference2 ppReference
);
```

## <a name="parameters"></a>Parameter
`ppRererence`\
vorgenommen Gibt ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) -Objekt zurück, das einen Verweis auf den Wert der Eigenschaft darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird ein Fehlercode zurückgegeben, normalerweise `E_NOTIMPL` oder `E_GETREFERENCE_NO_REFERENCE` .

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
