---
description: Ruft eine Liste optionaler modifiziererer ab.
title: 'Idebugmodopt:: getmodopts | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 971d04662042afed1afe8e1861d0080b513ca74d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149937"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Ruft eine Liste optionaler modifiziererer ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetModOpts(
   ULONG  celt,
   BSTR*  rgelt,
   ULONG* pceltFetched
);
```

```csharp
int GetModOpts(
   uint         celt,
   out string[] rgelt,
   ref uint     pceltFetched
);
```

## <a name="parameters"></a>Parameter
`celt`\
in Anzahl der Elemente, die zurückgegeben werden sollen.

`rgelt`\
vorgenommen Gibt ein Array zurück, das die Optionen enthält.

`pceltFetched`\
[in, out] Anzahl der im Array zurückgegebenen Elemente `rgelt` .

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
