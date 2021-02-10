---
title: Auswählen einer Python-Umgebung für ein Projekt
description: Sie können eine bestimmte Python-Umgebung auswählen, einschließlich Anaconda-Umgebungen und virtueller Umgebungen, und auf ein bestimmtes Projekt anwenden.
ms.date: 03/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 6521df812d708744a617c0e3fe95285fdbfa0262
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970607"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>Auswählen einer Python-Umgebung für ein Projekt

Sämtlicher Code in einem Python-Projekt wird im Kontext einer bestimmten Umgebung ausgeführt, z.B. als globale Python-Umgebung, Anaconda-Umgebung, virtuelle Umgebung oder Conda-Umgebung. Visual Studio verwendet diese Umgebung auch für das Debugging, für Import- und Membervervollständigungen, für Syntaxüberprüfungen sowie für weitere Tasks, die Sprachdienste erforderlich machen, welche für die Python-Version und eine Reihe von installierten Paketen spezifisch sind.

Alle neuen Python-Projekte in Visual Studio werden anfänglich für die Verwendung der globalen Standardumgebung konfiguriert, die im **Projektmappen-Explorer** unter dem Knoten **Python-Umgebungen** angezeigt wird:

![Globale Python-Standardumgebung im Projektmappen-Explorer](media/environments/environments-project.png)

::: moniker range="vs-2017"
Klicken Sie mit der rechten Maustaste auf den Knoten **Python-Umgebungen**, und klicken Sie auf **Python-Umgebungen hinzufügen/entfernen**, um die Umgebung eines Projekts zu entfernen. Wählen Sie aus der angezeigten Liste, die globale, virtuelle und Conda-Umgebungen enthält, diejenigen aus, die im Knoten **Python-Umgebungen** angezeigt werden sollen:

![Dialogfeld „Python-Umgebungen hinzufügen/entfernen“](media/environments/environments-add-remove.png)

Nachdem Sie auf **OK** geklickt haben, werden alle ausgewählten Umgebungen unter dem Knoten **Python-Umgebungen** angezeigt. Die aktuell aktivierte Umgebung wird fett formatiert angezeigt:

![Mehrere Python-Umgebungen im Projektmappen-Explorer](media/environments/environments-project-multiple.png)

Klicken Sie mit der rechten Maustaste auf den Namen der Umgebung, und wählen Sie **Umgebung aktivieren** aus, um eine andere Umgebung schnell zu aktivieren. Ihre Auswahl wird mit dem Projekt gespeichert, und wann immer Sie das Projekt in Zukunft öffnen, ist diese Umgebung aktiviert. Wenn Sie alle Optionen im Dialogfeld **Python-Umgebungen hinzufügen/entfernen** deaktivieren, aktiviert Visual Studio die globale Standardumgebung.

Das Kontextmenü des Knotens **Python-Umgebungen** stellt ebenfalls zusätzliche Befehle bereit:

