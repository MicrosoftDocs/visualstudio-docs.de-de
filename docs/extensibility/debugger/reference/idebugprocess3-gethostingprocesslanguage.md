---
description: Diese Methode gibt eine GUID zurück, die die Sprache dieses Prozesses darstellt, die durch einen-Befehl von sethostingprocesslanguage festgelegt wird.
title: 'IDebugProcess3:: gethostingprocesslanguage | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::GetHostingProcessLanguage
ms.assetid: 52fca002-a9ef-43b1-9192-afbe7bb59ad4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 303f0e5dcd4cc87bbc13e55fcc9b95bc870213d5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158435"
---
# <a name="idebugprocess3gethostingprocesslanguage"></a>IDebugProcess3::GetHostingProcessLanguage
Diese Methode gibt einen zurück, `GUID` der die Sprache dieses Prozesses darstellt, die durch einen-Befehl von [sethostingprocesslanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)festgelegt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetHostingProcessLanguage(
   GUID* pguidLang
);
```

```csharp
int GetHostingProcessLanguage(
   out Guid pguidLang
);
```

## <a name="parameters"></a>Parameter
`pguidLang`\
vorgenommen Der der `GUID` Sprache dieses Prozesses. `GUID_NULL` (C++) oder `Guid.Empty` (c#) bedeutet, dass die Sprache nicht festgelegt ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)
