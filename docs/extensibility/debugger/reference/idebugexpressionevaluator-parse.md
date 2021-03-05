---
description: Diese Methode konvertiert eine Ausdrucks Zeichenfolge in einen analysierten Ausdruck.
title: Idebugexpressionevaluator::P Arse | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f6a586c7e7cac1a4ef034b7941840db59d376180
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152493"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Diese Methode konvertiert eine Ausdrucks Zeichenfolge in einen analysierten Ausdruck.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Parse( 
   LPCOLESTR                upstrExpression,
   PARSEFLAGS               dwFlags,
   UINT                     nRadix,
   BSTR*                    pbstrError,
   UINT*                    pichError,
   IDebugParsedExpression** ppParsedExpression
);
```

```csharp
int Parse(
   string                     upstrExpression,
   enum_PARSEFLAGS            dwFlags,
   uint                       nRadix,
   out string                 pbstrError,
   out uint                   pichError,
   out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>Parameter
`upstrExpression`\
in Die Ausdrucks Zeichenfolge, die analysiert werden soll.

`dwFlags`\
in Eine Auflistung der [Parameterflags](../../../extensibility/debugger/reference/parseflags.md) -Konstanten, die bestimmen, wie der Ausdruck analysiert werden soll.

`nRadix`\
in Radix, das zum Interpretieren numerischer Informationen verwendet werden soll.

`pbstrError`\
vorgenommen Gibt den Fehler als menschenlesbaren Text zurück.

`pichError`\
vorgenommen Gibt die Zeichenposition des Starts des Fehlers in der Ausdrucks Zeichenfolge zurück.

`ppParsedExpression`\
vorgenommen Gibt den analysierten Ausdruck in einem [idebugobjesedexpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) -Objekt zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode erzeugt einen analysierten Ausdruck, kein tatsächlicher Wert. Ein analysierte Ausdruck ist für die Auswertung bereit, d. h. in einen-Wert konvertiert.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
