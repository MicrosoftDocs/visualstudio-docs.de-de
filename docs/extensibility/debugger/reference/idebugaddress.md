---
description: Diese Schnittstelle stellt die Adresse eines Elements dar.
title: Idebugaddress | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f49107e4d06fa828d059ebd9916ca254882ff0a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154963"
---
# <a name="idebugaddress"></a>IDebugAddress
Diese Schnittstelle stellt die Adresse eines Elements dar. Sie wird vom Symbol Handler zurückgegeben.

## <a name="syntax"></a>Syntax

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Symbol Anbieter implementiert diese Schnittstelle, um eine Adresse eines Objekts darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Viele Methoden für viele Schnittstellen geben diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Ruft eine [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) -Struktur ab, die ein-Objekt und seinen Speicherort beschreibt.|

## <a name="remarks"></a>Bemerkungen
 Der Symbol Anbieter gibt diese Schnittstelle zurück, um ein Objekt und seinen Speicherort innerhalb eines bestimmten Bereichs (z. b. Funktion, Methode oder Klasse) darzustellen. Diese Schnittstelle wird von zurückgegeben und an verschiedene Methoden des Symbol Anbieters und der Ausdrucks Auswertung übermittelt. Normalerweise ist der Symbol Anbieter die einzige Entität, die den Inhalt dieser Schnittstelle interpretieren muss.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
