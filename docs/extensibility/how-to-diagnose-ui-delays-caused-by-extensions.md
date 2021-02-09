---
title: Diagnostizieren von Verzögerungen bei der Benutzeroberfläche in Visual Studio | Microsoft-Dokumentation
description: Visual Studio benachrichtigt Sie, wenn Benutzeroberflächen Verzögerungen durch eine Erweiterung verursacht werden könnten. Erfahren Sie, wie Sie diagnostizieren können, was in Ihrem Erweiterungs Code zu Benutzeroberflächen Verzögerungen führt.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: jmartens
ms.workload: multiple
ms.openlocfilehash: 508fdd44a1c73f66d88317b7ec304e810f5f12e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890798"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Gewusst wie: Analysieren von Benutzeroberflächen-Verzögerungen durch Erweiterungen

Wenn die Benutzeroberfläche nicht mehr reagiert, untersucht Visual Studio den Aufrufstapel des UI-Threads, beginnend mit dem Blatt und arbeitet an der Basis. Wenn Visual Studio feststellt, dass ein Aufrufstapel Rahmen zu einem Modul gehört, das Teil einer installierten und aktivierten Erweiterung ist, wird eine Benachrichtigung angezeigt.

![Benachrichtigung zur Benutzeroberflächen Verzögerung (nicht Reaktionsfähigkeit)](media/ui-delay-notification-in-vs.png)

Die Benachrichtigung informiert den Benutzer darüber, dass die Benutzeroberflächen Verzögerung (d. h. die nicht Reaktionsfähigkeit in der Benutzeroberfläche) möglicherweise das Ergebnis von Code aus einer Erweiterung gewesen ist. Außerdem bietet der Benutzeroptionen, um die Erweiterung oder zukünftige Benachrichtigungen für diese Erweiterung zu deaktivieren.

In diesem Dokument wird beschrieben, wie Sie diagnostizieren können, was in Ihrem Erweiterungs Code zu Benutzeroberflächen-Verzögerungs Benachrichtigungen führt.

> [!NOTE]
> Verwenden Sie die experimentelle Instanz von Visual Studio nicht zur Diagnose von UI-Verzögerungen. Wenn die experimentelle Instanz verwendet wird, werden einige Teile der bei der Verwendung der UI-Verzögerungs Benachrichtigung erforderlichen Rückruf Stapel Analyse deaktiviert. Dies bedeutet, dass Benachrichtigungen für die Benutzeroberflächen Verzögerung möglicherweise nicht angezeigt werden.

Eine Übersicht über den Diagnoseprozess lautet wie folgt:
1. Identifizieren Sie das auslöserszenario.
2. Starten Sie vs mit Aktivitätenprotokollierung neu.
3. Etw-Ablauf Verfolgung starten.
4. Veranlassen Sie, dass die Benachrichtigung erneut angezeigt wird.
5. Beendet die ETW-Ablauf Verfolgung.
6. Prüfen Sie das Aktivitätsprotokoll, um die Verzögerungs-ID zu erhalten.
7. Analysieren Sie die ETW-Ablauf Verfolgung mithilfe der Verzögerungs-ID aus Schritt 6.

In den folgenden Abschnitten werden diese Schritte ausführlicher erläutert.

## <a name="identify-the-trigger-scenario"></a>Identifizieren des auslöserszenarios

Um eine Benutzeroberflächen Verzögerung zu diagnostizieren, müssen Sie zuerst bestimmen, welche Aktion (Aktions Folge) bewirkt, dass Visual Studio die Benachrichtigung anzeigt. Dies ist möglich, damit Sie die Benachrichtigung später mithilfe der Protokollierung aktivieren können.

## <a name="restart-vs-with-activity-logging-on"></a>Neustart im Vergleich mit der Aktivitäts Protokollierung

