---
title: Python-Unterstützung für Visual Studio unter Windows
titleSuffix: ''
description: Zusammenfassung der Python-Features in Visual Studio, durch die Visual Studio zur besten Python-IDE unter Windows wird (auch bekannt als Python-Tools für Visual Studio, PTVS).
ms.date: 06/05/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 0283cb4332e9137550b74a85c38d7963f3c77a70
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890473"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Arbeiten mit Python in Visual Studio unter Windows

Python ist eine beliebte Programmiersprache, die zuverlässig, flexibel, leicht zu erlernen und für alle Betriebssysteme kostenlos ist und sowohl von einer starken Entwicklercommunity als auch vielen kostenlosen Bibliotheken unterstützt wird. Python unterstützt alle Arten von Entwicklung, einschließlich Webanwendungen, Webdienste, Desktop-Apps, Skripts und wissenschaftliche Berechnungen, und wird von vielen Universitäten, Wissenschaftlern, gelegentlichen und professionellen Entwicklern gleichermaßen verwendet. Weitere Informationen zur Sprache finden Sie unter [python.org](https://www.python.org) und [Python for Beginners](https://www.python.org/about/gettingstarted/).

Visual Studio ist eine leistungsstarke Python-IDE unter Windows. Visual Studio bietet über die Workloads **Python-Entwicklung** und **Data Science** (Visual Studio 2017 und höhere Versionen) und die kostenlose Erweiterung Python Tools für Visual Studio (Visual Studio 2015 und früher) [Open-Source](https://github.com/Microsoft/ptvs)-Unterstützung für die Python-Sprache.

Python wird gegenwärtig nicht von Visual Studio für Mac unterstützt, ist jedoch über Visual Studio Code unter Mac und Linux verfügbar (siehe [Questions and answers](#questions-and-answers) (Fragen unten Antworten)).

Einführung:

- Folgen Sie den [Installationsanweisungen](installing-python-support-in-visual-studio.md), um die Python-Arbeitsauslastung einzurichten.
- Machen Sie sich anhand der Abschnitte in diesem Artikel mit den Python-Funktionen von Visual Studio vertraut.
::: moniker range="vs-2017"
- Befolgen Sie eine oder mehrere der Schnellstartanweisungen, um ein Projekt zu erstellen. Falls Sie sich nicht entscheiden können, womit Sie anfangen möchten, beginnen Sie mit [Erstellen einer Web-App mit Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
::: moniker range=">=vs-2019"
- Befolgen Sie eine oder mehrere der Schnellstartanweisungen, um ein Projekt zu erstellen. Wenn Sie unsicher sind, beginnen Sie mit [Schnellstart: Öffnen und Ausführen von Python-Code in einem Ordner](quickstart-05-python-visual-studio-open-folder.md) oder [Erstellen einer Web-App mit Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
- Befolgen Sie das Tutorial [Working with Python in Visual Studio (Arbeiten mit Python in Visual Studio)](tutorial-working-with-python-in-visual-studio-step-01-create-project.md), um ein vollständiges End-to-End-Erlebnis zu erhalten.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio unterstützt die Python-Version 2.7 und Version 3.5 bis 3.7. Es ist zwar möglich, Code mit Visual Studio zu bearbeiten, der in anderen Versionen von Python geschrieben wurde, aber diese Versionen werden offiziell nicht unterstützt, und Funktionen wie IntelliSense und Debuggen funktionieren möglicherweise nicht. Die Python-Version 3.8 befindet sich immer noch in der Entwicklung. Ausführliche Informationen zum Support finden Sie in diesem [Issue auf GitHub](https://github.com/microsoft/PTVS/issues/5822).
::: moniker-end

## <a name="support-for-multiple-interpreters"></a>Unterstützung mehrerer Interpreter

Das Visual Studio-Fenster **Python-Umgebungen** (unten in einer breiten, erweiterten Ansicht dargestellt) bietet eine zentrale Stelle zum Verwalten aller Ihrer globalen Python-Umgebungen, Conda-Umgebungen und virtuellen Umgebungen. Visual Studio erkennt Python-Installationen in standardmäßigen Speicherorten automatisch, und Sie können benutzerdefinierte Installationen konfigurieren. Mit jeder Umgebung können Sie problemlos Pakete verwalten, ein interaktives Fenster für die Umgebung öffnen und auf Ordner der Umgebung zugreifen.

::: moniker range="vs-2017"
![Erweiterte Ansicht des Fensters „Python-Umgebungen“](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Erweiterte Ansicht des Fensters „Python-Umgebungen“](media/environments/environments-expanded-view-2019.png)
::: moniker-end

Verwenden Sie den Befehl **Interaktives Fenster öffnen**, um Python-Code im Kontext von Visual Studio interaktiv auszuführen. Verwenden Sie den Befehl **In PowerShell öffnen**, um ein separates Befehlsfenster im Ordner der ausgewählten Umgebung zu öffnen. Über dieses Befehlsfenster können Sie jedes beliebige Python-Skript ausführen.

Weitere Informationen finden Sie unter:

- [Verwalten von Python-Umgebungen](managing-python-environments-in-visual-studio.md)
- [Referenz zu Python-Umgebungen](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Vielfältige Funktionen für die Bearbeitung, IntelliSense und Kennzeichnung von Code

Visual Studio bietet einen erstklassigen Python-Editor mit folgenden Funktionen: Syntaxfarben, automatische Vervollständigung für den gesamten Code und alle Bibliotheken, Codeformatierung, Signaturhilfe, Umgestaltung, Linting und Typhinweise. Visual Studio bietet auch einzigartige Features wie die Klassenansicht, **Zur Definition wechseln**, **Alle Verweise suchen** und Codeausschnitte. Durch die direkte Integration in das [interaktive Fenster](#interactive-window) können Sie schnell Python-Code entwickeln, der bereits in einer Datei gespeichert ist.

![Codevervollständigungen für Python-Code in Visual Studio](media/code-editing-completions-simple.png)

Weitere Informationen finden Sie unter:

- Dokumentation: [Edit Python code (Bearbeiten von Python-Code)](editing-python-code-in-visual-studio.md)
- Dokumentation: [Formatcode](formatting-python-code.md)
- Dokumentation: [Refactoring von Code](refactoring-python-code.md)
- Dokumentation: [Use a linter (Verwenden eines Linters)](linting-python-code.md)
- Dokumentation zu allgemeinen Features von Visual Studio: [Features des Code-Editors](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Interaktives Fenster

Für jede für Visual Studio geeignete Python-Umgebung können Sie einfach die gleiche interaktive Umgebung (REPL) für einen Python-Interpreter direkt in Visual Studio öffnen, statt eine separate Eingabeaufforderung zu verwenden. Sie können auch einfach zwischen Umgebungen wechseln. Wählen Sie zum Öffnen einer separaten Eingabeaufforderung zuerst Ihre gewünschte Umgebung im Fenster **Python-Umgebungen** und anschließend, wie unter [Unterstützung mehrerer Interpreter](#support-for-multiple-interpreters) beschrieben, den Befehl **In PowerShell öffnen** aus.

![Interaktives Python-Fenster in Visual Studio](media/interactive-window.png)

Visual Studio bietet zudem eine enge Integration zwischen dem Python-Code-Editor und dem **interaktiven** Fenster. Mit der Tastenkombination **STRG**+**EINGABE** wird die aktuelle Codezeile (oder der Codeblock) im Editor bequem an das **interaktive** Fenster gesendet und dann wird zur nächsten Zeile (oder zum nächsten Block) gewechselt. Mit **STRG**+**EINGABE** können Sie problemlos schrittweise Code durchlaufen, ohne den Debugger auszuführen. Sie können mit der gleichen Tastenkombination auch markierten Code an das **interaktive** Fenster senden und mühelos Code aus dem **interaktiven** Fenster in den Editor einfügen. Zusammen ermöglichen diese Funktionen, dass Sie Details für ein Segment des Codes im **interaktiven** Fenster ausarbeiten und die Ergebnisse problemlos in einer Datei im Editor speichern können.

Visual Studio unterstützt zudem IPython/Jupyter in der REPL, einschließlich Inlineplots, .NET und Windows Presentation Foundation (WPF).

Weitere Informationen finden Sie unter:

- [Interaktives Fenster](python-interactive-repl-in-visual-studio.md)
- [IPython in Visual Studio](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>Projektsystem und Projekt- und Elementvorlagen

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio 2019 unterstützt das Öffnen eines Ordners, der Python-Code enthält, und das Ausführen dieses Codes, ohne dass Projekt- und Projektmappendateien in Visual Studio erstellt werden müssen. Weitere Informationen finden Sie unter [Schnellstart: Öffnen und Ausführen von Python-Code in einem Ordner](quickstart-05-python-visual-studio-open-folder.md). Die Verwendung einer Projektdatei bietet jedoch gewisse Vorteile, wie in diesem Abschnitt erläutert.
::: moniker-end

Mit Visual Studio können Sie die Komplexität eines Projekts handhaben, während es mit der Zeit wächst. Ein *Visual Studio-Projekt* ist weitaus mehr als eine Ordnerstruktur: Es enthält Informationen dazu, wie die verschiedenen Dateien verwendet werden und wie sie miteinander in Beziehung stehen. Mit Visual Studio können Sie App-Code, Testcode, Webseiten, JavaScript, Buildskripts usw. unterscheiden, wodurch wiederum für die Datei geeignete Features ermöglicht werden. Mit einer Visual Studio-Projektmappe können Sie darüber hinaus mehrere verwandte Projekte verwalten, z.B. ein Python-Projekt und ein C++-Erweiterungsprojekt.

![Eine Visual Studio-Projektmappe mit Python- und C++-Projekten](media/projects-solution-explorer-two-projects.png)

Projekt- und Elementvorlagen automatisieren die Einrichtung unterschiedlicher Arten von Projekten und Dateien. Dadurch sparen Sie wertvolle Zeit und müssen komplizierte und fehleranfällige Details nicht mehr verwalten. Visual Studio stellt Vorlagen für Web-, Azure-, Data Science-, Konsolen- und andere Arten von Projekten bereit. Zudem gibt es Vorlagen für Dateien, wie Python-Klassen, Komponententests, Azure-Webkonfigurationen, HTML und sogar Django-Apps.

[![Projekt- und Elementvorlagen für Python in Visual Studio](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Weitere Informationen finden Sie unter:

- Dokumentation: [Verwalten von Python-Projekten](managing-python-projects-in-visual-studio.md)
- Dokumentation: [Referenz für Python-Elementvorlagen](python-item-templates.md)
- Dokumentation: [Python-Projektvorlagen](managing-python-projects-in-visual-studio.md#project-templates)
- Dokumentation: [Arbeiten mit C++ und Python](working-with-c-cpp-python-in-visual-studio.md)
- Dokumentation zu allgemeinen Features von Visual Studio: [Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Dokumentation zu allgemeinen Features von Visual Studio: [Projektmappen und Projekte in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Vollständige Debugfeatures

Eine der Stärken von Visual Studio ist der leistungsfähige Debugger. Speziell für Python ermöglicht Visual Studio Debuggen im gemischten Python/C++-Modus, Remotedebuggen unter Linux, Debuggen im **interaktiven** Fenster und Debuggen von Python-Komponententests.

![Visual Studio-Debugger für Python mit dem Popup einer Ausnahme](media/debugging-exception-popup.png)

::: moniker range=">=vs-2019"
In Visual Studio 2019 können Sie Code ohne Visual Studio-Projektdatei ausführen und debuggen. Ein Beispiel finden Sie unter [Schnellstart: Öffnen und Ausführen von Python-Code in einem Ordner](quickstart-05-python-visual-studio-open-folder.md).
::: moniker-end

Weitere Informationen finden Sie unter:

- Dokumentation: [Debuggen von Python](debugging-python-in-visual-studio.md)
- Dokumentation: [Python/C++: Debuggen im gemischten Modus](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Dokumentation: [Remotedebuggen unter Linux](debugging-python-code-on-remote-linux-machines.md)
- Dokumentation zu allgemeinen Features von Visual Studio: [Übersicht über die Features des Visual Studio-Debuggers](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Profilerstellungstools mit umfassender Berichterstellung

Mit der Profilerstellung wird untersucht, wie Zeit innerhalb der Anwendung aufgewendet wird. Visual Studio unterstützt die Profilerstellung mit CPython-basierten Interpretern und bietet die Möglichkeit, die Leistung zwischen verschiedenen Profilerstellungen zu vergleichen.

[![Visual Studio-Profiler-Ergebnisse für ein Python-Projekt](media/profiling-results.png)](media/profiling-results.png#lightbox)

Weitere Informationen finden Sie unter:

- Dokumentation: [Python-Profilerstellungstools](profiling-python-code-in-visual-studio.md)
- Dokumentation zu allgemeinen Features von Visual Studio: [Übersicht über das Profilerstellungsfeature](../profiling/profiling-feature-tour.md) (Nicht alle Funktionen der Visual Studio-Profilerstellung stehen für Python zur Verfügung.)

## <a name="unit-testing-tools"></a>Tools für Unittests

Sie können Tests im **Test-Explorer** von Visual Studio ermitteln, ausführen und verwalten und Unittests problemlos debuggen.

![Debuggen eines Python-Komponententests in Visual Studio](media/unit-test-debugging.png)

Weitere Informationen finden Sie unter:

- Dokumentation: [Tools für Unittests für Python](unit-testing-python-in-visual-studio.md)
- Dokumentation zu allgemeinen Features von Visual Studio: [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)

## <a name="azure-sdk-for-python"></a>Azure-SDK für Python

Die Azure-Bibliotheken für Python vereinfachen die Nutzung von Azure-Diensten aus Windows-, Mac OS X- und Linux-Apps. Sie können sie zum Erstellen und Verwalten von Azure-Ressourcen sowie zum Herstellen einer Verbindung mit Azure-Diensten verwenden. 

Weitere Informationen finden Sie unter [Azure-SDK für Python](/azure/python/) und [Azure-Bibliotheken für Python](/azure/python/python-sdk-azure-overview).

## <a name="questions-and-answers"></a>Fragen und Antworten

**F. Wird Python von Visual Studio für Mac unterstützt?**

A. Zurzeit nicht, aber Sie können sich auf [Developer Community (Entwicklercommunity)](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html) dafür einsetzen. Die [Visual Studio für Mac](/visualstudio/mac/)-Dokumentation identifiziert die aktuellen Entwicklungstypen, die unterstützt werden. In der Zwischenzeit funktioniert Visual Studio-Code auf Windows, Mac und Linux [problemlos mit Python über die verfügbaren Erweiterungen](https://code.visualstudio.com/docs/languages/python).

**F. Was kann ich verwenden, um die Benutzeroberfläche mit Python zu erstellen?**

A. Das Hauptangebot in diesem Bereich ist das [Qt-Projekt](https://www.qt.io/qt-for-application-development/) mit Bindungen für Python mit dem Namen [PySide (die offizielle Bindung)](https://wiki.qt.io/PySide) (siehe auch [PySide-Downloads](https://download.qt.io/official_releases/pyside/.)) und [PyQt](https://wiki.python.org/moin/PyQt). Derzeit umfasst die Python-Unterstützung in Visual Studio keine bestimmten Tools für die Entwicklung von Benutzeroberflächen.

**F. Kann mit einem Python-Projekt eine eigenständige ausführbare Datei erzeugt werden?**

A. Python ist im Allgemeinen eine interpretierte Sprache, bei der Code nach Bedarf in einer geeigneten, Python-fähigen Umgebung wie Visual Studio und Webservern ausgeführt wird. Visual Studio selbst bietet derzeit keine Möglichkeit, eine eigenständige ausführbare Datei zu erstellen, was im Wesentlichen ein Programm mit einem eingebetteten Python-Interpreter bedeutet. Wie auf [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency) beschrieben, stellt die Python-Community jedoch unterschiedliche Möglichkeiten zum Erstellen von ausführbaren Dateien bereit. CPython unterstützt es auch, in eine native Anwendung eingebettet zu werden, wie im Blogbeitrag [Using CPython's embeddable zip file (Verwenden der eingebetteten ZIP-Datei von CPython)](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/) beschrieben wird.

::: moniker range="<=vs-2017"

## <a name="feature-support"></a>Funktionsunterstützung

Python-Features können wie im [Installationshandbuch](installing-python-support-in-visual-studio.md) beschrieben in den folgenden Editionen von Visual Studio installiert werden:

- [Visual Studio 2019 (alle Editionen)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2017 (alle Editionen)
- Visual Studio 2015 (alle Editionen)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express für Web, Update 2 oder höher
- Visual Studio 2013 Express für Desktop, Update 2 oder höher
- Visual Studio 2013 (Pro-Edition oder höher)
- Visual Studio 2012 (Pro-Edition oder höher)
- Visual Studio 2010 SP1 (Pro-Edition oder höher, .NET 4.5 ist erforderlich)

Visual Studio 2015 und frühere Versionen sind unter [visualstudio.microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/) verfügbar.

> [!Important]
> Features werden nur für die neueste Visual Studio-Version unterstützt und gewartet. Sie sind für ältere Versionen zwar verfügbar, werden jedoch nicht mehr aktiv verwaltet.

|          Python-Unterstützung          |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   Verwaltung mehrerer Interpreter   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Automatische Erkennung beliebte Interpreter | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Hinzufügen von benutzerdefinierten Interpretern      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Virtuelle Umgebungen       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         PIP/einfache Installation         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Projektsystem         |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ |      2012 Pro+       | 2010 SP1 Pro+ |
|--------------------------------|----------|----------|-----------|--------------|----------|-----------|----------------------|---------------|
| Neues Projekt aus vorhandenem Code | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Alle Dateien anzeigen         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Quellcodeverwaltung         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|        Git-Integration         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>1</sup> |   &#10007;    |

<br/>

|           Bearbeiten            |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Syntaxhervorhebung      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Automatische Vervollständigung         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Signaturhilfe        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          QuickInfo          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Objektkatalog/Klassenansicht   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Navigationsleiste        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Zur Definition wechseln       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Navigieren zu          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Alle Verweise suchen      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Automatischer Einzug       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Codeformatierung        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Umgestalten – Umbenennen       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Umgestalten – Methode extrahieren   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Umgestalten – Import hinzufügen/entfernen | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|            PyLint            | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Interaktives Fenster     |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Interaktives Fenster     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IPython mit Inlinediagrammen | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|               Desktop               |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Konsole/Windows-Anwendung     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IronPython WPF (mit XAML-Designer) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      IronPython Windows Forms       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Web         |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Django-Webprojekt  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Bottle-Webprojekt  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Flask-Webprojekt  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Generisches Webprojekt | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Azure          |   2017+   |   2015   | 2013 Comm | 2013 Desktop |       2013 Web       |      2013 Pro+       |      2012 Pro+       |    2010 SP1 Pro+     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   Bereitstellung auf einer Website   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>2</sup> |
|   Bereitstellung für eine Webrolle   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Bereitstellung für eine Workerrolle  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Ausführen im Azure-Emulator  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
|    Remotedebuggen    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> |       &#10007;       |
| Anfügen im Server-Explorer | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>

|           Django-Vorlagen           |   2017+   |   2015   | 2013 Comm | 2013 Desktop |       2013 Web       |      2013 Pro+       | 2012 Pro+ | 2010 SP1 Pro+ |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              Debuggen               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            Automatische Vervollständigung             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004;  |   &#10004;    |
| Automatische Vervollständigung für CSS und JavaScript | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007;  |   &#10007;    |

<br/>

|                  Debuggen                  |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  Debuggen                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Debuggen ohne ein Projekt         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Debuggen – Anfügen an Bearbeitung        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            Debuggen im gemischten Modus             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| Remotedebuggen (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|          Debuggen im interaktiven Fenster           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

<a name="matrix-profiling"></a>

| Profilerstellung |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-----------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Profilerstellung | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Test      |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Test-Explorer | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   Test ausführen    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  Test debuggen   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. Git-Unterstützung für Visual Studio 2012 steht in der Erweiterung Visual Studio-Tools für Git zur Verfügung (verfügbar im [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit)).

1. Für die Bereitstellung auf der Azure-Website ist das [Azure SDK für .NET 2.1 – Visual Studio 2010 SP1](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VS2010SP1AzurePack.2E2.2E1.appids) erforderlich. Höhere Versionen unterstützen Visual Studio 2010 nicht.

1. Für die Unterstützung von Azure-Webrollen und -Workerrollen ist das [Azure SDK für .NET 2.3 – VS 2012](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs11AzurePack.appids) oder höher erforderlich.

1. Für die Unterstützung von Azure-Webrollen und -Workerrollen ist das [Azure SDK für .NET 2.3 – VS 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) oder höher erforderlich.

1. Der Django-Vorlagen-Editor in Visual Studio 2013 weist einige bekannte Probleme auf, die durch die Installation von Update 2 gelöst werden.

1. Erfordert mindestens Windows 8. Visual Studio 2013 Express für Web weist kein Dialogfeld **An den Prozess anhängen** auf. Remotedebuggen für Azure-Websites ist allerdings über den Befehl **Debugger anfügen (Python)** im **Server-Explorer** möglich. Für das Remotedebuggen ist das [Azure SDK für .NET 2.3 – Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) oder höher erforderlich.

1. Erfordert mindestens Windows 8. Für den Befehl **Debugger anfügen (Python)** im **Server-Explorer** ist das [Azure SDK für .NET 2.3 – Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) oder höher erforderlich.

1. Erfordert mindestens Windows 8.
::: moniker-end
