---
title: Auswählen und Installieren von Python-Interpretern
description: Dieser Artikel enthält eine vollständige Liste der Python-Interpreter, die in Visual Studio unterstützt werden, sowie kurze Anweisungen dazu, wo die entsprechenden Installationsprogramme zu finden sind.
ms.date: 06/05/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e2c4cd4c110b55837009ea9d081a95180727d331
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916517"
---
# <a name="install-python-interpreters"></a>Installieren von Python-Interpretern

Bei der Installation der Workload für die Python-Entwicklung in Visual Studio 2017 und höher wird standardmäßig auch Python 3 (64-Bit) installiert. Optional können Sie die 32-Bit- und 64-Bit-Versionen von Python 2 und Python 3 zusammen mit Miniconda (Visual Studio 2019) oder Anaconda 2/Anaconda 3 (Visual Studio 2017) wie unter [Installation](installing-python-support-in-visual-studio.md) beschrieben installieren.

::: moniker range=">=vs-2019"
Oder installieren Sie die Standardversion der Python-Interpreter über das Dialogfeld **Umgebung hinzufügen**. Wählen Sie im Fenster **Python-Umgebungen** oder auf der Python-Symbolleiste den Befehl **Umgebung hinzufügen** aus. Legen Sie auf der Registerkarte **Python-Installation** fest, welche Interpreter Sie installieren möchten, und wählen Sie **Installieren** aus.
::: moniker-end

Sie können die in der folgenden Tabelle aufgelisteten Interpreter auch manuell außerhalb des Visual Studio-Installationsprogramms installieren. Wenn Sie beispielsweise Anaconda 3 vor Visual Studio installiert haben, ist keine erneute Installation über das Visual Studio-Installationsprogramm erforderlich. Sie können einen Interpreter auch manuell installieren, wenn beispielsweise eine neuere Version verfügbar ist, die noch nicht im Visual Studio-Installer enthalten ist.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio unterstützt die Python-Version 2.7 und Versionen ab 3.5. Es ist zwar möglich, Code mit Visual Studio zu bearbeiten, der in anderen Versionen von Python geschrieben wurde, aber diese Versionen werden offiziell nicht unterstützt, und Funktionen wie IntelliSense und Debuggen funktionieren möglicherweise nicht.
::: moniker-end

Für **Visual Studio 2015 und frühere Versionen** müssen Sie einen der Interpreter manuell installieren.

