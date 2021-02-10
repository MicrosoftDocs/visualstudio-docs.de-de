---
title: Symbole für den gemischten Python-C++-Debugmodus
description: Bereitstellung der Funktion zum Laden von Symbolen für vollständiges Debuggen von C++ und Python im gemischten Modus in Visual Studio.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- python
- data-science
ms.openlocfilehash: 52eb7535430248f519654c09924541a6900336cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933088"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>Installieren von Debugsymbolen für Python-Interpreter

Um ein vollständiges Debuggen zu ermöglichen, benötigt der [mixed-mode Python debugger (Python-Debugger für den gemischten Modus)](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) in Visual Studio die Debugsymbole für den Python-Interpreter, um zahlreiche interne Datenstrukturen zu analysieren. Für *python27.dll* ist die entsprechende Symboldatei zum Beispiel *python27.pdb*, und für *python36.dll* ist die Symboldatei *python36.pdb*. Jede Version des Interpreters bietet auch Symboldateien für eine Vielzahl von Modulen.

Mit Visual Studio 2017 und höher installieren die Interpreter Python 3 und Anaconda 3 automatisch ihre entsprechenden Symbole, und Visual Studio findet diese Symbole automatisch. Für Visual Studio 2015 und frühere Versionen oder bei Verwendung anderer Interpreter müssen Sie Symbole separat herunterladen und Visual Studio anschließend über das Dialogfeld **Extras** > **Optionen** auf der Registerkarte **Debuggen** > **Symbole** darauf aufmerksam machen. Diese Schritte werden in den folgenden Abschnitten ausführlich beschrieben.

Visual Studio fordert Sie möglicherweise zur Eingabe auf, wenn diese Symbole benötigt werden. In der Regel ist dies beim Starten einer Debugsitzung im gemischten Modus der Fall. In diesem Fall wird ein Dialogfeld mit zwei Optionen angezeigt:

