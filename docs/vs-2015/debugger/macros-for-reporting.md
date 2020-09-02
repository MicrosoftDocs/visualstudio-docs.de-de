---
title: Makros für die Berichterstellung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e4aee33d571f95e24a359fa2bc7e12ae8d64eae0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431627"
---
# <a name="macros-for-reporting"></a>Makros für die Berichterstellung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die in CRTDBG definierten **_RPTn**-und **_RPTFn** -Makros verwenden. H, um die Verwendung von- `printf` Anweisungen für das Debuggen zu ersetzen. Diese Makros verschwinden automatisch in Ihrem Releasebuild, wenn **_DEBUG** nicht definiert ist. Daher müssen Sie Sie nicht in **#ifdef**s einschließen.  
  
|Makro|Beschreibung|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Gibt eine Meldungszeichenfolge und 0 (null) bis vier Argumente aus. Bei _RPT1 bis **_RPT4** fungiert die Meldungszeichenfolge als printf-Formatzeichenfolge für die Argumente.|  
|**_RPTF0**, **_RPTF1**, **, _RPTF2** **_RPTF4**|Identisch mit **_RPTn** , aber diese Makros geben auch den Dateinamen und die Zeilennummer aus, in der sich das Makro befindet.|  
  
 Betrachten Sie das folgende Beispiel:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Durch diesen Code werden die Werte von `someVar` und `otherVar` in **stdout** ausgegeben. Sie können den folgenden Aufruf von `_RPTF2` verwenden, um dieselben Werte und zusätzlich Dateinamen und Zeilennummer auszugeben:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Wenn Sie für eine bestimmte Anwendung Debugberichte benötigen, die mit den Makros aus der C-Laufzeitbibliothek nicht erstellt werden können, können Sie selbst ein geeignetes Makro schreiben. Beispielsweise könnten Sie in eine der Headerdateien mit dem folgenden Beispiel vergleichbaren Code einfügen, durch den ein Makro mit dem Namen **ALERT_IF2** definiert wird:  
  
```  
#ifndef _DEBUG                  /* For RELEASE builds */  
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)  
#else                           /* For DEBUG builds   */  
#define  ALERT_IF2(expr, msg, arg1, arg2) \  
    do { \  
        if ((expr) && \  
            (1 == _CrtDbgReport(_CRT_ERROR, \  
                __FILE__, __LINE__, msg, arg1, arg2))) \  
            _CrtDbgBreak( ); \  
    } while (0)  
#endif  
```  
  
 Ein Aufrufen von **ALERT_IF2** kann alle Funktionen des **printf** -Codes am Anfang dieses Themas ausführen:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Da benutzerdefinierte Makros problemlos geändert werden können, um bedarfsabhängig mehr oder auch weniger Informationen an bestimmte Ziele zu senden, kann sich dieser Ansatz insbesondere bei steigenden Debuganforderungen als nützlich erweisen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md)
