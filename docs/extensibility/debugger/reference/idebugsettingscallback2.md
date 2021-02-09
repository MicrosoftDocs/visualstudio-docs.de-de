---
title: IDebugSettingsCallback2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 696f5eb00781c8f46ef099db1000b36a972a95dc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875808"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Ermöglicht Debug-engines das Remote Lesen von Metrikeinstellungen.

## <a name="syntax"></a>Syntax

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Diese Schnittstelle wird durch den Ereignis Rückruf des sitzungsdebug-Managers implementiert und von Debug-engines genutzt. Sie kann auch lokal anstelle von dbgmetric [d]. lib verwendet werden.

## <a name="methods"></a>Methoden
In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugSettingsCallback2` .

|Methode|Beschreibung|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Listet die verfügbaren Ausdrucksauswertungen unter Berücksichtigung der Sprach-und Hersteller Bezeichner auf.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Ruft ein lokales Objekt der Ausdrucks Auswertung ab, wenn die Metrik angegeben ist.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Ruft einen Wert ab, der der angegebenen Metrik der Ausdrucks Auswertung entspricht.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Ruft die metrikdatei der Ausdrucks Auswertung anhand des Namens oder der Metrik ab.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Ruft den eindeutigen Bezeichner für eine Ausdrucks auswertungsmetrik unter Berücksichtigung des Namens ab.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Ruft die Wert Zeichenfolge einer Ausdrucks Auswertungs Metrik unter Berücksichtigung des Namens ab.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Ruft den Wert einer Metrik mit dem angegebenen Namen ab.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Ruft den eindeutigen Bezeichner einer Metrik anhand des Namens ab.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Ruft die Wert Zeichenfolge der Metrik mit dem angegebenen Namen ab.|

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt eine Funktion, die ein **IDebugSettingsCallback2** -Objekt als Parameter annimmt.

```cpp
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)
{
    HRESULT hRes = E_FAIL;

    if ( ppCallback )
    {
        if ( EVAL(m_pdec) )
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```
