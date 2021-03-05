---
description: Ermöglicht es einer Debug-Engine, das Standardverhalten der Visual Studio-Benutzeroberfläche zu überschreiben, wenn Sie eine Debugsitzung beenden.
title: IDebugProgramDestroyEventFlags2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 02b2d934c2a556d3556d494368145e52a8c97394
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168191"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Ermöglicht es einer Debug-Engine, das Standardverhalten der Benutzeroberfläche zu überschreiben, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Wenn Sie eine Debugsitzung beenden.

## <a name="syntax"></a>Syntax

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Debug-engines implementiert. Dies ist nützlich für Hosts, die möglicherweise mehrere Programme während der Lebensdauer eines Prozesses erstellen und zerstören.

## <a name="methods"></a>Methoden
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProgramDestroyEventFlags2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Ruft die Flags für die Programm Zerstörung ab.|

## <a name="remarks"></a>Bemerkungen
 Das Standardverhalten der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche besteht darin, zurück in den Entwurfs Modus zu wechseln, nachdem alle Programme ein Programm zerstörungsereignis gesendet haben. Diese Schnittstelle ermöglicht es einer Debug-Engine, dieses Verhalten zu ändern.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
