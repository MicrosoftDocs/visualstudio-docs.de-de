---
description: Ruft die Attributinformationen als ein BLOB von Bytes ab.
title: 'Idebugcustomattribute:: getattributebytes | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d7cfc3ba650ff8277bb6cb85f5d1530d202bd426
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163082"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Ruft die Attributinformationen als ein BLOB von Bytes ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAttributeBytes( 
   BYTE*  ppBlob,
   DWORD* pdwLen
);
```

```csharp
int GetAttributeBytes(
   ref byte[] ppBlob,
   ref uint   pdwLen
);
```

## <a name="parameters"></a>Parameter
`ppBlob`\
[in, out] Ein Array, das mit dem Attribut Bytes gefüllt ist.

`pdwLen`\
[in, out] Gibt die maximale Anzahl von Bytes an, die im Array zurückgegeben werden sollen, `ppBlob` und gibt die Anzahl der Bytes zurück, die tatsächlich in das Array geschrieben wurden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Legen Sie den- `ppBlob` Parameter auf einen NULL-Wert fest, um die Anzahl der verfügbaren Bytes zurückzugeben. Weisen Sie dann ein Array zu, und übergeben Sie das Array für den `ppBlob` Parameter.

 Die Attribut Bytes stellen die Rohdaten des benutzerdefinierten Attributs dar.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
