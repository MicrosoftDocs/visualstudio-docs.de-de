---
title: 'Schnellstart: Klonen eines Python-Coderepositorys'
description: In diesem Schnellstart erstellen Sie ein Python-Projekt in Visual Studio, indem Sie das Python Koans-Repository mithilfe von Visual Studio Team Explorer klonen.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 55db74b2b2882aac12ac1587c4e972e31f7dfe10
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902400"
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Schnellstart: Klonen eines Repositorys in Python-Code in Visual Studio

Sobald Sie die [Python-Unterstützung in Visual Studio installiert](installing-python-support-in-visual-studio.md) haben, können Sie die GitHub-Erweiterung für Visual Studio hinzufügen. Mit der Erweiterung können Sie problemlos ein Repository von Python-Code klonen und daraus ein Projekt in der IDE erstellen. Sie können auch Repositorys in der Befehlszeile immer klonen und dann mit ihnen in Visual Studio arbeiten.

## <a name="install-the-github-extension-for-visual-studio"></a>Installieren Sie die GitHub-Erweiterung für Visual Studio

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

## <a name="work-with-github-in-visual-studio"></a>Arbeiten mit GitHub in Visual Studio

1. Starten Sie Visual Studio.

1. Klicken Sie auf **Ansicht** > **Team Explorer**, um das Fenster **Team Explorer** zu öffnen. Dort können Sie eine Verbindung zu GitHub oder Azure Repos herstellen oder ein Repository klonen. (Wenn unten die Seite **Verbinden** nicht angezeigt wird, klicken Sie auf das Steckersymbol in der Befehlszeile oben, wodurch Sie direkt auf diese Seite weitergeleitet werden.)

    ![Das Team Explorer-Fenster zeigt Azure Repos, GitHub und das Klonen eines Repositorys.](media/team-explorer.png)

1. Wählen Sie unter **Lokale Git-Repositorys** den Befehl **Klonen** aus, geben Sie anschließend `https://github.com/gregmalcolm/python_koans` in das URL-Feld ein, geben Sie einen Ordner für die geklonten Dateien ein, und klicken Sie auf **Klonen**.

    > [!Tip]
    > Der Ordner, den Sie in **Team Explorer** angeben, empfängt die geklonten Dateien. Im Gegensatz zum Befehl `git clone` wird beim Erstellen eines Klons in **Team Explorer** nicht automatisch ein Unterordner mit dem Namen des Repositorys erstellt.

1. Wenn das Klonen abgeschlossen ist, erscheint der Name des Repositorys in der Liste **Lokale Git-Repositorys**. Doppelklicken Sie auf den Namen, um zum Repository-Dashboard im **Team Explorer** zu navigieren.

1. Klicken Sie unter **Projektmappen** auf **Neu**.

    ![Das Fenster „Team Explorer“, in dem ein neues Projekt aus einem Klon erstellt wird](media/team-explorer-new-project.png)

1. Navigieren Sie im nun angezeigten Dialogfeld **Neues Projekt** zur Sprache **Python** (oder suchen Sie nach „Python“), wählen Sie **Aus vorhandenem Python-Code** aus, geben Sie einen Namen für das Projekt an, legen Sie als **Speicherort** denselben Ordner fest, in dem auch das Repository gespeichert ist, und klicken Sie auf **OK**. Klicken Sie in dem sich öffnenden Assistenten auf **Fertig stellen**.

1. Klicken Sie im Menü auf **Ansicht** > **Projektmappen-Explorer**.

1. Erweitern Sie im **Projektmappen-Explorer** den Knoten **python3**. Klicken Sie mit der rechten Maustaste zunächst auf **contemplate_koans.py**, und klicken Sie anschließend auf **Als Startdatei festlegen**. Bei diesem Schritt meldet Visual Studio, welche Datei beim Ausführen des Projekts verwendet werden soll.

