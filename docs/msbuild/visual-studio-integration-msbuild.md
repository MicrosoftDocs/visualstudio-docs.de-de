---
title: Integration von Visual Studio (MSBuild)
titleSuffix: ''
description: Erfahren Sie, wie Visual Studio Projekte im MSBuild-Format hosten kann, selbst wenn diese über ein anderes Tool erstellt wurden und angepasste Buildprozesse verwenden.
ms.custom: seodec18, SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ff8f195b6d77aeab9a01a6f3f6262f4024de1153
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951653"
---
# <a name="visual-studio-integration-msbuild"></a>Integration in Visual Studio (MSBuild)

Visual Studio hostet MSBuild, um verwaltete Projekte zu laden und zu erstellen. Da das Projekt über MSBuild ausgeführt wird, können nahezu alle Projekte im MSBuild-Format erfolgreich in Visual Studio verwendet werden – selbst dann, wenn das Projekt über ein anderes Tool erstellt wurde und einen angepassten Buildprozess verwendet.

 Dieser Artikel beschreibt spezifische Aspekte des MSBuild-Hostings von Visual Studio, die beim Anpassen von Projekten und *TARGETS*-Dateien berücksichtigt werden müssen, die Sie in Visual Studio laden und erstellen möchten. So wird sichergestellt, dass Visual Studio-Funktionen wie IntelliSense und das Debuggen für Ihr benutzerdefiniertes Projekt funktionieren.

 Weitere Informationen über C++-Projekte finden Sie unter [Projektdateien](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Projektdateierweiterungen

 *MSBuild.exe* erkennt jede Projektdateierweiterung, die dem Muster *.\*PROJ* entspricht. Visual Studio hingegen erkennt nur eine Teilmenge dieser Projektdateinamenerweiterungen, die das sprachspezifische Projektsystem zum Laden des Projekts bestimmen. Visual Studio umfasst kein sprachunabhängiges MSBuild-basiertes Projektsystem.

 Beispielsweise können über das C#-Projektsystem *CSPROJ*-Dateien geladen werden, Visual Studio kann aber keine *XXPROJ*-Dateien laden. Eine Projektdatei für Quelldateien in einer beliebigen Sprache muss dieselbe Erweiterung wie Visual Basic- oder C#-Projektdateien verwenden, um in Visual Studio geladen zu werden.

## <a name="well-known-target-names"></a>Bekannte Zielnamen

 Durch Klicken auf den Befehl **Erstellen** in Visual Studio wird das Standardziel im Projekt ausgeführt. Häufig wird dieses Ziel auch als `Build`bezeichnet. Durch Auswählen des Befehls **Neu erstellen** oder **Bereinigen** wird versucht, im Projekt ein Ziel mit dem gleichen Namen auszuführen. Durch Klicken auf **Veröffentlichen** wird das Ziel mit dem Namen `PublishOnly` ausgeführt.

## <a name="configurations-and-platforms"></a>Konfigurationen und Plattformen

 Konfigurationen werden in MSBuild-Projekten durch Eigenschaften dargestellt, die in einem `PropertyGroup`-Element gruppiert werden, das ein `Condition`-Attribut enthält. Visual Studio prüft diese Bedingungen, um eine Liste der anzuzeigenden Projektkonfigurationen und Plattformen zu erstellen. Damit diese Liste erfolgreich extrahiert werden kann, müssen die Bedingungen in einem Format vorliegen, das dem folgenden Format ähnelt:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 In Visual Studio werden zu diesem Zweck die Bedingungen für `PropertyGroup`, `ItemGroup` und `Import` sowie für die Eigenschaft und die Elemente überprüft.

## <a name="additional-build-actions"></a>Zusätzliche Buildvorgänge

 Mit Visual Studio können Sie den Elementtypnamen einer Datei in einem Projekt über die Eigenschaft **Buildvorgang** im Fenster **Dateieigenschaften** ändern. In diesem Menü werden **Compile**, **EmbeddedResource**, **Content** und **None** sowie alle anderen bereits im Projekt vorhandenen Elementtypnamen aufgeführt. Um sicherzustellen, dass alle benutzerdefinierten Elementtypnamen in diesem Menü immer verfügbar sind, können Sie dem Elementtyp `AvailableItemName`die entsprechenden Namen hinzufügen. Durch Hinzufügen des folgenden Elements zur Projektdatei wird beispielsweise in diesem Menü der benutzerdefinierte Typ **JScript** für alle Projekte eingefügt, die diesen Typ importieren:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> Einige Elementtypnamen sind spezifisch für Visual Studio, werden jedoch in diesem Dropdownmenü nicht aufgeführt.

## <a name="in-process-compilers"></a>Prozessinterne Compiler

 In Visual Studio wird nach Möglichkeit die prozessinterne Version des Visual Basic-Compilers verwendet, um eine höhere Leistung zu erzielen. (Gilt nicht für C#.) Dazu müssen die folgenden Bedingungen erfüllt sein:

- Für Visual Basic-Projekte muss in einem Ziel des Projekts eine Aufgabe mit dem Namen `Vbc` vorhanden sein.

- Der `UseHostCompilerIfAvailable` -Parameter der Aufgabe muss auf true festgelegt sein.

## <a name="design-time-intellisense"></a>IntelliSense zur Entwurfszeit

 Um IntelliSense-Unterstützung in Visual Studio zu erhalten, bevor ein Build eine Ausgabeassembly generiert hat, müssen die folgenden Bedingungen erfüllt sein:

- Ein Ziel mit dem Namen `Compile`muss vorliegen.

- Über das `Compile` -Ziel oder eine der zugehörigen Abhängigkeiten muss die Kompilieraufgabe für das Projekt aufgerufen werden, z. B. `Csc` oder `Vbc`.

- Über das `Compile` -Ziel oder eine der zugehörigen Abhängigkeiten muss der Compiler so eingerichtet werden, dass alle erforderlichen Parameter für IntelliSense, vor allem alle Verweise, empfangen werden.

- Die im Abschnitt [Prozessinterne Compiler](#in-process-compilers) aufgeführten Bedingungen müssen erfüllt sein.

## <a name="build-solutions"></a>Erstellen von Projektmappen

 In Visual Studio wird die Anordnung der Projektmappendateien und Projektbuilds durch Visual Studio selbst gesteuert. Wenn eine Lösung mit *msbuild.exe* über die Befehlszeile erstellt wird, analysiert MSBuild die Lösungsdatei und ordnet die Projektbuilds an. In beiden Fällen werden die Projekte einzeln in der Reihenfolge der Abhängigkeiten erstellt. Gleichzeitig werden Verweise zwischen Projekten nicht durchlaufen. Wenn hingegen einzelne Projekte mit *msbuild.exe* erstellt werden, werden Verweise zwischen Projekten durchlaufen.

 Bei der Kompilierung innerhalb von Visual Studio wird die Eigenschaft `$(BuildingInsideVisualStudio)` auf `true` festgelegt. Damit kann im Projekt oder in den *TARGETS*-Dateien festgelegt werden, dass der Build ein anderes Verhalten aufweist.

## <a name="display-properties-and-items"></a>Anzeigen von Eigenschaften und Elementen

 Visual Studio erkennt bestimmte Eigenschaftennamen und -werte. Über die folgende Eigenschaft in einem Projekt wird beispielsweise im **Projekt-Designer** im Feld **Anwendungstyp** die Option **Windows-Anwendung** angezeigt.

```xml
<OutputType>WinExe</OutputType>
```

 Der Eigenschaftswert kann im **Projekt-Designer** bearbeitet und in der Projektdatei gespeichert werden. Wird für diese Eigenschaft beim Bearbeiten ein ungültiger Wert angegeben, zeigt Visual Studio beim Laden des Projekts eine Warnmeldung an, und der ungültige Wert wird durch einen Standardwert ersetzt.

 Visual Studio erkennt Standardwerte für einige Eigenschaften. Diese Eigenschaften werden in der Projektdatei nur beibehalten, wenn die Werte vom Standardwert abweichen.

 Eigenschaften mit arbiträren Namen werden in Visual Studio nicht angezeigt. Wenn Sie arbiträre Eigenschaften in Visual Studio ändern möchten, müssen Sie die Projektdatei im XML-Editor öffnen und die Eigenschaften manuell bearbeiten. Weitere Informationen finden Sie im Abschnitt [Bearbeiten von Projektdateien in Visual Studio](#edit-project-files-in-visual-studio) weiter unten in diesem Thema.

 Die im Projekt mit beliebigen Elementtypnamen definierten Elemente werden standardmäßig im **Projektmappen-Explorer** unter dem entsprechenden Projektknoten angezeigt. Um ein Element in der Anzeige auszublenden, legen Sie die `Visible` -Metadaten auf `false`fest. Das folgende Element wird beispielsweise im Buildprozess verwendet, im **Projektmappen-Explorer** jedoch nicht angezeigt.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> Die `Visible`-Metadaten werden vom **Projektmappen-Explorer** für C++-Projekte ignoriert. Elemente werden immer angezeigt, selbst wenn für `Visible` FALSE festgelegt ist.

 Die Elemente, die in den in das Projekt importierten Dateien deklariert sind, werden standardmäßig nicht angezeigt. Die während des Buildprozesses erstellten Elemente werden nie im **Projektmappen-Explorer** angezeigt.

## <a name="conditions-on-items-and-properties"></a>Bedingungen für Elemente und Eigenschaften

 Während eines Builds werden alle Bedingungen vollständig eingehalten.

 Beim Bestimmen der anzuzeigenden Eigenschaftswerte werden Eigenschaften, die Visual Studio als konfigurationsabhängig eingestuft werden, anders bewertet als Eigenschaften, die Visual Studio als konfigurationsunabhängig betrachtet. Für Eigenschaften, die als konfigurationsabhängig betrachtet werden, legt Visual Studio die Eigenschaften `Configuration` und `Platform` in geeigneter Weise fest und weist MSBuild an, das Projekt neu auszuwerten. Bei konfigurationsunabhängigen Eigenschaften wird nicht festgelegt, auf welche Weise Bedingungen ausgewertet werden.

 Bedingte Ausdrücke für Elemente werden beim Festlegen der Elemente, die im **Projektmappen-Explorer** angezeigt werden sollen, immer ignoriert.

## <a name="debugging"></a>Debuggen

 Zum Suchen und Starten der Ausgabeassembly sowie zum Anhängen des Debuggers müssen die Eigenschaften `OutputPath`, `AssemblyName` und `OutputType` in Visual Studio ordnungsgemäß definiert sein. Wenn über den Compiler im Buildprozess keine *PDB*-Datei generiert wurde, kann der Debugger nicht angehängt werden.

## <a name="design-time-target-execution"></a>Zielausführung zur Entwurfszeit

 Visual Studio versucht beim Laden eines Projekts, Ziele mit bestimmten Namen auszuführen. Zu diesen Zielen gehören `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths` und `CopyRunEnvironmentFiles`. Visual Studio führt diese Ziele aus, damit der Compiler zum Bereitstellen von IntelliSense initialisiert, der Debugger initialisiert und die im Projektmappen-Explorer angezeigten Verweise aufgelöst werden können. Wenn die Ziele nicht vorhanden sind, wird das Projekt ordnungsgemäß geladen und erstellt, aber die Entwurfszeitfunktionen in Visual Studio stehen nicht in vollem Umfang zur Verfügung.

## <a name="edit-project-files-in-visual-studio"></a>Bearbeiten von Projektdateien in Visual Studio

 Um ein MSBuild-Projekt direkt zu bearbeiten, können Sie die Projektdatei im XML-Editor von Visual Studio von öffnen.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>So entladen und bearbeiten Sie eine Projektdatei in Visual Studio

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das Projekt , und wählen Sie dann **Projekt entladen** aus.

     Das Projekt ist als **(nicht verfügbar)** gekennzeichnet.

2. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das nicht verfügbare Projekt, und wählen Sie dann **\<Project File> bearbeiten** aus.

     Die Projektdatei wird im XML-Editor von Visual Studio geöffnet.

3. Bearbeiten, speichern und schließen Sie dann die Projektdatei.

4. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das nicht verfügbare Projekt, und wählen Sie dann **Projekt erneut laden** aus.

## <a name="intellisense-and-validation"></a>IntelliSense und Validierung

 Bei Verwendung des XML-Editors zum Bearbeiten von Projektdateien werden IntelliSense und die Validierung über MSBuild-Schemadateien gesteuert. Diese werden im Schemacache installiert, der sich unter *\<Visual Studio installation directory>\Xml\Schemas\1033\MSBuild* befindet.

 Die grundlegenden MSBuild-Typen werden in *Microsoft.Build.Core.xsd* definiert, die von Visual Studio verwendeten allgemeinen Typen werden in *Microsoft.Build.CommonTypes.xsd* definiert. Zum Anpassen der Schemas für die Bereitstellung von IntelliSense und zur Validierung benutzerdefinierter Elementtypnamen, Eigenschaften und Aufgaben können Sie entweder *Microsoft.Build.xsd* bearbeiten oder ein benutzerdefiniertes Schema erstellen, das das CommonTypes-Schema oder Core-Schema enthält. Beim Erstellen eines benutzerdefinierten Schemas müssen Sie den XML-Editor so einrichten, dass das **Eigenschaftenfenster** verwendet wird.

## <a name="edit-loaded-project-files"></a>Bearbeiten geladener Projektdateien

 Visual Studio speichert die Inhalte von Projektdateien und von über Projektdateien importierten Dateien zwischen. Wenn Sie eine geladene Projektdatei bearbeiten, werden Sie von Visual Studio automatisch zum erneuten Laden des Projekts aufgefordert, damit die Änderungen wirksam werden. Wenn Sie jedoch eine Datei bearbeiten, die über ein geladenes Projekt importiert wurde, wird keine Meldung zum Neuladen angezeigt. Sie müssen das Projekt dann manuell entladen und anschließend neu laden, damit Änderungen wirksam werden.

## <a name="output-groups"></a>Ausgabegruppen

 Mehrere in *Microsoft.Common.targets* definierte Ziele verfügen über Namen, die auf `OutputGroups` oder `OutputGroupDependencies` enden. Visual Studio ruft diese Ziele auf, um bestimmte Listen von Projektausgaben abzurufen. Das `SatelliteDllsProjectOutputGroup`-Ziel erstellt beispielsweise eine Liste aller in einem Build erstellten Satellitenassemblys. Diese Ausgabegruppen werden bei Features wie Veröffentlichung, Bereitstellung und Verweisen zwischen Projekten verwendet. Projekte ohne eine entsprechende Definition werden in Visual Studio geladen und erstellt, einige Funktionen werden jedoch möglicherweise nicht ordnungsgemäß ausgeführt.

## <a name="reference-resolution"></a>Auflösen von Verweisen

 Verweisauflösung ist der Prozess, bei dem die in einer Projektdatei gespeicherten Verweiselemente verwendet werden, um tatsächliche Assemblys zu suchen. Visual Studio muss die Verweisauflösung initiieren, um ausführliche Eigenschaften für jeden Verweis im **Eigenschaftenfenster** anzuzeigen. In der folgenden Liste werden die drei Verweistypen sowie deren Auflösung beschrieben.

- Assemblyverweise:

   Das Projektsystem ruft ein Ziel mit dem bekannten Namen `ResolveAssemblyReferences`auf. Von diesem Ziel sollen Elemente mit dem Elementtypnamen `ReferencePath`erstellt werden. Alle Elemente müssen jeweils über eine Elementspezifikation (Wert des `Include` -Attributs eines Elements) mit dem vollständigen Pfad zum entsprechenden Verweis verfügen. Die Elemente sollten über alle Metadaten der übergebenen Eingabeelemente sowie über die folgenden neuen Metadaten verfügen:

  - `CopyLocal`: Gibt an, ob die Assembly in den Ausgabeordner kopiert werden soll. Ist auf true oder false festgelegt.

  - `OriginalItemSpec`: Enthält die ursprüngliche Elementspezifikation des Verweises.

  - `ResolvedFrom`: Auf „{TargetFrameworkDirectory}“ festgelegt, wenn die Auflösung über das .NET Framework-Verzeichnis erfolgte.

- COM-Verweise:

   Das Projektsystem ruft ein Ziel mit dem bekannten Namen `ResolveCOMReferences`auf. Von diesem Ziel sollen Elemente mit dem Elementtypnamen `ComReferenceWrappers`erstellt werden. Alle Elemente müssen jeweils über eine Elementspezifikation mit dem vollständigen Pfad zur Interop-Assembly für den entsprechenden Verweis verfügen. Die Elemente müssen über alle Metadaten der übergebenen Eingabeelemente sowie über neue Metadaten mit dem Namen `CopyLocal` verfügen, mit denen über die Festlegung auf TRUE oder FALSE angegeben wird, ob die Assembly in den Ausgabeordner kopiert werden soll.

- Systemeigene Verweise

   Das Projektsystem ruft ein Ziel mit dem bekannten Namen `ResolveNativeReferences`auf. Von diesem Ziel sollen Elemente mit dem Elementtypnamen `NativeReferenceFile`erstellt werden. Die Elemente müssen über alle Metadaten der übergebenen Eingabeelemente sowie über neue Metadaten mit dem Namen `OriginalItemSpec`mit der ursprünglichen Elementspezifikation des entsprechenden Verweises verfügen.

## <a name="performance-shortcuts"></a>Leistungsoptimierungen

 Wenn Sie die Visual Studio-IDE verwenden, um das Debuggen zu starten (entweder durch Drücken der F5-Taste oder in der Menüleiste durch Auswahl von **Debuggen** > **Debugging starten**) oder um das Projekt zu erstellen (z. B **Erstellen** > **Projektmappe erstellen**), wendet der Buildprozess zur Leistungsverbesserung eine schnelle Überprüfung auf Updates an. In einigen Fällen, in denen benutzerdefinierte Builds Dateien erstellen, die ihrerseits erstellt werden, werden die geänderten Dateien von der schnellen Überprüfung auf Updates nicht einwandfrei erkannt. In Projekten, die eine gründlichere Überprüfung auf Updates erfordern, lässt sich die schnelle Überprüfung auf Aktualisierungen deaktivieren, indem die Umgebungsvariable `DISABLEFASTUPTODATECHECK=1`festgelegt wird. Alternativ kann dies als MSBuild-Eigenschaft im Projekt oder in einer vom Projekt importierten Datei festgelegt werden.

 Für reguläre Builds in Visual Studio trifft die schnelle Überprüfung auf Updates nicht zu, und das Projekt wird erstellt, als ob Sie den Build an der Eingabeaufforderung aufgerufen hätten.

## <a name="see-also"></a>Siehe auch

- [How to: Erweitern des Visual Studio-Buildprozesses](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [Erstellen eines Builds von der IDE aus](../msbuild/starting-a-build-from-within-the-ide.md)
- [Registrieren von .NET Framework-Erweiterungen](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
- [Item-Element (MSBuild)](../msbuild/item-element-msbuild.md)
- [Property-Element (MSBuild)](../msbuild/property-element-msbuild.md)
- [Target-Element (MSBuild)](../msbuild/target-element-msbuild.md)
- [Csc-Aufgabe](../msbuild/csc-task.md)
- [Vbc-Aufgabe](../msbuild/vbc-task.md)
