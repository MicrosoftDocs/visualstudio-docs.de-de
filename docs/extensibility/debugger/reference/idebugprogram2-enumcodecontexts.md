---
description: Ruft eine Liste der Code Kontexte für eine angegebene Position in einer Quelldatei ab.
title: 'IDebugProgram2:: enumcodekontexte | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd26ee9fe0c6e28695eeca5a77a5b90fbbb25213
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164733"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
Ruft eine Liste der Code Kontexte für eine angegebene Position in einer Quelldatei ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumCodeContexts( 
   IDebugDocumentPosition2*  pDocPos,
   IEnumDebugCodeContexts2** ppEnum
);
```

```csharp
int EnumCodeContexts( 
   IDebugDocumentPosition2     pDocPos,
   out IEnumDebugCodeContexts2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`pDocPos`\
in Ein [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) -Objekt, das eine abstrakte Position in einer Quelldatei darstellt, die der IDE bekannt ist.

`ppEnum` vorgenommen Gibt ein [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) -Objekt zurück, das eine Liste der Code Kontexte enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode ermöglicht dem sitzungsdebug-Manager (SDM) oder der IDE, eine Quelldatei Position einer Code Position zuzuordnen. Wenn die Quelle mehrere Code Blöcke generiert (z. b. C++-Vorlagen), wird mehr als ein Code Kontext zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
