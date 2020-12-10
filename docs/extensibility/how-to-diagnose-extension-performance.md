---
title: 'Vorgehensweise: Diagnostizieren der Erweiterungs Leistung | Microsoft-Dokumentation'
description: Visual Studio benachrichtigt Benutzer über langsame Erweiterungen. Erfahren Sie, wie die Auswirkungen auf die Erweiterung berechnet werden und wie Erweiterungen lokal analysiert werden können.
ms.custom: SEO-VS-2020
ms.date: 11/08/2016
ms.topic: how-to
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jillfra
ms.workload:
- bertaygu
ms.openlocfilehash: 03721f2aedd231dd9d4c4edaadf5eeb3a89389c2
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994198"
---
# <a name="measuring-extension-impact-in-startup"></a>Messen der Erweiterungs Auswirkung beim Starten

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Konzentrieren Sie sich auf die Erweiterungs Leistung in Visual Studio 2017

Basierend auf Kundenfeedback war einer der Schwerpunktbereiche für die Visual Studio 2017-Version der Start-und Lösungs Ladeleistung. Als das Visual Studio-Platt Form Team haben wir daran gearbeitet, die Leistung beim Laden von Starts und Lösungen zu verbessern. Im Allgemeinen können die Messungen für installierte Erweiterungen eine beträchtliche Auswirkung auf diese Szenarien haben.

Damit Benutzer diese Auswirkung besser verstehen können, haben wir in Visual Studio ein neues Feature hinzugefügt, um Benutzer über langsame Erweiterungen zu benachrichtigen. In einigen Fällen erkennt Visual Studio eine neue Erweiterung, die entweder den Lade-oder Startvorgang der Projekt Mappe verlangsamt. Wenn eine Verlangsamung erkannt wird, wird Benutzern in der IDE eine Benachrichtigung angezeigt, die auf das Dialogfeld "Visual Studio-Leistung verwalten" hinweist. Auf dieses Dialogfeld kann auch immer über das Menü Hilfe zugegriffen werden, um zuvor erkannte Erweiterungen zu durchsuchen.

![Verwalten der Leistung von Visual Studio](media/manage-performance.png)

Dieses Dokument soll Erweiterungs Entwicklern helfen, indem die Berechnung der Erweiterungs Auswirkung beschrieben wird. Außerdem wird in diesem Dokument beschrieben, wie die Auswirkungen der Erweiterung lokal analysiert werden können. Durch das lokale analysieren der Erweiterungs Auswirkung wird festgelegt, ob eine Erweiterung möglicherweise als Leistungs Beeinträchtigung der Erweiterung angezeigt wird.

