---
title: 'Vorgehensweise: Vergleichen von Leistungsdatendateien | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 185494623e019ef666374bd46e52bca0d58738f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185935"
---
# <a name="how-to-compare-performance-data-files"></a>Vorgehensweise: Vergleichen von Leistungsdatendateien
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Ergebnisse von zwei unterschiedlichen Profilerdatendateien (.vsp oder .vsps) vergleichen, indem Sie einen Vergleichsbericht („Diff“) oder eine Ansicht erstellen. Der Vergleich zeigt die Unterschiede, Leistungsabnahmen und -verbesserungen, die von einer Profilerstellungssitzung in die andere aufgetreten sind.  
  
 Der Unterschiedsbericht enthält eine Tabellenansicht der Daten. In der Tabelle wird das Delta bzw. die Abweichung von der Baseline dargestellt. Zur Berechnung wird der Unterschied zwischen dem alten Wert, dem Baselinewert und dem Ergebniswert aus der neuen Analyse ermittelt.  
  
 Vergleiche der Profilerdaten können auf den Funktionen im Code, den Modulen in der Anwendung, Zeilen, Anweisungszeigern (IPs) und Typen basieren.  
  
 Es kann ein Schwellenwert festgelegt werden, um Störungen zu reduzieren und alle Daten in der Tabellenansicht der Zeilen herauszufiltern, bei denen keine Änderung um einen bestimmten Wert feststellbar ist.  
  
### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>So erstellen Sie eine Vergleichsdatei für ein Projekt im Leistungs-Explorer.  
  
1. Wählen Sie in **Leistungs-Explorer**unter **Berichte**die VSP-oder VSPS-Berichtsdatei aus, die Sie als Baselinewerte für den Vergleich verwenden möchten.  
  
2. Wählen Sie die VSP- oder VSPS-Berichtsdateien, die Sie vergleichen möchten.  
  
3. Klicken Sie mit der rechten Maustaste auf ausgewählten Dateien, und wählen Sie **Berichte vergleichen** aus.  
  
### <a name="to-compare-values"></a>So vergleichen Sie Werte  
  
1. Wählen Sie im Fenster „Berichtsansicht“ die Registerkarte **Vergleichsbericht**.  
  
2. Wählen Sie in der Dropdownliste **Tabelle** entweder Funktionen oder Module für den Vergleich.  
  
3. Wählen Sie in der Dropdownliste **Spalte** den Wert aus, den Sie vergleichen möchten.  
  
4. (Optional) Geben Sie einen Wert für **Schwellenwert** ein.  
  
5. Klicken Sie auf **Übernehmen**.  
  
### <a name="to-compare-report-files"></a>So vergleichen Sie Berichtsdateien  
  
1. Klicken Sie im Menü **Analysieren** auf **Leistungsberichte vergleichen**.  
  
2. Suchen Sie im Fenster **Analysedateien für Vergleich auswählen** die **Dateianalyse Datei** (VSP-oder VSPS-Datei) und die **Vergleichs Datei** (VSP-oder VSPS-Datei), und wählen Sie Sie aus.  
  
3. Klicken Sie auf **OK**.
