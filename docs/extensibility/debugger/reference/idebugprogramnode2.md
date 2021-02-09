---
title: IDebugProgramNode2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1e6460653795720f10dca7f304035c49e4d8e035
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898528"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
Diese Schnittstelle stellt ein Programm dar, das deentschlbelt werden kann.

## <a name="syntax"></a>Syntax

```
IDebugProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Eine Debug-Engine (de) oder ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle, um ein Programm darzustellen, das gedebuggt werden kann. Diese Schnittstelle wird in der Regel auf demselben Objekt implementiert, das die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle implementiert. Diese Schnittstelle wird bei [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] durch Aufrufen von [publishprogramnode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)registriert.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 [Getproviderprogramnode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) aufrufen, um diese Schnittstelle zurückzugeben. Ein benutzerdefinierter Port Lieferant empfängt diese Schnittstelle über einen [addprogram Node](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)-Rückruf. Ein de empfängt diese Schnittstelle über einen [Anfüge](../../../extensibility/debugger/reference/idebugengine2-attach.md)Befehl.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProgramNode2` .

|Methode|Beschreibung|
|------------|-----------------|
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Ruft den Namen eines Programms ab.|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Ruft den Namen des Prozesses ab, von dem ein Programm gehostet wird.|
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Ruft den System Prozess Bezeichner für den Prozess ab, der ein Programm gehostet.|
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|Veraltet. Verwenden Sie nicht.|
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|Veraltet. Verwenden Sie nicht. Eine alternative Vorgehensweise finden Sie in der [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) -Schnittstelle.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Ruft den Namen und den Bezeichner des ab, auf dem dieses Programm ausgeführt wird.|
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|Veraltet. Verwenden Sie nicht.|

## <a name="remarks"></a>Bemerkungen
 Der Sitzungs-Debug-Manager (SDM) ruft in der Regel [getproviderprogramnode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) auf, um diese Schnittstelle zu erhalten.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
