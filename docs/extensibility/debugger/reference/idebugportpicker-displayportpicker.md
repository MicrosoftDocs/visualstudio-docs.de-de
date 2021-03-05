---
description: Zeigt das angegebene Dialogfeld an, in dem der Benutzer einen Port auswählen kann.
title: Idebugportpicker::D isplayportpicker | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c07e95343521692d41d045a89a4038f5ff64e7b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142556"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Zeigt das angegebene Dialogfeld an, in dem der Benutzer einen Port auswählen kann.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DisplayPortPicker(
   HWND hwndParentDialog,
   BSTR* pbstrPortId
);
```

```csharp
public int DisplayPortPicker(
   int hwndParentDialog,
   out string pbstrPortId
);
```

## <a name="parameters"></a>Parameter
`hwndParentDialog`\
in Handle für das übergeordnete Dialogfeld.

`pbstrPortId`\
vorgenommen Zeichenfolge für den Port Bezeichner

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Ein Rückgabewert von `S_FALSE` (oder ein Rückgabewert von `S_OK` , bei dem `BSTR` auf festgelegt ist `NULL` ) gibt an, dass der Benutzer auf **Abbrechen** geklickt hat.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
