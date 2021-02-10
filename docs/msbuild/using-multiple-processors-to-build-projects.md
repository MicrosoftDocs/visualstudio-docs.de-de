---
title: Verwenden mehrerer Prozessoren für die Erstellung von Projekten | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild Systeme nutzen kann, die mehrere Prozessoren oder Prozessoren mit mehreren Kernen umfassen, indem ein separater Buildprozess für jeden verfügbaren Prozessor erstellt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c1560b40fe94af8dae5223981dd8e0c790320085
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946370"
---
# <a name="use-multiple-processors-to-build-projects"></a>Verwenden mehrerer Prozessoren für die Erstellung von Projekten

MSBuild kann Systeme nutzen, die über mehrere Prozessoren oder Prozessoren mit mehreren Kernen verfügen. Für jeden verfügbaren Prozessor wird ein separater Buildprozess erstellt. Wenn das System zum Beispiel über vier Prozessoren verfügt, werden vier Buildprozesse erstellt. MSBuild kann diese Builds gleichzeitig verarbeiten und daher die Gesamtbuildzeit verringern. Das gleichzeitige Erstellen von Builds führt jedoch zu einigen Änderungen bei Buildprozessen. In diesem Thema werden diese Änderungen erläutert.

## <a name="project-to-project-references"></a>Projekt-zu-Projekt-Verweise

 Wenn die Microsoft-Build-Engine einen Projekt-zu-Projekt-Verweis (P2P) ermittelt, während parallele Builds zum Erstellen eines Projekts verwendet werden, wird der Verweis nur einmal erstellt. Wenn zwei Projekte über den gleichen P2P-Verweis verfügen, wird der Verweis nicht für jedes Projekt neu erstellt. Stattdessen gibt die Build-Engine den gleichen P2P-Verweis an beide Projekte zurück, die davon abhängen. Zukünftige Anforderungen in der Sitzung für das gleiche Ziel erhalten den gleichen P2P-Verweis.

## <a name="cycle-detection"></a>Schleifenerkennung

 Die Zykluserkennung funktioniert genauso wie bei MSBuild 2.0, mit der Ausnahme, dass MSBuild nun Berichte über die Erkennung eines Zyklus zu einem anderen Zeitpunkt oder im Build erstellen kann.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Fehler und Ausnahmen bei der parallelen Builderstellung

 Bei der parallelen Builderstellung können Fehler und Ausnahmen zu einem anderen Zeitpunkt auftreten als bei der nicht parallelen Builderstellung; außerdem kann die Erstellung eines anderen Builds fortgesetzt werden, wenn ein Build nicht erstellt werden kann. MSBuild beendet keinen Projektbuild, der parallel mit einem fehlerhaften Build ausgeführt wird. Der Buildprozess anderer Projekte wird fortgesetzt, bis er erfolgreich abgeschlossen oder fehlgeschlagen ist. Wenn jedoch <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> aktiviert wurde, wird die Erstellung von Builds nicht abgebrochen, auch wenn ein Fehler auftritt.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>C++-Projektdateien (.vcproj) und Projektmappendateien (.sln)

 Sowohl C++-Projekt- als auch -Projektmappendateien ( *.vcxproj* und *.sln*) können an die [MSBuild-Aufgabe](../msbuild/msbuild-task.md) übergeben werden. Für C++-Projekte wird VCWrapperProject aufgerufen, und anschließend wird das interne MSBuild-Projekt erstellt. Für C++-Projektmappen wird SolutionWrapperProject, und anschließend wird das interne MSBuild-Projekt erstellt. In beiden Fällen wird das resultierende Projekt auf die gleiche Weise behandelt wie jedes andere MSBuild-Projekt.

## <a name="multi-process-execution"></a>Multiprozessausführung

 Bei fast allen buildbezogenen Aktivitäten ist es erforderlich, dass das aktuelle Verzeichnis während des Buildprozesses gleich bleibt, um pfadbezogene Fehler zu vermeiden. Aus diesem Grund können Projekte in MSBuild nicht in verschiedenen Threads ausgeführt werden, weil dies zur Erstellung mehrerer Verzeichnisse führen würde.

 Um dieses Problem zu vermeiden und dennoch Builds mit mehreren Prozessen zu ermöglichen, verwendet MSBuild die „Prozessisolation“. Durch Verwendung der Prozessisolation kann MSBuild maximal `n` Prozesse erstellen, wobei `n` der Anzahl von im System verfügbaren Prozessoren entspricht. Wenn MSBuild zum Beispiel eine Projektmappe auf einem System mit zwei Prozessoren erstellt, werden nur zwei Buildprozesse erstellt. Diese Prozesse werden zum Erstellen aller Projekte der Lösung wiederverwendet.

## <a name="see-also"></a>Weitere Informationen

- [Paralleles Erstellen von mehreren Projekten](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Aufgaben](../msbuild/msbuild-tasks.md)