| Befehl | Beschreibung |
| --- | --- |
| **Virtuelle Umgebung hinzufügen** | Startet den Prozess zum Erstellen einer neuen virtuellen Umgebung im Projekt Weitere Informationen finden Sie unter [Create a virtual environment (Erstellen einer virtuellen Umgebung)](#create-a-virtual-environment). |
| **Vorhandene virtuelle Umgebung hinzufügen** | Fordert Sie dazu auf, einen Ordner auszuwählen, der eine virtuelle Umgebung enthält, und fügt diese der Liste unter **Python-Umgebungen** hinzu, ohne diese zu aktivieren Weitere Informationen finden Sie unter [Aktivieren einer vorhandenen virtuellen Umgebung](#activate-an-existing-virtual-environment). |
| **Erstellen einer Conda-Umgebung** | Wechselt zum *Fenster* **Python-Umgebungen**, in dem Sie einen Namen für die Umgebung eingeben und deren Basisinterpreter angeben. Weitere Informationen finden Sie unter [Conda-Umgebungen](managing-python-environments-in-visual-studio.md#conda-environments). |
::: moniker-end

::: moniker range=">=vs-2019"
Klicken Sie mit der rechten Maustaste auf den Knoten **Python-Umgebungen**, und wählen Sie **Umgebung hinzufügen** aus. Sie können **Umgebung hinzufügen** auch aus der Umgebungs-Dropdownliste in der Python-Symbolleiste auswählen.

Wählen Sie im Dialogfeld **Umgebung hinzufügen** die Registerkarte **Vorhandene Umgebung** und anschließend in der Dropdownliste **Umgebung** eine neue Umgebung aus:

![Auswählen einer Projektumgebung im Dialogfeld „Umgebung hinzufügen“](media/environments/environments-project-2019.png)

Falls Sie einem Projekt bereits eine Umgebung hinzugefügt haben, die nicht dem globalen Standard entspricht, müssen Sie ggf. eine neu hinzugefügte Umgebung aktivieren. Klicken Sie unter dem Knoten **Python-Umgebungen** mit der rechten Maustaste auf die entsprechende Umgebung, und wählen Sie **Umgebung aktivieren** aus. Wenn Sie eine Umgebung aus dem Projekt entfernen möchten, wählen Sie **Entfernen** aus.

![Aktivieren und Entfernen einer Projektumgebung](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>Verwenden von virtuellen Umgebungen

Eine virtuelle Umgebung ist eine einzigartige Kombination aus einem bestimmten Python-Interpreter und einem bestimmten Satz Bibliotheken, die sich von anderen globalen und Conda-Umgebungen unterscheidet. Eine virtuelle Umgebung ist für ein Projekt spezifisch und wird in einem Projektordner gespeichert. Dieser Ordner enthält die installierten Bibliotheken der Umgebung sowie eine *pyvenv.cfg*-Datei, die den Pfad zum *Basisinterpreter* der Umgebung angibt, der sich an anderer Stelle im Dateisystem befindet. (Das bedeutet, dass eine virtuelle Umgebung keine Kopie des Interpreters enthält, sondern nur einen Link zu diesem.)

Ein Vorteil bei der Verwendung einer virtuellen Umgebung liegt daran, dass diese immer die genauen Abhängigkeiten des Projekts angibt, während Sie das Projekt entwickeln. (Im Gegensatz dazu enthält eine gemeinsam genutzte globale Umgebung alle Bibliotheken, unabhängig davon, ob Sie diese im Projekt verwenden.) Über die virtuelle Umgebung können Sie dann einfach eine *requirements.txt*-Datei erstellen, die dazu verwendet wird, diese Abhängigkeiten auf einem anderen Entwicklungs- oder Produktionscomputer erneut zu installieren. Weitere Informationen finden Sie unter [Verwalten von erforderlichen Paketen mit „requirements.txt“](managing-required-packages-with-requirements-txt.md).

Wenn Sie ein Projekt in Visual Studio öffnen, das eine *requirements.txt*-Datei enthält, stellt Visual Studio Ihnen die Option bereit, die virtuelle Umgebung neu zu erstellen. Auf Computern, auf denen Visual Studio nicht installiert ist, können Sie `pip install -r requirements.txt` verwenden, um die Pakete wiederherzustellen.

Da eine virtuelle Umgebung einen hartcodierten Pfad zum Basisinterpreter enthält, und da Sie die Umgebung mithilfe von *requirements.txt* neu erstellen können, lassen Sie üblicherweise den gesamten Ordner der virtuellen Umgebung aus der Quellcodeverwaltung aus.

In den folgenden Abschnitten wird erklärt, wie eine vorhandene virtuelle Umgebung in einem Projekt aktiviert wird und wie eine neue virtuelle Umgebung erstellt wird.

In Visual Studio kann eine virtuelle Umgebung wie jede andere Umgebung über den Knoten **Python-Umgebungen** im **Projektmappen-Explorer** für ein Projekt aktiviert werden.

Sobald eine virtuelle Umgebung zu Ihrem Projekt hinzugefügt wird, wird diese im Fenster **Python-Umgebungen** angezeigt. Sie können diese dann wie jede andere Umgebung aktivieren und die enthaltenen Pakete verwalten.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>Erstellen einer virtuellen Umgebung

Sie können eine neue virtuelle Umgebung direkt in Visual Studio erstellen:

1. Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf **Python-Umgebungen**, und wählen Sie **Virtuelle Umgebung hinzufügen** aus. Daraufhin wird folgendes Dialogfeld angezeigt:

    ![Erstellen einer virtuellen Umgebung](media/environments/environments-add-virtual-1.png)

1. Geben Sie im Feld **Speicherort der virtuellen Umgebung** einen Pfad für die virtuelle Umgebung an. Wenn Sie nur einen Namen angeben, wird die virtuelle Umgebung innerhalb des aktuellen Projekts in einem Unterordner dieses Namens erstellt.

1. Wählen Sie eine Umgebung als Basisinterpreter aus, und klicken Sie auf **Erstellen**. Visual Studio zeigt eine Statusanzeige an, während die Umgebung erstellt wird und alle erforderlichen Pakete heruntergeladen werden. Nach Abschluss des Vorgangs wird die virtuelle Umgebung im Fenster **Python-Umgebungen** für das Projekt angezeigt, das die Umgebung enthält.

1. Die virtuelle Umgebung ist nicht standardmäßig aktiviert. Um die virtuelle Umgebung für das Projekt zu aktivieren, klicken Sie mit der rechten Maustaste darauf und wählen **Umgebung aktivieren** aus.

> [!Note]
> Wenn der Pfad zum Speicherort eine vorhandene virtuelle Umgebung bezeichnet, erkennt Visual Studio den Basisinterpreter automatisch (mithilfe der *orig-prefix.txt*-Datei im Verzeichnis *lib* der Umgebung) und ändert die Schaltfläche **Erstellen** in **Hinzufügen**.
>
> Wenn Sie eine virtuelle Umgebung hinzufügen und eine *requirements.txt*-Datei vorhanden ist, zeigt das Dialogfeld **Virtuelle Umgebung hinzufügen** eine Option zur automatischen Paketinstallation an. Auf diese Weise kann eine Umgebung ganz einfach auf einem anderen Computer neu erstellt werden:
>
> ![Erstellen einer virtuellen Umgebung mit „requirements.txt“](media/environments/environments-requirements-txt.png)
>
> Das Ergebnis ist das gleiche wie bei der Verwendung des Befehls **Vorhandene virtuelle Umgebung hinzufügen**.

### <a name="activate-an-existing-virtual-environment"></a>Aktivieren einer vorhandenen virtuellen Umgebung

Wenn Sie bereits an anderer Stelle eine virtuelle Umgebung erstellt haben, können Sie diese wie folgt für ein Projekt aktivieren:

1. Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf **Python-Umgebungen**, und wählen Sie **Vorhandene virtuelle Umgebung hinzufügen** aus.

1. Navigieren Sie im angezeigten Dialogfeld **Durchsuchen** zu dem Ordner, der die virtuelle Umgebung enthält, wählen Sie ihn aus, und klicken Sie auf **OK**. Wenn Visual Studio eine *requirements.txt*-Datei in dieser Umgebung erkennt, werden Sie gefragt, ob diese Paket installiert werden sollen.

1. Nach kurzer Zeit wird die virtuelle Umgebung im **Projektmappen-Explorer** unter dem Knoten **Python-Umgebungen** angezeigt. Die virtuelle Umgebung ist nicht standardmäßig aktiviert. Klicken Sie daher mit der rechten Maustaste auf die Umgebung, und wählen Sie **Umgebung aktivieren** aus.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="create-a-virtual-environment"></a>Erstellen einer virtuellen Umgebung

Sie können eine neue virtuelle Umgebung direkt in Visual Studio erstellen:

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Python-Umgebungen**, und wählen Sie **Umgebung hinzufügen** aus. Alternativ kann **Umgebung hinzufügen** auch in der Dropdownliste auf der Python-Symbolleiste ausgewählt werden. Wählen Sie im daraufhin angezeigten Dialogfeld **Umgebung hinzufügen** die Registerkarte **Virtuelle Umgebung** aus:

    ![Registerkarte „Virtuelle Umgebung“ des Dialogfelds „Umgebung hinzufügen“](media/environments/environments-add-virtual-1-2019.png)

1. Geben Sie einen Namen für die virtuelle Umgebung an, wählen Sie einen Basisinterpreter aus, und bestätigen Sie dessen Speicherort. Geben Sie unter **Pakete aus Datei installieren** den Pfad zu einer Datei vom Typ *requirements.txt* an, falls gewünscht.

1. Überprüfen Sie die restlichen Optionen des Dialogfelds:

    | Option | BESCHREIBUNG |
    | --- | --- |
    | Als aktuelle Umgebung festlegen | Aktiviert die neue Umgebung nach der Erstellung im ausgewählten Projekt. |
    | Als Standardumgebung für neue Projekte festlegen | Dient zum automatischen Festlegen und Aktivieren der virtuellen Umgebung in allen neuen Projekten, die in Visual Studio erstellt werden. Bei Verwendung dieser Option muss sich die virtuelle Umgebung an einem Ort außerhalb eines bestimmten Projekts befinden.  |
    | In Fenster „Python-Umgebungen“ anzeigen | Gibt an, ob nach dem Erstellen der Umgebung das Fenster **Python-Umgebungen** geöffnet werden soll. |
    | Diese Umgebung global bereitstellen | Gibt an, ob die virtuelle Umgebung auch als globale Umgebung fungieren soll. Bei Verwendung dieser Option muss sich die virtuelle Umgebung an einem Ort außerhalb eines bestimmten Projekts befinden. |

1. Wählen Sie **Erstellen** aus, um die virtuelle Umgebung fertig zu stellen. Visual Studio zeigt eine Statusanzeige an, während die Umgebung erstellt wird und alle erforderlichen Pakete heruntergeladen werden. Nach Abschluss des Vorgangs ist die virtuelle Umgebung aktiviert und wird im **Projektmappen-Explorer** unter dem Knoten **Python-Umgebungen** sowie im Fenster **Python-Umgebungen** für das enthaltende Projekt angezeigt.

### <a name="activate-an-existing-virtual-environment"></a>Aktivieren einer vorhandenen virtuellen Umgebung

Wenn Sie bereits an anderer Stelle eine virtuelle Umgebung erstellt haben, können Sie diese wie folgt für ein Projekt aktivieren:

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Python-Umgebungen**, und wählen Sie **Umgebung hinzufügen** aus.

1. Navigieren Sie im angezeigten Dialogfeld **Durchsuchen** zu dem Ordner, der die virtuelle Umgebung enthält, wählen Sie ihn aus, und klicken Sie auf **OK**. Wenn Visual Studio eine *requirements.txt*-Datei in dieser Umgebung erkennt, werden Sie gefragt, ob diese Paket installiert werden sollen.

1. Nach kurzer Zeit wird die virtuelle Umgebung im **Projektmappen-Explorer** unter dem Knoten **Python-Umgebungen** angezeigt. Die virtuelle Umgebung ist nicht standardmäßig aktiviert. Klicken Sie daher mit der rechten Maustaste auf die Umgebung, und wählen Sie **Umgebung aktivieren** aus.
::: moniker-end

### <a name="remove-a-virtual-environment"></a>Entfernen einer virtuellen Umgebung

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die virtuelle Umgebung, und wählen Sie **Entfernen** aus.

1. Sie werden von Visual Studio gefragt, ob Sie die virtuelle Umgebung entfernen oder löschen möchten. Wenn Sie **Entfernen** auswählen, ist die Umgebung für das Projekt nicht mehr verfügbar, verbleibt aber im Dateisystem. Wenn Sie **Löschen** auswählen, wird die Umgebung sowohl aus dem Projekt entfernt als auch aus dem Dateisystem gelöscht. Der Basisinterpreter bleibt unverändert.

## <a name="view-installed-packages"></a>Anzeigen installierter Pakete

Erweitern Sie im Projektmappen-Explorer den Knoten einer bestimmten Umgebung, um die in dieser Umgebung installierten Pakete anzuzeigen (dies bedeutet, dass Sie diese Pakete importieren und in Ihrem Code verwenden können, wenn die Umgebung aktiv ist):

![Python-Pakete für eine Umgebung im Projektmappen-Explorer](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
Um neue Pakete zu installieren, klicken Sie mit der rechten Maustaste auf die Umgebung, und wählen Sie **Python-Paket installieren** aus, um zur entsprechenden Registerkarte **Pakete** im Fenster **Python-Umgebungen** zu wechseln. Geben Sie einen Suchbegriff ein (in der Regel den Paketnamen), und Visual Studio zeigt entsprechende Pakete an.
::: moniker-end
::: moniker range=">=vs-2019"
Um neue Pakete zu installieren, klicken Sie mit der rechten Maustaste auf die Umgebung, und wählen Sie **Python-Pakete verwalten** aus (oder verwenden Sie die Paketschaltfläche auf der Python-Symbolleiste), um zur entsprechenden Registerkarte **Pakete** im Fenster **Python-Umgebungen** zu wechseln. Geben Sie auf der Registerkarte **Pakete** einen Suchbegriff ein (in der Regel den Paketnamen). Daraufhin zeigt Visual Studio entsprechende Pakete an.
::: moniker-end

Für die meisten Umgebungen werden Pakete (und Abhängigkeiten) in Visual Studio aus dem [Python Package Index (PyPI)](https://pypi.org) heruntergeladen. Dort können Sie auch nach verfügbaren Paketen suchen. Statusleiste und Ausgabefenster von Visual Studio zeigen Informationen zur Installation an. Um ein Paket zu deinstallieren, klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Entfernen** aus.

Der Conda-Paket-Manager verwendet im Allgemeinen `https://repo.continuum.io/pkgs/` als Standardkanal. Es sind jedoch auch andere Kanäle verfügbar. Weitere Informationen finden Sie auf „docs.conda.io“ unter [Managing channels](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html) (Verwalten von Kanälen).

Hinweis: Die angezeigten Einträge sind nicht immer unbedingt richtig, und eine Installation oder Deinstallation ist möglicherweise unzuverlässig oder unmöglich. Visual Studio verwendet den pip-Paket-Manager, falls verfügbar, und lädt ihn bei Bedarf herunter und installiert ihn. Visual Studio kann auch den easy_install-Paket-Manager verwenden. Pakete, die mit `pip` oder `easy_install` über die Befehlszeile installiert wurden, werden ebenfalls angezeigt.

Beachten Sie auch, dass Visual Studio die Verwendung von `conda` zum Installieren von Paketen in einer Conda-Umgebung derzeit nicht unterstützt. Verwenden Sie stattdessen `conda` über die Befehlszeile.

> [!Tip]
> Eine gängige Situation, in der pip ein Paket nicht installieren kann, liegt vor, wenn das Paket Quellcode für native Komponenten in *\*.pyd*-Dateien enthält. Wenn die erforderliche Version von Visual Studio nicht installiert ist, kann pip diese Komponenten nicht kompilieren. Die in dieser Situation angezeigte Fehlermeldung ist **Fehler: „vcvarsall.bat“ wurde nicht gefunden**. `easy_install` kann häufig vorkompilierte Binärdateien herunterladen, und Sie können einen geeigneten Compiler für ältere Python-Versionen von [https://www.microsoft.com/download/details.aspx?id=44266](https://www.microsoft.com/download/details.aspx?id=44266) herunterladen. Weitere Informationen finden Sie unter [How to deal with the pain of "unable to find vcvarsallbat"](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/) (Umgang mit der Fehlermeldung, dass vcvarsallbat nicht gefunden werden konnte) im Teamblog zu Python-Tools.

## <a name="see-also"></a>Siehe auch

- [Verwalten von Python-Umgebungen in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Verwenden von „requirements.txt“ für Abhängigkeiten](managing-required-packages-with-requirements-txt.md)
- [Suchpfade](search-paths.md)
- [Das Fenster „Python-Umgebungen“](python-environments-window-tab-reference.md)
