---
title: 'Idebugobject:: GetSize | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::GetSize
helpviewer_keywords:
- IDebugObject::GetSize method
ms.assetid: 89af423b-36eb-479d-b2de-2693455eca15
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ffafe6b62047a577b2bfce74c8462d9051c4dcfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192265"
---
# <a name="idebugobjectgetsize"></a>IDebugObject::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Größe des-Objekts in Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetSize(   
   UINT* pnSize  
);  
```  
  
```csharp  
int GetSize(  
   out uint pnSize  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pnSize`  
 vorgenommen Gibt die Größe in Bytes zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md) -Methode, um den Wert als Byte Sequenz abzurufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
