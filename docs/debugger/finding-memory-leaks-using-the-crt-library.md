---
title: Finden von Arbeitsspeicherverlusten mit der CRT-Bibliothek | Microsoft-Dokumentation
description: Hier erfahren Sie, wie der C-/C++-Debugger und die C-Laufzeitbibliothek (C Run-Time, CRT) Ihnen dabei helfen können, Arbeitsspeicherverlust zu erkennen. Zu den verwendeten Methoden gehören Arbeitsspeicherverlust-Berichte und das Vergleichen von Arbeitsspeicher-Momentaufnahmen.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f98bfb3aca5be844018c4c7d9736ab2fa74ebb71
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870674"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>Finden von Arbeitsspeicherverlusten mit der CRT-Bibliothek

Arbeitsspeicherverluste gehören zu den subtilsten und am schwersten zu erkennenden Fehlern in C/C++-Apps. Arbeitsspeicherverluste entstehen dadurch, dass zuvor zugewiesener Arbeitsspeicher nicht ordnungsgemäß freigegeben wird. Ein geringfügiger Arbeitsspeicherverlust wird möglicherweise zunächst nicht bemerkt, aber im Laufe der Zeit kann es zu Symptomen von einer schlechten Leistung bis hin zu Abstürzen kommen, wenn die App nicht mehr über genügend Arbeitsspeicher verfügt. Eine App mit einem Speicherverlust, der den gesamten verfügbaren Arbeitsspeicher betrifft, kann dazu führen, dass andere Apps abstürzen, wodurch Unsicherheit entsteht, welche App für das Problem verantwortlich ist. Selbst harmlose Arbeitsspeicherverluste können auf andere Probleme hindeuten, die korrigiert werden sollten.

Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Debugger und die C-Laufzeitbibliothek (CRT) können Ihnen helfen, Arbeitsspeicherverluste zu erkennen und zu identifizieren.

## <a name="enable-memory-leak-detection"></a>Aktivieren der Arbeitsspeicherverlusterkennung

Die wichtigsten Tools zum Erkennen von Arbeitsspeicherverlusten sind der C/C++-Debugger und die Debugging-Heapfunktionen der C-Laufzeitbibliothek (CRT).

Um alle Debugging-Heapfunktionen zu aktivieren, fügen Sie die folgenden Anweisungen in der hier genannten Reihenfolge in das C++-Programm ein:

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

