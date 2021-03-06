---
description: Diese Methode gibt eine Liste von typvisualisierungen zurück, die dieser Dienst kennt.
title: 'Ieevisualizerservice:: getcustomviewerlist | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0bd9c633c6b65bbd597619f9fd30487a734d9004
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222899"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Diese Methode gibt eine Liste von typvisualisierungen zurück, die dieser Dienst kennt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCustomViewerList(
   ULONG                celtSkip,
   ULONG                celtRequested,
   DEBUG_CUSTOM_VIEWER* rgViewers,
   ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
   uint                  celtSkip,
   uint                  celtRequested,
   DEBUG_CUSTOM_VIEWER[] rgViewers,
   out uint              pceltFetched
);
```

## <a name="parameters"></a>Parameter
`celtSkip`\
in Anzahl der Visualisierungen, die übersprungen werden sollen.

`celRequested`\
in Anzahl der abzurufenden Visualisierungen (gibt auch die Größe des `rgViewers` Arrays an).

`rgViewers`\
[in, out] Array von [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Strukturen, die ausgefüllt werden sollen.

`pceltFetched`\
vorgenommen Anzahl von Visualisierungen, die tatsächlich abgerufen wurden.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
- [Getcustomviewerlist](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) übergibt die Anforderung als Teil der Unterstützung für typvisualisierungen an diese Methode. Wenn die Ausdrucks Auswertung auch benutzerdefinierte Viewer für denselben Typ bereitstellt, kann Sie entsprechend ausgefüllte [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Strukturen für diese benutzerdefinierten Viewer an die Liste anfügen. Stellen Sie sicher, dass [getcustomviewercount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) diese zusätzlichen Viewer widerspiegelt.

 Ausführliche Informationen zu den Unterschieden zwischen Visualisierungen und Viewern finden Sie unter [typschnell Ansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) .

## <a name="see-also"></a>Weitere Informationen
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
