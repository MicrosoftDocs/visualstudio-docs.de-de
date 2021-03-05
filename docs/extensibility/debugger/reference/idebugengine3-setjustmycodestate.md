---
description: Diese Methode teilt der Debug-Engine die Statusinformationen "justMyCode" mit.
title: 'IDebugEngine3:: setjustmycodestate | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a81fa4bda506cf1be27f658b071910e7c8ccd8a7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153702"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Diese Methode teilt der Debug-Engine die Statusinformationen "justMyCode" mit.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>Parameter
`fUpdate`\
in Ungleich NULL ( `TRUE` ) zum Aktualisieren aktueller Informationen, 0 (null), `FALSE` um alle Informationen zurückzusetzen (wobei zuvor festgelegte Elemente ignoriert werden).

`dwModules`\
in Anzahl von Informationsstrukturen in `rgJMCSpec.`

`rgJMCSpec`\
in Array der zu verwendenden [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Strukturen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 JustMyCode ist das Konzept, nur den Code zu debuggen, der einem Benutzer angehört, und alle zwischen Codes, wie z. b. Systemcode, zu ignorieren – auch wenn Quellcode für diesen Systemcode verfügbar ist.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
