---
title: Verwalten von Python-Umgebungen und -Interpretern
description: Verwalten Sie globale, virtuelle und Conda-Umgebungen im Fenster „Python-Umgebungen“. Dort können Sie Python-Interpreters und -Pakete installieren und Visual Studio-Projekten Umgebungen zuweisen.
ms.date: 08/06/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- python
- data-science
ms.openlocfilehash: efd75e79d7c015539dfe045f7b0a3b266cfb4756
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923754"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Erstellen und Verwalten von Python-Umgebungen in Visual Studio

Eine **Python-Umgebung** ist ein Kontext, in dem Sie Python-Code ausführen und der globale, virtuelle und Conda-Umgebungen umfasst. Eine Umgebung besteht aus einem Interpreter, einer Bibliothek (in der Regel die Python-Standardbibliothek) und mehreren installierten Paketen. Diese Komponenten bestimmen gemeinsam, welche Sprachkonstrukte und Syntax gültig sind, auf welche Betriebssystemfunktionen Sie zugreifen können und welche Pakete Sie verwenden können.

In Visual Studio unter Windows verwenden Sie das Fenster **Python-Umgebungen** wie in diesem Artikel beschrieben zum Verwalten der Umgebungen und zum Auswählen einer Standardumgebung für neue Projekte. Andere Aspekte von Umgebungen werden in den folgenden Artikeln beschrieben:

- Anstelle der Standardumgebung können Sie [eine spezifische Umgebung](selecting-a-python-environment-for-a-project.md) für beliebige Projekte auswählen.

