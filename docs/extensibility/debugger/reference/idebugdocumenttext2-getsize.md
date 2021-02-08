---
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
ms.openlocfilehash: ecb8257d2428222fd18d6cafdfde950cb743f293
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844865"
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
