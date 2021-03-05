---
description: Stellt einen Parameter für einen generischen Typ mit verwaltetem Code dar.
title: Idebuggenericparamfield | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c4ab1cd79826e2f9f07a4f325d701be4e9eb9c9d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172570"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Stellt einen Parameter für einen generischen Typ mit verwaltetem Code dar.

## <a name="syntax"></a>Syntax

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Wird für die Unterstützung von Generika verwendet.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden für die [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Gibt die Anzahl der Einschränkungen zurück, die diesem generischen Parameter zugeordnet sind.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Ruft die Einschränkungen ab, die diesem generischen Parameter zugeordnet sind.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Ruft die Flags für diesen generischen Parameter ab.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Ruft den Index dieses generischen Parameters ab.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Ruft den Namen dieses generischen Parameters ab.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Ruft den Typ oder den Methoden Besitzer dieses generischen Parameters ab.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