- Ausführliche Informationen zum Erstellen und Verwenden virtueller Umgebungen für Python-Projekte finden Sie unter [Verwenden von virtuellen Umgebungen](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Wenn Sie Pakete in einer Umgebung installieren möchten, verwenden Sie die [Referenz zur Registerkarte „Pakete“](python-environments-window-tab-reference.md#packages-tab).

- Informationen zum Installieren anderer Python-Interpretern finden Sie unter [Installieren von Python-Interpretern](installing-python-interpreters.md). Im Allgemeinen werden neue Installationen und Umgebungen von Visual Studio erkannt und im Fenster **Python-Umgebungen** angezeigt, wo Sie sie zur Verwendung für Projekte auswählen können, wenn Sie ein Installationsprogramm für eine Python-Hauptverteilung herunterladen und ausführen.

Wenn Sie noch nicht mit Python in Visual Studio vertraut sind, finden Sie das allgemeine Hintergrundwissen in den folgenden Artikeln:

- [Arbeiten mit Python in Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Installieren von Python-Unterstützung für Visual Studio](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> Sie können Umgebungen für Python-Code nicht verwalten, der nur als Ordner über **Datei** > **Öffnen** > **Ordner** geöffnet wurde. Stattdessen [erstellen Sie ein Python-Projekt aus vorhandenem Code](quickstart-01-python-in-visual-studio-project-from-existing-code.md), um die Umgebungsfeatures von Visual Studio nutzen zu können.
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Sie können Umgebungen für Python-Code verwalten, der als Ordner über **Datei** > **Öffnen** > **Ordner** geöffnet wurde. Mithilfe der Python-Symbolleiste können Sie zwischen allen erkannten Umgebungen wechseln und außerdem eine neue Umgebung hinzufügen. Die Umgebungsinformationen werden in der Datei „PythonSettings.json“ im Ordner „.vs“ des Arbeitsbereichs gespeichert.
::: moniker-end

## <a name="the-python-environments-window"></a>Das Fenster „Python-Umgebungen“

Die Umgebungen, die Visual Studio bekannt sind, werden im Fenster **Python-Umgebungen** angezeigt. Zum Öffnen dieses Fensters können Sie eine der folgenden Methoden verwenden:

- Wählen Sie den Menübefehl **Ansicht** > **Weitere Fenster** > **Python-Umgebungen** aus.
- Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **Python-Umgebungen** für ein Projekt, und wählen Sie **Alle Python-Umgebungen anzeigen** aus:

    ::: moniker range="vs-2017"
    ![Befehl „Alle Umgebungen anzeigen“ im Projektmappen-Explorer](media/environments/environments-view-all.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Befehl „Alle Umgebungen anzeigen“ im Projektmappen-Explorer](media/environments/environments-view-all-2019.png)
    ::: moniker-end

In jedem Fall wird das Fenster **Python-Umgebungen** mit dem **Projektmappen-Explorer** angezeigt:

::: moniker range="vs-2017"
![Fenster „Python-Umgebungen“](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Fenster „Python-Umgebungen“](media/environments/environments-default-view-2019.png)
::: moniker-end

Visual Studio sucht mithilfe der Registrierung nach installierten globalen Umgebungen (gemäß [PEP 514](https://www.python.org/dev/peps/pep-0514/)) sowie nach virtuellen Umgebungen und Conda-Umgebungen (siehe [Typen von Umgebungen](#types-of-environments)). Wenn eine Umgebung wider Erwarten nicht in der Liste angezeigt wird, finden Sie weitere Informationen unter [Manuelles Identifizieren einer vorhandenen Umgebung](#manually-identify-an-existing-environment).

Wenn Sie eine Umgebung in der Liste auswählen, werden in Visual Studio verschiedene Eigenschaften und Befehle der Umgebung auf der Registerkarte **Übersicht** angezeigt. Wie Sie beispielsweise im obigen Bild sehen können, ist der Speicherort des Interpreters *C:\Python36-32*. Die vier Befehle am unteren Rand der Registerkarte **Übersicht** öffnen jeweils eine Eingabeaufforderung, in der der Interpreter ausgeführt wird. Weitere Informationen finden Sie unter [Referenz zu den Registerkarten im Fenster „Python-Umgebungen“: Übersicht](python-environments-window-tab-reference.md#overview-tab).

Verwenden Sie die Dropdownliste unter der Liste von Umgebungen, um zu verschiedenen Registerkarten wie **Pakete** oder **IntelliSense** zu wechseln. Diese Registerkarten werden auch in der [Referenz zu den Registerkarten im Fenster „Python-Umgebungen“](python-environments-window-tab-reference.md) beschrieben.

Die Auswahl einer Umgebung beeinflusst nicht ihre Beziehung zu Projekten. Die Standardumgebung, die in der Liste in Fettschrift aufgeführt wird, ist die, die Visual Studio für alle neuen Projekte verwendet. Verwenden Sie den Befehl **Als Standardumgebung für neue Projekte festlegen**, um eine andere Umgebung für neue Projekte zu verwenden. Sie können innerhalb des Kontexts eines Projekts immer eine spezifische Umgebung auswählen. Weitere Informationen finden Sie unter [Zuweisen einer Umgebung für ein Projekt](selecting-a-python-environment-for-a-project.md).

Rechts neben jeder aufgelisteten Umgebung befindet sich ein Steuerelement, das ein **interaktives** Fenster für die jeweilige Umgebung öffnet. (In Visual Studio 2017, Version 15.5 und niedriger, wird ein weiteres Steuerelement angezeigt, das die IntelliSense-Datenbank der jeweiligen Umgebung aktualisiert. Details zur Datenbank finden Sie unter [Referenz zu den Registerkarten im Fenster „Python-Umgebungen“](python-environments-window-tab-reference.md)).

::: moniker range="vs-2017"
> [!Tip]
> Wenn Sie das Fenster **Python-Umgebungen** weit genug erweitern, werden die Umgebungen ausführlicher angezeigt, was Ihre Arbeit erleichtern kann.
>
> ![Erweiterte Ansicht des Fensters „Python-Umgebungen“](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Tip]
> Wenn Sie das Fenster **Python-Umgebungen** weit genug erweitern, werden die Umgebungen ausführlicher angezeigt, was Ihre Arbeit erleichtern kann.
>
> ![Erweiterte Ansicht des Fensters „Python-Umgebungen“](media/environments/environments-expanded-view-2019.png)
::: moniker-end

> [!Note]
> Obwohl Visual Studio die Option „system-site-packages“ beachtet, gibt es keine Möglichkeit, sie in Visual Studio zu ändern.

### <a name="what-if-no-environments-appear"></a>Was geschieht, wenn keine Umgebungen angezeigt werden?

Wenn keine Umgebungen angezeigt werden, bedeutet dies, dass Visual Studio keine Python-Installationen an den standardmäßigen Speicherorten gefunden hat. Angenommen, Sie haben Visual Studio 2017 oder eine höhere Version installiert, aber alle Interpreteroptionen in den Installeroptionen für die Python-Workload gelöscht. Ähnlich verhält es sich, wenn Sie während der Installation von Visual Studio 2015 oder niedriger keinen Interpreter manuell installiert haben (siehe [Installieren von Python-Interpretern](installing-python-interpreters.md)).

Wenn Sie wissen, dass ein Python-Interpreter auf Ihrem Computer vorhanden ist, Visual Studio (beliebige Version) diesen jedoch nicht erkennt, verwenden Sie den Befehl **+ Custom** (+ Benutzerdefiniert), um dessen Speicherort manuell anzugeben. Lesen Sie hierzu den nächsten Abschnitt [Manuelles Identifizieren einer vorhandenen Umgebung](#manually-identify-an-existing-environment).

> [!Tip]
> Visual Studio erkennt Updates auf einen vorhandenen Interpreter, z.B. ein Upgrade von Python 2.7.11 auf 2.7.14 mit den Installationsprogrammen von python.org. Während des Installationsvorgangs wird die ältere Umgebung aus der Liste der **Python-Umgebungen** entfernt und dann durch das Update ersetzt.
>
> Wenn Sie jedoch einen Interpreter und dessen Umgebung manuell über das Dateisystem verschieben, ist Visual Studio der neue Speicherort nicht bekannt. Weitere Informationen finden Sie unter [Verschieben eines Interpreters](installing-python-interpreters.md#move-an-interpreter).

### <a name="types-of-environments"></a>Typen von Umgebungen

Visual Studio kann mit globalen, virtuellen und Conda-Umgebungen arbeiten.

#### <a name="global-environments"></a>Globale Umgebungen

Jede Python-Installation (z.B. Python 2.7, Python 3.6, Python 3.7, Anaconda 4.4.0 usw.; siehe [Installieren von Python-Interpretern](installing-python-interpreters.md)) verwaltet ihre eigene *globale Umgebung*. Jede Umgebung besteht aus dem spezifischen Python-Interpreter, einer Standardbibliothek, einer Reihe von vorinstallierten Paketen sowie jeglichen zusätzlichen Paketen, die Sie installieren, während die Umgebung aktiviert ist. Das Installieren eines Pakets in einer globalen Umgebung macht das Paket für alle Projekte verfügbar, die dieselbe Umgebung verwenden. Wenn sich die Umgebung in einem geschützten Bereich des Dateisystems befindet (z.B. in *C:\Programme*), sind für die Installation von Paketen Administratorrechte erforderlich.

Globale Umgebungen sind für alle Projekte auf dem Computer verfügbar. Wählen Sie in Visual Studio eine globale Umgebung als Standardumgebung aus, die für alle Projekte genutzt wird, wenn Sie keine spezifische Umgebung für ein Projekt aussuchen. Weitere Informationen finden Sie unter [Zuweisen einer Umgebung für ein Projekt](selecting-a-python-environment-for-a-project.md).

#### <a name="virtual-environments"></a>Virtuelle Umgebungen

Obwohl die Arbeit in einer globalen Umgebung eine einfache Möglichkeit zum Einstieg darstellt, wird diese Umgebung im Laufe der Zeit mit vielen verschiedenen Paketen überladen, die Sie für verschiedene Projekte installieren. Ein solches Durcheinander erschwert das Testen von Anwendungen für spezifische Pakete mit bekannten Versionen, weshalb es sich dabei um die Art von Umgebung handelt, die sich eher auf einem Buildserver oder Webserver eignet. Außerdem können Konflikte auftreten, wenn zwei Projekte inkompatible Pakete oder verschiedene Versionen erfordern.

Aus diesem Grund erstellen Entwickler oft eine *virtuelle Umgebung* für ein Projekt. Eine virtuelle Umgebung ist ein Unterordner in einem Projekt, der eine Kopie eines spezifischen Interpreters enthält. Wenn Sie die virtuelle Umgebung aktivieren, werden alle Pakete, die Sie installieren, nur in dem Unterordner der Umgebung installiert. Wenn Sie dann ein Python-Programm in dieser Umgebung ausführen, können Sie sich sicher sein, dass es nur für diese spezifischen Pakete ausgeführt wird.

Visual Studio stellt direkte Unterstützung für das Erstellen einer virtuellen Umgebung für ein Projekt bereit. Wenn Sie beispielsweise ein Projekt öffnen, dass eine *requirements.txt*-Datei enthält, oder ein Projekt aus einer Vorlage erstellen, die diese Datei enthält, werden Sie von Visual Studio dazu aufgefordert, eine virtuelle Umgebung automatisch zu erstellen und diese Abhängigkeiten zu installieren.

In einem offenen Projekt können Sie jederzeit eine neue virtuelle Umgebung erstellen. Erweitern Sie im **Projektmappen-Explorer** den Projektknoten, klicken Sie mit der rechten Maustaste auf **Python-Umgebungen**, und klicken Sie dann auf „Virtuelle Umgebung hinzufügen“. Weitere Informationen finden Sie unter [Erstellen einer virtuellen Umgebung](./selecting-a-python-environment-for-a-project.md?view=vs-2019&preserve-view=true#create-a-virtual-environment-1).

Visual Studio enthält auch einen Befehl, um eine *requirements.txt*-Datei aus einer virtuellen Umgebung zu generieren. Dies vereinfacht das erneute Erstellen der Umgebung auf anderen Computern. Weitere Informationen finden Sie unter [Verwenden von virtuellen Umgebungen](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

#### <a name="conda-environments"></a>Conda-Umgebungen

Eine Conda-Umgebung ist eine mit dem `conda`-Tool oder der in Visual Studio 2017 ab Version 15.7 integrierten Conda-Verwaltung erstellte Umgebung. (Anaconda oder Miniconda erforderlich; die über den Visual Studio-Installer verfügbar sind; siehe [Installieren von Python-Unterstützung für Visual Studio unter Windows](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017).)

::: moniker range="vs-2017"

1. Wählen Sie **+ Conda-Umgebung erstellen** im Fenster **Python-Umgebungen** aus, wodurch eine Registerkarte **Neue Conda-Umgebung erstellen** geöffnet wird:

    ![Erstellen-Registerkarte für eine neue Conda-Umgebung](media/environments/environments-conda-1.png)

1. Geben Sie in das Feld **Name** einen Namen für die Umgebung ein, wählen Sie im Feld **Python** einen Python-Basisinterpreter aus, und klicken Sie auf **Erstellen**.

1. Im Fenster **Ausgabe** werden der Fortschritt für die neue Umgebung sowie nach Abschluss der Erstellung einige CLI-Anweisungen angezeigt:

    ![Erfolgreiche Erstellung einer Conda-Umgebung](media/environments/environments-conda-2.png)

1. In Visual Studio können Sie eine Conda-Umgebung für ein Projekt wie jede andere Umgebung aktivieren, wie unter [Auswählen einer Umgebung für ein Projekt](selecting-a-python-environment-for-a-project.md) beschrieben.

1. Verwenden Sie zum Installieren von Paketen in der Umgebung die Registerkarte [Pakete](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

::: moniker range=">=vs-2019"

1. Wählen Sie im Fenster **Python-Umgebungen** (oder über die Python-Symbolleiste) die Option **+ Umgebung hinzufügen** aus. Daraufhin wird das Dialogfeld **Umgebung hinzufügen** geöffnet. Wählen Sie in diesem Dialogfeld die Registerkarte **Conda-Umgebung** aus:

    ![Registerkarte „Conda-Umgebung“ im Dialogfeld „Umgebung hinzufügen“](media/environments/environments-conda-1-2019.png)

1. Konfigurieren Sie die folgenden Felder:

    | Feld | Beschreibung |
    | --- | --- |
    | Projekt | Das Projekt, in dem die Umgebung erstellt werden soll (falls eine Visual Studio-Projektmappe mehrere Projekte enthält) |
    | name | Der Name für die Conda-Umgebung |
    | Pakete hinzufügen von | Wählen Sie **Environment file** (Umgebungsdatei) aus, wenn Sie eine Datei vom Typ *environment.yml* besitzen, in der die Abhängigkeiten beschrieben sind. Wählen Sie alternativ **One or more Anaconda package names** (Mindestens ein Anaconda-Paketname) aus, und geben Sie mindestens ein Python-Paket bzw. eine Python-Version im Feld unten an. Die Paketliste weist Conda zum Erstellen einer Python-Umgebung an. Verwenden Sie zum Installieren der aktuellen Python-Version `python` und zum Installieren einer bestimmten Version `python=,major>.<minor>` wie in `python=3.7`. Sie können auch die Paketschaltfläche verwenden, um Python-Versionen und allgemeine Pakete aus verschiedenen Menüs auszuwählen. |
    | Als aktuelle Umgebung festlegen | Aktiviert die neue Umgebung nach der Erstellung im ausgewählten Projekt. |
    | Als Standardumgebung für neue Projekte festlegen | Dient zum automatischen Festlegen und Aktivieren der Conda-Umgebung in allen neuen Projekten, die in Visual Studio erstellt werden. Diese Option entspricht der Verwendung von **Als Standardumgebung für neue Projekte festlegen** im Fenster **Python-Umgebungen**. |
    | In Fenster „Python-Umgebungen“ anzeigen | Gibt an, ob das Fenster **Python-Umgebungen** nach dem Erstellen der Umgebung angezeigt werden soll. |

    > [!Important]
    > Geben Sie beim Erstellen einer Conda-Umgebung unbedingt mindestens eine Python-Version oder ein Python-Paket mithilfe von `environments.yml` oder der Paketliste an. Dadurch wird sichergestellt, dass die Umgebung eine Python-Laufzeit enthält. Andernfalls ignoriert Visual Studio die Umgebung: Die Umgebung wird nicht im Fenster **Python-Umgebungen** angezeigt, ist nicht als aktuelle Umgebung für ein Projekt festgelegt und ist nicht als globale Umgebung verfügbar.
    >
    > Falls Sie eine Conda-Umgebung ohne Python-Version erstellen, zeigen Sie mithilfe des Befehls `conda info` die Speicherorte der Conda-Umgebungsordner an, und entfernen Sie dann den Unterordner für die Umgebung manuell aus diesem Speicherort.

1. Wählen Sie **Erstellen**, und beobachten Sie den Fortschritt im Fenster **Ausgabe**. Die Ausgabe enthält nach dem Abschluss der Erstellung einige CLI-Anweisungen:

    ![Erfolgreiche Erstellung einer Conda-Umgebung](media/environments/environments-conda-2-2019.png)

1. In Visual Studio können Sie eine Conda-Umgebung für ein Projekt wie jede andere Umgebung aktivieren, wie unter [Auswählen einer Umgebung für ein Projekt](selecting-a-python-environment-for-a-project.md) beschrieben.

1. Verwenden Sie zum Installieren zusätzlicher Pakete in der Umgebung die Registerkarte [Pakete](python-environments-window-tab-reference.md#packages-tab).
::: moniker-end

> [!Note]
> Um optimale Ergebnisse mit Conda-Umgebungen zu erzielen, verwenden Sie Conda 4.4.8 oder höher (Conda-Versionen unterscheiden sich von Anaconda-Versionen). Geeignete Versionen von Miniconda (Visual Studio 2019) und Anaconda (Visual Studio 2017) können Sie über den Visual Studio-Installer installieren.

Führen Sie `conda info` an einer Anaconda-Eingabeaufforderung (d. h. einer Eingabeaufforderung mit „Anaconda“ im Pfad) aus, um die Conda-Version, den Speicherort der Conda-Umgebungen sowie weitere Informationen anzuzeigen:

```cli
conda info
```

Ihre Conda-Umgebungsordner werden wie folgt angezeigt:

```output
       envs directories : C:\Users\user\.conda\envs
                          c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
```

Da Conda-Umgebungen nicht mit einem Projekt gespeichert werden, verhalten sich ähnlich wie globale Umgebungen. Wenn Sie z.B. ein neues Paket in einer Conda-Umgebung installieren, steht dieses Paket allen Projekten zur Verfügung, die diese Umgebung verwenden.

Für Visual Studio-2017, Version 15.6 und früher, können Sie Conda-Umgebungen verwenden, indem Sie manuell darauf zeigen, wie unter [Manuelles Ermitteln einer vorhandenen Umgebung](#manually-identify-an-existing-environment) beschrieben.

Visual Studio 2017, Version 15.7 und höher, erkannt Conda-Umgebungen automatisch und zeigt sie im Fenster **Python-Umgebungen** an, wie im nächsten Abschnitt beschrieben.

## <a name="manually-identify-an-existing-environment"></a>Manuelles Identifizieren einer vorhandenen Umgebung

Führen Sie die folgenden Schritte aus, um eine Umgebung zu identifizieren, die an einem nicht standardmäßigen Ort installiert ist (z. B. eine Conda-Umgebung in Visual Studio 2017, Version 15.6 und früher):

::: moniker range="vs-2017"

1. Wählen Sie im Fenster **Python-Umgebungen** die Option **+ Benutzerdefiniert**, um die Registerkarte **Konfigurieren** zu öffnen:

    ![Standardansicht für eine neue benutzerdefinierte Umgebung](media/environments/environments-custom-1.png)

1. Geben Sie einen Namen für die Umgebung in das Feld **Beschreibung** ein.

1. Geben Sie den Pfad des Interpreters in das Feld **Präfixpfad** ein, oder navigieren Sie dorthin (mithilfe von **...** ).

1. Wenn Visual Studio einen Python-Interpreter an diesem Speicherort erkennt (z.B. unter dem unten gezeigten Pfad für eine Conda-Umgebung), wird der Befehl **Automatische Erkennung** aktiviert. Durch Auswahl von **Automatische Erkennung** werden die verbleibenden Felder ausgefüllt. Sie können diese Felder auch manuell ausfüllen.

    ![Aktivieren des Befehls zur automatischen Erkennung](media/environments/environments-custom-2.png)

    ![Ausfüllen der Felder für die Umgebung nach der automatischen Erkennung](media/environments/environments-custom-3.png)

1. Sobald die Felder alle gewünschten Werte enthalten, wählen Sie **Übernehmen**, um die Konfiguration zu speichern. Sie können die Umgebung nun wie jede andere in Visual Studio verwenden.

1. Wenn Sie eine manuell identifizierte Umgebung entfernen möchten, wählen Sie auf der Registerkarte **Konfigurieren** den Befehl **Entfernen** aus. Umgebungen mit automatischer Erkennung bieten diese Option nicht. Weitere Informationen finden Sie unter [Registerkarte „Konfigurieren“](python-environments-window-tab-reference.md#configure-tab).

::: moniker-end

::: moniker range=">=vs-2019"

1. Wählen Sie im Fenster **Python-Umgebungen** (oder über die Python-Symbolleiste) die Option **+ Umgebung hinzufügen** aus. Daraufhin wird das Dialogfeld **Umgebung hinzufügen** geöffnet. Wählen Sie in diesem Dialogfeld die Registerkarte **Vorhandene Umgebung** aus:

    ![Registerkarte „Vorhandene Umgebung“ im Dialogfeld „Umgebung hinzufügen“](media/environments/environments-custom-1-2019.png)

1. Wählen Sie das Dropdownmenü **Umgebung** und dann **Benutzerdefiniert** aus:

    ![Option für vorhandene Umgebung im Dialogfeld „Umgebung hinzufügen“](media/environments/environments-custom-2-2019.png)

1. Geben Sie im Dialogfeld in den Feldern unter **Präfixpfad** den Pfad zum Interpreter ein, oder navigieren Sie mithilfe von **...** zu diesem Pfad. Dadurch wird der Großteil der anderen Felder aufgefüllt. Wählen Sie **Hinzufügen** aus, wenn Sie die Werte überprüft und ggf. angepasst haben.

    ![Felder zum Angeben von Details für eine benutzerdefinierte Umgebung im Dialogfeld „Umgebung hinzufügen“](media/environments/environments-custom-3-2019.png)

1. Die Details der Umgebung können jederzeit im Fenster **Python-Umgebungen** überprüft und angepasst werden. Wählen Sie in diesem Fenster die Umgebung und dann die Registerkarte **Konfigurieren** aus. Nehmen Sie Ihre Änderungen vor, und wählen Sie den Befehl **Übernehmen** aus. Sie können die Umgebung mit dem Befehl **Entfernen** auch löschen (für automatisch erkannte Umgebungen nicht verfügbar). Weitere Informationen finden Sie unter [Registerkarte „Konfigurieren“](python-environments-window-tab-reference.md#configure-tab).
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Korrigieren oder Löschen ungültiger Umgebungen

Wenn Visual Studio Registrierungseinträge für eine Umgebung sucht, der Pfad zum Interpreter jedoch ungültig ist, zeigt das Fenster **Python-Umgebungen** den Namen durchgestrichen an:

::: moniker range="vs-2017"
![Das Fenster „Python-Umgebungen“ mit einer ungültigen Umgebung](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Das Fenster „Python-Umgebungen“ mit einer ungültigen Umgebung](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Umgebungen, die Sie behalten möchten, lassen sich korrigieren, indem Sie zunächst den **Reparaturvorgang** des Installers starten. Die Installer für die Standardversion von Python 3.x beispielsweise enthält diese Option.

Wenn Sie eine Umgebung korrigieren möchten, die über keine Reparaturoption verfügt, oder eine ungültige Umgebung entfernen, führen Sie die folgenden Schritte aus, um die Registrierung direkt zu ändern. Visual Studio aktualisiert das Fenster **Python-Umgebungen** automatisch, wenn Sie Änderungen an der Registrierung vornehmen.

1. Führen Sie *regedit.exe* aus.
1. Navigieren Sie zu **HKEY_LOCAL_MACHINE\SOFTWARE\Python** oder **HKEY_CURRENT_USER\SOFTWARE\Python**. Für IronPython müssen Sie stattdessen nach  **IronPython** suchen.
1. Erweitern Sie den Knoten, der der Verteilung entspricht, z. B. **Python Core** für CPython oder **ContinuumAnalytics** für Anaconda. Erweitern Sie für IronPython den Versionsnummerknoten.
1. Überprüfen Sie die Werte im Knoten **InstallPath**:

    ![Registrierungseinträge für eine Standardinstallation von CPython](media/environments/environments-registry-entries.png)

    - Wenn die Umgebung weiterhin auf dem Computer vorhanden ist, ändern Sie den Wert von **ExecutablePath** in den richtigen Speicherort. Korrigieren Sie wenn nötig auch die Werte **(Standard)** und **WindowedExecutablePath**.
    - Wenn die Umgebung nicht mehr auf Ihrem Computer vorhanden ist und Sie sie aus dem Fenster **Python-Umgebungen** entfernen möchten, löschen Sie den übergeordneten Knoten von **InstallPath**, z.B. **3.6** in der Abbildung oben.
    - Ungültige Einstellungen in **HKEY_CURRENT_USER\SOFTWARE\Python** überschreiben die Einstellungen in **HKEY_LOCAL_MACHINE\SOFTWARE\Python**

## <a name="see-also"></a>Siehe auch

- [Installieren von Python-Interpretern](installing-python-interpreters.md)
- [Auswählen eines Interpreters für ein Projekt](selecting-a-python-environment-for-a-project.md)
- [Verwenden von „requirements.txt“ für Abhängigkeiten](managing-required-packages-with-requirements-txt.md)
- [Suchpfade](search-paths.md)
- [Das Fenster „Python-Umgebungen“](python-environments-window-tab-reference.md)