Durch die `#define` -Anweisung wird eine Basisversion der CRT-Heapfunktionen der entsprechenden Debugversion zugeordnet. Wenn Sie die `#define`-Anweisung weglassen, ist das Speicherabbild des Arbeitsspeicherverlusts [weniger detailliert](#interpret-the-memory-leak-report).

Durch das Einschließen von *crtdbg.h* werden die Funktionen `malloc` und `free` den zugehörigen Debugversionen [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) und [_free_dbg](/cpp/c-runtime-library/reference/free-dbg) zugeordnet, welche die Speicherbelegung und -freigabe nachverfolgen. Diese Zuordnung findet nur in Debugbuilds mit `_DEBUG`statt. Releasebuilds verwenden die normalen Funktionen `malloc` und `free` .

Nachdem Sie die Debugging-Heapfunktionen mithilfe der vorangehenden-Anweisungen aktiviert haben, platzieren Sie einen Aufruf von [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) vor einem Endpunkt der App, sodass beim Beenden der App ein Bericht über Arbeitsspeicherverluste angezeigt wird.

```cpp
_CrtDumpMemoryLeaks();
```

Wenn Ihre App mehrere Endpunkte aufweist, müssen Sie `_CrtDumpMemoryLeaks` nicht manuell an jedem Endpunkt platzieren. Um einen automatischen Aufruf von `_CrtDumpMemoryLeaks` an jedem Endpunkt auszulösen, platzieren Sie am Anfang Ihrer App einen Aufruf von `_CrtSetDbgFlag` mit den hier gezeigten Bitfeldern:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

Standardmäßig gibt `_CrtDumpMemoryLeaks` den Arbeitsspeicherverlust-Bericht im Bereich **Debuggen** des **Ausgabefensters** aus. Bei Verwendung einer Bibliothek wird die Ausgabe u. U. auf einen anderen Ort zurückgesetzt.

Sie können `_CrtSetReportMode` verwenden, um den Bericht an einen anderen Speicherort oder wieder an das Fenster **Ausgabe** umzuleiten – wie hier gezeigt:

```cpp
_CrtSetReportMode( _CRT_WARN, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>Interpretieren des Arbeitsspeicherverlust-Berichts

Wenn `_CRTDBG_MAP_ALLOC` nicht in der App definiert ist, zeigt [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) einen Arbeitsspeicherverlust-Bericht an, der wie folgt aussieht:

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Wenn `_CRTDBG_MAP_ALLOC` in der App definiert ist, sieht der Arbeitsspeicherverlust-Bericht wie folgt aus:

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Der zweite Bericht enthält den Dateinamen und die Zeilennummer, in der der Speicherblock mit dem Arbeitsspeicherverlust zuerst belegt wurde.

Unabhängig davon, ob Sie `_CRTDBG_MAP_ALLOC` definieren oder nicht, sind im Arbeitsspeicherverlust-Bericht folgende Informationen enthalten:

- Die Speicherbelegungsnummer, in diesem Beispiel `18`
- Der Blocktyp, in diesem Beispiel `normal`
- Der hexadezimale Speicherbereich, in diesem Beispiel `0x00780E80`
- Die Größe des Blocks, in diesem Beispiel `64 bytes`
- Die ersten 16 Bytes Daten im Block im Hexadezimalformat

Speicherblocktypen sind *normal*, *Client* oder *CRT*. Ein *normaler Block* ist gewöhnlicher, durch das Programm belegter Speicher. Ein *Clientblock* ist ein spezieller Speicherblocktyp, der von MFC-Programmen für Objekte verwendet wird, die einen Destruktor erfordern. Durch den MFC-Operator `new` wird entsprechend dem zu erstellenden Objekt ein normaler Block oder ein Clientblock erstellt.

Ein *CRT-Block* wird von der CRT-Bibliothek zur eigenen Verwendung belegt. Die CRT-Bibliothek behandelt das Aufheben der Zuordnung für diese Blöcke, sodass CRT-Blöcke nicht im Arbeitsspeicherverlust-Bericht angezeigt werden, es sei denn, es handelt sich um schwerwiegende Probleme mit der CRT-Bibliothek.

Zwei weitere Speicherblocktypen werden nie in Arbeitsspeicherverlust-Berichten angezeigt. Bei einem *freien Block* handelt es sich um Arbeitsspeicher, der freigegeben wurde, sodass es sich definitionsgemäß nicht um einen Verlust handelt. Ein *ignorierter Block* ist ein Speicherblock, der explizit von Ihnen markiert wurde, damit er aus dem Arbeitsspeicherverlust-Bericht ausgeschlossen wird.

Mit den obigen Verfahren werden Speicherverluste für Arbeitsspeicher identifiziert, der mithilfe der CRT-`malloc`-Standardfunktion zugewiesen wurde. Belegt das Programm Speicher mithilfe des C++-Operators `new`, werden im Arbeitsspeicherverlust-Bericht möglicherweise nur der Dateiname und die Zeilennummer angezeigt, wo `operator new` `_malloc_dbg` aufruft. Um einen nützlicheren Arbeitsspeicherverlust-Berichts zu erstellen, können Sie ein Makro wie das folgende schreiben, das die Zeile meldet, die die Belegung vorgenommen hat:

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

Nun können Sie den `new`-Operator ersetzen, indem Sie das `DBG_NEW`-Makro in Ihrem Code verwenden. In Debugbuilds wird von `DBG_NEW` eine Überladung des globalen `operator new` verwendet, die zusätzliche Parameter für den Blocktyp, die Datei und die Zeilennummer nutzt. Die Überladung von `new` ruft `_malloc_dbg` auf, um die zusätzlichen Informationen zu erfassen. In den Arbeitsspeicherverlust-Berichten werden der Dateiname und die Zeilennummer angezeigt, in der die Blöcke mit dem Arbeitsspeicherverlust belegt wurden. Releasebuilds verwenden weiterhin den Standardoperator `new`. Ein Beispiel für dieses Verfahren:

```cpp
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```

Wenn Sie diesen Code im Visual Studio-Debugger ausführen, generiert der Aufruf von `_CrtDumpMemoryLeaks` einen Bericht im Fenster **Ausgabe**, der in etwa wie folgt aussieht:

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

Diese Ausgabe meldet, dass die zu einem Speicherverlust führende Belegung in Zeile 20 der Datei *debug_new.cpp* erfolgte.

>[!NOTE]
>Es wird nicht empfohlen, ein Präprozessormakro mit dem Namen `new` oder einem anderen Programmiersprachen-Schlüsselwort zu erstellen.

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Festlegen von Haltepunkten für eine Speicherbelegungsnummer

Die Speicherbelegungsnummer gibt Aufschluss darüber, wann ein Speicherblock mit Arbeitsspeicherverlust belegt wurde. Ein Block mit der Speicherbelegungsnummer 18 ist z. B. der 18. Speicherblock, der während der Ausführung der App belegt wurde. Im CRT-Bericht werden alle Speicherblockbelegungen während der Ausführung gezählt, einschließlich der Belegungen durch die CRT-Bibliothek und andere Bibliotheken wie MFC. Daher ist Speicherbelegungsblock Nummer 18 wahrscheinlich nicht der 18. Speicherblock, der von Ihrem Code zugewiesen wird.

Sie können die Speicherbelegungsnummer verwenden, um einen Haltepunkt für die Speicherbelegung festzulegen.

**So legen Sie einen Haltepunkt für die Speicherbelegung im Überwachungsfenster fest:**

1. Legen Sie einen Haltepunkt am Anfang der App fest, und starten Sie das Debuggen.

1. Wenn die App am Haltepunkt angehalten wird, öffnen Sie ein Fenster **Überwachung**, indem Sie **Debuggen** > **Fenster** > **Überwachen 1** (bzw. **Überwachen 2**, **Überwachen 3** oder **Überwachen 4**) auswählen.

1. Geben Sie im Fenster **Überwachung** in der Spalte **Name** `_crtBreakAlloc` ein.

   Bei Verwendung der Multithread-DLL-Version der CRT-Bibliothek (/MD-Option) fügen Sie den Kontextoperator hinzu: `{,,ucrtbased.dll}_crtBreakAlloc`
   
   Stellen Sie sicher, dass Debugsymbole geladen sind. Andernfalls wird `_crtBreakAlloc` als *nicht identifiziert* gemeldet.

1. Drücken Sie die **EINGABETASTE**.

   Der Debugger wertet den Aufruf aus und gibt das Ergebnis in der Spalte **Wert** aus. Wenn Sie keine Haltepunkte für Speicherbelegungen festgelegt haben, lautet dieser Wert **–1**.

1. Ersetzen Sie den Wert in der Spalte **Wert** durch die Nummer der Speicherbelegung, bei der die Unterbrechung durch den Debugger erfolgen soll.

Nachdem Sie einen Haltepunkt für eine Speicherbelegungsnummer festgelegt haben, fahren Sie mit dem Debuggen fort. Stellen Sie sicher, dass die Ausführung unter denselben Bedingungen erfolgt, damit sich die Speicherbelegungsnummer nicht ändert. Wenn das Programm bei der angegebenen Speicherbelegung unterbrochen wird, prüfen Sie im Fenster **Aufrufliste** und in anderen Debuggerfenstern, unter welchen Bedingungen der Speicher belegt wurde. Anschließend können Sie die Ausführung fortsetzen, um zu beobachten, was mit dem Objekt geschieht, und festzustellen, warum es nicht ordnungsgemäß freigegeben wird.

Das Festlegen eines Datenhaltepunkts für das Objekt kann auch hilfreich sein. Weitere Informationen finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md).

Sie können auch Speicherbelegungshaltepunkte im Code festlegen. Sie können folgende Einstellungen vornehmen:

```cpp
_crtBreakAlloc = 18;
```

 oder:

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>Vergleichen von Speicherzuständen

Ein weiteres Verfahren zum Ermitteln von Speicherverlusten besteht darin, zu bestimmten Zeitpunkten Momentaufnahmen von Speicherzuständen der Anwendung aufzuzeichnen. Um eine Momentaufnahme des Speicherzustands an einem bestimmten Punkt in der Anwendung aufzuzeichnen, erstellen Sie eine `_CrtMemState`-Struktur, die Sie dann an die `_CrtMemCheckpoint`-Funktion übergeben.

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

Durch die `_CrtMemCheckpoint`-Funktion wird eine Momentaufnahme des aktuellen Speicherzustands in die Struktur eingefügt.

Um den Inhalt einer `_CrtMemState`-Struktur auszugeben, übergeben Sie die Struktur an die `_ CrtMemDumpStatistics`-Funktion:

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics` gibt ein Speicherabbild des Speicherzustands aus, das wie folgt aussieht:

```cmd
0 bytes in 0 Free Blocks.
0 bytes in 0 Normal Blocks.
3071 bytes in 16 CRT Blocks.
0 bytes in 0 Ignore Blocks.
0 bytes in 0 Client Blocks.
Largest number used: 3071 bytes.
Total allocations: 3764 bytes.
```

Um festzustellen, ob in einem Codeabschnitt ein Arbeitsspeicherverlust aufgetreten ist, können Sie Momentaufnahmen des Speicherzustands vor und nach dem Abschnitt erstellen und die beiden Zustände anschließend mithilfe von `_ CrtMemDifference` vergleichen:

```cpp
_CrtMemCheckpoint( &s1 );
// memory allocations take place here
_CrtMemCheckpoint( &s2 );

if ( _CrtMemDifference( &s3, &s1, &s2) )
   _CrtMemDumpStatistics( &s3 );
```

`_CrtMemDifference` vergleicht die Speicherzustände `s1` und `s2` und gibt in (`s3`) ein Ergebnis zurück, das die Differenz zwischen `s1` und `s2` darstellt.

Eine Methode zum Suchen nach Arbeitsspeicherverlusten besteht darin, zunächst `_CrtMemCheckpoint`-Aufrufe am Anfang und Ende der App einzufügen und anschließend mit `_CrtMemDifference` die Ergebnisse zu vergleichen. Wenn `_CrtMemDifference` einen Arbeitsspeicherverlust anzeigt, können Sie weitere `_CrtMemCheckpoint`-Aufrufe hinzufügen, um das Programm anhand einer Binärsuche aufzuteilen, bis Sie die Quelle des Verlusts gefunden haben.

## <a name="false-positives"></a>Falsch positive Ergebnisse

 `_CrtDumpMemoryLeaks` kann falsche Hinweise auf Arbeitsspeicherverluste geben, wenn eine Bibliothek interne Zuordnungen als normale Blöcke statt als CRT-Blöcke oder Client-Blöcke kennzeichnet. In diesem Fall kann `_CrtDumpMemoryLeaks` den Unterschied zwischen Benutzerspeicherbelegungen und internen Bibliotheksspeicherbelegungen nicht erkennen. Wenn die globalen Destruktoren für die Bibliotheksspeicherbelegungen nach dem Punkt ausgeführt werden, an dem `_CrtDumpMemoryLeaks`aufgerufen wird, wird jede interne Bibliotheksspeicherbelegung als Arbeitsspeicherverlust angezeigt. In früheren Versionen der Standardvorlagenbibliothek (vor Visual Studio .NET) werden unter Umständen von `_CrtDumpMemoryLeaks` derartige falsch positive Ergebnisse ausgegeben.

## <a name="see-also"></a>Siehe auch

- [Details zum CRT-Debugheap](../debugger/crt-debug-heap-details.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)
