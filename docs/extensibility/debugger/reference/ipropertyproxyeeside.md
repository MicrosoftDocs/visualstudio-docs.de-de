---
title: Ipropertyproxyeeside | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f0331365716c8399c1b2a565fc8046482df5d80f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938901"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Diese Schnittstelle stellt Methoden zum Anzeigen von Daten für das zugeordnete-Objekt bereit. Diese Schnittstelle ist Teil der Unterstützung für typvisualisierungen.

## <a name="syntax"></a>Syntax

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von einer Ausdrucks Auswertung implementiert, um typvisualisierungen zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [getpropertyproxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) auf, um diese Schnittstelle zu erhalten. Rufen Sie [QueryInterface](/cpp/atl/queryinterface) für eine [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle auf, um die [ipropertyproxyprovider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) -Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge
 Die folgenden Methoden werden von dieser Schnittstelle implementiert:

|Methode|Beschreibung|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Initialisiert einen Datenquellen Anbieter, damit auf die Daten des Objekts zugegriffen werden kann.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Ruft Informationen zur Assembly des Objekts ab.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Ruft die Anfangsdaten für das-Objekt ab.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Erstellt eine Kopie eines vorhandenen Datenspeichers.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Erstellt einen Verweis auf eine vorhandene Datenspeicherung.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Ruft Informationen zu einer bestimmten Assembly im Kontext der Assembly ab, die dieses-Objekt enthält.|

## <a name="remarks"></a>Bemerkungen
 Eine typschnell Ansicht verwendet diese Schnittstelle für den Zugriff auf die Werte, die dem Objekt zugeordnet sind, zu dem diese Schnittstelle gehört. Der Zugriff auf die Daten erfolgt über die [ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Schnittstelle, die eine schreibgeschützte Ansicht der Daten bereitstellt.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
