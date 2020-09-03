---
title: Herausfinden, ob Zeiger eine Speicheradresse beschädigen | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 075569815d55ea30f688c5ce86c56990fca03cd1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350354"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Wie wird festgestellt, ob Zeiger eine Speicheradresse zerstören?
## <a name="problem-description"></a>Problembeschreibung
 Vermutlich wird der Speicher an der Adresse 0x00408000 von einem Zeiger des Programms zerstört. Wie kann festgestellt werden, was dort geschieht?

## <a name="solution"></a>Lösung

#### <a name="check-for-heap-corruption"></a>Überprüfen des Heaps auf Beschädigungen

- Ein Speicherschaden ist eigentlich die Folge einer Heapbeschädigung. Verwenden Sie in diesem Fall das Global Flags-Dienstprogramm (gflags.exe) oder "pageheap.exe". Siehe [/windows-hardware/drivers/debugger/gflags-and-pageheap](/windows-hardware/drivers/debugger/gflags-and-pageheap).

#### <a name="to-find-where-the-memory-address-is-modified"></a>So finden Sie die geänderte Stelle der Speicheradresse

1. Legen Sie einen Datenhaltepunkt bei 0x00408000 fest. Weitere Informationen finden Sie unter [Set a data change breakpoint (native C++ only) (Festlegen eines Haltepunkts für Datenänderungen (nur nativer C++-Code))](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).

2. Zeigen Sie den Speicherinhalt bei Erreichen eines Haltepunkts im Fenster **Speicher** ab Adresse 0x00408000 an. Weitere Informationen finden Sie unter [Arbeitsspeicherfenster](../debugger/memory-windows.md).

## <a name="see-also"></a>Siehe auch
- [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)
