---
title: IDebugModule2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a43c7e7ed24da7d73784e20e9e998bdfe69cbd65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929746"
---
# <a name="idebugmodule2"></a>IDebugModule2
Diese Schnittstelle stellt ein Modul dar, d. –. eine ausführbare Einheit eines Programms – z. b. eine DLL.

## <a name="syntax"></a>Syntax

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (de) implementiert diese Schnittstelle, um ein Modul darzustellen und Zugriff auf Informationen über dieses Modul bereitzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Bei einem [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) -Rückruf wird diese Schnittstelle zurückgegeben. Der de sendet mithilfe der- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Methode die [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) -Schnittstelle an den Sitzungs-Debug-Manager (SDM).

 Diese Schnittstelle kann auch in einer [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Struktur zurückgegeben werden (die durch einen aufzurufenden [enumframeinfo-Befehl](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)zurückgegeben wird).

- [Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) gibt auch diese Schnittstelle zurück ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) gibt die [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) -Schnittstelle zurück).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugModule2` .

|Methode|Beschreibung|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Ruft den [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) ab, der dieses Modul beschreibt.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|VERALTET. Verwenden Sie nicht. Lädt die Symbole für dieses Modul erneut.|

## <a name="remarks"></a>Bemerkungen
 Modul Informationen können im Fenster " **Module** " der IDE angezeigt werden.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
