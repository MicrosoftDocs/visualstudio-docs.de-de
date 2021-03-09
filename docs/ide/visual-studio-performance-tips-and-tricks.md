---
title: Tipps zum Verbessern der Leistung
description: Hier erfahren Sie, wie Sie nicht verwendete Visual Studio-Features optimieren, um die Leistung zu verbessern.
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e2187426fbd2e8892d41672c1cf682ed0b93592
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683762"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Tipps und Tricks für die Leistung von Visual Studio

Diese die Leistung von Visual Studio betreffenden Empfehlungen sind für Situationen mit wenig Arbeitsspeicher gedacht, die selten auftreten. In solchen Fällen können Sie bestimmte Funktionen von Visual Studio optimieren, die zu dem Zeitpunkt wahrscheinlich nicht verwendet werden. Die folgenden Tipps sind nicht als allgemeine Empfehlungen gedacht.

> [!NOTE]
> Wenn Sie aufgrund von Speicherproblemen Probleme mit dem Produkt haben, informieren Sie uns über das [Feedbacktool](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="use-a-64-bit-os"></a>Verwenden eines 64-Bit-Betriebssystems

Wenn Sie Ihr System von einer 32-Bit-Version von Windows auf eine 64-Bit-Version aktualisieren, erweitern Sie die Menge des für Visual Studio verfügbaren virtuellen Arbeitsspeichers von 2 auf 4 GB. Dadurch kann Visual Studio erheblich größere Workloads verarbeiten, obwohl es sich um einen 32-Bit-Prozess handelt.

Weitere Informationen finden Sie unter [Speicherlimits](/windows/desktop/Memory/memory-limits-for-windows-releases) und [Use /LARGEADDRESSAWARE on 64-Bit Windows (Verwenden von „/LARGEADDRESSAWARE“ unter 64-Bit Windows)](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="disable-automatic-file-restore"></a>Deaktivieren der automatischen Dateiwiederherstellung

Visual Studio öffnet Dokumente, die in der vorherigen Sitzung geöffnet waren, automatisch beim erneuten Öffnen. Dadurch kann sich die Ladezeit einer Projektmappe um bis zu 30 % oder mehr verlängern, je nach geöffnetem Projekttyp und geladenen Dokumenten. Auch Designer wie Windows Forms und XAML sowie einige JavaScript und Typescript-Dateien werden möglicherweise langsam geöffnet.

Visual Studio benachrichtigt Sie in einer gelben Leiste, wenn die automatische Wiederherstellung dazu führt, dass eine Projektmappe deutlich langsamer geladen wird. Die automatische Dateiwiederherstellung lässt sich wie folgt deaktivieren:

1. Klicken Sie in der Menüleiste auf **Extras** > **Optionen**, um das Dialogfeld **Optionen** zu öffnen.

1. Deaktivieren Sie auf der Seite **Projects and Solution** (Projekte und Projektmappen)  > **Allgemein** das Kontrollkästchen **Reopen documents on solution load** (Dokumente beim Laden der Projektmappe erneut öffnen).

Wenn Sie die automatische Dateiwiederherstellung deaktivieren, können Sie mit einem der [Gehe zu](../ide/go-to.md)-Befehlen schnell zu Dateien navigieren, die Sie öffnen möchten.

- Für die allgemeine **Gehe zu**-Funktionalität klicken Sie auf **Bearbeiten** > **Gehe zu** > **Gehe zu allen**, oder drücken Sie **STRG**+**T**.

- Wechseln Sie in einer Projektmappe direkt zum Speicherort der letzten Bearbeitung, indem Sie auf **Bearbeiten** > **Gehe zu** > **Zum Speicherort der letzten Bearbeitung wechseln** bzw. **STRG**+**UMSCHALT**+**RÜCK** drücken.

- Verwenden Sie **Go To Recent File** (Zur zuletzt besuchten Datei wechseln), um eine Liste der zuletzt besuchten Dateien in einer Projektmappe anzuzeigen. Wählen Sie **Bearbeiten** > **Gehe zu** > **Go To Recent File** (Gehe zur zuletzt bearbeiteten Datei), oder drücken Sie **STRG**+**1**, **STRG**+**R**.

## <a name="configure-debugging-options"></a>Konfigurieren von Debugoptionen

Wenn Sie in der Regel während des Debuggens von Sitzungen über nicht ausreichend Arbeitsspeicher verfügen, können Sie die Leistung optimieren, indem Sie mindestens eine Konfigurationsänderung vornehmen.

- **Nur meinen Code aktivieren**

    Die einfachste Optimierung ist die Aktivierung der Funktion **Nur eigenen Code**, die nur Symbole für das Projekt lädt. Die Aktivierung dieser Funktion zu erheblichen Arbeitsspeichereinsparungen für das Debuggen von verwalteten Anwendungen (.NET) führen. Diese Option ist in einigen Projekttypen bereits standardmäßig aktiviert.

    Um **Nur mein Code** zu aktivieren, wählen Sie **Extras** > **Optionen** > **Debuggen** > **Allgemein** und anschließend **Nur meinen Code aktivieren** aus.

- **Angeben der zu ladenden Symbole**

    Für das native Debuggen ist das Laden von Symboldateien (*PDB*) im Hinblick auf die Arbeitsspeicherressourcen teuer. Sie können Ihre Debugsymbol-Einstellungen konfigurieren, um Arbeitsspeicher zu sparen. In der Regel konfigurieren Sie die Projektmappe so, dass nur Module aus Ihrem Projekt geladen werden.

    Wählen Sie zum Laden von Symbolen **Extras** > **Optionen** > **Debuggen** > **Symbole** aus.

    Legen Sie die Optionen auf **Nur angegebene Module** anstelle von **Alle Module** fest, und geben Sie die Module an, die geladen werden sollen. Während des Debuggens können Sie im Fenster **Module** auch mit der rechten Maustaste auf bestimmte Module klicken, um ein Modul in den Symbolladeborgang explizit aufzunehmen. (Wählen Sie zum Öffnen des Fensters während des Debuggens **Debuggen** > **Windows** > **Module** aus.)

    Weitere Informationen finden Sie unter [Understand symbol files (Grundlegendes zu Symboldateien)](?view=vs-2019&preserve-view=true).

- **Deaktivieren von Diagnosetools**

    Es wird empfohlen, die CPU-Profilerstellung nach ihrer Verwendung zu deaktivieren. Diese Funktion kann große Mengen von Ressourcen belegen. Sobald die CPU-Profilerstellung aktiviert ist, wird dieser Status in allen nachfolgenden Debugsitzungen beibehalten. Daher muss sie nach Beendigung explizit deaktiviert werden. Sie können einige Ressourcen speichern, indem Sie während des Debuggens die Diagnosetools deaktivieren, sollten Sie diese Funktionen nicht bereitstellen müssen.

    Um die **Diagnosetools** zu deaktivieren, starten Sie eine Debugsitzung, wählen Sie **Extras** > **Optionen** > **Debuggen** > **Allgemein** aus, und deaktivieren Sie dann die Option **Diagnosetools während des Debuggens aktivieren**.

    Weitere Informationen finden Sie unter [Profilerstellungstools](../profiling/profiling-feature-tour.md).

## <a name="disable-tools-and-extensions"></a>Deaktivieren von Tools und Erweiterungen

Einige Tools oder Erweiterungen können ausgeschaltet werden, um die Leistung zu verbessern.

> [!TIP]
> Häufig können Sie Leistungsprobleme isolieren, indem Sie Erweiterungen eine nach der anderen deaktivieren und die Leistung immer wieder überprüfen.

### <a name="managed-language-service-roslyn"></a>Dienste für verwaltete Sprachen (Roslyn)

Informationen zu Leistungsüberlegungen hinsichtlich der .NET Compiler Platform („Roslyn“) finden Sie unter [Performance considerations for large solutions (Überlegungen zur Leistung bei großen Projektmappen)](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md).

- **Deaktivieren der vollständigen Projektmappenanalyse**

    Visual Studio analysiert Ihre gesamte Projektmappe, um eine alle Fehler vor dem Erstellen eines Builds zu erfassen. Diese Funktion ist nützlich, um Fehler so früh wie möglich zu identifizieren. Allerdings kann diese Funktion bei großen Projektmappen beträchtliche Arbeitsspeicherressourcen konsumieren. Wenn Sie Arbeitsspeichermangel oder ähnliche Probleme haben, können Sie diese Funktion deaktivieren, um diese Ressourcen freizugeben. Diese Option ist für Visual Basic standardmäßig aktiviert und für C# deaktiviert.

    Klicken Sie zum Deaktivieren der **vollständigen Projektmappenanalyse** auf **Extras** > **Optionen** > **Text-Editor**, und wählen Sie **Visual Basic** oder **C#** aus. Klicken Sie dann auf **Erweitert**, und deaktivieren das Kontrollkästchen **Enable full solution analysis** (Vollständige Projektmappenanalyse aktivieren).

- **Deaktivieren von CodeLens**

    Visual Studio führt eine Aufgabe **Alle Verweise suchen** für jede Methode aus, während sie angezeigt wird. CodeLens bietet Funktionen wie die Inlineanzeige der Anzahl der Verweise. Die Arbeit wird in einem separaten Prozess ausgeführt, z.B. *ServiceHub.RoslynCodeAnalysisService32*. In großen Projektmappen oder auf Systemen mit eingeschränkten Ressourcen kann diese Funktion entscheidenden Einfluss auf die Leistung haben. Wenn beim Laden von großen Projektmappen auf einem 4-GB-Computer beispielsweise Probleme mit dem Arbeitsspeicher auftreten oder wenn es bei diesem Prozess zu hoher CPU-Auslastung kommt, können Sie CodeLens deaktivieren, um Ressourcen freizugeben.

    Um **CodeLens** zu deaktivieren, wählen Sie **Extras** > **Optionen** > **Text-Editor** > **Alle Sprachen** > **CodeLens** aus, und deaktivieren Sie das Feature.

    > [!NOTE]
    > CodeLens ist in den Visual Studio-Editionen „Professional“ und „Enterprise“ verfügbar.

### <a name="other-tools-and-extensions"></a>Andere Tools und Erweiterungen

- **Deaktivieren von Erweiterungen**

    Erweiterungen sind zusätzliche, zu Visual Studio hinzugefügte Softwarekomponenten, die neue Funktionalität bereitstellen oder vorhandene Funktionalität erweitern. Erweiterungen können häufig eine Quelle von Problemen mit Arbeitsspeicherressourcen sein. Wenn bei Ihnen Arbeitsspeicherprobleme auftreten, deaktivieren Sie die Erweiterungen nacheinander, um die Auswirkungen auf das Szenario oder den Workflow zu beobachten.

   ::: moniker range="vs-2017"

    Um Erweiterungen zu deaktivieren, wechseln Sie zu **Tools** > **Erweiterungen und Updates**, und deaktivieren eine bestimmte Erweiterung.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

    Um Erweiterungen zu deaktivieren, deaktivieren Sie unter **Erweiterungen** > **Erweiterungen verwalten** eine bestimmte Erweiterung.

   ::: moniker-end

- **Deaktivieren des Zuordnungsmodus**

    Im [**Zuordnungsmodus**](how-to-track-your-code-by-customizing-the-scrollbar.md#display-modes) werden Codezeilen als Miniaturansicht auf der Scrollleiste angezeigt. Der Zuordnungsmodus ist standardmäßig aktiviert.

    Um den Zuordnungsmodus zu deaktivieren, navigieren Sie zu **Extras** > **Optionen** > **Text-Editor** > **Alle Sprachen** > **Scrollleisten**, und deaktivieren Sie im Abschnitt **Verhalten** die Option **Zuordnungsmodus für vertikale Scrollleiste verwenden**.

- **Deaktivieren des Zeilenumbruchs**

    [**Zeilenumbruch**](./reference/how-to-manage-word-wrap-in-the-editor.md) zeigt den Teil einer langen Zeilean, der über die aktuelle Breite des Code-Editor-Fensters hinausgeht. Zeilenumbruch ist standardmäßig aktiviert.

    Um den Zeilenumbruch für ein Projekt zu deaktivieren, an dem Sie aktuelle arbeiten, navigieren Sie zu **Bearbeiten** > **Erweitert** > **Zeilenumbruch**. (Sie können diese Einstellung mithilfe derselben Menübefehle umschalten.)

    Um Zeilenumbruch für alle Projekte zu deaktivieren, navigieren Sie zu **Extras** > **Optionen** > **Allgemein** > **Text-Editor** > **Alle Sprachen** > **Allgemein**, und deaktivieren Sie dann im Abschnitt **Einstellungen** die Option **Zeilenumbruch**.

- **Deaktivieren des XAML-Designers**

    Der XAML-Designer ist standardmäßig aktiviert. Es werden aber nur Ressourcen belegt, wenn Sie eine *XAML*-Datei öffnen. Wenn Sie mit XAML-Dateien arbeiten, den Designer aber nicht verwenden möchten, deaktivieren Sie diese Funktion, um Arbeitsspeicher freizugeben.

    Um den XAML-Designer zu deaktivieren, navigieren Sie zu **Extras** > **Optionen** > **XAML-Designer** > **XAML-Designer aktivieren**, und deaktivieren Sie die Option.

- **Entfernen von Workloads**

    Sie können den Visual Studio-Installer verwenden, um Workloads zu entfernen, die nicht mehr verwendet werden. Dadurch kann Ihre Start- und Laufzeitkosten zu optimieren, indem Pakete und Assemblys übersprungen werden, die nicht mehr benötigt werden.

- **Hinzufügen nicht nachverfolgter Dateien zur lokalen GITIGNORE-Datei**

    Visual Studio führt den Git-Befehl `git status` mit nicht verfolgten Dateien aus, um ein nahtloses Benutzererlebnis zu gewährleisten, wenn neue Dateien in ein Repository hinzugefügt werden. Bei einer großen Anzahl nicht verfolgter Dateien kann `git status` sehr viel zusätzlichen Arbeitsspeicher belegen. Um diese Dateien zu ignorieren und die Leistung von `git status` zu verbessern, können Sie diese Dateien oder Ordner zu Ihrer lokalen GITIGNORE-Datei hinzufügen. Wechseln Sie zum Zugriff auf die Datei zu **Git** > **Einstellungen** > **Git-Repositoryeinstellungen**. Klicken Sie anschließend im Abschnitt **Git-Dateien** auf **Hinzufügen**, um eine GITIGNORE-Datei zu erstellen, oder klicken Sie auf **Bearbeiten**, wenn Sie bereits über eine solche Datei verfügen.

## <a name="force-a-garbage-collection"></a>Erzwingen einer Garbage Collection

Die CLR verwendet eine Arbeitsspeicherverwaltungssystem mit Garbage Collection. In diesem System wird manchmal Speicher von Objekten belegt, die nicht mehr benötigt werden. Dieser Status ist vorübergehend. Der Garbage Collector gibt diesen Arbeitsspeicher basierend auf dessen Leistungs- und Ressourcenverwendungsheuristik frei. Sie können die CLR mit einem Hotkey in Visual Studio zwingen, nicht verwendeten Arbeitsspeicher zu sammeln. Wenn die Menge an nicht verwendeten Objekten bereits sehr groß ist und Sie eine automatische Speicherbereinigung erzwingen, sollten Sie im **Task-Manager** sehen können, wie die Arbeitsspeicherauslastung des Prozesses *devenv.exe* abnimmt. Es ist aber nur selten notwendig, diese Methode anzuwenden. Nachdem jedoch ein teurer Vorgang (z.B. ein vollständiger Build, eine Debugsitzung oder ein Ereignis in einer offenen Projektmappe) abgeschlossen wurde, kann Ihnen die Methode dabei helfen zu bestimmen, wie viel Arbeitsspeicher tatsächlich vom Prozess verwendet wird. Da Visual Studio (verwaltetes & nativ) kombiniert wird, ist es gelegentlich möglich, dass die native Zuweisung und der Garbage Collector um begrenzte Arbeitsspeicherressourcen konkurrieren. Bei hoher Arbeitsspeicherauslastung kann es hilfreich sein, die Ausführung des Garbage Collectors zu erzwingen.

Um eine automatische Speicherbereinigung zu erzwingen, verwenden Sie den Hotkey: **STRG**+**ALT**+**UMSCHALTTASTE**+**F12**, **STRG**+**ALT**+**UMSCHALTTASTE**+**F12** (zweimal drücken).

Wenn das Erzwingen der Garbage Collection zur zuverlässigen Funktion Ihres Szenarios führt, übermitteln Sie uns einen Bericht über die Visual Studio-Feedbacktool, denn dieses Verhalten ist wahrscheinlich ein Fehler.

Eine ausführliche Beschreibung des CLR-Garbage Collectors finden Sie unter [Fundamentals of Garbage Collection (Grundlagen der Garbage Collection)](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Weitere Informationen

- [Optimieren der Visual Studio-Leistung](../ide/optimize-visual-studio-performance.md)
- [Load solutions faster with Visual Studio 2017 version 15.6 (Schnelleres Laden großer Projektmappen in Visual Studio 2017-Version 15.6)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)