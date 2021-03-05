---
description: Diese Methode ruft ein Property-Objekt ab, das die lokalen, Argumente und anderen Eigenschaften einer Methode enthält.
title: 'Idebugexpressionevaluator:: getmethodproperty | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4d98e661ad3f469c41c120e07e6d54f76b089cb0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152506"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Diese Methode ruft ein Property-Objekt ab, das die lokalen, Argumente und anderen Eigenschaften einer Methode enthält.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMethodProperty( 
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BOOL                  fIncludeHiddenLocals,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodProperty(
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   int                  fIncludeHiddenLocals,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Parameter
`pSymbolProvider`\
in Der zu verwendende Symbol Anbieter, ausgedrückt als [idebugsymbolprovider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) -Objekt.

`pAddress`\
in Die Adresse im Code, ausgedrückt als [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Objekt, das in die nächstgelegene enthaltende Funktion aufgelöst werden soll.

`pBinder`\
in Der zu verwendende Binder, ausgedrückt als [idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) -Objekt.

`fIncludeHiddenLocals`\
in Ungleich NULL ( `TRUE` ) bedeutet, verborgene lokale Variablen einzuschließen; NULL ( `FALSE` ) bedeutet, dass ausgeblendete lokale Variablen ausgeblendet werden.

`ppProperty`\
vorgenommen Gibt ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt zurück, das die Methode darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Verborgene lokale Variablen sind in der Regel Variablen, die vom Compiler generiert werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
