---
title: IDebugProperty2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c5cec0d93919058eae725a9e49198f1704d8bfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962196"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Diese Schnittstelle stellt eine Stapel Rahmen Eigenschaft, eine Programmdokument Eigenschaft oder eine andere Eigenschaft dar. Die-Eigenschaft ist normalerweise das Ergebnis einer Ausdrucks Auswertung.

> [!NOTE]
> Diese Verwendung von "Property" sollte nicht mit der Bedeutung einer Element Variablen einer Klasse verwechselt werden, obwohl eine `IDebugProperty2` solche Entität darstellen kann.

## <a name="syntax"></a>Syntax

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die de implementiert diese Schnittstelle, um eine bestimmte Art von Wert darzustellen. Der Wert kann z. b. ein numerischer Wert als Ergebnis einer Ausdrucks Auswertung, ein Speicher Kontext, der zum Anzeigen von Arbeitsspeicher verwendet wird, oder eine Liste von Registern und deren Werten sein.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [evaluatesync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [evaluateasync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) auf, um diese Schnittstelle zu erhalten, die das Ergebnis einer Auswertung darstellt. `IDebugExpression2::EvaluateAsync` gibt diese Schnittstelle zurück, indem eine [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) -Schnittstelle an die SDM gesendet wird, die wiederum [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) zum Abrufen der Eigenschaft aufruft.

- [Getdebugproperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) gibt diese Schnittstelle zurück, um das zugehörige Skript Dokument bereitzustellen.

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) gibt diese Schnittstelle zurück, um den Rückgabewert einer Funktion darzustellen.

- [Getdebugproperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) gibt diese Schnittstelle zurück, um verschiedene Eigenschaften des Programms (z. b. einen Namen oder einen Speicher Kontext) darzustellen.

- [Getdebugproperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) gibt diese Schnittstelle zurück, um verschiedene Eigenschaften des Stapel Rahmens (z. b. lokale Variablen) darzustellen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProperty2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Füllt eine [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Struktur, die eine Eigenschaft beschreibt.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Legt den Wert einer Eigenschaft aus einer Zeichenfolge fest.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Legt den Wert der-Eigenschaft aus dem Wert eines angegebenen Verweises fest.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Listet die untergeordneten Elemente einer Eigenschaft auf.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Gibt das übergeordnete Element einer Eigenschaft zurück.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Gibt die Eigenschaft zurück, die die am häufigsten abgeleitete Eigenschaft einer Eigenschaft beschreibt.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Gibt die Arbeitsspeicher Bytes zurück, die den Wert einer Eigenschaft bilden.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Gibt den Arbeitsspeicher Kontext für einen Eigenschafts Wert zurück.|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Gibt die Größe des Eigenschafts Werts in Byte zurück.|
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Gibt einen Verweis auf den Wert dieser Eigenschaft zurück.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Gibt die erweiterten Informationen einer Eigenschaft zurück.|

## <a name="remarks"></a>Bemerkungen
 Eine Eigenschaft, die durch eine `IDebugProperty2` Schnittstelle dargestellt wird, kann als Wert mit einem Namen, einem Typ und einer Adresse betrachtet werden. In allgemeineren Begriffen kann ein alle Elemente `IDebugProperty2` darstellen, die über eine hierarchische Struktur mit übergeordneten und untergeordneten Knoten verfügen.

 Eine Eigenschaft ist normalerweise Transitory und wird nur so lange wie der aktuelle Stapel Rahmen (z. b.). Auf der anderen Seite wird ein Verweis, der durch eine [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) -Schnittstelle dargestellt wird, so lange beibehalten, wie der Wert im Arbeitsspeicher verbleibt.

 Die IDE kann die `IDebugProperty2` -Schnittstelle verwenden, um Benutzern das Durchsuchen und Ändern von Eigenschaften zur Laufzeit zu ermöglichen.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
