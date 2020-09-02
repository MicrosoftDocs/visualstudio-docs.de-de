---
title: IDebugPort2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c9227e2e05499feac628a5b90fc6e3d2a4399992
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188560"
---
# <a name="idebugport2"></a>IDebugPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt einen debugsport auf einem Computer dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle, um einen Debugport auf einem Computer darzustellen.  
  
 Wenn der Port Sende Port Ereignisse unterstützt, muss er auch die- <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Schnittstelle implementieren, um eine Schnittstelle zu unterstützen, die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> wiederum die [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) -Schnittstelle bietet.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Aufrufe von [getPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) oder [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) geben diese Schnittstelle zurück, die den angeforderten Port darstellt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugPort2` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Gibt den Portnamen zurück.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Gibt den Port Bezeichner zurück.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Gibt die Anforderung zurück, die zum Erstellen eines Ports verwendet wird (falls verfügbar).|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Gibt den Port Lieferanten für diesen Port zurück.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Gibt eine Schnittstelle zum Prozess zurück, wenn der Bezeichner des Prozesses angegeben ist.|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Listet alle Prozesse auf, die auf einem Port ausgeführt werden.|  
  
## <a name="remarks"></a>Bemerkungen  
 Der lokale Port ermöglicht den Zugriff auf alle Prozesse und Programme, die auf dem lokalen Computer ausgeführt werden. Andere Ports stellen möglicherweise eine serielle Kabelverbindung mit einem Windows CE basierten Gerät oder eine Netzwerkverbindung mit einem nicht-DCOM-Computer dar. Die `IDebugPort2` -Schnittstelle wird verwendet, um den Namen und den Bezeichner eines Ports zu suchen, alle Prozesse aufzulisten, die auf dem Port ausgeführt werden, und Funktionen zum Starten und Beenden von Prozessen auf dem Port bereitzustellen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
