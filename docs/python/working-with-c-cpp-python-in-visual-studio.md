---
title: Erstellen von C++-Erweiterungen für Python
description: Eine exemplarische Vorgehensweise zum Erstellen einer C++-Erweiterung für Python mithilfe von Visual Studio, CPython und PyBind11 einschließlich Informationen zum Debuggen im gemischten Modus.
ms.date: 11/19/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 461e68979de6c3b711c05cc4be3ef9d5bd761397
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885936"
---
# <a name="create-a-c-extension-for-python"></a>Erstellen einer C++-Erweiterung für Python

Module, die in C++ (oder C#) geschrieben werden, werden häufig verwendet, um die Funktionen eines Python-Übersetzers zu erweitern sowie den Zugriff auf Fähigkeiten des Betriebssystem auf niedriger Ebene zu aktivieren. Es gibt drei Haupttypen von Modulen:

- Accelerator-Modul: Da Python eine interpretierte Sprache ist, können bestimmte Teile des Codes in C++ für höhere Leistung geschrieben werden.
- Wrapper-Module: machen bestehende C/C++-Schnittstellen für den Python-Code verfügbar oder stellen eine „Python-ähnlichere“ API zur Verfügung, die mit Python einfach zu verwenden ist.
- Systemzugriffsmodule auf niedriger Ebene: Diese werden erstellt, um auf Features der CPython-Laufzeit auf niedriger Ebene, auf das Betriebssystem oder auf die zugrunde liegende Hardware zuzugreifen.

Dieser Artikel führt Sie durch die Erstellung eines C++-Erweiterungsmoduls für CPython, das einen Hyperbeltangens berechnet und diesen aus dem Python-Code abruft. Die Routine wird zuerst in Python implementiert, um den relativen Leistungsgewinn durch Implementieren derselben Routine in C++ zu veranschaulichen.

Dieser Artikel veranschaulicht auch zwei Möglichkeiten zum Verfügbarmachen von C++ in Python:

- Die CPython-Standarderweiterungen, die in der [Python-Dokumentation](https://docs.python.org/3/c-api/) beschrieben werden.
- [PyBind11](https://github.com/pybind/pybind11), das aufgrund der Einfachheit für C++ 11 empfohlen wird.

Ein Vergleich dieser beiden und anderer Maßnahmen finden Sie unter [Alternative Ansätze](#alternative-approaches) am Ende dieses Artikels.

Das abgeschlossene Beispiel aus dieser exemplarischen Vorgehensweise finden Sie unter [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio 2017 oder höher, wobei die Workloads **Desktopentwicklung mit C++** und **Python-Entwicklung** mit den Standardoptionen installiert werden müssen.
- Aktivieren Sie in der Workload **Python-Entwicklung** ebenfalls das Kontrollkästchen **Native Python-Entwicklungstools** auf der rechten Seite. Durch diese Option wird der Großteil der Konfigurationen eingerichtet, die in diesem Artikel beschrieben werden. (Diese Option enthält automatisch auch die C++-Workload.)

    ![Auswählen der Option „Native Python-Entwicklungstools“](media/cpp-install-native.png)

    > [!Tip]
    > Die Installation der Workload **Data Science und analytische Anwendungen** umfasst standardmäßig außerdem Python und die Option **Native Python-Entwicklungstools**.

Weitere Informationen finden Sie unter [Install Python Support for Visual Studio (Installieren von Python-Unterstützung für Visual Studio)](installing-python-support-in-visual-studio.md), einschließlich der Verwendung anderer Versionen von Visual Studio. Wenn Sie Python separat installieren, stellen Sie sicher, dass Sie **Download debugging symbols** (Debugsymbole herunterladen) und **Download debug binaries** (Debugbinärdateien herunterladen) unter **Erweiterte Optionen** im Installer auswählen. Durch diese Option wird sichergestellt, dass Sie über die erforderlichen Debugbibliotheken verfügen, wenn Sie einen Debugbuild ausführen.

## <a name="create-the-python-application"></a>Erstellen der Python-Anwendung

1. Erstellen Sie ein neues Python-Projekt in Visual Studio, indem Sie **Datei** > **Neu** > **Projekt** auswählen. Suchen Sie nach "Python", wählen Sie die Vorlage **Python Application** (Python-Anwendung), weisen Sie ihr einen geeigneten Namen und Standort zu, und klicken Sie auf **OK**.

1. Für das Arbeiten mit C++ ist die Verwendung eines 32-Bit-Python-Interpreters erforderlich (Python 3.6 oder höher wird empfohlen). Erweitern Sie im **Projektmappen-Explorer** von Visual Studio den Projektknoten und anschließend den Knoten **Python-Umgebungen**. Wenn Keine 32-Bit-Umgebung als Standardumgebung angezeigt wird (entweder in Fettdruck oder als **globaler Standard** gekennzeichnet), befolgen Sie die Anweisungen unter [Select a Python environment for a project (Auswählen einer Python-Umgebung für ein Projekt)](selecting-a-python-environment-for-a-project.md). Wenn Sie noch keinen 32-Bit-Interpreter installiert haben, finden Sie unter [Install Python interpreters (Installieren von Python-Interpretern)](installing-python-interpreters.md) weitere Informationen.

1. Fügen Sie in der *.py*-Datei des Projekts den folgenden Code ein, der die Berechnung eines Hyperbeltangens durchführt (Dieser wird ohne Verwendung der mathematischen Bibliothek zum einfacheren Vergleich implementiert). Geben Sie den Code gerne manuell ein, um einige der [Bearbeitungsfunktionen von Python](editing-python-code-in-visual-studio.md) kennenzulernen.

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <= 1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d] (Python implementation)')
    ```

1. Führen Sie das Programm mit **Debuggen** > **Starten ohne Debuggen** (**STRG**+**F5**) aus, um die Ergebnisse anzuzeigen. Sie können die `COUNT`-Variable anpassen, um die Ausführungsdauer des Benchmarks zu ändern. Legen Sie für diese exemplarische Vorgehensweise die „Count“-Variable fest, sodass die Benchmarks jeweils etwa zwei Sekunden benötigen.

> [!TIP]
> Wenn Sie Benchmarks ausführen, sollten Sie immer **Debuggen** > **Ohne Debuggen starten** verwenden, um den Mehraufwand zu vermeiden, der anfällt, wenn Code innerhalb des Visual Studio-Debuggers ausgeführt wird.

## <a name="create-the-core-c-projects"></a>Erstellen der C++-Hauptprojekte

Folgen Sie den Anweisungen in diesem Abschnitt, um zwei identische C++-Projekte namens „superfastcode“ und „superfastcode2“ zu erstellen. Später verwenden Sie in jedem Projekt verschiedene Methoden, um den C++-Code in Python verfügbar zu machen.

1. Stellen Sie sicher, dass die Umgebungsvariable `PYTHONHOME` auf den Python-Interpreter festgelegt ist, den Sie verwenden möchten. Die C++-Projekte in Visual Studio basieren auf dieser Variable, um Dateien zu suchen, z.B. *python.h*, die bei der Erstellung von Python-Erweiterungen verwendet werden.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, und wählen Sie **Hinzufügen** > **Neues Projekt** aus. Eine Visual Studio-Projektmappe kann sowohl Python- als auch C++-Projekte zusammen enthalten (was einer der Vorteile von Visual Studio für Python ist).

1. Suchen Sie nach „C++“, wählen Sie **Leeres Projekt** aus, geben Sie den Namen „superfastcode“ (bzw. „superfastcode2“ für das zweite Projekt) ein, und klicken Sie dann auf **OK**.

    > [!Tip]
    > Wenn **Native Python-Entwicklungstools** in Visual Studio installiert ist, können Sie stattdessen mit der Vorlage **Python-Erweiterungsmodul** beginnen, die bereits vieles von dem enthält, was im Folgenden beschrieben wird. In dieser Vorgehensweise zeigt jedoch der Start mit einem leeren Projekt ausführlich die Erstellung des Erweiterungsmoduls. Sobald Sie den Prozess verstanden haben, spart Ihnen die Vorlage Zeit beim Schreiben Ihrer eigenen Erweiterungen.

1. Erstellen Sie eine C++-Datei im neuen Projekt, indem Sie mit der rechten Maustaste auf den Knoten **Quelldateien** klicken, **Hinzufügen** > **Neues Element** und dann **C++-Datei** auswählen, es `module.cpp` benennen und dann auf **OK** klicken.

    > [!Important]
    > Eine Datei mit der *.cpp*-Erweiterung wird benötigt, um die C++-Eigenschaftsseiten in den folgenden Schritten zu aktivieren.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das C++-Projekt, und wählen Sie **Eigenschaften** aus.

1. Legen Sie **Konfiguration** am oberen Rand des angezeigten Dialogfelds **Eigenschaftenseiten** auf **Alle Konfigurationen** und **Plattform** auf **Win32** fest.

1. Legen Sie die spezifischen Eigenschaften wie in der folgenden Tabelle beschrieben fest, und klicken Sie auf **OK**.

    | Registerkarte | Eigenschaft | Wert |
    | --- | --- | --- |
    | **Allgemein** | **Allgemein** > **Zielname** | Geben Sie den Namen des Moduls so an, wie er von Python in `from...import`-Anweisungen verwendet werden soll. Sie verwenden diesen Namen in C++, wenn Sie das Modul für Python definieren. Wenn Sie den Namen des Projekts als Modulnamen verwenden möchten, behalten Sie den Standardwert **$(ProjectName)** bei. |
    | | **Allgemein** > **Zielerweiterung** | **.pyd** |
    | | **Projektstandards** > **Konfigurationstyp** | **Dynamische Bibliothek (.dll)** |
    | **C/C++-**  > **Allgemein** | **Zusätzliche Includeverzeichnisse** | Fügen Sie den für Ihre Installation geeigneten Python Add the Python *include*-Ordner hinzu, z.B. `c:\Python36\include`.  |
    | **C/C++-**  > **Präprozessor** | **Präprozessordefinitionen** | **Nur CPython**: Fügen Sie `Py_LIMITED_API;` (einschließlich des Semikolons) zum Anfang der Zeichenfolge hinzu. Durch diese Definition werden einige Funktionen eingeschränkt, die Sie aus Python aufrufen können, und der Code wird zwischen unterschiedlichen Python-Versionen portabler. Wenn Sie mit PyBind11 arbeiten, fügen Sie diese Definition nicht hinzu, da sonst Buildfehler angezeigt werden. |
    | **C/C++**  > **Codegenerierung** | **Laufzeitbibliothek** | **Multithreaded-DLL (/MD)** (siehe Warnung unten) |
    | **Linker** > **Allgemein** | **Zusätzliche Bibliotheksverzeichnisse** | Fügen Sie den für Ihre Installation geeigneten Python *libs*-Ordner hinzu, der *.lib*-Dateien enthält, z.B. `c:\Python36\libs`. (Achten Sie darauf, dass Sie auf den *libs*-Ordner verweisen, der *.lib*-Dateien enthält und *nicht* auf den *Lib*-Ordner, der *.py*-Dateien enthält.) |

    > [!Tip]
    > Wenn die Registerkarte „C/C++“ nicht in den Projekteigenschaften angezeigt wird, enthält das Projekt keine Dateien, die als C/C++-Quelldateien identifiziert werden. Dieser Zustand kann eintreten, wenn Sie eine Quelldatei ohne eine *.c*- oder *.cpp*-Erweiterung erstellen. Wenn Sie zuvor versehentlich `module.coo` statt `module.cpp` im Dialogfeld „Neues Element“ eingegeben haben, erstellt Visual Studio die Datei, legt den Dateityp jedoch nicht auf „C/C++-Code“ fest, was die Registerkarte „C/C++-Eigenschaften“ aktiviert. Solche falschen Identifizierungen können auch auftreten, wenn Sie die Datei mit `.cpp` umbenennen. Zum Festlegen des korrekten Dateityps klicken Sie mit der rechten Maustaste auf die Datei im **Projektmappen-Explorer**, wählen **Eigenschaften** aus und legen **Dateityp** auf **C/C++-Code** fest.

    > [!Warning]
    > Legen Sie die Option **C/C++**  > **Codegenerierung** > **Runtimebibliothek** auch für eine Debugkonfiguration immer auf **Multithreaded-DLL (/MD)** fest, da durch diese Einstellung die Python-Binärdateien erstellt werden, die nicht für das Debuggen verwendet werden. Wenn Sie CPython verwenden und die **Multithreaded-Debug-DLL (/MDd)** -Option festlegen, wird beim Erstellen einer **Debug**-Konfiguration die folgende Fehlermeldung ausgegeben: **C1189: Py_LiMITED_API is incompatible with Py_DEBUG, Py_TRACE_REFS und Py_REF_DEBUG (C1189: Py_LIMITED_API ist nicht mit Py_DEBUG, Py_TRACE_REFS und Py_REF_DEBUG kompatibel)** . Wenn Sie darüber hinaus `Py_LIMITED_API` entfernen (dies ist bei CPython, aber nicht bei PyBind11 erforderlich), um den Buildfehler zu vermeiden, stürzt Python beim Versuch, das Modul zu importieren, ab. (Der Absturz geschieht, wie im Folgenden beschrieben, innerhalb des DLL-Aufrufs von `PyModule_Create`, mit der Ausgabemeldung **Fatal Python error: PyThreadState_Get: no current thread** (Schwerwiegender Python-Fehler: PyThreadState_Get: kein aktueller Thread.))
    >
    > Die /MDd-Option wird zum Erstellen der Python-Debugbinärdateien (z.B. *python_d.exe*) verwendet. Wenn Sie sie jedoch für eine Erweiterungs-DLL verwenden, wird weiterhin der Buildfehler mit `Py_LIMITED_API` verursacht.

1. Klicken Sie mit der mit der rechten Maustaste auf das C++-Projekt, und wählen Sie **Erstellen** aus, um Ihre Konfigurationen (**Debug** und **Release**) zu testen. Die *.pyd*-Dateien sind im **Projektmappenordner** unter **Debug** und **Release** und nicht im C++-Projektordner selbst zu finden.

1. Fügen Sie der Datei *module.cpp* des C++-Projekts folgenden Code hinzu:

    ```cpp
    #include <Windows.h>
    #include <cmath>

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. Erstellen Sie das C++-Projekt erneut, um zu bestätigen, dass Ihr Code korrekt ist.

1. Sofern Sie dies noch nicht getan haben, wiederholen Sie die oben genannten Schritte, um ein zweites Projekt mit dem Namen "superfastcode2" mit identischem Inhalt zu erstellen.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Konvertieren von C++-Projekten in Erweiterungen für Python

Sie müssen die exportierten Methoden zunächst so anpassen, dass Sie mit den Python-Typen interagieren, um die C++-DLL in eine Python-Erweiterung konvertieren zu können. Anschließend fügen Sie eine Funktion hinzu, die das Modul zusammen mit den Definitionen der Modulmethoden exportiert.

In den folgenden Abschnitten wird erläutert, wie diese Schritte unter Verwendung von CPython-Erweiterungen und PyBind11 durchgeführt werden.

### <a name="cpython-extensions"></a>CPython-Erweiterungen

Hintergrundinformationen zu dem, was in diesem Abschnitt für Python 3.x gezeigt wird, finden Sie im [Python/C++-API-Referenzhandbuch](https://docs.python.org/3/c-api/index.html) und insbesondere in den [Modulobjekten](https://docs.python.org/3/c-api/module.html) auf python.org. (Denken Sie daran, Ihre Python-Version oben rechts im Dropdownmenü auszuwählen, um die richtige Dokumentation anzuzeigen).

Beziehen Sie sich bei der Arbeit mit Python 2.7 stattdessen auf die Artikel [Extending Python 2.7 with C or C++](https://docs.python.org/2.7/extending/extending.html) (Erweitern von Python 2.7 mit C oder C++) und [Porting Extension Modules to Python 3](https://docs.python.org/2.7/howto/cporting.html) (Portierung von Erweiterungsmodulen auf Python 3) (python.org).

1. Fügen Sie am Anfang der *module.cpp*-Datei *Python.h* ein:

    ```cpp
    #include <Python.h>
    ```

1. Ändern Sie die `tanh_impl`-Methode, um Python-Typen (d.h. ein `PyObject*`-Objekt) zu akzeptieren und zurückzugeben:

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Fügen Sie eine Struktur hinzu, die definiert, wie die `tanh_impl`-Funktion von C++ Python angezeigt wird:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Fügen Sie eine Struktur hinzu, die das Modul so definiert, wie Sie im Python-Code darauf verweisen möchten, insbesondere bei Verwendung der `from...import`-Anweisung. (Stellen Sie sicher, dass dies mit dem Wert in den Projekteigenschaften unter **Konfigurationseigenschaften** > **Allgemein** > **Zielname** übereinstimmt.) Im folgenden Beispiel bedeutet der Modulname „superfastcode“, dass Sie `from superfastcode import fast_tanh` in Python verwenden können, da `fast_tanh` in `superfastcode_methods` definiert ist. (Dateinamen innerhalb des C++-Projekts wie *module.cpp* sind nicht von Bedeutung.)

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Fügen Sie eine Methode hinzu, die Python aufruft, wenn das Modul geladen wird, die `PyInit_<module-name>` genannt werden muss, wobei &lt;module-name&gt; genau mit der Eigenschaft **Allgemein** > **Zielname** des C++-Projekts übereinstimmt (das bedeutet, dass sie mit dem Dateinamen von *.pyd* übereinstimmt, der vom Projekt erstellt wird).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Legen Sie die Zielkonfiguration auf **Release** fest, und erstellen Sie das C++-Projekt erneut, um Ihren Code zu überprüfen. Informationen zur [Problembehandlung](#troubleshooting) finden Sie im folgenden Abschnitt.

### <a name="pybind11"></a>PyBind11

Wenn Sie die Schritte im vorherigen Abschnitt abgeschlossen haben, haben Sie sicher bemerkt, dass Sie zum Erstellen der erforderlichen Modulstrukturen für den C++-Code viele Codebausteine verwendet haben. PyBind11 vereinfacht den Prozess mithilfe von Makros in einer C++-Headerdatei, sodass mit weniger Code das gleiche Ergebnis erzielt werden kann. Hintergrundinformationen zum Inhalt dieses Abschnitts finden Sie unter [PyBind11-Grundlagen](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (github.com).

1. Installieren Sie PyBind11 unter Verwendung von „pip“: `pip install pybind11` oder `py -m pip install pybind11`.

1. Fügen Sie am Anfang der *module.cpp*-Datei *pybind11.h* ein.

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. Verwenden Sie am Ende der *module.cpp*-Datei das Makro `PYBIND11_MODULE`, um den Einstiegspunkt zur C++-Funktion zu definieren.

    ```cpp
    namespace py = pybind11;

    PYBIND11_MODULE(superfastcode2, m) {
        m.def("fast_tanh2", &tanh_impl, R"pbdoc(
            Compute a hyperbolic tangent of a single argument expressed in radians.
        )pbdoc");

    #ifdef VERSION_INFO
        m.attr("__version__") = VERSION_INFO;
    #else
        m.attr("__version__") = "dev";
    #endif
    }
    ```

1. Legen Sie die Zielkonfiguration auf **Release** fest, und erstellen Sie das C++-Projekt, um Ihren Code zu überprüfen. Besuchen Sie zur Problembehandlung den nächsten Abschnitt, wenn Fehler auftreten.

### <a name="troubleshooting"></a>Problembehandlung

Beim C++-Modul treten möglicherweise aus den folgenden Gründen Fehler beim Kompilieren auf:

- *Python.h* kann nicht gefunden werden (**E1696: cannot open source file „Python.h“ (E1696: Die Quelldatei „Python.h“ kann nicht geöffnet werden)** und oder **C1083: cannot open include file: „Python.h“: No such file or directory (Includedatei kann nicht geöffnet werden: „Python.h“. Datei oder Verzeichnis existiert nicht.)** ): Überprüfen Sie, ob der Pfad in **C/C++**  > **Allgemein** > **Zusätzliche Includeverzeichnisse** in den Projekteigenschaften auf den *Include*-Ordner Ihrer Python-Installation zeigt. Siehe Schritt 6 unter [Erstellen des wesentlichen C++-Projekts](#create-the-core-c-projects).

- Die Python-Bibliotheken konnten nicht gefunden werden: Überprüfen Sie, ob der Pfad in **Linker** > **Allgemein** > **Zusätzliche Bibliotheksverzeichnisse** in den Projekteigenschaften auf den *libs*-Ordner Ihrer Python-Installation zeigt. Siehe Schritt 6 unter [Erstellen des wesentlichen C++-Projekts](#create-the-core-c-projects).

- Linker-Fehler im Zusammenhang mit der Zielarchitektur: Ändern Sie die Zielarchitektur des C++-Projekts so, dass sie mit der Ihrer Python-Installation übereinstimmt. Wenn Sie z.B. mit dem C++-Projekt auf x64 abzielen, aber Ihre Python-Installation ein x86-System ist, ändern Sie das C++-Projekt auf x86 ab.

## <a name="test-the-code-and-compare-the-results"></a>Testen des Codes und Vergleichen der Ergebnisse

Da Sie nun die DLLs als Python-Erweiterungen strukturiert haben, können Sie sich vom Python-Projekt auf sie beziehen, die Module importieren und ihre Methoden verwenden.

### <a name="make-the-dll-available-to-python"></a>Verfügbarmachen der DLL für Python

Es gibt zwei Methoden, um die DLL Python zur Verfügung zu stellen.

Die erste Methode funktioniert, wenn das Python-Projekt und das C++-Projekt sich in derselben Projektmappe befinden. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **Verweise** Ihres Python-Projekts, und klicken Sie dann auf **Verweis hinzufügen**. Klicken Sie in dem angezeigten Dialogfeld auf die Registerkarte **Projekte**, wählen Sie anschließend die Projekte **superfastcode** und **superfastcode2** aus, und klicken Sie dann auf **OK**.

![Hinzufügen eines Verweises auf das superfastcode-Projekt](media/cpp-add-reference.png)

Durch die alternative Methode, die in den folgenden Schritten beschrieben wird, wird das Modul in der globalen Python-Umgebung installiert. Dadurch wird es ebenfalls für andere Python-Projekte zur Verfügung gestellt. (In der Regel erfordert dies, dass Sie die IntelliSense-Vervollständigungsdatenbank für diese Umgebung in Visual Studio 2017 Version 15.5 und früher aktualisieren. Eine Aktualisierung ist ebenfalls erforderlich, wenn das Modul aus der Umgebung entfernt wird.)

1. Wenn Sie Visual Studio 2017 oder höher verwenden, führen Sie den Visual Studio-Installer aus, wählen Sie **Ändern** und anschließend **Einzelne Komponenten** > **Compiler, Buildtools und Runtimes** > **Visual C++ 2015.3 v140-Toolset** aus. Dieser Schritt ist notwendig, da Python (für Windows) selbst mit Visual Studio 2015 (Version 14.0) erstellt wurde und erwartet, dass diese Tools beim Erstellen einer Erweiterung über die hier beschriebene Methode verfügbar ist. (Beachten Sie, dass Sie möglicherweise eine 32-Bit-Version von Python installieren müssen, um die DLL auf Win32 statt x64 auszurichten.)

1. Erstellen Sie im C++-Projekt eine Datei mit dem Namen *setup.py*, indem Sie mit der rechten Maustaste auf Projekt klicken und anschließend auf **Hinzufügen** > **Neues Element**. Wählen Sie dann **C++-Datei (.cpp)** aus, benennen Sie die Datei `setup.py`, und wählen Sie anschließend auf **OK** aus (wenn Sie die Datei mit der *.py*-Erweiterung benennen, erkennt Visual Studio sie als Python an, obwohl die C++-Dateivorlage verwendet wird). Wenn die Datei im Editor angezeigt wird, fügen Sie den nachstehenden für die Erweiterungsmethode geeigneten Code ein:

    **CPython-Erweiterungen (superfastcode-Projekt):**

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Weitere Informationen zur Dokumentation für dieses Skript finden Sie unter [Building C and C++ Extensions (Erstellen von C- und C++-Erweiterungen)](https://docs.python.org/3/extending/building.html) (python.org).

    **PyBind11 (superfastcode2-Projekt):**

    ```python
    import os, sys

    from distutils.core import setup, Extension
    from distutils import sysconfig

    cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']

    sfc_module = Extension(
        'superfastcode2', sources = ['module.cpp'],
        include_dirs=['pybind11/include'],
        language='c++',
        extra_compile_args = cpp_args,
        )

    setup(
        name = 'superfastcode2',
        version = '1.0',
        description = 'Python package with superfastcode2 C++ extension (PyBind11)',
        ext_modules = [sfc_module],
    )
    ```

1. Der *setup.py*-Code weist Python an, die Erweiterung mithilfe des C++-Toolsets von Visual Studio 2015 zu erstellen, wenn Sie auf der Befehlszeile verwendet wird. Öffnen Sie eine Eingabeaufforderung mit erhöhten Rechten, navigieren Sie zum Ordner mit dem C++-Projekt (d.h. der Ordner, der *setup.py* enthält), und geben Sie den folgenden Befehl ein:

    ```command
    pip install .
    ```

    oder:

    ```command
    py -m pip install .
    ```

### <a name="call-the-dll-from-python"></a>Aufrufen der DLL von Python

Nachdem Sie die DLL wie im vorherigen Abschnitt beschrieben für Python verfügbar gemacht haben, können Sie nun die Funktionen `superfastcode.fast_tanh` und `superfastcode2.fast_tanh2` aus dem Python-Code aufrufen und deren Leistung mit der Python-Implementierung vergleichen.

1. Fügen Sie die folgenden Zeilen zu der *.py*-Datei hinzu, um aus den DLLs exportierte Methoden aufzurufen und deren Ausgaben anzuzeigen:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Wenn Sie das Python-Programm ausführen (**Debuggen** > **Starten ohne Debuggen** oder **STRG**+**F5**), können Sie beobachten, dass die C++-Routinen ca. fünf- bis zwanzigmal schneller als die Python-Implementierung ausgeführt wird. Eine typische Ausgabe sieht wie folgt aus:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Wenn der Befehl **Ohne Debuggen starten** deaktiviert ist, klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf das Python-Projekt, und wählen Sie **Set as Startup Project (Als Startprojekt festlegen)** aus.

1. Versuchen Sie die `COUNT`-Variable zu vergrößern, sodass die Unterschiede deutlicher werden. Beachten Sie, dass ein **Debugbuild** des C++-Moduls zudem langsamer als ein **Releasebuild** ausgeführt wird, da der **Debugbuild** weniger optimiert ist und verschiedene Fehlerprüfungen enthält. Sie können zum Vergleich zwischen diesen Konfigurationen wechseln.

> [!NOTE]
> In der Ausgabe können Sie sehen, dass die PyBind11-Erweiterung zwar nicht so schnell wie die CPython-Erweiterung, aber dennoch deutlich schneller als die normale Python-Implementierung ist. Der Unterschied ist auf geringen aufrufspezifischen Aufwand zurückzuführen, der von PyBind11 verursacht wird, um die C++-Schnittstelle erheblich zu vereinfachen. Dieser aufrufspezifische Unterschied ist tatsächlich ziemlich gering: Da der Testcode die Erweiterungsfunktionen 500.000 Mal aufruft, erhöhen die hier angezeigten Ergebnisse diesen Aufwand. In der Regel leistet eine C++-Funktion mehr Arbeit als die hier verwendeten normalen `fast_tanh[2]`-Methoden, bei denen der Aufwand nicht von Bedeutung ist. Dennoch führt die Verwendung des CPython-Ansatzes beim Implementieren von Methoden, die möglicherweise tausendfach pro Minute aufgerufen werden, zu einer besseren Leistung als die Verwendung des PyBind11-Ansatzes.

## <a name="debug-the-c-code"></a>Debuggen des C++-Codes

Visual Studio unterstützt das gemeinsame Debuggen von Python- und C++-Code. Dieser Abschnitt veranschaulicht den Prozess mithilfe des Projekts **superfastcode**. Die Schritte für das Projekt **superfastcode2** sind identisch.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Python-Projekt, wählen Sie **Eigenschaften** und die Registerkarte **Debuggen** aus, und wählen Sie anschließend die Option **Debuggen** > **Debuggen von nativem Code aktivieren** aus.

    > [!Tip]
    > Wenn Sie das Debuggen von nativem Code aktivieren, kann das Python-Ausgabefenster möglicherweise sofort verschwinden, wenn das Programm ohne die übliche Pause **Drücken Sie eine beliebige Taste, um fortzufahren...** abgeschlossen wurde. Um eine Pause zu erzwingen, fügen Sie die `-i`-Option dem Feld **Ausführen** > **Interpreterargumente** auf der Registerkarte **Debuggen** hinzu, wenn Sie das Debuggen von nativem Code aktivieren. Dieses Argument den Python-Interpreter in den interaktiven Modus versetzt, nach dem Code abgeschlossen ist, die zu diesem Zeitpunkt wartet er Sie drücken **STRG**+**Z** > **EINGABETASTE**  zu beenden. (Wenn es Ihnen nichts ausmacht, Ihren Python-Code zu ändern, können Sie auch `import os`- und `os.system("pause")`-Anweisungen an das Ende Ihres Programms hinzufügen. Durch diesen Code wird die ursprüngliche Aufforderung zur Pause dupliziert.)

1. Klicken Sie auf **Datei** > **Speichern**, um die Änderungen an den Eigenschaften zu speichern.

1. Legen Sie die Buildkonfiguration in der Visual Studio-Symbolleiste **Debuggen** fest.

    ![Festlegen der Buildkonfiguration auf „Debuggen“](media/cpp-set-debug.png)

1. Da es in der Regel länger dauert, Code im Debugger auszuführen, sollten Sie die `COUNT`-Variable in der *.py*-Datei auf einen fünfmal niedrigeren Wert (z.B. von `500000` auf `100000`) festlegen.

1. Legen Sie einen Haltepunkt auf der ersten Zeile der `tanh_impl`-Methode in Ihrem C++-Code fest, und starten Sie anschließend den Debugger (**F5** oder **Debuggen** > **Debuggen starten**). Der Debugger wird angehalten, wenn dieser Code aufgerufen wird. Wenn der Haltepunkt nicht getroffen wird, überprüfen Sie, ob die Konfiguration auf **Debuggen** festgelegt ist und Sie das Projekt gespeichert haben. (Dies geschieht nicht automatisch beim Starten des Debuggers).

    ![Anhalten an einem Haltepunkt im C++-Code](media/cpp-debugging.png)

1. An diesem Punkt können Sie den C++-Code schrittweise durchgehen, Variablen prüfen, etc. Diese Funktionen werden detailliert unter [Gemeinsames Debuggen von Python und C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) beschrieben.

## <a name="alternative-approaches"></a>Alternative Ansätze

Es gibt wie in der folgenden Tabelle beschrieben verschiedene Methoden zum Erstellen von Python-Erweiterungen. Die ersten beiden Einträge für CPython und PyBind11 enthalten den bereits in diesem Artikel beschriebenen Inhalt.

| Ansatz | Generation | Rechtsvertreter | Pro(s) | Kon(s) |
| --- | --- | --- | --- | --- |
| C/C++-Erweiterungsmodule für CPython | 1991 | Standardbibliothek | [Ausführliche Dokumentation und Tutorials](https://docs.python.org/3/c-api/) Vollständige Kontrolle. | Kompilierung, Portabilität, Verweisverwaltung Hohe C-Kenntnisse. |
| [PyBind11](https://github.com/pybind/pybind11) (empfohlen für C++) | 2015 |  | Einfache, reine Headerbibliothek zur Erstellung von Python-Bindungen von bestehendem C++-Code Wenige Abhängigkeiten PyPy-Kompatibilität | Neuer, weniger ausgefeilt Vermehrter Einsatz von C++11-Features Kurze Liste unterstützter Compiler (Visual Studio ist enthalten) |
| Cython (empfohlen für C) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) | Python-ähnlich. Sehr fortgeschrittenen. Hohe Leistung. | Kompilierung, neue Syntax, neue Toolkette. |
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | | Funktioniert mit nur nahezu jedem C++-Compiler. | Große und komplexe Sammlung von Bibliotheken; enthält viele Problemumgehungen für alte Compiler. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Keine Kompilierung, breite Verfügbarkeit | Unpraktisches und fehleranfälliges Zugreifen und Mutieren von C-Strukturen |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Generieren von Bindungen gleichzeitig für mehrere Sprachen | Übermäßiger Mehraufwand, wenn Python das einzige Ziel darstellt |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/), [pypy](https://pypy.org/) | Einfache Integration, PyPy-Kompatibilität | Neuer, weniger ausgefeilt |
| [cppyy](https://cppyy.readthedocs.io/en/latest/) | 2017 | | Ähnlich wie cffi mit C++. | Neuer, kann möglicherweise zu Problemen mit Visual Studio 2017 führen. |

## <a name="see-also"></a>Siehe auch

Das abgeschlossene Beispiel aus dieser exemplarischen Vorgehensweise finden Sie unter [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).
