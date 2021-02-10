---
title: Verwalten von Python-Anwendungsprojekten
description: Projekte in Visual Studio verwalten Abhängigkeiten zwischen Dateien sowie die Komplexität von Beziehungen in einer Anwendung.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 09203557fd9adcd6580dfafa981d6ed4f80eca16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936456"
---
# <a name="python-projects-in-visual-studio"></a>Python-Projekte in Visual Studio

Python-Anwendungen werden in der Regel nur mit Ordnern und Dateien definiert, aber diese Struktur kann bei größeren Anwendungen, die vielleicht automatisch generierte Dateien, JavaScript für Webanwendungen usw. einbeziehen, komplex werden. Ein Visual Studio-Projekt kann Sie beim Verwalten dieser komplexen Struktur unterstützen. Das Python-Projekt (eine *PYPROJ*-Datei) identifiziert alle Quell- und Inhaltsdateien des Projekts, enthält Buildinformationen für jede Datei, verwaltet die Informationen zur Integration in Quellcodeverwaltungssysteme und unterstützt Sie beim Organisieren Ihrer Anwendung in logische Komponenten.

![Python-Projekt im Projektmappen-Explorer](media/projects-solution-explorer.png)

Darüber hinaus werden Projekte immer in einer Visual Studio-*Projektmappe* verwaltet, die eine beliebige Anzahl von Projekten enthalten kann, die möglicherweise aufeinander verweisen. Ein Python-Projekt kann z.B. auf ein C++-Projekt verweisen, das ein Erweiterungsmodul implementiert. Bei dieser Beziehung erstellt Visual Studio automatisch das C++-Projekt (falls erforderlich), wenn Sie mit dem Debuggen des Python-Projekts beginnen. (Eine allgemeine Erörterung finden Sie unter [Projektmappen und Projekte in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).)

