---
description: Diese Schnittstelle ermöglicht es dem sitzungsdebug-Manager (SDM), an ein Programm anzufügen und den Programmknoten zu erhalten, der einem Programm zugeordnet ist.
title: IDebugProgramEx2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f3efe419eaf037602ce1148c898c6c30dd86d23b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149573"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Diese Schnittstelle ermöglicht es dem sitzungsdebug-Manager (SDM), an ein Programm anzufügen und den Programmknoten zu erhalten, der einem Programm zugeordnet ist.

## <a name="syntax"></a>Syntax

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle auf demselben Objekt wie die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle, damit die SDM an ein Programm angefügt werden kann, während gleichzeitig der Port Lieferant alle an das Programm angefügten Sitzungen verfolgen kann. Der benutzerdefinierte portlieferant kann diese Schnittstelle implementieren, wenn er Sie auswählt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Der SDM ruft [QueryInterface](/cpp/atl/queryinterface) für eine `IDebugProgram2` Schnittstelle auf, um diese Schnittstelle zu erhalten, um Sitzungen zu verfolgen, die an Programme angefügt sind.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProgramEx2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Anfügen](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Fügt ein Programm an eine Sitzung an.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Ruft den einem Programm zugeordneten Programmknoten ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle ist zwischen dem SDM und dem Programm privat.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: portpriv. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
