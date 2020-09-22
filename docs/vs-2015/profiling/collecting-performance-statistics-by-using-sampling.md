---
title: Sammeln von Leistungsstatistiken durch Sampling | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
ms.assetid: 8e36361b-bb3d-40c6-b286-0e68c0ecb915
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b84674eafde85528e04157ab213913e57d27e60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841267"
---
# <a name="collecting-performance-statistics-by-using-sampling"></a>Sammeln von Leistungsstatistiken durch Sampling
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Standardmäßig werden mit der Samplingmethode der [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)]-Profilerstellungstools nach jeweils 10.000.000 Prozessorzyklen Profilerstellungsinformationen gesammelt (etwa jede Hundertstelsekunde auf einem 1-GHz-Computer). Die Samplingmethode ist nützlich für das Auffinden von Prozessornutzungsproblemen und ist die vorgeschlagene Methode zum Starten der meisten Leistungsuntersuchungen.  
  
 **Anforderungen**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Zum Angeben der Samplingmethode haben Sie folgende Möglichkeiten:  
  
- Klicken Sie auf der ersten Seite des Profilerstellungs-Assistenten auf **CPU-Sampling (empfohlen)**.  
  
- Klicken Sie in der Symbolleiste **Leistungs-Explorer** in der Liste **Methode** auf **Sampling**.  
  
- Klicken Sie im Eigenschaftendialogfeld der Leistungssitzung auf der Seite **Allgemein** auf **Sampling**.  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
 Sie können zusätzliche Optionen im Dialogfeld _Leistungs Sitzung_**Eigenschaften Seiten** der Leistungs Sitzung angeben. So öffnen Sie dieses Dialogfeld  
  
- Klicken Sie in **Leistungs-Explorer**mit der rechten Maustaste auf den Namen der Leistungs Sitzung, und klicken Sie dann auf **Eigenschaften**.  
  
  Die Aufgaben in der folgenden Tabelle beschreiben Optionen, die Sie im Dialogfeld _Leistungssitzung_**Eigenschaftenseiten** angeben können, wenn Sie ein Profil mithilfe der Samplingmethode erstellen.  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|Fügen Sie auf der Seite **Allgemein** gesammelte Daten zur .NET-Speicherbelegung und Lebensdauer hinzu, und geben Sie Namensdetails für die generierte Profilerstellungs-Datendatei (VSP) an.|-   [Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Vorgehensweise: Dateinamensoptionen für Profilerstellungsdaten](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Ändern Sie auf der Seite **Sampling** die Samplingrate, ändern Sie das Samplingereignis von Prozessortaktzyklen in einen anderen Prozessorleistungsindikator, oder ändern Sie beide Werte.|-   [Gewusst wie: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md)|  
|Wenn sich in der Codeprojektmappe mehrere EXE-Projekte befinden, geben Sie auf der Seite **Starten** die zu startenden Anwendungen sowie die Startreihenfolge an.|-   [Erfassen von Ebeneninteraktionsdaten mit der Visual Studio-IDE](../profiling/collecting-tier-interaction-data.md)|  
|Fügen Sie auf der Seite **Ebeneninteraktionen** ADO.NET-Aufrufinformationen zu den Daten hinzu, die während der Profilerstellung gesammelt wurden.|-   [Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile](../profiling/collecting-tier-interaction-data.md)|  
|Geben Sie auf der Seite **Windows-Ereignisse** ein oder mehrere ETW-Ereignisse (Ereignisse der Ereignisablaufverfolgung für Windows) an, die mit den Samplingdaten erfasst werden sollen.|-   [Gewusst wie: Erfassen von Daten der Ereignis Ablauf Verfolgung für Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Geben Sie auf der Seite **Windows-Indikatoren** einen oder mehrere Betriebssystem-Leistungsindikatoren an, die den Profilerstellungsdaten als Markierungen hinzugefügt werden sollen.|-   [Gewusst wie: Sammeln von Windows-Counter-Daten](../profiling/how-to-collect-windows-counter-data.md)|  
|Geben Sie auf der Seite **Erweitert** die Version der .NET Framework-Laufzeit für die Profilerstellung an, wenn die Anwendungsmodule mehrere Versionen verwenden. Standardmäßig wird die zuerst geladene Version für die Profilerstellung verwendet.|-   [Vorgehensweise: Angeben der .NET Framework Laufzeit](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
