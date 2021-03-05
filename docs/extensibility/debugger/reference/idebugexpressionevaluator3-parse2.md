---
description: Konvertiert eine Ausdrucks Zeichenfolge in einen analysierten Ausdruck, wenn der Symbol Anbieter und die Adresse des Auswertungs Rahmens angegeben sind.
title: IDebugExpressionEvaluator3::P arse2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3::Parse2
ms.assetid: 78099628-d600-4f76-b7c8-ee07c864af1e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39edfbcdec6f634307c61b3db4ac76b238ac3614
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152207"
---
# <a name="idebugexpressionevaluator3parse2"></a>IDebugExpressionEvaluator3::Parse2
Konvertiert eine Ausdrucks Zeichenfolge in einen analysierten Ausdruck, wenn der Symbol Anbieter und die Adresse des Auswertungs Rahmens angegeben sind.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Parse2 (
    LPCOLESTR                upstrExpression,
    PARSEFLAGS               dwFlags,
    UINT                     nRadix,
    IDebugSymbolProvider*    pSymbolProvider,
    IDebugAddress*           pAddress,
    BSTR*                    pbstrError,
    UINT*                    pichError,
    IDebugParsedExpression** ppParsedExpression
);
```

```csharp
HRESULT Parse2 (
    string                     upstrExpression,
    enum_PARSEFLAGS            dwFlags,
    uint                       nRadix,
    IDebugSymbolProvider       pSymbolProvider,
    IDebugAddress              pAddress,
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

`pSymbolProvider`\
in Schnittstelle des Symbol Anbieters.

`pAddress`\
in Adresse des Auswertungs Rahmens.

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

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird gezeigt, wie diese Methode für ein **CEE** -Objekt implementiert wird, das die [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md) -Schnittstelle verfügbar macht.

```cpp
HRESULT CEE::Parse2 ( LPCOLESTR in_szExprText,
  PARSEFLAGS in_FLAGS,
  UINT in_RADIX,
  IDebugSymbolProvider *pSymbolProvider,
  IDebugAddress *pAddress,
  BSTR* out_pbstrError,
  UINT* inout_pichError,
  IDebugParsedExpression** out_ppParsedExpression )
{
    // precondition
    REQUIRE( NULL != in_szExprText );
    //REQUIRE( NULL != out_pbstrError );
    REQUIRE( NULL != inout_pichError );
    REQUIRE( NULL != out_ppParsedExpression );

    if (NULL == in_szExprText)
        return E_INVALIDARG;

    if (NULL == inout_pichError)
        return E_POINTER;

    if (NULL == out_ppParsedExpression)
        return E_POINTER;

    if (out_pbstrError)
        *out_pbstrError = NULL;

    *out_ppParsedExpression = NULL;

    INVARIANT( this );

    if (!this->ClassInvariant())
        return E_UNEXPECTED;

    // function body
    EEDomain::fParseExpression DomainVal =
    {
        this,                   // CEE*
        in_szExprText,          // LPCOLESTR
        in_FLAGS,               // EVALFLAGS
        in_RADIX,               // RADIX
        out_pbstrError,         // BSTR*
        inout_pichError,        // UINT*
        pSymbolProvider,
        out_ppParsedExpression  // Output
    };

    return (*m_LanguageSpecificUseCases.pfParseExpression)(DomainVal);
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)
