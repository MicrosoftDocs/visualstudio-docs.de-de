---
description: Ruft den Wert ab, auf den als eine Reihe von aufeinander folgenden Bytes gezeigt wird.
title: 'Idebugpointerobject:: GetBytes | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 51d5e4cf65c9e72dada225e042f7d3d11e9b4b4c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169677"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Ruft den Wert ab, auf den als eine Reihe von aufeinander folgenden Bytes gezeigt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int GetBytes(
   uint       dwStart,
   uint       dwCount,
   out byte[] pBytes,
   out uint   pdwBytes
);
```

## <a name="parameters"></a>Parameter
`dwStart`\
in Ein Offset (in Bytes) vom Anfang des Objekts, auf das verwiesen wird.

`dwCount`\
in Die Anzahl der abzurufenden bytes.

`pBytes`\
[in, out] Ein Array, das mit dem Wert als Folge von aufeinander folgenden Bytes gefüllt wird, beginnend mit dem angegebenen Offset aus dem Objekt, auf das verwiesen wird.

`pdwBytes`\
vorgenommen Gibt die Anzahl der tatsächlich abgerufenen Bytes zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird verwendet, wenn der Zeiger, der durch dieses [idebugpointerobject](../../../extensibility/debugger/reference/idebugpointerobject.md) dargestellt wird, auf einen primitiven Typ oder ein einfaches Array primitiver Typen zeigt (d. h. ein Array, das durch eine einfache Bytefolge dargestellt werden kann).

## <a name="see-also"></a>Weitere Informationen
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
