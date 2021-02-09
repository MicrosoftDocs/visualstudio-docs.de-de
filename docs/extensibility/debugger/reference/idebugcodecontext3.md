---
title: IDebugCodeContext3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 14bcfb7498ad22156ae18998ebe5958aad1b9026
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928756"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Erweitert die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Schnittstelle, um das Abrufen von Modul-und Prozessschnittstellen zu ermöglichen.

## <a name="syntax"></a>Syntax

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Wird von Debug-engines implementiert und vom [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugpaket verwendet.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden der- `IDebugCodeContext2` Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:

|Methode|Beschreibung|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Ruft einen Verweis auf die-Schnittstelle des Debug-Moduls ab.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Ruft einen Verweis auf die-Schnittstelle des Debugprozesses ab.|

## <a name="remarks"></a>Bemerkungen
 Dies ist eine optionale Schnittstelle, die in der Regel nicht implementiert werden muss.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
