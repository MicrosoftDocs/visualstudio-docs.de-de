---
title: 'IDiaDataSource:: get_lastError | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3ad0570436dda6ac9ae52325c891b32a563cf6f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547363"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Dateinamen für den letzten Ladefehler ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pRetVal  
 vorgenommen Gibt eine Zeichenfolge zurück, die den Namen der PDB-Datei enthält, die dem letzten Ladefehler zugeordnet ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt den letzten Fehlercode zurück, der durch einen Ladevorgang verursacht wurde. Gibt zurück, `E_INVALIDARG` Wenn der- `pRetVal` Parameter ist `NULL` .  
  
## <a name="example"></a>Beispiel  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
