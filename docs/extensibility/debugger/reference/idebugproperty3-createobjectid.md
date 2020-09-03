---
title: 'IDebugProperty3:: kreateobjectid | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d3993d674f029260dbe32d16c576cb239ff8d6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721171"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Erstellt eine eindeutige ID für diese Eigenschaft, um sicherzustellen, dass Sie für alle anderen Eigenschaften eindeutig ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird aufgerufen, wenn der Sitzungs-Debug-Manager sicherstellen möchte, dass diese Eigenschaft unter allen anderen Eigenschaften eindeutig identifiziert wird. Die Debug-Engine (de) unterstützt diese Methode, es sei denn, die Eigenschaften, mit denen Sie umgeht, sind bereits eindeutig identifiziert Wenn die de diese Methode nicht unterstützt, wird zurückgegeben `E_NOTIMPL` .

 Jede mit erstellte eindeutige ID `CreateObjectID` wird zerstört, wenn die [destroyobjectid](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) -Methode aufgerufen wird. Dies signalisiert auch das Ende der Notwendigkeit, diese Eigenschaft eindeutig zu identifizieren.

> [!NOTE]
> Es ist keine Methode zum Abrufen dieser eindeutigen ID vorhanden, d. h., der Dienst kann alle für eindeutige IDs benötigten, wenn die- `CreateObjectID` Methode aufgerufen wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
