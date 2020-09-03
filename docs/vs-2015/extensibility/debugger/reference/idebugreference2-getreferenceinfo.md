---
title: 'IDebugReference2:: getreferenceingefo | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 77cccb562db79d9f6a53113bda0c4434e19c6813
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155828"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) -Struktur ab, die einen Verweis beschreibt. Für zukünftige Verwendung reserviert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```csharp  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFields`  
 in Eine Kombination von Flags aus der [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) Enumeration, die die in der [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Struktur auszufüllenden Felder bestimmen.  
  
 `nRadix`  
 in Der zum Formatieren numerischer Informationen zu verwendende Basis.  
  
 `dwTimeout`  
 in Maximale Zeit in Millisekunden, die gewartet werden soll, bevor diese Methode zurückgegeben wird. Verwenden `INFINITE` Sie, um unbegrenzt zu warten.  
  
 `rgpArgs`  
 in Ein Array von [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) -Objekten. Für zukünftige Verwendung reserviert. Legen Sie auf einen NULL-Wert fest.  
  
 `dwArgCount`  
 in Die Anzahl der Verweis Argumente im `rgpArgs` Array. Für zukünftige Verwendung reserviert. Legen Sie auf 0 fest.  
  
 `pReferenceInfo`  
 vorgenommen Eine [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) -Struktur, die mit einer Beschreibung der Eigenschaft ausgefüllt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
