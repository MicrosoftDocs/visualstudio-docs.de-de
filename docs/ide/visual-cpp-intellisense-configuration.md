---
title: Konfigurieren eines C++-Projekts für IntelliSense
description: Hier erfahren Sie, wie Sie Ihr C++-Projekt manuell konfigurieren, um dafür zu sorgen, dass IntelliSense ordnungsgemäß funktioniert. Dazu verwenden Sie die IDE in Visual Studio, um IntelliSense-Probleme zu erkennen und zu beheben.
ms.custom: SEO-VS-2020
ms.date: 10/08/2018
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 34be73203f5c1d01e4674e7892e0f89d4aae4816
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478795"
---
# <a name="configure-a-c-project-for-intellisense"></a>Konfigurieren eines C++-Projekts für IntelliSense

In einigen Fällen müssen Sie Ihr C++-Projekt möglicherweise manuell konfigurieren, damit IntelliSense ordnungsgemäß funktioniert. Für MSBuild-Projekte (basierend auf VCXPROJ-Dateien) können Sie Einstellungen in den Projekteigenschaften anpassen. Für Nicht-MSBuild-Projekte passen Sie die Einstellungen in der Datei „CppProperties.json“ im Stammverzeichnis des Projekts an. In einigen Fällen müssen Sie möglicherweise eine Hinweisdatei erstellen, damit IntelliSense Makrodefinitionen besser verstehen kann. Die Visual Studio-IDE hilft Ihnen, IntelliSense-Probleme zu identifizieren und zu beheben.

## <a name="single-file-intellisense"></a>IntelliSense mit Einzeldatei

Wenn Sie eine Datei öffnen, die nicht in einem Projekt enthalten ist, bietet Visual Studio eine gewisse IntelliSense-Unterstützung, aber standardmäßig werden keine Fehlermarken angezeigt. Wenn auf der **Navigationsleiste** die Angabe *Sonstige Dateien* angezeigt wird, dann erklärt das wahrscheinlich, warum Sie keine Fehlermarken unter falschem Code sehen, oder warum kein Präprozessormakro definiert wird.

## <a name="check-the-error-list"></a>Überprüfen der Fehlerliste

Wenn eine Datei nicht im Einzeldateimodus geöffnet ist und IntelliSense nicht ordnungsgemäß funktioniert, ist die erste Ressource, die Sie überprüfen müssen, das Fenster „Fehlerliste“. Um alle IntelliSense-Fehler für die aktuelle Quelldatei zusammen mit allen enthaltenen Headerdateien anzuzeigen, wählen Sie **Erstellen + IntelliSense** in der Dropdownliste aus:

![VC++-IntelliSense in der Fehlerliste](media/vcpp-intellisense-error-list.png)

IntelliSense generiert maximal 1.000 Fehler. Wenn es über 1000 Fehler in den Headerdateien einer Quelldatei gibt, dann zeigt die Quelldatei nur eine einzige Fehlermarke am Anfang der Quelldatei an.

## <a name="ensure-include-paths-are-correct"></a>Sicherstellen, dass die #include-Pfade richtig sind

### <a name="msbuild-projects"></a>MSBuild-Projekte

Wenn Sie Ihre Builds außerhalb der Visual Studio-IDE ausführen und Ihre Builds erfolgreich sind, IntelliSense aber fehlerhaft ist, ist es möglich, dass Ihre Befehlszeile nicht mit den Projekteinstellungen für mindestens eine Konfiguration synchron ist. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, und stellen Sie sicher, dass alle **#include**-Pfade für die aktuelle Konfiguration und Plattform richtig sind. Wenn die Pfade in allen Konfigurationen und Plattformen identisch sind, können Sie **Alle Konfigurationen** und **Alle Plattformen** auswählen und dann überprüfen, ob die Pfade richtig sind.

![VC++-Include-Verzeichnisse](media/vcpp-intellisense-include-paths.png)

Um die aktuellen Werte für Buildmakros wie **VC_IncludePath** anzuzeigen, wählen Sie die Zeile „Include-Verzeichnisse“ aus, und klicken Sie dann auf das Dropdownmenü auf der rechten Seite. Wählen Sie dann **\<Edit>** aus, und klicken Sie auf die Schaltfläche **Makros**.

### <a name="makefile-projects"></a>Makefile-Projekte

Für Makefile-Projekte, die auf der NMake-Projektvorlage basieren, wählen Sie **NMake** im linken Bereich und dann **Suchpfad** unter der Kategorie **IntelliSense** aus:

![Include-Pfade für das Makefile-Projekt](media/vcpp-intellisense-makefile-include-paths.png)

### <a name="open-folder-projects"></a>Open Folder-Projekte

Stellen Sie für CMake-Projekte sicher, dass die #include-Pfade für alle Konfigurationen in „CMakeLists.txt“ richtig angegeben werden. Andere Projekttypen erfordern möglicherweise eine Datei „CppProperties.json“. Weitere Informationen finden Sie unter [Konfigurieren von IntelliSense mit „CppProperties.json“](/cpp/build/open-folder-projects-cpp#configure-code-navigation-with-cpppropertiesjson). Stellen Sie sicher, dass die Pfade für jede Konfiguration richtig sind, die in der Datei definiert ist.

Wenn ein Syntaxfehler in der Datei „CppProperties.json“ vorliegt, ist IntelliSense in den betroffenen Dateien fehlerhaft. Visual Studio zeigt den Fehler im Ausgabefenster an.

## <a name="tag-parser-issues"></a>Tagparserprobleme

Der Tagparser ist ein „Fuzzy“-C++-Parser, der zum Durchsuchen und für die Navigation verwendet wird. Er ist sehr schnell, versucht aber nicht, jedes Codekonstrukt vollständig zu verstehen.

