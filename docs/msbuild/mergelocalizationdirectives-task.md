---
title: MergeLocalizationDirectives-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild die MergeLocalizationDirectives-Aufgabe verwendet, um die Lokalisierungsattribute und -kommentare von XAML-Dateien im Binärformat in eine einzige Datei zusammenzuführen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97d04978a2809a4744f62f27c375efdec1e43dcc
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903873"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives-Aufgabe

Die <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives>-Aufgabe führt die Lokalisierungsattribute und -kommentare aus einer oder mehreren XAML-Binärformatdateien für die gesamte Assembly in einer einzelnen Datei zusammen.

## <a name="task-parameters"></a>Aufgabenparameter

| Parameter | Beschreibung |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Erforderlicher **ITaskItem[]** -Parameter.<br /><br /> Gibt die Liste der Dateien mit Lokalisierungsrichtlinien für einzelne Dateien im XAML-Binärformat an. |
| `OutputFile` | Erforderlicher **String** -Ausgabeparameter.<br /><br /> Gibt den Ausgabepfad der kompilierten Lokalisierungsrichtlinien-Assembly an. |

## <a name="remarks"></a>Hinweise

Sie können dem XAML-Inhalt Lokalisierungsattribute und -kommentare hinzufügen. Mit WPF-Lokalisierungsunterstützung (Windows Presentation Foundation) können Sie Lokalisierungsattribute und -kommentare entfernen und in einer von der generierten Assembly separaten *LOC* -Datei ablegen. Verwenden Sie hierzu das **LocalizationPropertyStorage** -Attribut. Weitere Informationen zu Lokalisierungsattributen und -kommentaren sowie **LocalizationPropertyStorage** finden Sie unter [Lokalisierungsattribute und -kommentare](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden die Lokalisierungskommentare mehrerer XAML-Binärformatdateien in einer einzelnen *LOC* -Datei zusammengeführt.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MergeLocalizationDirectivesTask">
    <MergeLocalizationDirectives
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"
      OutputFile="obj\debug\WPFMSBuildSample.loc" />
  </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

- [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)
- [Referenz zu MSBuild-Tasks für WPF](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Erstellen einer WPF-Anwendung (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
