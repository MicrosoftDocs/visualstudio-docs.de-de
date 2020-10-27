---
title: Kompilieren und Erstellen
description: Hier erfahren Sie, wie Sie die Buildmethoden der Visual Studio-IDE, MSBuild-Befehlszeilentools oder von Azure Pipelines verwenden, um eine Anwendung zu erstellen.
ms.custom: SEO-VS-2020
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac65fa9eaaf8e318e99e134957b335141f07577c
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136588"
---
# <a name="compile-and-build-in-visual-studio"></a>Kompilieren und Erstellen in Visual Studio

Eine erste Einführung zum Erstellen in der IDE finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Anwendung](walkthrough-building-an-application.md).

Sie können mit der Visual Studio-IDE, MSBuild-Befehlszeilentools und Azure Pipelines eine Anwendung erstellen:

| Erstellungsmethode | Vorteile |
| --- |--- | --- |
| IDE |- Direktes Erstellen von Builds und Testen in einem Debugger<br />- Ausführen von Multiprozessorbuilds für C++- und C#-Projekte<br />- Anpassen verschiedener Aspekte des Buildsystems |
| CMake | – Erstellen von Projekten mit dem CMake-Tool<br />– Verwenden desselben Buildsystems für Linux- und Windows-Plattformen |
| MSBuild-Befehlszeile| - Erstellen von Projekten, ohne Visual Studio zu installieren<br />- Ausführen von Multiprozessorbuilds für alle Projekttypen<br />- Anpassen der meisten Bereiche des Buildsystems|
| Azure Pipelines | - Automatisieren des Buildprozesses als Teil einer fortlaufenden Integration oder einer fortlaufenden Zustellpipeline<br />- Anwenden von automatisierten Tests mit jedem Build<br />– Verwenden der nahezu unbegrenzten cloudbasierten Ressourcen für Buildprozesse<br />- Anpassen des Buildworkflows und Erstellen von Buildaktivitäten zum Ausführen benutzerdefinierter Aufgaben|

Die Dokumentation in diesem Bereich geht näher auf den IDE-basierten Buildprozess ein. Weitere Informationen zu den anderen Methoden finden Sie unter [MSBuild](../msbuild/msbuild.md) und [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Kompilieren und Generieren in Visual Studio für Mac](/visualstudio/mac/compiling-and-building).

## <a name="overview-of-building-from-the-ide"></a>Überblick: Erstellen aus der IDE

Wenn Sie ein Projekt erstellen, erstellt Visual Studio Standardbuildkonfigurationen für das Projekt und die Projektmappe, die das Projekt enthält.  Diese Konfigurationen definieren, wie die Projektmappen und Projekte erstellt und bereitgestellt werden. Insbesondere die Projektkonfigurationen sind eindeutig für die jeweilige Zielplattform (z.B. Windows oder Linux) und den Buildtyp (z.B. Debug oder Release). Sie können diese Konfigurationen beliebig bearbeiten und nach Bedarf eigene Konfigurationen erstellen.

Eine erste Einführung zum Erstellen in der IDE finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Anwendung](walkthrough-building-an-application.md).

Unter [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) finden Sie Informationen zur Anpassung verschiedener Aspekte, die Sie an diesem Prozess vornehmen können. Diese Anpassungen beinhalten das [Ändern des Ausgabeverzeichnisses](how-to-change-the-build-output-directory.md), das [Angeben benutzerdefinierter Ereignisse](specifying-custom-build-events-in-visual-studio.md), das [Verwalten von Projektabhängigkeiten](how-to-create-and-remove-project-dependencies.md), das [Verwalten von Buildprotokolldateien](how-to-view-save-and-configure-build-log-files.md) und das [Unterdrücken von Compilerwarnungen](how-to-suppress-compiler-warnings.md).

Eine Vielzahl weiterer Aufgaben finden Sie hier:
- [Grundlagen der Buildkonfiguration](understanding-build-configurations.md)
- [Grundlagen zu Buildplattformen](understanding-build-platforms.md)
- [Verwalten von Projekt- und Projektmappeneigenschaften](managing-project-and-solution-properties.md)
- Geben Sie Buildereignisse in [C#](how-to-specify-build-events-csharp.md) und [Visual Basic](how-to-specify-build-events-visual-basic.md) an.
- [Festlegen von Buildoptionen](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Build Multiple Projects in Parallel (Paralleles Erstellen mehrerer Projekte)](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="see-also"></a>Siehe auch

- [Erstellen von Websites](/previous-versions/hwxa5aha(v=vs.140))
- [Kompilieren und Erstellen (Visual Studio für Mac)](/visualstudio/mac/compiling-and-building)
- [CMake-Projekte in Visual Studio](/cpp/build/cmake-projects-in-visual-studio)