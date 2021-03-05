---
description: Ruft die Größe des Texts an dieser Position im Dokument ab.
title: 'IDebugDocumentText2:: GetSize | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91dd1b2a510589ab048bd1bd290b0ab4aabe571b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167307"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Ruft die Größe des Texts an dieser Position im Dokument ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSize( 
   ULONG* pcNumLines,
   ULONG* pcNumChars
);
```

```csharp
int GetSize( 
   ref uint pcNumLines,
   ref uint pcNumChars
);
```

## <a name="parameters"></a>Parameter
`pcNumLines`\
vorgenommen Gibt die Anzahl von Textzeilen zurück.

`pcNumChars`\
vorgenommen Gibt die Anzahl von Textzeichen zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen

 [Nur C++] Wenn ein bestimmter Wert nicht erwünscht ist, übergeben Sie einen NULL-Wert für den-Parameter.

 [Nur c#] Beide Parameter müssen angegeben werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
