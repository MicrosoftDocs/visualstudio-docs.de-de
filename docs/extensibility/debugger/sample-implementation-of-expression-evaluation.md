---
title: Beispiel Implementierung der Ausdrucks Auswertung | Microsoft-Dokumentation
description: Erfahren Sie, wie Visual Studio "paramesetext" aufruft, um ein IDebugExpression2-Objekt für einen Windows-Überwachungs Ausdruck zu entwickeln.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec7ddd5270fdac3513c3f63673e5a5f3d05464b5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960948"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Beispiel Implementierung der Ausdrucks Auswertung
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bei einem **Überwachungs** Fenster Ausdruck ruft Visual Studio " [paramesetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) " auf, um ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Objekt zu entwickeln. `IDebugExpressionContext2::ParseText` instanziiert eine Ausdrucks Auswertung (EE) [und ruft die](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) Analyse auf, um ein [idebugzisedexpression](../../extensibility/debugger/reference/idebugparsedexpression.md) -Objekt zu erhalten.

 `IDebugExpressionEvaluator::Parse`Führt die folgenden Aufgaben aus:

1. [Nur C++] Analysiert den Ausdruck, um nach Fehlern zu suchen.

2. Instanziiert eine-Klasse ( `CParsedExpression` in diesem Beispiel aufgerufen), mit der die `IDebugParsedExpression` -Schnittstelle ausgeführt und der Ausdruck in der-Klasse gespeichert wird, der analysiert werden soll.

3. Gibt die- `IDebugParsedExpression` Schnittstelle aus dem- `CParsedExpression` Objekt zurück.

> [!NOTE]
> In den folgenden Beispielen und im mycee-Beispiel wird die Analyse von der Ausdrucks Auswertung nicht getrennt.

## <a name="managed-code"></a>Verwalteter Code
 Der folgende Code zeigt eine Implementierung von `IDebugExpressionEvaluator::Parse` in verwaltetem Code. Mit dieser Version der Methode wird die Analyse auf [evaluatesync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) festgelegt, da der Code für die Analyse auch gleichzeitig ausgewertet wird (siehe [Auswerten eines Überwachungs Ausdrucks](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT Parse(
                string                 expression,
                uint                   parseFlags,
                uint                   radix,
            out string                 errorMessage,
            out uint                   errorPosition,
            out IDebugParsedExpression parsedExpression)
        {
            errorMessage = "";
            errorPosition = 0;

            parsedExpression =
                new CParsedExpression(parseFlags, radix, expression);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Nicht verwalteter Code
Der folgende Code ist eine Implementierung von `IDebugExpressionEvaluator::Parse` in nicht verwaltetem Code. Diese Methode ruft eine Hilfsfunktion `Parse` auf,, um den Ausdruck zu analysieren und auf Fehler zu überprüfen. diese Methode ignoriert jedoch den resultierenden Wert. Die formale Auswertung wird an [evaluatesync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) zurückgestellt, wo der Ausdruck analysiert wird, während er ausgewertet wird (siehe [Auswerten eines Überwachungs Ausdrucks](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```cpp
STDMETHODIMP CExpressionEvaluator::Parse(
        in    LPCOLESTR                 pszExpression,
        in    PARSEFLAGS                flags,
        in    UINT                      radix,
        out   BSTR                     *pbstrErrorMessages,
        inout UINT                     *perrorCount,
        out   IDebugParsedExpression  **ppparsedExpression
    )
{
    if (pbstrErrorMessages == NULL)
        return E_INVALIDARG;
    else
        *pbstrErrormessages = 0;

    if (pparsedExpression == NULL)
        return E_INVALIDARG;
    else
        *pparsedExpression = 0;

    if (perrorCount == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    // Look for errors in the expression but ignore results
    hr = ::Parse( pszExpression, pbstrErrorMessages );
    if (hr != S_OK)
        return hr;

    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );
    if (!pparsedExpr)
        return E_OUTOFMEMORY;

    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,
                                      reinterpret_cast<void**>(ppparsedExpression) );
    pparsedExpr->Release();

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [Auswerten eines Überwachungsfenster Ausdrucks](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Auswerten eines Überwachungs Ausdrucks](../../extensibility/debugger/evaluating-a-watch-expression.md)
