---
title: 'Profilerstellung über die Befehlszeile: Erstellen von Berichten'
description: Hier erfahren Sie, wie Sie mit dem Befehlszeilentool VSPerfReport aus Profilerstellungs-Datendateien Berichte im XML- oder CSV-Format (durch Trennzeichen getrennte Datei) erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 68bb6c863921cdfa87da99d19f85afa8afb8c49b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955930"
---
# <a name="create-profiler-reports-from-the-command-line"></a>Erstellen von Profiler-Berichten über die Befehlszeile
Mit dem Befehlszeilentool **VSPerfReport** können Sie Berichte im *XML*- oder *CSV*-Format aus Profilerstellungsdateien (*VSP*) erstellen. VSPerfReport-Berichtstypen entsprechen in den tabellenbasierten Ansichten der Schnittstelle für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sie können den Bericht filtern, sodass nur Ihr Code und nur ein Teil der Profilerstellungs-Datendatei angezeigt wird. Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).

 Sie können die Freigabe der Profilerstellungs-Datendateien auch vereinfachen, indem Sie Symbole in die *VSP*-Dateien einbetten und bereits analysierte Berichtdateien (*VSPS*) erstellen, die kleiner sind und sich schneller öffnen lassen.

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Verwandte Inhalte|
|----------|---------------------|
|**Erstellen eines einfachen Berichts:** Erstellen Sie alle oder eine Teilmenge der VSPerfReport-Berichtstypen.|-   [Erstellen eines einfachen Berichts](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|
|**Vergleichen von zwei Profilerstellungs-Datendateien:** Erstellen Sie einen Vergleichsbericht, in dem die Leistungsdaten in zwei Profilerstellungs-Datendateien verglichen werden.|-   [Vorgehensweise: Erstellen eines Profiler-Vergleichsberichts über eine Eingabeaufforderung](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|
|**Anzeigen von Daten über Aufrufablaufverfolgung und Ereignisablaufverfolgung für Windows (ETW):** Erstellen Sie einen Aufrufablaufverfolgungsbericht, in dem Zeitsteuerungsinformationen für jeden Einstiegs- und Endpunkt der Funktionen Ihrer Anwendung sowie jeder Aufruf anderer Funktionen durch die Funktion aufgeführt sind. Sie können auch eine ausführliche Auflistung aller ETW-Ereignisse erstellen, die bei einer Profilerstellungsausführung erfasst wurden.|-   [How to: Create a call trace report (Vorgehensweise: Erstellen eines Ablaufverfolgungsberichts für Aufrufe)](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|
|**Filtern eines Berichts:** Filtern Sie einen Bericht auf nur die Funktionen im Code oder auf eine Zeit in der Profilerstellungs-Datendatei.|-   [Vorgehensweise: Filtern von Berichten über die Befehlszeile](../profiling/how-to-filter-reports-from-the-command-line.md)|
|**Erstellen portierbarer Profilerstellungs-Datendateien:** Sie können die Freigabe von Profilerstellungsdaten vereinfachen, indem Sie die Symbole für eine Profilerstellungsausführung in die *VSP*-Datei einbetten. Sie können auch eine bereits analysierte Profilerstellungs-Datendatei (*VSPS*) erstellen, die kleiner ist und sich schneller öffnen lässt.|-   [Erstellen portierbarer Profilerstellungs-Datendateien](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
