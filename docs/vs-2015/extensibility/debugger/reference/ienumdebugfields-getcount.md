---
title: 'Ienumentbugfields:: GetCount | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFields::GetCount
helpviewer_keywords:
- IEnumDebugFields::GetCount method
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f45cabbc9f95b41cbaabbdef1e3241bdfa7959d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199654"
---
# <a name="ienumdebugfieldsgetcount"></a>IEnumDebugFields::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode gibt die Anzahl der Elemente in der-Enumeration zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pcelt`  
 vorgenommen Gibt die Anzahl der Elemente in der-Enumeration zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist nicht Teil der üblichen com-Enumerationsschnittstelle, die angibt, dass nur "Next", "Clone", "Skip" und "Reset" implementiert werden müssen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
