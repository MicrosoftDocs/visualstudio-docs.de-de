---
description: Erstellt einen Enumerator für ausgewählte lokale Variablen der Methode.
title: 'Idebugmethodfield:: enumlocals | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d99b6e4b3cf30cccd4a2785f3712b34d9471bdd8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166332"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Erstellt einen Enumerator für ausgewählte lokale Variablen der Methode.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumLocals(
    IDebugAddress*     pAddress,
    IEnumDebugFields** ppLocals
);
```

```csharp
int EnumLocals(
    IDebugAddress        pAddress,
    out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
in Ein [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Objekt, das die debugadresse darstellt, mit der der Kontext oder der Gültigkeitsbereich für die lokalen Variablen ausgewählt wird.

`ppLocals`\
vorgenommen Gibt ein [ienumdebug Fields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das eine Liste der lokalen Variablen darstellt. Andernfalls wird ein NULL-Wert zurückgegeben, wenn keine lokalen vorhanden sind.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird S_OK zurückgegeben, oder es wird S_FALSE zurückgegeben, wenn keine lokalen vorhanden sind Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Nur die Variablen, die in dem Block definiert sind, der die angegebene debugadresse enthält, werden aufgezählt. Wenn alle lokalen Variablen, einschließlich der vom Compiler generierten lokalen Variablen, benötigt werden, müssen Sie die [enumalllocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) -Methode aufrufen.

Eine Methode kann mehrere Bereichs bezogene Kontexte oder Blöcke enthalten. Beispielsweise enthält die folgende erfunderte Methode drei Bereiche, die beiden inneren Blöcke und den Methoden Text selbst.

```csharp
public void func(int index)
{
    // Method body scope
    int a = 0;
    if (index == 1)
    {
        // Inner scope 1
        int temp1 = a;
    }
    else
    {
        // Inner scope 2
        int temp2 = a;
    }
}
```

Das [idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md) -Objekt stellt die `func` Methode selbst dar. Das Aufrufen der- `EnumLocals` Methode mit einer [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) , die auf die Adresse festgelegt `Inner Scope 1` ist, gibt eine Enumeration zurück, die die `temp1` Variable enthält, z.b..

## <a name="see-also"></a>Weitere Informationen
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
