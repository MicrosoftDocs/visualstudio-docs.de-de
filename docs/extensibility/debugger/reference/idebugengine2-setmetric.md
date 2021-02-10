---
title: 'IDebugEngine2:: setmetric | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4bb3c01b28f2d2c6e90616d389d9858d3346db72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933517"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Diese Methode legt einen Registrierungs Wert fest, der als Metrik bezeichnet wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

## <a name="parameters"></a>Parameter
`pszMetric`\
in Der Name der Metrik.

`varValue`\
in Gibt den Metrikwert an.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Eine Metrik ist ein Registrierungs Wert, mit dem das Verhalten einer Debug-Engine geändert oder unterstützte Funktionen angekündigt werden. Diese Methode kann den-Befehl an die entsprechende Form der SDK-Hilfsprogramme [für die Debugfunktion](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) weiterleiten `SetMetric` .

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
