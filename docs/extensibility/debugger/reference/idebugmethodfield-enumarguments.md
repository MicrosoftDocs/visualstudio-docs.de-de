---
description: Erstellt einen Enumerator für den Typ jedes Arguments, das erforderlich ist, um die Methode aufzurufen.
title: 'Idebugmethodfield:: enumarguments | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04815bb1fc148893c5b594223f6b92bfb7e0d97f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172124"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Erstellt einen Enumerator für den Typ jedes Arguments, das erforderlich ist, um die Methode aufzurufen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parameter
`ppParams`\
vorgenommen Gibt ein [ienumdebug Fields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste der Argument Typen darstellt. Gibt einen NULL-Wert zurück, wenn keine Argumente vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben oder S_FALSE zurückgegeben, wenn keine Argumente vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Jedes Element ist ein [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt, das die Typen der einzelnen Parameter darstellt. Rufen Sie die [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) -Methode auf, um Informationen über den Typ der einzelnen Parameter abzurufen.

 Wenn der Name des Parameters zusammen mit dem Typ benötigt wird, müssen Sie die [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) -Methode aufrufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
