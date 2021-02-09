---
title: 'Idebugfield:: getextendedinfo | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 911556cb615e373d620b496fb31e5d6093b7cc37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869933"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Diese Methode erhält erweiterte Informationen zu einem Feld.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetExtendedInfo( 
   REFGUID guidExtendedInfo,
   BYTE**  prgBuffer,
   DWORD*  pdwLen
);
```

```csharp
int GetExtendedInfo(
   ref Guid guidExtendedInfo,
   IntPtr[] prgBuffer,
   ref uint pdwLen
);
```

## <a name="parameters"></a>Parameter
`guidExtendedInfo`\
in Wählt die Informationen aus, die zurückgegeben werden sollen. Gültige Werte sind:

|Wert|Beschreibung|
|-----------|-----------------|
|`guidConstantValue`|Der-Wert als Bytefolge.|
|`guidConstantType`|Der Typ als Typsignatur.|

`prgBuffer`\
vorgenommen Gibt die erweiterten Informationen zurück.

`pdwLen`\
[in, out] Gibt die Größe der erweiterten Informationen in Bytes zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Derzeit gibt diese Methode nur den Typ oder den Wert einer Konstanten zurück. Der Aufrufer muss den in zurückgegebenen Puffer `prgBuffer` durch Aufrufen der com- `CoTaskMemFree` Funktion (C++) oder <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (c#) freigeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
