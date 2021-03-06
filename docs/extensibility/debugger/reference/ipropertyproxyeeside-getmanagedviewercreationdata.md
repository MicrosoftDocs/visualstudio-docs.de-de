---
description: Ruft Informationen über den Viewer für diesen Eigenschaftentyp ab, um diesen Viewer zu instanziieren.
title: 'Ipropertyproxyeeside:: getmanagedviewerkreationdata | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f2d7d4ef3f35cb0ad00f91033213449af8cb7306
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224134"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Ruft Informationen über den Viewer für diesen Eigenschaftentyp ab, um diesen Viewer zu instanziieren.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
   out string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     className,
   out enum_ASSEMBLYLOCRESOLUTION alr,
   out int                        replacementOk
);
```

## <a name="parameters"></a>Parameter
`assemName`\
vorgenommen Gibt den Namen der Assembly zurück, die dieses-Objekt enthält.

`assemBytes`\
vorgenommen Gibt ein [ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Objekt zurück, das die Assemblybytes dieses Objekts enthält (Dies ist ein NULL-Wert, wenn keine Bytes verfügbar sind).

`assemPdb`\
vorgenommen Gibt ein `IEEDataStorage` Objekt zurück, das die Symbol Speicherinformationen für dieses Objekt enthält (Dies ist ein NULL-Wert, wenn kein Symbol Speicher verfügbar ist).

`className`\
vorgenommen Gibt den Klassennamen zurück, der dieses-Objekt enthält.

`alr`\
vorgenommen Gibt einen Wert aus der [assemblylokresolution](../../../extensibility/debugger/reference/assemblylocresolution.md) -Enumeration zurück, der den Speicherort der Assembly angibt.

`replacementOk`\
vorgenommen Gibt einen Wert ungleich 0 (NULL `TRUE` ) zurück, wenn der Wert dieses Objekts geändert werden kann; NULL ( `FALSE` ), wenn das Objekt schreibgeschützt ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird von typvisualisierungen verwendet, um einen verwalteten Viewer zu instanziieren.

## <a name="see-also"></a>Weitere Informationen
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
