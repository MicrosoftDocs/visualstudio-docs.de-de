---
title: Komponententest für Python-Code
description: Einrichten von Unittests für Python-Code in Visual Studio, um die Features des Test-Explorers zum Ermitteln, Ausführen und Debuggen von Tests in vollem Umfang zu nutzen.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bd63d927e41a8b360eb7d934693bb3c83a30ea4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920682"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Auswählen des Testframeworks für ein Python-Projekt

Visual Studio unterstützt zwei Testframeworks für Python: [unittest](https://docs.python.org/3/library/unittest.html) und [pytest](https://pytest.org/en/latest/) (ab Visual Studio 2019, Version 16.3, verfügbar). Standardmäßig ist kein Framework ausgewählt, wenn Sie ein Python-Projekt erstellen. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektnamen, und wählen Sie die Option **Eigenschaften** aus, um ein Framework festzulegen. Dadurch wird der Projekt-Designer geöffnet, in dem Sie Tests auf der Registerkarte **Test** konfigurieren können. Auf dieser Registerkarte können Sie das Testframework auswählen, das Sie für Ihr Projekt verwenden möchten. 

* Für das **UnitTest**-Framework wird das Stammverzeichnis des Projekts für die Testermittlung verwendet. Dieser Speicherort sowie das Textmuster zum Identifizieren von Tests können auf der Registerkarte **Test** mit benutzerdefinierten Werten angepasst werden.
* Für das **pytest**-Framework werden Testoptionen wie „Testspeicherort“ und „Dateinamenmuster“ mithilfe der INI-Standardkonfigurationsdatei von pytest festgelegt. Weitere Informationen finden Sie in der [pytest-Referenzdokumentation](https://docs.pytest.org/en/latest/reference.html#ini-options-ref).

Sobald Sie die Auswahl und die Einstellungen Ihres Frameworks gespeichert haben, wird die Testermittlung im Test-Explorer gestartet. Wenn das Fenster „Test-Explorer“ noch nicht geöffnet ist, navigieren Sie zur Symbolleiste, und klicken Sie auf **Test** > **Test-Explorer**.

## <a name="configure-testing-for-python-without-a-project"></a>Konfigurieren von Tests für Python ohne ein Projekt
Mit Visual Studio können Sie vorhandenen Python-Code ohne ein Projekt ausführen und testen, indem Sie [einen Ordner mit Python-Code öffnen](../../quickstart-05-python-visual-studio-open-folder.md). Unter diesen Umständen müssen Sie eine **PythonSettings.json**-Datei zum Konfigurieren der Tests verwenden. 
1. Öffnen Sie Ihren vorhandenen Python-Code mithilfe der Option **Lokalen Ordner öffnen**. 

   ![Visual Studio-Startbildschirm](../../media/quickstart-open-folder/01-open-local-folder.png)

1. Klicken Sie im Fenster „Projektmappen-Explorer“ auf **Alle Dateien anzeigen**, um alle Dateien im aktuellen Ordner anzuzeigen.

   ![Schaltfläche „Alle Dateien anzeigen“](../../media/unit-test-show-files.png)

1. Navigieren Sie im Ordner **Lokale Einstellungen** zur Datei **PythonSettings.json**. Wenn Sie diese Datei nicht im Ordner **Lokale Einstellungen** finden können, erstellen Sie sie manuell.
   
1. Fügen Sie das Feld **TestFramework** zur Einstellungsdatei hinzu, und legen Sie sie, je nachdem, welches Testframework Sie verwenden möchten, auf **pytest** oder **UnitTest** fest.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > Wenn die Felder **UnitTestRootDirectory** und **UnitTestPattern** beim **UnitTest**-Framework nicht in der Datei „PythonSettings.json“ angegeben sind, werden sie jeweils mit den Standardwerten „.“ und „test*.py“ hinzugefügt.

1. Wenn Ihr Ordner ein **src**-Verzeichnis enthält, das von dem Ordner getrennt ist, der Ihre Tests enthält, legen Sie den Pfad zum **src**-Ordner mithilfe des Felds **SearchPaths** in Ihrer **PythonSettings.json**-Datei fest.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Speichern Sie Ihre Änderungen an der Datei „PythonSettings.json“, um die Testermittlung für das angegebene Framework zu initiieren. 
   > [!Note]
   > Wenn das Fenster „Test-Explorer“ bereits geöffnet ist, können Sie die Ermittlung auch mit **STRG** + **R,A** auslösen.

## <a name="discover-and-view-tests"></a>Entdecken und Anzeigen von Tests

Visual Studio identifiziert Tests von **UnitTest** und **pytest** als Methoden, deren Namen mit `test` beginnen. Gehen Sie folgendermaßen vor, um die Testermittlung anzuzeigen:

1. Öffnen Sie ein [Python-Projekt](../../managing-python-projects-in-visual-studio.md).

1. Klicken Sie, sobald das Projekt in Visual Studio geladen wurde, mit der rechten Maustaste auf Ihr Projekt im Projektmappen-Explorer, und wählen Sie dann das Framework **UnitTest** oder **pytest** in den Eigenschaften auf der Registerkarte **Test** aus.
   > [!Note]
   > Wenn Sie das pytest-Framework verwenden, können Sie den Testspeicherort und die Dateinamenmuster mithilfe der INI-Standardkonfigurationsdatei von pytest festlegen. Standardmäßig wird der Arbeitsbereich-/Projektordner mit den Mustern `test_*py` und `*_test.py` verwendet. Weitere Informationen finden Sie in der [pytest-Referenzdokumentation](https://docs.pytest.org/en/latest/reference.html#ini-options-ref).

1. Nachdem Sie das Framework ausgewählt haben, klicken Sie erneut mit der rechten Maustaste auf das Projekt, klicken Sie auf **Hinzufügen** > **Neues Element**, wählen Sie dann **Python-Komponententest** aus, und klicken Sie anschließend auf **Hinzufügen**.

1. Hierdurch wird eine Datei *test_1.py* mit Code erstellt, der das `unittest`-Standardmodul importiert, eine Testklasse aus `unittest.TestCase` ableitet und `unittest.main()` aufruft, wenn Sie das Skript direkt ausführen:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Speichern Sie die Datei bei Bedarf, und öffnen Sie dann den **Test-Explorer** mit dem Menübefehl **Test** > **Windows**.

1. Der **Text-Explorer** durchsucht Ihr Projekt nach Tests und zeigt diese wie unten dargestellt an. Durch Doppelklicken auf einen Test wird dessen Quelldatei geöffnet.

    ![Test-Explorer mit Anzeige des Standardtests „test_A“](../../media/unit-test-a-2.png) 

1. Wenn Sie Ihrem Projekt weitere Tests hinzufügen, können Sie die Ansicht im **Test-Explorer** über das Menü **Gruppieren nach** auf der Symbolleiste organisieren:

    ![Symbolleistenmenü „Gruppieren nach“ im Test-Explorer](../../media/unit-test-group-menu-2.png) 

1. Sie können auch Text in das **Suchfeld** eingeben, um Tests nach Namen zu filtern.

Weitere Informationen zum `unittest`-Modul und zum Schreiben von Tests finden Sie in der [Python 2.7-Dokumentation](https://docs.python.org/2/library/unittest.html) bzw. in der [Python 3.7-Dokumentation](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="run-tests"></a>Tests durchführen

Im **Test-Explorer** können Sie Tests auf vielfältige Weise ausführen:

- **Alle ausführen** führt alle angezeigten Tests aus (gemäß Filter).
- Das Menü **Ausführen** stellt Ihnen Befehle zum Ausführen fehlerhafter, erfolgreicher oder nicht ausgeführter Tests als Gruppe zur Verfügung.
- Sie können einen oder mehrere Tests auswählen, mit der rechten Maustaste darauf klicken und **Ausgewählte Tests ausführen** wählen.

Tests werden im Hintergrund ausgeführt, und der **Test-Explorer** aktualisiert den Status der einzelnen Tests, sobald sie abgeschlossen sind:

- Erfolgreiche Tests werden mit einem grünen Häkchen markiert, und die zum Ausführen des Tests erforderliche Zeit wird angezeigt:

    ![Status „Erfolgreich“ für test_A](../../media/unit-test-A-pass.png)

- Fehlerhafte Tests werden mit einem roten Kreuz markiert und mit einem Link **Ausgabe** versehen, unter dem die Konsolenausgabe und die `unittest`-Ausgabe aus dem Testlauf angezeigt wird:

    ![Status „Fehlerhaft“ für test_A](../../media/unit-test-A-fail.png)

    ![Fehlerhafter test_A mit Grund](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Debuggen von Tests

Da Unittests Codeteile sind, können sie genau wie jeder andere Code Fehler aufweisen und müssen gelegentlich in einem Debugger ausgeführt werden. Im Debugger können Sie Haltepunkte setzen, Variablen untersuchen und Code durchlaufen. Visual Studio bietet auch Diagnosetools für Unittests.

> [!Note]
> Standardmäßig werden für das Testdebuggen die Debugger ptvsd 4 für Visual Studio 2017 (ab Version 15.8) und debugpy für Visual Studio 2019 (ab Version 16.5) verwendet. Wenn Sie stattdessen „PTVSD 3“ verwenden möchten, können Sie die Option **Legacydebugger verwenden** unter **Extras** > **Optionen** > **Python** > **Debuggen** aktivieren. 

Um mit dem Debuggen zu beginnen, legen Sie einen anfänglichen Haltepunkt im Code fest, klicken Sie im **Test-Explorer** mit der rechten Maustaste auf den Test (oder eine Auswahl), und wählen Sie **Ausgewählte Tests debuggen** aus. Visual Studio startet den Python-Debugger auf dieselbe Weise wie für Anwendungscode.

![Debuggen eines Tests](../../media/unit-test-debugging.png)

Sie können auch **Code Coverage für ausgewählte Tests analysieren** verwenden. Weitere Informationen finden Sie unter [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
