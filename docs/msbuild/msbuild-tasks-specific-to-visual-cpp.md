---
title: Spezifische MSBuild-Aufgaben für C++ | Microsoft-Dokumentation
description: Erfahren Sie, welche MSBuild-Aufgaben verfügbar sind und beim Kompilieren von C++-Code verwendet werden, wenn C++ installiert ist.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 82ba5ad3beb8a676df23cc69184c8766bca72f77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878265"
---
# <a name="msbuild-tasks-specific-to-c"></a>Spezifische MSBuild-Aufgaben für C++

Aufgaben stellen den Code bereit, der während des Buildprozesses ausgeführt wird. Wenn C++ installiert wird, sind zusätzlich zu den mit MSBuild installierten Aufgaben die folgenden Aufgaben verfügbar. Weitere Informationen finden Sie unter [Übersicht über MSBuild (C++)](/cpp/build/msbuild-visual-cpp-overview).

 Zusätzlich zu den Parametern für jede Aufgabe hat jede Aufgabe auch die folgenden Parameter.

| Parameter | Beschreibung |
|-------------------| - |
| `Condition` | Optionaler `String`-Parameter.<br /><br /> Ein `Boolean`-Ausdruck, mit dem die MSBuild-Engine bestimmt, ob diese Aufgabe ausgeführt wird. Informationen zu den von MSBuild unterstützten Bedingungen finden Sie unter [Bedingungen](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Dieser Parameter ist optional. Kann einen oder mehrere der folgenden Werte enthalten:<br /><br /> -   **WarnAndContinue** oder **true**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element [Ziel](../msbuild/target-element-msbuild.md) und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Warnungen behandelt.<br />-   **ErrorAndContinue**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element `Target` und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Fehler behandelt.<br />-   **ErrorAndStop** oder **false** (Standard). Wenn eine Aufgabe fehlschlägt, werden die übrigen Aufgaben im Element `Target` und im Build nicht ausgeführt, und das komplette Element `Target` sowie der Build wird als fehlgeschlagen betrachtet.<br /><br /> Versionen von .NET Framework vor 4.5 unterstützten nur die Werte `true` und `false`.<br /><br /> Weitere Informationen finden Sie unter [Vorgehensweise: Ignorieren von Fehlern in Aufgaben](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[BscMake-Aufgabe](../msbuild/bscmake-task.md)|Führt das Microsoft-Wartungshilfsprogramm zum Durchsuchen von Informationen aus (*bscmake.exe*).|
|[CL-Aufgabe](../msbuild/cl-task.md)|Umschließt das C++-Compilertool (*cl.exe*).|
|[CPPClean-Aufgabe](../msbuild/cppclean-task.md)|Löscht die temporären Dateien, die MSBuild erstellt, wenn ein C++-Projekt erstellt wird.|
|[ClangCompile-Aufgabe](../msbuild/clangcompile-task.md)|Umschließt das C++-Compilertool (*clang.exe*).|
|[CustomBuild-Aufgabe](../msbuild/custombuild-task.md)|Umschließt das C++-Compilertool (*cmd.exe*).|
|[FXC-Aufgabe](../msbuild/fxc-task.md)|Verwenden Sie HLSL-Shader-Compiler im Buildprozess.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Liest alte Nachverfolgungsprotokolle, schreibt neue Nachverfolgungsprotokolle und gibt Elemente zurück, die nicht auf dem neuesten Stand sind. (Hilfsaufgabe)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Ruft Ausgabedateinamen für CL und andere Tools ab, die nur die Angabe des Ausgabeverzeichnisses oder des vollständigen Dateinamens zulassen. (Hilfsaufgabe)|
|[LIB-Aufgabe](../msbuild/lib-task.md)|Umschließt das 32-Bit-Tool von Microsoft zur Bibliotheksverwaltung (*lib.exe*).|
|[Link-Aufgabe](../msbuild/link-task.md)|Umschließt das C++-Linkertool (*link.exe*).|
|[MIDL-Aufgabe](../msbuild/midl-task.md)|Umschließt das MIDL-Compilertool (Microsoft Interface Definition Language) (*midl.exe*).|
|[MT-Aufgabe](../msbuild/mt-task.md)|Umschließt das Microsoft-Manifesttool (*mt.exe*).|
|[MultiToolTask-Aufgabe](../msbuild/multitooltask-task.md)|Keine Beschreibung|
|[ParallelCustomBuild-Aufgabe](../msbuild/parallelcustombuild-task.md)|Führen Sie parallele Instanzen der [CustomBuild Aufgabe](../msbuild/custombuild-task.md) aus.|
|[RC-Aufgabe](../msbuild/rc-task.md)|Umschließt das Microsoft Windows-Ressourcencompilertool (*rc.exe*).|
|[SetEnv-Aufgabe](../msbuild/setenv-task.md)|Legt den Wert einer bestimmten Umgebungsvariable fest oder löscht ihn.|
|[TrackedVCToolTask-Basisklasse](../msbuild/trackedvctooltask-base-class.md)|Erbt von [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[VCMessage-Aufgabe](../msbuild/vcmessage-task.md)|Protokolliert Warn- und Fehlermeldungen während eines Builds. (Nicht erweiterbar. Nur zur internen Verwendung.)|
|[VCToolTask-Basisklasse](../msbuild/vctooltask-base-class.md)|Erbt von [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask).|
|[XDCMake-Aufgabe](../msbuild/xdcmake-task.md)|Umschließt das XML-Dokumentationstool (*xdcmake.exe*), das die XML-Dokument-Kommentardateien ( *.xdc*) in einer *XML*-Datei zusammengeführt.|
|[XSD-Aufgabe](../msbuild/xsd-task.md)|Umschließt das XML-Schemadefinitionstool (*xsd.exe*), das Schema- oder Klassendateien aus einer Quelle generiert. *Siehe Hinweis weiter unten.*|
|[MSBuild-Referenz](../msbuild/msbuild-reference.md)|Beschreibt die Elemente des MSBuild-Systems.|
|[Aufgaben](../msbuild/msbuild-tasks.md)|Beschreibt die Aufgaben, die Einheiten von Code darstellen, die kombiniert werden können, um einen Build zu erstellen.|
|[Schreiben von Aufgaben](../msbuild/task-writing.md)|Beschreibt das Erstellen einer Aufgabe.|

> [!NOTE]
> Ab Visual Studio 2017 ist die Unterstützung von C++-Projekten für *xsd.exe* veraltet. Sie können die APIs **Microsoft.VisualC.CppCodeProvider** weiterhin verwenden, indem Sie die Datei *CppCodeProvider.dll* manuell dem globalen Assemblycache hinzufügen.
