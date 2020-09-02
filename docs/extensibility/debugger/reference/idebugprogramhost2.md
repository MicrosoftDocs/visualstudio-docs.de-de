---
title: IDebugProgramHost2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64db456e0c438f8665f122c3cd1b079c2ad1cea1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722209"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
Diese Schnittstelle stellt Host-(Prozess-) Informationen zu einem Programm bereit.

## <a name="syntax"></a>Syntax

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine implementiert diese Schnittstelle für das gleiche Objekt wie die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle, um Informationen über den Host Prozess bereitzustellen. Dies ist eine optionale Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) für eine `IDebugProgram2` Schnittstelle auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProgramHost2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Ruft den Titel, den anzeigen Amen oder den Dateinamen des Hostingprozesses dieses Programms ab.|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Ruft den Prozess Bezeichner des Hostingprozesses dieses Programms ab.|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Ruft den Namen des Computers ab, auf dem der Hostingprozess dieses Programms ausgeführt wird.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
