---
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15f0ddf70849377d37ec74839550de6057b3450c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731314"
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

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
