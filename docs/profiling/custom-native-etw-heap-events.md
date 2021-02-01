---
title: Ereignisse für benutzerdefinierte native ETW-Heap | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie mit einem benutzerdefinierten Heap den Mehraufwand für die Speicherbelegung reduzieren, aber dennoch dem Arbeitsspeicherprofiler Speicherbelegungsinformationen für die Belegungsanalyse zur Verfügung stellen.
ms.custom: SEO-VS-2020
ms.date: 02/24/2017
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- C++
ms.workload:
- cplusplus
ms.openlocfilehash: 61005bf108d0dab16ec419e942e3da97e02cdc7f
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686323"
---
# <a name="custom-native-etw-heap-events"></a>Ereignisse für benutzerdefinierte native ETW-Heaps

Visual Studio enthält eine Vielzahl von [profiling and diagnostic tools (Profilerstellungs- und Diagnosetools)](../profiling/profiling-feature-tour.md), einschließlich einer nativen Speicherprofilerstellung.  Dieser Profiler hängt sich an [ETW-Ereignisse](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) vom Heap-Anbieter, und bietet eine Analyse, wie Speicher zugeordnet und verwendet wird.  Dieses Tool kann standardmäßig nur aus dem standardmäßigen Windows-Heap vorgenommene Zuordnungen analysieren. Zuordnungen außerhalb dieses nativen Heap werden nicht angezeigt.

Es gibt viele Fälle, in denen Sie Ihren eigenen benutzerdefinierten Heap verwenden und den Zuordnungsaufwand aus dem Standard-Heap vermeiden möchten.  Beispielsweise können Sie [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) verwenden, um eine große Menge an Speicher am Anfang der App oder des Spiels zuzuordnen, und anschließend Ihre eigenen Blöcke in dieser Liste zu verwalten.  In diesem Szenario würde das Speicherprofilerstellungstool nur diese anfänglichen Zuordnung und nicht die benutzerdefinierte Verwaltung innerhalb des Speicherblocks finden.  Jedoch können Sie mithilfe des benutzerdefinierten nativen Heap-ETW-Anbieters dafür sorgen,dass das Tool alle Zuordnungen kennt, die Sie außerhalb des Standard-Heaps vornehmen.

In einem Projekt wie dem Folgenden, in dem `MemoryPool` ein benutzerdefinierter Heap ist, würden Sie z.B. nur eine einzige Zuordnung auf dem Windows-Heap sehen:

```cpp
class Foo
{
public:
    int x, y;
};

...

// MemoryPool is a custom managed heap, which allocates 8192 bytes
// on the standard Windows Heap named "Windows NT"
MemoryPool<Foo, 8192> mPool;

// the "allocate" method requests memory from the pool created above
// and is cast to an object of type Foo, shown above
Foo* pFoo1 = (Foo*)mPool.allocate();
Foo* pFoo2 = (Foo*)mPool.allocate();
Foo* pFoo3 = (Foo*)mPool.allocate();
```

Eine Momentaufnahme aus dem [Speicherauslastungstool](../profiling/memory-usage.md) ohne benutzerdefinierte Heap-Nachverfolgung würde nur einfach die einzelne 8.192 Byte-Zuordnung und keine der benutzerdefinierten Zuordnungen, die vom Pool vorgenommen wurden, anzeigen:

![Windows-Heapzuordnung](media/heap-example-windows-heap.png)

Sie können dieses Tool auch zum Nachverfolgen der Speicherauslastung in Ihrem benutzerdefinierten Heap verwenden, indem Sie die folgenden Schritte ausführen.

## <a name="how-to-use"></a>Verwendung

Diese Bibliothek kann problemlos in C und C++ verwendet werden.

1. Fügen Sie den Header für den benutzerdefinierten Heap-ETW-Anbieter ein:

   ```cpp
   #include <VSCustomNativeHeapEtwProvider.h>
   ```

1. Hinzufügen des `__declspec(allocator)`-Decorator für alle Funktionen in Ihrem benutzerdefinierten Heapmanager, das einen Zeiger auf den neu zugeordneten Heapspeicher zurückgibt.  Dieser Decorator ermöglicht es dem Tool, den Typ des zurückgegebenen Speichers korrekt zu identifizieren.  Beispiel:

   ```cpp
   __declspec(allocator) void *MyMalloc(size_t size);
   ```

   > [!NOTE]
   > Dieser Decorator informiert den Compiler, dass diese Funktion ein Aufruf an eine Zuweisung ist.  Jeder Aufruf der Funktion wird die Adresse der Aufrufsite, die Größe der Aufrufanweisung und die TypeId des neuen Objekts zu einem neuen `S_HEAPALLOCSITE`-Symbol ausgeben.  Wenn eine Aufrufliste zugeordnet ist, wird Windows ein ETW-Ereignis mit diesen Informationen ausgeben.  Der Speicherprofilerstellungstool führt die Aufrufliste dazu, eine Rückgabeadresse entsprechend des `S_HEAPALLOCSITE`-Symbols zu suchen. Die TypeId-Informationen im Symbol wird verwendet, um den Laufzeittyp der Zuordnung anzuzeigen.
   >
   > Kurz gesagt bedeutet dies, dass ein Aufruf, der wie `(B*)(A*)MyMalloc(sizeof(B))` aussieht, im Tool als `B`-Typ angezeigt wird, nicht `void` oder `A`.

1. Erstellen Sie für C++ das `VSHeapTracker::CHeapTracker`-Objekt, das einen Namen für den Heap bereitstellt, der im Profilerstellungstool angezeigt werden wird:

   ```cpp
   auto pHeapTracker = std::make_unique<VSHeapTracker::CHeapTracker>("MyCustomHeap");
   ```

   Wenn Sie C verwenden, verwenden Sie stattdessen.die `OpenHeapTracker`-Funktion.  Diese Funktion gibt ein Handle zurück, das Sie verwenden, wenn Sie andere Nachverfolgungsfunktionen aufrufen:

   ```C
   VSHeapTrackerHandle hHeapTracker = OpenHeapTracker("MyHeap");
   ```

