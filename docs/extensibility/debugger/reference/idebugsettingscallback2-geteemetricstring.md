---
description: Ruft die Wert Zeichenfolge einer Ausdrucks Auswertungs Metrik unter Berücksichtigung des Namens ab.
title: 'IDebugSettingsCallback2:: geteemetricstring | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricString
ms.assetid: 85e3c093-6a91-4101-ab32-d8ac6eed4918
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e5fa78173eeb74ae5f0137805c09298304abd65
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168750"
---
# <a name="idebugsettingscallback2geteemetricstring"></a>IDebugSettingsCallback2::GetEEMetricString
Ruft die Wert Zeichenfolge einer Ausdrucks Auswertungs Metrik unter Berücksichtigung des Namens ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEEMetricString(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   BSTR*   pbstrValue
);
```

```csharp
private int GetEEMetricString(
   ref Guid   guidLang,
   ref Guid   guidVendor,
   string     pszMetric,
   out string pbstrValue
);
```

## <a name="parameters"></a>Parameter
`guidLang`\
in Eindeutiger Bezeichner der Programmiersprache.

`guidVendor`\
in Eindeutiger Bezeichner des Anbieters.

`pszMetric`\
in Der Name der Metrik.

`pbstrValue`\
vorgenommen Gibt die metrikwertzeichenfolge zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
