---
description: Ermöglicht das Abfragen von Informationen über den Bereitstellungs Zielcomputer.
title: IDebugWindowsComputerPort2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a9c7e940c2284b5b39097226f9a5b0c3b34a0d18
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222951"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Ermöglicht das Abfragen von Informationen über den Bereitstellungs Zielcomputer.

## <a name="syntax"></a>Syntax

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von Port Objekten des sitzungsdebug-Managers implementiert.

## <a name="methods"></a>Methoden
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugWindowsComputerPort2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Getcomputerinfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Ruft Informationen über den Computer ab, auf dem der Debugger ausgeführt wird.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
