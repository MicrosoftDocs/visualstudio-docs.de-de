---
description: Diese Schnittstelle stellt einen Verweis auf eine Stapel Rahmen Eigenschaft oder eine andere Eigenschaft dar.
title: IDebugReference2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 04d9795388b2a079d0eb7ac1d787bf92de6cdff4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165851"
---
# <a name="idebugreference2"></a>IDebugReference2
Diese Schnittstelle stellt einen Verweis auf eine Stapel Rahmen Eigenschaft oder eine andere Eigenschaft dar.

> [!NOTE]
> `IDebugReference2` ist für die zukünftige Verwendung reserviert, und alle zugehörigen Methoden sollten zurückgeben `E_NOTIMPL` .

## <a name="syntax"></a>Syntax

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die de implementiert diese Schnittstelle, um einen Verweis auf eine bestimmte Art von Wert darzustellen. Der Wert kann z. b. ein numerischer Wert als Ergebnis einer Ausdrucks Auswertung, ein Speicher Kontext, der zum Anzeigen von Arbeitsspeicher verwendet wird, oder eine Liste von Registern und deren Werten sein.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [getreferenzierung](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) zum Abrufen dieser Schnittstelle auf. " [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) " und " [getderivedmustreferenzierung](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) " geben ebenfalls diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugReference2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Ruft die [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) -Struktur ab, die diesen Verweis beschreibt.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Legt den Wert dieses Verweises aus einer Zeichenfolge fest.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Legt den Wert dieses Verweises aus einem anderen Verweis fest.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Listet die untergeordneten Elemente dieses Verweises auf.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Ruft das übergeordnete Element dieses Verweises ab.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Ruft den am weitesten abgeleiteten Verweis dieses Verweises ab.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Ruft die Arbeitsspeicher Bytes ab, auf die sich dieser Verweis bezieht.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Ruft einen Speicher Kontext für diesen Verweis ab.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Ruft die Größe dieses Verweises in Bytes ab.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Legt diesen Verweistyp fest.|
|[Vergleichen](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Vergleicht diesen Verweis mit einem anderen.|

## <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Diese Verwendung von "Property" sollte nicht mit der Bedeutung einer Element Variablen einer Klasse verwechselt werden, obwohl eine `IDebugReference2` solche Entität darstellen kann.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) stellt eine Eigenschaft dar, während `IDebugReference2` einen Verweis auf eine Eigenschaft darstellt, in der Regel ein Verweis auf ein Objekt in dem Programm, das deentschlgt wird.

 Der Hauptunterschied zwischen einer Eigenschaft und einem Verweis besteht darin, dass eine Eigenschaft auf eine benannte Instanz eines Objekts verweist, während ein Verweis auf eine unbenannte Instanz verweist. Eine Eigenschaft kann z. b. auf ein Objekt im Heap des Programms durch verweisen `"a.b"` . Eine andere Eigenschaft verweist möglicherweise auf dasselbe Objekt wie `"c.d"` . Die Möglichkeit, auf diese Eigenschaft zu verweisen, erfordert, dass `"a.b"` oder im Gültigkeits `"c.d"` Bereich liegen. Ein Verweis auf dieses Objekt ist namenenlos. auf das-Objekt kann verwiesen werden, solange der Arbeitsspeicher für dieses Objekt gültig ist.

 Eine `IDebugProperty2` Schnittstelle kann als Wert mit einem Namen, einem Typ und einer Adresse betrachtet werden. Eine `IDebugReference2` kann andererseits als Typ und als Adresse betrachtet werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
