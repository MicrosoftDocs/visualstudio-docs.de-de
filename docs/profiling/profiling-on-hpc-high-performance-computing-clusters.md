---
title: Profilerstellung bei HPC-Clustern | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie ein Profil auf Berechnungsknoten von Microsoft Windows HPC-Clustern mithilfe der Samplingmethode für die Visual Studio-Profilerstellungstools erstellen können.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.hpc.wizard.exeoptions
- vs.performance.hpc.wizard.summary
- vs.performance.hpc.wizard.startoptions
- vs.performance.hpc.wizard.intro
- vs.performance.hpc.property.basic
- vs.performance.hpc.wizard.application
- vs.performance.hpc.wizard.clusteroptions
- vs.performance.hpc.property.advanced
helpviewer_keywords:
- profililng tools,HPC
- HPC profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 06a160adda25debe21d8262d9064c23849011dc9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720526"
---
# <a name="profile-on-hpc-high-performance-computing-clusters"></a>Profilerstellung bei HPC-Clustern (High Performance Computing)

Sie können ein Profil auf Berechnungsknoten von Microsoft Windows HPC-Clustern mithilfe der Samplingmethode für die Visual Studio-Profilerstellungstools erstellen. Weitere Informationen zu HPC finden Sie unter [Windows HPC](https://azure.microsoft.com/solutions/big-compute/) auf der Microsoft-Website.

## <a name="prerequisites"></a>Voraussetzungen

Um ein Profil auf einem HPC-Berechnungsknoten zu erstellen, müssen Sie Folgendes ausführen:

- Installieren Sie Microsoft HPC Pack 2008 auf dem gleichen Computer wie Visual Studio. Der Computer muss nicht Teil des HPC-Clusters sein. Sie können das HPC Pack im [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=4812) installieren.

- Installieren Sie das .NET Framework 4 und die eigenständige Version der Profilerstellungstools auf dem HPC-Berechnungsknoten. Installationsprogramme für .NET Framework und den eigenständigen Profiler stehen auf den Visual Studio-Installationsmedien zur Verfügung. **Hinweis** Sie müssen die Berechnung nach der Installation von .NET Framework und vor der Installation der Profilerstellungstools neu starten.

  So installieren Sie .NET Framework 4 und die eigenständigen Profilerstellungstools auf einem aktiven HPC-Berechnungsknoten und aktivieren die Profilerstellung auf dem Cluster:

1. Öffnen Sie das Eingabeaufforderungsfenster, das im HPC Pack installiert ist.

2. Geben Sie in der Eingabeaufforderung folgende Befehle ein:

    1. `clusrun /all /scheduler:` *%HeadNode% %FxPath%* `/q /norestart`

    2. `clusrun /all /scheduler:` *%HeadNode%* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`

    3. `clusrun /all /scheduler:` *%HeadNode% %ProfilerPath%* `/q /norestart`

| | |
|------------------| - |
| *%HeadNode%* | Der Name des Hauptknotens für den Cluster. |
| *%FxPath%* | Pfad zum .NET Framework 4-Installer. Der Pfad auf den Visual Studio-Installationsmedien lautet: WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe. |
| *%ProfilerPath%* | Der Pfad zur eigenständigen Version des Installationsprogramms der Profilerstellungstools. Der Pfad auf den Visual Studio-Installationsmedien lautet: Standalone Profiler\x64\vs_profiler.exe. |

## <a name="profile-on-an-hpc-compute-node"></a>Profil auf einem HPC-Berechnungsknoten

Konfigurieren Sie eine Profilerstellungssitzung mit dem HPC-Leistungs-Assistenten, um die Informationen des HPC-Cluster und -Ziel anzugeben. Sie können zusätzliche Optionen in der Eigenschaftenseiten der Leistungssitzung festlegen. Die Profilerstellungstools stellen automatisch die erforderlichen Zielbinärdateien bereit und starten den Profiler und die HPC-Anwendung.

1. Klicken Sie im Menü **Analyse** auf **HPC-Leistungs-Assistenten starten**. Wenn der Befehl nicht verfügbar ist, stellen Sie sicher, dass Sie über die oben aufgeführten, erforderlichen Komponenten verfügen.

2. Klicken Sie auf **Weiter** auf der ersten Seite des Assistenten.

3. Wählen Sie auf der zweiten Seite des Assistenten die Anwendung aus, für die Sie ein Profil erstellen möchten.

   - Wählen Sie die Option **Ein oder mehrere verfügbare Projekte** aus, und wählen Sie dann den Namen des Projekts aus der Liste aus, um ein Profil für ein Projekt zu erstellen, das momentan in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] geöffnet ist.

   - Wählen Sie die Option **Eine ausführbare (. EXE-Datei)** aus, um ein Profil für eine Binärdatei zu erstellen, die sich nicht in einem geöffneten Projekt befindet.

4. Klicken Sie auf **Weiter**.

5. Führen Sie auf der vierten Seite des Assistenten folgende Schritte aus:

    - Wenn Sie ein Profil für eine ausführbare Datei erstellen, die sich nicht in einem geöffneten Projekt befindet, geben Sie den Pfad für die Binärdatei in **What is the full path to the executable** (Welcher ist der vollständige Pfad zur ausführbaren Datei) an.

    - Wenn Sie ein Profil für eine ausführbare Datei erstellen, die sich nicht in einem geöffneten Projekt befindet, können Sie angeben, dass alle Befehlszeilenargumente an den Prozess **Befehlszeilenargumente** übergeben werden.

    - Geben Sie in **Remote-Arbeitsverzeichnis** den Pfad zu dem Ordner an, der von den Prozessinstanzen auf den einzelnen Berechnungsknoten verwendet wird.

    - Geben Sie in **Bereitstellungsspeicherort** den Pfad zum Verzeichnis an, das HPC-Server zum Bereitstellen von Images für die Bereitstellung verwendet.

6. Klicken Sie auf **Weiter**.

7. Auf der vierten Seite des Assistenten:

    - Klicken Sie in der Liste **Hauptknoten** auf den Computer, der sich wie der HPC-Hauptknoten in der Profilerstellung verhält. Der Hauptknoten kann „Localhost“ sein. Sie können somit ein Profil auf dem lokalen Computer erstellen, ohne ein Cluster zu benötigen.

    - Klicken Sie in der Liste **Anzahl von Prozessen** auf die Anzahl der Instanzen der Anwendung, die ausgeführt werden sollen.

    - Wählen Sie aus der Liste **Profilerstellungsoptionen** das Ziel Profilerstellungsziel aus.

         Um ein Profil für einen bestimmten Prozess im Cluster zu erstellen, wählen Sie die Option **Profil für Rang** aus, und wählen Sie dann den Rang des Prozesses aus der Dropdown-Liste aus.

         Um ein Profil für den Prozess oder die Prozesse zu erstellen, die auf einem bestimmten Knoten im HPC-Cluster ausgeführt werden, wählen Sie die Option **Profil für Knoten** aus, und wählen Sie dann den Knoten aus der Dropdown-Liste aus.

8. Klicken Sie auf **Weiter**.

9. Auf der fünften Seite des Assistenten können Sie den Profiler und den Profilerstellungsprozess sofort starten oder mithilfe des Leistungs-Explorer später starten.

    - Wählen Sie **Profilerstellung nach Abschluss des Assistenten starten** aus, um die Profilerstellung sofort zu starten, dieses Kontrollkästchen zu deaktivieren, um die Profilerstellung manuell starten.

10. Klicken Sie auf **Fertig stellen**.

## <a name="set-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Festlegen von HPC-Profilerstellungseigenschaften mithilfe von Eigenschaftenseiten der Leistungssitzung

Sie können die Eigenschaften von Leistungssitzungen ändern, die Sie für den HPC-Assistenten der Profilerstellungstools auf der Seite HPC-Starteigenschaften der Eigenschaftenseite der Leistungssitzung festlegen. Sie können zusätzliche Optionen auf der erweiterten HPC-Eigenschaftenseite festlegen.

### <a name="to-open-the-performance-session-property-pages"></a>Öffnen der Eigenschaftenseiten der Leistungssitzung

1. Öffnen Sie bei Bedarf die Leistungssitzungsdatei (.psess) im Leistungs-Explorer. Klicken Sie im Menü **Datei** auf **Öffnen** und suchen Sie die Datei.

2. Klicken Sie im Leistungs-Explorer mit der rechten Maustaste auf den Namen der Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.

3. Um auf das Dialogfeld Eigenschaftenseiten zuzugreifen, verwenden Sie eine der folgenden Methoden:

    - Klicken Sie auf **Allgemein**, und wählen Sie dann **Auf HPC-Cluster erfassen** aus, um die HPC-Profilerstellung zu aktivieren oder deaktivieren Sie dieses Kontrollkästchen, um die HPC-Profilerstellung zu deaktivieren.

    - Klicken Sie auf **HPC-Starteigenschaften**, um die Eigenschaften, die die HPC-Anwendung starten, zu ändern.

    - Sie können zusätzliche Optionen unter **Erweiterte HPC-Eigenschaften** festlegen.

### <a name="hpc-launch-properties"></a>HPC-Starteigenschaften

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|**Hauptknoten**|Gibt den Computer an, der sich wie der HPC-Hauptknoten in der Profilerstellung verhält.|
|**Anzahl der Prozesse**|Gibt die Anzahl der Instanzen der Anwendung an, die in der Anwendung mit der Profilerstellung ausgeführt werden.|
|**Profil für Rang**|Um ein Profil für einen bestimmten Prozess im Cluster zu erstellen, wählen Sie die Option **Profil für Rang** aus, und wählen Sie dann den Rang des Prozesses aus der Dropdown-Liste aus.|
|**Profil für Knoten**|Um ein Profil für den Prozess oder die Prozesse zu erstellen, die auf einem bestimmten Knoten im HPC-Cluster ausgeführt werden, wählen Sie die Option **Profil für Knoten** aus, und wählen Sie dann den Knoten aus der Dropdown-Liste aus.|
|**Remote-Arbeitsverzeichnis**|Gibt den Pfad zu dem Ordner an, der von den Prozessinstanzen auf den einzelnen Berechnungsknoten verwendet wird.|
|**Bereitstellungsspeicherort**|Gibt den Pfad zu dem Verzeichnis an, das von den HPC-Servern zur Bereitstellung von Images für die Bereitstellung verwendet wird.|

### <a name="advanced-properties"></a>Erweiterte Eigenschaften

| Eigenschaft | BESCHREIBUNG |
|---------------------------------------| - |
| **Projektname** | Der Name des aktuellen [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]-Projekts oder -Lösung. |
| **Bereinigen beim Beenden des Profilers** | Wenn TRUE, werden die Binärdateien entfernt, die in das Ausführungsverzeichnis bereitgestellt wurden. Durch das Benutzerprogramm erstellte Dateien und Verzeichnisse werden in diesem Schritt nicht entfernt. Wenn das Ausführungsverzeichnis und das Bereitstellungsverzeichnis von der IDE erstellt wurden, wird die IDE versuchen, diese zu entfernen. Dies geschieht nicht, wenn sie Dateien haben, die nicht von der IDE bereitgestellt wurden. |
| **Zusätzliche bereitzustellende Dateien** | Gibt eine durch Semikolons getrennte Liste mit zusätzlichen Dateien auf den Berechnungsknoten an. Sie können auf die Schaltfläche klicken (**...**), um mithilfe des Dialogfelds mehrere Dateien auszuwählen. |
| **Mpiexec-Befehl** | Gibt die Anwendung an, die die MPI-Anwendung startet. Der Standardwert lautet **mpiexec.exe** |
| **Mpiexec-Argumente** | Gibt die Argumente an, die an den Befehl mpiexec.exe übergeben werden sollen. |
| **Angeforderte Knoten im Cluster** | Gibt die Anzahl der Knoten im Cluster an, auf denen die Anwendung ausgeführt wird. |
| **Bereitstellen von CRT-Dateien** | Wenn TRUE, wird die C/C++-Laufzeit auf dem Cluster bereitgestellt. |
| **Präprofilskript** | Gibt den Pfad und den Dateinamen eines Skripts an, das auf dem lokalen Entwicklungscomputer vor dem Beginn der Profilerstellungssitzung ausgeführt wird. |
| **Präprofilskriptargumente** | Gibt die Argumente an, die an den Befehl mpiexec.exe übergeben werden sollen. |
| **Postprofilskript** | Gibt den Pfad und den Dateinamen eines Skripts an, das auf dem lokalen Entwicklungscomputer nach dem Ende der Profilerstellungssitzung ausgeführt wird. |
| **Postprofilskriptargumente** | Gibt die Argumente an, die an den Befehl mpiexec.exe übergeben werden sollen. |
