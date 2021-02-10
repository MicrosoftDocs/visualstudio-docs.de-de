---
title: Implementieren von getmethodproperty | Microsoft-Dokumentation
description: Erfahren Sie, wie Visual Studio mithilfe der getdebugproperty-Eigenschaft der Debug-Engine Informationen über die aktuelle Methode im Stapel Rahmen erhält.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 41150ad7909f15484b9bc035dd9dff70ad693029
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946006"
---
# <a name="implement-getmethodproperty"></a>Implementieren von getmethodproperty
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Visual Studio Ruft die [getdebugproperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)-Methode (de) der Debug-Engine auf, die wiederum [getmethodproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) aufruft, um Informationen über die aktuelle Methode im Stapel Rahmen abzurufen.

Diese Implementierung von `IDebugExpressionEvaluator::GetMethodProperty` führt die folgenden Aufgaben aus:

1. Ruft [getcontainerfield](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)auf und übergibt das [idebugaddress](../../extensibility/debugger/reference/idebugaddress.md) -Objekt. Der Symbol Anbieter (SP) gibt ein [idebugcontainerfield](../../extensibility/debugger/reference/idebugcontainerfield.md) zurück, das die Methode darstellt, die die angegebene Adresse enthält.

2. Ruft das [idebugmethodfield](../../extensibility/debugger/reference/idebugmethodfield.md) aus ab `IDebugContainerField` .

3. Instanziiert eine-Klasse ( `CFieldProperty` in diesem Beispiel genannt), die die [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle implementiert und das `IDebugMethodField` vom SP zurückgegebene-Objekt enthält.

4. Gibt die- `IDebugProperty2` Schnittstelle aus dem- `CFieldProperty` Objekt zurück.

## <a name="managed-code"></a>Verwalteter Code
Dieses Beispiel zeigt eine Implementierung von `IDebugExpressionEvaluator::GetMethodProperty` in verwaltetem Code.

```csharp
namespace EEMC
{
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]
    public class EEMCClass : IDebugExpressionEvaluator
    {
        public HRESULT GetMethodProperty(
                IDebugSymbolProvider symbolProvider,
                IDebugAddress        address,
                IDebugBinder         binder,
                int                  includeHiddenLocals,
            out IDebugProperty2      property)
        {
            IDebugContainerField containerField = null;
            IDebugMethodField methodField       = null;
            property = null;

            // Get the containing method field.
            symbolProvider.GetContainerField(address, out containerField);
            methodField = (IDebugMethodField) containerField;

            // Return the property of method field.
            property = new CFieldProperty(symbolProvider, address, binder, methodField);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Nicht verwalteter Code
Dieses Beispiel zeigt eine Implementierung von `IDebugExpressionEvaluator::GetMethodProperty` in nicht verwaltetem Code.

```
[CPP]
STDMETHODIMP CExpressionEvaluator::GetMethodProperty(
        in IDebugSymbolProvider *pprovider,
        in IDebugAddress        *paddress,
        in IDebugBinder         *pbinder,
        in BOOL                  includeHiddenLocals,
        out IDebugProperty2    **ppproperty
    )
{
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    IDebugContainerField* pcontainer = NULL;

    hr = pprovider->GetContainerField(paddress, &pcontainer);
    if (FAILED(hr))
        return hr;

    IDebugMethodField*    pmethod    = NULL;
    hr = pcontainer->QueryInterface( IID_IDebugMethodField,
            reinterpret_cast<void**>(&pmethod));
    pcontainer->Release();
    if (FAILED(hr))
        return hr;

    CFieldProperty* pfieldProperty = new CFieldProperty( pprovider,
                                                         paddress,
                                                         pbinder,
                                                         pmethod );
    pmethod->Release();
    if (!pfieldProperty)
        return E_OUTOFMEMORY;

    hr = pfieldProperty->Init();
    if (FAILED(hr))
    {
        pfieldProperty->Release();
        return hr;
    }

    hr = pfieldProperty->QueryInterface( IID_IDebugProperty2,
            reinterpret_cast<void**>(ppproperty));
    pfieldProperty->Release();

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [Beispiel Implementierung von lokalen Variablen](../../extensibility/debugger/sample-implementation-of-locals.md)
