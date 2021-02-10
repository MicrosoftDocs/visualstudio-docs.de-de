---
title: 'IDebugProperty2:: setvalueasreference | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2ed6cbf32d807734714f25453e33fe8bdd7fac0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961793"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Legt den Wert dieser Eigenschaft auf den Wert des angegebenen Verweises fest.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetValueAsReference(
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```csharp
int SetValueAsReference(
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parameter
`rgpArgs`\
in Ein Array von Argumenten, die an den Eigenschaften Setter für verwaltete Code übergeben werden. Wenn der Eigenschaften Setter keine Argumente annimmt oder dieses [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt nicht auf einen solchen Eigenschaften Setter verweist, `rgpArgs` sollte ein NULL-Wert sein. Dieser Parameter ist in der Regel ein NULL-Wert.

`dwArgCount`\
in Die Anzahl der Argumente im `rgpArgs` Array.

`pValue`\
in Ein Verweis in Form eines [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) -Objekts auf den Wert, der zum Festlegen dieser Eigenschaft verwendet werden soll.

`dwTimeout`\
in Gibt an, wie lange die Festlegung des Werts dauert (in Millisekunden). Ein typischer Wert ist `INFINITE` . Dies wirkt sich auf die Zeitspanne aus, die eine mögliche Auswertung annehmen kann.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird ein Fehlercode zurückgegeben, in der Regel einer der folgenden:

|Fehler|BESCHREIBUNG|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Das Festlegen des Werts aus einem Verweis wird nicht unterstützt.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Der Wert kann nicht festgelegt werden, da sich diese Eigenschaft auf eine Methode bezieht.|
|`E_SETVALUE_VALUE_IS_READONLY`|Der Wert ist schreibgeschützt und kann nicht festgelegt werden.|
|`E_NOTIMPL`|Die Methode ist nicht implementiert.|

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
