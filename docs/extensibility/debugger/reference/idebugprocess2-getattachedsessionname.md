---
description: Ruft den Namen der Sitzung ab, die diesen Prozess debuggt.
title: 'IDebugProcess2:: getattachedsessionname | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63d83a9d5f89ea06744454b790d988f1881c193b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142543"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Ruft den Namen der Sitzung ab, die diesen Prozess debuggt. Eine IDE kann diese Informationen für einen Benutzer anzeigen, der einen bestimmten Prozess auf einem bestimmten Computer debuggt.

> [!NOTE]
> Diese Methode ist veraltet, und ihre Implementierung sollte immer zurückgeben `E_NOTIMPL` .

## <a name="syntax"></a>Syntax

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>Parameter
`pbstrSessionName`\

## <a name="return-value"></a>Rückgabewert
 Diese Methode sollte immer zurückgeben `E_NOTIMPL` .

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
