---
title: IDebugCodeContext2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f03bef276d4f4aada1a173c45defd100e4becbf4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928690"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Diese Schnittstelle stellt die Anfangsposition einer Code Anweisung dar. Für die meisten Lauf Zeit Architekturen kann ein Code Kontext als Adresse im ausführungsstream eines Programms betrachtet werden.

## <a name="syntax"></a>Syntax

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine implementiert diese Schnittstelle, um die Position einer Code Anweisung mit einer Dokument Position in Beziehung zu setzen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Methoden für viele Schnittstellen geben diese Schnittstelle zurück (in der Regel [getcodecontext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)). Sie wird auch intensiv mit der [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) -Schnittstelle sowie in Informationen zur breakpointauflösung verwendet.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden in der [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) -Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:

|Methode|Beschreibung|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Ruft den Dokument Kontext ab, der dem aktiven Code Kontext entspricht.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Ruft die Sprachinformationen für diesen Code Kontext ab.|

## <a name="remarks"></a>Bemerkungen
 Der Hauptunterschied zwischen einer `IDebugCodeContext2` Schnittstelle und einer [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) -Schnittstelle besteht darin, dass ein `IDebugCodeContext2` immer Anweisungs orientiert ist. Dies bedeutet, dass eine `IDebugCodeContext2` immer auf den Anfang einer Anweisung zeigt, während ein `IDebugMemoryContext2` auf ein beliebiges Byte des Speichers in der Lauf Zeit Architektur verweisen kann. `IDebugCodeContext2` wird nicht durch die grundlegende Speichergröße (in der Regel Byte), sondern durch Anweisungen inkrementiert.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Nächste](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
