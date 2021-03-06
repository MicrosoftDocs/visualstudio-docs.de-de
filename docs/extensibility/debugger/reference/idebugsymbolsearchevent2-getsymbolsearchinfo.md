---
description: Wird von einem Ereignishandler aufgerufen, um Ergebnisse über einen Symbol Ladevorgang abzurufen.
title: 'IDebugSymbolSearchEvent2:: GetSymbolSearchInfo | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9f03562f3370268f720b2d8053bbd6a2979f6a19
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145767"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Wird von einem Ereignishandler aufgerufen, um Ergebnisse über einen Symbol Ladevorgang abzurufen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSymbolSearchInfo(
   IDebugModule3**    pModule,
   BSTR*              pbstrDebugMessage,
   MODULE_INFO_FLAGS* pdwModuleInfoFlags
);
```

```csharp
int GetSymbolSearchInfo(
   IDebugModule3              pModule,
   ref string                 pbstrDebugMessage,
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags
);
```

## <a name="parameters"></a>Parameter
`pModule`\
vorgenommen Ein IDebugModule3-Objekt, das das Modul darstellt, für das die Symbole geladen wurden.

`pbstrDebugMessage`\
[in, out] Gibt eine Zeichenfolge zurück, die alle Fehlermeldungen des Moduls enthält. Wenn kein Fehler vorliegt, enthält diese Zeichenfolge nur den Modulnamen, aber Sie ist nie leer.

> [!NOTE]
> [C++] `pbstrDebugMessage` darf nicht sein `NULL` und muss mit freigegeben werden `SysFreeString` .

`pdwModuleInfoFlags`\
vorgenommen Eine Kombination von Flags aus der [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) Enumeration, die angibt, ob Symbole geladen wurden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn ein Handler das [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) -Ereignis empfängt, nachdem versucht wurde, Debugsymbole für ein Modul zu laden, kann der Handler thismethod zum Ermitteln der Ergebnisse dieser Last abrufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
