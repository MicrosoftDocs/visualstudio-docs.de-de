---
title: IDebugComPlusSymbolProvider2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2 interface
ms.assetid: fa2f9b49-03ad-43c7-92d6-6dcb9c3d0531
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 658d7e5b8660a738616dc89be567f01c17406267
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928587"
---
# <a name="idebugcomplussymbolprovider2"></a>IDebugComPlusSymbolProvider2
Stellt einen com+-Symbol Anbieter mit spezifischen Methoden für verwalteten Code dar und erweitert den **idebugcomplussymbolprovider**[idebugcomplussymbolprovider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md).

## <a name="syntax"></a>Syntax

```
IDebugComPlusSymbolProvider2 : IDebugComPlusSymbolProvider
```

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden für die [idebugcomplussymbolprovider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) -Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:

|Methode|Beschreibung|
|------------|-----------------|
|[FunctionHasLineInfo](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-functionhaslineinfo.md)|Bestimmt, ob die angegebene Methode über Zeilen Informationen verfügt.|
|[GetTypesByName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypesbyname.md)|Ruft einen Typ mit dem angegebenen Namen ab.|
|[GetTypeFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypefromtoken.md)|Ruft einen Typ ab, der sein Token erhält.|
|[IsAddressSequencePoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-isaddresssequencepoint.md)|Bestimmt, ob die angegebene debugadresse ein Sequenz Punkt ist.|
|[LoadSymbolsFromCallback](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromcallback.md)|Lädt Debugsymbole mit der angegebenen Rückruf Methode.|
|[LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)|Lädt Debugsymbole aus einem Datenstrom, wenn das **ICorDebugModule** -Objekt angegeben ist.|
|[LoadSymbolsWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolswithcormodule.md)|Lädt Debugsymbole, wenn das **ICorDebugModule** -Objekt angegeben ist.|

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
