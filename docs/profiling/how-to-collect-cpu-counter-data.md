---
title: Sammeln von CPU-Indikatordaten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 96934250bc00b02630b60e83d50ed4b274db0323
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851280"
---
# <a name="how-to-collect-cpu-counter-data"></a>Vorgehensweise: Sammeln von CPU-Indikatordaten

Ein CPU-Ereignisindikator wird zum Sammeln von hardwarespezifischen Leistungsdaten verwendet. In diesem Artikel erfahren Sie, wie Sie Ereignisindikatordaten sammeln, wenn Sie die Instrumentierungsprofilerstellungs-Methode verwenden.

Es treten zwei Typen von CPU-Indikatorereignissen auf:

- Portable Ereignisse: CPU-Ereignisse, die unabhängig des bestimmten CPUs gesammelt werden.

- Plattformereignisse: CPU-Ereignisse, die mit einem bestimmten CPU verbunden sind.

  Portable Ereignisse enthalten allgemeine Ereignisse, z.B. zurückgezogene Anweisungen und nicht angehaltene Zyklen, CPU-Pufferereignisse, verzweigte Ereignisse sowie L2-Cache-Ereignisse. Die verfügbaren Plattformereignisindikatoren werden durch den Hersteller des Prozessors bestimmt.

  Ereigniskategorien können von portablen und Plattfomindikatoren gemeinsam genutzt werden. Die folgenden Datenkategorien gelten z.B. häufig für beide Typen:

- Speicherereignisse

- Front-End-Ereignisse

- Verzweigungsereignisse

  Sie können Leistungsindikatordaten auf zwei Arten im Profiler sammeln:

- Sammeln Sie Daten aus einem oder mehrere Leistungsindikatoren, wenn Sie ein Profil durch Instrumentation erstellen.

- Geben Sie ein Leistungsindikatorereignis als Samplingintervall an, wenn Sie das Profil durch Sampling erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md).

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>So sammeln Sie CPU-Leistungsindikatordaten, wenn Sie ein Profil durch Instrumentation erstellen.

1. Klicken Sie auf der Leistungssitzung **Eigenschaftenseiten** auf **CPU-Indikatoren.**

2. Wählen Sie das Kontrollkästchen **CPU-Indikatoren auflisten** aus.

3. Erweitern Sie die Struktur **Verfügbaren Leistungsindikatoren**, bis Sie die Beispielereignisse finden, die Sie sammeln möchten.

4. Wählen Sie für jedes Ereignis, das Sie erfassen möchten, das Ereignis aus, und klicken Sie dann auf den Pfeil nach rechts, um das Ereignis zur Liste **Ausgewählte Indikatoren** hinzuzufügen.

    > [!NOTE]
    > **Verfügbare Leistungsindikatoren** ist nur aktiviert, wenn Sie das Kontrollkästchen **CPU-Indikatoren auflisten** auswählen.

## <a name="see-also"></a>Siehe auch

[Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
[Eigenschaften von Leistungssitzungen](../profiling/performance-session-properties.md)
[CPU- und Windows-Indikatoren](../profiling/cpu-and-windows-counters.md)
[Vorgehensweise: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md)
