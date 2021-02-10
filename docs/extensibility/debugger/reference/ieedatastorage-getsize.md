---
title: 'Ieedatastorage:: GetSize | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2a18ae08500bd457f6e9ab316514836a30538a42
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965511"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Gibt die Anzahl von Bytes zurück, die in diesem-Objekt enthalten sind.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSize(
   ULONG* size
);
```

```csharp
int GetSize(
   out uint size
);
```

## <a name="parameters"></a>Parameter
`size`\
vorgenommen Die Anzahl von Bytes, die in diesem-Objekt enthalten sind.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Verwenden Sie die [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) -Methode, um die tatsächlichen Daten Bytes abzurufen.

## <a name="see-also"></a>Weitere Informationen
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)
