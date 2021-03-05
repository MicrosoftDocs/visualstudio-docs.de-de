---
description: Diese Methode deaktiviert die Bearbeitung und Fortsetzung für diesen Prozess (und alle darin enthaltenen Programme) explizit.
title: IDebugProcess3::D isableumc | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ffedebd14f720e006c0bec2044afe80901762b52
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158487"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Diese Methode deaktiviert die Bearbeitung und Fortsetzung für diesen Prozess (und alle darin enthaltenen Programme) explizit. Ein benutzerdefinierter Port Lieferant sollte immer zurückgeben `E_NOTIMPL` .

## <a name="syntax"></a>Syntax

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Parameter
`reason`\
in Ein Wert [aus der](../../../extensibility/debugger/reference/encunavailablereason.md) Enumeration "Enumeration" in "Enumeration".

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

> [!NOTE]
> Ein benutzerdefinierter Port Lieferant sollte immer zurückgeben `E_NOTIMPL` .

## <a name="remarks"></a>Bemerkungen
 Wenn "Bearbeiten und Fortfahren" für einen Prozess deaktiviert ist, kann es nur wieder aktiviert werden, indem der Prozess neu gestartet wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
