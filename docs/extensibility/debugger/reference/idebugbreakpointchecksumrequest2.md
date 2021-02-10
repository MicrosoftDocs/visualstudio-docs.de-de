---
title: IDebugBreakpointChecksumRequest2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1004b8139617e370c6eef1c78f372d1e3a6db611
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951250"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Stellt eine Dokument Prüfsumme für eine Haltepunkt Anforderung dar.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Wird vom [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugpaket implementiert und von Debug-engines genutzt.

## <a name="methods"></a>Methoden
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugBreakpointChecksumRequest2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Ruft die Prüfsumme des Dokuments für eine Haltepunkt Anforderung ab, wenn der eindeutige Bezeichner des zu verwendenden Prüfsummen Algorithmus angegeben wird.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Bestimmt, ob die Prüfsumme für dieses Dokument aktiviert ist.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
