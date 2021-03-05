---
description: Diese Methode fügt einen Programmknoten für jede angegebene Debug-Engine (de) hinzu.
title: 'IDebugProcessEx2:: addimplicitprogramnodes | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3a4c6446c2106d79dd14fc0378fc848eac3df18
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159990"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Diese Methode fügt einen Programmknoten für jede angegebene Debug-Engine (de) hinzu.

## <a name="syntax"></a>Syntax

```cpp
HRESULT AddImplicitProgramNodes(
   REFGUID guidLaunchingEngine,
   GUID*   rgguidSpecificEngines,
   DWORD   celtSpecificEngines
);
```

```csharp
int AddImplicitProgramNodes(
   ref Guid guidLaunchingEngine,
   Guid[]   rgguidSpecificEngines,
   uint     celtSpecificEngines
);
```

## <a name="parameters"></a>Parameter
`guidLaunchingEngine`\
in Der `GUID` einer de, die zum Starten von Programmen verwendet werden soll (und davon ausgegangen wird, dass Sie Ihre eigenen Programmknoten hinzufügt).

`rgguidSpecificEngines`\
in Array von des `GUID` s, für das Programmknoten hinzugefügt werden.

`celtSpecificEngines`\
in Die Anzahl der `GUID` im `rgguidSpecificEngines` Array.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
- [Programmknoten](../../../extensibility/debugger/program-nodes.md) werden für jede unter `rgguidSpecificEngines` – mit Ausnahme der Start-Engine (wie in angegeben) hinzugefügt `guidLaunchingEngine` . dabei wird davon ausgegangen, dass beim Starten eines Programms ein eigener Programmknoten hinzugefügt wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Programmknoten](../../../extensibility/debugger/program-nodes.md)
