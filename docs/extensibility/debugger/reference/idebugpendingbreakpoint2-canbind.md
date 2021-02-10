---
title: 'IDebugPendingBreakpoint2:: canbind | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::CanBind
helpviewer_keywords:
- IDebugPendingBreakpoint2::CanBind method
- CanBind method
ms.assetid: 84a2b189-ccf1-467e-8fab-0c0da68f0b91
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89781298dc9134f80f8f57cc0e008068fa47bad3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953200"
---
# <a name="idebugpendingbreakpoint2canbind"></a>IDebugPendingBreakpoint2::CanBind
Bestimmt, ob dieser ausstehende Breakpoint an einen Code Speicherort gebunden werden kann.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanBind ( 
   IEnumDebugErrorBreakpoints2** ppErrorEnum
);
```

```csharp
int CanBind ( 
   out IEnumDebugErrorBreakpoints2 ppErrorEnum
);
```

## <a name="parameters"></a>Parameter
`ppErrorEnum`\
vorgenommen Gibt ein [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) -Objekt zurück, das eine Liste von [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) -Objekten enthält, wenn Fehler auftreten können.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK.` zurück `S_FALSE` gegeben, wenn der Breakpoint nicht gebunden werden kann. in diesem Fall werden die Fehler vom-Parameter zurückgegeben `ppErrorEnum` . Andernfalls wird ein Fehlercode zurückgegeben. Gibt zurück, `E_BP_DELETED` Wenn der Breakpoint gelöscht wurde.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird aufgerufen, um zu bestimmen, was geschieht, wenn dieser ausstehende Haltepunkt gebunden wurde. Ruft die [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) -Methode auf, um den ausstehenden Breakpoint tatsächlich zu binden.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird gezeigt, wie diese Methode für ein einfaches-Objekt implementiert wird `CPendingBreakpoint` , das die [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) -Schnittstelle verfügbar macht.

```cpp
HRESULT CPendingBreakpoint::CanBind(IEnumDebugErrorBreakpoints2** ppErrorEnum)
{
   HRESULT hr;
   HRESULT hrT;

   // Check for a valid pointer to an error breakpoint enumerator
   // interface; otherwise, return hr = E_INVALIDARG.
   if (ppErrorEnum)
   {
      // Verify that the pending breakpoint has not been deleted. If
      // deleted, then return hr = E_BP_DELETED.
      if (m_state.state != PBPS_DELETED)
      {
         // Verify that the breakpoint is a file/line breakpoint.
         if (IsFlagSet(m_pBPRequest->m_bpRequestInfo.dwFields, BPREQI_BPLOCATION) &&
             m_pBPRequest->m_bpRequestInfo.bpLocation.bpLocationType == BPLT_CODE_FILE_LINE)
         {
            hr = S_OK;
         }
         // If the breakpoint type is not a file/line breakpoint, then the
         // result should be an error breakpoint.
         else
         {
            // If the error breakpoint member variable does not have
            // allocated memory.
            if (!m_pErrorBP)
            {
               // Create, AddRef, and initialize a CErrorBreakpoint object.
               if (CComObject<CErrorBreakpoint>::CreateInstance(&m_pErrorBP) == S_OK)
               {
                  m_pErrorBP->AddRef();
                  m_pErrorBP->Initialize(this);
               }
            }

            // Create a new enumerator of error breakpoints.
             CComObject<CEnumDebugErrorBreakpoints>* pErrorEnum;
            if (CComObject<CEnumDebugErrorBreakpoints>::CreateInstance(&pErrorEnum) == S_OK)
            {
               // Get the IDebugErrorBreakpoint2 information for the
               // CErrorBreakpoint object.
               CComPtr<IDebugErrorBreakpoint2> spErrorBP;
               hrT = m_pErrorBP->QueryInterface(&spErrorBP);
               assert(hrT == S_OK);
               if (hrT == S_OK)
               {
                  // Initialize the new enumerator of error breakpoints
                  // with the IDebugErrorBreakpoint2 information.
                  IDebugErrorBreakpoint2* rgpErrorBP[] = { spErrorBP.p };
                  hrT = pErrorEnum->Init(rgpErrorBP, &(rgpErrorBP[1]), NULL, AtlFlagCopy);
                  if (hrT == S_OK)
                  {
                     // Verify that the passed IEnumDebugErrorBreakpoints2
                     // interface can be successful queried by the
                     // created CEnumDebugErrorBreakpoints object.
                     hrT = pErrorEnum->QueryInterface(ppErrorEnum);
                     assert(hrT == S_OK);
                  }
               }

               // Otherwise, delete the CEnumDebugErrorBreakpoints object.
               if (FAILED(hrT))
               {
                  delete pErrorEnum;
               }
            }

            hr = S_FALSE;
         }
      }
      else
      {
         hr = E_BP_DELETED;
      }
   }
   else
   {
      hr = E_INVALIDARG;
   }

   return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [Zwick](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
