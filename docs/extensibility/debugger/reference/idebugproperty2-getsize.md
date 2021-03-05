---
description: Ruft die Größe des Eigenschafts Werts in Bytes ab.
title: 'IDebugProperty2:: GetSize | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd6342efd1d9bcb2d2ac063438ee741df3c61325
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166813"
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
Ruft die Größe des Eigenschafts Werts in Bytes ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSize ( 
   DWORD* pdwSize
);
```

```csharp
int GetSize ( 
   out uint pdwSize
);
```

## <a name="parameters"></a>Parameter
`pdwSize`\
vorgenommen Gibt die Größe des Eigenschafts Werts in Byte zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben. Gibt zurück, `S_GETSIZE_NO_SIZE` Wenn die Eigenschaft keine Größe hat.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
