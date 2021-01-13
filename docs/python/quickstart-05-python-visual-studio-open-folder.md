---
title: 'Schnellstart: Öffnen eines Ordners mit Python-Code'
description: In dieser Schnellstartanleitung erfahren Sie, wie Sie ohne ein Visual Studio-Projekt einen Ordner mit Python-Code öffnen und den Code ausführen (nur Visual Studio 2019).
ms.date: 03/12/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
monikerRange: '>= vs-2019'
ms.openlocfilehash: d11ffcb2c43d2c519d75d43afad6383e0bfaa44a
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761276"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>Schnellstart: Öffnen und Ausführen von Python-Code in einem Ordner

Nach der [Installation von Python-Unterstützung für Visual Studio 2019](installing-python-support-in-visual-studio.md) können Sie ganz einfach vorhandenen Python-Code in Visual Studio 2019 ausführen, ohne ein Visual Studio-Projekt zu erstellen.

> [!Note]
> Bei Visual Studio 2017 und früheren Versionen mussten Sie ein Visual Studio-Projekt für die Ausführung von Python-Code erstellen. Die Erstellung des Projekts ist mit einer integrierten Projektvorlage ganz einfach. Ein Beispiel finden Sie unter [Schnellstart: Erstellen eines Python-Projekts aus vorhandenem Code](quickstart-01-python-in-visual-studio-project-from-existing-code.md)

1. In dieser exemplarischen Vorgehensweise können Sie einen beliebigen Ordner mit Python-Code verwenden. Wenn Sie dem hier gezeigten Beispiel folgen möchten, klonen Sie mit dem Befehl `git clone https://github.com/gregmalcolm/python_koans`das GitHub-Repository „gregmalcolm/python_koans“ in einem geeigneten Ordner auf Ihrem Computer.

1. Starten Sie Visual Studio 2019, und wählen Sie auf dem Startbildschirm unten in der Spalte **Erste Schritte** die Option **Öffnen** aus. Wird Visual Studio bereits ausgeführt, wählen Sie stattdessen **Datei** > **Öffnen** > **Ordner** aus.

    ![Visual Studio-Startbildschirm](media/quickstart-open-folder/01-open-local-folder.png)

1. Navigieren Sie zu dem Ordner mit dem Python-Code, und wählen Sie dann **Ordner auswählen** aus. Wählen Sei bei Verwendung des Codes von „python_koans“ unbedingt den Ordner `python3` im geklonten Ordner aus.

    ![Dialogfeld „Ordner auswählen“ des Befehls „Ordner öffnen“](media/quickstart-open-folder/02-select-folder.png)