Visual Studio kann ein "Aktivitätsprotokoll" generieren, das beim Debuggen eines Problems nützliche Informationen bereitstellt. Öffnen Sie Visual Studio mit der Befehlszeilenoption, um die Aktivitäts Protokollierung in Visual Studio zu `/log` aktivieren. Nach dem Start von Visual Studio wird das Aktivitätsprotokoll an folgendem Speicherort gespeichert:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Weitere Informationen dazu, wie Sie Ihre vs-Instanz-ID finden können, finden Sie unter [Tools zum erkennen und Verwalten von Visual Studio-Instanzen](../install/tools-for-managing-visual-studio-instances.md). Wir verwenden dieses Aktivitätsprotokoll später, um weitere Informationen zu Benutzeroberflächen Verzögerungen und zugehörigen Benachrichtigungen zu erhalten.

## <a name="starting-etw-tracing"></a>Etw-Ablauf Verfolgung wird gestartet

Sie können [perfview](https://github.com/Microsoft/perfview/) verwenden, um eine ETW-Ablauf Verfolgung zu erfassen. Perfview bietet eine benutzerfreundliche Schnittstelle, die sowohl zum Erfassen einer etw-Ablauf Verfolgung als auch zur Analyse verwendet wird. Verwenden Sie den folgenden Befehl, um eine Ablauf Verfolgung zu erfassen:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Dadurch wird der Anbieter "Microsoft-VisualStudio" aktiviert. Dies ist der Anbieter, den Visual Studio für Ereignisse verwendet, die sich auf Benachrichtigungen in der Benutzeroberfläche beziehen. Außerdem wird das Schlüsselwort für den Kernel Anbieter angegeben, den perfview zum Generieren der **Thread Zeit Stapel** Ansicht verwenden kann.

## <a name="trigger-the-notification-to-appear-again"></a>Benachrichtigung zum erneuten Anzeigen der Benachrichtigung

Nachdem perfview die Ablauf Verfolgungs Sammlung gestartet hat, können Sie die triggeraktionssequenz (aus Schritt 1) verwenden, damit die Benachrichtigung erneut angezeigt wird. Sobald die Benachrichtigung angezeigt wird, können Sie die Ablauf Verfolgungs Sammlung für perfview abbrechen, um die Ausgabedatei der Ablauf Verfolgung zu verarbeiten und zu generieren.

## <a name="stop-etw-tracing"></a>Etw-Ablauf Verfolgung Abbrechen

Um die Ablauf Verfolgungs Sammlung anzuhalten, verwenden Sie einfach die Schaltfläche Auflistung **Abbrechen** im Fenster perfview. Wenn Sie die Ablauf Verfolgungs Sammlung beenden, verarbeitet perfview automatisch die ETW-Ereignisse und generiert eine Ausgabedatei der Ablauf Verfolgung.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Überprüfen des Aktivitäts Protokolls, um die Verzögerungs-ID zu erhalten

Wie bereits erwähnt, finden Sie das Aktivitätsprotokoll unter *%AppData%\microsoft\visualstudio \<vs_instance_id>\ActivityLog.xml*. Jedes Mal, wenn Visual Studio eine Benutzeroberflächen Verzögerung der Erweiterung erkennt, wird ein Knoten mit als Quelle in das Aktivitätsprotokoll geschrieben `UIDelayNotifications` . Dieser Knoten enthält vier Informationen über die Benutzeroberflächen Verzögerung:

- Die UI-Verzögerungs-ID, eine sequenzielle Zahl, die eine Benutzeroberflächen Verzögerung in einer vs-Sitzung eindeutig identifiziert
- Die Sitzungs-ID, die die Visual Studio-Sitzung von Anfang bis Ende eindeutig identifiziert.
- Gibt an, ob eine Benachrichtigung für die Benutzeroberflächen Verzögerung angezeigt wurde oder nicht.
- Die Erweiterung, die die Benutzeroberflächen Verzögerung wahrscheinlich verursacht hat

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> Nicht alle Benutzeroberflächen Verzögerungen führen zu einer Benachrichtigung. Daher sollten Sie immer den Wert " **Benachrichtigung angezeigt?** " überprüfen, um die richtige Benutzeroberflächen Verzögerung korrekt zu ermitteln.

Nachdem Sie die korrekte Benutzeroberflächen Verzögerung im Aktivitätsprotokoll gefunden haben, notieren Sie sich die im Knoten angegebene UI-Verzögerungs-ID. Im nächsten Schritt wird die ID verwendet, um nach dem entsprechenden ETW-Ereignis zu suchen.

## <a name="analyze-the-etw-trace"></a>Analysieren der etw-Ablauf Verfolgung

Öffnen Sie als nächstes die Ablauf Verfolgungs Datei. Hierzu können Sie entweder die gleiche Instanz von perfview verwenden oder eine neue Instanz starten und den aktuellen Ordner Pfad in der oberen linken Ecke des Fensters auf den Speicherort der Ablauf Verfolgungs Datei festlegen.

![Festlegen des Ordner Pfads in perfview](media/perfview-set-path.png)

Wählen Sie dann im linken Bereich die Ablauf Verfolgungs Datei aus, und öffnen Sie Sie, indem Sie im Kontextmenü auf **Öffnen** klicken.

> [!NOTE]
> Standardmäßig gibt perfview ein ZIP-Archiv aus. Wenn Sie *trace.zip* öffnen, wird das Archiv automatisch deaktiviert und die Ablauf Verfolgung geöffnet. Sie können dies überspringen, indem Sie die **ZIP** -Datei während der Ablauf Verfolgungs Sammlung deaktivieren. Wenn Sie jedoch die Übertragung und Verwendung von Ablauf Verfolgungen auf verschiedenen Computern planen, wird dringend empfohlen, das **ZIP** -Feld nicht zu deaktivieren. Ohne diese Option werden die erforderlichen PDBs für ngen-Assemblys nicht mit der Ablauf Verfolgung begleitet, sodass Symbole aus ngen-Assemblys auf dem Zielcomputer nicht aufgelöst werden. (Weitere Informationen zu pdsb für ngen-Assemblys finden Sie in [diesem Blogbeitrag](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/) .)

Es kann einige Minuten dauern, bis perfview die Ablauf Verfolgung verarbeitet und geöffnet hat. Nachdem die Ablauf Verfolgung geöffnet ist, wird eine Liste mit verschiedenen "Ansichten" darunter angezeigt.

![Perfview-Zusammenfassungs Ansicht](media/perfview-summary-view-events-selected.png)

Zuerst wird die **Ereignis** Ansicht verwendet, um den Zeitbereich der Benutzeroberflächen Verzögerung zu ermitteln:

1. Öffnen Sie die Ansicht **Ereignisse** , indem `Events` Sie unter der Ablauf Verfolgung den Knoten auswählen und im Kontextmenü die Option **Öffnen** auswählen.
2. Wählen Sie `Microsoft-VisualStudio/ExtensionUIUnresponsiveness` im linken Bereich "" aus.
3. EINGABETASTE drücken

Die Auswahl wird angewendet, und alle `ExtensionUIUnresponsiveness` Ereignisse werden im rechten Bereich angezeigt.

![Auswählen von Ereignissen in der Ereignisansicht](media/perfview-event-selection.png)

Jede Zeile im rechten Bereich entspricht einer Benutzeroberflächen Verzögerung. Das Ereignis enthält den Wert "Delay ID", der der verzögerten ID im Aktivitätsprotokoll aus Schritt 6 entsprechen sollte. Da `ExtensionUIUnresponsiveness` am Ende der UI-Verzögerung ausgelöst wird, kennzeichnet der Zeitstempel des Ereignisses (ungefähr) die Endzeit der Benutzeroberflächen Verzögerung. Das Ereignis enthält auch die Dauer der Verzögerung. Wir können die Dauer des Endzeit Stempels subtrahieren, um den Zeitstempel zu erhalten, wann die Benutzeroberflächen Verzögerung gestartet wurde.

![Berechnen des Zeit Bereichs für die Benutzeroberflächen Verzögerung](media/ui-delay-time-range.png)

Im vorherigen Screenshot ist beispielsweise der Zeitstempel des Ereignisses 12.125,679, und die Verzögerungs Dauer beträgt 6.143,085 (MS). Demnach sind
* Der Verzögerungs Start beträgt 12.125,679-6.143,085 = 5.982,594.
* Der Zeitbereich für die Benutzeroberflächen Verzögerung beträgt 5.982,594 bis 12.125,679.

Sobald der Zeitbereich vorhanden ist, können wir die Ansicht **Ereignisse** schließen und die **Thread Zeit (mit der startstopps-Aktivität) der Stapel** Ansicht öffnen. Diese Ansicht ist besonders nützlich, da häufig Erweiterungen, die den UI-Thread blockieren, nur auf andere Threads oder einen e/a-gebundenen Vorgang warten. Daher kann die **CPU-Stapel** Ansicht, die in den meisten Fällen die Option "Gehe zu" ist, die Zeit, die der Thread blockiert, nicht erfassen, da die CPU während dieser Zeit nicht verwendet wird. Die **Thread Zeit Stapel** löst dieses Problem, indem die blockierte Zeit ordnungsgemäß angezeigt wird.

![Thread Zeit (mit startstoppaktivitäten) Stapel Knoten in der perfview-Zusammenfassungs Ansicht](media/perfview-thread-time-with-startstop-activities-stacks.png)

Wählen Sie beim Öffnen der **Thread Zeit Stapel** Ansicht den **devenv** -Prozess zum Starten der Analyse aus.

![Thread Zeit Stapel Ansicht für UI-Verzögerungs Analyse](media/ui-delay-thread-time-stacks.png)

In der Ansicht **Thread Zeit Stapel** oben links auf der Seite können Sie den Zeitbereich auf die Werte festlegen, die wir im vorherigen Schritt berechnet haben, und die **Eingabe** Taste drücken, damit die Stapel an diesen Zeitbereich angepasst werden.

> [!NOTE]
> Zu bestimmen, welcher Thread der UI-Thread (Start Thread) ist, kann kontraintuitiv sein, wenn die Ablauf Verfolgungs Sammlung gestartet wird, nachdem Visual Studio bereits geöffnet ist. Allerdings sind die ersten Elemente im Stapel des UI-Threads (Start) wahrscheinlich immer Betriebssystem-DLLs (*ntdll.dll* und *kernel32.dll*), gefolgt von `devenv!?` und dann `msenv!?` . Mithilfe dieser Sequenz kann der UI-Thread identifiziert werden.

 ![Identifizieren des Start Threads](media/ui-delay-startup-thread.png)

Sie können diese Ansicht auch weiter filtern, indem Sie nur Stapel einschließen, die Module aus dem Paket enthalten.

* Legen Sie **grouppats** auf leeren Text fest, um alle standardmäßig hinzugefügten Gruppierungen zu entfernen.
* Legen Sie " **incpats** " fest, um einen Teil des Assemblynamens zusätzlich zum vorhandenen Prozessfilter einzubeziehen. In diesem Fall sollte Sie "Debug" lauten **. UIDelayR2**.

![Festlegen von "GroupPath" und "incpath" in der Thread Zeit Stapel Ansicht](media/perfview-tts-group-path-inc-path.png)

Perfview enthält eine ausführliche Anleitung im Menü " **Hilfe** ", mit der Sie Leistungsengpässe in Ihrem Code identifizieren können. Zusätzlich finden Sie unter den folgenden Links weitere Informationen zum Verwenden von Visual Studio-Threading-APIs zur Optimierung Ihres Codes:

* [https://github.com/Microsoft/vs-threading/blob/master/doc/index.md](https://github.com/Microsoft/vs-threading/blob/master/doc/index.md)
* [https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md)

Sie können auch die neuen statischen Visual Studio-Analysen für Erweiterungen (nuget-Paket [hier](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)) verwenden, die Anleitungen zu bewährten Methoden zum Schreiben effizienter Erweiterungen bereitstellen. Hier finden Sie eine Liste der [vs SDK-Analysen](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) und [Threading-Analysen](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Wenn Sie die nicht Reaktionsfähigkeit aufgrund von Abhängigkeiten nicht beheben können (z. b. wenn die Erweiterung synchrone vs-Dienste im UI-Thread aufruft), möchten wir Sie darüber informieren. Wenn Sie Mitglied unseres Visual Studio-Partner Programms sind, können Sie sich mit uns in Verbindung setzen, indem Sie eine Supportanfrage für Entwickler einreichen. Verwenden Sie andernfalls das Tool "Problem melden", um Ihr Feedback zu senden und `"Extension UI Delay Notifications"` in den Titel einzubeziehen. Fügen Sie auch eine ausführliche Beschreibung ihrer Analyse ein.
