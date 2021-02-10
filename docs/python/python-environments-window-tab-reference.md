---
title: Referenz zum Fenster „Python-Umgebungen“
description: Dieser Artikel beschreibt jede der Registerkarten, die im Fenster „Python-Umgebungen“ in Visual Studio angezeigt werden.
ms.date: 03/18/2019
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d00f8cc05e4a2a2ce1e947207997cc2e46d9d9f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912378"
---
# <a name="python-environments-window-tabs-reference"></a>Referenz zu den Registerkarten im Fenster „Python-Umgebungen“

So öffnen Sie das Fenster **Python-Umgebungen**:

- Wählen Sie den Menübefehl **Ansicht** > **Weitere Fenster** > **Python-Umgebungen** aus.
- Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **Python-Umgebungen** für ein Projekt, und wählen Sie **Alle Python-Umgebungen anzeigen** aus.

Wenn Sie das Fenster **Python-Umgebungen** weit genug erweitern, werden diese Optionen als Registerkarten angezeigt, was Ihre Arbeit damit erleichtern kann. Zur besseren Übersicht werden die Registerkarten in diesem Artikel in der erweiterten Ansicht angezeigt.

::: moniker range="vs-2017"
![Erweiterte Ansicht des Fensters „Python-Umgebungen“](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Erweiterte Ansicht des Fensters „Python-Umgebungen“](media/environments/environments-expanded-view-2019.png)
::: moniker-end

## <a name="overview-tab"></a>Registerkarte „Übersicht“

Bietet grundlegende Informationen und Befehle für die Umgebung:

::: moniker range="vs-2017"
![Registerkarte „Übersicht“ von Python-Umgebungen](media/environments/environments-overview-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Registerkarte „Übersicht“ von Python-Umgebungen](media/environments/environments-overview-tab-2019.png)
::: moniker-end

