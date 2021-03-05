---
description: Erweitert den idebugtypefieldbuilder, damit Array Typen erstellt werden können.
title: IDebugTypeFieldBuilder2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e73642024cb379e804559ba8dd55eb44722cf580
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223003"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Erweitert den **idebugtypefieldbuilder** , damit Array Typen erstellt werden können.

## <a name="syntax"></a>Syntax

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle kann vom Symbol Anbieter abgerufen werden.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden in der [idebugtypefieldbuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) -Schnittstelle implementiert diese Schnittstelle die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Erstellt ein Array des angegebenen Typs und der angegebenen Größe.|

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
