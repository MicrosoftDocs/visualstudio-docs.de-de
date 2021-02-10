---
title: AL (Assembly Linker)-Aufgabe | Microsoft-Dokumentation
description: Verwenden Sie die MSBuild-Aufgabe „Assembly Linker (AL)“, um AL.exe zu umschließen. Dieses Tool wird mit dem Windows Software Development Kit bereitgestellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AL
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- AL task [MSBuild]
- MSBuild, AL task
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d99c33a74512b380d7b5260d5b7e747c6a39e41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923871"
---
# <a name="al-assembly-linker-task"></a>AL-Aufgabe (Assembly Linker)

Die AL-Aufgabe schließt *AL.exe* ein, ein Tool, das mit dem Windows Software Development Kit (SDK) bereitgestellt wird. Mit dem Assembly Linker-Tool wird eine Assembly mit einem Manifest aus einer oder mehreren Dateien erstellt, bei denen es sich um Module oder Ressourcendateien handelt. Compiler und Entwicklungsumgebungen könnten diese Funktionen möglicherweise bereits bieten, daher ist es häufig nicht erforderlich, diese Aufgabe direkt zu verwenden. Der Assembly Linker ist besonders nützlich für Entwickler, die eine einzelne Assembly aus mehreren Komponentendateien erstellen müssen, z.B. solche, die möglicherweise bei einer Entwicklung in verschiedenen Sprachen produziert werden. Diese Aufgabe kombiniert die Module nicht in einer einzelnen Assemblydatei; die einzelnen Module müssen weiterhin verteilt werden und in der richtigen Reihenfolge verfügbar sein, damit die resultierende Assembly ordnungsgemäß geladen wird. Weitere Informationen zu *AL.exe* finden Sie unter [AL.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `AL` -Aufgabe beschrieben.

| Parameter | Beschreibung |
|---------------------| - |
| `AlgorithmID` | Optionaler `String`-Parameter.<br /><br /> Legt einen Algorithmus zum Hashen aller Dateien in einer Mehrfachdateiassembly mit Ausnahme der Datei, die das Assemblymanifest enthält, fest. Weitere Informationen finden Sie in der Dokumentation zur Option `/algid` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `BaseAddress` | Optionaler `String`-Parameter.<br /><br /> Legt die Adresse fest, an der eine DLL zur Laufzeit auf dem Computer des Benutzers geladen wird. Das Laden von Anwendungen kann beschleunigt werden, wenn nicht das Betriebssystem die DLLs im Prozessbereich verschiebt, sondern die Basisadresse der DLLs angegeben wird. Dieser Parameter entspricht der /base[address](/dotnet/framework/tools/al-exe-assembly-linker). |
| `CompanyName` | Optionaler `String`-Parameter.<br /><br /> Legt eine Zeichenfolge für das Feld `Company` in der Assembly fest. Weitere Informationen finden Sie in der Dokumentation zur Option `/comp[any]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Configuration` | Optionaler `String`-Parameter.<br /><br /> Legt eine Zeichenfolge für das Feld `Configuration` in der Assembly fest. Weitere Informationen finden Sie in der Dokumentation zur Option `/config[uration]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Copyright` | Optionaler `String`-Parameter.<br /><br /> Legt eine Zeichenfolge für das Feld `Copyright` in der Assembly fest. Weitere Informationen finden Sie in der Dokumentation zur Option `/copy[right]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Culture` | Optionaler `String`-Parameter.<br /><br /> Legt die Kulturzeichenfolge fest, die mit der Assembly verknüpft werden soll. Weitere Informationen finden Sie in der Dokumentation zur Option `/c[ulture]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `DelaySign` | Optionaler `Boolean`-Parameter.<br /><br /> `true`, um nur den öffentlichen Schlüssel in die Assembly einzufügen; `false`, um die Assembly vollständig zu signieren. Weitere Informationen finden Sie in der Dokumentation zur Option `/delay[sign]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Description` | Optionaler `String`-Parameter.<br /><br /> Legt eine Zeichenfolge für das Feld `Description` in der Assembly fest. Weitere Informationen finden Sie in der Dokumentation zur Option `/descr[iption]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EmbedResources` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Bettet die angegebenen Ressourcen in das Image ein, das das Assemblymanifest enthält. Diese Aufgabe kopiert den Inhalt der Ressourcendatei in das Image. An Elemente, die an diesen Parameter übergeben werden, sind möglicherweise die optionalen `LogicalName`- und `Access`-Metadaten angefügt. Mit den `LogicalName`-Metadaten wird der interne Bezeichner für die Ressource angegeben.  Die `Access`-Metadaten können auf `private` festgelegt werden, damit die Ressource für andere Assemblys nicht sichtbar ist. Weitere Informationen finden Sie in der Dokumentation zur Option `/embed[resource]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EvidenceFile` | Optionaler `String`-Parameter.<br /><br /> Bettet die angegebene Datei mit dem Ressourcennamen `Security.Evidence` in die Assembly ein.<br /><br /> Sie können `Security.Evidence` nicht für normale Ressourcen verwenden. Dieser Parameter entspricht der Option `/e[vidence]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ExitCode` | Optionaler schreibgeschützter `Int32`-Ausgabeparameter.<br /><br /> Legt den durch den ausgeführten Befehl bereitgestellten Exitcode fest. |
| `FileVersion` | Optionaler `String`-Parameter.<br /><br /> Legt eine Zeichenfolge für das Feld `File Version` in der Assembly fest. Weitere Informationen finden Sie in der Dokumentation zur Option `/fileversion` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Flags` | Optionaler `String`-Parameter.<br /><br /> Legt einen Wert für das Feld `Flags` in der Assembly fest. Weitere Informationen finden Sie in der Dokumentation zur Option `/flags` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `GenerateFullPaths` | Optionaler `Boolean`-Parameter.<br /><br /> Veranlasst die Aufgabe, den absoluten Pfad für alle Dateien zu verwenden, die in einer Fehlermeldung gemeldet werden. Dieser Parameter entspricht der Option `/fullpaths` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyContainer` | Optionaler `String`-Parameter.<br /><br /> Gibt einen Container an, der ein Schlüsselpaar enthält. Dieser wird zum Signieren der Assembly (d. h. zum Zuweisen eines starken Namens zur Assembly) verwendet, indem ein öffentlicher Schlüssel in das Assemblymanifest eingefügt wird. Dann wird die endgültige Assembly von der Aufgabe mit dem privaten Schlüssel signiert. Weitere Informationen finden Sie in der Dokumentation zur Option `/keyn[ame]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyFile` | Optionaler `String`-Parameter.<br /><br /> Legt eine Datei fest, die ein Schlüsselpaar oder einfach einen öffentlichen Schlüssel zum Signieren einer Assembly enthält. Der Compiler fügt den öffentlichen Schlüssel in das Assemblymanifest ein und signiert anschließend die endgültige Assembly mit dem privaten Schlüssel. Weitere Informationen finden Sie in der Dokumentation zur Option `/keyf[ile]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `LinkResources` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Verknüpft die angegebenen Ressourcendateien mit einer Assembly. Die Ressource wird Teil der Assembly, aber die Datei wird nicht kopiert. An Elemente, die an diesen Parameter übergeben werden, sind möglicherweise die optionalen `LogicalName`-, `Target`- und `Access`-Metadaten angefügt. Mit den `LogicalName`-Metadaten wird der interne Bezeichner für die Ressource angegeben. Die `Target`-Metadaten können angeben, in welchen Pfad und mit welchem Dateinamen die Aufgabe die Datei kopiert, bevor sie diese neue Datei in die Assembly kompiliert. Die `Access`-Metadaten können auf `private` festgelegt werden, damit die Ressource für andere Assemblys nicht sichtbar ist. Weitere Informationen finden Sie in der Dokumentation zur Option `/link[resource]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `MainEntryPoint` | Optionaler `String`-Parameter.<br /><br /> Legt den vollqualifizierten Namen (*Klasse.Methode*) der Methode fest, die als Einstiegspunkt verwendet werden soll, wenn ein Modul in eine ausführbare Datei konvertiert wird. Dieser Parameter entspricht der Option `/main` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `OutputAssembly` | Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>-Ausgabeparameter<br /><br /> Legt den Namen der von dieser Aufgabe generierten Datei fest. Dieser Parameter entspricht der Option `/out` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Platform` | Optionaler `String`-Parameter.<br /><br /> Schränkt ein, auf welcher Plattform dieser Code ausgeführt werden kann. Mögliche Werte: `x86`, `Itanium`, `x64` oder `anycpu`. Der Standardwert ist `anycpu`. Dieser Parameter entspricht der Option `/platform` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductName` | Optionaler `String`-Parameter.<br /><br /> Legt eine Zeichenfolge für das Feld `Product` in der Assembly fest. Weitere Informationen finden Sie in der Dokumentation zur Option `/prod[uct]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductVersion` | Optionaler `String`-Parameter.<br /><br /> Legt eine Zeichenfolge für das Feld `ProductVersion` in der Assembly fest. Weitere Informationen finden Sie in der Dokumentation zur Option `/productv[ersion]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ResponseFiles` | Optionaler `String[]`-Parameter.<br /><br /> Legt die Antwortdateien fest, die zusätzliche Optionen enthalten, die über den Assembly Linker übergeben werden sollen. |
| `SdkToolsPath` | Optionaler `String`-Parameter.<br /><br /> Legt den Pfad zu den SDK-Tools wie z.B. „resgen.exe“ fest. |
| `SourceModules` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Ein oder mehrere Module, die in einer Assembly kompiliert werden. Die Module werden im Manifest der resultierenden Assembly aufgelistet und müssen noch verteilt werden und verfügbar sein, damit die Assembly sie laden kann. Die an diesen Parameter übergebenen Elemente haben möglicherweise zusätzliche Metadaten mit dem Namen `Target`, die angeben, in welchen Pfad und mit welchem Dateinamen die Aufgabe die Datei kopiert, bevor sie diese neue Datei in die Assembly kompiliert. Weitere Informationen finden Sie in der Dokumentation zu [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). Dieser Parameter entspricht der Liste der Module, die ohne einen bestimmten Schalter an *Al.exe* übergeben werden. |
| `TargetType` | Optionaler `String`-Parameter.<br /><br /> Legt das Dateiformat der Ausgabedatei fest: `library` (Codebibliothek), `exe` (Konsolenanwendung) oder `win` (Windows-basierte Anwendung). Der Standardwert ist `library`. Dieser Parameter entspricht der Option `/t[arget]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `TemplateFile` | Optionaler `String`-Parameter.<br /><br /> Legt die Assembly fest, von der mit Ausnahme des Felds für die Kultur alle Assemblymetadaten geerbt werden. Die angegebene Assembly muss über einen starken Namen verfügen.<br /><br /> Eine Assembly, die Sie mit dem Parameter `TemplateFile` erstellen, ist eine Satellitenassembly. Dieser Parameter entspricht der Option `/template` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Timeout` | Optionaler `Int32`-Parameter.<br /><br /> Gibt die Zeitdauer in Millisekunden an, nach der die ausführbare Datei der Aufgabe beendet wird. Der Standardwert ist `Int.MaxValue`. Dieser gibt an, dass es kein Zeitlimit gibt. |
| `Title` | Optionaler `String`-Parameter.<br /><br /> Legt eine Zeichenfolge für das Feld `Title` in der Assembly fest. Weitere Informationen finden Sie in der Dokumentation zur Option `/title` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ToolPath` | Optionaler `String`-Parameter.<br /><br /> Legt den Speicherort fest, von wo aus die Aufgabe die zugrunde liegende ausführbare Datei (Al.exe) lädt. Wenn dieser Parameter nicht angegeben ist, verwendet die Aufgabe den SDK-Installationspfad der Version des Frameworks, die von MSBuild ausgeführt wird. |
| `Trademark` | Optionaler `String`-Parameter.<br /><br /> Legt eine Zeichenfolge für das Feld `Trademark` in der Assembly fest. Weitere Informationen finden Sie in der Dokumentation zur Option `/trade[mark]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Version` | Optionaler `String`-Parameter.<br /><br /> Legt Versionsinformationen für diese Assembly fest. Das Format der Zeichenfolge ist *major.minor.build.revision*. Der Standardwert ist 0. Weitere Informationen finden Sie in der Dokumentation zur Option `/v[ersion]` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Icon` | Optionaler `String`-Parameter.<br /><br /> Fügt eine *ICO*-Datei in die Assembly ein. Die *ICO*-Datei verleiht der Ausgabedatei in Datei-Explorer das gewünschte Aussehen. Dieser Parameter entspricht der Option `/win32icon` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Resource` | Optionaler `String`-Parameter.<br /><br /> Fügt eine Win32-Ressource (*RES*-Datei) in die Ausgabedatei ein. Weitere Informationen finden Sie in der Dokumentation zur Option `/win32res` in [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Beispiel

 Das folgende Beispiel erstellt eine Assembly mit den angegebenen Optionen.

```xml
<AL
    EmbedResources="@(EmbeddedResource)"
    Culture="%(EmbeddedResource.Culture)"
    TemplateFile="@(IntermediateAssembly)"
    KeyContainer="$(KeyContainerName)"
    KeyFile="$(KeyOriginatorFile)"
    DelaySign="$(DelaySign)"

    OutputAssembly=
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">

    <Output TaskParameter="OutputAssembly"
        ItemName="SatelliteAssemblies"/>
</AL>
```

## <a name="see-also"></a>Siehe auch

* [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
* [Aufgaben](../msbuild/msbuild-tasks.md)