Beispielsweise wertet er Präprozessormakros nicht aus. Deshalb kann es vorkommen, dass Code, der diese intensiv nutzt, falsch analysiert wird. Wenn der Tagparser auf ein unbekanntes Codekonstrukt trifft, überspringt er möglicherweise die gesamte Coderegion.

Dieses Problem manifestiert sich in Visual Studio häufig auf zweierlei Weise:

1. Wenn die Navigationsleiste ein innerstes Makro anzeigt, wurde die aktuelle Funktionsdefinition übersprungen:

   ![Tagparser überspringt Funktionsdefinition](media/vcpp-intellisense-tag-parser-macro.png)

1. Die IDE bietet an, eine Funktionsdefinition für eine bereits definierte Funktion zu erstellen:

   ![Tagparser bietet an, eine vorhandene Funktion zu definieren](media/vcpp-intellisense-tag-parser-function.png)

Um diese Art von Problemen zu beheben, fügen Sie dem Stammverzeichnis Ihres Lösungsverzeichnisses eine Datei namens **cpp.hint** hinzu. Weitere Informationen finden Sie unter [Hinweisdateien](/cpp/build/reference/hint-files).

Tagparserfehler werden im Fenster **Fehlerliste** angezeigt.

## <a name="validate-project-settings-with-diagnostic-logging"></a>Überprüfen der Projekteinstellungen mit Diagnoseprotokollierung

Um zu überprüfen, ob der IntelliSense-Compiler die richtigen Compileroptionen verwendet (einschließlich der Include-Pfade und Präprozessormakros), aktivieren Sie die Diagnoseprotokollierung von IntelliSense-Befehlszeilen unter **Extras > Optionen > Text-Editor > C/C++ > Erweitert > Diagnoseprotokollierung**. Legen Sie **Protokollierung aktivieren** auf TRUE, den **Protokolliergrad** auf 5 (ausführlichste Protokollierung) und den **Protokollierungsfilter** auf 8 (IntelliSense-Protokollierung) fest.

Das Ausgabefenster zeigt nun die Befehlszeilen an, die an den IntelliSense-Compiler übergeben werden. Hier ist eine Beispielausgabe:

```output
[IntelliSense] Configuration Name: Debug|Win32
[IntelliSense] Toolset IntelliSense Identifier:
[IntelliSense] command line options:
/c
/I.
/IC:\Repo\Includes
/DWIN32
/DDEBUG
/D_DEBUG
/Zc:wchar_t-
/Zc:forScope
/Yustdafx.h
```

Diese Informationen können Ihnen helfen zu verstehen, warum IntelliSense unrichtige Informationen bereitstellt. Wenn das Include-Verzeichnis Ihres Projekts beispielsweise **$(MyVariable)\Include** enthält und das Diagnoseprotokoll **/I\Include** als Include-Pfad anzeigt, bedeutet dies, dass **$(MyVariable)** nicht ausgewertet und aus dem endgültigen Include-Pfad entfernt wurde.

## <a name="about-the-intellisense-build"></a>Informationen zum IntelliSense-Build

Visual Studio verwendet einen speziellen C++-Compiler, um die Datenbank zu erstellen und zu verwalten, die alle IntelliSense-Funktionen unterstützt. Um die IntelliSense-Datenbank mit dem Code synchron zu halten, startet Visual Studio automatisch reine IntelliSense-Builds als Hintergrundtasks als Reaktion auf bestimmte Änderungen in den Projekteinstellungen oder Quelldateien.

In einigen Fällen kann es jedoch vorkommen, dass Visual Studio die IntelliSense-Datenbank nicht rechtzeitig aktualisiert. Wenn Sie beispielsweise einen Befehl **git pull** oder **git checkout** ausführen, kann es bis zu einer Stunde dauern, bis Visual Studio Änderungen in den Dateien erkennt. Sie können eine erneute Überprüfung aller Dateien in einer Projektmappe erzwingen, indem Sie mit der rechten Maustaste auf den Projektknoten im **Projektmappen-Explorer** klicken und dann **Projektmappe neu prüfen** auswählen.

## <a name="troubleshooting-intellisense-build-failures"></a>Problembehandlung bei IntelliSense-Buildfehlern

Ein IntelliSense-Build generiert zwar keine Binärdateien, kann aber trotzdem fehlschlagen. Eine mögliche Ursache für Fehler sind benutzerdefinierte PROPS- oder TARGET-Dateien. In Visual Studio 2017 Version 15.6 und höher werden reine IntelliSense-Buildfehler im Ausgabefenster protokolliert. Legen sie zum Anzeigen dieser Fehler **Ausgabe anzeigen von** auf **Projektmappe** fest:

![Ausgabefenster für Projektmappenfehler](media/vcpp-intellisense-output-window.png)

Die Fehlermeldung weist Sie ggf. an, Ablaufverfolgung zur Entwurfszeit zu aktivieren:

```output
error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
configuration 'Debug|x64'. IntelliSense might be unavailable.
Set environment variable TRACEDESIGNTIME=true and restart
Visual Studio to investigate.
```

Wenn Sie die Umgebungsvariable TRACEDESIGNTIME auf TRUE festlegen und Visual Studio neu starten, sehen Sie im Verzeichnis „%TEMP%“ eine Protokolldatei, die bei der Diagnose des Buildfehlers helfen kann.

Weitere Informationen zur Umgebungsvariablen TRACEDESIGNTIME finden Sie unter [Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Diagnosing-Project-System-Build-Errors.md) und [Gemeinsames Projektsystem](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Die Informationen in diesen Artikeln sind für C++-Projekte relevant.

## <a name="see-also"></a>Weitere Informationen

- [Visual C++ IntelliSense](visual-cpp-intellisense.md)
