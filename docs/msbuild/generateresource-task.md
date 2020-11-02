---
title: GenerateResource-Aufgabe | Microsoft-Dokumentation
description: Verwenden Sie die MSBuild-Aufgabe „GenerateResource“, um TXT- und RESX-Dateien in das bzw. aus dem RESSOURCES-Format der Common Language Runtime zu konvertieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateResource task
- GenerateResource task [MSBuild]
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 124e5dcc3666698dd71927e15c3686038233c317
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436870"
---
# <a name="generateresource-task"></a>GenerateResource-Aufgabe

Konvertiert zwischen *TXT-* und *RESX* -Dateien (im XML-basierten Ressourcenformat) und binären *RESOURCES* -Dateien der Common Language Runtime, die in eine ausführbare Laufzeitbinärdatei eingebettet oder in Satellitenassemblys kompiliert werden können. Diese Aufgabe dient normalerweise zum Konvertieren von *TXT* - oder *RESX* -Dateien in *RESOURCES* -Dateien. Die `GenerateResource`-Aufgabe ist funktional identisch mit [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator).

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der `GenerateResource` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`AdditionalInputs`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Enthält zusätzliche Eingaben für die Abhängigkeitsüberprüfung, die von dieser Aufgabe ausgeführt wird. Beispielsweise sollten die Projekt- und Zieldateien in der Regel Eingaben sein, damit bei ihrer Aktualisierung alle Ressourcen neu generiert werden.|
|`EnvironmentVariables`|Optionaler `String[]`-Parameter.<br /><br /> Gibt ein Array von Name-Wert-Paaren von Umgebungsvariablen an, das zusätzlich zum regulären Umgebungsblock (oder diesen selektiv überschreibend) an die erzeugte *resgen.exe* übergeben werden sollte.|
|`ExcludedInputPaths`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt ein Array von Elementen an, die Pfade angeben; nachverfolgte Eingaben aus diesen Pfaden werden während der Überprüfung auf aktuellen Stand ignoriert.|
|`ExecuteAsTool`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, werden *tlbimp.exe* und *aximp.exe* von dem entsprechenden Zielframework aus prozessextern ausgeführt, um die erforderlichen Wrapperassemblys zu generieren. Dieser Parameter ermöglicht die Festlegung von Zielversionen von `ResolveComReferences`.|
|`FilesWritten`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Namen aller auf den Datenträger geschriebenen Dateien. Dies schließt ggf. auch die Cachedatei ein. Dieser Parameter ist hilfreich für Implementierungen des Bereinigens.|
|`MinimalRebuildFromTracking`|Optionaler `Boolean`-Parameter.<br /><br /> Ruft einen Schalter ab, der angibt, ob ein nachverfolgter inkrementeller Build verwendet wird, oder legt ihn fest. Wenn `true`, wird der inkrementelle Build aktiviert; andernfalls wird eine erneute Erstellung erzwungen.|
|`NeverLockTypeAssemblies`|Optionaler `Boolean`-Parameter.<br /><br /> Dient zum Abrufen oder Festlegen eines booleschen Werts, der angibt, ob eine neue [AppDomain](/dotnet/api/system.appdomain) zum Auswerten der Ressourcendateien ( *RESX* ) erstellt werden soll (true) oder ob eine neue [AppDomain](/dotnet/api/system.appdomain) nur erstellt werden soll, wenn die Ressourcendateien auf die Assembly eines Benutzers verweisen (false).|
|`OutputResources`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Gibt den Namen der generierten Dateien an, z.B. der *RESOURCES* -Dateien. Wenn Sie keinen Namen angeben, wird der Name der entsprechenden Eingabedatei verwendet, und die erstellte *RESOURCES* -Datei wird in dem Verzeichnis gespeichert, das die Eingabedatei enthält.|
|`PublicClass`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, wird eine stark typisierte Ressourcenklasse als öffentliche Klasse erstellt.|
|`References`|Optionaler `String[]`-Parameter.<br /><br /> Verweise, aus denen Typen in *RESX* -Dateien geladen werden. Datenelemente der *RESX* -Datei können vom Typ „.NET“ sein. Wenn die *RESX* -Datei gelesen wird, muss dieser aufgelöst werden. In der Regel wird dies mit Typladungsregeln erfolgreich aufgelöst. Wenn Sie in `References` Assemblys angeben, haben diese Vorrang.<br /><br /> Dieser Parameter ist für stark typisierte Ressourcen nicht erforderlich.|
|`SdkToolsPath`|Optionaler `String`-Parameter.<br /><br /> Legt den Pfad zu den SDK-Tools fest, wie z.B. *resgen.exe* .|
|`Sources`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die zu konvertierenden Elemente an. An diesen Parameter übergebene Elemente müssen eine der folgenden Erweiterungen aufweisen:<br /><br /> -    *.txt:* Gibt die Erweiterung für eine zu konvertierende Textdatei an. Textdateien dürfen nur Zeichenfolgenressourcen enthalten.<br />-    *.resx:* Gibt die Erweiterung für eine zu konvertierende XML-basierte Ressourcendatei an.<br />-    *.restext:* Gibt das gleiche Format wie *.txt* an. Diese andere Erweiterung ist nützlich, wenn Sie Quelldateien klar unterscheiden möchten, die Ressourcen aus anderen Quelldateien in Ihrem Buildprozess enthalten.<br />-    *.resources:* Gibt die Erweiterung für eine zu konvertierende Ressourcendatei an.|
|`StateFile`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt den Pfad zu einer optionalen Cachedatei an, die zum Beschleunigen der Abhängigkeitsprüfung von Verknüpfungen in *RESX* -Eingabedateien verwendet wird.|
|`StronglyTypedClassName`|Optionaler `String`-Parameter.<br /><br /> Gibt den Klassennamen für die stark typisierte Ressourcenklasse an. Wenn dieser Parameter nicht angegeben ist, wird der Basisname der Ressourcendatei verwendet.|
|`StronglyTypedFilename`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt den Dateinamen der Quelldatei an. Wenn dieser Parameter nicht angegeben ist, wird der Name der Klasse mit sprachabhängiger Erweiterung als Basisdateiname verwendet. Beispiel: *MyClass.cs* .|
|`StronglyTypedLanguage`|Optionaler `String`-Parameter.<br /><br /> Gibt die Sprache an, die beim Generieren der Klassenquelle für die Ressource mit starker Typisierung verwendet werden soll. Dieser Parameter muss genau mit einer der Sprachen übereinstimmen, die von CodeDomProvider verwendet werden. Beispiel: `VB` oder `C#`.<br /><br /> Mit der Übergabe eines Werts an diesen Parameter weisen Sie die Aufgabe an, stark typisierte Ressourcen zu generieren.|
|`StronglyTypedManifestPrefix`|Optionaler `String`-Parameter.<br /><br /> Gibt den Ressourcennamespace oder das Manifestpräfix zur Verwendung in der generierten Klassenquelle für die Ressource mit starker Typisierung an.|
|`StronglyTypedNamespace`|Optionaler `String`-Parameter.<br /><br /> Gibt den Namespace an, der für die generierte Klassenquelle für die Ressource mit starker Typisierung verwendet werden soll. Wenn dieser Parameter nicht angegeben wird, befinden sich alle Ressourcen mit starker Typisierung im globalen Namespace.|
|`TLogReadFiles`|Optionaler schreibgeschützter <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Ruft ein Array von Elementen ab, die die Lesenachverfolgungs-Protokolle darstellen.|
|`TLogWriteFiles`|Optionaler schreibgeschützter <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Ruft ein Array von Elementen ab, die die Schreibnachverfolgungs-Protokolle darstellen.|
|`ToolArchitecture`|Optionaler <xref:System.String?displayProperty=fullName>-Parameter.<br /><br /> Wird verwendet, um zu bestimmen, ob *Tracker.exe* zum Erzeugen von *ResGen.exe* verwendet werden muss oder nicht.<br /><br /> Sollte als Mitglied der <xref:Microsoft.Build.Utilities.ExecutableType>-Enumeration analysierbar sein. Wenn `String.Empty`, wird eine Heuristik zum Ermitteln einer Standardarchitektur verwendet. Sollte als Mitglied der Microsoft.Build.Utilities.ExecutableType-Enumeration analysierbar sein.|
|`TrackerFrameworkPath`|Optionaler `String`-Parameter.<br /><br /> Gibt den Pfad zu dem entsprechenden .NET Framework-Speicherort an, der *FileTracker.dll* enthält.<br /><br /> Wenn festgelegt, übernimmt der Benutzer die Verantwortung dafür, sicherzustellen, dass die Bitanzahl von *FileTracker.dll* , die übergeben wird, der Bitanzahl von *ResGen.exe* entspricht, die verwendet werden soll. Wenn nicht festgelegt, wählt die Aufgabe den entsprechenden Speicherort basierend auf der aktuellen .NET Framework-Version.|
|`TrackerLogDirectory`|Optionaler `String`-Parameter.<br /><br /> Gibt das temporäre Verzeichnis an, in dem die Nachverfolgungsprotokolle vom Ausführen dieser Aufgabe gespeichert werden.|
|`TrackerSdkPath`|Optionaler `String`-Parameter.<br /><br /> Gibt den Pfad zu dem entsprechenden Windows SDK-Speicherort an, der *Tracker.exe* enthält.<br /><br /> Wenn dieser festgelegt ist, übernimmt der Benutzer die Verantwortung dafür, sicherzustellen, dass die Bitanzahl von *Tracker.exe* , die übergeben wird, der Bitanzahl von *ResGen.exe* entspricht, die verwendet werden soll. Wenn nicht festgelegt, wählt die Aufgabe den entsprechenden Speicherort basierend auf der aktuellen Windows SDK-Version.|
|`TrackFileAccess`|Optionaler <xref:System.Boolean>-Parameter.<br /><br /> Wenn „true“, wird das Verzeichnis der Eingabedatei zum Auflösen relativer Dateipfade verwendet.|
|`UseSourcePath`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, wird angegeben, dass das Verzeichnis der Eingabedatei zum Auflösen relativer Dateipfade verwendet werden soll.|

