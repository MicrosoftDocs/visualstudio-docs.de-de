---
title: MarkupCompilePass1-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild die MarkupCompilePass1-Aufgabe verwendet, um nicht lokalisierbare XAML-Projektdateien in ein kompiliertes Binärformat zu konvertieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 775884692963da226947a8fac524a8bd440d6c8d
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904271"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1-Aufgabe

Mit der Aufgabe <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> werden nicht lokalisierte XAML-Projektdateien in das kompilierte Binärformat konvertiert.

## <a name="task-parameters"></a>Aufgabenparameter

| Parameter | Beschreibung |
| - | - |
| `AllGeneratedFiles` | Optionaler **ITaskItem[]** -Ausgabeparameter.<br /><br /> Enthält eine vollständige Liste von Dateien, die vom <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>-Task generiert werden. |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Optionaler **Boolean** -Parameter.<br /><br /> Gibt an, ob der Task in einer separaten <xref:System.AppDomain> ausgeführt werden soll. Wenn dieser Parameter **FALSE** zurückgibt, wird die Aufgabe in der gleichen <xref:System.AppDomain> wie MSBuild und schneller ausgeführt. Wenn der Parameter **TRUE** zurückgibt, wird die Aufgabe in einer zweiten <xref:System.AppDomain> isoliert von MSBuild und langsamer ausgeführt. |
| `ApplicationMarkup` | Optionaler **ITaskItem[]** -Parameter.<br /><br /> Gibt den Namen der XAML-Datei mit der Anwendungsdefinition an. |
| `AssembliesGeneratedDuringBuild` | Optionaler **String[]** -Parameter.<br /><br /> Gibt Verweise auf Assemblys an, die sich während des Buildprozesses ändern. Eine Visual Studio-Projektmappe kann möglicherweise ein Projekt enthalten, das auf die kompilierte Ausgabe eines anderen Projekts verweist. In diesem Fall kann die kompilierte Ausgabe des zweiten Projekts dem **AssembliesGeneratedDuringBuild** -Parameter hinzugefügt werden.<br /><br /> Hinweis: Der **AssembliesGeneratedDuringBuild** -Parameter muss Verweise auf den vollständigen Satz von Assemblys enthalten, die von einer Projektmappe generiert werden. |
| `AssemblyName` | Erforderlicher **String** -Parameter.<br /><br /> Gibt den Kurznamen der Assembly an, die für ein Projekt generiert wird. Wenn ein Projekt z. B. eine ausführbare Windows-Datei mit dem Namen *WinExeAssembly.exe* generiert, weist der **AssemblyName** -Parameter den Wert **WinExeAssembly** auf. |
| `AssemblyPublicKeyToken` | Optionaler **String** -Parameter.<br /><br /> Gibt das öffentliche Schlüsseltoken für die Assembly an. |
| `AssemblyVersion` | Optionaler **String** -Parameter.<br /><br /> Gibt die Versionsnummer der Assembly an. |
| `ContentFiles` | Optionaler **ITaskItem[]** -Parameter.<br /><br /> Gibt die Liste loser Inhaltsdateien an. |
| `DefineConstants` | Optionaler **String** -Parameter.<br /><br /> Gibt an, dass der aktuelle Wert von **DefineConstants** beibehalten wird. Dies betrifft die Generierung der Zielassembly. Wenn dieser Parameter geändert wird, könnte die öffentliche API in der Zielassembly geändert und die Kompilierung der XAML-Dateien, die auf lokale Typen verweisen, beeinträchtigt werden. |
| `ExtraBuildControlFiles` | Optionaler **ITaskItem[]** -Parameter.<br /><br /> Gibt eine Liste der Dateien an, die steuern, ob ein erneutes Erstellen ausgelöst wird, wenn der <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>-Task erneut ausgeführt wird. Ein erneutes Erstellen wird ausgelöst, wenn eine dieser Dateien geändert wird. |
| `GeneratedBamlFiles` | Optionaler **ITaskItem[]** -Ausgabeparameter.<br /><br /> Enthält die Liste der generierten Dateien im XAML-Binärformat. |
| `GeneratedCodeFiles` | Optionaler **ITaskItem[]** -Ausgabeparameter.<br /><br /> Enthält die Liste der generierten Dateien mit verwaltetem Code. |
| `GeneratedLocalizationFiles` | Optionaler **ITaskItem[]** -Ausgabeparameter.<br /><br /> Enthält die Liste der Lokalisierungsdateien, die für jede lokalisierbare XAML-Datei generiert wurden. |
| `HostInBrowser` | Optionaler **String** -Parameter.<br /><br /> Gibt an, ob die generierte Assembly eine XAML-Browseranwendung (XBAP) ist. Die gültigen Optionen sind **true** und **false**. Wenn **true** , wird Code generiert, um das Hosten in einem Browser zu unterstützen. |
| `KnownReferencePaths` | Optionaler **String[]** -Parameter.<br /><br /> Gibt Verweise auf Assemblys an, die sich während des Buildprozesses nicht ändern. Enthält Assemblys, die im globalen Assemblycache (GAC), in einem .NET-Installationsverzeichnis usw. enthalten sind. |
| `Language` | Erforderlicher **String** -Parameter.<br /><br /> Gibt die verwaltete Sprache an, die der Compiler unterstützt. Die gültigen Optionen sind **C#** , **VB** , **JScript** und **C++**. |
| `LanguageSourceExtension` | Optionaler **String** -Parameter.<br /><br /> Gibt die Erweiterung an, die der Erweiterung der generierten Datei mit verwaltetem Code angefügt wird:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Wenn für den **LanguageSourceExtension** -Parameter kein bestimmter Wert festgelegt ist, wird die Standarderweiterung für Quelldateinamen einer Sprache verwendet: *.vb* für Visual Basic, *.csharp* für C#. |
| `LocalizationDirectivesToLocFile` | Optionaler **String** -Parameter.<br /><br /> Gibt an, wie Lokalisierungsinformationen für jede XAML-Quelldatei generiert werden. Die gültigen Optionen sind **None** , **CommentsOnly** und **All**. |
| `OutputPath` | Erforderlicher **String** -Parameter.<br /><br /> Gibt das Verzeichnis an, in dem die generierten Dateien mit verwaltetem Code und die Dateien im XAML-Binärformat generiert werden. |
| `OutputType` | Erforderlicher **String** -Parameter.<br /><br /> Gibt den Typ der Assembly an, die von einem Projekt generiert wird. Die gültigen Optionen sind **winexe** , **wxe** , **library** und **netmodule**. |
| `PageMarkup` | Optionaler **ITaskItem[]** -Parameter.<br /><br /> Gibt eine Liste der zu verarbeitenden XAML-Dateien an. |
| `References` | Optionaler **ITaskItem[]** -Parameter.<br /><br /> Gibt die Liste der Verweise von Dateien auf Assemblys an, die die in den XAML-Dateien verwendeten Typen enthalten. |
| `RequirePass2ForMainAssembly` | Optionaler **boolescher** Ausgabeparameter.<br /><br /> Gibt an, ob das Projekt nicht lokalisierbare XAML-Dateien enthält, die auf in die Hauptassembly eingebettete lokale Typen verweisen. |
| `RequirePass2ForSatelliteAssembly` | Optionaler **boolescher** Ausgabeparameter.<br /><br /> Gibt an, ob das Projekt lokalisierbare XAML-Dateien enthält, die auf in die Hauptassembly eingebettete lokale Typen verweisen. |
| `RootNamespace` | Optionaler **String** -Parameter.<br /><br /> Gibt den Stammnamespace für Klassen innerhalb des Projekts an. **RootNamespace** wird auch als Standardnamespace für eine generierte Datei mit verwaltetem Code verwendet, wenn die zugehörige XAML-Datei nicht das `x:Class`-Attribut enthält. |
| `SourceCodeFiles` | Optionaler **ITaskItem[]** -Parameter.<br /><br /> Gibt die Liste der Codedateien für das aktuelle Projekt an. Die Liste enthält keine generierten sprachspezifischen Dateien mit verwaltetem Code. |
| `UICulture` | Optionaler **String** -Parameter.<br /><br /> Gibt die Satellitenassembly für die Benutzeroberflächenkultur an, in die die generierten XAML-Dateien im Binärformat eingebettet werden. Wenn **UICulture** nicht festgelegt ist, werden die generierten XAML-Dateien im Binärformat in die Hauptassembly eingebettet. |
| `XAMLDebuggingInformation` | Optionaler **Boolean** -Parameter.<br /><br /> Sofern **TRUE** , werden Diagnoseinformationen generiert und in die kompilierte XAML-Datei einbezogen, um das Debuggen zu unterstützen. |

