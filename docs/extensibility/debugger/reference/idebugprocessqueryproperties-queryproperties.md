---
title: 'Idebugprocessqueryproperties:: queryproperties | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperties
ms.assetid: 976a9962-b689-45bb-afb6-16b2c5dbc3b8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b7a1bb22b163c06b24db57b15824b82243af4b5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900164"
---
# <a name="idebugprocessquerypropertiesqueryproperties"></a>IDebugProcessQueryProperties::QueryProperties
Diese Methode fragt einen angegebenen Eigenschafts Wert des Debugprozesses ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT QueryProperties(
   ULONG                  celt,
   PROCESS_PROPERTY_TYPE *rgdwPropTypes,
   VARIANT               *rgtPropValues);
```

```csharp
int QueryProperties(
   uint                       celt,
   enum_PROCESS_PROPERTY_TYPE rgdwPropTypes,
   out object[ ]              rgtPropValues);
```

## <a name="parameters"></a>Parameter
`celt`\
in Größe der Arrays, die die Eigenschafts Definitionen und Eigenschaftswerte enthalten.

`dwPropType`\
in Ein Array, das Definitionen der abgefragten Eigenschaften enthält. Mögliche Werte sind:

- PROCESS_PROPERTY_COMMAND_LINE = 1

- PROCESS_PROPERTY_CURRENT_DIRECTORY = 2

- PROCESS_PROPERTY_ENVIRONMENT_VARIABLES = 3

`pvarPropValue`\
vorgenommen Ein Array, das die Eigenschaftswerte enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird nur selten verwendet.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)
