---
title: Leistungsberichtübersicht | Microsoft-Dokumentation
description: Sie können die Profilerstellungsdaten einer Leistungssitzung im Fenster „Leistungsbericht“ der IDE der Visual Studio Team System Development Edition anzeigen.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, about performance rerports
- performance, reports
- performance reports, about performance reports
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2e775c91759326407918befba3dd4bb52e19dd0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922275"
---
# <a name="performance-report-overview"></a>Leistungsberichtübersicht
Sie können die Profilerstellungsdaten einer Leistungssitzung im Fenster **Leistungsbericht** der integrierten Entwicklungsumgebung (integrated Development Environment (IDE)) der Visual Studio Team System Development Edition anzeigen. Die Profilerstellungsdaten werden in VSP- und VSPS-Dateien gespeichert. In den Anzeigefenstern für Berichte können Sie Leistungsprobleme der Anwendung anzeigen und analysieren.

> [!CAUTION]
> Eine Datei mit Profilerstellungsdaten enthält vertrauliche Informationen, wie z.B. den Computernamen, die Version des Betriebssystems, Dateipfade, Informationen im Arbeitsspeicher und andere Informationen zur Computerinstallation. Sie sollten die genaue Kontrolle über die Verteilung der Daten beibehalten, sowohl im nativen *VSP*-Format als auch beim Export in eine *CSV*- oder *XML*-Datei.
>
> Wenn Ablaufverfolgungsdaten als Teil der Leistungssitzung gesammelt werden, werden möglicherweise zusätzliche Informationen in der Protokolldatei der Ablaufverfolgung (*ETL*-Datei) angezeigt. Diese Informationen umfassen Ihren Domänen- und Benutzernamen; aus diesem Grund sollten Sie die genaue Kontrolle über die Verteilung der Protokolldatei beibehalten.

## <a name="performance-report-window"></a>Leistungsberichtfenster
 Das Leistungsberichtfenster ist ein Toolfenster, die zum Anzeigen, Verwalten und Filtern von Leistungsdaten verwendet wird und ein anpassbares Abfragesteuerelement enthält.

 In der Hauptsymbolleiste des Leistungsberichtfensters können Sie auf jede Ansicht zugreifen. Klicken Sie auf den Pfeil neben der Liste **Aktuelle Ansicht**, um die einzelnen verfügbaren Ansichten anzuzeigen und auszuwählen.

 Das Leistungsberichtfenster bietet die folgenden Datenansichten:

### <a name="summary-view"></a>Zusammenfassungsansicht
 Profilerstellungsdaten werden standardmäßig in der Zusammenfassungsansicht angezeigt. Diese Ansicht ist ein Ausgangspunkt bei Ihrer Überprüfung auf Leistungsprobleme. Von den einzelnen Zeilen in der Zusammenfassungsansicht können Sie zu detaillierteren Ansichten navigieren, indem Sie mit der rechten Maustaste auf die Funktions- oder Modulnamen klicken. Weitere Informationen finden Sie unter [Zusammenfassungsansicht](../profiling/summary-view.md).

### <a name="callercallee-view"></a>Aufrufer-/Aufgerufener-Ansicht
 Die Aufrufer-/Aufgerufener-Ansicht zeigt eine Aufrufstruktur für eine einzelne Funktion. Das Ansicht ist in drei Teile unterteilt:

- Die Zielfunktion wird in der Mitte der Ansicht angezeigt.

- Die Funktionen, die die Funktion (Aufrufer) aufgerufen haben, werden oberhalb der Zielfunktion angezeigt.

- Die Funktionen, die von der Zielfunktion (Aufgerufene) aufgerufen werden, werden unter dem Ziel angezeigt.

  Sie können eine andere Funktion durch Doppelklicken auf eine beliebige Funktion in der Aufrufer-/Aufgerufener-Liste auswählen. Weitere Informationen finden Sie unter [Aufrufer-/Aufgerufener-Ansicht](../profiling/caller-callee-view.md).

### <a name="call-tree-view"></a>Aufrufstrukturansicht
 In der Aufrufstrukturansicht werden die Funktionsausführungspfade angezeigt, die in der mit einem Profil versehenen Anwendung durchlaufen wurden. Der Stamm der Struktur ist der Einstiegspunkt in die Anwendung oder Komponente. Unter den einzelnen Funktionsknoten werden alle Funktionen aufgeführt, die von dieser aufgerufen wurden. Zudem werden Leistungsdaten über diese Funktionsaufrufe angezeigt.

 Die Aufrufstrukturansicht kann erweitert werden und den Ausführungspfad einer Funktion hervorheben, für die die meisten Samplings durchgeführt oder die meiste Zeit verwendet wurde. Um den aktivsten Pfad anzuzeigen, klicken Sie mit der rechten Maustaste auf die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**. Weitere Informationen finden Sie unter [Aufrufstrukturansicht](../profiling/call-tree-view.md).

### <a name="process-view"></a>Prozessansicht
 Die Prozessansicht zeigt Leistungsdaten für die einzelnen Prozesse und Threads an, für die ein Profil erstellt wurde. Weitere Informationen finden Sie unter [Prozessansicht](../profiling/process-view.md).

