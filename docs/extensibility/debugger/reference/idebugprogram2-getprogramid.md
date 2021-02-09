---
title: 'IDebugProgram2:: getProgramId | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7723333547e0aeac7fe7a73c0dc40b36f4b6e071
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890031"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Ruft eine GUID für dieses Programm ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetProgramId( 
   GUID* pguidProgramId
);
```

```csharp
int GetProgramId( 
   out Guid pguidProgramId
);
```

## <a name="parameters"></a>Parameter
`pguidProgramId`\
vorgenommen Gibt die `GUID` für dieses Programm zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Eine Debug-Engine (de) muss den Programm Bezeichner zurückgeben, der ursprünglich an die [onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) -oder [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode übermittelt wurde Dies ermöglicht die Identifizierung des Programms in Debugger-Komponenten.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
