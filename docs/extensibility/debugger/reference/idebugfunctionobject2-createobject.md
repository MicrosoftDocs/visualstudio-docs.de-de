---
description: Erstellt ein-Objekt, das einen Konstruktor mit den angegebenen Auswertungs Kennzeichen-Einstellungen und einem Timeout Wert verwendet.
title: 'IDebugFunctionObject2:: kreateobject | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4cd5eb81972af35b84c688e34b8cbc285c4723c2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143141"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Erstellt ein-Objekt, das einen Konstruktor mit den angegebenen Auswertungs Kennzeichen-Einstellungen und einem Timeout Wert verwendet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>Parameter
`pConstructor`\
in Ein [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Objekt, das den Konstruktor des zu erstellenden Objekts darstellt.

`dwArgs`\
in Die Anzahl der Parameter im `pArg` Array. Stellt die Anzahl von Parametern dar, die an den Konstruktor übergeben werden.

`pArgs`\
in Ein Array von [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekten, das die Parameter darstellt, die an den Konstruktor übergeben werden.

`dwEvalFlags`\
in Eine Kombination von Flags aus der [evalflags](../../../extensibility/debugger/reference/evalflags.md) -Enumeration, die angeben, wie die Auswertung durchgeführt werden soll.

`dwTimeout`\
in Maximale Zeit in Millisekunden, die gewartet werden soll, bevor diese Methode zurückgegeben wird. Verwenden **Sie unbegrenzt,** um unbegrenzt zu warten.

`ppObject`\
vorgenommen Gibt ein **idebugobject** -Objekt zurück, das das neu erstellte-Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das eine Instanz einer Klasse darstellt, oder einen anderen komplexen Typ, der einen Konstruktor benötigt, bei dem es sich um einen Parameter handelt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