1. Klicken Sie zunächst im Menü auf **Projekt** > **Koans-Eigenschaften** und anschließend auf die Registerkarte **Allgemein**, und legen Sie das **Arbeitsverzeichnis** auf „Python3“ fest. Dieser Schritt ist notwendig, da Visual Studio standardmäßig den Projektstamm als Arbeitsverzeichnis festlegt, anstatt den Speicherort der Startdatei zu verwenden (*python3\contemplate_koans.py* – dies können Sie auch in den Projekteigenschaften sehen). Der Programmcode sucht im Arbeitsverzeichnis nach einer *koans.txt*-Datei. Sie erhalten also einen Laufzeitfehler, wenn Sie diesen Wert nicht ändern.

    ![Festlegen des Arbeitsverzeichnisses für ein Python-Projekt](media/projects-set-working-directory.png)

1. Drücken Sie **STRG**+**F5**, oder wählen Sie **Debuggen** > **Ohne Debuggen starten** aus, um das Programm auszuführen. Wenn Ihnen ein **FileNotFoundError** für *koans.txt* angezeigt wird, prüfen Sie die Einstellungen für das Arbeitsverzeichnis, so wie im vorherigen Schritt beschrieben.

1. Wenn das Programm erfolgreich ausgeführt wird, zeigt es einen Assertionsfehler in Zeile 17 von *python3/koans/about_asserts.py* an. Dies ist beabsichtigt, da das Programm so entwickelt wurde, dass es Ihnen Python beibringt, indem Sie sämtliche beabsichtigte Fehler beheben müssen. (Weitere Details finden Sie unter [Ruby Koans](https://rubykoans.com/) – der Inspiration für Python Koans.)

    ![Erste Ausgabe des Python Koans-Programms](media/koans-output.png)

1. Öffnen Sie *python3/koans/about_asserts.py*, indem Sie zu der Datei im **Projektmappen-Explorer** navigieren und darauf doppelklicken. Beachten Sie, dass standardmäßig keine Zeilennummern im Editor erscheinen. Klicken Sie zum Ändern dieser Einstellung auf **Extras** > **Optionen** und im unteren Bereich des Dialogfelds auf **Alle Einstellungen** anzeigen. Navigieren Sie anschließend zu **Text-Editor** > **Python** > **Allgemein**, und klicken Sie auf **Zeilennummern**:

    ![Aktivieren der Zeilennummer für Python-Dateien](media/options-general-line-numbers.png)

1. Korrigieren Sie den Fehler, indem Sie das `False`-Argument in Zeile 17 in `True` ändern. Die Zeile sollte wie folgt lauten:

    ```python
    self.assertTrue(True) # This should be True
    ```

1. Führen Sie das Programm erneut aus. Wenn Visual Studio eine Warnung für einen Fehler ausgibt, antworten Sie mit **Ja**, um den Code weiter ausführen zu können. Daraufhin sehen Sie, dass die erste Überprüfung erfolgreich ist, und das Programm wird beim nächsten Koan beendet. Fahren Sie mit dem Korrigieren der Fehler fort, und führen Sie das Programm so oft Sie möchten erneut aus.

> [!Important]
> Mithilfe dieser Schnellstartanleitung haben Sie einen direkten Klon des *python_koans*-Repositorys auf GitHub erstellt. Solche Repositorys werden durch deren Autoren vor direkten Änderungen geschützt, sodass ein möglicher Änderungsversuch fehlschlägt. Tatsächlich forken Entwickler solche Repositorys in ihre GitHub-Konten. Nehmen Sie die Änderungen in diesem Konto vor, und erstellen Sie anschließend Pull Requests, um sie an das ursprüngliche Repository zu übermitteln. Wenn Sie über einen eigenen Fork verfügen, verwenden Sie diese URL anstatt der zuvor verwendeten ursprünglichen Repository-URL.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Tutorial: Arbeiten mit Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Siehe auch

- [Manuelles Identifizieren eines vorhandenen Python-Interpreters](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Installieren von Python-Unterstützung für Visual Studio unter Windows](installing-python-support-in-visual-studio.md)
- [Installationsspeicherorte](installing-python-support-in-visual-studio.md#install-locations)