## <a name="remarks"></a>Bemerkungen

Da *RESX* -Dateien Links zu anderen Ressourcendateien enthalten können, ist es nicht ausreichend, nur die Zeitstempel von *RESX* - und *RESOURCES* -Dateien zu vergleichen, um festzustellen, ob die Ausgaben aktuell sind. Stattdessen folgt die `GenerateResource`-Aufgabe den Links in den *RESX* -Dateien und prüft ebenfalls die Zeitstempel der verknüpften Dateien. Dies bedeutet, dass Sie `Inputs`- und `Outputs`-Attribute nicht allgemein für das Ziel verwenden sollten, das die `GenerateResource`-Aufgabe enthält, da dies dazu führen könnte, dass es übersprungen wird, wenn es tatsächlich ausgeführt werden sollte.

Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

Bei der Verwendung von MSBuild 4.0 für .NET 3.5-Projekte könnte bei der Ausführung des Builds auf x86-Ressourcen ein Fehler auftreten. Um dieses Problem zu umgehen, können Sie das Ziel als AnyCPU-Assembly erstellen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die `GenerateResource`-Aufgabe verwendet, um *RESOURCES* -Dateien aus den Dateien zu generieren, die von der `Resx`-Elementsammlung angegeben werden.

```xml
<GenerateResource
    Sources="@(Resx)"
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">
    <Output
        TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

Die `GenerateResource`-Aufgabe verwendet die \<LogicalName>-Metadaten eines \<EmbeddedResource>-Elements, um die Ressource zu benennen, die in einer Assembly eingebettet ist.

Unter der Voraussetzung, dass die Assembly „myAssembly“ genannt wird, generiert der folgende Code eine eingebettete Ressource namens *someQualifier.someResource.resources* :

```xml
<ItemGroup>
    <EmbeddedResource Include="myResource.resx">
        <LogicalName>someQualifier.someResource.resources</LogicalName>
    </EmbeddedResource>
</ItemGroup>
```

Ohne die \<LogicalName>-Metadaten würde die Ressource den Namen *myAssembly.myResource.resources* erhalten.  Dieses Beispiel gilt nur für den Visual Basic- und Visual C#-Buildprozess.

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