1. Visual Studio zeigt den Ordner im **Projektmappen-Explorer** in der sogenannten **Ordneransicht** an. Sie können Ordner mithilfe der Pfeile links von den Ordnernamen auf- und zuklappen:

    ![Steuerelemente zum Auf- und Zuklappen von Ordnern im Projektmappen-Explorer](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. Beim Öffnen eines Python-Ordners erstellt Visual Studio mehrere ausgeblendete Ordner für die Verwaltung von Einstellungen für das Projekt. Wählen Sie zum Anzeigen dieser Ordner (sowie anderer ausgeblendeter Dateien und Ordner wie *.git*) die Symbolleistenschaltfläche **Alle Dateien anzeigen** aus:

    ![Ansicht der ausgeblendeten Ordner im Projektmappen-Explorer](media/quickstart-open-folder/05-view-hidden-folders.png)

1. Damit Sie den Code ausführen können, müssen Sie zunächst die Startdatei oder die primäre Programmdatei angeben. In dem hier gezeigten Beispiel wird als Startdatei *contemplate-koans.py* verwendet. Klicken Sie mit der rechten Maustaste auf diese Datei, und wählen Sie **Als Startelement festlegen** aus.

    ![Festlegen eines Startelements im Projektmappen-Explorer](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > Befindet sich Ihr Startelement nicht im Stamm des geöffneten Ordners, müssen Sie außerdem der JSON-Datei mit der Startkonfiguration eine Zeile hinzufügen. Der entsprechende Vorgang ist im Abschnitt [Festlegen eines Arbeitsverzeichnisses](#set-a-working-directory) beschrieben.

1. Führen Sie den Code durch Drücken von **STRG**+**F5** oder Auswählen von **Debuggen** > **Starten ohne Debuggen** aus. Sie können auch die Symbolleistenschaltfläche auswählen, auf der das Startelement und eine Wiedergabeschaltfläche angezeigt werden. Dadurch wird Code im Visual Studio-Debugger ausgeführt. In allen Fällen erkennt Visual Studio, dass es sich bei Ihrem Startelement um eine Python-Datei handelt, und führt den Code daher automatisch in der Python-Standardumgebung aus. (Diese Umgebung wird rechts neben dem Startelement auf der Symbolleiste angezeigt.)

    ![Symbolleistenschaltfläche zum Starten des Debuggers](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. Die Ausgabe des Programms wird in einem separaten Befehlsfenster angezeigt:

    ![Ausgabefenster für die Ausführung des Python-Codes](media/quickstart-open-folder/08-result-window.png)

1. Wählen Sie zum Ausführen des Codes in einer anderen Umgebung die entsprechende Umgebung über das Dropdownmenü auf der Symbolleiste aus, und starten Sie dann das Startelement erneut.

1. Wählen Sie zum Schließen des Ordners in Visual Studio die Menübefehle **Datei** > **Ordner schließen** aus.

## <a name="set-a-working-directory"></a>Festlegen eines Arbeitsverzeichnisses

Visual Studio führt ein als Ordner geöffnetes Python-Projekt standardmäßig im Stamm dieses Ordners aus. Der Code in Ihrem Projekt geht jedoch unter Umständen davon aus, dass Python in einem Unterordner ausgeführt wird. Nehmen wir zum Beispiel an, dass Sie den Stammordner des Repositorys „python_koans“ öffnen und anschließend die Datei *python3/contemplate-koans.py* als Startelement festlegen. Wenn Sie dann den Code ausführen, wird ein Fehler mit dem Hinweis angezeigt, dass die Datei *koans.txt* nicht gefunden werden kann. Dieser Fehler tritt auf, weil *contemplate-koans.py* annimmt, dass Python im Ordner *python3* und nicht im Repositorystamm ausgeführt wird.

In diesem Fall müssen Sie der JSON-Datei mit der Startkonfiguration außerdem eine Zeile zur Angabe des Arbeitsverzeichnisses hinzufügen:

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Python-Startdatei ( *.py*), und wählen Sie **Einstellungen für Debuggen und Starten** aus.

    ![Screenshot der Ordneransicht im Projektmappen-Explorer mit ausgewählter Datei „contemplate-koans.py“ sowie ausgewählten Einstellungen für Debuggen und Starten im Kontextmenü.](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. Wählen Sie im angezeigten Dialogfeld **Debugger auswählen** die Option **Standard** und dann **Auswählen** aus.

    ![Screenshot des Dialogfelds „Debugger auswählen“ mit ausgewähltem Standarddebugger sowie ausgewählter Schaltfläche „Auswählen“.](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > Wenn **Standard** nicht zur Auswahl zur Verfügung steht, vergewissern Sie sich, dass Sie eine Python-Datei ( *.py*) ausgewählt haben, als Sie den Befehl **Einstellungen für Debuggen und Starten** ausgewählt haben. Visual Studio bestimmt anhand des Dateityps, welche Debuggeroptionen angezeigt werden.

1. Visual Studio öffnet eine Datei namens *launch.vs.json*, die sich im ausgeblendeten Ordner *.vs* befindet. Diese Datei beschreibt den Debugkontext für das Projekt. Fügen Sie zum Angeben eines Arbeitsverzeichnisses einen Wert für `"workingDirectory"` hinzu, wie in `"workingDirectory": "python3"` im folgenden Beispiel für „python-koans“:

    ```json
    {
      "version": "0.2.1",
      "defaults": {},
      "configurations": [
        {
          "type": "python",
          "interpreter": "(default)",
          "interpreterArguments": "",
          "scriptArguments": "",
          "env": {},
          "nativeDebug": false,
          "webBrowserUrl": "",
          "project": "python3\\contemplate_koans.py",
          "name": "contemplate_koans.py",
          "workingDirectory": "python3"
        }
      ]
    }
    ```

1. Speichern Sie die Datei, und starten Sie das Programm erneut. Es wird nun im angegebenen Ordner ausgeführt.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Tutorial: Arbeiten mit Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Siehe auch

- [Schnellstart: Erstellen eines Python-Projekts aus vorhandenem Code](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
- [Schnellstart: Klonen eines Repositorys in Python-Code in Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md)
- [Manuelles Identifizieren eines vorhandenen Python-Interpreters](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
