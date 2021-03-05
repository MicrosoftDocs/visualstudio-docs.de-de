---
description: Ruft die Attribute für dieses Debugereignis ab.
title: 'IDebugEvent2:: GetAttributes | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7402c2b5a367a3a0a681a9a17ef89872a7b3e96
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152974"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Ruft die Attribute für dieses Debugereignis ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAttribute( 
   DWORD* pdwAttrib
);
```

```csharp
int GetAttribute( 
   out uint pdwAttrib
);
```

## <a name="parameters"></a>Parameter
`pdwAttrib`\
vorgenommen Eine Kombination von Flags aus der [eventattributenumeration](../../../extensibility/debugger/reference/eventattributes.md) .

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle wird für alle Ereignisse gemeinsam. Diese Methode beschreibt den Typ des Ereignisses. Beispielsweise ist das Ereignis synchron oder asynchron, und ist es ein anhalteereignis.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
