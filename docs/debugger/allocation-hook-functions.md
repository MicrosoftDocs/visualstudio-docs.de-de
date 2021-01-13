---
title: Hookfunktionen für Reservierungen | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Verwendung von Hookfunktionen für Reservierungen, die mit „_CrtSetAllocHook“ installiert werden, wenn Sie CRT-Debugging (C Run-Time, C-Laufzeit) in Visual Studio ausführen müssen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0bea73a044dabce5270c06f68658f85c612574c
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729183"
---
# <a name="allocation-hook-functions"></a>Hookfunktionen für Reservierungen
Eine mithilfe von [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) installierte Hookfunktion für Reservierungen wird jedes Mal aufgerufen, wenn Speicherplatz belegt, erneut belegt oder freigegeben wird. Diese Art von Hook kann für viele verschiedene Zwecke verwendet werden. Sie können damit beispielsweise testen, wie eine Anwendung auf Speichermangel reagiert, Reservierungsmuster überprüfen oder Reservierungsinformationen für die spätere Analyse protokollieren.

> [!NOTE]
> Beachten Sie die Einschränkungen hinsichtlich der Verwendung von C-Laufzeitbibliotheksfunktionen in einer Zuweisungshookfunktion, die unter [Zuweisungshook und Speicherbelegungen von C-Laufzeitbibliotheken](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) beschrieben werden.

 Der Prototyp einer Reservierungshookfunktion sollte etwa wie folgt aussehen:

```cpp
int YourAllocHook(int nAllocType, void *pvData,
        size_t nSize, int nBlockUse, long lRequest,
        const unsigned char * szFileName, int nLine )
```

 Der Zeiger, den Sie an [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) übergeben, ist vom Typ **_CRT_ALLOC_HOOK**, wie in „CRTDBG.H“ definiert:

```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)
    (int, void *, size_t, int, long, const unsigned char *, int);
```

 Wenn die Laufzeitbibliothek die Hookfunktion aufruft, wird durch das *nAllocType*-Argument angegeben, welcher Reservierungsvorgang ausgeführt werden soll ( **_HOOK_ALLOC**, **_HOOK_REALLOC** oder **_HOOK_FREE**). Bei einer Freigabe oder einer erneuten Reservierung enthält `pvData` einen Zeiger auf den Artikelbereich des freizugebenden Blocks. Im Falle einer Reservierung ist dieser Zeiger jedoch NULL, da die Reservierung nicht stattgefunden hat. Die übrigen Argumente enthalten die jeweilige Reservierungsgröße, den Blocktyp, die damit verknüpfte, fortlaufende Anforderungsnummer und ggf. einen Zeiger auf den Dateinamen. Wenn die Argumente verfügbar sind, enthalten sie auch die Zeilennummer, in der die Reservierung vorgenommen wurde. Nachdem die Hookfunktion die vom Autor vorgesehenen Analysen und sonstigen Aufgaben durchgeführt hat, muss sie entweder **TRUE** (der Zuweisungsvorgang kann fortgesetzt werden) oder **FALSE** (der Zuweisungsvorgang kann nicht durchgeführt werden) zurückgeben. Eine einfache Hookfunktion dieses Typs überprüft beispielsweise, wie viel Speicher bisher belegt wurde, und gibt **FALSE** zurück, wenn die Belegung ein geringes Maß überschritten hat. In der Anwendung würden dann diejenigen Reservierungsfehler auftreten, die normalerweise vorkommen, wenn sehr wenig Speicher verfügbar ist. Komplexere Hookfunktionen könnten Reservierungsmuster nachverfolgen, die Speichernutzung analysieren oder beim Auftreten bestimmter Situationen eine Meldung ausgeben.

## <a name="see-also"></a>Siehe auch

- [Reservierungshooks und Speicherreservierungen von C-Laufzeitbibliotheken](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)