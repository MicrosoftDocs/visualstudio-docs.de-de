---
description: Aktiviert eine Debug-Engine, die DCOM verwendet, um die Visual Studio-Benutzeroberfläche zu bitten, sicherzustellen, dass die Firewall das Remote Debugging nicht blockiert.
title: IDebugFirewallConfigurationCallback2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf8659a1bc4af55a9809a3c85548b971a7193b26
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166527"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Aktiviert eine Debug-Engine, die DCOM verwendet, um die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche zu Fragen, um sicherzustellen, dass die Firewall das Remote Debugging nicht blockiert.

## <a name="syntax"></a>Syntax

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Wird vom Port-Objekt des sitzungsdebug-Managers implementiert.

## <a name="methods"></a>Methoden
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugFirewallConfigurationCallback2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Fordert an, dass die Firewall das Remote Debugging nicht blockiert.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
