---
title: IDebugProgramProvider2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6a3ccac5dc60c10983d3b1a33978196fad5197d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146325"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese registrierte Schnittstelle ermöglicht es dem sitzungsdebug-Manager (SDM), Informationen zu Programmen zu erhalten, die über die [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) -Schnittstelle "veröffentlicht" wurden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramProvider2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (de) implementiert diese Schnittstelle, um Informationen über Programme bereitzustellen, die debuggt werden. Diese Schnittstelle wird im Abschnitt de der Registrierung unter Verwendung der Metrik registriert `metricProgramProvider` , wie in [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)beschrieben.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die com- `CoCreateInstance` Funktion wird mit dem `CLSID` des Programm Anbieters aufgerufen, der aus der Registrierung abgerufen wird. Weitere Informationen finden Sie im Beispiel.  
  
## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Ruft Informationen zu ausgelaufenden Programmen ab, gefiltert auf unterschiedlichste Weise.|  
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Ruft einen Programmknoten ab, wenn eine bestimmte Prozess-ID angegeben wird.|  
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Richtet einen Rückruf zum Überwachen von Anbieter Ereignissen ein, die bestimmten Arten von Prozessen zugeordnet sind.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Richtet ein Gebiets Schema für alle sprachspezifischen Ressourcen ein, die von der de benötigt werden.|  
  
## <a name="remarks"></a>Bemerkungen  
 Normalerweise wird diese Schnittstelle von einem Prozess verwendet, um die Programme zu ermitteln, die in diesem Prozess ausgeführt werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Beispiel  
  
```cpp#  
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugProgramProvider2 *pProvider = NULL;  
    if (pDebugEngineGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetMetric(NULL,  
                    metrictypeEngine,  
                    *pDebugEngineGuid,  
                    metricProgramProvider,  
                    &clsidProvider,  
                    strRegistrationRoot);  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugProgramProvider2> spProgramProvider;  
            spProgramProvider.CoCreateInstance(clsidProvider);  
            if (spProgramProvider != NULL) {  
                pProvider = spProgramProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
