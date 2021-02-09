---
title: 'IDebugCoreServer3:: enableautoattach | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7873480c979bba4f52203c02864d24aa88cf06cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907998"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Aktiviert das automatische anfügen für die angegebenen Debug-engines.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>Parameter
`rgguidSpecificEngines`\
in Array von GUIDs für jedes Debug-Modul, das als automatische Anfügung markiert werden soll.

`celtSpecificEngines`\
in Die Anzahl der in angegebenen Engines `rgguidSpecificEngines` .

`pszStartPageUrl`\
in Die Start-URL, die beim automatischen Anhängen verwendet werden soll.

`pbstrSessionID`\
vorgenommen Die ID der Sitzung, die automatisch angefügt wurde.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben. Ein Fehlercode ist `E_AUTO_ATTACH_NOT_REGISTERED` , der angibt, dass die Klasse für die automatische Attach-Klasse nicht registriert wurde.

## <a name="remarks"></a>Bemerkungen
 Wenn ein Programm gestartet wird, das der angegebenen URL zugeordnet ist, werden die angegebenen Debug-engines automatisch gestartet und angefügt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
