---
title: Erhöhen der Wahrscheinlichkeit, dass ein Leistungsproblem behoben wird
description: Zusätzliche Informationen und bewährte Methoden für das Übermitteln von Leistungsproblemen in Visual Studio
ms.custom: SEO-VS-2020
author: madskristensen
ms.author: madsk
manager: jmartens
ms.date: 11/19/2019
ms.topic: conceptual
ms.openlocfilehash: d3db409c67ab961adfceaeb8e3236cd964f95399
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962898"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>Erhöhen der Wahrscheinlichkeit der Behebung eines Leistungsproblems

Das Tool [Problem melden](./how-to-report-a-problem-with-visual-studio.md?view=vs-2019&preserve-view=true) wird von Visual Studio-Benutzern häufig genutzt, um eine Vielzahl von Problemen zu melden. Das Visual Studio-Team macht im Feedback der Benutzer Tendenzen bei Abstürzen und Verlangsamungen aus und löst Probleme, die eine breite Masse von Benutzern betreffen. Je umsetzbarer ein bestimmtes Feedbackticket ist, desto wahrscheinlicher wird es vom Produktteam analysiert und schnell bearbeitet. In diesem Dokument werden die bewährten Methoden beim Melden von Problemen bezüglich Abstürzen oder Verlangsamung beschrieben, um sie umsetzbarer zu machen.

## <a name="general-best-practices"></a>Allgemeine bewährte Methoden

Visual Studio ist eine umfangreiche, komplexe Plattform, die eine Vielzahl von Sprachen, Projekttypen, Plattformen und mehr unterstützt. Seine Leistung hängt von Folgendem ab: den installierten und in einer Sitzung aktiven Komponenten, den installierten Erweiterungen, den Visual Studio-Einstellungen, der Computerkonfiguration und schließlich der Form des bearbeiteten Codes. Angesichts der Anzahl der Variablen ist es schwer zu sagen, ob dem Problembericht eines Benutzers das gleiche Problem wie in einem Problembericht eines anderen Benutzers zugrunde liegt, auch wenn das sichtbare Symptom identisch ist. Vor diesem Hintergrund finden Sie hier einige bewährte Methoden, um sicherzustellen, dass Ihr spezifischer Problembericht mit einer höheren Wahrscheinlichkeit einer Diagnose unterzogen wird.

**Wählen Sie einen möglichst spezifischen Titel**

Achten Sie auf eindeutige Merkmale des gemeldeten Problems, und geben Sie so viele Informationen wie möglich im Titel an. Wenn der Titel beschreibend ist, ist es weniger wahrscheinlich, dass Benutzer mit nicht damit verbundenen Problemen (aber oberflächlich demselben Symptom) Ihr Ticket bewerten oder kommentieren, was die Diagnose Ihres *Problems* erschwert.

**Übermitteln Sie im Zweifelsfall einen neuen Problembericht**

Viele Probleme weisen möglicherweise keine ausgeprägten Merkmale oder reproduzierbare Schritte auf. In solchen Fällen ist ein neuer Bericht besser als eine Zustimmung oder ein Kommentar zu einem anderen Bericht, der ein äußerlich ähnliches *Symptom* meldet. Fügen Sie Ihrem Bericht, wie weiter unten in diesem Dokument beschrieben, je nach dessen Typ zusätzliche Diagnosedateien hinzu.

**Problemspezifische bewährte Methoden**

Im Folgenden werden Probleme beschrieben, die ohne brauchbare Diagnosedateien schwer zu analysieren sind. Nachdem Sie den Sachverhalt bestimmt haben, der Ihr Problem am besten beschreibt, befolgen Sie die für diesen Sachverhalt spezifischen Feedbackschritte.

