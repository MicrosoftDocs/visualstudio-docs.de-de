---
title: Makros für die Berichterstellung | Microsoft-Dokumentation
description: Enthält Informationen zu den Debugmakros „_RPTn“ und „_RPTFn“ aus „CRTDBG.H“ und zur Erstellung Ihrer eigenen Debugmakros.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1920b4eddcbffa5cd51d548ade9af3a3a2f208d0
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903791"
---
# <a name="macros-for-reporting"></a>Makros für die Berichterstellung
Sie können zum Debuggen anstelle von `printf`-Anweisungen die in CRTDBG.H definierten Makros **_RPTn** und **_RPTFn** verwenden. Sie müssen sie nicht in **#ifdef**-Blöcke einschließen, da sie automatisch aus dem Releasebuild entfernt werden, wenn **_DEBUG** nicht definiert ist.

|Makro|Beschreibung|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Gibt eine Meldungszeichenfolge und 0 (null) bis vier Argumente aus. Bei **_RPT1** bis **_RPT4** fungiert die Meldungszeichenfolge als printf-Formatzeichenfolge für die Argumente.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF3**, **_RPTF4**|Identisch mit **_RPTn**. Bei diesen Makros wird jedoch zusätzlich der Name der Datei und die Zeilennummer ausgegeben, in der sich das Makro befindet.|

 Betrachten Sie das folgende Beispiel:

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 Durch diesen Code werden die Werte von `someVar` und `otherVar` in **stdout** ausgegeben. Sie können den folgenden Aufruf von `_RPTF2` verwenden, um dieselben Werte und zusätzlich Dateinamen und Zeilennummer auszugeben:

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

Möglicherweise benötigen Sie für eine bestimmte Anwendung Debugberichte, die mit den Makros aus der C-Laufzeitbibliothek nicht erstellt werden können. In diesen Fällen können Sie ein Makro schreiben, das speziell an Ihre Anforderungen angepasst ist. Beispielsweise könnten Sie in eine der Headerdateien mit dem folgenden Beispiel vergleichbaren Code einfügen, durch den ein Makro mit dem Namen **ALERT_IF2** definiert wird:

```cpp
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

 Alle Funktionen des **printf**-Codes können mit einem Aufruf von **ALERT_IF2** ausgeführt werden:

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 Sie können ein benutzerdefiniertes Makro problemlos ändern, um mehr oder weniger Informationen an verschiedene Ziele zu melden. Dieser Ansatz ist besonders nützlich, wenn weitere Debugginganforderungen erfüllt werden müssen.

## <a name="see-also"></a>Siehe auch
- [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md)
