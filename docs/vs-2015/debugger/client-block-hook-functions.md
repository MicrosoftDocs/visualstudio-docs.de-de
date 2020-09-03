---
title: Hookfunktionen für Clientblöcke | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5b1c754255ba0bc659c9b6968ad8ba0dea629ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702322"
---
# <a name="client-block-hook-functions"></a>Hookfunktionen für Clientblöcke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie die in `_CLIENT_BLOCK`-Blöcken gespeicherten Daten überprüfen oder als Bericht ausgeben möchten, können Sie speziell für diesen Zweck eine Funktion schreiben. Der Prototyp dieser Funktion muss etwa wie der folgende, in CRTDBG.H definierte Prototyp aussehen:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 Das bedeutet, dass die Hookfunktion einen **void**-Zeiger auf den Anfang des Zuweisungsblocks sowie einen Wert vom Typ **size_t**, der die Zuweisungsgröße angibt, akzeptieren und `void` zurückgeben muss. Der restliche Inhalt dieser Funktion ist Ihnen freigestellt.  
  
 Nachdem Sie die Hookfunktion mithilfe von [_CrtSetDumpClient](https://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033) installiert haben, wird sie bei jedem Dump eines `_CLIENT_BLOCK`-Blocks aufgerufen. Mithilfe von [_CrtReportBlockType](https://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) können Sie anschließend Informationen zum Typ oder Untertyp der im Dump ausgegebenen Blöcke abrufen.  
  
 Der Zeiger auf die Funktion, den Sie an `_CrtSetDumpClient` übergeben, ist vom Typ **_CRT_DUMP_CLIENT**, wie in „CRTDBG.H“ definiert:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schreiben von Hookfunktionen für Hook](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 Beispiel](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](https://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)
