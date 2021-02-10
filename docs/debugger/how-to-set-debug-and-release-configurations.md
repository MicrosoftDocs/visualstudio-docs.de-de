---
title: Festlegen von Debug- und Releasekonfigurationen | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie Debug- und Releasekonfigurationen in Visual Studio festlegen. Die Debugversion wird zum Debuggen und die Releaseversion für das endgültige Release verwendet.
ms.custom: SEO-VS-2020
ms.date: 10/05/2018
ms.topic: how-to
f1_keywords:
- vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6f96570f517d24492ecdacb4e45450fa7b7ba1cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908393"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Festlegen von Debug- und Releasekonfigurationen in Visual Studio

Visual Studio-Projekte verfügen über separate Release- und Debugkonfigurationen für Ihr Programm. Die Debugversion wird zum Debuggen und die Releaseversion für das endgültige Release verwendet.

In der Debugkonfiguration wird Ihr Programm mit vollständigen symbolischen Debuginformationen und ohne Optimierung kompiliert. Die Optimierung gestaltet das Debuggen etwas schwieriger, da die Beziehung zwischen Quellcode und generierten Anweisungen komplexer ist.

Die Releasekonfiguration Ihres Programms verfügt über keine symbolischen Debuginformationen und wird vollständig optimiert. Für verwalteten Code und C++-Code können Debuginformationen [abhängig von den verwendeten Compileroptionen](#BKMK_symbols_release) in PDB-Dateien generiert werden. Die Erstellung von PDB-Dateien kann hilfreich sein, wenn Sie später Ihre Releaseversion debuggen müssen.

Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfigurationen](../ide/understanding-build-configurations.md).

Sie können die Buildkonfiguration über die Symbolleiste im Menü **Build** oder über die Eigenschaftenseiten des Projekts ändern. Die Eigenschaftenseiten des Projekts sind sprachspezifisch. Das folgende Verfahren zeigt, wie die Buildkonfiguration über die Symbolleiste und das Menü geändert wird. Weitere Informationen zum Ändern der Buildkonfiguration in Projekten mit verschiedenen Sprachen finden Sie weiter unten im Abschnitt [Siehe auch](#see-also).

## <a name="change-the-build-configuration"></a>Ändern der Buildkonfiguration

Führen Sie zum Ändern der Buildkonfiguration eine der folgenden Aktionen aus:

* Wählen Sie im Menü **Build** die Option **Konfigurations-Manager** und anschließend **Debuggen** oder **Release** aus.

oder

* Wählen Sie auf der Symbolleiste im Listenfeld **Projektmappenkonfigurationen** die Option **Debuggen** oder **Release** aus.

  ![Symbolleiste für die Buildkonfiguration](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="generate-symbol-pdb-files-for-a-build-c-c-visual-basic-f"></a><a name="BKMK_symbols_release"></a>Generieren von Symboldateien (PDB-Dateien) für einen Build (C#, C++, Visual Basic, F#)

Sie können Symboldateien (PDB-Dateien) generieren und auswählen, welche Debuginformationen eingeschlossen werden sollen. Bei den meisten Projekttypen werden vom Compiler standardmäßig Symboldateien für Debug- und Releasebuilds generiert. Andere Standardeinstellungen variieren dagegen je nach Projekttyp und Visual Studio-Version.

> [!IMPORTANT]
> Der Debugger lädt nur eine PDB-Datei für eine ausführbare Datei, die genau mit der PDB-Datei übereinstimmt, die zum Zeitpunkt der Erstellung der ausführbaren Datei ebenfalls erstellt wurde (das heißt, die PDB-Datei muss die originale PDB-Datei oder eine Kopie der originalen PDB-Datei sein). Weitere Informationen finden Sie unter [Warum müssen Debuggersymboldateien exakt den Binärdateien entsprechen, mit denen sie erstellt wurden?](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with).

Diese Optionen werden unter Umständen bei jedem Projekttyp anders festgelegt.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generieren von Symboldateien für ein C#-, ASP.NET- oder Visual Basic-Projekt

Ausführliche Informationen zu Projekteinstellungen für Debugkonfigurationen in C# oder Visual Basic finden Sie unter [Projekteinstellungen für C#-Debugkonfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md) bzw. unter [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Wählen Sie im Projektmappen-Explorer das Projekt aus.

2. Wählen Sie das Symbol **Eigenschaften** aus (oder drücken Sie **ALT+EINGABE**).

3. Wählen Sie im Seitenbereich die Option **Erstellen** aus (bzw. **Kompilieren** in Visual Basic).

4. Wählen Sie in der Liste **Konfiguration** die Option **Debuggen** oder **Release** aus.

5. Wählen Sie die Schaltfläche **Erweitert** aus (bzw. die Schaltfläche **Erweiterte Kompilierungsoptionen** in Visual Basic).

6. Wählen Sie in der Liste **Debuginformationen** (bzw. in der Liste **Debuginfo generieren** in Visual Basic) die Option **Vollständig**, **Nur PDB** oder **Portierbar** aus.

   Das portierbare Format ist das neueste plattformübergreifende Format für .NET Core. Weitere Informationen zu den Optionen finden Sie unter [Dialogfeld „Erweiterte Buildeinstellungen“ (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Generieren von PDB-Dateien für Builds in C#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Erstellen Sie das Projekt.

   Die Symboldateien werden vom Compiler im gleichen Ordner erstellt wie die ausführbare Datei oder die Hauptausgabedatei.

### <a name="generate-symbol-files-for-a-c-project"></a>Generieren von Symboldateien für ein C++-Projekt

1. Wählen Sie im Projektmappen-Explorer das Projekt aus.

2. Wählen Sie das Symbol **Eigenschaften** aus (oder drücken Sie **ALT+EINGABE**).

3. Wählen Sie in der Liste **Konfiguration** die Option **Debuggen** oder **Release** aus.

4. Wählen Sie im Seitenbereich **Linker > Debuggen** und anschließend Optionen für **Debuginfo generieren** aus.

   Ausführliche Informationen zu Projekteinstellungen für Debugkonfigurationen in C++ finden Sie unter [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Konfigurieren Sie Optionen für **Programmdatenbankdatei erstellen**.

   In den meisten C++-Projekten wird der Standardwert `$(OutDir)$(TargetName).pdb` verwendet, wodurch PDB-Dateien im Ausgabeordner generiert werden.

   ![Generieren von PDB-Dateien für Builds in C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Erstellen Sie das Projekt.

   Die Symboldateien werden vom Compiler im gleichen Ordner erstellt wie die ausführbare Datei oder die Hauptausgabedatei.

## <a name="see-also"></a><a name="see-also"></a>Siehe auch

- [Angeben von Symboldateien (PDB-Dateien) und Quelldateien im Visual Studio-Debugger (C#, C++, Visual Basic, F#)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)<br/>
- [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [Projekteinstellungen für eine C#-Debugkonfiguration](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [How to: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)