- [Abstürze:](#crashes) Ein Absturz tritt auf, wenn der Prozess (Visual Studio) unerwartet beendet wird.

- [Fehlende Reaktionsfähigkeit:](#unresponsiveness) VS verliert über einen längeren Zeitraum die Reaktionsfähigkeit.

- [Probleme wegen Langsamkeit:](#slowness-and-high-cpu-issues) Eine bestimmte Aktion in VS erfolgt langsamer als gewünscht.

- [Hohe CPU-Auslastung:](#slowness-and-high-cpu-issues) Längere Zeiträume mit unerwartet hoher CPU-Auslastung

- [Out-of-Process-Probleme:](#out-of-process-issues) Ein durch einen Visual Studio-Satellitenvorgang verursachtes Problem.

## <a name="crashes"></a>Abstürze
Ein Absturz tritt auf, wenn der Prozess (Visual Studio) unerwartet beendet wird.

**Direkt reproduzierbare Abstürze**

Direkt reproduzierbare Abstürze sind Sachverhalte mit allen folgenden Merkmalen:

- Sind zu beobachten, wenn eine bekannte Reihe von Schritten durchlaufen wird

- Sind auf mehreren Computern (sofern verfügbar) zu beobachten

- Lassen sich in Beispielcode oder einem Projekt reproduzieren, das mit dem Feedback verknüpft oder als Teil dessen bereitgestellt werden kann (wenn die Schritte das Öffnen eines Projekts oder Dokuments vorsehen)

Befolgen Sie für diese Probleme die Schritte unter [Melden eines Problems](./how-to-report-a-problem-with-visual-studio.md), und stellen Sie sicher, dass Sie Folgendes angeben:

- Die Schritte zum Reproduzieren des Problems

- Ein eigenständiges Reproduzierungsprojekt (wie oben beschrieben) Wenn eine eigenständige Reproduzierung nicht möglich ist, geben Sie Folgendes an:

  - Die Sprache der geöffneten Projekte (C\#, C++ usw.)

  - Die Art des Projekts (Konsolenanwendung, ASP.NET usw.)

> [!NOTE]
> **Das nützlichste Feedback:** In diesem Fall ist das nützlichste Feedback die Abfolge der Schritte zum Reproduzieren des Problems sowie Beispielquellcode.

**Unbekannte Absturzursache**

Wenn Sie sich nicht sicher sind, was Ihre Abstürze verursacht, oder wenn sie willkürlich auftreten, können Sie bei jedem Absturz von Visual Studio Speicherabbilder lokal erfassen und diese an separate Feedbackelemente anfügen. Um Speicherabbilder bei einem Absturz von Visual Studio lokal zu speichern, führen Sie im Modus „Administrator“ in einem Befehlsfenster die folgenden Befehle aus:

```
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"
```

Passen Sie Anzahl und Ordner für Speicherabbilder entsprechend an. Weitere Informationen dazu finden Sie [hier](/windows/win32/wer/collecting-user-mode-dumps).

> [!NOTE]
> Mit dem Task-Manager erfasste Speicherabbilder haben wahrscheinlich die falsche Bitanzahl, wodurch sie weniger nützlich sind. Das oben beschriebene Verfahren ist die bevorzugte Methode zum Erfassen einer Heap-Abbilddatei. Wenn Sie den Task-Manager verwenden möchten, schließen Sie den aktuell aktiven Task-Manager. Starten Sie den 32-Bit-Task-Manager (%windir%\\syswow64\\taskmgr.exe), und erfassen Sie in diesem eine Heap-Abbilddatei.

> [!NOTE]
> Jede Speicherabbilddatei, die von dieser Methode erstellt wird, kann bis zu 4 GB groß sein. Stellen Sie sicher, dass Sie DumpFolder auf einen Speicherort mit ausreichendem Speicherplatz auf dem Laufwerk festlegen oder DumpCount entsprechend anpassen.

Bei jedem Absturz von Visual Studio wird am konfigurierten Speicherort eine Speicherabbilddatei **devenv.exe.[Nummer].dmp** erstellt.

Verwenden Sie anschließend die Visual Studio-Funktion „Problem melden“. Dies ermöglicht Ihnen, das entsprechende Speicherabbild anzufügen.

1. Ermitteln Sie die zum Absturz gehörige Speicherabbilddatei (suchen Sie nach einer Datei mit dem passenden Erstellungszeitpunkt).

2. Zippen Sie die Datei (\*.zip) nach Möglichkeit, um sie zu verkleinern, bevor Sie Feedback übermitteln.

3. Befolgen Sie die Schritte unter [Melden eines Problems](./how-to-report-a-problem-with-visual-studio.md), und fügen Sie die Heap-Abbilddatei an ein neues Feedbackelement an.

> [!NOTE]
> **Das nützlichste Feedback:** Für diesen Sachverhalt ist das nützlichste Feedback die zum Zeitpunkt des Absturzes erfasste Heap-Abbilddatei.

## <a name="unresponsiveness"></a>Fehlende Reaktionsfähigkeit
VS verliert über einen längeren Zeitraum die Reaktionsfähigkeit.

**Direkt reproduzierbare fehlende Reaktionsfähigkeit**

Wie im entsprechenden Abschnitt zu Abstürzen beschrieben, sind für Probleme, die sich leicht reproduzieren lassen, auf mehreren Computern auftreten und in einem kleinen Beispiel demonstriert werden können, die nützlichsten Feedbackberichte diejenigen, die Schritte zur Reproduzierung des Problems und Beispielquellcode zu dessen Veranschaulichung enthalten.

**Fehlende Reaktionsfähigkeit aus unbekanntem Grund**

Wenn sich eine fehlende Reaktionsfähigkeit auf unvorhersehbare Weise bemerkbar macht, starten Sie beim nächsten Auftreten eine neue Instanz von Visual Studio, und melden Sie ein Problem aus dieser Instanz.
Stellen Sie sicher, dass Sie in der Anzeige „Aufzeichnen“ die Visual Studio-Sitzung auswählen, die nicht reagiert. (Weitere Informationen zum Aufzeichnen von Aktionen, die wir ausführen können, um das Problem zu reproduzieren, finden Sie in Schritt 8 der Seite [Vorgehensweise: Melden eines Problems](./how-to-report-a-problem-with-visual-studio.md).)

Wenn die nicht reagierende Visual Studio-Instanz im Modus „Administrator“ gestartet wurde, muss die zweite Instanz ebenfalls im Modus „Administrator“ gestartet werden.

>[!NOTE]
> **Das nützlichste Feedback:** Für diesen Sachverhalt ist das nützlichste Feedback die zum Zeitpunkt der fehlenden Reaktionsfähigkeit erfasste Heap-Abbilddatei.

## <a name="slowness-and-high-cpu-issues"></a>Probleme aufgrund von Verlangsamung und hoher CPU-Auslastung

Was die Lösung eines Problem aufgrund von Verlangsamung oder hoher CPU-Auslastung am besten ermöglicht, ist eine Leistungsüberwachung, die während des verlangsamten Betriebs oder eines Ereignisses mit hoher CPU-Auslastung erfasst wird.

>[!NOTE]
> Isolieren Sie nach Möglichkeit jedes Szenario in einem separaten, spezifischen Feedbackbericht.
Wenn beispielsweise Eingabe und Navigation langsam erfolgen, führen Sie die folgenden Schritte einmal pro Problem aus. Dies hilft dem Produktteam, die Ursache bestimmter Probleme zu ergründen.

Führen Sie die folgenden Schritte aus, um die Leistung optimal zu erfassen:

1. Falls noch nicht geschehen, öffnen Sie eine Instanz von Visual Studio, in der Sie das Problem reproduzieren können.

    - Richten Sie alles ein, um das Problem zu reproduzieren. Wenn Sie beispielsweise möchten, dass ein bestimmtes Projekt mit einer bestimmten geöffneten Datei geladen wird, stellen Sie sicher, dass beide Schritte abgeschlossen sind, bevor Sie fortfahren.

    - Wenn Sie *kein* spezifisches Problem beim Laden einer Projektmappe melden, warten Sie nach dem Öffnen der Projektmappe 5-10 Minuten (oder je nach Größe der Projektmappe noch länger), bevor Sie die Leistungsüberwachung aufzeichnen. Beim Laden der Projektmappe werden viele Daten erzeugt, sodass das Warten einiger Minuten uns hilft, uns auf das spezifische Problem zu konzentrieren, das Sie melden.

2. Starten Sie eine zweite Kopie von Visual Studio, *ohne dass eine Projektmappe geöffnet ist*.

3. Öffnen Sie in der neuen Kopie von Visual Studio das Tool **Problem melden**.

4. Führen Sie die Schritte unter [Melden eines Problems](./how-to-report-a-problem-with-visual-studio.md) aus, bis Sie den Schritt zum „Bereitstellen einer Ablaufverfolgung und Heap-Abbilddatei (optional)“ erreichen.

5. Wählen Sie die Aufzeichnung der ersten Kopie von Visual Studio (in der ein Leistungsproblem auftritt), und starten Sie die Aufzeichnung.

    - Die Anwendung „Schrittaufzeichnung“ wird eingeblendet und beginnt mit der Aufzeichnung.

    - Führen Sie **während der Aufzeichnung** in der ersten Kopie von Visual Studio die problematische Aktion aus. Es ist für uns schwierig, spezifische Leistungsprobleme zu beheben, wenn sie nicht innerhalb der aufgezeichneten Zeit auftreten.

    - Wenn die Aktion kürzer als 30 Sekunden ist und sich leicht wiederholen lässt, wiederholen Sie die Aktion, um das Problem weiter zu demonstrieren.

    - In den meisten Fällen genügt eine Ablaufverfolgung von 60 Sekunden, um die Probleme aufzuzeigen, insbesondere wenn die problematische Aktion länger als 30 Sekunden gedauert hat (oder wiederholt wurde). Die Dauer kann bei Bedarf angepasst werden, um das Verhalten zu erfassen, das korrigiert werden soll.

6. Klicken Sie in der Schrittaufzeichnung auf „Aufzeichnung beenden“, sobald das Ereignis mit verlangsamten Betrieb oder hoher CPU-Auslastung, das Sie melden möchten, beendet ist. Die Verarbeitung der Leistungsüberwachungsdaten kann einige Minuten dauern.

7. Nach Abschluss des Vorgangs weist Ihr Feedback mehrere Anlagen auf. Fügen Sie beliebige zusätzliche Dateien hinzu, die helfen können, das Problem zu reproduzieren (ein Beispielprojekt, Screenshots, Videos usw.).

8. Senden Sie das Feedback.

Wenn während der Aufzeichnung einer Leistungsüberwachung die Verlangsamung oder hohe CPU-Auslastung, die Sie melden, endet, beenden Sie sofort die Aufzeichnung. Bei Erfassung von zu vielen Informationen werden die ältesten Informationen überschrieben. Wenn die Ablaufverfolgung nicht rechtzeitig (innerhalb weniger Sekunden) nach dem betreffenden Vorgang beendet wird, werden nützliche Ablaufverfolgungsdaten überschrieben.

Fügen Sie keine Leistungsüberwachungen direkt an Feedbackelemente an, die bereits auf der Website der Entwicklercommunity vorhanden sind. Das Anfordern/Bereitstellen zusätzlicher Informationen ist ein unterstützter Workflow in dem in Visual Studio integrierten Tool „Problem melden“. Wenn eine Leistungsüberwachung erforderlich ist, um das Problem in einem vorherigen Feedbackelement zu lösen, legen wir den Status des Feedbackelements auf „Weitere Informationen erforderlich“ fest. Darauf kann genauso wie auf ein neues Problem reagiert werden. Eine ausführliche Anleitung finden Sie im Abschnitt [Weitere Informationen erforderlich](./how-to-report-a-problem-with-visual-studio.md#when-further-information-is-needed) im Dokument zum Tool „Problem melden“.

> [!NOTE]
> **Das nützlichste Feedback:** Bei nahezu allen Problemen aufgrund von Langsamkeit und hoher CPU-Auslastung ist das nützlichste Feedback eine allgemeine Beschreibung dessen, was Sie zu tun versucht haben, sowie die ZIP-Datei mit der Leistungsüberwachung (\*.etl.zip), in der das Verhalten während dieses Zeitraums erfasst wurde.

**Erweiterte Leistungsüberwachung**

Die Funktionen zum Erfassen einer Ablaufverfolgung im Tool „Problem melden“ sind in den meisten Szenarien ausreichend. Es kann jedoch vorkommen, dass mehr Kontrolle über die Erfassung der Ablaufverfolgung erforderlich ist (z. B. eine Ablaufverfolgung mit höherer Puffergröße). In diesem Fall ist PerfView ein besonders gut geeignetes Tool. Schritte zur manuellen Aufzeichnung der Leistungsüberwachung mit dem Tool PerfView finden Sie auf der Seite zum [Aufzeichnen der Leistungsüberwachung mit PerfView](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Recording-performance-traces-with-PerfView.md).

## <a name="out-of-process-issues"></a>Out-of-Process-Probleme

> [!NOTE]
> Ab Visual Studio 2019 Version 16.3 werden Out-of-Process-Protokolle automatisch an das Feedback angehängt, das mit dem Tool „Problem melden“ übermittelt wird.
Wenn das Problem jedoch direkt reproduzierbar ist, könnte das Befolgen der folgenden Schritte dennoch helfen, zusätzliche Informationen hinzuzufügen, um das Problem besser diagnostizieren zu können.

Es gibt eine Reihe von Satellitenprozessen, die parallel zu Visual Studio ausgeführt werden und verschiedene Features von außerhalb des Hauptprozesses von Visual Studio bereitstellen. Wenn ein Fehler in einem dieser Satellitenprozesse auftritt, wird er normalerweise auf der Visual Studio Seite als „StreamJsonRpc.RemoteInvocationException“ oder „StreamJsonRpc.ConnectionLostException“ angezeigt.

Was diese Art von Problemen am einfachsten gestaltet, ist die Bereitstellung zusätzlicher Protokolle, die durch die folgenden Schritte gesammelt werden können:

1. Wenn es sich um ein direkt reproduzierbares Problem handelt, löschen Sie zunächst den Ordner **%temp%/servicehub/logs**. Wenn Sie dieses Problem nicht reproduzieren können, halten Sie diesen Ordner intakt und ignorieren Sie die folgenden Aufzählungen:

    - Legen Sie die globale Umgebungsvariable **ServiceHubTraceLevel** auf **Alle** fest.
    - Reproduzieren Sie das Problem.

2. Laden Sie Microsoft Visual Studio und das .NET Framework-Protokollerfassungstool [hier](https://www.microsoft.com/download/details.aspx?id=12493) herunter.
3. Führen Sie das Tool aus. Dadurch wird eine ZIP-Datei an **%temp%/vslogs.zip** ausgegeben. Fügen Sie diese Datei an Ihr Feedback an.

## <a name="see-also"></a>Siehe auch

* [Visual Studio-Feedbackoptionen](../ide/feedback-options.md)
* [Vorgehensweise: Melden eines Problems mit Visual Studio für Mac](/visualstudio/mac/report-a-problem)
* [Melden eines Problems mit dem Visual C++-Toolset oder der -Dokumentation](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio Developer Community](https://aka.ms/feedback/suggest?space=8)
* [Developer Community data privacy (Datenschutz in der Entwicklercommunity)](developer-community-privacy.md)