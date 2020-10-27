---
title: Behandeln von MSBuild-Problemen und Erstellen von Protokollen
description: Hier erfahren Sie, wie Sie Buildprobleme in Ihrem Visual Studio-Projekt diagnostizieren und ggf. ein Protokoll erstellen können, das zur Untersuchung an Microsoft gesendet wird.
ms.custom: SEO-VS-2020
ms.date: 06/27/2019
ms.technology: vs-ide-compile
ms.topic: troubleshooting
helpviewer_keywords:
- msbuild logs"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: c6b08b243a5b4eec3119ceedbaf2177670aa3e83
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136575"
---
# <a name="troubleshoot-and-create-logs-for-msbuild-problems"></a>Behandeln von MSBuild-Problemen und Erstellen von Protokollen

Mit den folgenden Verfahren können Sie Buildprobleme in Ihrem Visual Studio-Projekt diagnostizieren und ggf. ein Protokoll erstellen, das zur Untersuchung an Microsoft gesendet wird.

## <a name="a-property-value-is-ignored"></a>Ein Eigenschaftswert wird ignoriert

Wenn eine Projekteigenschaft offenbar auf einen bestimmten Wert festgelegt ist, aber keine Auswirkungen auf den Build zeigt, gehen Sie wie folgt vor:

1. Öffnen Sie die Visual Studio Developer-Eingabeaufforderung, die Ihrer Version von Visual Studio entspricht.
1. Führen Sie den folgenden Befehl aus, nachdem Sie die Werte für den Projektmappenpfad, die Konfiguration und den Projektnamen eingesetzt haben:

    ```cmd
    msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /pp:out.xml MyProject.vcxproj
    ```

    Dieser Befehl generiert eine „vorverarbeitete“ msbuild-Projektdatei (out.xml). Sie können diese Datei nach einer bestimmten Eigenschaft durchsuchen, um zu sehen, wo diese definiert ist.

Der Build verwendet immer die letzte Definition einer Eigenschaft. Wenn die Eigenschaft zweimal festgelegt ist, wird der erste Wert durch den zweiten überschrieben. Darüber hinaus wertet MSBuild das Projekt in mehreren Durchläufen aus:

- PropertyGroups und Imports
- ItemDefinitionGroups
- ItemGroups
- Ziele

Bei der folgenden Reihenfolge gilt daher Folgendes:

```xml
<PropertyGroup>
   <MyProperty>A</MyProperty>
</PropertyGroup>
<ItemGroup>
   <MyItems Include="MyFile.txt"/>
</ItemGroup>
<ItemDefinitionGroup>
  <MyItems>
      <MyMetadata>$(MyProperty)</MyMetadata>
  </MyItems>
</ItemDefinitionGroup>
<PropertyGroup>
   <MyProperty>B</MyProperty>
</PropertyGroup>
```

Der Wert von „MyMetadata“ für das Element „MyFile.txt“ wird zur Buildzeit als „B“ ausgewertet (nicht „A“ und nicht leer).

## <a name="incremental-build-is-building-more-than-it-should"></a>Beim inkrementellen Build wird mehr erstellt als erwartet

Wenn MSBuild ein Projekt oder ein Projektelement unnötigerweise neu generiert, erstellen Sie ein detailliertes oder ein binäres Buildprotokoll. Sie können das Protokoll nach der Datei durchsuchen, die unnötigerweise erstellt oder kompiliert wurde. Die Ausgabe sieht in etwa folgendermaßen aus:

```output
  Task "CL"

  Using cached input dependency table built from:

  F:\test\Project1\Project1\Debug\Project1.tlog\CL.read.1.tlog

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ
  Project1.cpp will be compiled because F:\TEST\PROJECT1\PROJECT1\PROJECT1.H was modified at 6/5/2019 12:37:09 PM.

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ

  Write Tracking Logs:
  Debug\Project1.tlog\CL.write.1.tlog
```

Wenn Sie den Build in der Visual Studio-IDE (mit detaillierter Ausführlichkeit im Ausgabefenster) erstellen, wird die Ursache dafür, dass die einzelnen Projekte nicht aktuell sind, im **Ausgabefenster** angezeigt:

```output
1>------ Up-To-Date check: Project: Project1, Configuration: Debug Win32 ------

1>Project is not up-to-date: build input 'f:\test\project1\project1\project1.h' was modified after the last build finished.
```

## <a name="create-a-binary-msbuild-log"></a>Erstellen eines binären msbuild-Protokolls

1. Öffnen Sie die Developer-Eingabeaufforderung für Ihre Version von Visual Studio.
1. Führen Sie an der Eingabeaufforderung einen der folgenden Befehle aus. (Verwenden Sie dabei die tatsächlichen Projekt- und Konfigurationswerte.)

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
    ```

    oder

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
    ```

Eine Datei „Msbuild.binlog“ wird in dem Verzeichnis erstellt, von dem aus Sie MSBuild ausgeführt haben. In der [strukturierten Msbuild-Protokollanzeige](http://www.msbuildlog.com/) können Sie sie anzeigen und durchsuchen.

## <a name="create-a-detailed-log"></a>Erstellen eines detaillierten Protokolls

1. Wechseln Sie im Visual Studio-Hauptmenü zu **Extras** > **Optionen** > **Projekte und Projektmappen** >**Erstellen und ausführen** .
1. Legen Sie **Ausführlichkeit der Protokolldatei des MSBuild-Projektbuilds** in beiden Kombinationsfeldern auf **Detailliert** fest. Das erste steuert die Buildausführlichkeit im **Ausgabefenster** , und das zweite steuert die Buildausführlichkeit in der Datei „\<projectname\>.log“, die während des Buildvorgangs im Zwischenverzeichnis der einzelnen Projekte erstellt wird.
2. Geben Sie an einer Visual Studio Developer-Eingabeaufforderung einen der folgenden Befehle ein, und setzen Sie dabei die tatsächlichen Werte für Pfad und Konfiguration ein:

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln
    ```

    oder

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    Eine Datei „Msbuild.log“ wird in dem Verzeichnis erstellt, von dem aus Sie msbuild ausgeführt haben.

## <a name="see-also"></a>Siehe auch

- [Problembehandlung für Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
