---
description: Diese Schnittstelle ist eine von IDebugProcess2 Implementierern implementierte Erweiterungsschnittstelle.
title: Idebugprocessqueryproperties | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8205b96723a1b48da46e6e19162c50139c9fe71d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166215"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Diese Schnittstelle ist eine von [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) Implementierern implementierte Erweiterungsschnittstelle. Sie ermöglicht es dem Implementierer, Informationen zur debugprozessumgebung zu erhalten.

## <a name="syntax"></a>Syntax

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Implementieren Sie diese Schnittstelle, um Informationen zur Ausführungsumgebung eines Debugprozesses zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProcessQueryProperties` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Fragt nach einem Eigenschafts Wert ab.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Fragt nach Eigenschafts Werten ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle ist selten implementiert.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: portpriv. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
