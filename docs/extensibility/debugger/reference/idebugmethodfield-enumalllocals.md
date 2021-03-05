---
description: Erstellt einen Enumerator für alle lokalen Variablen der Methode, einschließlich derjenigen, die intern von einem Compiler generiert werden.
title: 'Idebugmethodfield:: enumalllocals | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38f14ba2d520974b9f8f567c7840737ed2763080
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172167"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Erstellt einen Enumerator für alle lokalen Variablen der Methode, einschließlich derjenigen, die intern von einem Compiler generiert werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
in Ein [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Objekt, das eine debugadresse innerhalb der Methode darstellt, die auf einen bestimmten Bereich oder Kontext verweist.

`ppLocals`\
vorgenommen Gibt ein [ienumdebug Fields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste aller lokalen Variablen im angegebenen Bereich darstellt. Andernfalls wird ein NULL-Wert zurückgegeben, der keine lokalen Variablen angibt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben, oder es wird S_FALSE zurückgegeben, wenn keine lokalen vorhanden sind Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Nur die Variablen, die in dem Block definiert sind, der die angegebene debugadresse enthält, werden aufgezählt. Diese Methode schließt alle vom Compiler generierten lokalen Variablen ein. Wenn nur die lokalen Variablen in der Quelle explizit definiert sind, müssen Sie die [enumlocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) -Methode aufzurufen.

 Eine Methode kann mehrere Bereichs bezogene Kontexte oder Blöcke enthalten.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
