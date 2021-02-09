---
title: Idebugsymbolproviderdirect | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 29f0e7e3d2fefe0f47dc971ebff273bf2745a5ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909430"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Stellt einen Symbol Anbieter dar, der direkten Zugriff auf Metadaten und Kern Symbol Schnittstellen hat.

## <a name="syntax"></a>Syntax

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>Methoden
 Diese Schnittstelle implementiert die folgenden Methoden:

|Methode|Beschreibung|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Ruft den Anwendungs Domänen Bezeichner anhand der debugadresse ab.|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Ruft Informationen zu den Modulen in der Symbolgruppe ab.|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Ruft Informationen über die Symbolgruppe ab, in der der Symbol Anbieter ein Member ist.|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Ruft die Informationen zum Metadatenimport ab.|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Ruft Informationen zur Methode an der angegebenen debugadresse ab.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Ruft einen Symbol Reader für nicht verwalteten Code ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle kann anstelle der meisten anderen Symbol Anbieter Schnittstellen verwendet werden. Er bietet direkten Zugriff auf die Metadaten und `CorSym` Schnittstellen.

## <a name="requirements"></a>Anforderungen
 Header: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