- Über **Dialogfeld mit Symboleinstellungen öffnen** wird das Dialogfeld **Optionen** auf der Registerkarte **Debuggen** > **Symbole** geöffnet.
- Über **Symbole für meinen Interpreter herunterladen** wird diese aktuelle Dokumentationsseite geöffnet. Klicken Sie in diesem Fall auf **Extras** > **Optionen**, und navigieren Sie zur Registerkarte **Debuggen** > **Symbole**, um fortzufahren.

    ![Aufforderung für Debugsymbole im gemischten Modus](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>Herunterladen von Symbolen

- Python 3.5 und höher: Debugsymbole über das Python-Installationsprogramm erhalten. Wählen Sie **Benutzerdefinierte Installation** und **Weiter**, um zu **Erweiterte Optionen** zu gelangen, und aktivieren Sie dann die Kontrollkästchen für **Debugsymbole herunterladen** und **Debugbinärdateien herunterladen**:

    ![Installationsprogramm für Python 3.x mit Debugsymbolen](media/mixed-mode-debugging-symbols-installer35.png)

    Die Symboldateien (*PDB*) befinden sich dann im Stammordner für die Installation (Symboldateien für einzelne Module befinden sich auch im *DLLs*-Ordner). Aus diesem Grund werden sie von Visual Studio automatisch gefunden, und es sind keine weiteren Schritte erforderlich.

- Python 3.4.x und frühere Versionen: Symbole sind als herunterladbare *ZIP*-Dateien aus [Offizielle Distributionen](#official-distributions) oder [Enthought Canopy](#enthought-canopy) verfügbar. Extrahieren Sie nach dem Download die Dateien in einen lokalen Ordner, z.B. in den Ordner *Symbols* (Symbole) im Python-Ordner.

    > [!Important]
    > Symbole unterscheiden sich zwischen kleineren Builds von Python sowie zwischen 32-Bit- und 64-Bit-Builds, weshalb die Versionen genau übereinstimmen sollten. Erweitern Sie zur Überprüfung des verwendeten Interpreters im **Projektmappen-Explorer** den *Knoten* **Python-Umgebungen** Ihres Projekts, und notieren Sie sich den Umgebungsnamen. Wechseln Sie dann zum *Fenster* **Python-Umgebungen**, und notieren Sie sich den Installationsspeicherort. Öffnen Sie anschließend ein Befehlsfenster an diesem Speicherort, und starten Sie *python.exe*, wodurch die genaue Version angezeigt wird sowie ob es sich um einen 32-Bit- oder 64-Bit-Build handelt.

- Bei jeder anderen Python-Distribution eines Drittanbieters wie z.B. ActiveState Python müssen Sie sich an die Autoren dieser Distribution wenden und sie um die Symbole bitten. WinPython dagegen enthält den Python-Standardinterpreter in unveränderter Form. Verwenden Sie dafür also die Symbole der offiziellen Distribution für die entsprechende Versionsnummer.

## <a name="point-visual-studio-to-the-symbols"></a>Angabe der Symbole in Visual Studio

Wenn Sie Symbole separat heruntergeladen haben, führen Sie folgende Schritte aus, um Visual Studio auf sie aufmerksam zu machen. Wenn Sie Symbole mit dem Installationsprogramm von Python 3.5 oder höher installiert haben, werden sie von Visual Studio automatisch gefunden.

1. Klicken Sie auf **Extras** > **Optionen**, und navigieren Sie zu **Debuggen** > **Symbole**.

1. Klicken Sie in der Symbolleiste auf die Schaltfläche **Hinzufügen** (siehe unten), geben Sie den Ordner ein, in dem Sie die heruntergeladenen Symbole erweitert haben (in dem sich *python.pdb* befindet, also z.B. *c:\python34\Symbols*), und klicken Sie auf **OK**.

    ![Symboloptionen für den Debugger im gemischten Modus](media/mixed-mode-debugging-symbols.png)

1. Während einer Debugsitzung werden Sie von Visual Studio möglicherweise auch aufgefordert, den Speicherort einer Quelldatei für den Python-Interpreter anzugeben. Wenn Sie Quelldateien heruntergeladen haben (z. B. von [python.org/downloads](https://www.python.org/downloads/)), können Sie natürlich auch diese angeben.

> [!Note]
> Die Funktionen zum Zwischenspeichern von Symbolen im Dialogfeld werden verwendet, um einen lokalen Cache für Symbole zu erstellen, die von einer Onlinequelle bezogen wurden. Diese Funktionen werden für die Symbole des Python-Interpreters nicht benötigt, da diese bereits lokal vorhanden sind. In jedem Fall finden Sie weitere Informationen unter [Angeben von Symbolen und Quelldateien im Visual Studio-Debugger](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="official-distributions"></a>Offizielle Distributionen

| Python-Version | Downloads |
| --- | --- |
| 3.5 und höher | Installieren Sie Symbole mit dem Python-Installationsprogramm. |
| 3.4.4 | [32 Bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32 Bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32 Bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32 Bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32 Bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32 Bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32 Bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32 Bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32 Bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32 Bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32 Bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.15 | [32 Bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15.amd64-pdb.zip) |
| 2.7.14 | [32 Bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14.amd64-pdb.zip) |
| 2.7.13 | [32 Bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13.amd64-pdb.zip) |
| 2.7.12 | [32 Bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12.amd64-pdb.zip) |
| 2.7.11 | [32 Bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32 Bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32 Bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32 Bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32 Bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32 Bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32 Bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32 Bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32 Bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32 Bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32 Bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |

## <a name="enthought-canopy"></a>Enthought Canopy

Enthought Canopy stellt Symbole für die zugehörigen Binärdateien ab Version 1.2 bereit. Die Symbole werden automatisch zusammen mit der Distribution installiert, Sie müssen jedoch den Ordner mit den Symbolen manuell zum Symbolpfad hinzufügen, wie oben beschrieben. Bei einer typischen benutzerbezogenen Installation von Canopy befinden sich die Symbole unter *%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts* (64-Bit-Version) und unter *%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts* (32-Bit-Version).

Enthought Canopy 1.1 und früher sowie Enthought Python Distribution (EPD) stellen keine Interpretersymbole bereit und sind daher nicht mit dem Debuggen im gemischten Modus kompatibel.
