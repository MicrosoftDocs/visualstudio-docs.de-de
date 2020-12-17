---
title: Herausfinden, ob Zeiger eine Speicheradresse beschädigen | Microsoft-Dokumentation
Description: Um zu ermitteln, ob der Zeiger den Arbeitsspeicher beschädigt, können Sie nach Heapbeschädigungen suchen und einen Datenbreakpoint festlegen, um zu ermitteln, wie ein Wert geändert wird.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: 310ec0b881c3b4a299a3d933511e54db0e288ddf
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398363"
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
