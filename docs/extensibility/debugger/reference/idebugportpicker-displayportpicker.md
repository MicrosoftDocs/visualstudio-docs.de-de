---
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
ms.openlocfilehash: 49cc4500e887a3fbfcd8f6da8a62c42c75ef56aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929536"
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
