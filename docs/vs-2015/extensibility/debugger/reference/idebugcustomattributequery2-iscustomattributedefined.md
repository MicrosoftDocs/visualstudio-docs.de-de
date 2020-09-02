---
title: 'IDebugCustomAttributeQuery2:: iscustomattributedefined | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6ef6a04d263e322d408bb7d7c95da1929d89010c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569318"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bestimmt, ob ein benutzerdefiniertes Attribut anhand des Namens vorhanden ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszCustomAttributeName`  
 in Eine Zeichenfolge mit dem Namen des zu suchenden benutzerdefinierten Attributs.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt S_OK zurück, wenn das benutzerdefinierte Attribut für dieses Feld definiert ist, andernfalls wird S_FALSE zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Rufen Sie die [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) -Methode auf, um die dem benutzerdefinierten Attribut zugeordneten Attribut Bytes zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
