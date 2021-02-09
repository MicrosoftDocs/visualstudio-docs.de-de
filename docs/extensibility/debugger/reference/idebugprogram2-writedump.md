---
title: 'IDebugProgram2:: Write-Dump | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 265c77acdb15069c1fcd7f33d93d4ff74a528eca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896148"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Schreibt ein dump in eine Datei.

## <a name="syntax"></a>Syntax

```cpp
HRESULT WriteDump( 
   DUMPTYPE  DumpType,
   LPCOLESTR pszDumpUrl
);
```

```csharp
int WriteDump( 
   enum_DUMPTYPE  DumpType,
   string         pszDumpUrl
);
```

## <a name="parameters"></a>Parameter
`DumpType`\
in Ein Wert aus der [dumptype](../../../extensibility/debugger/reference/dumptype.md) -Enumeration, der den Typ des dumpwerts angibt, z. b. Short oder Long.

`pszDumpUrl`\
in Die URL, in die der Dump geschrieben werden soll. In der Regel ist dies in Form von `file://c:\path\filename.ext` , kann jedoch eine beliebige gültige URL sein.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein Programm Abbild umfasst in der Regel den aktuellen Stapel Rahmen, den Stapel selbst, eine Liste der Threads, die im Programm ausgeführt werden, und möglicherweise jeglichen Speicher, den das Programm besitzt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
