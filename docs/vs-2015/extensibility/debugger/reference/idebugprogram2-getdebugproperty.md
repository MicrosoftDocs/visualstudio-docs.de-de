---
title: 'IDebugProgram2:: getdebug Property | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29b86a1aa144e553b126445a865330a8edb786ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187905"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Eigenschaften des Programms ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppProperty`  
 vorgenommen Gibt ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt zurück, das die Eigenschaften des Programms darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Eigenschaften, die von dieser Methode zurückgegeben werden, sind spezifisch für das Programm. Wenn das Programm mehr als eine Eigenschaft zurückgeben muss, ist das von dieser Methode zurückgegebene [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt ein Container mit zusätzlichen Eigenschaften, und der Aufruf der [enumchildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) -Methode gibt eine Liste aller Eigenschaften zurück.  
  
 Ein Programm kann eine beliebige Anzahl und einen Typ zusätzlicher Eigenschaften verfügbar machen, die über die-Schnittstelle beschrieben werden können `IDebugProperty2` . Eine IDE zeigt möglicherweise die zusätzlichen Programm Eigenschaften über eine Benutzeroberfläche des generischen Eigenschaften Browsers an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