Visual Studio (alle Versionen) überprüft die Registrierung gemäß den Angaben unter [PEP 514 - Python registration in the Windows registry (PEP 514 – Registrieren von Python in der Windows-Registrierung)](https://www.python.org/dev/peps/pep-0514/) und erkennt so automatisch jeden installierten Python-Interpreter und die zugehörige Umgebung. Python-Installationen befinden sich in der Regel unter **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32-Bit) und **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64-Bit) innerhalb der Knoten für die Verteilung, z.B. **PythonCore** (CPython) und **ContinuumAnalytics** (Anaconda).

Wenn Visual Studio keine installierte Umgebung findet, folgen Sie den Anweisungen unter [Manuelles Identifizieren einer vorhandenen Umgebung](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

Visual Studio zeigt im Fenster [**Python-Umgebungen**](managing-python-environments-in-visual-studio.md#the-python-environments-window) alle bekannten Umgebungen an und erkennt Updates für vorhandene Interpreter automatisch.

| Interpreter | Beschreibung |
| --- | --- |
| [CPython](https://www.python.org/) | Der „native“ und am häufigsten verwendete Interpreter, verfügbar in 32- und 64-Bit-Versionen (32-Bit wird empfohlen). Er umfasst die neuesten Sprachfeatures, die maximale Python-Paketkompatibilität, vollständige Unterstützung für das Debuggen und Interoperabilität mit [IPython](https://ipython.org/). Siehe auch: [Should I use Python 2 or Python 3? (Sollte ich Python 2 oder Python 3 verwenden?)](https://wiki.python.org/moin/Python2orPython3). Beachten Sie, dass Visual Studio 2015 und frühere Versionen Python 3.6 nicht unterstützen, und den Fehler **Unsupported python version 3.6** (Python-Version 3.6 wird nicht unterstützt) ausgeben können. Verwenden Sie stattdessen Python 3.5 oder frühere Versionen. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Eine .NET-Implementierung von Python, verfügbar in 32-Bit- und 64-Bit-Versionen, die C#-/F#-/Visual Basic-Interoperabilität, Zugriff auf .NET APIs, Python-Standarddebuggen (jedoch kein C++-Debuggen im gemischten Modus) und IronPython-/C#-Debuggen im gemischten Modus bietet. IronPython unterstützt jedoch keine virtuelle Umgebungen. |
| [Anaconda](https://www.continuum.io) | Eine offene Data Science-Plattform, die von Python unterstützt wird und die neueste Version von CPython sowie die meisten der nicht leicht zu installierenden Pakete enthält. Wir empfehlen diesen Interpreter, wenn keine andere Entscheidung möglich ist. |
| [PyPy](https://www.pypy.org/) | Eine leistungsstarke JIT-Implementierung für die Ablaufverfolgung von Python, die gut für Programme mit langer Ausführungszeit und Situationen, in denen Sie Leistungsprobleme identifizieren, jedoch keine anderen Lösungen finden können, geeignet ist. Der Interpreter kann mit Visual Studio verwendet werden, bietet jedoch nur eingeschränkte Unterstützung für erweiterte Debugfunktionen. |
| [Jython](https://www.jython.org/) | Eine Implementierung von Python auf der Java Virtual Machine (JVM). Ähnlich wie bei IronPython kann in Jython ausgeführter Code mit Java-Klassen und -Bibliotheken interagieren, aber möglicherweise viele für CPython vorgesehene Bibliotheken nicht verwenden. Der Interpreter kann mit Visual Studio verwendet werden, bietet jedoch nur eingeschränkte Unterstützung für erweiterte Debugfunktionen. |

Wenn Sie als Entwickler neue Formen der Erkennung für Python-Umgebungen bereitstellen möchten, finden Sie unter [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (PTVS-Umgebungserkennung, github.com) weitere Informationen.

## <a name="move-an-interpreter"></a>Verschieben eines Interpreters

Wenn Sie einen vorhandenen Interpreter an einen neuen Speicherort im Dateisystem verschieben, erkennt Visual Studio diese Änderung nicht automatisch.

- Wenn Sie den Speicherort des Interpreters ursprünglich über das Fenster **Python-Umgebungen** angegeben haben, verwenden Sie die Registerkarte **Konfigurieren** in diesem Fenster, um den neuen Speicherort zu ermitteln. Weitere Informationen finden Sie unter [Manuelles Identifizieren einer vorhandenen Umgebung](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

- Wenn Sie den Interpreter mit einem Installationsprogramm installiert haben, führen Sie die folgenden Schritte aus, um den Interpreter am neuen Speicherort neu zu installieren:

  1. Stellen Sie den Python-Interpreter an seinem ursprünglichen Speicherort wieder her.
  2. Deinstallieren Sie den Interpreter mithilfe des Installationsprogramms; dabei werden die Registrierungseinträge gelöscht.
  3. Installieren Sie den Interpreter am gewünschten Speicherort neu.
  4. Starten Sie Visual Studio neu. Das Programm sollte den neuen Speicherort automatisch erkennen.

Mit diesem Prozess stellen Sie sicher, dass die Registrierungseinträge, die den Speicherort des von Visual Studio verwendeten Interpreters identifizieren, ordnungsgemäß aktualisiert werden. Durch die Verwendung eines Installationsprogramms werden auch Probleme durch möglicherweise vorhandene Nebenwirkungen behoben.

## <a name="see-also"></a>Weitere Informationen

- [Verwalten von Python-Umgebungen](managing-python-environments-in-visual-studio.md)
- [Auswählen eines Interpreters für ein Projekt](selecting-a-python-environment-for-a-project.md)
- [Verwenden von „requirements.txt“ für Abhängigkeiten](managing-required-packages-with-requirements-txt.md)
- [Suchpfade](search-paths.md)
- [Das Fenster „Python-Umgebungen“](python-environments-window-tab-reference.md)
