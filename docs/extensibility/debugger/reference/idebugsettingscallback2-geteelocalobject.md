---
description: Ruft ein lokales Objekt der Ausdrucks Auswertung unter Berücksichtigung des metriknamens ab.
title: 'IDebugSettingsCallback2:: geteelocalobject | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEELocalObject
ms.assetid: e69a3469-a049-420c-b918-c48a1e7b9baf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72ff072cdb6c0431a7b04e644f71186c91763efa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168763"
---
# <a name="idebugsettingscallback2geteelocalobject"></a>IDebugSettingsCallback2::GetEELocalObject
Ruft ein lokales Objekt der Ausdrucks Auswertung unter Berücksichtigung des metriknamens ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEELocalObject(
   REFGUID     guidLang,
   REFGUID     guidVendor,
   LPCWSTR     pszMetric,
   IUnknown ** ppUnk
);
```

```csharp
private int GetEELocalObject(
   ref Guid          guidLang,
   ref Guid          guidVendor,
   string            pszMetric,
   out System.Object ppUnk
);
```

## <a name="parameters"></a>Parameter
`guidLang`\
in Eindeutiger Bezeichner der Programmiersprache.

`guidVendor`\
in Eindeutiger Bezeichner des Anbieters.

`pszMetric`\
in Der Name der Metrik.

`ppUnk`\
vorgenommen Gibt das lokale Objekt der Ausdrucks Auswertung zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
