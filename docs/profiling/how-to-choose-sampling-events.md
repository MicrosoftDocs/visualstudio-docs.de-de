---
title: Auswählen von Samplingereignissen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f28859b1c17c735be405c6c56ebabcbe43903170
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851293"
---
# <a name="how-to-choose-sampling-events"></a>Vorgehensweise: Auswählen von Samplingereignissen
Die Profilerstellungstools [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sammeln standardmäßig Leistungsdaten in einem Intervall, das als eine Anzahl von Prozesszyklen angegeben wird, die vom profilierten Prozess verwendet wird. Die Anzahl von Zyklen in einem Intervall beträgt standardmäßig 10.000.000, was ungefähr 0,01 Sekunden auf einem 1-GHz-Computer entpricht. Sie können die Anzahl von Zyklen in einem Intervall sowie das Beispielereignis ändern. Die folgenden Beispielereignisse sind verfügbar:

- Taktzyklen: bei CPU-Problemen

- Seitenfehler: bei Arbeitsspeicherproblemen

- Systemaufrufe: bei E/A-Probleme

- Leistungsindikator – CPU-Indikatoren für Leistungsproblemen auf niedriger Ebene

> [!IMPORTANT]
> Wenn Sie .NET-Speicherdaten mithilfe der Sampling-Methode sammeln (Belegungen, Lebensdauer von Objekten oder beides), werden benutzerspezifische Samplingereignisse ignoriert und Ereignisse zur Speicherbelegung, zur automatischen Speicherbereinigung (oder beide) werden zur Datensammlung verwendet.

### <a name="to-select-a-sample-event"></a>So wählen Sie ein Beispielereignis aus

1. Klicken Sie im **Leistungs-Explorer**mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie in den **Eigenschaftenseiten** auf die Eigenschaften **Sampling**.

3. Wählen Sie aus der Dropdownliste **Beispielereignisse** das Beispielereignis aus, das Sie zur Profilerstellung Ihrer Anwendung verwende möchten.

    > [!NOTE]
    > Die **verfügbaren Leistungsindikatoren** sind nur aktiviert, wenn Sie aus der Dropdown-Liste **Beispielereignis** **Leistungsindikator** auswählen.

4. Wenn Sie **Leistungsindikator** auswählen, klicken Sie vom Strukturansicht-Steuerelement auf **Verfügbare Leistungsindikatoren** auf einen bestimmten CPU-Indikator.

    - Indikatoren aus dem Knoten **Portable Ereignisse** sind für alle Prozessortypen verfügbar.

    - Indikatoren aus dem Knoten **Plattformereignisse** sind spezifische Prozessoren am aktuellen Computer und sind vielleicht für andere Prozessortypen verfügbar.

5. Wenn Sie ein Beispielereignis auswählen, wird ein standardmäßiger Samplingintervallwert im Textfeld **Samplingintervall** angezeigt. Bei Bedarf können Sie den gewünschten Wert in das Textfeld eingeben.

## <a name="see-also"></a>Siehe auch
- [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
- [How to: Auswählen von Collectionmethoden](../profiling/how-to-choose-collection-methods.md)
- [CPU- und Windows-Indikatoren](../profiling/cpu-and-windows-counters.md)
- [Grundlagen zu Samplingdatenwerten](../profiling/understanding-sampling-data-values.md)
- [Profilerstellung über die Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)
