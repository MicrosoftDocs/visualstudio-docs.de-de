---
description: Stellt Gebiets Schema Unterstützung für einen Port Lieferanten bereit.
title: IDebugPortSupplierLocale2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c29bd3fb882be6529daa0d26ab4cde23c11d0bc0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167060"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
Stellt Gebiets Schema Unterstützung für einen Port Lieferanten bereit.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplierLocale2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle, um das Gebiets Schema festzulegen.

## <a name="methods"></a>Methoden
 In der folgenden Tabelle sind die Methoden von **IDebugPortSupplierLocale2** aufgeführt.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Legt das Gebiets Schema für den Port Lieferanten fest.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: portpriv. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
