---
title: 'IDebugEngine3:: loadsymbols | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f823f0087ee612a7850e000469271e0c2a778b62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887301"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Lädt (bei Bedarf) Symbole für alle Module, die von dieser Debug-Engine gedebuggt werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>Parameter
 Keine.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird der Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Dadurch werden Debugsymbole für alle Module geladen, auf die von dieser Debug-Engine verwiesen wird Die Symbole werden nur geladen, wenn Sie nicht bereits geladen wurden. Symbole werden in den Pfaden durchsucht, die durch einen Aufrufen von [setsymbolpath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)festgelegt werden.

## <a name="see-also"></a>Weitere Informationen
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
