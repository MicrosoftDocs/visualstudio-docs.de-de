---
title: Neues in Visual Studio 2017
titleSuffix: ''
description: Informationen zu den neuen Features in Visual Studio 2017
ms.date: 12/18/2018
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 3b2654622f9cb4de05068b58570ab1494c2a3f34
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960649"
---
# <a name="whats-new-in-visual-studio-2017"></a>Neues in Visual Studio 2017

**Für [Release 15.9](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017) aktualisiert**

Möchten Sie von einer vorherigen Version von Visual Studio aktualisieren? Visual Studio 2017 bietet Ihnen folgende Vorteile: Beispiellose Produktivität für alle Entwickler, Apps und Plattformen. Verwenden Sie Visual Studio 2017 zum Entwickeln von Apps für Android, iOS, Windows, Linux, das Web und die Cloud. Schnelles Codieren, einfaches Debuggen und einfache Diagnose, häufige Tests und zuverlässige Releases. Sie können Visual Studio auch durch Erstellen eigener Erweiterungen erweitern und anpassen. Verwenden Sie die Versionskontrolle, agile Prozesse, und steigern Sie die Effizienz bei der Zusammenarbeit mit diesem Release!

>[!div class="button"]
>[Herunterladen von Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

Dies ist eine allgemeine Zusammenfassung aller Änderungen, die seit der vorherigen Version, Visual Studio 2015, vorgenommen wurden:

* **[Neu definierte Grundlagen](#redefined-fundamentals)** Mit der neuen Setupfunktionalität können Sie generell schneller installieren und das, was Sie wünschen, dann installieren, wenn Sie es benötigen.
* **[Leistung und Produktivität](#performance-and-productivity)** Wir haben uns auf neue, moderne Bereitstellungsfunktionen für Mobilgeräte sowie Cloud- und Desktopcomputer konzentriert. Außerdem startet Visual Studio schneller, reagiert besser und benötigt weniger Arbeitsspeicher.
* **[Cloud-App-Entwicklung mit Azure](#cloud-app-development-with-azure)** Eine integrierte Sammlung von Azure-Tools, die Ihnen das einfache Entwickeln von primär auf die Cloud ausgelegten Apps in Microsoft Azure ermöglichen. Visual Studio vereinfacht das Konfigurieren, Erstellen, Debuggen, Packen und Bereitstellen von Apps und Diensten in Azure.
* **[Windows App-Entwicklung](#windows-app-development)** Verwenden Sie die UWP-Vorlagen in Visual Studio 2017, um ein einzelnes Projekt für alle Windows 10-Geräte zu erstellen: PC, Tablet, Smartphone, Xbox, HoloLens, Surface Hub usw.
* **[Entwicklung mobiler Apps](#mobile-app-development)** Sie können mit Xamarin in kürzester Zeit Neuerungen einführen und Ergebnisse erzielen. Mit dieser Entwicklungsumgebung werden Ihre Anforderungen für mobile, plattformübergreifende Anwendungen vereinheitlicht und auf eine einzige grundlegende Codebasis und einige wenige erforderliche Fertigkeiten eingeschränkt.
* **[Plattformübergreifende Entwicklung](#cross-platform-development)** Übermitteln Sie Software problemlos an alle Zielplattform. Weiten Sie DevOps-Prozesse mithilfe von Redgate Data Tools auf SQL Server aus, und automatisieren Sie die sichere Datenbankbereitstellung aus Visual Studio. Verwenden Sie alternativ .NET Core, um Apps und Bibliotheken zu schreiben, die unverändert unter Windows, Linux und macOS ausgeführt werden.
* **[Spieleentwicklung](#games-development)** Mithilfe der Visual Studio-Tools für Unity (VSTU) können Sie Visual Studio zum Schreiben von Spiel- und Editorskripts in C# verwenden und dann den leistungsfähigen Debugger zum Suchen und Beheben von Fehlern nutzen.
* **[KI-Entwicklung](#ai-development)** Mit Visual Studio Tools for AI können Sie die Produktivitätsfeatures von Visual Studio verwenden, um KI-Innovationen zu beschleunigen. Erstellen und testen Sie Deep Learning- und KI-Lösungen, die sich nahtlos in Azure Machine Learning integrieren lassen und stabile ML-Experimentieren-Funktionen ermöglichen, und stellen Sie diese Lösungen bereit.

> [!NOTE]
> Eine vollständige Liste der neuen Features und Funktionen in Visual Studio 2017 finden Sie unter [Aktuelle Versionsanmerkungen](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017). Weitere Informationen zu zukünftig angebotenen Features finden Sie in den [Anmerkungen zur Vorschauversion](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017).

Im Anschluss finden Sie ausführlichere Informationen zu einigen der wichtigsten Verbesserungen und neuen Funktionen in Visual Studio 2017.

## <a name="redefined-fundamentals"></a>Neu definierte Grundlagen

### <a name="a-new-setup-experience"></a>Ein neues Setuperlebnis

In Visual Studio können Sie jetzt einfacher und schneller nur die Funktionen installieren, die Sie benötigen, wenn Sie sie benötigen. Und es lässt sich auch sauber wieder deinstallieren.

Die wichtigste Änderung beim Installieren von Visual Studio ist die neue Setupoberfläche. Auf der Registerkarte **Arbeitsauslastungen** sehen Sie gruppierte Installationsoptionen, die allgemeine Frameworks, Sprachen und Plattformen darstellen. Von der .NET-Desktopentwicklung bis zur C++-Anwendungsentwicklung unter Windows, Linux und iOS ist alles abgedeckt.

Wählen Sie die benötigten Arbeitsauslastungen, und ändern Sie sie bei Bedarf.

![Visual Studio 2017-Setupdialogfeld](../install/media/install-visual-studio-enterprise.png)

Und Sie verfügen ferner über Optionen, um die Installation zu optimieren:

* Möchten Sie Ihre Komponenten lieber selbst aussuchen, statt Arbeitsauslastungen zu verwenden? Wählen Sie im Installationsprogramm die Registerkarte **Einzelne Komponenten** aus.
* Möchten Sie Sprachpakete installieren, ohne zugleich auch die eingestellte Sprache für Windows ändern zu müssen? Wählen Sie die Registerkarte **Sprachpakete** des Installationsprogramms aus.
* **Neues in 15.7:** Soll der Speicherort für die Installation von Visual Studio geändert werden? Wählen Sie die Registerkarte **Installationsoptionen** des Installationsprogramms aus.

Weitere Informationen zur neuen Installationsoberfläche sowie ausführliche Anweisungen, die Sie durch die Installation führen, finden Sie auf der Seite [Installieren von Visual Studio](../install/install-visual-studio.md).

### <a name="a-focus-on-accessibility"></a>Konzentration auf Barrierefreiheit

**In Version 15.3** wurden über 1.700 gezielte Fixes vorgenommen, um die Kompatibilität zwischen Visual Studio und den Hilfstechnologien zu verbessern, die viele Kunden verwenden. Es gibt Dutzende von Szenarien, die kompatibler mit Bildschirmsprachausgaben, Designs mit hohem Kontrast und anderen Hilfstechnologien sind als jemals zuvor. Debugger, Editor und Shell wurden ebenfalls allesamt erheblich verbessert.

Weitere Informationen finden Sie im Blogbeitrag [Accessibility improvements in Visual Studio 2017 version 15.3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Verbesserungen der Barrierefreiheit in Visual Studio 2017 [Version 15.3]).

## <a name="performance-and-productivity"></a>Leistung und Produktivität

### <a name="sign-in-across-multiple-accounts"></a>Anmelden mit mehreren Konten

Wir haben in Visual Studio einen neuen Identitätsdienst eingeführt, der Ihnen die übergreifende Verwendung von Benutzerkonten in Team Explorer, Azure-Tools, Microsoft Store-Veröffentlichungen usw. ermöglicht.

Sie auch länger angemeldet bleiben. Visual Studio wird Sie nicht alle 12 Stunden auffordern, sich anzumelden. Weitere Informationen finden Sie im Blogbeitrag [Fewer Visual Studio Sign-in Prompts (Weniger Anmeldeaufforderungen in Visual Studio)](https://devblogs.microsoft.com/visualstudio/fewer-visual-studio-sign-in-prompts/).

### <a name="start-visual-studio-faster"></a>Schnellerer Start von Visual Studio

Das neue Leistungscenter von Visual Studio kann Ihnen helfen, die IDE-Startzeit zu optimieren. Im Leistungscenter werden alle Erweiterungen und Toolfenster aufgelistet, die den Start der IDE verlangsamen könnten. Sie können es zum Verbessern der Startleistung verwenden, indem Sie festlegen, wann Erweiterungen gestartet werden oder ob bestimmte Toolfenster beim Start geöffnet sein sollen.

### <a name="faster-on-demand-loading-of-extensions"></a>Schnelleres Laden von Erweiterungen bei Bedarf

Visual Studio verschiebt seine Erweiterungen (und arbeitet auch mit Erweiterungen von Drittanbietern zusammen), damit sie erst bei Bedarf geladen werden, statt gleich beim IDE-Start. Möchten Sie wissen, welche Erweiterungen sich auf den Start, das Laden von Projektmappen und die Leistung bei der Eingabe auswirken? Sie finden diese Informationen unter **Hilfe** > **Visual Studio-Leistung verwalten**.

  ![Dialogfeld „Optionen“ in Visual Studio 2017](media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Verwalten von Erweiterungen mit dem Roaming-Erweiterungs-Manager

Es ist einfacher, jede Entwicklungsumgebung mit Ihren bevorzugten Erweiterungen einzurichten, wenn Sie sich bei Visual Studio anmelden. Der neue Roaming-Erweiterungs-Manager verfolgt alle Ihre bevorzugten Erweiterungen nach, indem er eine synchronisierte Liste in der Cloud erstellt.

Um eine Liste Ihrer Erweiterungen in Visual Studio anzuzeigen, klicken Sie auf **Extras** > **Erweiterungen und Updates**, und klicken Sie dann auf den **Roaming-Erweiterungs-Manager**.

![Visual Studio 2017: Dialogfeld „Erweiterungen und Updates“](media/vs2017ide-extensions-and-updates.png)

Der Roaming-Erweiterungs-Manager verfolgt alle von Ihnen installierten Erweiterungen nach, Sie können aber wählen, welche Ihrer Roamingliste hinzugefügt werden sollen.

![Visual Studio 2017 – Roaming Extensions Manager](media/vs2017ide-RoamingExtensionManager.png)

Wenn Sie den Roaming-Erweiterungs-Manager verwenden, werden Sie drei Symboltypen in Ihrer Liste bemerken:

* ![Symbol für „Roaming erfolgt“](media/vs2017ide-roamedicon.png) **_Roaming erfolgt_**: Eine Erweiterung, die in Ihrer Roamingliste enthalten, auf Ihrem Computer jedoch nicht installiert ist.
  (Erweiterungen dieses Typs können Sie mithilfe der Schaltfläche **Download** herunterladen.)
* ![Symbol für „Roaming und Installation erfolgt“](media/vs2017ide-roamedinstalledicon.png) **_Roaming und Installation erfolgt_**: Alle Erweiterungen, die in dieser Roamingliste enthalten und in der Entwicklungsumgebung installiert sind.
  (Wenn Sie sich gegen das Roaming entscheiden, können Sie zum Entfernen die Schaltfläche **Roaming beenden** verwenden.)
* ![Symbol für „Installiert“](media/vs2017ide-installedicon.png) **_Installiert_**: Alle Erweiterungen, die in dieser Umgebung installiert, aber nicht in der Roamingliste enthalten sind.
  (Sie können der Roamingliste Erweiterungen mithilfe der Schaltfläche **Roaming starten** hinzufügen.)

Jede Erweiterung, die Sie herunterladen, während Sie angemeldet sind, wird zu Ihrer Liste als **Roamed & Installed** (Roaming und Installation) hinzugefügt. Die Erweiterung wird dann zu Ihrer Roamingliste hinzugefügt, über die Sie auf diese über Ihren Computer zugreifen können.

### <a name="experience-live-unit-testing"></a>Entdecken Sie Live Unit Testing

In Visual Studio Enterprise 2017 liefern Ihnen Livekomponententests Livekomponententest-Ergebnisse und Codeabdeckung im Editor währende der Codierung. Dies funktioniert mit C#- und Visual Basic-Projekten für .NET Framework und .NET Core und unterstützt Testframeworks von MSTest, xUnit und NUnit.

![Live Unit Testing](media/lut-codewindow.png)

Weitere Informationen finden Sie unter [Introducing Live Unit Testing (Einführung in Live Unit Testing)](../test/live-unit-testing-intro.md). Eine Liste der neuen Funktionen, die in jedem Release von Visual Studio Enterprise 2017 hinzugefügt werden, finden Sie unter [What's new in Live Unit Testing (Neuerungen in Live Unit Testing)](../test/live-unit-testing-whats-new.md).

### <a name="set-up-a-cicd-pipeline"></a>Einrichten einer CI/CD-Pipeline

#### <a name="automated-testing"></a>Automatisiertes Testen

Automatisiertes Testen ist ein wesentlicher Bestandteil aller DevOps-Pipelines. Damit können Sie konsistent und zuverlässig testen und Ihre Projektmappe in viel kürzeren Abständen freigeben. CI/CD-Flüsse (Continuous Integration und Continuous Delivery) können Prozesse effektiver gestalten.

Weitere Informationen zu automatisierten Tests finden Sie im Blogbeitrag [CI/CD pipeline for automated tests in DevOps](/archive/blogs/visualstudioalmrangers/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently) (CI/CD-Pipeline für automatisierte Tests in DevOps).

Weitere Informationen zu Neuigkeiten in der DevLabs-Erweiterung [Continuous Delivery-Tools for Visual Studio (Continuous Delivery-Tools für Visual Studio)](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) finden Sie in dem Blogbeitrag [Committing with Confidence: Commit Time Code Quality (Commit mit Vertrauen: Commit ausführen mit Zeitcodequalität)](https://devblogs.microsoft.com/visualstudio/committing-with-confidence-getting-code-quality-information-at-commit-time/).

### <a name="visual-studio-ide-enhancements"></a>Verbesserungen der Visual Studio-IDE

#### <a name="multi-caret-editing"></a>Bearbeiten mit mehreren Caretzeichen

**Neues in 15.8:** Das gleichzeitige Bearbeiten von mehreren Stellen in einer Datei ist jetzt ganz einfach. Erstellen Sie zunächst an mehreren Stellen in einer Datei Einfügemarken und Auswahlpunkte. Nehmen Sie dann mithilfe des Features zum Bearbeiten mit mehreren Caretzeichen dieselbe Änderung an zwei oder mehr Stellen gleichzeitig vor.

Weitere Informationen finden Sie im Abschnitt [Multi-caret selection](finding-and-replacing-text.md#multi-caret-selection) (Auswählen mehrerer Caretzeichen) auf der Seite [Suchen und Ersetzen von Text](finding-and-replacing-text.md).

#### <a name="keep-keybinding-profiles-consistent"></a>Konsistente Tastenzuordnungsprofile

**Neues in 15.8:** Nun können Sie darauf achten, dass Ihre Tastenzuordnungen mit den zwei neuen Tastaturprofilen konsistent bleiben: Visual Studio Code und ReSharper (Visual Studio). Diese Schemas finden Sie unter **Extras** > **Optionen** > **Allgemein** > **Tastatur** und über das oberste Dropdownmenü.

  ![Neue Tastenzuordnungsprofile für Visual Studio Code und ReSharper](media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>Verwenden neuer Refactorings

Als Refactoring wird der Prozess bezeichnet, Ihren Code zu verbessern, nachdem dieser geschrieben wurde. Durch Refactoring wird die interne Struktur des Codes geändert, ohne dessen Verhalten zu ändern. Neue Refactorings werden häufig hinzugefügt. Im Folgenden sind einige davon aufgeführt:

* Hinzufügen von Parametern (aus CallSite)
* Generieren von Überschreibungen
* Hinzufügen benannter Argumente
* NULL-Überprüfung für Parameter hinzufügen
* Einfügen von Zifferntrennzeichen in Literale
* Ändern der Basis für numerische Literale (z.B. von hexadezimal zu binär)
* Konvertieren von if-to-switch
* Nicht verwendete Variablen entfernen

Weitere Informationen finden Sie unter [Schnelle Aktionen](common-quick-actions.md).

#### <a name="interact-with-git"></a>Interaktion mit Git

Wenn Sie in Visual Studio an einem Projekt arbeiten, können Sie Ihren Code für einen Git-Dienst einrichten, ihn schnell dahin übertragen und dort veröffentlichen. Sie können Ihre Git-Repositorys auch mit Menüklicks auf Schaltflächen in der unteren rechten Ecke der IDE verwalten.

![Interaktion von Visual Studio 2017 mit dem Git-Dialogfeld](media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>Benutzerfreundlichere Navigationssteuerelemente

Wir haben die Benutzerfreundlichkeit der Navigation verbessert, sodass Sie mit größerer Sicherheit und weniger Ablenkung von A nach B gelangen.

* **Neues in 15.4:** **Gehe zu Definition** (**STRG**+**Klicken** oder **F12**) &ndash; Mausbenutzer können einfacher zu der Definition eines Members navigieren, indem sie **STRG** drücken und dann auf das Member klicken. Durch das Drücken von **STRG** und das Zeigen auf ein Codesymbol mit der Maus wird dieses unterstrichen und in einen Link umgewandelt. Weitere Informationen finden Sie unter [Go To Definition and Peek Definition (Gehe zu Definition und Definition einsehen)](go-to-and-peek-definition.md).

* **Zur Implementierung wechseln** (**Strg**+**F12**) &ndash; Navigieren Sie von jedem Basistyp oder Member zu dessen verschiedenen Implementierungen.

* **Go To All** (**Strg**+**T** oder **Strg**+ **,** ) &ndash; ( Gehe zu allen) Navigieren Sie direkt zu jeder beliebigen Datei-/Typ-/Member-/Symboldeklaration. Sie können die Ergebnisliste filtern oder die Abfragesyntax verwenden (z.B. „f Suchbegriff“ für Dateien, „t Suchbegriff“ für Typen usw.).

  ![Verbesserte Option „Gehe zu allen“](media/vs2017ide-navigation-go-to.png)

* **Alle Verweise suchen** (**Umschalt**+**F12**) &ndash; Mit Syntaxfarbgebung können Sie „Alle Verweise suchen“-Ergebnisse nach einer Kombination aus Projekt, Definition und Pfad gruppieren. Sie können auch Ergebnisse „sperren“, damit Sie die Suche nach anderen Verweisen fortsetzen können, ohne die ursprünglichen Ergebnisse zu verlieren.

  ![Neues Tool „Alle Verweise suchen“](media/vs2017ide-find-all-references.png)

* **Strukturschnellansicht**: Punktierte, graue, vertikale Linien (Einzugsführungslinien) dienen nun als Orientierungshilfen im Code, um Kontext innerhalb Ihres Bezugssystems bereitzustellen. Vielleicht kennen Sie sie von den beliebten Produktivitäts-Power Tools. Damit können Sie jederzeit ohne zu scrollen visuell darstellen und ermitteln, in welchem Codeblock Sie sich befinden. Wenn Sie den Mauszeiger über die Zeilen bewegen, werden QuickInfos angezeigt, die Ihnen die Öffnung dieses Blocks und seine übergeordneten Elemente anzeigen. Dies ist sowohl für alle Sprachen verfügbar, die über TextMate-Grammatiken unterstützt werden, als auch für C#, Visual Basic und XAML.

  ![Strukturschnellansicht in Visual Studio 2017](media/vsIDE-StructureVisualizer.png)

Weitere Informationen zu den neuen Produktivitätsfeatures finden Sie im Blogbeitrag [Announcing Visual Studio 2017: Productivity, Performance, and Partners](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-productivity-performance-and-partners/) (Ankündigung von Visual Studio 2017: Produktivität, Leistung und Partner).

### <a name="visual-c"></a>Visual C++

Sie werden eine Reihe von Verbesserungen in Visual Studio bemerken, z.B. die Verteilung von C++ Core Guidelines mit Visual Studio, das Update des Compilers durch verbesserte Unterstützung für C++11- und C++-Funktionen und Hinzufügen und Aktualisieren von Funktionalität in den C++-Bibliotheken. Wir haben auch die Leistung der C++-IDE, die Installation von Arbeitsauslastungen und anderes mehr verbessert.

Wir haben ebenfalls mehr als 250 Fehler und gemeldete Probleme mit dem Compiler und den Tools behoben, von denen viele durch Kunden über die [Community für C++-Entwickler](https://aka.ms/feedback/report?space=62 "Community für C++-Entwickler") übermittelt wurden.

Ausführliche Angaben finden Sie auf der Seite [Neuerungen bei Visual C++ in Visual Studio 2017](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio).

### <a name="debugging-and-diagnostics"></a>Debuggen und Diagnose

#### <a name="run-to-click"></a>Ausführung bis Klick

Nun können Sie leichter während des Debuggens vorwärts springen, ohne einen Haltepunkt festlegen zu müssen, um in der gewünschten Zeile zu stoppen. Wenn Sie im Debugger angehalten werden, klicken Sie einfach auf das Symbol, das neben der Codezeile angezeigt wird. Die nächste Codeausführung wird nun an dieser Zeile anhalten, sobald sie im Codepfad erreicht wird.

![Debuggen in Visual Studio 2017: Ausführung bis Klick](media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>Die neue Ausnahmen-Hilfe

Die neue Ausnahmen-Hilfe hilft Ihnen, Ihre Ausnahmeinformationen auf einen Blick anzeigen. Die Informationen werden in einem kompakten Format mit unmittelbarem Zugriff auf die inneren Ausnahmen angezeigt. Wenn Sie eine NullReferenceException diagnostizieren, können Sie direkt in der Ausnahme-Hilfe schnell sehen, was NULL war.

![Dialogfeld der neuen Ausnahmen-Hilfe in Visual Studio](media/vs2017ide-ExceptionHelper.png)

Weitere Informationen finden Sie im Blogbeitrag [Using the New Exception Helper in Visual Studio (Verwenden der neuen Ausnahmen-Hilfe in Visual Studio)](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/).

#### <a name="snapshots-and-intellitrace-step-back"></a>Momentaufnahmen und das IntelliTrace-Feature „Step-back“

**Neues in Version 15.5**: Das IntelliTrace-Feature „Schritt zurück“ nimmt automatisch bei jedem Breakpoint und Debuggerschritt eine Momentaufnahme Ihrer Anwendung auf. Durch die erfassten Momentaufnahmen können Sie zu vorherigen Haltepunkten oder Schritten zurückkehren und sich den Zustand der Anwendung so anzeigen lassen, wie er zuvor war. Mit dem IntelliTrace-Feature „Step-back“ können Sie Zeit sparen, wenn Sie den vorherigen Zustand der Anwendung anzeigen oder diesen wiederherstellen, aber das Debuggen nicht erneut starten möchten.

Sie können Momentaufnahmen anzeigen und durch diese navigieren, indem Sie die Schaltflächen **Schritt zurück** und **Schritt vorwärts** in der **Debug**-Symbolleiste verwenden. Mit diesen Schaltflächen können Sie durch die Ereignisse navigieren, die in der Registerkarte **Ereignisse** des Fensters **Diagnosetools** angezeigt werden. Wenn Sie mit „Schritt zurück“ oder „Schritt vor“ zu einem Ereignis navigieren, wird das verlaufsbezogene Debuggen für das ausgewählte Ereignis automatisch aktiviert.

![Beispiel für das IntelliTrace-Feature „Step back“ in Visual Studio](../debugger/media/intellitrace-step-back-icons-description.png  "Schaltflächen „Schritt zurück“ und „Schritt vorwärts“")

Weitere Informationen finden Sie auf der Seite [View snapshots using IntelliTrace step-back (Anzeigen von Momentaufnahmen mithilfe des IntelliTrace-Features „Step-back“)](../debugger/view-historical-application-state.md).

### <a name="containerization"></a>Containerisierung

Container bieten eine höhere App-Dichte und niedrigere Bereitstellungskosten sowie eine verbesserte Produktivität und DevOps-Flexibilität.

#### <a name="docker-container-tooling"></a>Tools für Docker-Container

**Neues in Version 15.5**:

* Visual Studio enthält Tools für Docker-Container, die nun mehrstufige Dockerdateien unterstützen, die das Erstellen von optimierten Containerimages vereinfachen.
* Wenn Sie ein Projekt mit Docker-Unterstützung öffnen, werden von Visual Studio automatisch die erforderlichen Containerimages im Hintergrund abgerufen, erstellt und ausgeführt. Sie können dieses Verhalten über die Einstellung **Container im Hintergrund automatisch starten** in Visual Studio deaktivieren.

## <a name="cloud-app-development-with-azure"></a>Cloud-App-Entwicklung mit Azure

### <a name="azure-functions-tools"></a>Azure Functions-Tools

Als Teil der Workload „Azure-Entwicklung“ haben wir Tools eingefügt, mit denen Sie Azure-Funktionen entwickeln, indem Sie vorkompilierte C#-Klassenbibliotheken verwenden. Sie können jetzt auf dem lokalen Entwicklungscomputer erstellen, ausführen und debuggen und anschließend direkt aus Visual Studio in Azure veröffentlichen.

Weitere Informationen finden Sie auf der Seite [Azure Functions-Tools für Visual Studio](/azure/azure-functions/functions-develop-vs).

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>Debuggen von ASP.NET-Live-Apps mithilfe von Andockpunkten und Protokollpunkten in Azure-Live-Apps

**Neues in Version 15.5**: Der Momentaufnahmedebugger erstellt eine Momentaufnahme Ihrer Apps, die sich in der Produktion befinden, wenn Code ausgeführt wird, der für Sie relevant ist. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

Die Momentaufnahmensammlung ist für folgende Web-Apps verfügbar, die in Azure App Service ausgeführt werden:

* ASP.NET-Apps, die in .NET Framework 4.6.1 oder höher ausgeführt werden.
* ASP.NET Core-Apps, die in .NET Core 2.0 oder höher unter Windows ausgeführt werden.

Weitere Informationen finden Sie unter [Debug live ASP.NET apps using snappoints and logpoints (Debuggen von ASP.NET-Live-Apps mithilfe von Andockpunkten und Protokollpunkten)](../debugger/debug-live-azure-applications.md).

## <a name="windows-app-development"></a>Windows App-Entwicklung

### <a name="universal-windows-platform"></a>Universelle Windows-Plattform

Universelle Windows-Plattform (UWP) ist die App-Plattform für Windows 10. Sie können Apps für UWP mit nur einem API-Satz, einem App-Paket und einem Store entwickeln, um alle Windows 10-Geräte (PC, Tablet, Smartphone, Xbox, HoloLens, Surface Hub usw.) zu erreichen. UWP unterstützt verschiedene Bildschirmgrößen und eine Vielzahl von Interaktionsmodellen, z.B. Fingereingabe, Maus und Tastatur, Gamecontroller oder Stifteingabe. Hinter UWP-Apps steht die Idee, dass Benutzer ihre Funktionen mobil auf ALLEN Geräten verwenden und jeweils das Gerät verwenden möchten, das am praktischsten und produktivsten für die vorliegende Aufgabe ist.

![Universelle Windows-Plattform](../cross-platform/media/uwp_coreextensions.png)

Wählen Sie aus C#, Visual Basic, C++ oder JavaScript Ihre bevorzugte Entwicklungssprache aus, um eine UWP-App für Windows 10-Geräte zu erstellen. Visual Studio 2017 stellt für jede Sprache eine Vorlage für UWP-Apps bereit, durch die Sie ein einzelnes Projekt für alle Geräte erstellen können. Wenn Ihre Arbeit abgeschlossen ist, können Sie ein App-Paket erstellen und dieses von Visual Studio aus an Microsoft Store übermitteln, um Ihre App für Kunden mit Windows 10-Geräten bereitzustellen.

**Neues in Version 15.5**: Version 15.5 von Visual Studio 2017 bietet eine optimale Unterstützung für das Windows 10 Fall Creators Update SDK (10.0.16299.0). Das Windows 10 Fall Creators Update enthält viele Verbesserungen für UWP-Entwickler. Im Folgenden finden Sie einige der wichtigsten Änderungen: 

* **Unterstützung für .NET Standard 2.0**<br/>Zusätzlich zur optimierten App-Entwicklung ist das Windows 10 Fall Creators Update das erste Release von Windows 10, das Unterstützung für .NET Standard 2.0 bietet. [.NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/) ist eine Referenzimplementierung der Basisklassenbibliothek, die jede .NET-Plattform implementieren kann. Das Ziel von .NET Standard besteht darin, das Freigeben von Code für .NET-Entwickler für jede .NET-Plattform, mit der sie arbeiten möchten, so einfach wie möglich zu gestalten.
* **Das Beste aus UWP und Win32**<br/>Die Windows 10-Plattform wurde durch die [Desktop-Brücke](/windows/uwp/porting/desktop-to-uwp-root) verbessert, um Windows 10 für alle .NET-Entwickler unabhängig davon zu verbessern, ob der derzeitige Fokus auf UWP, WPF, Windows Forms oder Xamarin liegt. Mit dem neuen Projekttyp für das Packen von Apps in Version 15.5 von Visual Studio 2017 können Sie Windows-App-Pakete für Ihre Windows Presentation Foundation- oder Windows Forms-Projekte genau wie für UWP-Projekte erstellen. Nachdem Sie Ihre App gepackt haben, erhalten Sie alle Vorteile von Windows 10 für die App-Entwicklung und können diese über Microsoft Store (bei Verbraucher-Apps) oder Microsoft Store für Unternehmen und Bildungseinrichtungen verteilen. Da gepackte Apps über Zugriff auf die vollständige UWP-API-Oberfläche und auf die Win32-APIs auf dem Desktop verfügen, können Sie Ihre Windows Presentation Foundation- und Windows Forms-Apps nach und nach mit den UWP-APIs und den Windows 10-Features modernisieren. Darüber hinaus können Sie Ihre Win32-Komponenten mit allen Win32-Funktionen in Ihre UWP-Anwendungen integrieren, die auf dem Desktop gekennzeichnet sind.

Weitere Informationen zu UWP finden Sie auf der Seite [Entwickeln von Apps für die universelle Windows-Plattform (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md).

## <a name="mobile-app-development"></a>Entwicklung mobiler Apps

### <a name="xamarin"></a>Xamarin

Als Teil der Workload „Mobile Entwicklung mit .NET“ können mit C#, .NET und Visual Studio vertraute Entwickler mithilfe von Xamarin native Apps für Android, iOS und Windows bereitstellen. Entwickler können bei der Arbeit mit Xamarin für mobile Apps die vertraute Leistungsstärke und Produktivität nutzen, einschließlich Remotedebuggen auf Android&mdash;, iOS- und Windows-Geräten – ohne native Programmiersprachen wie Objective-C oder Java erlernen zu müssen.

Weitere Informationen finden Sie unter [Visual Studio und Xamarin](/xamarin/).

### <a name="entitlements-editor"></a>Berechtigungs-Editor

**Neues in 15.3:** Für Ihre iOS-Entwicklungsanforderungen haben wir einen eigenständigen Berechtigungs-Editor hinzugefügt. Er enthält eine benutzerfreundliche Benutzeroberfläche, die problemlos durchsucht werden kann. Doppelklicken Sie auf die Datei *entitlements.plist*, um ihn zu starten.

![Berechtigungs-Editor für Xamarin](media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Visual Studio-Tools für Xamarin

**Neues in 15.4:** Mit Xamarin Live können Entwickler ihre Apps direkt auf iOS-und Android-Geräten kontinuierlich bereitstellen, testen und debuggen. Nachdem Sie Xamarin Live Player heruntergeladen haben &mdash;(aus dem App Store oder von Google Play)&mdash;, können Sie Ihr Gerät mit Visual Studio verknüpfen. So verändern Sie den Prozess des Erstellens mobiler Apps von Grund auf. Diese Funktion ist jetzt in Visual Studio beinhaltet und kann unter **Tools** > **Optionen** > **Xamarin** > **Sonstiges** > **Xamarin Live Player aktivieren** aktiviert werden.

![Animation der Verknüpfung, Bereitstellung und der Livebearbeitungsmodi von Xamarin Live Player](media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Support für den Google Android-Emulator

**Neues in 15.8:** Wenn Sie Hyper-V verwenden, können Sie den Android-Emulator von Google nun parallel mit anderen Hyper-V-basierten Technologien verwenden, einschließlich Hyper-V-VMs, Docker-Tools und dem HoloLens-Emulator. (Diese Funktion erfordert Windows 10 April 2018 Update oder höher.)

![Der Google Android-Emulator mit Hyper-V-Technologien](media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Editor mit geteilter Ansicht für den Xamarin.Android-Designer

Ebenso **neu in 15.8:** Für Xamarin.Android wurden wichtige Verbesserungen am Designer durchgeführt. Ein Editor mit geteilter Ansicht wurde eingeführt, mit dem Sie Layouts gleichzeitig erstellen, bearbeiten und eine Vorschau dafür erstellen können.

![Der Editor mit geteilter Ansicht für den Xamarin.Android-Designer](media/android-designer-split-view.png)

Weitere Informationen finden Sie unter [Hardwarebeschleunigung für verbesserte Leistung des Emulators](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

### <a name="visual-studio-app-center"></a>Visual Studio App Center

**Neues in Version 15.5**: Visual Studio App Center ist &mdash;nun allgemein für Android, iOS, macOS und Windows-Apps verfügbar&mdash; und enthält alle erforderlichen Komponenten, um den Lebenszyklus Ihrer Apps zu verwalten, einschließlich automatisierter Builds, Tests auf echten Geräten in der Cloud, der Verteilung an Betatester und App-Stores sowie des Überwachens der tatsächlichen Nutzung durch Absturz- und Analysedaten. Bei Apps, die in Objective-C, Swift, Java, C#, Xamarin oder React Native geschrieben wurden, werden sämtliche Features unterstützt.

  ![Testumgebung von Visual Studio App Center](media/app-center-test-env.png)

Weitere Informationen finden Sie im Blogbeitrag [Introducing App Center: Build, test, distribute and monitor apps in the cloud (Einführung in App Center: Erstellen, testen, verteilen und überwachen von Apps in der Cloud)](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/).

## <a name="cross-platform-development"></a>Plattformübergreifende Entwicklung

### <a name="redgate-data-tools"></a>Redgate Data Tools

Um DevOps-Funktionen für die Entwicklung der SQL Server-Datenbank zu erweitern, sind Redgate Data Tools jetzt in Visual Studio verfügbar.

In Visual Studio 2017 Enterprise sind enthalten:

* [Redgate ReadyRollCore ](https://www.red-gate.com/products/sql-development/sql-change-automation/?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) unterstützt Sie bei der Entwicklung von Migrationsskripts, dem Verwalten von Datenbankänderungen mithilfe von Quellcodeverwaltung und dem sicherem Automatisieren von Bereitstellungen der Änderungen an SQL Server-Datenbanken zusammen mit Anwendungsänderungen.
* [Redgate SQL Prompt Core](https://www.red-gate.com/products/sql-development/sql-prompt/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) unterstützt Sie beim schnelleren und genaueren Schreiben von SQL mithilfe intelligenter Codevervollständigung. Datenbank- und Systemobjekte sowie Schlüsselwörter werden während der Eingabe automatisch von SQL Prompt vervollständigt und es werden auch Spaltenvorschläge bereitgestellt. Dies führt zu optimiertem Code und weniger Fehlern, da Sie sich nicht jeden Spaltennamen oder Alias merken müssen.

In allen Editionen von Visual Studio 2017 ist enthalten:

* [Redgate SQL Search](https://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) steigert Ihre Produktivität, weil Sie schnell nach SQL-Fragmenten und -Objekten in mehreren Datenbanken suchen können.

Weitere Informationen finden Sie im Blogbeitrag [Redgate Data Tools in Visual Studio 2017](https://devblogs.microsoft.com/visualstudio/redgate-data-tools-in-visual-studio-2017/).

### <a name="net-core"></a>.NET Core

.NET Core ist eine allgemeine, modulare, plattformübergreifende Open Source-Implementierung des .NET-Standards und enthält vieler der gleichen APIs wie das .NET Framework.

Die .NET Core-Plattform besteht aus mehreren Komponenten, die den verwalteten Compiler, die Runtime, die Basisklassenbibliotheken sowie zahlreiche Anwendungsmodelle wie ASP.NET Core umfassen. .NET Core unterstützt derzeit die drei Hauptbetriebssysteme: Windows, Linux und macOS Sie können .NET Core in Geräte-, Cloud- und eingebetteten/IoT-Szenarien verwenden.

Außerdem enthält es nun Unterstützung für Docker.

**Neues in 15.3:** Visual Studio 2017 Version 15.3 unterstützt die .NET Core 2.0-Entwicklung. Wenn .NET Core 2.0 verwendet wird, muss das .NET Core 2.0 SDK separat heruntergeladen und installiert werden.

Weitere Informationen finden Sie im [Leitfaden für .NET Core](/dotnet/core/index).

## <a name="games-development"></a>Spieleentwicklung

### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools für Unity

Als Teil der Workload „Entwicklung von Spielen für Unity“ haben wir die Tools eingefügt, mit denen Sie plattformübergreifend entwickeln können, um 2D- und 3D-Spiele und interaktiven Inhalt zu erstellen. Sie können ein einmal entwickeltes Spiel auf 21 Plattformen, einschließlich aller mobilen Plattformen, WebGL, Mac, PC- und Linux- Desktops, Web und Konsolen, mit Visual Studio 2017 und Unity 5.6 veröffentlichen.

Weitere Informationen finden Sie unter [Visual Studio Tools für Unity](/gamedev/unity/get-started/visual-studio-tools-for-unity.md).

## <a name="ai-development"></a>KI-Entwicklung

### <a name="visual-studio-tools-for-ai"></a>Visual Studio-Tools für KI

**Neues in Version 15.5**: Verwenden Sie die Produktivitätsfeatures von Visual Studio, um KI-Innovationen zu beschleunigen. Verwenden Sie die integrierten Features des Code-Editors wie die Syntaxhervorhebung, IntelliSense und die automatische Textformatierung. Sie können Ihre Deep Learning-Anwendung interaktiv in Ihrer lokalen Umgebung testen, indem Sie das Debuggen in ausführlichen Schritten für lokale Variablen und Modelle verwenden.

  ![Deep Learning-IDE](../ai/media/about/ide.png)

Weitere Informationen finden Sie unter [Visual Studio Tools für KI](../ai/about-ai-tools.md).

## <a name="whats-next"></a>Ausblick

Wir aktualisieren Visual Studio 2017 häufig mit neuen Features, die die Entwicklung immer weiter verbessern. Nachfolgend werden einige der wichtigsten Updates aufgeführt, die sich derzeit in der Phase der experimentellen Vorschau befinden:

* **[Live Share:](https://visualstudio.microsoft.com/services/live-share/)** ein neues Tool, über das Sie eine Codebasis und deren Kontext für ein anderes Teammitglied freigeben können und direkt in Visual Studio eine sofortige bidirektionale Kollaboration erhalten. Mithilfe von Live Share können Ihre Teammitglieder ohne Probleme und auf sichere Weise ein Projekt, das Sie für sie freigegeben haben, lesen, bearbeiten und debuggen sowie darin navigieren.<br><br>Weitere Informationen finden Sie unter [Live Share FAQ (Häufig gestellte Fragen zu Live Share)](/visualstudio/liveshare/faq).<br><br>
* **[IntelliCode](https://visualstudio.microsoft.com/services/intellicode/)** : eine neue Funktion zur Verbesserung der Softwareentwicklung unter Verwendung von KI. Dabei werden bessere kontextbezogene Codevervollständigungen zur Verfügung gestellt, Entwickler werden dabei unterstützt, gemäß den Mustern und Formatierungen ihres Teams zu codieren, versteckte Codeprobleme zu finden und Code Reviews auf die Bereiche zu beschränken, die wirklich wichtig sind. <br><br>Weitere Informationen finden Sie unter [IntelliCode FAQ (Häufig gestellte Fragen zu IntelliCode)](/visualstudio/intellicode/faq).

Sie möchten mehr über unsere Pläne für Visual Studio 2017 erfahren? Weitere Informationen finden Sie auf der Seite [Visual Studio-Roadmap](/visualstudio/productinfo/vs2018-roadmap).

Und schauen Sie sich auch unsere neueste Version von [Visual Studio 2019](whats-new-visual-studio-2019.md) an.

## <a name="contact-us"></a>Kontakt

Warum sollten Sie dem Visual Studio-Team ein Feedback senden? Weil wir das Feedback unserer Kunden ernst nehmen. Es gibt den Anstoß zu vielen unserer Initiativen.

Wenn Sie einen Vorschlag zu möglichen Verbesserungen von Visual Studio machen oder mehr über Optionen zur Produktunterstützung erfahren möchten, finden Sie weitere Informationen auf der Seite [Send us feedback](feedback-options.md) (Senden Sie uns Feedback).

### <a name="report-a-problem"></a>Problem melden

Manchmal reicht eine Nachricht nicht aus, um das gesamte Ausmaß eines Problems, auf das Sie gestoßen sind, deutlich zu machen. Wenn Visual Studio bei Ihnen nicht reagiert, abstürzt oder Leistungsprobleme auftreten, können Sie die Schritte zur Reproduktion und unterstützende Dateien (wie Screenshots, Überwachungs- und Heap-Speicherabbilddateien) mithilfe des Tools **Problem melden** an uns weiterleiten. Weitere Informationen zur Verwendung dieses Tools finden Sie auf der Seite [Melden eines Problems](how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Siehe auch

* [Visual Studio 2017 – Anmerkungen zu dieser Version](/visualstudio/releasenotes/vs2017-relnotes)
* [Neuigkeiten im Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)
* [Neues in Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Neues in C#](/dotnet/csharp/whats-new)
* [Neues für Team Foundation Server](/azure/devops/server/whats-new)
* [Neues in Visual Studio für Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [Neues in Visual Studio 2019](whats-new-visual-studio-2019.md)