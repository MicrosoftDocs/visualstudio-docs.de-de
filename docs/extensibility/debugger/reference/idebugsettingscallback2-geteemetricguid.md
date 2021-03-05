---
description: Ruft den eindeutigen Bezeichner für eine Ausdrucks auswertungsmetrik unter Berücksichtigung des Namens ab.
title: 'IDebugSettingsCallback2:: geteemetricguid | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricGuid
ms.assetid: 3d70c19a-595d-44f1-a7b3-a0cf8f15e371
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16bc9671ee9f982eaf924d8966f2fc39a274eb6e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165773"
---
# <a name="idebugsettingscallback2geteemetricguid"></a>IDebugSettingsCallback2::GetEEMetricGuid
Ruft den eindeutigen Bezeichner für eine Ausdrucks auswertungsmetrik unter Berücksichtigung des Namens ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEEMetricGuid(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   GUID*   pguidValue
);
```

```csharp
HRESULT GetEEMetricGuid(
   ref Guid guidLang,
   ref Guid guidVendor,
   string   pszMetric,
   out Guid pguidValue
);
```

## <a name="parameters"></a>Parameter
`guidLang`\
in Eindeutiger Bezeichner der Programmiersprache.

`guidVendor`\
in Eindeutiger Bezeichner des Anbieters.

`pszMetric`\
in Der Name der Metrik.

`pguidValue`\
vorgenommen Gibt den eindeutigen Bezeichner der Metrik zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
