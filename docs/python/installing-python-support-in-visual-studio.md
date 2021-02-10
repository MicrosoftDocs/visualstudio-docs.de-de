---
title: Installieren von Python-Unterstützung
description: Informationen zum Installieren von Python Tools für Visual Studio (PTVS) in Visual Studio 2017, 2015, 2013, 2012 und 2010, einschließlich Optionen und Installationsspeicherorten.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e0c1cf29c7579978d5992de46b14c01fee0799c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881645"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Installieren von Python-Unterstützung für Visual Studio unter Windows

Um die Python-Unterstützung für Visual Studio (auch als Python Tools für Visual Studio bzw. PTVS bezeichnet) zu installieren, befolgen Sie die Anweisungen in dem Abschnitt, der Ihrer Version von Visual Studio entspricht:

- [Visual Studio 2017 und Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 und früher](#visual-studio-2013-and-earlier)

Wenn die Python-Unterstützung nach Ausführung der Installationsschritte schnell getestet werden soll, öffnen Sie das Fenster **Interaktives Python**, indem Sie die Tasten **ALT**+**I** drücken und `2+2` eingeben. Wenn Sie die Ausgabe von `4` nicht sehen, überprüfen Sie Ihre Schritte.

> [!Tip]
> Die Python-Arbeitsauslastung enthält die hilfreiche Cookiecutter-Erweiterung, die eine grafische Benutzeroberfläche bietet, auf der Sie Vorlagen ermitteln, Vorlageoptionen eingeben und Projekte und Dateien erstellen können. Weitere Einzelheiten finden Sie unter [Verwenden von Cookiecutter](using-python-cookiecutter-templates.md).

> [!Note]
> Python wird zurzeit nicht von Visual Studio für Mac unterstützt, steht jedoch auf Mac und Linux über Visual Studio-Code zur Verfügung. Weitere Informationen finden Sie unter [Questions and answers](overview-of-python-tools-for-visual-studio.md#questions-and-answers) (Fragen und Antworten).

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 und Visual Studio 2017

1. Laden Sie den aktuellen Visual Studio-Installer herunter, und führen Sie ihn aus. Wenn Sie Visual Studio bereits installiert haben, führen Sie den Visual Studio-Installer aus, wählen die Option **Ändern** aus (siehe [Ändern von Visual Studio](../install/modify-visual-studio.md)), und fahren Sie mit Schritt 2 fort.

    > [!div class="nextstepaction"]
    > [Installieren von Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Die Community Edition eignet sich für einzelne Entwickler, Schulungsumgebungen, akademische Forschung und Open Source-Entwicklung. Installieren Sie für andere Verwendungszwecke [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) oder [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted).

1. Der Installer bietet Ihnen eine Liste von Workloads, bei denen es sich um Gruppen von verwandten Optionen für bestimmte Entwicklungsbereiche handelt. Wählen Sie für Python die Workload **Python-Entwicklung** aus.

    ![Arbeitsauslastung zur Python-Entwicklung im Visual Studio-Installationsprogramm](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    Optional: Wenn Sie mit Data Science arbeiten, verwenden Sie ggf. die Workload **Data Science und analytische Anwendungen**. Diese Workload enthält Support für die Sprachen Python, R und F#. Weitere Informationen finden Sie unter [Data science and analytical applications workload (Workload für Data Science und analytische Anwendungen)](data-science-and-analytical-applications-workload.md).

    > [!Note]
    > Die Python- und Data Science-Workloads sind nur für Visual Studio 2017, Version 15.2 und höher verfügbar.

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Optional: Wenn Sie mit Data Science arbeiten, verwenden Sie ggf. die Workload **Data Science und analytische Anwendungen**. Diese Workload enthält Support für Python und F#-Sprachen. Weitere Informationen finden Sie unter [Data science and analytical applications workload (Workload für Data Science und analytische Anwendungen)](data-science-and-analytical-applications-workload.md).
    ::: moniker-end

1. Wählen Sie bei Bedarf zusätzliche Optionen auf der rechten Seite des Installers aus. Überspringen Sie diesen Schritt, um die Standardoptionen zu akzeptieren.

    ::: moniker range="vs-2017"
    ![Optionen zur Python-Entwicklung im Visual Studio-Installationsprogramm](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Optionen zur Python-Entwicklung im Visual Studio 2019-Installer](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | Option | Beschreibung |
    | --- | --- |
    | Python-Verteilungen | Wählen Sie eine beliebige Kombination der verfügbaren Optionen wie 32-Bit- und 64-Bit-Varianten der Python 2-, Python 3-, Miniconda-, Anaconda2- und Anaconda3-Verteilungen aus, mit denen Sie arbeiten möchten. Jede enthält den Interpreter, die Runtime und die Bibliotheken der Verteilung. Bei Anaconda handelt es sich um eine offene Data Science-Plattform, die eine große Auswahl an vorinstallierten Paketen enthält. (Sie können jederzeit zum Visual Studio-Installer zurückkehren, um Verteilungen hinzuzufügen oder zu entfernen.)  **Hinweis:** Wenn Sie eine Distribution außerhalb des Visual Studio-Installers installiert haben, muss die entsprechende Option hier nicht aktiviert werden. Visual Studio erkennt vorhandene Python-Installationen automatisch. Weitere Informationen finden Sie im [Fenster „Python-Umgebungen“](managing-python-environments-in-visual-studio.md#the-python-environments-window). Wenn eine neuere Version von Python als im Installationsprogramm angezeigt verfügbar ist, können Sie diese Version separat installieren, und Visual Studio erkennt sie. |
    | **Unterstützung von Cookiecutter-Vorlagen** | Installiert die grafische Benutzeroberfläche von Cookiecutter, um Vorlagen zu ermitteln, Vorlagenoptionen einzugeben und Projekte und Dateien zu erstellen. Weitere Informationen finden Sie unter [Verwenden der Cookiecutter-Erweiterung](using-python-cookiecutter-templates.md). |
    | **Webunterstützung für Python** | Installiert Tools für die Webentwicklung einschließlich der Bearbeitungsunterstützung für HTML, CSS und JavaScript sowie Vorlagen für Projekte, die Bottle-, Flask- und Django-Frameworks verwenden. Weitere Informationen finden Sie unter [Python-Webprojektvorlagen](python-web-application-project-templates.md). |
    | **IoT-Unterstützung für Python** | Unterstützt die Windows IoT Core-Entwicklung mithilfe von Python. |
    | **Native Python-Entwicklungstools** | Installiert den C++-Compiler und andere erforderliche Komponenten, um native Erweiterungen für Python zu entwickeln. Weitere Informationen finden Sie unter [Erstellen einer C++-Erweiterung für Python](working-with-c-cpp-python-in-visual-studio.md). Installieren Sie außerdem die Workload **Desktopentwicklung mit C++** , um über volle Unterstützung für C++ zu verfügen. |
    | **Kerntools für Azure Cloud Services** | Bietet zusätzliche Unterstützung für Azure Cloud Services-Entwickler in Python. Weitere Informationen finden Sie unter [Projekte für Azure Cloud Services](python-azure-cloud-service-project-template.md). |
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | Option | Beschreibung |
    | --- | --- |
    | Python-Verteilungen | Wählen Sie eine beliebige Kombination der verfügbaren Optionen wie 32-Bit- und 64-Bit-Varianten der Python 2-, Python 3-, Miniconda-, Anaconda2- und Anaconda3-Verteilungen aus, mit denen Sie arbeiten möchten. Jede enthält den Interpreter, die Runtime und die Bibliotheken der Verteilung. Bei Anaconda handelt es sich um eine offene Data Science-Plattform, die eine große Auswahl an vorinstallierten Paketen enthält. (Sie können jederzeit zum Visual Studio-Installer zurückkehren, um Verteilungen hinzuzufügen oder zu entfernen.)  **Hinweis:** Wenn Sie eine Distribution außerhalb des Visual Studio-Installers installiert haben, muss die entsprechende Option hier nicht aktiviert werden. Visual Studio erkennt vorhandene Python-Installationen automatisch. Weitere Informationen finden Sie im [Fenster „Python-Umgebungen“](managing-python-environments-in-visual-studio.md#the-python-environments-window). Wenn eine neuere Version von Python als im Installationsprogramm angezeigt verfügbar ist, können Sie diese Version separat installieren, und Visual Studio erkennt sie. |
    | **Unterstützung von Cookiecutter-Vorlagen** | Installiert die grafische Benutzeroberfläche von Cookiecutter, um Vorlagen zu ermitteln, Vorlagenoptionen einzugeben und Projekte und Dateien zu erstellen. Weitere Informationen finden Sie unter [Verwenden der Cookiecutter-Erweiterung](using-python-cookiecutter-templates.md). |
    | **Webunterstützung für Python** | Installiert Tools für die Webentwicklung einschließlich der Bearbeitungsunterstützung für HTML, CSS und JavaScript sowie Vorlagen für Projekte, die Bottle-, Flask- und Django-Frameworks verwenden. Weitere Informationen finden Sie unter [Python-Webprojektvorlagen](python-web-application-project-templates.md). |
    | **Native Python-Entwicklungstools** | Installiert den C++-Compiler und andere erforderliche Komponenten, um native Erweiterungen für Python zu entwickeln. Weitere Informationen finden Sie unter [Erstellen einer C++-Erweiterung für Python](working-with-c-cpp-python-in-visual-studio.md). Installieren Sie außerdem die Workload **Desktopentwicklung mit C++** , um über volle Unterstützung für C++ zu verfügen. |
    | **Kerntools für Azure Cloud Services** | Bietet zusätzliche Unterstützung für Azure Cloud Services-Entwickler in Python. Weitere Informationen finden Sie unter [Projekte für Azure Cloud Services](python-azure-cloud-service-project-template.md). |
    ::: moniker-end

1. Nach der Installation bietet der Installer Optionen für das Ändern, Starten, Reparieren oder Deinstallieren von Visual Studio. Die Schaltfläche **Ändern** ändert sich zu **Aktualisieren**, wenn Updates für die installierten Komponenten von Visual Studio verfügbar sind. (Die Option **Ändern** ist anschließend im Dropdownmenü verfügbar.) Sie können Visual Studio und den Installer ebenfalls über das Windows-Menü **Start** starten, indem Sie nach „Visual Studio“ suchen.

    ![Starten, Ändern oder Deinstallieren von Visual Studio über den Installer](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>Problembehandlung

Wenn Probleme bei der Installation oder Ausführung von Python in Visual Studio auftreten, versuchen Sie Folgendes:

- Überprüfen Sie, ob der gleiche Fehler über die Python-CLI auftritt, d.h. bei Ausführen von *python.exe* über eine Eingabeaufforderung.
- Verwenden Sie die [**Reparaturoption**](../install/repair-visual-studio.md) im Visual Studio-Installer.
- Reparieren oder installieren Sie Python neu über **Einstellungen** > **Apps & Features** (unter Windows).

**Beispielfehler:** Failed to start interactive process: System.ComponentModel.Win32Exception (0x80004005): Unknown error (0xc0000135) at Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext(). (Fehler beim Starten des interaktiven Prozesses: System.ComponentModel.Win32Exception (0x80004005): Unbekannter Fehler (0xc0000135) bei Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext().)

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Führen Sie das Visual Studio-Installationsprogramm über **Systemsteuerung > Programme und Funktionen** aus, wählen Sie **Microsoft Visual Studio 2015** aus, und dann **Ändern**.

1. Wählen Sie im Installationsprogramm **Ändern**.

1. Wählen Sie **Programmiersprachen** > **Python-Tools für Visual Studio** und dann **Weiter** aus:

    ![PTVS-Option im Visual Studio 2015-Installationsprogramm](media/installation-vs2015.png)

1. Nach Abschluss der Installation von Visual Studio [installieren Sie einen Python-Interpreter Ihrer Wahl](installing-python-interpreters.md). Visual Studio 2015 unterstützt nur Python 3.5 und früher. Spätere Versionen erzeugen Fehlermeldungen wie **Nicht unterstützte Python-Version 3.6**. Wenn Sie bereits einen Interpreter installiert haben und Visual Studio diesen nicht automatisch erkennt, finden Sie weitere Informationen unter [Manuelles Identifizieren einer vorhandenen Umgebung](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 und früher

1. Installieren Sie die entsprechende Version der Python-Tools für Visual Studio für Ihre Version von Visual Studio:

    - Visual Studio 2013: [PTVS 2.2.2 für Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2.2) Im Dialogfeld **Datei** > **Neues Projekt** in Visual Studio 2013 finden Sie eine Verknüpfung für diesen Prozess.
    - Visual Studio 2010 und 2012: [PTVS 2.1.1 für Visual Studio 2010 und 2012](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Installieren Sie einen Python-Interpreter Ihrer Wahl](installing-python-interpreters.md). Wenn Sie bereits einen Interpreter installiert haben und Visual Studio diesen nicht automatisch erkennt, finden Sie weitere Informationen unter [Manuelles Identifizieren einer vorhandenen Umgebung](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="install-locations"></a>Installationsspeicherorte

Standardmäßig wird die Python-Unterstützung für alle Benutzer auf einem Computer installiert.

Bei Visual Studio 2019 und Visual Studio 2017wird die Python-Workload unter *%ProgramFiles(x86)%\Microsoft Visual Studio\\<VS-Version>\\<VS_edition>Common7\IDE\Extensions\Microsoft\Python* installiert. &lt;VS_version&gt; steht für 2019 oder 2017 und &lt;VS_edition&gt; für Community, Professional oder Enterprise.

Für Visual Studio 2015 und früher gelten folgende Installationspfade:

- 32-Bit:
  - Pfad: *%Programme (x86)%\Microsoft Visual Studio \<VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\\<PTVS_ver>*
  - Registrierungsspeicherort des Pfads: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\<VS_ver>\InstallDir**
- 64-Bit:
  - Pfad: *%Programme%\Microsoft Visual Studio \<VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\\<PTVS_ver>*
  - Registrierungsspeicherort des Pfads: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<VS_ver>\InstallDir**

Dabei gilt:

- &lt;VS_ver&gt; ist:
  - 14.0 für Visual Studio 2015
  - 12.0 für Visual Studio 2013
  - 11.0 für Visual Studio 2012
  - 10.0 für Visual Studio 2010
- &lt;PTVS_ver&gt; ist eine Versionsnummer, z. B. 2.2.2, 2.1.1, 2.0, 1.5, 1.1 oder 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Benutzerspezifische Installationen (1.5 und früher)

Bei Python Tools für Visual Studio 1.5 und früheren Versionen war die Installation nur für den aktuellen Benutzer zulässig. In diesem Fall lautet der Installationspfad *%LocalAppData%\Microsoft\VisualStudio\\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\\<PTVS_ver>* , wobei für &lt;VS_ver&gt; und &lt;PTVS_ver&gt; die obige Beschreibung gilt.
