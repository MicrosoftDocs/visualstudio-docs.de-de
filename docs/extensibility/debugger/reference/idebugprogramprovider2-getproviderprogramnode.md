---
title: 'IDebugProgramProvider2:: getproviderprogramnode | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5d6720626c578ca0ae5e005f8b2f2c8ea0786b6b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959674"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Ruft den Programmknoten für ein bestimmtes Programm ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
);
```

## <a name="parameters"></a>Parameter
`Flags`\
in Eine Kombination von Flags aus der [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) Enumeration. Die folgenden Flags sind für diesen-Befehl typisch:

|Flag|Beschreibung|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Der Aufrufer wird auf dem Remote Computer ausgeführt.|
|`PFLAG_DEBUGGEE`|Der Aufrufer wird gerade gedebuggt (für jeden Knoten werden weitere Informationen über das Marshalling zurückgegeben).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Der Aufrufer wurde angefügt, aber nicht vom Debugger gestartet.|

`pPort`\
in Der Port, auf dem der Aufrufprozess ausgeführt wird.

`processId`\
in Eine [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur, die die ID des Prozesses mit dem fraglichen Programm enthält.

`guidEngine`\
in GUID der Debug-Engine, an die das Programm angefügt ist (sofern vorhanden).

`programId`\
in ID des Programms, für das der Programmknoten angezeigt werden soll.

`ppProgramNode`\
vorgenommen Ein [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) -Objekt, das den angeforderten Programmknoten darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
