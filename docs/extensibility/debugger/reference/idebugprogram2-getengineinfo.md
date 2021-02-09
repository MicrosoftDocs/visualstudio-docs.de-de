---
title: 'IDebugProgram2:: getengineingefo | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetEngineInfo
helpviewer_keywords:
- IDebugProgram2::GetEngineInfo
ms.assetid: 3a4f2dc0-e082-4d8d-aeaf-463ab09d279b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b26d6dcde31d3599c8aa8f8223c1f3cf00a59437
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906254"
---
# <a name="idebugprogram2getengineinfo"></a>IDebugProgram2::GetEngineInfo
Ruft den Namen und die GUID der Debug-Engine (de) ab, die dieses Programm ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEngineInfo( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo( 
   out string pbstrEngine,
   out GUID   pguidEngine
);
```

## <a name="parameters"></a>Parameter
`pbstrEngine`\
vorgenommen Gibt den Namen des-Programms zurück, auf dem das Programm ausgeführt wird.

`pguidEngine`\
vorgenommen Gibt die GUID des-Programms zurück, auf dem dieses Programm ausgeführt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Jede de definiert eine eigene GUID zur Identifizierung.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
