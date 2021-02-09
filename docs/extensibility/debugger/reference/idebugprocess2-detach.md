---
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
ms.openlocfilehash: 6418a7f628eef4e00ea0555c07122555eb6d600c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874086"
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
