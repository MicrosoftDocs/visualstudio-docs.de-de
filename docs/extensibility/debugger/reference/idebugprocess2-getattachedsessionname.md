---
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
ms.openlocfilehash: a4692fdbc08655553a829c0f44037221f2e8b410
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907864"
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
