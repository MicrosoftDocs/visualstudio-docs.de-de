---
description: Stellt eine Dokument Prüfsumme für eine Haltepunkt Anforderung dar.
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
ms.openlocfilehash: 6bb0bdd70d2d4d1d56e341bc8f21ef1127433219
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173709"
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

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
