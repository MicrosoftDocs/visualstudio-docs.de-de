---
title: 'IDebugProgram2:: Step | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd9d314865eb2051b67d7c127a6c5cc2395b1863
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387225"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Führt einen Schritt aus.  
  
> [!NOTE]
> Diese Methode ist als veraltet markiert. Verwenden Sie stattdessen die [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) -Methode.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pThread`  
 in Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den abgestuften Thread darstellt.  
  
 `sk`  
 in Ein Wert aus der [stepkind](../../../extensibility/debugger/reference/stepkind.md) -Enumeration, der die Art des Schritts angibt.  
  
 `step`  
 in Ein Wert aus der [stepunit](../../../extensibility/debugger/reference/stepunit.md) -Enumeration, der die Einheit des Schritts angibt (z. b. durch Anweisung oder Anweisung).  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine Thread Synchronisierung oder Kommunikation zwischen Threads vorhanden ist, sollten andere Threads im Programm ausgeführt werden, wenn ein bestimmter Thread schrittweise ausgeführt wird.  
  
> [!WARNING]
> Senden Sie während der Behandlung dieses Aufrufes kein anhalteereignis oder ein sofortiges (synchrones [) Ereignis.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Andernfalls reagiert der Debugger möglicherweise nicht mehr.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
