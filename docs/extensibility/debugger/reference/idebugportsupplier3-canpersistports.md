---
description: Diese Methode bestimmt, ob der Port Lieferant Ports (durch das Schreiben auf den Datenträger) zwischen den Aufrufen des Debuggers beibehalten kann.
title: 'IDebugPortSupplier3:: canpersistports | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 092f6e372d8f98e731ad90a7d261fe015d019656
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172008"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Diese Methode bestimmt, ob der Port Lieferant Ports (durch das Schreiben auf den Datenträger) zwischen den Aufrufen des Debuggers beibehalten kann.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Parameter
 Keine.

## <a name="return-value"></a>Rückgabewert
 `S_OK` , wenn Ports persistent sein können, oder, `S_FALSE` um anzugeben, dass die Ports nicht persistent sein können.

## <a name="remarks"></a>Bemerkungen
 Wenn der Port Lieferant Ports beibehalten kann, sollte er dies tun, wenn er zerstört wird, und ihn dann erneut laden, wenn er erneut instanziiert wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
