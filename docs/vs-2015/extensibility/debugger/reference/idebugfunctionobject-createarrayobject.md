---
title: 'Idebugfunctionobject:: anatearrayobject | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 53c1961eb1ed72580fc314d7a1542ddc926780f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205811"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt ein Array Objekt. Dieses Array kann entweder primitive Werte oder Objektinstanzwerte enthalten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ot`  
 in Gibt einen Wert aus der [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) Enumeration an, der den Typ des neuen Array Objekts angibt.  
  
 `pClassField`  
 in Ein [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt, das die Klasse eines Objekts darstellt, wenn ein Array von objektinstanzwerten erstellt wird. Wenn Sie ein Array primitiver Objekte erstellen, ist dieser Parameter ein NULL-Wert.  
  
 `dwRank`  
 in Der Rang oder die Anzahl der Dimensionen des Arrays.  
  
 `dwDims`  
 in Die Größe der einzelnen Dimensionen des Arrays.  
  
 `dwLowBounds`  
 in Der Ursprung der einzelnen Dimensionen (in der Regel 0 oder 1).  
  
 `ppObject`  
 vorgenommen Gibt ein [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt zurück, das das neu erstellte Array darstellt. Dabei handelt es sich eigentlich um ein [idebugarrayobject](../../../extensibility/debugger/reference/idebugarrayobject.md) -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das einen Array Parameter für die Funktion darstellt, die durch die [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Schnittstelle dargestellt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
