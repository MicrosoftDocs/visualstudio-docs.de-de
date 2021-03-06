---
description: Diese Schnittstelle stellt ein Bytearray dar.
title: Ieedatastorage | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9434138114f2b4b0615e20c1b556ff6387c715de
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227332"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Diese Schnittstelle stellt ein Bytearray dar.

## <a name="syntax"></a>Syntax

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Ausdrucks Auswertung (EE) implementiert diese Schnittstelle, um ein Bytearray darzustellen (wird von typvisualisierungen zum Abrufen und Ändern von Daten über die [ipropertyproxyeeside](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) -Schnittstelle verwendet). Der EE implementiert diese Schnittstelle in der Regel, um externe typvisualisierungen zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die-Methoden der- `IPropertyProxyEESide` Schnittstelle geben diese Schnittstelle zurück. Rufen Sie [getpropertyproxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) auf, um die [ipropertyproxyeeside](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) -Schnittstelle zu erhalten. Rufen Sie [QueryInterface](/cpp/atl/queryinterface) für eine [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle auf, um die [ipropertyproxyprovider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) -Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge
 Die- `IEEDataStorage` Schnittstelle implementiert die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Ruft die angegebene Anzahl von Daten Bytes in einen angegebenen Puffer ab.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Ruft die Anzahl der verfügbaren Daten Bytes ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird von einer typschnell Ansicht verwendet, um auf Daten zuzugreifen, die von einem bestimmten Objekt gespeichert werden. Die Daten werden als Bytearray behandelt, sodass die typschnell Ansicht diese auf die gleiche Weise bearbeiten kann, wie Sie dem Benutzer zur Verfügung gestellt wird.

 Ein benutzerdefinierter Viewer kann bei Bedarf auch diese Schnittstelle verwenden, obwohl ein benutzerdefinierter Viewer in der Regel eine benutzerdefinierte Schnittstelle, [getmemorybytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) oder [getstringchars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (für Zeichen folgen orientierte Daten) verwendet.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
