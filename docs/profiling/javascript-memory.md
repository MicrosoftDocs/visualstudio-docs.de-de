---
title: Analysieren von JavaScript-Speicherauslastung in UWP-Apps | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie die JavaScript-Speicheranalyse in Visual Studio Ihnen dabei helfen kann, die Speicherauslastung zu verstehen und Arbeitsspeicherverluste in UWP-Apps zu finden, die mit JavaScript für Windows erstellt wurden.
ms.custom: ''
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- JavaScript
helpviewer_keywords:
- dominators, memory analyzer (JavaScript)
- memory leaks (JavaScript)
- heap memory, JavaScript
- leaks, memory (JavaScript)
- snapshots, memory analyzer (JavaScript)
- JavaScript Memory Analyzer
- analyzing memory, JavaScript
- memory analyzer, JavaScript
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a29d12a4ca2e6a7a620c5197f76c0ad35ac33a40
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721683"
---
# <a name="analyze-javascript-memory-usage-in-uwp-apps"></a>Analysieren der JavaScript-Arbeitsspeicherauslastung in UWP-Apps
Die JavaScript-Speicheranalyse ist in Visual Studio verfügbar und soll Ihnen dabei helfen, die Speicherauslastung zu verstehen und Speicherverluste in UWP-Apps zu finden, die mit JavaScript für Windows erstellt wurden. Zu den unterstützten Apps zählen Apps für universelle Windows-Apps.

 Der JavaScript-Arbeitsspeicheranalyse bietet folgende Möglichkeiten:

- Unterstützung bei der Suche nach Problemen mit der Speicherauslastung in der App, indem die wichtigsten Daten hervorgehoben werden.

     Sie erhalten diese Daten als Momentaufnahmen-Zusammenfassung, bei denen die Unterschiede zwischen zwei Momentaufnahmen dargestellt und Links zu detaillierteren Ansichten bereitgestellt werden.

- Bereitstellen von Ansichten von Dominatoren, Typen und Stämmen, um Unterstützung bei der Problemisolierung zu bieten.

- Verringerung nicht ausführbarer Informationen in den JavaScript-Heapdaten.

     Automatische Filterung von Objekten, die nicht direkt im App-Code erstellt werden. Sie können Daten auch nach Objektnamen filtern.

## <a name="run-the-javascript-memory-analyzer"></a>Ausführen der JavaScript-Speicheranalyse
 Sie können das Speicheranalysetool mit einer in Visual Studio geöffneten, funktionierenden UWP-App verwenden.

#### <a name="to-run-the-memory-analyzer"></a>So führen Sie die Speicheranalyse aus

1. Öffnen Sie Visual Studio.

2. Wenn Sie die App aus Visual Studio heraus ausführen, klicken Sie auf der Symbolleiste **Standard** in der Liste **Debugging starten** auf ein Debugziel für Ihr Projekt: entweder **Lokaler Computer** oder **Gerät**.

3. Klicken Sie auf der Menüleiste auf **Debuggen** > **Leistungsprofiler**.

     Standardmäßig wird das aktuelle Startprojekt analysiert. Wenn Sie das Analyseziel ändern möchten, wählen Sie **Ziel ändern** aus.

     ![Analyseziel ändern](../profiling/media/js_tools_target.png "JS_Tools_Target")

     Folgende Optionen sind für das Analyseziel verfügbar:

    - **Startprojekt**. Analysiert das aktuelle Startprojekt. Wenn Sie die Anwendung auf einem Remotecomputer ausführen, müssen Sie diese Option aktivieren. Dies ist die Standardauswahl.

    - **Ausgeführte App**. Ermöglicht die Auswahl einer UWP-App aus einer Liste ausgeführter Apps. Diese Option können Sie nicht verwenden, wenn Sie die App auf einem Remotecomputer ausführen.

         Verwenden Sie diese Option zum Analysieren der Speicherauslastung von auf Ihrem Computer ausgeführten Apps, wenn Sie keinen Zugriff auf den Quellcode haben.

    - **Installierte App**. Ermöglicht die Auswahl einer installierten UWP-App, die analysiert werden soll. Diese Option können Sie nicht verwenden, wenn Sie die App auf einem Remotecomputer ausführen.

         Verwenden Sie diese Option zum Analysieren der Speicherauslastung von auf Ihrem Computer installierten Apps, wenn Sie keinen Zugriff auf den Quellcode haben. Diese Option kann auch nützlich sein, um die Speicherauslastung einer App außerhalb der eigenen App-Entwicklung zu analysieren.

4. Aktivieren Sie unter **Verfügbare Tools** das Kontrollkästchen **JavaScript-Memory** , und wählen Sie dann **Start** aus.

5. Wenn Sie die Speicheranalyse starten, werden Sie im Fenster "Benutzerkontensteuerung" eventuell aufgefordert, die Berechtigung zur Ausführung von Visual Studio ETW Collector.exe anzugeben. Klicken Sie auf **Ja**.

     Interagieren Sie mit der App, um die relevanten Speicherauslastungsszenarien zu testen und das Arbeitsspeicherdiagramm anzuzeigen, wie in den folgenden Abschnitten erläutert.

6. Wechseln Sie mittels der Tastenkombination **ALT**+**TAB** zu Visual Studio.

