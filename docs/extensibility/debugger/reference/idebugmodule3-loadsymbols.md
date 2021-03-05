---
description: Lädt die Symbole für das aktuelle Modul.
title: 'IDebugModule3:: loadsymbols | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0612be8ffdde8a942331a89e08298f71414a4c76
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164824"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Lädt die Symbole für das aktuelle Modul.

## <a name="syntax"></a>Syntax

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Methode erfolgreich ist, wird `S_OK` zurückgegeben. Bei einem Fehler wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode lädt die Symbole aus dem aktuellen Suchpfad (der durch Aufrufen der [setsymbolpath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) -Methode geändert werden kann).

 Diese Methode wird für die [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) -Methode bevorzugt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