| Befehl | Beschreibung |
| --- | --- |
| **Diese Umgebung zum Standard für neue Projekte machen** | Legt die aktive Umgebung fest, die möglicherweise dazu führt, dass Visual Studio (2017 Version 15.5 und früher) kurzzeitig nicht mehr reagiert, während es die IntelliSense-Datenbank lädt. Umgebungen mit vielen Paketen reagieren möglicherweise längere Zeit nicht mehr. |
| **Website des Verteilers besuchen** | Öffnen eine von der Python-Verteilung bereitgestellt URL in einem Browser. Python 3.x öffnet beispielsweise python.org. |
| **Interaktives Fenster öffnen** | Öffnet das [interaktive Fenster (REPL)](python-interactive-repl-in-visual-studio.md) für diese Umgebung in Visual Studio und wendet alle [Startskripts (siehe unten)](#startup-scripts) an. |
| **Interaktive Skripts untersuchen** | Siehe [Startskripte](#startup-scripts). |
| **Interaktiven IPython-Modus verwenden** | Wenn diese Option aktiviert ist, wird das **interaktive** Fenster standardmäßig mit IPython geöffnet. Dadurch sind Inline-Plots und erweiterte IPython-Syntax möglich, wie z.B. `name?` zum Anzeigen der Hilfe und `!command` für Shellbefehle. Diese Option wird empfohlen, wenn Sie eine Verteilung von Anaconda verwenden, da diese zusätzliche Pakete erfordert. Weitere Informationen finden Sie unter [Verwenden von IPython im interaktiven Fenster](interactive-repl-ipython.md). |
| **In PowerShell öffnen** | Öffnet den Interpreter in einem Befehlsfenster von PowerShell. |
| (Ordner- und Programmverknüpfungen) | Bieten Ihnen schnellen Zugriff auf den Installationsordner der Umgebung und die Interpreter *python.exe* und *pythonw.exe*. Ersterer wird im Windows Explorer geöffnet, die anderen beiden in einem Konsolenfenster. |

### <a name="startup-scripts"></a>Startskripte

Beim Verwenden von interaktiven Fenstern in ihrem alltäglichen Workflow entwickeln Sie mit hoher Wahrscheinlichkeit Hilfsfunktionen, die Sie häufig verwenden. Möglicherweise erstellen Sie z.B. eine Funktion, die einen Datenrahmen in Excel öffnet. Dann können Sie den Code als Startskript speichern, sodass dieser immer über das **interaktive** Fenster verfügbar ist.

Startskripts enthalten Code, der vom **interaktiven** Fenster automatisch geladen und ausgeführt wird, einschließlich Importe, Funktionsdefinitionen und vieles mehr. Auf derartige Skripts kann auf zwei Weisen verwiesen werden:

1. Wenn Sie eine Umgebung installieren, erstellt Visual Studio einen Ordner *Documents\Visual Studio \<version>\Python Scripts\\\<environment>* , wobei &lt;Version&gt; der Visual Studio-Version (wie etwa 2017 oder 2019) und &lt;Environment&gt; dem Namen der Umgebung entspricht. Sie können mit dem Befehl **Interaktive Skripts untersuchen** ganz leicht zum umgebungsspezifischen Ordner navigieren. Wenn Sie das **interaktive** Fenster für diese Umgebung starten, lädt es alle hier gefundenen *.py*-Dateien und führt diese in alphabetischer Reihenfolge aus.

1. Das Steuerelement **Skripts** auf der Registerkarte **Extras** > **Optionen** > **Python** > **Interaktives Fenster** (siehe Optionen für das [interaktive](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options) Fenster) gibt einen zusätzlichen Ordner für Startskripts an, die in allen Umgebungen geladen und ausgeführt werden. Diese Funktion funktioniert aktuell noch nicht.

## <a name="configure-tab"></a>Registerkarte „Konfigurieren“

Wenn die Registerkarte **Konfigurieren** verfügbar ist, enthält sie die in der folgenden Tabelle beschriebenen Details. Wenn diese Registerkarte nicht vorhanden ist, bedeutet dies, dass alle Details von Visual Studio automatisch verwaltet werden.

::: moniker range="vs-2017"
![Registerkarte „Konfigurieren“ von Python-Umgebungen](media/environments/environments-configure-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Registerkarte „Konfigurieren“ von Python-Umgebungen](media/environments/environments-configure-tab-2019.png)
::: moniker-end

| Feld | Beschreibung |
| --- | --- |
| **Beschreibung** | Der Name für die Umgebung. |
| **Präfixpfad** | Der Speicherort des Basisordners des Interpreters. Durch Festlegen dieses Werts und Klicken auf **Automatisch erkennen** versucht Visual Studio, die anderen Felder für Sie auszufüllen. |
| **Interpreterpfad** | Der Pfad zur ausführbaren Datei des Interpreters, üblicherweise der Präfixpfad gefolgt von **python.exe**. |
| **Fenstermodus-Interpreter** | Der Pfad zur ausführbaren Datei ohne Konsole, häufig der Präfixpfad gefolgt von **pythonw.exe**. |
| **Bibliothekspfad**<br/>(sofern verfügbar) | Gibt den Stamm der Standardbibliothek an. Dieser Wert kann allerdings ignoriert werden, wenn Visual Studio einen genaueren Pfad vom Interpreter anfordern kann. |
| **Sprachversion** | Wird im Dropdownmenü ausgewählt |
| **Architektur** | Wird normalerweise automatisch erkannt und ausgefüllt, andernfalls **32-Bit** oder **64-Bit**. |
| **Pfadumgebungsvariable** | Die Umgebungsvariable, die der Interpreter verwendet, um Suchpfade zu finden. Visual Studio ändert den Wert der Variablen, wenn Python gestartet wird, sodass sie die Suchpfade des Projekts enthält. In der Regel sollte diese Eigenschaft auf **PYTHONPATH** festgelegt werden, aber einige Interpreter verwenden einen anderen Wert. |

## <a name="packages-tab"></a>Registerkarte „Pakete“

*In früheren Versionen auch als „pip“ bezeichnet.*

Verwaltet die Pakete, die mithilfe von Pip (die Registerkarte **Pakete (PyPI)** ) oder Conda (die Registerkarte **Pakete (Conda)** für Conda-Umgebungen in Visual Studio 2017 Version 15.7 und höher) in der Umgebung installiert werden. Auf dieser Registerkarte können Sie zudem neue Pakete einschließlich der zugehörigen Abhängigkeiten suchen und installieren.

Bereits installierte Pakete werden mit Steuerelementen zum Aktualisieren (nach unten gerichteter Pfeil) und Deinstallieren (X in einem Kreis) des Pakets angezeigt:

![Registerkarte mit Paketen in Python-Umgebungen](media/environments/environments-pip-tab-controls.png)

Bei Eingabe eines Suchbegriffs werden sowohl die Liste der installierten Pakete als auch Pakete, die von PyPi aus installiert werden können, gefiltert.

::: moniker range="vs-2017"
![Registerkarte mit Python-Umgebungspaketen mit einer Suche nach „num“](media/environments/environments-pip-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Registerkarte mit Python-Umgebungspaketen mit einer Suche nach „num“](media/environments/environments-pip-tab-2019.png)
::: moniker-end

In der obigen Abbildung können Sie erkennen, dass die Suchergebnisse einige Pakete anzeigt, die dem Suchbegriff entsprechen. Der erste Eintrag in der Liste ist jedoch ein Befehl, um **pip install \<name>** direkt auszuführen. Wenn Sie sich auf der Registerkarte **Pakete (Conda)** befinden, wird Ihnen stattdessen **conda install \<name>** angezeigt:

::: moniker range="vs-2017"
![Registerkarte „Pakete (Conda)“, auf der ein Conda-Installationsbefehl angezeigt wird](media/environments/environments-conda-tab-install.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Registerkarte „Pakete (Conda)“, auf der ein Conda-Installationsbefehl angezeigt wird](media/environments/environments-conda-tab-install-2019.png)
::: moniker-end

In beiden Fällen können Sie die Installation anpassen, indem Sie im Suchfeld Argumente nach dem Paketnamen hinzufügen. Wenn Sie Argumente einschließen, zeigen die Suchergebnisse **pip install** oder **conda install** gefolgt von den Inhalten des Suchfelds an:

::: moniker range="vs-2017"
![Verwenden von Argumenten in pip- und Conda-Installationsbefehlen](media/environments/environments-pip-tab-arguments.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Verwenden von Argumenten in pip- und Conda-Installationsbefehlen](media/environments/environments-pip-tab-arguments-2019.png)
::: moniker-end

Durch das Installieren eines Pakets wird ein Unterordner im *Lib*-Ordner der Umgebung im Dateisystem erstellt. Wenn bei Ihnen beispielsweise Python 3.6 in *c:\Python36* installiert ist, werden Pakete in *c:\Python36\Lib* installiert; wenn Anaconda3 in *c:\Programme\Anaconda3* installiert ist, werden Pakete in *c:\Programme\Anaconda3\Lib* installiert. Bei Conda-Umgebungen werden Pakete im Ordner dieser Umgebung installiert.

### <a name="grant-administrator-privileges-for-package-install"></a>Erteilen von Administratorrechten für die Paketinstallation

Wenn Sie Pakete in einer Umgebung installieren, die sich in einem geschützten Bereich des Dateisystems befindet (z.B. *c:\Program Files\Anaconda3\Lib*), muss Visual Studio `pip install` mit erhöhten Rechten ausführen, damit die Unterordner des Pakets erstellt werden können. Wenn erhöhte Rechte erforderlich sind, zeigt Visual Studio folgende Aufforderung an: **Es sind möglicherweise Administratorberechtigungen erforderlich, um Pakete für diese Umgebung zu installieren, zu aktualisieren oder zu entfernen**:

![Eingabeaufforderung für erhöhte Rechte](media/environments/environments-pip-elevate.png)

**Jetzt Rechte erweitern** erteilt Administratorrechte an „pip“ für einen einzigen Vorgang, auch gemäß Aufforderungen des Betriebssystems nach Berechtigungen. Wenn Sie **Ohne Administratorberechtigungen fortfahren** auswählen, wird die Installation des Pakets versucht, „pip“ schlägt allerdings beim Erstellen von Ordnern fehl. Die Ausgabe kann z. B. so aussehen: **error: could not create 'C:\Program Files\Anaconda3\Lib\site-packages\png.py' (Fehler: 'C:\Programme\Anaconda3\Lib\site-packages\png.py' konnte nicht erstellt werden. Berechtigung verweigert)** .

Wenn Sie **Beim Installieren oder Entfernen von Paketen immer Rechte erweitern** auswählen, wird verhindert, dass das Dialogfeld für die entsprechende Umgebung angezeigt wird. Wenn Sie das Dialogfeld wieder anzeigen möchten, wählen Sie unter **Extras** > **Optionen** > **Python** > **Allgemein** die Schaltfläche **Alle dauerhaft ausgeblendeten Dialogfelder zurücksetzen** aus.

Auf der gleichen Registerkarte **Optionen** können Sie auf **„pip“ immer als Administrator ausführen** klicken, um das Dialogfeld für alle Umgebungen zu unterdrücken. Weitere Informationen finden Sie unter [Optionen > Registerkarte „Allgemein“](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Sicherheitseinschränkungen bei älteren Versionen von Python

Wenn Sie Python 2.6, 3.1 oder 3.2 verwenden, zeigt Visual Studio die Warnung **Aufgrund neuer Sicherheitseinschränkungen funktioniert die Installation über das Internet bei dieser Version von Python möglicherweise nicht** an:

![Warnung zu pip-Installationseinschränkungen mit älteren Versionen von Python](media/environments/environments-old-version-restriction.png)

Die Warnung wird angezeigt, weil `pip install` für ältere Versionen von Python keine Unterstützung für TLS 1.2 (Transport Layer Security) enthält. Dieses Protokoll ist jedoch erforderlich, um Pakete von der Paketquelle „pypi.org“ herunterzuladen. Benutzerdefinierte Python-Builds unterstützen TLS 1.2 möglicherweise. In diesem Fall kann `pip install` funktionieren.

Möglicherweise können Sie das entsprechende *get-pip.py*-Skript für ein Paket von [bootstrap.pypa.io](https://bootstrap.pypa.io/) herunterladen, ein Paket von [pypi.org](https://pypi.org/) manuell herunterladen und das Paket dann über die lokale Kopie installieren.

Es wird jedoch empfohlen, einfach ein Upgrade auf Python 2.7 oder 3.3 oder höher durchzuführen. In diesem Fall wird die Warnung nicht angezeigt.

::: moniker range="vs-2017"
## <a name="intellisense-tab"></a>Registerkarte „IntelliSense“

Zeigt den aktuellen Status der IntelliSense-Vervollständigungsdatenbank:

![Registerkarte „IntelliSense“ von Python-Umgebungen](media/environments/environments-intellisense-tab.png)

- In Visual Studio 2017 Version 15.5 und früher hängen IntelliSense-Vervollständigungen von einer Datenbank ab, die für diese Bibliothek kompiliert wurde. Das Erstellen der Datenbank wird im Hintergrund ausgeführt, wenn eine Bibliothek installiert wird, kann aber eine Weile dauern und ist möglicherweise noch nicht abgeschlossen, wenn Sie mit dem Schreiben von Code beginnen.
- Visual Studio 2017 Version 15.6 und höher verwendet eine schnellere Methode, um Vervollständigungen bereitzustellen, die nicht standardmäßig von der Datenbank abhängen. Deshalb trägt die Registerkarte die Bezeichnung **IntelliSense [Datenbank deaktiviert]** . Sie können die Datenbank durch Deaktivieren der Option **Extras** > **Optionen** > **Python** > **Experimentell** > **Use new style IntelliSense for environments (Neues IntelliSense für Umgebungen verwenden)** aktivieren.

Wenn Visual Studio eine neue Umgebung erkennt (oder wenn Sie eine hinzufügen), wird die Datenbank automatisch kompiliert, indem die Quelldateien der Bibliothek analysiert werden. Dieser Prozess kann eine Minute oder bis zu einer Stunde oder noch länger dauern, je nachdem, was installiert ist. (Zu Anaconda gehören z.B. viele Bibliotheken, und es dauert einige Zeit, die Datenbank zu kompilieren.) Wenn der Vorgang abgeschlossen ist, erhalten Sie detaillierte IntelliSense-Daten und müssen die Datenbank erst erneut aktualisieren (mit der Schaltfläche **DB aktualisieren**), wenn Sie weitere Bibliotheken installieren.

Bibliotheken, für die noch keine Daten kompiliert wurden, werden mit einem **!** gekennzeichnet. Wenn die Datenbank einer Umgebung nicht vollständig ist, wird daneben auch ein **!** in der Liste der wichtigsten Umgebungen angezeigt.

::: moniker-end

## <a name="see-also"></a>Siehe auch

- [Verwalten von Python-Umgebungen in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Auswählen eines Interpreters für ein Projekt](selecting-a-python-environment-for-a-project.md)
- [Verwenden von „requirements.txt“ für Abhängigkeiten](managing-required-packages-with-requirements-txt.md)
- [Suchpfade](search-paths.md)
