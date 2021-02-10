---
title: 'Tutorialschritt 1: Python in Visual Studio, Erstellen eines Projekts'
titleSuffix: ''
description: Dies ist die Übersicht und Schritt 1 einer grundlegenden Einführung in Python-Funktionen in Visual Studio, einschließlich Voraussetzungen und das Erstellen eines neuen Python-Projekts.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 74259a6e15446d8ca0b07f3b694d0285427f8d9f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861555"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Tutorial: Arbeiten mit Python in Visual Studio

Python ist eine beliebte Programmiersprache, die zuverlässig, flexibel, leicht zu erlernen und für alle Betriebssysteme kostenlos ist und sowohl von einer starken Entwicklercommunity als auch vielen kostenlosen Bibliotheken unterstützt wird. Die Programmiersprache unterstützt alle Arten von Entwicklung, einschließlich Webanwendungen, Webdienste, Desktop-Apps, Skripts und wissenschaftliche Berechnungen, und wird gleichermaßen von vielen Universitäten, Wissenschaftlern sowie hobbymäßigen und professionellen Entwicklern verwendet.

Visual Studio bietet erstklassige Unterstützung für Python. In diesem Tutorial finden Sie Informationen zu den folgenden Vorgängen:

- [Step 0: Installation (Schritt 0: Installation)](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [Schritt 1: Erstellen eines Python-Projekts (dieser Artikel)](#step-1-create-a-new-python-project)
- [Step 2: Writing and running code to see Visual Studio IntelliSense at work (Schritt 2: Schreiben und Ausführen von Code, um mit Visual Studio IntelliSense in der Praxis zu arbeiten)](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [Step 3: Create more code in the interactive REPL window (Schritt 3: Erstellen von weiterem Code im interaktivem REPL-Fenster)](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [Step 4: Run the completed program in the Visual Studio debugger (Schritt 4: Ausführen eines abgeschlossenen Programms im Visual Studio-Debugger)](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [Schritt 5: Install packages and manage Python environments (Installieren von Paketen und Verwalten von Python-Umgebungen)](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [Schritt 6: Work with Git (Arbeiten mit Git)](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>Schritt 1: Erstellen eines neuen Python-Projekts

Visual Studio verwaltet in einem *Projekt* sämtliche Dateien, die zusammen eine einzige Anwendung erstellen, einschließlich Quellcode, Ressourcen, Konfigurationen, etc. Ein Projekt formalisiert und verwaltet die Beziehung zwischen allen Projektdateien und externen Ressourcen, die für mehrere Projekte freigegeben sind. In Projekten kann Ihre Anwendung problemlos erweitert und vergrößert werden, anders als dies beim Verwalten der Beziehungen eines Projekts in Ad-Hoc-Ordnern, Skripten, Textdateien oder ohne andere technische Optionen der Fall wäre.

In diesem Tutorial beginnen Sie mit einem einfachen Projekt, das nur eine leere Codedatei enthält.

1. Wählen Sie in Visual Studio **Datei** > **Neu** > **Projekt** (**STRG**+**UMSCHALT**+**N**) aus, wodurch das Dialogfeld **Neues Projekt** geöffnet wird. An dieser Stelle durchsuchen Sie sprachenübergreifende Vorlagen und wählen anschließend eine Sprache für Ihr Projekt aus und geben an, wo Visual Studio Dateien speichern soll.

1. Klicken Sie auf der linken Seite auf **Installiert** > **Python**, oder suchen Sie nach „Python“, um Python-Vorlagen anzuzeigen. Über die Suchfunktion können Sie leicht Vorlagen finden, wenn Sie deren Speicherorte in der Sprachenstruktur nicht kennen.

    ![Dialogfeld „Neues Projekt“ mit Python-Projekten](media/vs-getting-started-python-01-new-project.png)

    Beachten Sie, dass die Python-Unterstützung in Visual Studio eine Reihe von Projektvorlagen, einschließlich Webanwendungen, unter Verwendung der Bottle-, Flask- und Django-Frameworks beinhaltet. Im Rahmen dieser exemplarischen Vorgehensweise beginnen wir jedoch mit einem leeren Projekt.

1. Klicken Sie auf die Vorlage **Python-Anwendung**, geben Sie einen Namen für das Projekt an, und klicken Sie auf **OK**.

1. Nach einigen Augenblicken zeigt Visual Studio die Projektstruktur im **Projektmappen-Explorer**-Fenster (1) an. Die Standardcodedatei ist im Editor (2) geöffnet. Das **Eigenschaftenfenster** (3) wird ebenfalls angezeigt. Darin sind zusätzliche Informationen zu jedem im **Projektmappen-Explorer** ausgewählten Element enthalten, einschließlich Informationen zum genauen Speicherort auf dem Datenträger.

    ![Projektmappen-Explorer mit einem Python-Projekt](media/vs-getting-started-python-02-windows.png)

1. Nehmen Sie sich einige Minuten Zeit, um sich mit dem **Projektmappen-Explorer** vertraut zu machen. Über diese Funktion durchsuchen Sie Dateien und Ordner in Ihrem Projekt.

    ![Erweiterter Projektmappen-Explorer zum Anzeigen von verschiedenen Funktionen](media/vs-getting-started-python-03-solution-explorer.png)

    (1) Ihr Projekt wird fettgedruckt dargestellt, mit dem Namen, den Sie im Dialogfeld **Neues Projekt** festgelegt haben. Auf dem Datenträger wird dieses Projekt im Projektordner durch eine *.pyproj* dargestellt.

    (2) Auf der oberen Ebene finden Sie eine *Projektmappe*, die standardmäßig denselben Namen hat wie Ihr Projekt. Eine Projektmappe, die auf dem Datenträger durch eine *SLN*-Datei dargestellt wird, ist ein Container für mindestens ein zugehöriges Projekt. Wenn Sie z.B. eine C++-Erweiterung für Ihre Python-Anwendung schreiben, kann das C++-Projekt in derselben Projektmappe gespeichert werden. Die Projektmappe enthält unter Umständen neben Projekten für dedizierte Projektprogramme ein Projekt für einen Webdienst.

    (3) Unter Ihrem Projekt werden Quelldateien angezeigt – in diesem Fall eine einzelne *.py*-Datei. Wenn Sie auf eine Datei klicken, werden deren Eigenschaften im **Eigenschaftenfenster** angezeigt. Wenn Sie auf eine Datei doppelklicken, wird diese je nach Dateityp auf die vorgesehene Weise geöffnet.

    (4) Unter diesem Projekt wird außerdem der Knoten **Python-Umgebungen** angezeigt. Wenn der Knoten erweitert ist, werden die für Sie verfügbaren Python-Interpreters angezeigt. Erweitern Sie einen Interpreterknoten, um die in dieser Umgebung (5) installierten Bibliotheken abzurufen.

    Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf einen beliebigen Knoten oder ein beliebiges Element, um auf ein Menü der entsprechenden Befehle zuzugreifen. Beispielsweise können Sie über den Befehl **Umbenennen** den Namen jedes beliebigen Knotens oder Elements umbenennen, einschließlich des Projekts und der Projektmappe.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Schreiben und Ausführen von Code](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Ausführlichere Informationen

- [Python-Projekte in Visual Studio](managing-python-projects-in-visual-studio.md)
- [Erfahren Sie mehr über die Python-Sprache unter python.org](https://www.python.org)
- [Python für Anfänger](https://www.python.org/about/gettingstarted/)
