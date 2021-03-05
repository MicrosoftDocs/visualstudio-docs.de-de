---
description: Idebugprocesssecurity wird von einem Port Lieferanten implementiert, um den Benutzer zu warnen, dass das Anfügen an den Prozess unsicher ist.
title: Idebugprocesssecurity | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b5e2ca72cc3d9c1d204c6fb1f90ccc9b03060cff
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166098"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` wird von einem Port Lieferanten implementiert, um den Benutzer zu warnen, dass das Anfügen an den Prozess unsicher ist.

## <a name="syntax"></a>Syntax

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProcessSecurity` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Ruft den Benutzernamen vom Port Lieferanten ab.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Warnt einen Benutzer, dass das Anhängen an den Debugprozess unsicher ist.|

## <a name="remarks"></a>Bemerkungen
 Implementieren Sie diese Schnittstelle, um eine Warnung anzuzeigen und dem Benutzer zu gestatten, abzubrechen, wenn der Prozess, an den Sie anhängen, als unsicher eingestuft werden kann.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Ports](../../../extensibility/debugger/ports.md)
- [Portanbieter](../../../extensibility/debugger/port-suppliers.md)
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