### <a name="modules-view"></a>Modulansicht
 In der Modulansicht werden die Module im Projekt aufgelistet und Profilerstellungsdaten für jedes Modul angezeigt. Erweitern oder reduzieren Sie den Modulnamen, um die Profilerstellungsdaten der Funktion anzuzeigen. Wenn die Daten mithilfe der Samplingmethode erfasst wurden, sind darüber hinaus Profilerstellungsdaten zur Quellcodezeile und zum Anweisungszeiger verfügbar. Weitere Informationen finden Sie unter [Modulansicht](../profiling/modules-view.md).

### <a name="functions-view"></a>Funktionsansicht
 Die Funktionsansicht listet die Funktionen auf, die während der Profilerstellung aufgerufen wurden. Weitere Informationen finden Sie unter [Funktionsansicht](../profiling/functions-view.md).

### <a name="line-view"></a>Zeilenansicht
 In der Zeilenansicht werden die bestimmten Quellcodezeilen angezeigt, die während der Sampling-Profilerstellung ausgeführt wurden. Weitere Informationen finden Sie unter [Zeilenansicht](../profiling/lines-view.md).

### <a name="instruction-pointer-ip-view"></a>Anweisungszeigeransicht (IPs)
 In der Ansicht des Anweisungszeiger werden die bestimmten Anweisungen angezeigt, die während der Sampling-Profilerstellung ausgeführt wurden. Weitere Informationen finden Sie unter [Anweisungszeigeransicht (IPs)](../profiling/instruction-pointers-ips-view.md).

### <a name="allocation-view"></a>Zuordnungsansicht
 Die Zuordnungsansicht ist verfügbar, wenn **.NET-Objektzuordnung sammeln** auf der Seite **Allgemein** im Eigenschaftendialogfeld **Leistungssitzung** ausgewählt wurde. Informationen hierzu finden Sie unter [Übersicht über Leistungssitzungen](../profiling/performance-session-overview.md). Die Zuordnungsansicht listet die .NET-Objekte auf, die von der Anwendung oder Komponente zugeordnet wurden. Wenn eine Objektzeile erweitert wird, wird eine Aufrufstruktur angezeigt. Die Aufrufstruktur zeigt die Ausführungspfade, die zur Erstellung des Objekts geführt haben. Informationen werden auch über die Anzahl der inklusiven und exklusiven Zuordnungen für jede Funktion in der Aufrufstruktur angezeigt. Die Zuordnungsansicht kann den Ausführungspfad einer Funktion, die die größte Anzahl an Objekten zugeordnet hat, auch erweitern und hervorheben. Um den aktivsten Pfad anzuzeigen, klicken Sie mit der rechten Maustaste auf die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**. Weitere Informationen finden Sie unter [Sammeln von Daten zur .NET-Speicherbelegung und -lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) und [Zuordnungsansicht](../profiling/dotnet-memory-allocations-view.md).

### <a name="objects-lifetime-view"></a>Objektlebensdaueransicht
 Die Objektlebensdaueransicht ist verfügbar, wenn **.NET Objekt-Zuordnungsinformationen auflisten** und **Lebensdauerinformationen für .NET-Objekte auflisten** auf der Seite **Allgemein** des Eigenschaftendialogfelds **Leistungssitzung** ausgewählt wurden.

 Die Objektlebensdaueransicht zeigt die Gesamtanzahl der Instanzen der einzelnen Typen und die Anzahl der Objekte, die in jeder Erstellung der Garbage Collection gesammelt wurden. Weitere Informationen finden Sie unter [Objektlebensdaueransicht](../profiling/object-lifetime-view.md).

## <a name="customizable-filter-control"></a>Anpassbares Filtersteuerelement
 Das anpassbare Filtersteuerelement verfügt über die folgenden Optionen:

- **Filter importieren**: ruft eine zuvor gespeicherte benutzerdefinierte Abfrage ab.

- **Filter exportieren**: speichert die benutzerdefinierte Abfrage am angegebenen Speicherort.

- **Abfrage durchführen**: führt die Abfrage durch, wie im benutzerdefinierten Abfragesteuerelement angezeigt.

- **Abfrage beenden**: beendet die Ausführung einer Abfrage, die ausgeführt wird. Diese Schaltfläche ist nicht verfügbar, wenn keine Abfrage ausgeführt wird.

- **Abfrage anzeigen**: blendet das benutzerdefinierte Steuerelement ein/aus.

- **Analysierte Daten speichern**: speichert den Bericht zusammen mit der aktuellen Analyse als VSPS-Datei.

- **Exportieren**: speichert den aktuellen Bericht im CVS-Format oder als XML-formatierte Datei mit Optionen, die verschiedenen Ansichten zu speichern.

## <a name="see-also"></a>Siehe auch
- [Analysieren der durch Leistungstools erstellten Daten](../profiling/analyzing-performance-tools-data.md)
- [Leistungsberichtansichten](../profiling/performance-report-views.md)
