---
title: 'Idebugfield:: GetSize | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6330179f1bbfffcb1f590dfc09ae0c06385f12e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869855"
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
Diese Methode ruft die Größe eines Felds in Bytes ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSize( 
   DWORD* pdwSize
);
```

```csharp
int GetSize(
   out uint pdwSize
);
```

## <a name="parameters"></a>Parameter
`pdwSize`\
vorgenommen Gibt die Größe zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Alle Felder haben einen Typ, und alle Typen haben eine Größe. Ein Feld mit einem Bytetyp hat z. b. eine Größe von 1 Byte.

## <a name="see-also"></a>Weitere Informationen
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