7. Um von der Arbeitsspeicheranalyse erfasste Daten anzuzeigen, wählen Sie **Heap-Momentaufnahme erstellen** aus. Siehe [View a snapshot summary](#view-a-snapshot-summary) weiter unten in diesem Thema.

## <a name="check-memory-usage"></a>Überprüfen der Speicherauslastung
 Sie können versuchen, Speicherverluste zu identifizieren, indem Sie unterschiedliche Ansichten in der JavaScript-Arbeitsspeicheranalyse verwenden. Wenn Sie bereits Speicherverlust bei der App vermuten, finden Sie unter [Isolate a memory leak](#isolate-a-memory-leak) einen vorgeschlagenen Workflow.

 Verwenden Sie die folgenden Ansichten, um Speicherverluste in einer App zu identifizieren:

- [Anzeigen der Zusammenfassung der Live-Speicherauslastung](#view-live-memory-usage-summary). Verwenden Sie das Speicherauslastungsdiagramm, um nach abrupten Zunahmen bei der Speicherauslastung oder bei sich kontinuierlich erhöhender Speicherauslastung zu suchen, die durch bestimmte Aktionen entsteht. Verwenden Sie die Zusammenfassungsansicht der Speicherauslastung in Liveansicht, um Momentaufnahmen des Heaps zu erstellen. Die Momentaufnahmen werden als Auflistung unter dem Speicherauslastungsdiagramm angezeigt.

    > [!TIP]
    > Sie erkennen eine Spitze in der Speicherauslastung, wenn Sie eine Momentaufnahme erstellen. Verwenden Sie die Momentaufnahmezusammenfassungen, um Genaueres über die Zunahme zu erfahren.

- [View a snapshot summary](#view-a-snapshot-summary). Sie können Kurzinformationen der Momentaufnahmen während oder nach einer Sitzung zur Arbeitsspeicherprofilerstellung anzeigen. Verwenden Sie die Zusammenfassungen der Momentaufnahmen, um zu den Ansichten der Momentaufnahmedetails und des Momentaufnahmevergleichs zu verknüpfen.

    > [!TIP]
    > In der Regel bieten die Ansichten des Momentaufnahmevergleichs die nützlichsten Informationen zu Speicherverlusten.

- [Anzeigen von Momentaufnahmedetails](#view-snapshot-details). Sie zeigt detaillierte Speicherauslastungsdaten für eine einzelne Momentaufnahme.

- [Anzeigen eines Momentaufnahmevergleichs](#view-a-snapshot-diff). Es werden differenzielle Werte zwischen Momentaufnahmen angezeigt. Diese Ansichten zeigen Unterschiede in der Objektgröße und -anzahl an.

## <a name="isolate-a-memory-leak"></a>Isolate a memory leak
 In den folgenden Schritten wird ein Workflow vorgeschlagen, mit dem Sie die JavaScript-Speicheranalyse effektiver verwenden können. Diese Schritte können hilfreich sein, wenn Sie Speicherverlust bei der App vermuten. Ein Tutorial, das Sie durch den Prozess zum Identifizieren eines Speicherverlusts in einer funktionierenden App führt, finden Sie unter [Exemplarische Vorgehensweise: Suchen eines Speicherverlusts (JavaScript)](javascript-memory.md).

1. Öffnen Sie die App in Visual Studio.

2. Führen Sie die JavaScript-Speicheranalyse aus (siehe vorherige Schritte)

3. Führen Sie Ihre App für das Szenario aus, das Sie testen möchten. Dies kann z. B. eine große DOM-Veränderung sein, wenn eine bestimmte Seite geladen oder die App gestartet wird.

4. Wiederholen Sie das Szenario noch ein- bis viermal.

   > [!TIP]
   > Indem Sie das Testszenario mehrmals wiederholen, können Sie sicherstellen, dass die Initialisierungsarbeit aus den Ergebnissen herausgefiltert werden kann.

5. Wechseln Sie zu Visual Studio (drücken Sie **ALT**+**TAB**).

6. Nehmen Sie eine Momentaufnahme des Baselineheaps auf, indem Sie **Heap-Momentaufnahme erstellen** auswählen.

    In der folgenden Abbildung ist ein Beispiel für eine Momentaufnahme eines Baselineheaps dargestellt:

    ![Momentaufnahme der Baseline](../profiling/media/js_mem_leak_workflow_baseline.png "JS_Mem_Leak_Workflow_Baseline")

   > [!TIP]
   > Zur genaueren zeitlichen Steuerung bei Momentaufnahmen verwenden Sie den Befehl [Associate source code with memory usage data](#associate-source-code-with-memory-usage-data) im Code.

7. Wechseln Sie zu Ihrer App, und wiederholen Sie das Szenario, das Sie testen (nur einmal).

8. Wechseln Sie zu Visual Studio, und nehmen Sie eine zweite Momentaufnahme auf.

9. Wechseln Sie zu Ihrer App, und wiederholen Sie das Szenario, das Sie testen (nur einmal).

10. Wechseln Sie zu Visual Studio, und nehmen Sie eine dritte Momentaufnahme auf.

     In der folgenden Abbildung wird ein Beispiel einer zweiten und dritten Momentaufnahme dargestellt.

     ![Zweite und dritte Momentaufnahme](../profiling/media/js_mem_leak_workflow.png "JS_Mem_Leak_Workflow")

     Indem Sie in diesem Workflow eine grundlegende Momentaufnahme und dann eine zweite und dritte Momentaufnahme machen, können Sie die Änderungen einfacher herausfiltern, die nichts mit Speicherverlusten zu tun haben. Es gibt z. B. möglicherweise erwartete Änderungen, wie das Aktualisieren von Kopf- und Fußzeilen auf einer Seite, die zu einige Änderungen bei der Speicherauslastung führen, aber nicht mit Speicherverlusten zusammenhängen.

11. Wählen Sie in der dritten Momentaufnahme einen Link zu einer der Differenzansichten:

    - Differenzielle Heapgröße (Link links unter der Heapgröße). Der Linktext gibt die Differenz zwischen der Heapgröße der aktuellen Momentaufnahme und der Heapgröße der vorherigen Momentaufnahme an.

    - Differenzielle Objektanzahl (Link rechts unter der Objektanzahl). Der Linktext zeigt zwei Werte an (z. B. + 1858 / -1765): Der erste Wert ist die Anzahl neuer Objekte, die seit der vorherigen Momentaufnahme hinzugefügt wurden. Der zweite Wert ist die Anzahl der Objekte, die seit der vorherigen Momentaufnahme entfernt wurden.

      Über diese Links wird eine Detailansicht der Differenzen zwischen den Momentaufnahmen für die Heaptypen geöffnet, die entweder nach beibehaltener Größe oder nach Objektanzahl sortiert ist, abhängig davon, auf welchen Link Sie geklickt haben.

12. Wählen Sie eine der folgenden Filteroptionen für den **Bereich** , damit Sie Probleme bei der Speichernutzung einfacher finden können:

    - **Übrige Objekte der Momentaufnahme #2**.

    - **Objekte zwischen Momentaufnahme #2 und #3 eingefügt**

    > [!TIP]
    > Verwenden Sie die gefilterte Ansicht der Objekte, die von der vorherigen Momentaufnahme übrig sind, um Speicherverluste genauer zu untersuchen. Wenn die differenzielle Objektanzahl zum Beispiel +205/-195 beträgt, zeigt diese Ansicht die zehn übrig gebliebenen Objekte an, die wahrscheinlich für die Speicherverluste verantwortlich sind.

     Die folgende Abbildung zeigt eine Differenzansicht der Objekte, die aus der Momentaufnahme 2 übrig geblieben sind.

     ![Momentaufnahme einer Differenzansicht, einschließlich Typen](../profiling/media/js_mem_snapshot_diff.png "JS_Mem_Snapshot_Diff")

     In der vorhergehenden Abbildung können wir sehen, dass aus der vorherigen Momentaufnahme zwei Objekte übrig geblieben sind. Untersuchen Sie, ob es sich hierbei um ein erwartetes Verhalten dieser speziellen App handelt. Wenn nicht, kann dies auf einen Speicherverlusts hinweisen.

13. Um zu sehen, woher Objekte in den Vergleichsansichten im globalen Objekt, das die Durchführung einer Garbage Collection verhindert, entstammen, öffnen Sie das Kontextmenü für ein Objekt, und wählen Sie dann **In Stammansicht anzeigen** aus. Es kann sein, dass eine große Anzahl von Objekten im Speicher beibehalten wird, da sie von einem einzelnen Objekt bzw. einigen wenigen Objekten referenziert werden, die dem globalen Objekt als Stamm zugewiesen sind.

14. Wenn in der Ansicht der übrig gebliebenen Objekte zu viele Objekte angezeigt werden, versuchen Sie, den Zeitraum noch genauer einzugrenzen, in dem der Speicherverlust auftritt. Erstellen Sie anschließend die drei Momentaufnahmen noch einmal. Um den Speicherverlust weiter zu isolieren, verwenden Sie [Associate source code with memory usage data](#associate-source-code-with-memory-usage-data), [Associate source code with memory usage data](#associate-source-code-with-memory-usage-data)und andere Daten zur Speicherauslastung, die in der Arbeitsspeicheranalyse verfügbar sind.

## <a name="view-live-memory-usage-summary"></a>Anzeigen der Zusammenfassung der Live-Speicherauslastung
 Die Zusammenfassungsansicht der Live-Speicherauslastung stellt ein Speicherauslastungsdiagramm für die ausgeführte App und eine Auflistung aller Kacheln der Momentaufnahmen-Zusammenfassung bereit. In dieser Ansicht können Sie grundlegende Aufgaben ausführen, wie das Erstellen von Momentaufnahmen, die Analyse von Informationen der Zusammenfassung und das Navigieren zu anderen Ansichten. Wenn Sie die Datenerfassung beendet haben, verschwindet das Arbeitsspeicherdiagramm, und Sie sehen nur die Ansicht der [View a snapshot summary](#view-a-snapshot-summary) .

 Das Arbeitsspeicherdiagramm zeigt eine aktive Ansicht des Prozessarbeitsspeichers der App, die private Bytes, systemeigenen Speicher und den JavaScript-Heap umfasst. Das Arbeitsspeicherdiagramm ist eine bildlauffähige Ansicht des Prozessspeichers. Hier sehen Sie, wie es aussieht:

 ![Arbeitsspeicherdiagramm für den JavaScript-Speicheranalyzer](../profiling/media/js_mem_memory_graph.png "JS_Mem_Memory_Graph")

 Wenn Sie Ihrem Code Benutzermarkierungen hinzugefügt haben (siehe [Associate source code with memory usage data](#associate-source-code-with-memory-usage-data)), wird ein umgekehrtes Dreieck im Speicherauslastungsdiagramm angezeigt, um anzugeben, wann dieser Codeabschnitt erreicht ist.

 Ein Teil des im Arbeitsspeicherdiagramm dargestellten Arbeitsspeichers wird von der JavaScript-Laufzeit zugeordnet. Sie können diese Speicherauslastung in der App nicht steuern. Die im Diagramm dargestellte Speicherauslastung erhöht sich bei Erstellen der ersten Momentaufnahme und erhöht sich geringfügig bei jeder weiteren Momentaufnahme.

## <a name="view-a-snapshot-summary"></a>View a snapshot summary
 Um eine Momentaufnahme des aktuellen Zustands der Speicherauslastung der App zu erstellen, wählen Sie im Arbeitsspeicherdiagramm **Heap-Momentaufnahme erstellen** aus. Eine Kachel zur Momentaufnahmen-Zusammenfassung wird in der Zusammenfassung der Live-Speicherauslastung (bei laufender App) und in der Momentaufnahmenzusammenfassung (bei beendeter App) angezeigt und enthält Informationen zum JavaScript-Heap sowie Links zu ausführlicheren Informationen. Bei mindestens zwei erstellten Momentaufnahmen stellt eine Momentaufnahme zusätzliche Informationen zum Vergleich der aktuellen Daten mit denen der vorherigen Momentaufnahme bereit.

> [!NOTE]
> Die JavaScript-Arbeitsspeicheranalyse erzwingt vor jeder Momentaufnahme die Durchführung einer Garbage Collection. Damit werden konsistentere Ergebnisse zwischen den Ausführungen sichergestellt.

 Im Folgenden finden Sie ein Beispiel einer Momentaufnahmenzusammenfassung bei Erstellung mehrerer Momentaufnahmen.

 ![Momentaufnahmezusammenfassung](../profiling/media/js_mem_snapshot_summary.png "JS_Mem_Snapshot_Summary")

 Die Momentaufnahmenzusammenfassung enthält:

- Titel der Momentaufnahme und Zeitstempel

- Anzahl der potenziellen Probleme (gekennzeichnet durch ein blaues Informationssymbol). Diese Zahl, sofern vorhanden, identifiziert alle potenziellen Arbeitsspeicherprobleme, wie z. B. Knoten, die nicht am DOM angefügt sind. Die Zahl ist mit der Typenansicht der Momentaufnahme verknüpft. Diese ist nach Problemtyp sortiert, um die potenziellen Probleme hervorzuheben. Es wird eine QuickInfo mit einer Beschreibung des Problems angezeigt.

- Heapgröße. Diese Zahl umfasst DOM-Elemente und Objekte, die dem JavaScript-Heap von der JavaScript-Runtime-Engine hinzugefügt werden. Die Heapgröße ist mit der Typenansicht der Momentaufnahme verknüpft.

- Differenzielle Heapgröße. Dieser Wert stellt den Unterschied zwischen der Heapgröße der aktuellen Momentaufnahme und der Heapgröße der vorherigen Momentaufnahme dar. Hinter dem Wert sehen Sie einen roten Pfeil nach oben, falls der Arbeitsspeicher angestiegen ist, bzw. einen grünen Pfeil nach unten, wenn der Arbeitsspeicher gesunken ist. Wenn die Heapgröße sich zwischen den Momentaufnahmen nicht geändert hat, wird der Text **Keine Änderung** anstelle einer Zahl angezeigt. Für die erste Momentaufnahme sehen Sie den Text **Basislinie**. Die differenzielle Heapgröße ist mit der Ansicht "Typen" des Momentaufnahmevergleichs verknüpft.

- Objektanzahl. Diese Zahl gibt nur die in der App erstellten Objekte an. Integrierte, von der JavaScript-Laufzeit erstellte Objekte werden herausgefiltert. Die Objektanzahl ist ein Link zur Typansicht der Momentaufnahmedetails.

- Differenzielle Objektanzahl. Hier werden zwei Werte angezeigt: Der erste Wert ist die Anzahl neuer Objekte, die seit der vorherigen Momentaufnahme hinzugefügt wurden. Der zweite Wert ist die Anzahl der Objekte, die seit der vorherigen Momentaufnahme entfernt wurden. Die Abbildung zeigt zum Beispiel, dass 1.859 Objekte hinzugefügt wurden und 1.733 Objekte seit Momentaufnahme Nr. 1 entfernt wurden. Hinter dieser Information sehen Sie einen roten Pfeil nach oben, falls die Objektgesamtanzahl angestiegen ist, bzw. einen grünen Pfeil nach unten, wenn sie gesunken ist. Wenn sich die Objektanzahl nicht geändert hat, wird der Text **Keine Änderung** anstelle einer Zahl angezeigt. Für die erste Momentaufnahme sehen Sie den Text **Basislinie**. Die differenzielle Objektanzahl ist mit der Ansicht "Typen" des Momentaufnahmenvergleichs verknüpft.

- Screenshot des Bildschirms zum Zeitpunkt der Momentaufnahme.

## <a name="view-snapshot-details"></a>Anzeigen von Momentaufnahmedetails
 Sie können ausführliche Informationen zur Speicherauslastung für jede Momentaufnahme in den Ansichten "Momentaufnahmedetails" anzeigen.

 Wählen Sie in der Ansicht der Momentaufnahme-Zusammenfassung einen Link aus, um die Momentaufnahmedetails anzuzeigen. Beispielsweise werden durch Klicken auf den Link der Heapgröße standardmäßig die Momentaufnahmedetails mit der Typenansicht angezeigt.

 Diese Abbildung zeigt die Typenansicht in einem Momentaufnahmedetail, wobei die Speicherauslastungsdaten nach beibehaltener Größe sortiert sind.

 ![Momentaufnahmedetails, einschließlich potenzieller Probleme](../profiling/media/js_mem_snapshot_details.png "JS_Mem_Snapshot_Details")

 In der Ansicht der Momentaufnahmedetails können Sie Daten zur Speicherauslastung nach Typ, Stamm oder Dominator überprüfen, indem Sie eine Option aus der Symbolleiste auswählen:

- **Typen** Zeigt die Instanzenanzahl und die Gesamtgröße der Objekte im Heap, gruppiert nach Objekttyp. Standardmäßig werden diese nach Instanzenanzahl sortiert.

  > [!TIP]
  > In der Regel sind die Differenzansichten der Typen im Objektheap am nützlichsten, um einen Speicherverlust zu identifizieren. Diese Ansichten verfügen über einen **Bereichsfilter** , mit dem übrig gebliebene Objekte ermittelt werden können.

- **Stammelemente**. Zeigt eine hierarchische Ansicht von Objekten von den Stammobjekten bis zu den untergeordneten Verweisen an. Standardmäßig werden die untergeordneten Knoten nach der Spalte "Beibehaltene Größe" sortiert, beginnend mit dem größten Knoten.

- **Dominatoren** Zeigt eine Liste von Objekten im Heap an, die exklusive Verweise auf andere Objekte haben. Dominatoren werden nach beibehaltener Größe sortiert.

  > [!TIP]
  > Wenn Sie einen Dominator aus dem Arbeitsspeicher entfernen, geben Sie den gesamten Speicherplatz frei, den das Objekt besetzt. Bei einigen Apps kann die Dominatorenansicht dabei helfen, die Größe von beibehaltenem Speicher zu ermitteln, da Sie hiermit die vollständige Objektbezugskette untersuchen können.

  Alle drei Ansichten zeigen ähnliche Werttypen an, darunter:

- **Bezeichner** Der Name, der das Objekt am besten identifiziert. Zum Beispiel zeigen bei HTML-Elementen die Momentaufnahmendetails den ID-Attributwert an, sofern einer verwendet wird.

- **Typ**. Objekttyp (z. B. HTML-Linkelement oder div-Element).

- **Größe** Größe des Objekts, ohne die Größe aller referenzierten Objekte.

- **Beibehaltene Größe**. Objektgröße plus die Größe aller untergeordneten Objekte, die über keine weiteren übergeordneten Objekte verfügen. Aus praktischen Gründen handelt es sich bei dieser Summe um die Menge an Arbeitsspeicher, die vom Objekt beibehalten wird, sodass dieser Arbeitsspeicher wieder freigegeben wird, sobald Sie das Objekt löschen.

- **Anzahl** Zahl Objektinstanzen. Dieser Wert wird nur in der Typansicht angezeigt.

## <a name="view-a-snapshot-diff"></a>Anzeigen eines Momentaufnahmevergleichs
 In der JavaScript-Speicheranalyse können Sie in den Ansichten "Momentaufnahmevergleich" eine Momentaufnahme mit einer vorherigen vergleichen.

 In der Ansicht der Momentaufnahmezusammenfassung können Sie die differenziellen Momentaufnahmedetails anzeigen, indem Sie die differenzielle Heapgröße oder die Links der differenziellen Objektanzahl auswählen, nachdem mindestens zwei Momentaufnahmen ausgeführt wurden.

 Sie können Differenzinformationen über Typen, Stammelemente und Dominatoren anzeigen. Der Momentaufnahmevergleich zeigt alle Informationen, wie z. B. Objekte, die dem Heap in der Zeit zwischen den beiden Momentaufnahmen hinzugefügt wurden, an.

 Diese Abbildung zeigt die Ansicht "Typen" in einem Momentaufnahmevergleich.

 ![Momentaufnahme einer Differenzansicht, einschließlich Typen](../profiling/media/js_mem_snapshot_diff.png "JS_Mem_Snapshot_Diff")

 Im Fenster mit der Momentaufnahmendifferenz werden Ansichten von Dominatoren, Typen und Stämme genau so dargestellt wie im Fenster [Anzeigen von Momentaufnahmedetails](#view-snapshot-details) . Die Ansicht "Momentaufnahmevergleich" zeigen die gleichen Informationen wie die Momentaufnahmedetails an, und zusätzlich folgende Werte:

- **Größenunterschied**. Der Unterschied zwischen der Größe des Objekts in der aktuellen Momentaufnahme und seiner Größe in der vorherigen Momentaufnahme, ohne die Größe aller referenzierten Objekte.

- **Unterschied beibehaltene Größe**. Der Unterschied zwischen der beibehaltenen Größe des Objekts in der aktuellen Momentaufnahme und seiner beibehaltenen Größe in der vorherigen Momentaufnahme. Die beibehaltene Größe umfasst die Objektgröße sowie die Größe aller untergeordneten Objekte, die über keine anderen übergeordneten Objekte verfügen. Aus praktischen Gründen handelt es sich bei der beibehaltenen Größe um die Menge an Arbeitsspeicher, der vom Objekt beibehalten wird, sodass dieser Arbeitsspeicher wieder freigegeben wird, sobald Sie das Objekt löschen.

  Um die Differenzinformationen zwischen den Momentaufnahmen zu filtern, wählen Sie einen der **Bereichsfilter** oben in den Differenzansichten aus.

- **Übrige Objekte der Momentaufnahme \<number>** . Dieser Filter gibt die Differenz zwischen den Objekten, die dem Heap hinzugefügt wurden und die aus dem Heap entfernt wurden, im Vergleich zur Basis-Momentaufnahme und zur vorherigen Momentaufnahme an. Wenn die Momentaufnahmenzusammenfassung als Objektanzahl z. B. „+205/-195“ angibt, zeigt dieser Filter die zehn Objekte an, die hinzugefügt, jedoch nicht entfernt wurden.

  > [!TIP]
  > Um mit diesem Filter die nützlichsten Informationen anzuzeigen, befolgen Sie die unter [Isolate a memory leak](#isolate-a-memory-leak)beschriebenen Schritte.

- **Zwischen Momentaufnahme \<number> und \<number> hinzugefügte Objekte** Dieser Filter zeigt alle Objekte an, die nach der vorherigen Momentaufnahme dem Heap hinzugefügt wurden.

- **Alle Objekte in Momentaufnahme \<number>** Bei dieser Filtereinstellung werden keine Objekte im Heap herausgefiltert.

  Zum Anzeigen von Objektverweisen, die nicht dem aktuellen Filter **Bereich** entsprechen, wählen Sie in der rechten oberen Ecke des Bereichs die Option **Nicht übereinstimmende Verweise anzeigen** in der Einstellungsliste ![Settings drop&#45;down list in memory analyzer](../profiling/media/js_mem_settings.png "JS_Mem_Settings") (Dropdownliste „Einstellungen“ in Speicheranalyse) aus. Wenn Sie diese Einstellung aktivieren, werden nicht übereinstimmende Verweise mit grauem Text dargestellt.

> [!TIP]
> Es wird empfohlen, dass Sie die Schritte unter [Isolate a memory leak](#isolate-a-memory-leak) befolgen und dann anhand der übrigen Objekte, die mit dem **Bereichsfilter** herausgefiltert wurden, die Objekte ermitteln, die für den Speicherverlust verantwortlich sind.

## <a name="view-objects-by-dominator"></a>Anzeigen von Objekten nach Dominator
 In den Ansichten „Typen“ und „Dominatoren“ können Sie auswählen, ob Objekte in ihre Dominatoren gefaltet angezeigt werden sollen (dies ist die Standardansicht auf der Registerkarte **Dominatoren**). Wenn diese Ansicht ausgewählt ist, werden Dominatoren nur in der Ansicht der obersten Ebene von Objekten angezeigt. (Objekte, die untergeordnete Elemente von nicht globalen Objekten sind, werden in der Ansicht der obersten Ebene ausgeblendet.) Bei einigen Apps kann dies klären, welche Objekte einen Speicherverlust verursachen, indem Störungen in den Daten reduziert werden.

 Um die Anzeige von Objekten nach Dominator umzuschalten, wählen Sie die Schaltfläche **Objekte nach Dominator reduzieren** . ![Falten von Objekten in ihren Dominatoren](../profiling/media/js_mem_fold_objects.png "JS_Mem_Fold_Objects")

 Weitere Informationen zu Dominatoren finden Sie unter [Anzeigen von Momentaufnahmedetails](#view-snapshot-details).

## <a name="filter-data-by-identifier"></a>Daten nach Bezeichner filtern
 In den Ansichten "Dominatoren" und "Typen" können Sie Daten filtern, indem Sie nach bestimmten Bezeichnern suchen. Um nach einem Bezeichner zu suchen, geben Sie seinen Namen einfach oben rechts in das Textfeld **Bezeichnerfilter** ein. Wenn Sie mit der Eingabe beginnen, werden Bezeichner ohne die eingegebenen Zeichen herausgefiltert.

 Jede Ansicht hat ihren eigenen Filter, sodass der Filter nicht beibehalten wird, wenn Sie zu einer anderen Ansicht wechseln.

## <a name="find-an-object-in-the-object-tree"></a>Suchen eines Objekts in der Objektstruktur
 In den Typen- und Dominatorenansichten wird die Beziehung eines bestimmten Objekts zum `Global` -Objekt sichtbar. Für Objekte, die mit dem `Global` -Objekt als Stamm verknüpft sind, wird keine Garbage Collection durchgeführt. Sie können ein bekanntes Objekt leicht in der Stammansicht finden, ohne die Objektstruktur `Global` zu durchsuchen. Öffnen Sie hierzu das Kontextmenü für ein Objekt in der Ansicht "Dominatoren" oder "Typen", und wählen Sie dann **In Stammansicht anzeigen** aus.

## <a name="view-shared-object-references"></a>Anzeigen von freigegebenen Objektverweisen
 In den Typen- und Dominatorenansichten enthält der untere Bereich eine Objektverweisliste, in der die freigegebenen Verweise angezeigt werden. Wenn Sie ein Objekt im oberen Bereich auswählen, werden in der Objektverweisliste alle Objekte angezeigt, die auf dieses Objekt verweisen.

> [!NOTE]
> Zirkelverweise werden mit einem Sternchen (*) und einer Informations-QuickInfo angezeigt und können nicht erweitert werden. Andernfalls würden sie Sie am Durchlaufen der Verweisstruktur und an der Bestimmung von Objekten hindern, die Arbeitsspeicher einnehmen.

 Wenn Sie zusätzliche Hilfe bei der Identifizierung von gleichwertigen Objekten benötigen, wählen Sie in der Einstellungsliste ![Settings drop&#45;down list in memory analyzer](../profiling/media/js_mem_settings.png "JS_Mem_Settings") (Dropdownliste „Einstellungen“ in Speicheranalyse) in der rechten Ecke des oberen Bereichs die Option **Objekt-IDs anzeigen** aus. Durch diese Option werden Objekt-IDs neben den Objektnamen in der Liste **Bezeichner** angezeigt (die IDs werden in allen Ansichten, nicht nur in der Objektverweisliste, angezeigt). Objekte mit der gleichen ID sind freigegebene Verweise.

 Die folgende Abbildung zeigt die Objektverweisliste für ein ausgewähltes Element mit den angezeigten IDs an.

 ![Objektverweise mit angezeigten IDs](../profiling/media/js_mem_shared_refs.png "JS_Mem_Shared_Refs")

## <a name="show-built-in-objects"></a>Anzeigen integrierter Objekte
 Standardmäßig werden in den Ansichten "Dominatoren" und "Typen" nur die Objekte angezeigt, die in der App erstellt werden. Damit werden nicht benötigte Informationen herausgefiltert und auf die App bezogene Probleme isoliert. Manchmal ist es aber hilfreich, alle Objekte anzuzeigen, die von der JavaScript-Laufzeit für die App generiert werden.

 Wenn Sie diese Objekte anzeigen möchten, wählen Sie in der Einstellungsliste ![Settings drop&#45;down list in memory analyzer](../profiling/media/js_mem_settings.png "JS_Mem_Settings") (Dropdownliste „Einstellungen“ in Speicheranalyse) in der rechten oberen Ecke des Bereichs die Option **Integrierte anzeigen** aus.

## <a name="save-diagnostic-session-files"></a>Speichern von Diagnosesitzungsdateien
 Momentaufnahmenzusammenfassungen zu Diagnosezwecken sowie die zugeordneten Detailansichten werden als *DIAGSESSIONS*-Dateien gespeichert. Der **Projektmappen-Explorer** zeigt vorherige Diagnosesitzungen im Ordner "Diagnosesitzungen" an. Im **Projektmappen-Explorer** können Sie vorherige Sitzungen öffnen oder Dateien entfernen bzw. umbenennen.

## <a name="associate-source-code-with-memory-usage-data"></a>Zuordnen von Quellcode zu Speicherauslastungsdaten
 Zur Isolierung des Codeabschnitts, bei dem ein Arbeitsspeicherproblem vorliegt, verwenden Sie die folgenden Methoden:

- Suchen Sie nach Klassennamen und IDs für DOM-Elemente in den Details und den differenziellen Ansichten.

- Suchen Sie nach Zeichenfolgewerten in den Details und den Differenzansichten, die eventuell dem Quellcode zugeordnet sind.

- Verwenden Sie den Befehl [Suchen eines Objekts in der Objektstruktur](#find-an-object-in-the-object-tree) , um die Objektstruktur zu durchlaufen. Dies hilft Ihnen möglicherweise dabei, den entsprechenden Quellcode zu identifizieren.

- Fügen Sie Speicheranalysebefehle zum Quellcode hinzu.

  Sie können die folgenden Befehle im Quellcode verwenden:

- `console.takeHeapSnapshot` akzeptiert eine in der JavaScript-Arbeitsspeicheranalyse angezeigte Heapmomentaufnahme. Dieser Befehl ist einer der [JavaScript Console commands](../debugger/javascript-console-commands.md).

- `performance.mark` legt eine Benutzermarkierung fest (das umgekehrte Dreieck), die in der Zusammenfassungsansicht in der Zeitachse des Arbeitsspeicherdiagramms angezeigt wird, während die App ausgeführt wird. Dieser Befehl akzeptiert ein Zeichenfolgenargument, mit dem das Ereignis beschrieben und als QuickInfo im Arbeitsspeicherdiagramm angezeigt wird. Diese Beschreibung darf 100 Zeichen nicht übersteigen.

> [!TIP]
> Verwenden Sie `console.takeHeapSnapshot` , um die Analyse bei der Überprüfung von Speicherauslastungsszenarien zu beschleunigen.

 Diese Befehle lösen eine Ausnahme aus, wenn Sie sie der App hinzufügen und die App außerhalb der JavaScript-Speicheranalyse ausführen. Vor deren Verwendung jedoch können Sie testen, ob die Befehle vorhanden sind. (Die Befehle sind nicht früh in der Anlaufphase der Sitzung vorhanden.) Um sicherzustellen, dass Sie `takeHeapSnapshot`sicher aufrufen können, verwenden Sie den folgenden Code:

```javascript
if (console && console.takeHeapSnapshot) {
    console.takeHeapSnapshot();
}
```

 Um sicherzustellen, dass Sie `performance.mark` sicher aufrufen können, verwenden Sie den folgenden Code:

```javascript
if (performance && performance.mark) {
    performance.mark("message_string");
}

```

 Hier sehen Sie ein Arbeitsspeicherdiagramm mit einigen Benutzermarkierungen und der QuickInfo für die aktuell ausgewählte Benutzermarkierung, für die das `performance.mark` -Zeichenfolgeargument auf "Daten generiert" festgelegt wird:

 ![Verwenden einer Profilmarkierung](../profiling/media/js_mem_performance_marks.png "JS_Mem_Performance_Marks")

## <a name="tips-to-identify-memory-issues"></a>Tipps zum Identifizieren von Arbeitsspeicherproblemen

- Führen Sie den unter [Isolieren eines Speicherverlusts](#isolate-a-memory-leak) beschriebenen Workflow aus, und verwenden Sie den Filter **Übrige Objekte der Momentaufnahme \<number>** in einer Differenzansicht, um Kandidaten zu identifizieren, die wahrscheinlich für die Speicherverluste verantwortlich sind.

- Verwenden Sie [Suchen eines Objekts in der Objektstruktur](#find-an-object-in-the-object-tree) können Sie anzeigen, an welcher Stelle in der Speicherhierarchie auf ein Objekt verwiesen wird. Die Stammansicht zeigt, wie ein Objekt mit dem globalen Objekt als Stamm verknüpft ist, was die Garbage Collection für dieses Objekt verhindern würde.

- Wenn die Ursache eines Arbeitsspeicherproblems schwer zu erkennen ist, verwenden Sie die verschiedenen Ansichten (z. B. Dominatoren und Typen), um nach Gemeinsamkeiten zu suchen. Dies kann insbesondere dazu nützlich sein, ein Objekt (oder einige wenige Objekte) zu identifizieren, die Verweise auf viele andere Objekte in der Ansicht enthalten.

- Suchen Sie nach Objekten, die versehentlich im Arbeitsspeicher beibehalten werden, nachdem der Benutzer zu einer neuen Seite navigiert ist. Dies ist eine häufige Ursache von Arbeitsspeicherproblemen. Zum Beispiel:

  - Die falsche Verwendung der Funktion [URL.CreateObjectUrl](https://developer.mozilla.org/docs/Web/API/URL/createObjectURL) kann dieses Problem verursachen.

  - Einige Objekte stellen möglicherweise eine `dispose` -Methode und Verwendungsempfehlungen bereit. So sollten Sie zum Beispiel `dispose` für ein [WinJS.Binding.List](/previous-versions/windows/apps/hh700774\(v\=win.10\)) aufrufen, wenn Sie die `createFiltered` -Methode der Liste aufrufen und dann von einer Seite weg navigieren.

  - Sie müssen unter Umständen einen oder mehrere Eventlistener entfernen. Weitere Informationen finden Sie unter [View DOM event listeners](../debugger/quickstart-debug-html-and-css.md).

- Sehen Sie sich den letzten Teil [dieses Video](https://channel9.msdn.com/Events/Build/2013/3-316) von der Build 2013-Konferenz über die JavaScript-Speicheranalyse an.

- Lesen Sie sich [Managing memory in UWP apps (Verwalten von Speicher in UWP-Apps)](/archive/msdn-magazine/2012/windows-8-special-issue/javascript-managing-memory-in-windows-store-apps) durch.

- Erwägen Sie, vorübergehend Code zu ändern, um Probleme zu isolieren. Auf diese Weise können Sie z. B. folgende Vorgänge durchführen:

  - Verwenden Sie die Befehle für die Speicheranalyse, `console.takeSnapshot` und `performance.mark`. (Siehe [Associate source code with memory usage data](#associate-source-code-with-memory-usage-data).)

    Sie können diese Befehle zum Isolieren von Problemen verwenden, die Sie nicht isolieren können, indem Sie manuell eine Heap-Momentaufnahme erstellen.

  - Erstellen Sie ein Testobjekt, und verfolgen Sie es in den Ansichten der JavaScript-Speicheranalyse, z. B. in der Typenansicht. Beispielsweise können Sie einem anderen Objekt ein sehr großes Objekt anfügen, um festzustellen, ob für ein bestimmtes Objekt oder Element eine Garbage Collection durchgeführt wurde.