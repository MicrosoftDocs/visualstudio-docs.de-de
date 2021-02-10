---
title: 'Idebugpointerobject:: SetBytes | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 57f1a077923a174ece5323256ad474dda3ec685f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952277"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Legt den Wert fest, auf den aus einer Reihe von aufeinander folgenden Bytes gezeigt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int SetBytes(
   uint     dwStart,
   uint     dwCount,
   byte[]   pBytes,
   out uint pdwBytes
);
```

## <a name="parameters"></a>Parameter
`dwStart`\
in Ein Offset (in Bytes) vom Anfang des Objekts, auf das verwiesen wird.

`dwCount`\
in Die Anzahl der festzulegenden bytes.

`pBytes`\
in Ein Bytearray, das den neuen Wert darstellt. Dieser Wert wird im-Objekt gespeichert, beginnend beim angegebenen Offset.

`pdwBytes`\
vorgenommen Gibt die Anzahl der tatsächlich festgelegten Bytes zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird verwendet, wenn der Zeiger, der durch dieses [idebugpointerobject](../../../extensibility/debugger/reference/idebugpointerobject.md) dargestellt wird, auf einen primitiven Typ oder ein einfaches Array primitiver Typen zeigt (d. h. ein Array, das durch eine einfache Bytefolge dargestellt werden kann). Dieses `IDebugPointerObject` Objekt kann kein NULL-Verweis sein (es muss auf eine Adresse im Arbeitsspeicher verweisen).

## <a name="see-also"></a>Weitere Informationen
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
