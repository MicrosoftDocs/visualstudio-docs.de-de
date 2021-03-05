---
description: Gibt einen Bezeichner für den Code Speicherort zurück, der den aktuellen codeort darstellt.
title: 'IDebugDisassemblyStream2:: getcurrentlocation | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
ms.assetid: 512302f1-12b1-4107-8a6e-c5bc878ce1c3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75687f0ad229ae1e2284b18dcc864e17d5b734d3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154430"
---
# <a name="idebugdisassemblystream2getcurrentlocation"></a>IDebugDisassemblyStream2::GetCurrentLocation
Gibt einen Bezeichner für den Code Speicherort zurück, der den aktuellen codeort darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCurrentLocation( 
   UINT64* puCodeLocationId
);
```

```csharp
int GetCurrentLocation( 
   out ulong puCodeLocationId
);
```

## <a name="parameters"></a>Parameter
`puCodeLocationId`\
vorgenommen Gibt den Bezeichner des Code Speicher Orts zurück. Eine Beschreibung eines Code Speicherort Bezeichners finden Sie im Abschnitt "Hinweise" der Methode " [getcodelta ocationid](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) ".

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Bezeichner für den Code Speicherort kann durch Aufrufen der [getcodecontext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) -Methode in einen Code Kontext konvertiert werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
