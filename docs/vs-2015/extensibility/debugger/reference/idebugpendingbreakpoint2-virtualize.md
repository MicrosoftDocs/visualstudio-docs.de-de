---
title: 'IDebugPendingBreakpoint2:: Virtualize | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Virtualize
helpviewer_keywords:
- Virtualize method
- IDebugPendingBreakpoint2::Virtualize method
ms.assetid: 58c8e9a5-4494-47c2-bddb-56f628da6a2d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caf4277afc63d403cc3d02c4d79b9e5f2b1b8d26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143882"
---
# <a name="idebugpendingbreakpoint2virtualize"></a>IDebugPendingBreakpoint2::Virtualize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Schaltet den virtualisierten Zustand dieses ausstehenden Breakpoints um. Wenn ein ausstehender Haltepunkt virtualisiert wird, versucht die Debug-Engine jedes Mal, wenn neuer Code in das Programm geladen wird, Sie zu binden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Virtualize(   
   BOOL fVirtualize  
);  
```  
  
```cpp#  
int Virtualize(   
   int fVirtualize  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fVirtualize`  
 in Legen Sie auf ungleich NULL () fest, `TRUE` um den ausstehenden Breakpoint zu virtualisieren, oder auf NULL ( `FALSE` ), um die Virtualisierung zu deaktivieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt zurück, `E_BP_DELETED` Wenn der Breakpoint gelöscht wurde.  
  
## <a name="remarks"></a>Bemerkungen  
 Jedes Mal, wenn Code geladen wird, wird ein virtualisierter Haltepunkt gebunden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie diese Methode für ein einfaches-Objekt implementiert wird `CPendingBreakpoint` , das die [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) -Schnittstelle verfügbar macht.  
  
```cpp#  
HRESULT CPendingBreakpoint::Virtualize(BOOL fVirtualize)    
{    
   HRESULT hr;    
  
   // Verify that the pending breakpoint has not been deleted. If deleted,   
   // then return hr = E_BP_DELETED.    
   if (m_state.state != PBPS_DELETED)    
   {    
      if (fVirtualize)    
      {    
         // Set the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         SetFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
      else    
      {    
         // Clear the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         ClearFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_BP_DELETED;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
