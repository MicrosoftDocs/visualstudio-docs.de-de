---
title: Zusammenfassungsansicht | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.summary
helpviewer_keywords:
- performance reports, summary view
- profiling tools reports, Summary view
- profiling tools, Summary view
- Summary view
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4346b0e7459ee3c78669ab9178555370ffac16d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545508"
---
# <a name="summary-view"></a>Zusammenfassungsansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Zusammenfassungsansicht zeigt Informationen über die leistungsintensivsten Funktionen oder Objekte in einem Profilerstellungslauf an. In dieser Ansicht wird anhand der Leistungsmetriken der Profilerstellungsmethode ein Zeitachsendiagramm und mindestens zwei Listen mit den leistungsintensivsten Funktionen oder Objekten dargestellt. Die Daten in dieser Ansicht sind von der verwendeten Profilerstellungsmethode abhängig (Sampling, Instrumentierung oder Parallelität) und davon, ob die .NET-Speicherreservierung erfasst wurde.  
  
 Das Zeitachsendiagramm in der Zusammenfassungsansicht zeigt für alle Zusammenfassungsansichten, außer der der Parallelitätsdaten, die Auslastung des Prozessors (CPU) während der Profilerstellung durch die profilierte Anwendung an.  
  
- Wenn Sie im Diagramm einen Zeitabschnitt angeben, können Sie die Daten für diesen Abschnitt erneut analysieren oder die Zeitachsenanzeige für diesen Abschnitt vergrößern. Weitere Informationen finden Sie unter Gewusst [wie: Filtern von Berichts Ansichten aus der Zusammenfassungs Zeitachse](../profiling/how-to-filter-report-views-from-the-summary-timeline.md) .  
  
- Sie können in einer Zusammenfassungsansichtsliste auf eine Funktion klicken, um die Ansicht „Funktionsdetails“ für die Funktion anzuzeigen. Sie können ebenfalls mit der rechten Maustaste auf die Funktion für andere Ansichtsoptionen klicken.  
  
- Öffnen Sie das Menü **Extras**, zeigen Sie auf **Optionen**, und klicken Sie auf **Leistungstools**, um die Anzahl der Elemente zu verändern, die in der Zusammenfassungsansicht angezeigt werden. Ändern Sie unter **Allgemeine Einstellungen** die Einstellung **Anzahl der Funktionen in der Zusammenfassungsansicht**.  
  
## <a name="notifications-links"></a>Benachrichtigungslinks  
 Sie können auf Links in der Benachrichtigungsliste klicken, um Anzeigeoptionen für den Bericht festzulegen. Sie finden die Liste rechts neben dem Zeitachsendiagramm.  
  
|Option|Beschreibung|  
|-|-|  
|**Show Non-User Code** (Nicht benutzerseitigen Code anzeigen)<br /><br /> **Nur eigenen Code anzeigen**|Nicht verfügbar für nativen Code oder Profilerstellungsdaten, die über die Instrumentierungsmethode erfasst wurden. Schaltet zwischen dem Anzeigen von Daten aus dem Benutzercode (**Nur eigenen Code anzeigen**) und dem Anzeigen von Daten aus dem gesamten Code um, einschließlich des Systemcodes (**Show Non-User Code** (Nicht benutzerseitigen Code anzeigen)). Standardmäßig sind die Daten auf den Benutzercode beschränkt. Informationen zum Ändern der Einstellung finden Sie unter Vorgehens [Weise: Filtern Profilerstellungstools Berichts Ansichten zum Anzeigen nur eigenen Code](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).|  
|**Leitfaden anzeigen**|Zeigt Warnungen für Leistungsregeln im Fenster **Fehlerliste** an. Weitere Informationen finden Sie unter [Verwenden von Leistungsregeln zur Analyse von Daten.](../profiling/using-performance-rules-to-analyze-data.md)|  
  
## <a name="report"></a>Bericht  
 Sie können auf Links in der Berichtsliste klicken, um verschiedene Ansichten zu öffnen und den Bericht zu vergleichen, speichern oder zu filtern. Sie finden die Liste rechts neben dem Zeitachsendiagramm.  
  
|Name|Beschreibung|  
|-|-|  
|**Gekürzte Aufrufstruktur anzeigen**|Zeigt die leistungsintensivsten Ausführungspfade in der Aufrufstrukturansicht an. Weitere Informationen finden Sie unter [View Tree View](../profiling/call-tree-view.md).|  
|**Langsamste Zeile anzeigen**|Nicht verfügbar für Profilerstellungsdaten, die über die Instrumentierungsmethode erfasst wurden. Zeigt die leistungsintensivsten Quellcodezeilen in der Zeilenansicht an. Weitere Informationen finden Sie unter [Zeilen Ansicht](../profiling/lines-view.md).|  
|**Berichte vergleichen**|Zeigt das Dialogfeld **Analysedateien für Vergleich auswählen** an, in dem Sie eine andere Profilerstellungs-Datendatei angeben können, um einen Vergleich mit der aktuellen Datei zu ziehen. Weitere Informationen finden Sie unter [Vergleichen von Leistungsdatendateien](../profiling/comparing-performance-data-files.md).|  
|**Berichtsdaten exportieren**|Zeigt das Dialogfeld **Exportbericht** an, in dem Sie mindestens eine Berichtsansicht angeben können, die als durch Trennzeichen getrennte (CSV) oder XML-Datei gespeichert werden soll. Weitere Informationen finden Sie unter Vorgehens [Weise: Exportieren von Profilerstellungstools-Berichten](https://msdn.microsoft.com/174b5bd3-df9b-4fd4-88d4-76032ab90451).|  
|**Analysierten Bericht speichern**|Speichert die aktuelle Profilerstellungsdatendatei als eine VSPS-Datei, die in der Schnittstelle für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] schneller geöffnet wird. Weitere Informationen finden Sie unter Gewusst [wie: Speichern von analysierten Profilerstellungs-Datendateien](https://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556).|  
|**Berichtsdaten filtern**|Zeigt den Filterbereich des Profilerstellungsberichts an, in dem Sie Kriterien für die Einschränkung der Daten in der Berichtsansicht bestimmen können. Weitere Informationen finden Sie unter [Filter für die Leistungsbericht Ansicht](../profiling/performance-report-view-filter.md) .|  
|**Vollbild umschalten**|Schaltet den Vollbildmodus für die Berichtsansicht ein bzw. aus.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zusammenfassungs Ansicht](../profiling/summary-view-sampling-data.md)   
 [Zusammenfassungs Ansicht](../profiling/summary-view-instrumentation-data.md)   
 [Zusammenfassungs Ansicht](../profiling/summary-view-dotnet-memory-data.md)
