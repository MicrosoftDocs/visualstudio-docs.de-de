---
title: 'Idebugexpressionevaluator:: getmethodlocationproperty | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13759bc8598c4739fbb9d2263dd8dc7d1b84c16e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930420"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Diese Methode konvertiert einen Methoden Speicherort und Offset in eine Speicheradresse.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMethodLocationProperty( 
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodLocationProperty(
   string               upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Parameter
`upstrFullyQualifiedMethodPlusOffset`\
in Der Speicherort und der Offset der Methode als Zeichenfolge.

`pSymbolProvider`\
in Der Symbol Anbieter, ausgedrückt als [idebugsymbolprovider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) -Objekt.

`pAddress`\
in Eine Adresse innerhalb der Methode, ausgedrückt als [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Objekt.

`pBinder`\
in Der als [idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) -Objekt ausgedrückte Binder.

`ppProperty`\
vorgenommen Gibt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle zurück, die die Speicheradresse darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die zurückgegebene Adresse kann z. b. zum Festlegen eines Breakpoints verwendet werden.

 Trotz des namens `upstrFullyQualifiedMethodPlusOffset` kann diesem Parameter ein teilweise qualifizierter Methodenname übergeben werden. In diesem Fall ist die ausgewählte Methode die Methode, die geschlossen wird `pAddress` . Die Art und Weise, wie dieser Parameter interpretiert wird, ist die Implementierung der Ausdrucks Auswertung und der unterstützten Sprache.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
