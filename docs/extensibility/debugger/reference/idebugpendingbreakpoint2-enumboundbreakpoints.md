---
title: 'IDebugPendingBreakpoint2:: enumboundbreakpoints | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::EnumBoundBreakpoints
helpviewer_keywords:
- EnumBoundBreakpoints method
- IDebugPendingBreakpoint2::EnumBoundBreakpoints method
ms.assetid: 179c7c54-8446-462d-b099-e0f9cf06dc52
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2b65e36552ccdf8bf30777f13761183eb38e6700
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953096"
---
# <a name="idebugpendingbreakpoint2enumboundbreakpoints"></a>IDebugPendingBreakpoint2::EnumBoundBreakpoints
Listet alle Haltepunkte auf, die von diesem ausstehenden Haltepunkt gebunden sind.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumBoundBreakpoints( 
   IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int EnumBoundBreakpoints( 
   out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
vorgenommen Gibt ein [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) -Objekt zurück, das die gebundenen Breakpoints auflistet.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt zurück, `E_BP_DELETED` Wenn der Breakpoint gelöscht wurde.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird gezeigt, wie diese Methode für ein einfaches-Objekt implementiert wird `CPendingBreakpoint` , das die [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) -Schnittstelle verfügbar macht.

```cpp
HRESULT CPendingBreakpoint::EnumBoundBreakpoints(IEnumDebugBoundBreakpoints2** ppEnum)
{
   HRESULT hr;

   // Verify that the passed IEnumDebugBoundBreakpoints2 interface pointer
   // is valid.
   if (ppEnum)
   {
      *ppEnum = NULL;

      // Verify that the pending breakpoint has not been deleted. If
      // deleted, then return hr = E_BP_DELETED.
      if (m_state.state != PBPS_DELETED)
      {
         // If the bound breakpoint member variable is valid.
         if (m_pBoundBP)
         {
            // Get the bound breakpoint.
            CComPtr<IDebugBoundBreakpoint2> spBoundBP;
            hr = m_pBoundBP->QueryInterface(&spBoundBP);
            assert(hr == S_OK);
            if (hr == S_OK)
            {
               // Create the bound breakpoint enumerator.
               CComObject<CEnumDebugBoundBreakpoints>* pBoundEnum;
               hr = CComObject<CEnumDebugBoundBreakpoints>::CreateInstance(&pBoundEnum);
               assert(hr == S_OK);
               if (hr == S_OK)
               {
                  // Initialize the enumerator of bound breakpoints with
                  // the IDebugBoundBreakpoint2 information.
                  IDebugBoundBreakpoint2* rgBoundBP[] = { spBoundBP.p };
                  hr = pBoundEnum->Init(rgBoundBP, &(rgBoundBP[1]), NULL, AtlFlagCopy);
                  if (hr == S_OK)
                  {
                     // Verify that the passed IEnumDebugBoundBreakpoints2
                     // interface can be queried by the created
                     // CEnumDebugBoundBreakpoints object.
                     hr = pBoundEnum->QueryInterface(ppEnum);
                     assert(hr == S_OK);
                  }

                  // Otherwise, delete the CEnumDebugBoundBreakpoints object.
                  if (FAILED(hr))
                  {
                     delete pBoundEnum;
                  }
               }
            }
         }
         else
         {
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
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
