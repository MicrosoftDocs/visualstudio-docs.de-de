---
title: 'IDebugQueryEngine2:: getengineingeterface | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab1d9be5e4405cea3bb75d7837d4ff3ad9a91e9c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909794"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Ruft eine benutzerdefinierte Debug-Engine-Schnittstelle (de) ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEngineInterface( 
   IUnknown** ppUnk
);
```

```csharp
int GetEngineInterface( 
   out object ppUnk
);
```

## <a name="parameters"></a>Parameter
`ppUnk`\
vorgenommen Gibt ein `IUnknown` -Objekt zurück, das die Debug-Engine (de) darstellt und die für jede andere gültige Schnittstelle abgefragt werden kann, die einer de (z. b. [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) oder [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)) zugeordnet ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die resultierende Schnittstelle sollte mit Bedacht verwendet werden, da durch den Aufruf von über Schnittstellen, die von dieser Methode abgerufen werden, die Verarbeitung des Sitzungs-Debug-Managers umgangen wird. Dies kann dazu führen, dass die SDM in einen fehlerhaften Zustand versetzt wird oder

## <a name="see-also"></a>Weitere Informationen
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
