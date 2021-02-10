---
title: Verwenden von PyLint für Python-Code
description: Führen Sie PyLint in Visual Studio aus, um Probleme in Python-Code zu prüfen, einschließlich der Befehlszeilenoptionen zum Anpassen des Linting.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 97336bf028a02c6c1f90262754dc0c89aa81e1cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882803"
---
# <a name="use-pylint-to-check-python-code"></a>Verwenden von PyLint zur Überprüfung von Python-Code

[PyLint](https://www.pylint.org/), ein häufig verwendetes Tool, das Python-Code auf Fehler überprüft und gute Python-Codemuster unterstützt, ist in Visual Studio für Python-Projekte integriert.

## <a name="run-pylint"></a>Ausführen von PyLint

Klicken Sie einfach im **Projektmappen-Explorer** mit der rechten Maustaste auf ein Python-Projekt, und wählen Sie **Python** > **PyLint ausführen** aus:

![PyLint-Befehl im Kontextmenü für Python-Projekte](media/code-pylint-command.png)

Wenn Sie diesen Befehl verwenden, werden Sie dazu aufgefordert, PyLint in Ihrer aktiven Umgebung zu installieren, wenn es noch nicht vorhanden ist.

PyLint-Warnungen und -Fehler werden im **Fehlerlistenfenster** angezeigt:

![PyLint-Fehlerliste](media/code-pylint-error-list.png)

Durch Doppelklicken auf einen Fehler gelangen Sie direkt zu dem Quellcode, der das Problem verursacht.

> [!Tip]
> Eine detaillierte Liste aller PyLint-Ausgabemeldungen finden Sie in der [PyLint-Funktionsreferenz](https://pylint.readthedocs.io/en/latest/technical_reference/features.html).

## <a name="set-pylint-command-line-options"></a>Festlegen von PyLint-Befehlszeilenoptionen

Der Abschnitt mit [Befehlszeilenoptionen](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) in der PyLint-Dokumentation beschreibt, wie das Verhalten von PyLint über eine *.pylintrc*-Konfigurationsdatei gesteuert wird. Eine solche Datei kann im Stammverzeichnis eines Python-Projekts in Visual Studio oder in einem anderen Verzeichnis platziert werden, je nachdem, in welchem Umfang die Einstellungen angewendet werden sollen (Details finden Sie in den [Befehlszeilenoptionen](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options)).

Um z.B. die in der obigen Abbildung gezeigten „missing-docstring“-Warnungen mit einer *.pylintrc*-Datei in einem Projekt zu unterdrücken, gehen Sie folgendermaßen vor:

1. Navigieren Sie in der Befehlszeile zum Stammverzeichnis Ihres Projekts (dort finden Sie Ihre *.pyproj*-Datei), und führen Sie den folgenden Befehl aus, um eine kommentierte Konfigurationsdatei zu generieren:

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. Wählen Sie im Visual Studio-Projektmappen-Explorer mit der rechten Maustaste Ihr Projekt, wählen Sie **Hinzufügen** > **Vorhandenes Element** aus, navigieren Sie zur neuen *.pylintrc*-Datei, wählen Sie sie aus, und wählen Sie **Hinzufügen** aus.

1. Öffnen Sie die Datei zum Bearbeiten, die eine Reihe von Einstellungen enthält, mit denen Sie arbeiten können. Um eine Warnung zu deaktivieren, suchen Sie den Abschnitt `[MESSAGES CONTROL]` und darin die Einstellung `disable`. Es gibt eine lange Zeichenfolge mit spezifischen Meldungen, an die Sie beliebige Warnungen anfügen können. Im vorliegenden Beispiel wird `,missing-docstring` angefügt (einschließlich des trennenden Kommas).

1. Speichern Sie die *.pylintrc*-Datei, und führen Sie PyLint erneut aus. Sie werden feststellen, dass die Warnungen jetzt unterdrückt werden.

> [!Tip]
> Um eine *.pylintrc*-Datei aus einer Netzwerkfreigabe zu verwenden, erstellen Sie auf der Netzwerkfreigabe eine Umgebungsvariable namens `PYLINTRC` mit dem Wert des Dateinamens und verwenden dazu einen UNC-Pfad oder einen zugeordneten Laufwerkbuchstaben. Beispielsweise `PYLINTRC=\\myshare\python\.pylintrc`.