1. Rufen Sie beim Zuweisen von Speicher mithilfe der benutzerdefinierte Funktion die `AllocateEvent` (C++)- oder `VSHeapTrackerAllocateEvent` (C)-Methode auf, und übergeben Sie den Zeiger an den Speicher und ihre Größe, um die Zuordnung zu verfolgen:

   ```cpp
   pHeapTracker->AllocateEvent(memPtr, size);
   ```

   oder

   ```C
   VSHeapTrackerAllocateEvent(hHeapTracker, memPtr, size);
   ```

   > [!IMPORTANT]
   > Vergessen Sie nicht, Ihre benutzerdefinierte Zuweisungsfunktion mit dem weiter oben beschriebenen `__declspec(allocator)`-Decorator-Element zu markieren.

1. Rufen Sie beim Freigeben von Speicher mithilfe der benutzerdefinierte Funktion die `DeallocateEvent` (C++)- oder `VSHeapTracerDeallocateEvent` (C)-Funktion auf und übergeben Sie den Zeiger an den Speicher, um die Freigabe zu verfolgen:

   ```cpp
   pHeapTracker->DeallocateEvent(memPtr);
   ```

   oder:

   ```C
   VSHeapTrackerDeallocateEvent(hHeapTracker, memPtr);
   ```

1. Rufen Sie beim Neuzuordnen von Speicher mithilfe der benutzerdefinierte Funktion die `ReallocateEvent` (C++)- oder `VSHeapReallocateEvent` (C)-Methode auf, und übergeben Sie einen Zeiger an den neuen Speicher, an die Größe der Zuordnung und einen Zeiger an den alten Speicher:

   ```cpp
   pHeapTracker->ReallocateEvent(memPtrNew, size, memPtrOld);
   ```

   oder:

   ```C
   VSHeapTrackerReallocateEvent(hHeapTracker, memPtrNew, size, memPtrOld);
   ```

1. Verwenden Sie schlussendlich den `CHeapTracker`-Destruktor, entweder manuell oder über standardmäßige Bereichsregeln, oder die `CloseHeapTracker`-Funktion in C, um die benutzerdefinierte Heap-Nachverfolgung in C++ zu schließen und zu bereinigen:

   ```cpp
   delete pHeapTracker;
   ```

   oder:

   ```C
   CloseHeapTracker(hHeapTracker);
   ```

## <a name="track-memory-usage"></a>Nachverfolgen der Arbeitsspeicherauslastung
Mit diesen Aufrufen kann Ihr benutzerdefinierter Heapverbrauch jetzt mithilfe des Standard-**Speicherauslastungs**-Tools in Visual Studio nachverfolgt werden.  Weitere Informationen zur Verwendung dieses Tools finden Sie unter der [Speicherauslastungs](../profiling/memory-usage.md)-Dokumentation. Stellen Sie sicher, dass Sie die Heap-Profilerstellung mit Momentaufnahmen aktiviert haben, andernfalls wird Ihr benutzerdefinierter Heapverbrauch nicht angezeigt.

![Aktivieren der Heap-Profilerstellung](media/heap-enable-heap.png)

Verwenden Sie zum Anzeigen Ihrer benutzerdefinierten Heap-Nachverfolgung den **Heap**-Dropdown, der sich in der oberen rechten Ecke des **Snapshot**-Fensters befindet, um die Anzeige von *NT-Heap* in Ihren eigenen zuvor genannten Heap zu ändern.

![Heap-Auswahl](media/heap-example-custom-heap.png)

Mithilfe des obigen Codebeispiels, mit `MemoryPool` zum Erstellen eines `VSHeapTracker::CHeapTracker`-Objekts, und unserer eigenen `allocate`-Methode, die nun die `AllocateEvent`-Methode aufruft, können Sie das Ergebnis der benutzerdefinierten Zuordnung sehen, die drei Instanzen mit insgesamt 24 Bytes zeigt, alle sind vom Typ `Foo`.

Das Standardheap *NT-Heap* sieht genauso aus wie vorher, außer dass das `CHeapTracker`-Objekt hinzugefügt wurde.

![NT-Heap mit Tracker](media/heap-example-windows-heap.png)

Wie bei dem standardmäßigen Windows-Heap, können Sie dieses Tool auch verwenden, um Momentaufnahmen zu vergleichen und um nach Verlusten und Beschädigung in Ihrem benutzerdefinierten Heap zu suchen, das in der Hauptdokumentation [Speicherauslastung](../profiling/memory-usage.md) beschrieben wird.

> [!TIP]
> Visual Studio enthält auch ein **Speicherauslastungstool** im **Leistungsprofilerstellungs-Toolset**, das in der Menüoption **Debuggen** > **Leistungsprofilerstellung** oder über die Tastenkombination **ALT**+**F2** aktiviert wird.  Diese Funktion enthält keine Heap-Nachverfolgung und wird Ihren benutzerdefinierten Heap nicht wie hier beschrieben anzeigen.  Nur das **Diagnosetools**-Fenster, das im Menü **Debuggen** > **Windows** > **Diagnosetools anzeigen** oder mit der Tastenkombination **STRG**+**ALT**+**F2** aktiviert werden kann, enthält diese Funktion.

## <a name="see-also"></a>Siehe auch
[Einführung in Profilerstellungstools](../profiling/profiling-feature-tour.md)
[Messen der Speicherauslastung in Visual Studio](../profiling/memory-usage.md)
