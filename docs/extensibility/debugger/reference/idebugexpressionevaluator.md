---
description: Diese Schnittstelle stellt die Ausdrucks Auswertung dar.
title: Idebugexpressionevaluator | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b2e1fb465155bac2aa4be2b0d0a041715bf63bfa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152350"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Diese Schnittstelle stellt die Ausdrucks Auswertung dar.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Diese Schnittstelle muss von der Ausdrucks Auswertung implementiert werden.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Um diese Schnittstelle zu erhalten, instanziieren Sie die Ausdrucks Auswertung `CoCreateInstance` mithilfe der-Methode, indem Sie die Klassen-ID (CLSID) der Auswertung verwenden. Weitere Informationen finden Sie im Beispiel.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugExpressionEvaluator` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Konvertiert eine Ausdrucks Zeichenfolge in einen analysierten Ausdruck.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Ruft die lokalen Variablen, Argumente und andere Eigenschaften einer Methode ab.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Konvertiert einen Methoden Speicherort und Offset in eine Speicheradresse.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Bestimmt, welche Sprache zum Erstellen von druckbaren Ergebnissen verwendet werden soll.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Legt den Registrierungs Stamm fest. Wird für Paralleles Debuggen verwendet.|

## <a name="remarks"></a>Bemerkungen
In einer typischen Situation instanziiert die Debug-Engine (de) die Ausdrucks Auswertung (EE) als Ergebnis eines Aufrufes von " [bisetext](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)". Da der de die Sprache und den Anbieter der EE kennt, die er verwenden möchte, ruft der de die CLSID des EE aus der Registrierung ab (die SDK-Hilfsprogramme [für die Debugfunktion](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , `GetEEMetric` , hilft bei diesem Abruf).

Nachdem der EE instanziiert wurde, ruft der de-Ausdruck [auf, um](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) den Ausdruck zu analysieren und in einem [idebugzisedexpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) -Objekt zu speichern. Später wertet ein [aufrufsausdruck für evaluatesync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) den Ausdruck aus.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: EE. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt, wie die Ausdrucks Auswertung mithilfe eines Symbol Anbieters und einer Adresse im Quellcode instanziiert wird. In diesem Beispiel wird eine Funktion, `GetEEMetric` , aus den SDK-Hilfsprogrammen [zum Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) der Bibliothek "dbgmetric. lib" verwendet.

```cpp
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,
                                                 IDebugAddress *pSourceAddress)
{
    // This is typically defined globally but is specified here just
    // for this example.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";

    IDebugExpressionEvaluator *pEE = NULL;
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {
        HRESULT hr         = S_OK;
        GUID  languageGuid = { 0 };
        GUID  vendorGuid   = { 0 };

        hr = pSymbolProvider->GetLanguage(pSourceAddress,
                                          &languageGuid,
                                          &vendorGuid);
        if (SUCCEEDED(hr)) {
            CLSID clsidEE = { 0 };
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;
            // Get the expression evaluator's CLSID from the registry.
            ::GetEEMetric(languageGuid,
                          vendorGuid,
                          metricCLSID,
                          &clsidEE,
                          strRegistrationRoot);
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {
                // Instantiate the expression evaluator.
                spExpressionEvaluator.CoCreateInstance(clsidEE);
            }
            if (spExpressionEvaluator != NULL) {
                pEE = spExpressionEvaluator.Detach();
            }
        }
    }
    return pEE;
}
```

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
