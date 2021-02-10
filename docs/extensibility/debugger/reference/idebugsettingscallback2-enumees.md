---
title: 'IDebugSettingsCallback2:: umumees | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af31c78058ffa0816a566a090288cb1e31c17b70
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963028"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
Listet die verfügbaren Ausdrucksauswertungen unter Berücksichtigung der Sprach-und Hersteller Bezeichner auf.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumEEs(
   DWORD  celtBuffer,
   GUID*  rgguidLang,
   GUID*  rgguidVendor,
   DWORD* pceltEEs
);
```

```csharp
public int EnumEEs(
   uint       celtBuffer,
   ref Guid   rgguidLang,
   ref Guid   rgguidVendor,
   ref uint[] pceltEEs
);
```

## <a name="parameters"></a>Parameter
`celtBuffer`\
in Anzahl der Elemente im `pceltEEs` Puffer.

`rgguidLang`\
[in, out] Eindeutiger Bezeichner für die Programmiersprache.

`rgguidVendor`\
[in, out] Eindeutiger Bezeichner für den Anbieter.

`pceltEEs`\
[in, out] Array von Ausdrucks auswergratoren.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
