---
description: Bestimmt den Speicherort des angegebenen verwalteten Assemblyverweises.
title: 'Ipropertyproxyeeside:: resolveassemblyref | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 687ca5922cc59322c37b7b391a9b5f40d52c14ad
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225577"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
Bestimmt den Speicherort des angegebenen verwalteten Assemblyverweises.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ResolveAssemblyRef(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  assemLocation,
   ASSEMBLYLOCRESOLUTION* alr
);
```

```csharp
int ResolveAssemblyRef(
   ref string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     assemLocation,
   out enum_ASSEMBLYLOCRESOLUTION alr
);
```

## <a name="parameters"></a>Parameter
`assemName`\
in Der Name der Assembly, die aufgelöst werden soll.

`assemBytes`\
vorgenommen Gibt ein [ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Objekt zurück, das die dem Verweis zugeordneten Assemblybytes enthält.

`assemPdb`\
vorgenommen Gibt ein-Objekt zurück, `IEEDataStorage` das die diesem Verweis zugeordneten Symbol Speicherdaten enthält.

`assemLocation`\
vorgenommen Gibt den Pfad zum Speicherort dieses Verweises zurück.

`alr`\
vorgenommen Gibt einen Wert aus der [assemblylokresolution](../../../extensibility/debugger/reference/assemblylocresolution.md) -Enumeration zurück, der den Speicherort der Assembly dieses Verweises angibt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird in der Regel nicht von einer benutzerdefinierten Ausdrucks Auswertung implementiert.

## <a name="see-also"></a>Weitere Informationen
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
