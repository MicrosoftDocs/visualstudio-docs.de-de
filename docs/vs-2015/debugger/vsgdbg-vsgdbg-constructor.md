---
title: VsgDbg::VsgDbg (Konstruktor) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3bd179aea7d961df6145b7af2f074927fcdc3e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157444"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Konstruktor)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erstellt eine Instanz der `VsgDbg`-Klasse mit oder ohne das Vorbereiten einer In-App-Komponente der Grafikdiagnose, um Grafikinformationen standardmäßig aktiv zu erfassen und aufzuzeichnen, basierend auf dem angegebenen booleschen Parameter.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `bDefaultInit`  
 `true`, um anzugeben, dass die In-App-Komponente der Grafikdiagnose vorbereitet werden muss, um aktiv Grafikinformationen zu erfassen und aufzuzeichnen; `false`, um anzugeben, dass die In-App-Komponente der Grafikdiagnose zu diesem Zeitpunkt nicht vorbereitet werden soll, um aktiv Grafikinformationen zu erfassen und aufzuzeichnen.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Konstruktor aufgerufen wird, während `bDefaultInit` auf `true` festgelegt ist, wird der Dateiname der Grafikprotokolldatei dadurch bestimmt, wie die Präprozessorsymbole `DONT_SAVE_VSGLOG_TO_TEMP` und `VSG_DEFAULT_RUN_FILENAME` definiert sind, bevor `vsgcapture.h` in die App eingeschlossen wird.  
  
 Wenn der Konstruktor mit `bDefaultInit` festgelegt auf `false` aufgerufen wird, kann die In-App-Komponente der Grafikdiagnose vorbereitet werden, um Grafikinformationen zu einem späteren Zeitpunkt aktiv zu erfassen und aufzuzeichnen, indem die `Init`-Funktion aufgerufen wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vsgdbg:: ~ vsgdbg (Dekonstruktor)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
