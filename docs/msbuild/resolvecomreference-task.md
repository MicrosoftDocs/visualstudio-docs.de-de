---
title: ResolveCOMReference-Task | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild die Aufgabe „ResolveComReference“ verwendet, um eine Liste mit mindestens einem Typbibliotheksnamen oder TLB-Dateien in Speicherorte auf dem Datenträger aufzulösen.
ms.custom: SEO-VS-2020
ms.date: 07/25/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveCOMReference task
- ResolveCOMReference task [MSBuild]
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e98d0d64a8df1dac29127ffcf76fe8b6cc39a43
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048626"
---
# <a name="resolvecomreference-task"></a>ResolveComReference-Aufgabe

Akzeptiert eine Liste aus mindestens einem Typbibliotheksnamen oder mindestens einer *TLB* -Datei und löst diese Bibliotheken an Speicherorten auf Datenträgern auf.

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `ResolveCOMReference` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`DelaySign`|Optionaler `Boolean`-Parameter.<br /><br /> Legt den öffentlichen Schlüssel in der Assembly ab, wenn der Wert `true` ist Signiert die Assembly vollständig, wenn der Wert `false` ist|
|`EnvironmentVariables`|Optionaler `String[]`-Parameter.<br /><br /> Ein Array von Paaren von Umgebungsvariablen; durch Gleichheitszeichen getrennt. Diese Variablen werden an die erstellten *tlbimp.exe* und *aximp.exe* zusätzlich zum regulären Umgebungsblock oder zum ausgewählten Überschreiben übergeben.|
|`ExecuteAsTool`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, werden *tlbimp.exe* und *aximp.exe* von dem entsprechenden Zielframework aus prozessextern ausgeführt, um die erforderlichen Wrapperassemblys zu generieren. Dieser Parameter ermöglicht Multi-Targeting.|
|`IncludeVersionInInteropName`|Optionaler `Boolean`-Parameter.<br /><br /> Die typelib-Version enthält den Wrappernamen, wenn der Wert `true` ist. Der Standardwert ist `false`.|
|`KeyContainer`|Optionaler `String`-Parameter.<br /><br /> Gibt einen Container an, der ein öffentliches/privates Schlüsselpaar enthält.|
|`KeyFile`|Optionaler `String`-Parameter.<br /><br /> Gibt ein Element an, das ein öffentliches/privates Schlüsselpaar enthält.|
|`NoClassMembers`|Optionaler `Boolean`-Parameter.|
|`ResolvedAssemblyReferences`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Gibt die aufgelösten Assemblyverweise an|
|`ResolvedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Gibt die vollqualifizierten Dateien auf Datenträger an, die den physischen Speicherorten der Typbibliotheken entsprechen, die für diesen Task als Eingabe bereitgestellt wurden.|
|`ResolvedModules`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`Parameter.|
|`SdkToolsPath`|Optionaler <xref:System.String?displayProperty=fullName>-Parameter.<br /><br /> Wenn `ExecuteAsTool``true` ist, muss dieser Parameter auf den Pfad der SDK-Tools für die Zielframeworkversion festgelegt werden.|
|`StateFile`|Optionaler `String`-Parameter.<br /><br /> Gibt die Cachedatei für die Zeitstempel von COM-Komponenten an. Falls nicht vorhanden, erstellt jede Ausführung alle Wrapper neu.|
|`TargetFrameworkVersion`|Optionaler `String`-Parameter.<br /><br /> Gibt die Zielframeworkversion des Projekts an.<br /><br /> Der Standardwert ist `String.Empty`. Was bedeutet, dass nicht nach einem Verweis auf Grundlage des Zielframeworks gefiltert werden kann.|
|`TargetProcessorArchitecture`|Optionaler `String`-Parameter.<br /><br /> Gibt die bevorzugte Zielprozessorarchitektur an. Wird nach der Übersetzung an das Flag *tlbimp.exe* /machine übergeben.<br /><br /> Der Parameterwert sollte ein Member des Typs <xref:Microsoft.Build.Utilities.ProcessorArchitecture> sein.|
|`TypeLibFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt den Typbibliothek-Dateipfad zu COM-Verweisen an. In diesem Parameter enthaltene Elemente können Elementmetadaten enthalten. Weitere Informationen finden Sie im Abschnitt [TypeLibFiles-Elementmetadaten](#typelibfiles-item-metadata) weiter unten.|
|`TypeLibNames`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die aufzulösenden Typbibliotheksnamen an. In diesem Parameter enthaltene Elemente müssen einige Elementmetadaten enthalten. Weitere Informationen finden Sie im Abschnitt [TypeLibNames-Elementmetadaten](#typelibnames-item-metadata) weiter unten.|
|`WrapperOutputDirectory`|Optionaler `String`-Parameter.<br /><br /> Der Speicherort auf dem Datenträger für die generierte Interop-Assembly. Wenn diese Elementmetadaten nicht angegeben werden, verwendet der Task den absoluten Pfad des Verzeichnisses, in dem sich die Projektdatei befindet.|

## <a name="typelibnames-item-metadata"></a>TypeLibNames-Elementmetadaten

 In der folgenden Tabelle werden die Elementmetadaten beschrieben, die für an den `TypeLibNames`-Parameter übergebene Elemente zur Verfügung stehen.

|Metadaten|Beschreibung|
|--------------|-----------------|
|`GUID`|Erforderliche Elementmetadaten<br /><br /> Die GUID für die Typbibliothek. Wenn diese Elementmetadaten nicht festgelegt sind, schlägt der Task fehl.|
|`VersionMajor`|Erforderliche Elementmetadaten<br /><br /> Die Hauptversion der Typbibliothek Wenn diese Elementmetadaten nicht festgelegt sind, schlägt der Task fehl.|
|`VersionMinor`|Erforderliche Elementmetadaten<br /><br /> Die Nebenversion der Typbibliothek Wenn diese Elementmetadaten nicht festgelegt sind, schlägt der Task fehl.|
|`EmbedInteropTypes`|Optional `Boolean`-Metadaten.<br /><br />  Bei `true` betten Sie die Interop-Typen aus diesem Verweis direkt in Ihre Assembly ein, anstatt eine Interop-DLL zu generieren.|
|`LocaleIdentifier`|Optionale Elementmetadaten<br /><br /> Der Gebietsschemabezeichner (oder LCID) für die Typbibliothek Dieser wird als 32-Bit-Wert angegeben, der die Sprache identifiziert, die von einem Benutzer, einer Region oder eine Anwendung bevorzugt wird. Wenn diese Elementmetadaten nicht festgelegt sind, verwendet der Task den Standard-Gebietsschemabezeichner „0“ (null).|
|`WrapperTool`|Optionale Elementmetadaten<br /><br /> Gibt das Wrappertool an, das verwendet wird, um den Assemblywrapper für diese Typbibliothek zu generieren. Wenn diese Elementmetadaten nicht festgelegt sind, verwendet der Task das Standardwrappertool „tlbimp“. Die verfügbaren Optionen von Typbibliotheken, die die Groß-/Kleinschreibung nicht beachten, sind:<br /><br /> -   `Primary`: Verwenden Sie dieses Wrappertool, wenn Sie eine bereits generierte primäre Interopassembly für die COM-Komponente verwenden möchten. Wenn Sie dieses Wrappertool verwenden, geben Sie kein Wrapperausgabeverzeichnis an, weil der Task ansonsten fehlschlägt.<br />-   `TLBImp`: Verwenden Sie dieses Wrappertoll, wenn Sie eine Interopassembly für die COM-Komponente generieren möchten.<br />-   `AXImp`: Verwenden Sie dieses Wrappertoll, wenn Sie eine Interopassembly für ein ActiveX-Steuerelement generieren möchten.|

## <a name="typelibfiles-item-metadata"></a>TypeLibFiles-Elementmetadaten

 In der folgenden Tabelle werden die Elementmetadaten beschrieben, die für an den `TypeLibFiles`-Parameter übergebene Elemente zur Verfügung stehen.

|Metadaten|Beschreibung|
|--------------|-----------------|
|`EmbedInteropTypes`|Optionaler `Boolean`-Parameter.<br /><br />  Bei `true` betten Sie die Interop-Typen aus diesem Verweis direkt in Ihre Assembly ein, anstatt eine Interop-DLL zu generieren.|
|`WrapperTool`|Optionale Elementmetadaten<br /><br /> Gibt das Wrappertool an, das verwendet wird, um den Assemblywrapper für diese Typbibliothek zu generieren. Wenn diese Elementmetadaten nicht festgelegt sind, verwendet der Task das Standardwrappertool „tlbimp“. Die verfügbaren Optionen von Typbibliotheken, die die Groß-/Kleinschreibung nicht beachten, sind:<br /><br /> -   `Primary`: Verwenden Sie dieses Wrappertool, wenn Sie eine bereits generierte primäre Interopassembly für die COM-Komponente verwenden möchten. Wenn Sie dieses Wrappertool verwenden, geben Sie kein Wrapperausgabeverzeichnis an, weil der Task ansonsten fehlschlägt.<br />-   `TLBImp`: Verwenden Sie dieses Wrappertoll, wenn Sie eine Interopassembly für die COM-Komponente generieren möchten.<br />-   `AXImp`: Verwenden Sie dieses Wrappertoll, wenn Sie eine Interopassembly für ein ActiveX-Steuerelement generieren möchten.|

> [!NOTE]
> Je mehr Informationen Sie zur Verfügung stellen, um eine Typbibliothek eindeutig identifizieren zu können, desto wahrscheinlicher ist es, dass der Task in die korrekten Dateien auf dem Datenträger auflöst.

## <a name="remarks"></a>Hinweise

Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Utilities.Task>-Klasse. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [Taskbasisklasse](../msbuild/task-base-class.md).

Die COM-DLL muss nicht auf dem Computer registriert werden, damit diese Aufgabe funktioniert.

## <a name="msb4803-error"></a>Fehler MSB4803

Wenn Sie versuchen, ein Projekt auszuführen, das die Aufgabe `ResolveCOMReference` aus den `dotnet`-Befehlen der CLI verwendet, erhalten Sie den Fehler:

```output
MSB4803: The task "ResolveComReference" is not supported on the .NET Core version of MSBuild. Please use the .NET Framework version of MSBuild.
```

Diese Aufgabe wird in der .NET Core-Version von MSBuild nicht unterstützt, die verwendet wird, wenn Sie den Befehl `dotnet build` über die Befehlszeile ausführen. Versuchen Sie, das Projekt zu erstellen, indem Sie [MSBuild.exe](msbuild-command-line-reference.md) an der Developer-Eingabeaufforderung von Visual Studio aufrufen, da diese die .NET Framework-Version von MSBuild verwendet.

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
