---
title: Auswerten von lokalen Variablen | Microsoft-Dokumentation
description: Erfahren Sie, wie Visual Studio auf den Speicherort im Arbeitsspeicher zugreift, der einen lokalen Wert enthält, der vom aktuellen Status des Programms abhängig ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], evaluating locals
- expression evaluation, evaluating locals
ms.assetid: 7d1ed528-4e7a-4d8f-87b4-162440644a75
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 291c77568f17cfb0aed9d0d5b55e5ca193a6a702
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840638"
---
# <a name="evaluate-locals"></a>Lokale Auswertung
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) wird aufgerufen, um den Wert eines lokalen zu erhalten, sowie den Namen und den Typ des lokalen. Da der Wert eines lokalen von dem aktuellen Status des Programms abhängig ist, muss der Wert des lokalen Werts aus dem Arbeitsspeicher abgerufen werden. Das [idebugbinder](../../extensibility/debugger/reference/idebugbinder.md) -Objekt wird verwendet, um das [idebugfield](../../extensibility/debugger/reference/idebugfield.md) -Objekt, das die lokale darstellt, an die entsprechende Position im Speicher zu binden, die den Wert enthält. Diese Position im Arbeitsspeicher wird durch ein [idebugobject](../../extensibility/debugger/reference/idebugobject.md) -Objekt dargestellt.

Diese Funktion zum Abrufen des Werts eines lokalen wird in einer Hilfsfunktion gekapselt, die folgende Aufgaben ausführt:

1. Bindet das-Objekt an den Arbeits `IDebugField` Speicher, um ein- `IDebugObject` Objekt abzurufen.

2. Ruft den Wert aus dem Arbeitsspeicher ab. Dieser Wert wird als eine Reihe von Bytes dargestellt.

3. Formatiert den Wert basierend auf dem Typ des lokalen.

4. Gibt ein generisches-Objekt zurück, das den lokalen Wert enthält. In c# ist dies ein `object` , und in C++ ist dies ein `VARIANT` .

## <a name="managed-code"></a>Verwalteter Code
 Dies ist eine Implementierung einer Funktion, die den Wert einer lokalen in verwaltetem Code abruft.

```csharp
namespace EEMC
{
    internal class Field
    {
        internal static object GetValue(
            IDebugBinder binder,
            IDebugField field,
            Type t,
            uint size)
        {
            if (t == null || size == 0)  return null;

            IDebugObject debugObject = null;
            binder.Bind(null, field, out debugObject);

            byte[] buffer = new byte[size];
            for (int i = 0; i < size; i++)  buffer[i] = 0;

            debugObject.GetValue(buffer, size);

            if (t == typeof(sbyte)) return (sbyte) buffer[0];
            if (t == typeof(short)) return BitConverter.ToInt16(buffer, 0);
            if (t == typeof(int))   return BitConverter.ToInt32(buffer, 0);
            if (t == typeof(long))  return BitConverter.ToInt64(buffer, 0);
            if (t == typeof(byte))  return buffer[0];
            if (t == typeof(char))  return BitConverter.ToChar(buffer, 0);
            if (t == typeof(uint))  return BitConverter.ToUInt32(buffer, 0);
            if (t == typeof(ulong)) return BitConverter.ToUInt64(buffer, 0);
            if (t == typeof(float)) return BitConverter.ToSingle(buffer, 0);
            if (t == typeof(double))  return BitConverter.ToDouble(buffer, 0);
            if (t == typeof(bool))  return BitConverter.ToBoolean(buffer, 0);
            if (t == typeof(string))  return BitConverter.ToString(buffer, 0);
            return null;
        }
    }
}
```

## <a name="unmanaged-code"></a>Nicht verwalteter Code
 Dies ist eine Implementierung einer Funktion, die den Wert eines lokalen in nicht verwaltetem Code abruft. `FieldGetType` wird in " [lokale Werte](../../extensibility/debugger/getting-local-values.md)" angezeigt.

```cpp
HRESULT FieldGetPrimitiveValue(
    in  IDebugBinder* pbinder,
    in  IDebugField*  pfield,
    out VARIANT*      pvarValue
    )
{
    if (pvarValue == NULL)
        return E_INVALIDARG;
    else
        *pvarValue = 0;

    if (pfield == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    UINT          valueSize = 0;
    BYTE*         pvalueBits = NULL;
    IDebugObject* pobject    = NULL;

    //get the value as bits
    hr = pbinder->Bind( NULL, pfield, &pobject );
    if (FAILED(hr))
        return hr;

    hr = pobject->GetSize( &valueSize );
    if (FAILED(hr))
    {
        pobject->Release();
        return hr;
    }

    pvalueBits = reinterpret_cast<BYTE *>(malloc(valueSize * sizeof(BYTE)));
    if (!pvalueBits)
    {
        pobject->Release();
        return E_OUTOFMEMORY;
    }

    hr = pobject->GetValue( pvalueBits, valueSize );
    pobject->Release();
    if (FAILED(hr))
    {
        free(pvalueBits);
        return hr;
    }

    //get the type
    VARIANT     valueType;

    hr = FieldGetType( pfield, &valueType );
    if (FAILED(hr))
    {
        free(pvalueBits);
        return hr;
    }

    //copy a primitive value
    switch (valueType.vt)
    {
    case VT_BSTR:
        {
            pvarValue->vt = VT_BSTR;
            if (valueSize == 0)
                pvarValue->bstrVal = SysAllocString( OLE("") );
            else
                pvarValue->bstrVal =
                    SysAllocStringByteLen( reinterpret_cast<char*>(pvalueBits),
                                           valueSize );
        }

    case VT_BOOL:
    case VT_I1:
    case VT_I2:
    case VT_I4:
    case VT_I8:
    case VT_UI1:
    case VT_UI2:
    case VT_UI4:
    case VT_UI8:
    case VT_R4:
    case VT_R8:
        pvarValue->vt = valueType.vt;

        if (valueSize > 8)
            valueSize = 8;
        memcpy( &(pvarValue->iVal), pvalueBits, valueSize );
        break;

    case VT_VOID:
    case VT_EMPTY:
        pvarValue->vt = valueType.vt;
        break;

    default:
        //not a primitive type
        VariantClear(&valueType);
        free(pvalueBits);
        return E_FAIL;
    }

    free(pvalueBits);
    VariantClear(&valueType);
    return S_OK;
}
```

## <a name="see-also"></a>Weitere Informationen
- [Beispiel Implementierung von lokalen Variablen](../../extensibility/debugger/sample-implementation-of-locals.md)
- [Lokale Werte erhalten](../../extensibility/debugger/getting-local-values.md)
- [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md)
