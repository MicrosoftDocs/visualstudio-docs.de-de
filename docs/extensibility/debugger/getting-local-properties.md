---
title: Erhalten von lokalen Eigenschaften | Microsoft-Dokumentation
description: Erfahren Sie, wie Visual Studio enumchildren verwendet, um lokale Eigenschaften mit diesen Beispielen für verwalteten und nicht verwalteten Code zu erhalten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, getting local properties
- debugging [Debugging SDK], local properties
- expression evaluation, local properties
ms.assetid: 6c3a79e8-1ba1-4863-97c3-0216c3d9f092
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17b6d104f88999ba7dd8e115a752a78853af6603
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560017"
---
# <a name="get-local-properties"></a>Lokale Eigenschaften erhalten
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

In Visual Studio werden [enumchildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) aufgerufen, um ein [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) -Objekt zu erhalten, das Zugriff auf alle lokal bereit **gestellten lokalen Variablen** bietet, die im Fenster Lokal angezeigt werden. Visual Studio ruft dann auf, um die [Informationen zu erhalten](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) , die für jedes lokale angezeigt werden sollen. In diesem Beispiel implementiert die-Klasse `CEnumPropertyInfo` die- `IEnumDebugPropertyInfo2` Schnittstelle.

Diese Implementierung von `IEnumDebugPropertyInfo2::Next` führt die folgenden Aufgaben aus:

1. Löscht das Array, in dem die Informationen gespeichert werden sollen.

2. Ruft für jede lokale- [Umgebung auf,](../../extensibility/debugger/reference/ienumdebugfields-next.md) wobei die zurückgegebenen [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) im Array gespeichert werden, das zurückgegeben werden soll. Das [ienumdebugfields](../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt wurde bereitgestellt, als diese `CEnumPropertyInfo` Klasse instanziiert wurde.

## <a name="managed-code"></a>Verwalteter Code
Dieses Beispiel zeigt eine Implementierung von `IEnumDebugPropertyInfo2::EnumChildren` für die lokalen Methoden einer Methode in verwaltetem Code.

```csharp
namespace EEMC
{
    public class CEnumMethodField : IEnumDebugFields
    {
        public HRESULT Next(
                uint                  count,
                DEBUG_PROPERTY_INFO[] properties,
            out uint                  fetched)
        {
            if (count > properties.Length)
                throw new COMException();

            // Zero out the array.
            for (int i= 0; i < count; i++)
            {
                properties[i].bstrFullName = "";
                properties[i].bstrName = "";
                properties[i].bstrType = "";
                properties[i].bstrValue = "";
                properties[i].dwAttrib = 0;
                properties[i].dwFields = 0;
                properties[i].pProperty = null;
            }
            fetched = 0;

            // COM interop.
            HRESULT hr;
            uint innerFetched;
            IDebugField[] field = new IDebugField[1];

            while (fetched < count)
            {
                field[0] = null;
                innerFetched = 0;

                // Get next field.
                if (fetched < fieldCount)
                    hr = fields.Next(1, field, ref innerFetched);
                // No more fields.
                else return COM.S_FALSE;

                if (hr != COM.S_OK || innerFetched != 1 || field[0] == null)
                    throw new COMException("CEnumPropertyInfo.Next");

                // Get property from field.
                CFieldProperty fieldProperty =
                        new CFieldProperty(provider, address, binder, field[0]);

                DEBUG_PROPERTY_INFO[] property =
                        new DEBUG_PROPERTY_INFO[1];
                fieldProperty.GetPropertyInfo((uint) infoFlags, radix, 0, null, 0, property);
                properties[fetched++] = property[0];
            }
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Nicht verwalteter Code
 Dieses Beispiel zeigt eine Implementierung von `IEnumDebugPropertyInfo2::EnumChildren` für die lokalen Variablen einer Methode in nicht verwaltetem Code.

```cpp
STDMETHODIMP CEnumPropertyInfo::Next(
    in  ULONG                count,
    out DEBUG_PROPERTY_INFO* pelements,
    out ULONG*               pfetched )
{
    if (pfetched)
        *pfetched = 0;
    if (!pelements)
        return E_INVALIDARG;
    else
        memset( pelements, 0, count * sizeof(DEBUG_PROPERTY_INFO));

    HRESULT hr  = S_OK;
    ULONG   idx = 0;
    while (idx < count)
    {
        ULONG        fetchedFields;
        IDebugField* pfield;

        //get the next field
        hr = m_fields->Next( 1, &pfield, &fetchedFields );
        if (FAILED(hr))
            return hr;
        if (fetchedFields != 1)
            return E_FAIL;
        idx++;

        //create a CFieldProperty to retrieve the DEBUG_PROPERTY_INFO
        CFieldProperty* pproperty =
            new CFieldProperty( m_provider, m_address, m_binder, pfield );
        pfield->Release();
        if (!pproperty)
            return E_OUTOFMEMORY;

        hr = pproperty->Init();
        if (FAILED(hr))
        {
            pproperty->Release();
            return hr;
        }

        hr = pproperty->GetPropertyInfo( m_infoFlags,
                                         m_radix,
                                         0,
                                         NULL,
                                         0,
                                         pelements + idx - 1);
        pproperty->Release();
        if (FAILED(hr))
            return hr;
    }

    if (pfetched)
        *pfetched = idx;
    return hr;
}
```

## <a name="see-also"></a>Siehe auch
- [Beispiel Implementierung von lokalen Variablen](../../extensibility/debugger/sample-implementation-of-locals.md)
- [Auflisten von lokalen Elementen](../../extensibility/debugger/enumerating-locals.md)
