---
description: Trennt den Debugger von diesem Prozess, indem alle Programme im Prozess getrennt werden.
title: IDebugProcess2::D Etach | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5775ee9ffc3fa3c4151df999b64ba1160da6f7c3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166280"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Trennt den Debugger von diesem Prozess, indem alle Programme im Prozess getrennt werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Alle Programme und der Prozess werden weiterhin ausgeführt, sind jedoch nicht mehr Teil der Debugsitzung. Nachdem der Trennvorgang beendet wurde, werden keine weiteren Debugereignisse für diesen Prozess (und seine Programme) gesendet.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
