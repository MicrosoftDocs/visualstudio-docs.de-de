---
title: MarkupCompilePass2-Aufgabe | Microsoft Docs
description: Erfahren Sie, wie MSBuild die MarkupCompilePass2-Aufgabe verwendet, um einen zweiten Markupkompilierungsschritt für XAML-Dateien auszuführen, die auf Typen im gleichen Projekt verweisen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7425e0342974c3b000486f57227f768aac47b9ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966174"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2-Aufgabe

Mit der Aufgabe <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> wird ein zweiter Markupkompilierungsschritt für XAML-Dateien ausgeführt, die auf Typen im selben Projekt verweisen.

## <a name="task-parameters"></a>Aufgabenparameter

| Parameter | Beschreibung |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Optionaler **Boolean**-Parameter.<br /><br /> Gibt an, ob der Task in einer separaten <xref:System.AppDomain> ausgeführt werden soll. Wenn dieser Parameter **FALSE** zurückgibt, wird die Aufgabe in der gleichen <xref:System.AppDomain> wie MSBuild und schneller ausgeführt. Wenn der Parameter **TRUE** zurückgibt, wird die Aufgabe in einer zweiten <xref:System.AppDomain> isoliert von MSBuild und langsamer ausgeführt. |
| `AssembliesGeneratedDuringBuild` | Optionaler **String[]** -Parameter.<br /><br /> Gibt Verweise auf Assemblys an, die sich während des Buildprozesses ändern. Eine Visual Studio-Projektmappe kann möglicherweise ein Projekt enthalten, das auf die kompilierte Ausgabe eines anderen Projekts verweist. In diesem Fall kann die kompilierte Ausgabe des zweiten Projekts **AssembliesGeneratedDuringBuild** hinzugefügt werden.<br /><br /> Hinweis: **AssembliesGeneratedDuringBuild** muss Verweise auf den vollständigen Satz von Assemblys enthalten, die von einer Projektmappe generiert werden. |
| `AssemblyName` | Erforderlicher **String**-Parameter.<br /><br /> Gibt den Kurznamen der Assembly an, die für ein Projekt generiert wird. Wenn ein Projekt z. B. eine ausführbare Windows-Datei mit dem Namen *WinExeAssembly.exe* generiert, weist der **AssemblyName**-Parameter den Wert **WinExeAssembly** auf. |
| `GeneratedBaml` | Optionaler **ITaskItem[]**-Ausgabeparameter.<br /><br /> Enthält die Liste der generierten Dateien im XAML-Binärformat. |
| `KnownReferencePaths` | Optionaler **String[]** -Parameter.<br /><br /> Gibt Verweise auf Assemblys an, die während des Buildprozesses niemals geändert werden. Enthält Assemblys, die im globalen Assemblycache (GAC), in einem .NET-Installationsverzeichnis usw. enthalten sind. |
| `Language` | Erforderlicher **String**-Parameter.<br /><br /> Gibt die verwaltete Sprache an, die der Compiler unterstützt. Die gültigen Optionen sind **C#**, **VB**, **JScript** und **C++**. |
| `LocalizationDirectivesToLocFile` | Optionaler **String** -Parameter.<br /><br /> Gibt an, wie Lokalisierungsinformationen für jede XAML-Quelldatei generiert werden. Die gültigen Optionen sind **None**, **CommentsOnly** und **All**. |
| `OutputPath` | Erforderlicher **String**-Parameter.<br /><br /> Gibt das Verzeichnis an, in dem die generierten XAML-Binärformatdateien generiert werden. |
| `OutputType` | Erforderlicher **String**-Parameter.<br /><br /> Gibt den Typ der Assembly an, die von einem Projekt generiert wird. Die gültigen Optionen sind **winexe**, **wxe**, **library** und **netmodule**. |
| `References` | Optionaler **ITaskItem[]** -Parameter.<br /><br /> Gibt die Liste der Verweise von Dateien auf Assemblys an, die die in den XAML-Dateien verwendeten Typen enthalten. Ein Verweis zeigt auf die Assembly, die vom <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>-Task generiert wurde, der vor dem <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>-Task ausgeführt werden muss. |
| `RootNamespace` | Optionaler **String** -Parameter.<br /><br /> Gibt den Stammnamespace für Klassen innerhalb des Projekts an. **RootNamespace** wird auch als Standardnamespace für eine generierte Datei mit verwaltetem Code verwendet, wenn die zugehörige XAML-Datei nicht das `x:Class`-Attribut enthält. |
| `XAMLDebuggingInformation` | Optionaler **Boolean**-Parameter.<br /><br /> Sofern **TRUE**, werden Diagnoseinformationen generiert und in die kompilierte XAML-Datei einbezogen, um das Debuggen zu unterstützen. |

## <a name="remarks"></a>Hinweise

Vor dem Ausführen von **MarkupCompilePass2** müssen Sie eine temporäre Assembly mit den Typen generieren, die von den XAML-Dateien verwendet werden, deren Markupkompilierungsschritt aufgeschoben wurde. Sie generieren die temporäre Assembly durch Ausführen der **GenerateTemporaryTargetAssembly**-Aufgabe.

Ein Verweis auf die generierte temporäre Assembly wird bei der Ausführung an <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> übergeben, sodass die XAML-Dateien, deren Kompilierung im ersten Markupkompilierungsschritt aufgeschoben wurde, nun zur Kompilierung in das binäre Format übergeben werden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie mit dem <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>-Task ein zweiter Kompilierungsschritt durchgeführt wird.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass2Task">
    <MarkupCompilePass2
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
  </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

- [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)
- [Referenz zu MSBuild-Tasks für WPF](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Erstellen einer WPF-Anwendung (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Übersicht über WPF-XAML-Browseranwendungen](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
