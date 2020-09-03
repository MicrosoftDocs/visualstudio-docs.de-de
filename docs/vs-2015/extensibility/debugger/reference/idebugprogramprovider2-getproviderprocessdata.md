---
title: 'IDebugProgramProvider2:: getproviderprocessdata | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a50faf4531a098dde544adcffe535ed26e9c5cd8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148519"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft eine Liste der laufenden Programme aus einem angegebenen Prozess ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```csharp  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `Flags`  
 in Eine Kombination von Flags aus der [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) Enumeration. Die folgenden Flags sind für diesen-Befehl typisch:  
  
|Flag|Beschreibung|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|Der Aufrufer wird auf dem Remote Computer ausgeführt.|  
|`PFLAG_DEBUGGEE`|Der Aufrufer wird gerade gedebuggt (für jeden Knoten werden weitere Informationen über das Marshalling zurückgegeben).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Der Aufrufer wurde angefügt, aber nicht vom Debugger gestartet.|  
|`PFLAG_GET_PROGRAM_NODES`|Der Aufrufer fordert eine Liste der Programmknoten an, die zurückgegeben werden sollen.|  
  
 `pPort`  
 in Der Port, auf dem der Aufrufprozess ausgeführt wird.  
  
 `processId`  
 in Eine [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur, die die ID des Prozesses mit dem fraglichen Programm enthält.  
  
 `EngineFilter`  
 in Ein Array von GUIDs für Debug-engines, das zum Debuggen dieses Prozesses zugewiesen ist (diese werden verwendet, um die Programme zu filtern, die basierend auf den von den bereitgestellten Modulen unterstützten Modulen tatsächlich zurückgegeben werden. wenn keine Engines angegeben werden, werden alle Programme zurückgegeben).  
  
 `pProcess`  
 vorgenommen Eine [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) -Struktur, die mit den angeforderten Informationen ausgefüllt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode wird normalerweise von einem Prozess aufgerufen, um eine Liste von Programmen zu erhalten, die in diesem Prozess ausgeführt werden. Die zurückgegebenen Informationen sind eine Liste von [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) -Objekten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
