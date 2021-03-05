---
description: Diese Schnittstelle ermöglicht es einer Ausdrucks Auswertung (EE), den Wert einer Eigenschaft in einem beliebigen Format anzuzeigen.
title: Idebugcustomviewer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8d262869d24c50c543159952506a40be753b4be4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150691"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Diese Schnittstelle ermöglicht es einer Ausdrucks Auswertung (EE), den Wert einer Eigenschaft in einem beliebigen Format anzuzeigen.

## <a name="syntax"></a>Syntax

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
Ein EE implementiert diese Schnittstelle, um den Wert einer Eigenschaft in einem benutzerdefinierten Format anzuzeigen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Ein Aufrufder com- `CoCreateInstance` Funktion instanziiert diese Schnittstelle. Die `CLSID` an übergebenen `CoCreateInstance` wird aus der Registrierung abgerufen. Durch einen get-Befehl von [getcustomviewerlist](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) wird der Speicherort in der Registrierung abgerufen. Ausführliche Informationen und das Beispiel finden Sie in den hinweisen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
Diese Schnittstelle implementiert die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Gibt an, was erforderlich ist, um einen bestimmten Wert anzuzeigen.|

## <a name="remarks"></a>Bemerkungen
Diese Schnittstelle wird verwendet, wenn der Wert einer Eigenschaft nicht auf normale Weise angezeigt werden kann, z. –. mit einer Datentabelle oder einem anderen komplexen Eigenschaftentyp. Ein benutzerdefinierter Viewer, der durch die-Schnittstelle dargestellt wird, `IDebugCustomViewer` unterscheidet sich von einer typschnellansicht, bei der es sich um ein externes Programm zum Anzeigen von Daten eines bestimmten Typs handelt, unabhängig von der EE. Der EE implementiert einen benutzerdefinierten Viewer, der für diesen EE spezifisch ist. Ein Benutzer wählt den Typ der Schnellansicht aus, der verwendet werden soll, oder es handelt sich um eine typschnell Ansicht oder einen benutzerdefinierten Viewer. Ausführliche Informationen zu diesem Prozess finden Sie unter [visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

Ein benutzerdefinierter Viewer wird auf die gleiche Weise wie ein EE registriert und erfordert daher eine sprach-GUID und eine Anbieter-GUID. Die genaue Metrik (oder der Registrierungs Eintrags Name) ist nur dem EE bekannt. Diese Metrik wird in der [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Struktur zurückgegeben, die wiederum durch einen get-Befehl von " [getcustomviewerlist](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)" zurückgegeben wird. Der in der Metrik gespeicherte Wert ist der `CLSID` , der an die com- `CoCreateInstance` Funktion (siehe Beispiel) übermittelt wird.

Die [SDK-Hilfsprogramme für die Debugfunktion](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetEEMetric` können zum Registrieren eines benutzerdefinierten Viewers verwendet werden. Informationen `Debugging SDK Helpers` zu den spezifischen Registrierungs Schlüsseln, die von einem benutzerdefinierten Viewer benötigt werden, finden Sie im Abschnitt "Ausdrucks Auswertung" unter. Beachten Sie, dass ein benutzerdefinierter Viewer nur eine Metrik benötigt (die vom Implementierer definiert wird), während eine Ausdrucks Auswertung mehrere vordefinierte Metriken erfordert.

Normalerweise stellt ein benutzerdefinierter Viewer eine schreibgeschützte Ansicht der Daten bereit, da die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle, die für [displayvalue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) bereitgestellt wird, keine Methoden zum Ändern des Eigenschafts Werts enthält, außer als Zeichenfolge. Um das ändern beliebiger Datenblöcke zu unterstützen, implementiert der EE eine benutzerdefinierte Schnittstelle für das gleiche Objekt, das die- `IDebugProperty3` Schnittstelle implementiert. Diese benutzerdefinierte Schnittstelle stellt dann die Methoden bereit, die erforderlich sind, um einen beliebigen Datenblock zu ändern.

## <a name="requirements"></a>Requirements (Anforderungen)
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt, wie Sie den ersten benutzerdefinierten Viewer aus einer Eigenschaft erhalten, wenn diese Eigenschaft über benutzerdefinierte Viewer verfügt.

```cpp
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)
{
    // This string is typically defined globally.  For this example, it
    // is defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugCustomViewer *pViewer = NULL;
    if (pProperty != NULL) {
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);
        if (pProperty3 != NULL) {
            HRESULT hr;
            ULONG viewerCount = 0;
            hr = pProperty3->GetCustomViewerCount(&viewerCount);
            if (viewerCount > 0) {
                ULONG viewersFetched = 0;
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };
                hr = pProperty3->GetCustomViewerList(0,
                                                     1,
                                                     &viewerInfo,
                                                     &viewersFetched);
                if (viewersFetched == 1) {
                    CLSID clsidViewer = { 0 };
                    CComPtr<IDebugCustomViewer> spCustomViewer;
                    // Get the viewer's CLSID from the registry.
                    ::GetEEMetric(viewerInfo.guidLang,
                                  viewerInfo.guidVendor,
                                  viewerInfo.bstrMetric,
                                  &clsidViewer,
                                  strRegistrationRoot);
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {
                        // Instantiate the custom viewer.
                        spCustomViewer.CoCreateInstance(clsidViewer);
                        if (spCustomViewer != NULL) {
                            pViewer = spCustomViewer.Detach();
                        }
                    }
                }
            }
        }
    }
    return(pViewer);
}
```

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
