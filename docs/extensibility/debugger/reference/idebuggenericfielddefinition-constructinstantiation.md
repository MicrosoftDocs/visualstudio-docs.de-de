---
title: 'Idebuggenericfielddefinition:: constructinstantiierung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60ab91340c0f9baf9a75e6e283d3c1158bdbea3b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911114"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
Erstellt eine Feld Instanz, wenn ein Array von Typargumenten angegeben wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ConstructInstantiation(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   IDebugField** ppConstructedField
);
```

```csharp
int ConstructInstantiation(
   uint            cArgs,
   IDebugField[]   ppArgs,
   out IDebugField ppConstructedField
);
```

## <a name="parameters"></a>Parameter
`cArgs`\
in Anzahl der Argumente im `ppArgs` Array.

`ppArgs`\
in Ein Array, das die Typargumente enthält. Die Typargumente müssen geschlossene Typen sein (nicht generische oder vollständig instanziierte Generika).

`ppConstructedField`\
vorgenommen Gibt die [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle zurück, die das neue Feld darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Einschränkungen werden nicht geprüft.

## <a name="see-also"></a>Weitere Informationen
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
