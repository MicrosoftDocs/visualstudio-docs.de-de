---
description: Ruft die Anzahl der Wert Zeichenfolgen ab, die für die angegebene Eigenschaft oder das angegebene Feld angezeigt werden sollen.
title: 'Ieevisualizerservice:: getvaluedisplaystringcount | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b77e2537e7581bb15f6458b4515d407fcfa1f827
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222847"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Ruft die Anzahl der Wert Zeichenfolgen ab, die für die angegebene Eigenschaft oder das angegebene Feld angezeigt werden sollen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetValueDisplayStringCount (
   DWORD         displayKind,
   IDebugField * propertyOrField,
   ULONG *       pcelt
);
```

```csharp
int GetValueDisplayStringCount (
   uint        displayKind,
   IDebugField propertyOrField,
   out ulong   pcelt
);
```

## <a name="parameters"></a>Parameter
`displayKind`\
in Der Wert aus der [displaykind](../../../extensibility/debugger/reference/displaykind.md) -Enumeration.

`propertyOrField`\
in Eine [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Schnittstelle, die eine Eigenschaft oder ein Feld darstellt.

`pcelt`\
vorgenommen Gibt die Anzahl der anzuzeigenden Wert Zeichenfolgen zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
