---
description: Diese Methode legt die Sprache fest, die zum Erstellen von druckbaren Ergebnissen verwendet werden soll.
title: 'Idebugexpressionevaluator:: setlocale | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f109717c030c830f433a02bec52e5931e4b5e467
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152441"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
Diese Methode legt die Sprache fest, die zum Erstellen von druckbaren Ergebnissen verwendet werden soll.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale(
   ushort wLangID
);
```

## <a name="parameters"></a>Parameter
`wLangID`\
in Der Sprachen Bezeichner.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird möglicherweise mehrmals aufgerufen, während die Ausdrucks Auswertung (EE) geladen wird, sodass der EE in der Lage sein muss, die Sprachen im Handumdrehen zu wechseln. Der EE verwendet dieses Gebiets Schema, um Fehlermeldungen und Zeichen folgen in der entsprechenden Sprache zurückzugeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
