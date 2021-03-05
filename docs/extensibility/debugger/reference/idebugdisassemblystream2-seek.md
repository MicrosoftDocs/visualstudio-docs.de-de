---
description: Verschiebt den Lese Zeiger im disassemblystream um eine bestimmte Anzahl von Anweisungen relativ zu einer angegebenen Position.
title: 'IDebugDisassemblyStream2:: Seek | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1799e2fd0fb992a2b60f57e668937a927a14e7bc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170210"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Verschiebt den Lese Zeiger im disassemblystream um eine bestimmte Anzahl von Anweisungen relativ zu einer angegebenen Position.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Seek( 
   SEEK_START          dwSeekStart,
   IDebugCodeContext2* pCodeContext,
   UINT64              uCodeLocationId,
   INT64               iInstructions
);
```

```csharp
int Seek( 
   enum_SEEK_START    dwSeekStart,
   IDebugCodeContext2 pCodeContext,
   ulong              uCodeLocationId,
   long               iInstructions
);
```

## <a name="parameters"></a>Parameter
`dwSeekStart`\
in Ein Wert aus der [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) Enumeration, der die relative Position angibt, an der der Suchvorgang beginnen soll.

`pCodeContext`\
in Das [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt, das den Code Kontext darstellt, zu dem der Suchvorgang relativ ist. Dieser Parameter wird nur bei Verwendung von verwendet `dwSeekStart`  =  `SEEK_START_CODECONTEXT` ; andernfalls wird dieser Parameter ignoriert und kann ein NULL-Wert sein.

`uCodeLocationId`\
in Der Bezeichner für den Code Speicherort, zu dem der Suchvorgang relativ ist. Dieser Parameter wird bei verwendet `dwSeekStart`  =  `SEEK_START_CODELOCID` ; andernfalls wird dieser Parameter ignoriert und kann auf 0 (null) festgelegt werden. Eine Beschreibung eines Code Speicherort Bezeichners finden Sie im Abschnitt "Hinweise" der Methode " [getcodelta ocationid](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) ".

`iInstructions`\
in Die Anzahl der zu verschiebenden Anweisungen in Bezug auf die Position, die in angegeben ist `dwSeekStart` . Dieser Wert kann negativ sein, um rückwärts zu wechseln.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück `S_FALSE` , wenn die Suchposition zu einem Punkt über der Liste der verfügbaren Anweisungen lag. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn die Suche eine Position vor dem Anfang der Liste war, wird die Lese Position auf die erste Anweisung in der Liste festgelegt. Wenn das siehe eine Position nach dem Ende der Liste war, wird die Lese Position auf die letzte Anweisung in der Liste festgelegt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
