---
title: 'Idebugsymbolprovider:: getaddressesfromposition | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15838ff1efe9cba6920b98a8b7f00cb62f2fc3b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956463"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Mit dieser Methode wird eine Dokument Position einem Array von debugadressen zugeordnet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAddressesFromPosition( 
   IDebugDocumentPosition2* pDocPos,
   BOOL                     fStatmentOnly,
   IEnumDebugAddresses**    ppEnumBegAddresses,
   IEnumDebugAddresses**    ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromPosition( 
   IDebugDocumentPosition2  pDocPos,
   bool                     fStatmentOnly,
   out IEnumDebugAddresses  ppEnumBegAddresses,
   out IEnumDebugAddresses  ppEnumEndAddresses
);
```

## <a name="parameters"></a>Parameter
`pDocPos`\
in Die Position des Dokuments.

`fStatmentOnly`\
in Wenn true, werden die debugadressen auf eine einzige Anweisung beschränkt.

`ppEnumBegAddresses`\
vorgenommen Gibt einen Enumerator für die Start-debugadressen zurück, die dieser Anweisung oder Zeile zugeordnet sind.

`ppEnumEndAddresses`\
vorgenommen Gibt einen [ienumdebugadressen](../../../extensibility/debugger/reference/ienumdebugaddresses.md) -Enumerator für die End-debugadressen zurück, die dieser Anweisung oder Zeile zugeordnet sind.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Eine Dokument Position gibt in der Regel einen Bereich von Quellzeilen an. Diese Methode stellt die mit diesen Zeilen verknüpften Start-und End-debugadressen bereit. Einige Sprachen lassen Anweisungen zu, die mehrere Zeilen umfassen, oder Zeilen, die mehr als eine Anweisung enthalten. Diese Methode stellt ein Flag bereit, um die debugadressen auf eine einzelne Anweisung zu beschränken.

 Es ist möglich, dass eine einzelne Anweisung mehrere debugadressen hat, wie im Fall von Vorlagen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
