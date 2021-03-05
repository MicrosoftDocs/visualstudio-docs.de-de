---
description: Ruft eine Computer abhängige Darstellung des Bereichs physischer Adressen ab, der einem Stapel Rahmen zugeordnet ist.
title: 'IDebugStackFrame2:: getphysicalstackrange | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 41664f0e59b0eba6ae8a98599c74bd91fe26cf2a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145923"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Ruft eine Computer abhängige Darstellung des Bereichs physischer Adressen ab, der einem Stapel Rahmen zugeordnet ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>Parameter
`paddrMin`\
vorgenommen Gibt die niedrigste physische Adresse zurück, die diesem Stapel Rahmen zugeordnet ist.

`paddrMax`\
vorgenommen Gibt die höchste physische Adresse zurück, die diesem Stapel Rahmen zugeordnet ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die von dieser Methode zurückgegebenen Informationen werden vom Sitzungs-Debug-Manager (SDM) zum Sortieren von Stapel Rahmen verwendet.

 Es wird davon ausgegangen, dass die aufrufsstapel nach unten wächst, d. h., dass neue Stapel Rahmen bei immer niedrigeren Speicheradressen hinzugefügt werden. Eine Lauf Zeit Architektur muss physische Stapel Bereiche bereitstellen, die dieser Annahme entsprechen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
