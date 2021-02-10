---
title: Vergleichen von Leistungsdatendateien | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie die Ergebnisse aus zwei verschiedenen Profiler-Datendateien (.vsp oder .vsps) vergleichen, um Unterschiede, Leistungsregressionen und Leistungsverbesserungen zu finden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d47f51b5c46538bdeeb50db0627c5bd0840bcc14
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886144"
---
# <a name="how-to-compare-performance-data-files"></a>Vorgehensweise: Vergleichen von Leistungsdatendateien
Sie können die Ergebnisse von zwei unterschiedlichen Profilerdatendateien (.*vsp* oder .*vsps*) vergleichen, indem Sie einen Vergleichsbericht („Diff“) oder eine Ansicht erstellen. Der Vergleich zeigt die Unterschiede, Leistungsabnahmen und -verbesserungen, die von einer Profilerstellungssitzung in die andere aufgetreten sind.

 Der Unterschiedsbericht enthält eine Tabellenansicht der Daten. In der Tabelle wird das Delta bzw. die Abweichung von der Baseline dargestellt. Zur Berechnung wird der Unterschied zwischen dem alten Wert, dem Baselinewert und dem Ergebniswert aus der neuen Analyse ermittelt.

 Vergleiche der Profilerdaten können auf den Funktionen im Code, den Modulen in der Anwendung, Zeilen, Anweisungszeigern (IPs) und Typen basieren.

 Es kann ein Schwellenwert festgelegt werden, um Störungen zu reduzieren und alle Daten in der Tabellenansicht der Zeilen herauszufiltern, bei denen keine Änderung um einen bestimmten Wert feststellbar ist.

### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>So erstellen Sie eine Vergleichsdatei für ein Projekt im Leistungs-Explorer.

1. Wählen Sie im **Leistungs-Explorer** unter **Berichte** die *VSP*- oder *VSPS*-Berichtsdatei aus, die Sie als Baselinewert für den Vergleich verwenden möchten.

2. Wählen Sie die *VSP*- oder *VSPS*-Berichtsdateien aus, die Sie vergleichen möchten.

3. Klicken Sie mit der rechten Maustaste auf ausgewählten Dateien, und wählen Sie **Berichte vergleichen** aus.

### <a name="to-compare-values"></a>So vergleichen Sie Werte

1. Wählen Sie im Fenster „Berichtsansicht“ die Registerkarte **Vergleichsbericht**.

2. Wählen Sie in der Dropdownliste **Tabelle** entweder Funktionen oder Module für den Vergleich.

3. Wählen Sie in der Dropdownliste **Spalte** den Wert aus, den Sie vergleichen möchten.

4. (Optional) Geben Sie einen Wert für **Schwellenwert** ein.

5. Klicken Sie auf **Übernehmen**.

### <a name="to-compare-report-files"></a>So vergleichen Sie Berichtsdateien

1. Klicken Sie im Menü **Analysieren** auf **Leistungsberichte vergleichen**.

2. Durchsuchen Sie das Fenster **Analysedateien für den Vergleich auswählen** und wählen Sie die Analysedatei **Baselinedatei** (jeweils im *VSP*- oder *VSPS*-Format) und die **Vergleichsdatei** (jeweils im *VSP*- oder *VSPS*-Format) aus.

3. Klicken Sie auf **OK**.
