---
title: Auswerten eines Überwachungs Ausdrucks | Microsoft-Dokumentation
description: Erfahren Sie, wie Visual Studio evaluatesync verwendet, wenn es bereit ist, den Wert eines Watch-Ausdrucks anzuzeigen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d7433c9d4c2d5851dc5078a41c33a4391a75d86
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915673"
---
# <a name="evaluate-a-watch-expression"></a>Auswerten eines Überwachungs Ausdrucks
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Wenn Visual Studio bereit ist, den Wert eines Watch-Ausdrucks anzuzeigen, wird [evaluatesync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)aufgerufen, das wiederum [evaluatesync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)aufruft. Dieser Prozess erzeugt ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Objekt, das den Wert und den Typ des Ausdrucks enthält.

In dieser Implementierung von `IDebugParsedExpression::EvaluateSync` wird der Ausdruck analysiert und gleichzeitig ausgewertet. Diese Implementierung führt die folgenden Aufgaben aus:

1. Analysiert und wertet den Ausdruck aus, um ein generisches Objekt zu schaffen, das den Wert und dessen Typ enthält. In c# wird dies als `object` while in C++ dargestellt, das als dargestellt wird `VARIANT` .

2. Instanziiert eine-Klasse ( `CValueProperty` in diesem Beispiel genannt), die die `IDebugProperty2` -Schnittstelle implementiert, und speichert in der-Klasse den Wert, der zurückgegeben werden soll.

3. Gibt die- `IDebugProperty2` Schnittstelle aus dem- `CValueProperty` Objekt zurück.

## <a name="managed-code"></a>Verwalteter Code
Dies ist eine Implementierung von `IDebugParsedExpression::EvaluateSync` in verwaltetem Code. Die-Hilfsmethode `Tokenize` analysiert den Ausdruck in eine Analyse Struktur. Die-Hilfsfunktion `EvalToken` konvertiert das Token in einen-Wert. Die Hilfsfunktion durchläuft die Analyse Struktur `FindTerm` rekursiv und ruft `EvalToken` für jeden Knoten, der einen Wert darstellt, auf und wendet alle Vorgänge (Addition oder Subtraktion) im Ausdruck an.

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT EvaluateSync(
            uint evalFlags,
            uint timeout,
            IDebugSymbolProvider provider,
            IDebugAddress address,
            IDebugBinder binder,
            string resultType,
            out IDebugProperty2 result)
        {
            HRESULT retval = COM.S_OK;
            this.evalFlags = evalFlags;
            this.timeout = timeout;
            this.provider = provider;
            this.address = address;
            this.binder = binder;
            this.resultType = resultType;

            try
            {
                IDebugField field = null;
                // Tokenize, then parse.
                tokens = Tokenize(expression);
                result = new CValueProperty(
                        expression,
                        (int) FindTerm(EvalToken(tokens[0], out field),1),
                        field,
                        binder);
            }
            catch (ParseException)
            {
                result = new CValueProperty(expression, "Huh?");
                retval = COM.E_INVALIDARG;
            }
            return retval;
        }
    }
}
```

## <a name="unmanaged-code"></a>Nicht verwalteter Code
Dies ist eine Implementierung von `IDebugParsedExpression::EvaluateSync` in nicht verwaltetem Code. Die Hilfsfunktion `Evaluate` analysiert und wertet den Ausdruck aus und gibt einen zurück, `VARIANT` der den resultierenden Wert enthält. Die-Hilfsfunktion `VariantValueToProperty` bündelt das- `VARIANT` Objekt in ein- `CValueProperty` Objekt.

```cpp
STDMETHODIMP CParsedExpression::EvaluateSync(
    in  DWORD                 evalFlags,
    in  DWORD                 dwTimeout,
    in  IDebugSymbolProvider* pprovider,
    in  IDebugAddress*        paddress,
    in  IDebugBinder*         pbinder,
    in  BSTR                  bstrResultType,
    out IDebugProperty2**     ppproperty )
{
    // dwTimeout parameter is ignored in this implementation.
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (paddress == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    VARIANT value;
    BSTR    bstrErrorMessage = NULL;
    hr = ::Evaluate( pprovider,
                     paddress,
                     pbinder,
                     m_expr,
                     &bstrErrorMessage,
                     &value );
    if (hr != S_OK)
    {
        if (bstrErrorMessage == NULL)
            return hr;

        //we can display better messages ourselves.
        HRESULT hrLocal = S_OK;
        VARIANT varType;
        VARIANT varErrorMessage;

        VariantInit( &varType );
        VariantInit( &varErrorMessage );
        varErrorMessage.vt      = VT_BSTR;
        varErrorMessage.bstrVal = bstrErrorMessage;

        CValueProperty* valueProperty = new CValueProperty();
        if (valueProperty != NULL)
        {
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);
            if (SUCCEEDED(hrLocal))
            {
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,
                        reinterpret_cast<void**>(ppproperty) );
            }
        }

        VariantClear(&varType);
        VariantClear(&varErrorMessage); //frees BSTR
        if (!valueProperty)
            return hr;
        valueProperty->Release();
        if (FAILED(hrLocal))
            return hr;
    }
    else
    {
        if (bstrErrorMessage != NULL)
            SysFreeString(bstrErrorMessage);

        hr = VariantValueToProperty( pprovider,
                                     paddress,
                                     pbinder,
                                     m_radix,
                                     m_expr,
                                     value,
                                     ppproperty );
        VariantClear(&value);
        if (FAILED(hr))
            return hr;
    }

    return S_OK;
}
```

## <a name="see-also"></a>Weitere Informationen
- [Auswerten eines Überwachungs Fenster Ausdrucks](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Beispiel Implementierung der Ausdrucks Auswertung](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