> [!NOTE]
> Dieses Dokument konzentriert sich auf die Auswirkungen von Erweiterungen beim Starten und Laden von Projektmappen. Erweiterungen haben auch Auswirkungen auf die Visual Studio-Leistung, wenn Sie bewirken, dass die Benutzeroberfläche nicht mehr reagiert. Weitere Informationen zu diesem Thema finden Sie unter Gewusst [wie: Diagnostizieren von UI-Verzögerungen durch Erweiterungen](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Auswirkungen von Erweiterungen auf den Start

Eine der gängigsten Methoden für Erweiterungen, die die Startleistung beeinflussen, besteht darin, die automatische Auslastung in einem der bekannten Kontext der Start Benutzeroberfläche, wie z. b. nosolutionist oder shellinitialized, auszuwählen. Diese UI-Kontexte werden während des Starts aktiviert. Alle Pakete, die das- `ProvideAutoLoad` Attribut in ihrer Definition mit diesen Kontexten enthalten, werden zu diesem Zeitpunkt geladen und initialisiert.

Wenn die Auswirkung einer Erweiterung gemessen wird, konzentrieren wir uns in erster Linie auf die Zeit, die für die Erweiterungen aufgewendet wird, die automatisch in den obigen Kontexten geladen werden. Zu den gemessenen Zeiten zählen u. a. die folgenden:

* Laden von Erweiterungsassemblys für synchrone Pakete
* Die im paketklassenkonstruktor für synchrone Pakete verbrachte Zeit.
* Zeitaufwand für die Paket Initialisierungs Methode (oder SetSite) für synchrone Pakete
* Bei asynchronen Paketen werden die obigen Vorgänge im Hintergrund Thread ausgeführt.  Daher werden die Vorgänge von der Überwachung ausgeschlossen.
* Zeit, die für alle asynchronen Arbeiten aufgewendet wird, die während der Paket Initialisierung zur Ausführung im Haupt Thread geplant sind
* Die Zeit, die für Ereignishandler aufgewendet wurde, insbesondere die shellinitialisierte Kontext Aktivierung oder die shellzombie-Statusänderung.
* Ab Visual Studio 2017 Update 3 beginnen wir auch mit der Überwachung der Zeit, die für Aufrufe im Leerlauf aufgewendet wurde, bevor Shell initialisiert wird. Lange Vorgänge in Leerlauf Handlern bewirken auch eine nicht reagierende IDE und tragen zu einer vom Benutzer erkannten Startzeit bei.

Wir haben ab Visual Studio 2015 viele Features hinzugefügt. Diese Features helfen dabei, das automatische Laden von Paketen zu entfernen. Die-Funktionen verschieben außerdem die Notwendigkeit von Paketen, in spezifischere Fälle geladen zu werden. Zu diesen Fällen zählen Beispiele, in denen Benutzer die Erweiterung verwenden oder die Auswirkungen auf die Erweiterung beim automatischen Laden verringern würden.

Weitere Informationen zu diesen Features finden Sie in den folgenden Dokumenten:

[Regelbasierte UI-Kontexte](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): ein umfangreicheres Regelbasiertes Modul, das um UI-Kontexte aufbaut, ermöglicht Ihnen die Erstellung benutzerdefinierter Kontexte auf der Grundlage von Projekttypen,-Varianten und-Attributen. Benutzerdefinierte Kontexte können zum Laden eines Pakets in spezifischeren Szenarien verwendet werden. Diese spezifischen Szenarien umfassen das vorhanden sein eines Projekts mit einer bestimmten Funktion anstelle des Starts. Benutzerdefinierte Kontexte ermöglichen außerdem das [Binden der Befehls Sichtbarkeit an einen benutzerdefinierten Kontext](visibilityconstraints-element.md) , der auf Projektkomponenten oder anderen verfügbaren Begriffen basiert. Diese Funktion macht das Laden eines Pakets zum Registrieren eines Befehlsstatus-Abfrage Handlers nicht mehr erforderlich.

[Unterstützung für asynchrone](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)Pakete: die neue asyncpackage-Basisklasse in Visual Studio 2015 ermöglicht, dass Visual Studio-Pakete asynchron im Hintergrund geladen werden, wenn das Paket Ladevorgang durch ein Attribut für automatisches Laden oder eine asynchrone Dienst Abfrage angefordert wurde. Dieses Hintergrund Laden ermöglicht der IDE, reaktionsfähig zu bleiben. Die IDE reagiert auch dann, wenn die Erweiterung im Hintergrund initialisiert wird und kritische Szenarien wie das Starten und Laden von Projektmappen nicht beeinträchtigt werden.

[Asynchrone Dienste](how-to-provide-an-asynchronous-visual-studio-service.md): mit Unterstützung für asynchrone Pakete haben wir auch die Unterstützung für das asynchrone Abfragen von Diensten und das Registrieren asynchroner Dienste hinzugefügt. Noch wichtiger ist, dass wir an der Umstellung von Visual Studio-Kerndiensten zur Unterstützung asynchroner Abfragen arbeiten, sodass der Großteil der Arbeit in einer asynchronen Abfrage in Hintergrundthreads auftritt. Scomponentmodel (Visual Studio-MEF-Host) ist einer der wichtigsten Dienste, der nun die asynchrone Abfrage unterstützt, damit Erweiterungen das asynchrone Laden vollständig unterstützen können.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Verringern der Auswirkung von automatisch geladenen Erweiterungen

Wenn ein Paket während des Starts weiterhin automatisch geladen werden muss, ist es wichtig, die während der Paket Initialisierung durchgeführte Arbeit zu minimieren. Wenn Sie die Paket Initialisierungs Arbeit minimieren, verringert sich die Wahrscheinlichkeit, dass die Erweiterung den Startvorgang beeinträchtigt.

Einige Beispiele, die eine aufwändige Paket Initialisierung verursachen können, sind:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Verwendung synchroner Paket Ladevorgang anstelle der asynchronen Paket Auslastung

Da synchrone Pakete standardmäßig auf dem Haupt Thread geladen werden, empfehlen wir Erweiterungs Besitzern, die automatisch geladene Pakete haben, stattdessen die asynchrone Paketbasis Klasse zu verwenden, wie bereits erwähnt. Wenn Sie ein automatisch geladenes Paket ändern, um das asynchrone Laden zu unterstützen, wird es auch einfacher, die anderen Probleme zu beheben.

### <a name="synchronous-filenetwork-io-requests"></a>Synchrone e/a-Anforderungen

Im Idealfall sollten alle synchronen Dateien oder Netzwerk-e/a-Anforderungen im Haupt Thread vermieden werden. Ihre Auswirkung hängt vom Computer Status ab und kann in einigen Fällen über längere Zeiträume hinweg blockiert werden.

Die Verwendung des asynchronen Pakets und der asynchronen e/a-APIs sollte sicherstellen, dass die Paket Initialisierung den Haupt Thread in solchen Fällen nicht blockiert. Benutzer können auch weiterhin mit Visual Studio interagieren, während e/a-Anforderungen im Hintergrund auftreten.

### <a name="early-initialization-of-services-components"></a>Frühe Initialisierung von Diensten, Komponenten

Eines der allgemeinen Muster bei der Paket Initialisierung ist die Initialisierung von Diensten, die von dem Paket oder der Methode verwendet werden `constructor` `initialize` . Obwohl dadurch sichergestellt wird, dass Dienste verwendet werden können, kann es auch unnötige Kosten für das Laden von Paketen verursachen, wenn diese Dienste nicht sofort verwendet werden. Stattdessen sollten solche Dienste bei Bedarf initialisiert werden, um die Arbeit zu minimieren, die bei der Paket Initialisierung durchgeführt wurde.

Für globale Dienste, die von einem Paket bereitgestellt werden, können Sie Methoden verwenden, die `AddService` eine Funktion zum verzögerten Initialisieren des Diensts verwenden, wenn er von einer Komponente angefordert wird. Bei Diensten, die innerhalb des Pakets verwendet werden, können Sie Lazy \<T> oder asynclazy verwenden, \<T> um sicherzustellen, dass Dienste bei der ersten Verwendung initialisiert bzw. abgefragt werden.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Messen der Auswirkung von automatisch geladenen Erweiterungen mithilfe des Aktivitäts Protokolls

Ab Visual Studio 2017 Update 3 enthält das Visual Studio-Aktivitätsprotokoll nun Einträge, die sich auf die Leistung von Paketen beim Starten und Laden von Projektmappen auswirken. Um diese Messungen anzuzeigen, müssen Sie Visual Studio mit/log Switch öffnen und *ActivityLog.xml* Datei öffnen.

Im Aktivitätsprotokoll befinden sich die Einträge unter der Quelle "Visual Studio-Leistung verwalten" und sehen wie im folgenden Beispiel aus:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Dieses Beispiel zeigt, dass ein Paket mit der GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" 2008 MS beim Start von Visual Studio aufgewendet hat. Beachten Sie, dass Visual Studio bei der Berechnung der Auswirkungen eines Pakets die Kosten der obersten Ebene als primär Nummer ansieht, da dies die Einsparungen ist, die Benutzer sehen, wenn Sie die Erweiterung für das Paket deaktivieren.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Messen der Auswirkung von automatisch geladenen Erweiterungen mithilfe von perfview

Obwohl die Code Analyse bei der Identifizierung von Codepfade helfen kann, mit denen die Paket Initialisierung verlangsamt werden kann, können Sie die Ablauf Verfolgung auch verwenden, indem Sie Anwendungen wie perfview verwenden, um die Auswirkungen einer Paket Auslastung in Visual Studio zu verstehen.

Perfview ist ein systemweites Ablaufverfolgungs-Tool. Dieses Tool unterstützt Sie beim besseren Verständnis von Pfaden in einer Anwendung, entweder aufgrund der CPU-Auslastung oder Blockierungs Systemaufrufe. Im folgenden finden Sie ein kurzes Beispiel für die Analyse einer Beispiel Erweiterung mithilfe von perfview, die im [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567)verfügbar ist.

**Beispielcode:**

Dieses Beispiel basiert auf dem unten aufgeführten Beispielcode, der die Groß-/Kleinschreibung bei einigen häufigen Verzögerungen anzeigt:

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**Aufzeichnen einer Ablauf Verfolgung mit perfview:**

Nachdem Sie die Visual Studio-Umgebung mit installierter Erweiterung eingerichtet haben, können Sie eine Ablauf Verfolgung des Starts aufzeichnen, indem Sie perfview öffnen und im Menü **sammeln** das Dialogfeld **sammeln** öffnen.

![perfview-Menü "erfassen"](media/perfview-collect-menu.png)

Mit den Standardoptionen werden Aufruf Listen für die CPU-Auslastung bereitgestellt, aber da wir daran interessiert sind, die Zeit zu blockieren, sollten Sie auch **Thread Zeit** Stapel aktivieren. Wenn die Einstellungen fertig sind, können Sie auf **Sammlung starten** klicken und dann Visual Studio öffnen, nachdem die Aufzeichnung gestartet wurde.

Bevor Sie die Auflistung beendet haben, möchten Sie sicherstellen, dass Visual Studio vollständig initialisiert ist. das Hauptfenster ist vollständig sichtbar, und wenn Ihre Erweiterung Benutzeroberflächen Elemente enthält, die automatisch angezeigt werden, sind Sie ebenfalls sichtbar. Wenn Visual Studio vollständig geladen ist und die Erweiterung initialisiert ist, können Sie die Aufzeichnung beenden, um die Ablauf Verfolgung zu analysieren.

**Analysieren einer Ablauf Verfolgung mit perfview:**

Nachdem die Aufzeichnung abgeschlossen ist, öffnet perfview automatisch die Ablauf Verfolgung und erweitert die Optionen.

In diesem Beispiel interessieren wir uns hauptsächlich für die **Thread Zeit Stapel** Ansicht, die Sie unter **Advanced Group** finden. In dieser Ansicht wird die Gesamtzeit angezeigt, die von einer Methode für einen Thread aufgewendet wurde, einschließlich der CPU-Zeit und der blockierten Zeit, z. b. der Datenträger-e/a

 ![Thread Zeit Stapel](media/perfview-thread-time-stacks.png)

 Beim Öffnen der **Thread Zeit Stapel** Ansicht sollten Sie den **devenv** -Prozess zum Starten der Analyse auswählen.

Perfview enthält eine ausführliche Anleitung zum Lesen von Thread Zeit Stapeln in einem eigenen Hilfe Menü für eine ausführlichere Analyse. In diesem Beispiel möchten wir diese Ansicht weiter filtern, indem wir nur Stapel mit dem Modulnamen des Pakets und dem Start Thread einschließen.

1. Legen Sie **grouppats** auf leeren Text fest, um alle standardmäßig hinzugefügten Gruppierungen zu entfernen.
2. Legen Sie " **incpats** " fest, um einen Teil des Assemblynamens und des Start Threads zusätzlich zum vorhandenen Prozessfilter einzubeziehen. In diesem Fall sollte Sie "Debug" lauten **. Start Thread; Makevsslowextension**.

Nun werden in der Ansicht nur Kosten angezeigt, die den mit der Erweiterung verbundenen Assemblys zugeordnet sind. In dieser Ansicht bezieht sich die Zeit, die in der Spalte **inkl (inklusive Kosten)** des Start Threads aufgeführt ist, auf unsere gefilterte Erweiterung und wirkt sich auf den Start aus.

Im obigen Beispiel würden einige interessante Aufruf Stapel lauten:

1. E/ `System.IO` a mithilfe der Klasse: Obwohl die inklusiven Kosten dieser Frames in der Ablauf Verfolgung möglicherweise nicht zu teuer sind, ist dies eine mögliche Ursache für ein Problem, da die Datei-e/a-Geschwindigkeit von Computer zu Computer variiert.

   ![systemio-Frames](media/perfview-system-io-frames.png)

2. Blockierende Aufrufe, die auf andere asynchrone Aufgaben warten: in diesem Fall würde die inklusive Zeit die Zeit darstellen, zu der der Haupt Thread nach dem Abschluss der asynchronen Arbeit blockiert wird.

   ![Blockieren von Aufrufframes](media/perfview-blocking-call-frames.png)

Eine der anderen Sichten in der Ablauf Verfolgung, die zum Ermitteln der Auswirkung nützlich sein wird, sind die **Bild Lade Stapel**. Sie können dieselben Filter anwenden, die auf die **Thread Zeit Stapel** Ansicht angewendet werden, und alle Assemblys ermitteln, die aufgrund des Codes, der von dem automatisch geladenen Paket ausgeführt wird, geladen wurden.

Es ist wichtig, die Anzahl der geladenen Assemblys in einer Paket Initialisierungs Routine zu minimieren, da jede zusätzliche Assembly zusätzliche Datenträger-e/a-Vorgänge umfasst, die den Start auf langsameren Computern erheblich verlangsamen können.

## <a name="summary"></a>Zusammenfassung

Der Start von Visual Studio war einer der Bereiche, zu denen wir ständig Feedback erhalten. Unser Ziel, wie bereits erwähnt, besteht darin, dass alle Benutzer unabhängig von den installierten Komponenten und Erweiterungen eine konsistente Start Funktion haben. Wir möchten mit Erweiterungs Besitzern zusammenarbeiten, um uns dabei zu unterstützen, dieses Ziel zu erreichen. Der obige Leitfaden sollte hilfreich sein, um die Auswirkungen von Erweiterungen auf den Start zu verstehen und entweder zu vermeiden, dass Sie automatisch geladen oder geladen werden müssen, um die Auswirkungen auf die Benutzerproduktivität zu minimieren.
