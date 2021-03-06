---
description: Diese Schnittstelle listet DEBUG_PROPERTY_INFO Strukturen auf.
title: IEnumDebugPropertyInfo2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fea2dc5cf958f87463af9dfca9f29bec5d01a82b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224186"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Diese Schnittstelle listet [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen auf.

## <a name="syntax"></a>Syntax

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um Informationen für eine bestimmte Eigenschaft darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [enumchildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) auf, um diese Schnittstelle abzurufen, die die untergeordneten Elemente einer bestimmten Eigenschaft darstellt. Rufen Sie [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) auf, um diese Schnittstelle zu erhalten, die die Eigenschaften eines bestimmten Stapel Rahmens darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IEnumDebugPropertyInfo2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Ruft eine angegebene Anzahl von [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen in einer Enumerationsfolge ab.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Überspringt eine angegebene Anzahl von [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen in einer enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klonen](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Ruft die Anzahl der [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Im Allgemeinen ist eine Eigenschaft eine Hierarchie von Informationen, die einen Namen, einen Wert, eine Adresse und einen Typ enthalten kann, sowie alle anderen Informationen, die für das zugeordnete Eigenschafts Objekt oder den Stapel Rahmen geeignet sind. Weitere Informationen finden Sie unter [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) .

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
