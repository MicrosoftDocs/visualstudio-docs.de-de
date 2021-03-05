---
description: Mit dieser Methode wird die Sprache festgelegt, unter der der Prozess gehostet wird.
title: 'IDebugProcess3:: Einstellungs Sprache | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d2a95a5f8181b7b58198a8a56b7fb0037ef0bc1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150119"
---
# <a name="idebugprocess3sethostingprocesslanguage"></a>IDebugProcess3::SetHostingProcessLanguage
Mit dieser Methode wird die Sprache festgelegt, unter der der Prozess gehostet wird. Diese Sprache kann dann von der Debug-Engine (de) zum Laden der entsprechenden Ausdrucks Auswertung verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetHostingProcessLanguage(
   REFGUID guidLang
);
```

```csharp
int SetHostingProcessLanguage(
   ref Guid guidLang
);
```

## <a name="parameters"></a>Parameter
`guidLang`\
[in] `GUID` der Sprache, die von der de verwendet werden soll. Geben `GUID_NULL` Sie (C++) oder `Guid.Empty` (c#) an, damit der de die Standardsprache verwendet.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
- [Gethostingprocesslanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md) kann verwendet werden, um die aktuelle Spracheinstellung abzurufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)
