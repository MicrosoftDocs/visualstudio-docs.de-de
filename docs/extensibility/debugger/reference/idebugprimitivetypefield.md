---
description: Stellt einen primitiven typenumerationswert aus einer idebugfield-Schnittstelle dar.
title: Idebugprimitivetypeer-Feld | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ba0fd92098d8089f6d80573c1db53e0b7e003b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150301"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
Stellt einen primitiven typenumerationswert aus einer [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle dar.

## <a name="syntax"></a>Syntax

```
IDebugPrimitiveTypeField : IDebugField
```

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden für die [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle implementiert diese Schnittstelle die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Ruft den primitiven Typ ab, der diesem Feld zugeordnet ist.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
