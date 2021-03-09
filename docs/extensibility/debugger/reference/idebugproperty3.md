---
title: IDebugProperty3 | Microsoft-Dokumentation
description: Diese Schnittstelle bietet Unterstützung für das Abrufen einer willkürlich langen Zeichenfolge, die der-Eigenschaft zugeordnet ist. dabei wird der-Eigenschaft eine eindeutige ID zugeordnet, eine Liste benutzerdefinierter Viewer für die Eigenschaft abgerufen, und der Wert einer Eigenschaft wird mit der Möglichkeit zum Melden fehlerender Fehler festgelegt.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 65da477c47e88699cc479f632843f839b3d02f9d
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469774"
---
# <a name="idebugproperty3"></a>IDebugProperty3
Diese Schnittstelle bietet Unterstützung für:

- Abrufen einer willkürlich langen Zeichenfolge, die der-Eigenschaft zugeordnet ist.

- Zuordnen einer eindeutigen ID zur-Eigenschaft.

- Abrufen einer Liste benutzerdefinierter Viewer für die-Eigenschaft.

- Festlegen des Werts einer Eigenschaft mit der Möglichkeit, resultierende Fehler zu melden

## <a name="syntax"></a>Syntax

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle für das gleiche Objekt, das [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) implementiert, um Unterstützung für lange Zeichen folgen, Eigenschaften-IDs und benutzerdefinierte Viewer bereitzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) für eine `IDebugProperty2` Schnittstelle auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den von geerbten Methoden macht `IDebugProperty2` die- `IDebugProperty3` Schnittstelle die folgenden Methoden verfügbar.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Gibt die Länge der Zeichenfolge zurück, die der-Eigenschaft zugeordnet ist.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Gibt die Zeichenfolge in einem vom Benutzer bereitgestellten Puffer zurück.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Erstellt eine eindeutige ID für diese Eigenschaft.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Zerstört die eindeutige ID für diese Eigenschaft.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Gibt die Anzahl der benutzerdefinierten Viewer zurück, mit der diese Eigenschaft angezeigt werden kann.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Gibt die Liste der benutzerdefinierten Viewer zurück, mit der diese Eigenschaft angezeigt werden kann.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Legt den Wert dieser Eigenschaft fest und gibt eine Fehlermeldung zurück, wenn etwas schief gegangen ist.|

## <a name="remarks"></a>Bemerkungen
- [Setvalueasstringwitherror](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) ist die bevorzugte Methode für den Sitzungs-Debug-Manager (SDM), den Wert einer Eigenschaft festzulegen.

## <a name="requirements"></a>Requirements (Anforderungen)
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
