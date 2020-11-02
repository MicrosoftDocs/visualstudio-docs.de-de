---
title: GenerateTemporaryTargetAssembly-Aufgabe | Microsoft-Dokumentation
description: Verwenden Sie die MSBuild-Aufgabe „GenerateTemporaryTargetAssembly“, um eine Assembly zu erzeugen, wenn ein Projekt auf einen Typ verweist, der lokal deklariert ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- build process [WPF MSBuild], XAML page refers to a locally declared type
- GenerateTemporaryTargetAssembly task [WPF MSBuild]
- GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters
- creating an assembly [WPF MSBuild], XAML page refers to a locally declared type
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a100ad8a3be57288e49a858d6f87851269df303
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436765"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly-Aufgabe

Mit der Aufgabe <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> wird eine Assembly generiert, wenn mindestens eine XAML-Seite in einem Projekt auf einen Typ verweist, der lokal in diesem Projekt deklariert ist. Die generierte Assembly wird entfernt, nachdem der Build abgeschlossen ist, oder wenn beim Buildprozess ein Fehler auftritt.

## <a name="task-parameters"></a>Aufgabenparameter

| Parameter | Beschreibung |
|--------------------------| - |
| `AssemblyName` | Erforderlicher **String** -Parameter.<br /><br /> Gibt den Kurznamen der Assembly an, die für ein Projekt generiert wird, und ist auch der Name der temporär generierten Zielassembly. Wenn ein Projekt z. B. eine ausführbare Windows-Datei mit dem Namen *WinExeAssembly.exe* generiert, weist der **AssemblyName** -Parameter den Wert **WinExeAssembly** auf. |
| `CompileTargetName` | Erforderlicher **String** -Parameter.<br /><br /> Gibt den Namen des MSBuild-Ziels an, das zum Generieren von Assemblys aus Quellcodedateien verwendet wird. Der typische Wert für **CompileTargetName** ist **CoreCompile** . |
| `CompileTypeName` | Erforderlicher **String** -Parameter.<br /><br /> Gibt den Typ der Kompilierung an, die vom Ziel ausgeführt wird, das durch den **CompileTargetName** -Parameter angegeben wird. Für das **CoreCompile** -Ziel ist dieser Wert **Compile** . |
| `CurrentProject` | Erforderlicher **String** -Parameter.<br /><br /> Gibt den vollständigen Pfad der MSBuild-Projektdatei für das Projekt an, das eine temporäre Zielassembly erfordert. |
| `GeneratedCodeFiles` | Optionaler **ITaskItem[]** -Parameter.<br /><br /> Gibt die Liste der sprachspezifischen verwalteten Codedateien an, die mit der [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)-Aufgabe generiert wurden. |
| `IntermediateOutputPath` | Erforderlicher **String** -Parameter.<br /><br /> Gibt das Verzeichnis an, in dem die temporäre Zielassembly generiert wird. |
| `MSBuildBinPath` | Erforderlicher **String** -Parameter.<br /><br /> Gibt den Speicherort von *MSBuild.exe* an, die zum Kompilieren der temporären Zielassembly erforderlich ist. |
| `ReferencePath` | Optionaler **ITaskItem[]** -Parameter.<br /><br /> Gibt eine Liste von Assemblys nach Pfad und Namen an, auf die die Typen verweisen, die in die temporäre Zielassembly kompiliert werden. |
| `ReferencePathTypeName` | Erforderlicher **String** -Parameter.<br /><br /> Gibt den Parameter an, der vom Kompilierungszielparameter ( **CompileTargetName** ) verwendet wird, der die Liste der Assemblyverweise ( **ReferencePath** ) angibt. Der entsprechende Wert ist **ReferencePath** . |

## <a name="remarks"></a>Hinweise

Im ersten Markupkompilierungsschritt, der von [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) ausgeführt wird, werden XAML-Dateien in das Binärformat kompiliert. Folglich benötigt der Compiler eine Liste der referenzierten Assemblys mit den Typen, die von den XAML-Dateien verwendet werden. Wenn jedoch eine XAML-Datei einen Typ verwendet, der im selben Projekt definiert ist, wird eine entsprechende Assembly für das Projekt erst bei Erstellung des Projekts erstellt. Aus diesem Grund kann ein Assemblyverweis nicht beim ersten Markupkompilierungsschritt bereitgestellt werden.

Stattdessen verschiebt **MarkupCompilePass1** die Konvertierung von XAML-Dateien, die Verweise auf Typen im gleichen Projekt enthalten, auf einen zweiten Markupkompilierungsschritt, der von [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md) ausgeführt wird. Bevor **MarkupCompilePass2** ausgeführt wird, wird eine temporäre Assembly generiert. Diese Assembly enthält die von den XAML-Dateien verwendeten Typen, deren Markupkompilierungsschritt aufgeschoben wurde. Ein Verweis auf die generierte Assembly wird während der Ausführung an **MarkupCompilePass2** übergeben, um die Konvertierung der zurückgestellten XAML-Dateien in das Binärformat zu ermöglichen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird eine temporäre Assembly generiert, da *Page1.xaml* einen Verweis auf einen Typ im gleichen Projekt enthält.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="GenerateTemporaryTargetAssemblyTask">
    <GenerateTemporaryTargetAssembly
      AssemblyName="WPFMSBuildSample"
      CompileTargetName="CoreCompile"
      CompileTypeName="Compile"
      CurrentProject="FullBuild.proj"
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"
      IntermediateOutputPath=".\obj\debug\"
      MSBuildBinPath="$(MSBuildBinPath)"
      ReferencePathTypeName="ReferencePath"/>
  </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

- [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)
- [Referenz zu MSBuild-Tasks](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Erstellen einer WPF-Anwendung (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Übersicht über WPF-XAML-Browseranwendungen](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