## <a name="remarks"></a>Hinweise

Die Aufgabe <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> kompiliert XAML normalerweise im Binärformat und generiert Codedateien. Wenn eine XAML-Datei Verweise auf Typen enthält, die im gleichen Projekt definiert sind, wird ihre Kompilierung in das Binärformat durch **MarkupCompilePass1** auf einen zweiten Markupkompilierungsschritt ( **MarkupCompilePass2** ) aufgeschoben. Die Kompilierung solcher Dateien muss aufgeschoben werden, weil sie warten müssen, bis die referenzierten lokal definierten Typen kompiliert sind. Wenn eine XAML-Datei allerdings ein `x:Class`-Attribut aufweist, generiert <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> die entsprechende sprachspezifische Codedatei.

Eine XAML-Datei ist lokalisierbar, wenn sie Elemente enthält, die das `x:Uid`-Attribut verwenden:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

Eine XAML-Datei verweist auf einen lokal definierten Typ, wenn sie einen XML-Namespace deklariert, der mit dem `clr-namespace`-Wert auf einen Namespace im aktuellen Projekt verweist:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"
    >
    <Grid>
      <Grid.Resources>
        <localNameSpace:LocalType x:Key="localType" />
      </Grid.Resources>
      ...
    </Grid>
</Page>
```

Wenn eine beliebige XAML-Datei lokalisierbar ist oder auf einen lokal definierten Typ verweist, ist ein zweiter Markupkompilierungsschritt erforderlich, bei dem [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) und dann [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md) ausgeführt werden müssen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie XAML-Dateien mit drei *Seiten* in das Binärformat konvertiert werden. *Seite1* enthält einen Verweis auf einen Typ (`Class1`), der sich im Stammnamespace des Projekts befindet und daher nicht in diesem Markupkompilierungsschritt in Binärformatdateien konvertiert wird. Stattdessen wird [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) ausgeführt und anschließend [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass1Task">
    <MarkupCompilePass1
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      ApplicationMarkup="App.xaml"
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"
      SourceCodeFiles="Class1.cs"
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
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