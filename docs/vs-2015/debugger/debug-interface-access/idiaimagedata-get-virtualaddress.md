---
title: 'IDiaImageData:: get_virtualAddress | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_virtualAddress method
ms.assetid: 67ecdc8c-d342-4d0b-b02a-c6b88e22fd02
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df8a8a351fb7557d5483b006c9b0b31ea7fcf27d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202208"
---
# <a name="idiaimagedataget_virtualaddress"></a>IDiaImageData::get_virtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Speicherort im virtuellen Speicher des Bilds ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt die virtuelle Adresse des Bilds zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