Visual Studio bietet eine Vielzahl von Python-Projektvorlagen, mit der Sie schnell eine Reihe von Anwendungsstrukturen einrichten können, einschließlich einer Vorlage zum Erstellen eines Projekts aus einer vorhandenen Ordnerstruktur und einer Vorlage zum Erstellen eines leeren Projekts. Einen Index finden Sie unter [Projektvorlagen](#project-templates).

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019 unterstützt das Öffnen eines Ordners, der Python-Code enthält, und das Ausführen dieses Codes, ohne dass Projekt- und Projektmappendateien in Visual Studio erstellt werden müssen. Weitere Informationen finden Sie unter [Schnellstart: Öffnen und Ausführen von Python-Code in einem Ordner](quickstart-05-python-visual-studio-open-folder.md). Die Verwendung einer Projektdatei bietet jedoch gewisse Vorteile, wie in diesem Abschnitt erläutert.
::: moniker-end

> [!Tip]
> Sie können Python-Code ohne ein Projekt problemlos in allen Visual Studio-Versionen verwenden. Sie können zum Beispiel eine eigenständige Python-Datei öffnen und die automatische Vervollständigung, IntelliSense und das Debuggen verwenden. Klicken Sie hierzu mit der rechten Maustaste in den Editor und dann auf **Mit Debugging starten** klicken. Da diese Art von Code immer die globale Standardumgebung verwendet, stellen Sie jedoch möglicherweise falsche Vervollständigungen oder Fehler fest, wenn der Code für eine andere Umgebung vorgesehen ist. Darüber hinaus analysiert Visual Studio alle Dateien und Pakete in dem Ordner, in dem die einzelne Datei geöffnet wird, was sehr viel CPU-Zeit in Anspruch nimmt.
>
> Es ist einfach, ein Visual Studio-Projekt aus vorhandenem Code zu erstellen, wie unter [Erstellen eines Projekts aus vorhandenen Dateien](#create-project-from-existing-files) beschrieben.

![Filmkamerasymbol für Video](../install/media/video-icon.png "Video ansehen") [Deep Dive: Use source control with Python projects (Vertiefung: Verwenden der Quellcodeverwaltung mit Python-Projekten)](https://youtu.be/Aq8eqApnugM) (youtube.com, 8 Minuten und 55 Sekunden).

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Hinzufügen von Dateien, Zuweisen einer Startdatei und Festlegen von Umgebungen

Bei der Entwicklung Ihrer Anwendung müssen Sie dem Projekt in der Regel neue Dateien verschiedenen Typs hinzufügen. Fügen Sie solche Dateien hinzu, indem Sie mit der rechten Maustaste auf das Projekt klicken, und klicken Sie dann auf **Hinzufügen** > **Vorhandenes Element**, um nach der hinzuzufügenden Datei zu suchen, oder klicken Sie auf **Hinzufügen** > **Neues Element**, um ein Dialogfeld mit mehreren Elementvorlagen zu öffnen. Wie in der Referenz zu [Elementvorlagen](python-item-templates.md) beschrieben, enthalten Vorlagen leere Python-Dateien, eine Python-Klasse, einen Komponententest und verschiedene Dateien zu Webanwendungen. Sie können diese Optionen mit einem Testprojekt ausprobieren, um zu erfahren, was in Ihrer Visual Studio-Version verfügbar ist.

Jedem Python-Projekt ist eine im **Projektmappen-Explorer** fett angezeigte Startdatei zugewiesen. Die Startdatei ist die Datei, die ausgeführt wird, wenn Sie das Debuggen starten (**F5** oder **Debuggen** > **Debuggen starten**) oder das Projekt im **interaktiven** Fenster ausführen (**UMSCHALTTASTE**+**ALT**+**F5** oder **Debuggen** > **Execute Project in Python Interactive** (Projekt in interaktivem Python ausführen)). Klicken Sie zum Ändern mit der rechten Maustaste auf die neue Datei, und wählen Sie **Als Startelement festlegen** (bzw. in älteren Visual Studio-Versionen **Als Startdatei festlegen**) aus.

> [!Tip]
> Wenn Sie die ausgewählte Startdatei aus einem Projekt entfernen und keine neue auswählen, weiß Visual Studio nicht, mit welcher Python-Datei gestartet werden soll, wenn Sie versuchen, das Projekt auszuführen. In diesem Fall zeigt Visual Studio 2017 Version 15.6 und höher einen Fehler an; frühere Versionen öffnen entweder ein Ausgabefenster, in dem der Python-Interpreter ausgeführt wird, oder das Ausgabefenster wird nur kurz angezeigt und dann beinahe sofort wieder geschlossen. Wenn eine dieser Verhaltensweisen auftritt, überprüfen Sie, ob Sie eine zugewiesene Startdatei haben.
>
> Wenn Sie das Ausgabefenster aus beliebigem Grund geöffnet lassen möchten, klicken Sie mit der rechten Maustaste auf Ihr Projekt, wählen Sie **Eigenschaften** und dann die Registerkarte **Debuggen** aus, und fügen Sie anschließend `-i` dem Feld **Interpreterargumente** hinzu. Durch dieses Argument wird der Interpreter nach Abschluss des Programms in den interaktiven Modus versetzt. Das Fenster bleibt dabei geöffnet, bis Sie **STRG**+**Z** > **EINGABETASTE** zum Beenden drücken.

::: moniker range="vs-2017"
Ein neues Projekt ist immer der standardmäßigen globalen Python-Umgebung zugeordnet. Um das Projekt einer anderen Umgebung zuzuordnen (einschließlich virtueller Umgebungen), klicken Sie mit der rechten Maustaste auf den Knoten **Python-Umgebungen** im Projekt, klicken Sie auf **Python-Umgebungen hinzufügen/entfernen**, und wählen Sie dann die gewünschten Umgebungen aus.
::: moniker-end
::: moniker range=">=vs-2019"
Ein neues Projekt ist immer der standardmäßigen globalen Python-Umgebung zugeordnet. Um das Projekt einer anderen Umgebung zuzuordnen (einschließlich virtueller Umgebungen), klicken Sie mit der rechten Maustaste auf den Knoten **Python-Umgebungen** im Projekt, und wählen Sie **Umgebungen hinzufügen...** und dann die gewünschten Umgebungen aus. Sie können auch das Dropdown-Steuerelement für Umgebungen auf der Symbolleiste verwenden, um eine Umgebung auszuwählen oder dem Projekt eine weitere Umgebung hinzuzufügen.

![Befehl „Umgebung hinzufügen“ auf der Python-Symbolleiste](media/environments/environments-toolbar-2019.png)
::: moniker-end

Um die aktive Umgebung zu ändern, klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die gewünschte Umgebung, und wählen Sie **Umgebung aktivieren** aus, wie unten dargestellt. Weitere Informationen finden Sie unter [Zuweisen einer Umgebung für ein Projekt](selecting-a-python-environment-for-a-project.md).

![Aktivieren einer Umgebung für ein Python-Projekt](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Projektvorlagen

Visual Studio bietet Ihnen eine Reihe von Methoden zum Einrichten eines Python-Projekts, entweder von Grund auf oder aus vorhandenem Code. Wählen Sie den Menübefehl **Datei** > **Neu** > **Projekt** aus, oder klicken Sie mit der rechten Maustaste auf die Projektmappe im **Projektmappen-Explorer**, und wählen Sie **Hinzufügen** > **Neues Projekt** aus. In beiden Fällen öffnen Sie das unten gezeigte Dialogfeld **Neues Projekt**. Suchen Sie entweder nach „Python“, oder klicken Sie auf den Knoten **Installiert** > **Python**, um Python-spezifische Vorlagen anzuzeigen:

![Dialogfeld „Neues Projekt“ mit Python-Vorlagen](media/projects-new-project-dialog.png)

Die folgende Tabelle fasst die in Visual Studio 2017 und höher verfügbaren Vorlagen zusammen (nicht alle Vorlagen stehen in allen früheren Versionen zur Verfügung):

| Vorlage | BESCHREIBUNG |
| --- | --- |
| [**Aus vorhandenem Python-Code**](#create-project-from-existing-files) | Erstellt ein Visual Studio-Projekt aus vorhandenem Python-Code in einer Ordnerstruktur.  |
| **Python-Anwendung** | Eine grundlegende Projektstruktur für eine neue Python-Anwendung mit einer einzelnen, leeren Quelldatei. Standardmäßig wird das Projekt im Konsoleninterpreter der globalen Standardumgebung ausgeführt, die Sie durch [Zuweisen einer anderen Umgebung](selecting-a-python-environment-for-a-project.md) ändern können. |
| [**Azure Cloud Services**](python-azure-cloud-service-project-template.md) | Ein in Python geschriebenes Projekt für einen Azure-Clouddienst |
| [**Webprojekte**](python-web-application-project-templates.md) | Auf verschiedenen Frameworks einschließlich Bottle, Django und Flask basierende Projekte für Web-Apps. |
| **IronPython-Anwendung** | Ähnlich wie die Python-Anwendungsvorlage, verwendet aber IronPython durch standardmäßige Aktivierung .von NET-Interop und Debuggen im gemischten Modus mit .NET-Sprachen. |
| **IronPython-WPF-Anwendung** | Eine Projektstruktur mit IronPython mit Windows Presentation Foundation-XAML-Dateien für die Benutzeroberfläche der Anwendung. Visual Studio bietet einen XAML-Benutzeroberflächen-Designer, CodeBehind kann in Python geschrieben werden, und die Anwendung wird ohne Anzeige einer Konsole ausgeführt. |
| **IronPython-Silverlight-Webseite** | Ein IronPython-Projekt, das in einem Browser mit Silverlight ausgeführt wird. Der Python-Code für die Anwendung ist auf der Webseite als Skript enthalten. Ein Codebaustein-Skript-Tag übernimmt JavaScript-Code, der die Ausführung von IronPython in Silverlight initialisiert, von wo aus der Python-Code mit dem DOM kommunizieren kann. |
| **IronPython-Windows Forms-Anwendung** | Eine Projektstruktur mit IronPython, bei der die Benutzeroberfläche mithilfe von Windows Forms-Code erstellt wird. Die Anwendung wird ohne Anzeige einer Konsole ausgeführt. |
| **Hintergrundanwendung (IoT)** | Unterstützt die Bereitstellung von Python-Projekten zur Ausführung als Hintergrunddienste auf Geräten. Unter [Windows 10 IoT Core](https://dev.windows.com/en-us/iot) erhalten Sie weitere Informationen. |
| **Python-Erweiterungsmodul** | Diese Vorlage erscheint unter Visual C++, wenn Sie die **nativen Python-Entwicklungstools** mit der Python-Arbeitsauslastung in Visual Studio 2017 oder höher installiert haben (weitere Informationen finden Sie unter [Installation](installing-python-support-in-visual-studio.md)). Sie stellt die grundlegende Struktur für eine C++-Erweiterungs-DLL bereit, ganz ähnlich der, die unter [Erstellen einer C++-Erweiterung für Python](working-with-c-cpp-python-in-visual-studio.md) beschrieben wird. |

> [!Note]
> Da Python eine interpretierte Programmiersprache ist, produzieren Python-Projekte in Visual Studio keine eigenständigen ausführbaren Dateien, wie andere Projekte in kompilierten Sprachen (z.B. C#). Weitere Informationen finden Sie unter [Questions and answers](overview-of-python-tools-for-visual-studio.md#questions-and-answers) (Fragen und Antworten).

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Erstellen eines Projekts aus vorhandenen Dateien

> [!Important]
> Der hier beschriebene Prozess verschiebt oder kopiert die ursprünglichen Quelldateien nicht. Wenn Sie mit einer Kopie arbeiten möchten, erstellen Sie zunächst eine Kopie des Ordners.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Verknüpfte Dateien

Verknüpfte Dateien sind Dateien, die in ein Projekt eingebunden sind, sich aber in der Regel außerhalb der Projektordner der Anwendung befinden. Sie werden im **Projektmappen-Explorer** wie normale Dateien überlagert mit einem Verknüpfungssymbol angezeigt: ![Dateiverknüpfungssymbol](media/projects-linked-file-icon.png)

Verknüpfte Dateien werden in der Datei *.pyproj* mit dem `<Compile Include="...">`-Element angegeben. Verknüpfte Dateien sind implizit, wenn Sie einen relativen Pfad außerhalb der Verzeichnisstruktur nutzen, oder sie sind explizit, wenn sie Pfade im **Projektmappen-Explorer** verwenden:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Verknüpfte Dateien werden unter folgenden Bedingungen ignoriert:

- Die verknüpfte Datei enthält Linkmetadaten, und der im Include-Attribut angegebene Pfad befindet sich im Projektverzeichnis.
- Die verknüpfte Datei dupliziert eine Datei, die in der Projekthierarchie vorhanden ist
- Die verknüpfte Datei enthält Linkmetadaten, und der Linkpfad ist ein relativer Pfad außerhalb der Projekthierarchie.
- Der Linkpfad ist ein Stammpfad.

### <a name="work-with-linked-files"></a>Arbeiten mit verknüpften Dateien

Klicken Sie zum Hinzufügen eines vorhandenen Elements als Link mit der rechten Maustaste auf den Ordner im Projekt, dem Sie die Datei hinzufügen möchten, und wählen Sie **Hinzufügen** > **Vorhandenes Element** aus. Wählen Sie im daraufhin angezeigten Dialogfeld eine Datei aus, und wählen Sie **Als Link hinzufügen** aus der Dropdownliste der Schaltfläche **Hinzufügen**. Sofern keine in Konflikt stehenden Dateien vorhanden sind, wird mit diesem Befehl ein Link im ausgewählten Ordner erstellt. Allerdings wird der Link nicht hinzugefügt, wenn bereits eine Datei mit dem gleichen Namen vorhanden ist, oder ein Link zu dieser Datei bereits im Projekt vorhanden ist.

Wenn Sie versuchen, eine Verknüpfung zu einer Datei zu erstellen, die bereits im Projektordner vorhanden ist, wird sie als normale Datei und nicht als Link hinzugefügt. Um eine Datei in einen Link zu konvertieren, wählen Sie **Datei** > **Speichern unter** aus, um die Datei an einem Speicherort außerhalb der Projekthierarchie zu speichern; Visual Studio konvertiert sie automatisch in einen Link. Auf ähnliche Weise kann ein Link mit **Datei** > **Speichern unter** zurückkonvertiert werden, um die Datei an beliebiger Stelle in der Projekthierarchie zu speichern.

Wenn Sie eine verknüpfte Datei im **Projektmappen-Explorer** verschieben, wird der Link verschoben, aber die eigentliche Datei ist nicht betroffen. Ebenso wird beim Löschen eines Links nur der Link entfernt, ohne Auswirkung auf die Datei.

Verknüpfte Dateien können nicht umbenannt werden.

## <a name="references"></a>Referenzen

Visual Studio-Projekte unterstützen das Hinzufügen von Verweisen auf Projekte und Erweiterungen, die im **Projektmappen-Explorer** unter dem Knoten **Verweise** angezeigt werden:

![Erweiterungsverweise in Python-Projekten](media/projects-extension-references.png)

Erweiterungsverweise geben in der Regel Abhängigkeiten zwischen Projekten an und dienen zum Bereitstellen von IntelliSense beim Entwurf oder der Verknüpfung bei der Kompilierung. Python-Projekte verwenden Verweise ähnlich, aber aufgrund der Dynamik von Python werden sie in erster Linie zur Entwurfszeit verwendet, um verbessertes IntelliSense bereitzustellen. Sie können auch für die Bereitstellung in Microsoft Azure verwendet werden, um zusätzliche Abhängigkeiten zu installieren.

### <a name="extension-modules"></a>Erweiterungsmodule

Ein Verweis auf eine Datei *.pyd* aktiviert IntelliSense für das generierte Modul. Visual Studio lädt die Datei *.pyd* in den Python-Interpreter und prüft Typen und Funktionen. Es wird auch versucht, die Dokumentzeichenfolgen für Funktionen zu analysieren, um Signaturhilfe zu bieten.

Wenn zu einem beliebigen Zeitpunkt das Erweiterungsmodul auf dem Datenträger aktualisiert wird, analysiert Visual Studio das Modul im Hintergrund neu. Diese Aktion hat keine Auswirkung auf das Laufzeitverhalten, aber einige Vervollständigungen stehen nicht zur Verfügung, bis die Analyse abgeschlossen ist.

Sie müssen dem Ordner, der das Modul enthält, möglicherweise auch einen [Suchpfad](search-paths.md) hinzufügen.

### <a name="net-projects"></a>.NET-Projekte

Bei der Arbeit mit IronPython können Sie .NET-Assemblys Verweise hinzufügen, um IntelliSense zu aktivieren. Klicken Sie für .NET-Projekte in der Projektmappe mit der rechten Maustaste auf den **Verweise**-Knoten in Ihrem Python-Projekt, wählen Sie **Verweis hinzufügen**, wählen Sie die **Projekte**-Registerkarte, und suchen Sie das gewünschte Projekt. Wählen Sie für DLLs, die Sie separat heruntergeladen haben, stattdessen die Registerkarte **Durchsuchen**, und navigieren Sie zu der gewünschten DLL.

Da Verweise in IronPython nicht verfügbar sind, bis ein Aufruf von `clr.AddReference('<AssemblyName>')` erfolgt, müssen Sie der Assembly auch einen entsprechenden `clr.AddReference`-Aufruf hinzufügen, in der Regel direkt zu Beginn Ihres Codes. Beispielsweise enthält der von der Projektvorlage für die **IronPython-Windows Forms-Anwendung** in Visual Studio erstellte Code zwei Aufrufe am Anfang der Datei:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>WebPI-Projekte

Sie können WebPI-Produkteinträgen Verweise für die Bereitstellung in Microsoft Azure Cloud Services hinzufügen, wo Sie zusätzliche Komponenten über den WebPI-Feed installieren können. Standardmäßig ist der angezeigte Feed Python-spezifisch und enthält Django, CPython und andere Kernkomponenten. Sie können auch Ihre eigenen Feeds auswählen, wie unten dargestellt. Beim Veröffentlichen in Microsoft Azure installiert eine Setupaufgabe alle Produkte, auf die verwiesen wird.

> [!IMPORTANT]
> Web PI-Projekte sind in Visual Studio 2017 oder Visual Studio 2019 nicht verfügbar.

![WebPI-Verweise](media/projects-webPI-components.png)
