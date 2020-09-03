---
title: 'IDebugDocument2:: GetName | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2af7f4dc01ee3a2fe3fb5026602a0b5d4f766b17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731970"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Ruft den Namen des Dokuments in einer von mehreren Formularen ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

## <a name="parameters"></a>Parameter
`gnType`\
in Ein Wert aus der [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) Enumeration, der den Typ des zurück zugebende namens bestimmt.

`pbstrFileName`\
vorgenommen Gibt eine Zeichenfolge zurück, die den Dokumentnamen enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode kann z. b. den Namen des Dokuments als Titel oder als Dateinamen oder sogar als Teil eines Datei namens zurückgeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
