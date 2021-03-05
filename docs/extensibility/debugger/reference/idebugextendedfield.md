---
description: Erweitert die Typen von Feldern, die zur Unterstützung verwalteter Code Generics verfügbar sind.
title: Idebugextendedfield | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5da66ddab0f485587ac5779187384a749459419e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152103"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
Erweitert die Typen von Feldern, die zur Unterstützung verwalteter Code Generics verfügbar sind.

## <a name="syntax"></a>Syntax

```
IDebugExtendedField : IDebugField
```

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden für die [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Ruft die angegebene erweiterte Feldart ab.|
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Bestimmt, ob das Feld einen geschlossenen Typ darstellt.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
