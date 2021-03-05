---
description: Diese Schnittstelle stellt einen Typ einer Variablen dar.
title: Idebugdynamicfield | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dcf148294a7c18c2b717bb4de63dac7e656e25d6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167229"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Diese Schnittstelle stellt einen Typ einer Variablen dar.

## <a name="syntax"></a>Syntax

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Symbol Anbietern als Basisklasse für jeden Typ implementiert, der zur Laufzeit bestimmt werden kann. Dies gilt nur für verwalteten Code.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle stellt eine Basisklasse dar, von der speziellere Schnittstellen abgeleitet werden können.

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge
 Diese Schnittstelle stellt keine Methoden bereit, die nicht von geerbt wurden `IDebugField` .

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
