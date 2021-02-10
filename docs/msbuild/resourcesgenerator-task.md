---
title: ResourcesGenerator-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe der Aufgabe „ResourcesGenerator“ mindestens eine Ressource in eine RESOURCES-Datei einbettet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a26c8bfc29ca985a725deea6c75b14d68abb9eb4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937887"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator-Aufgabe

Die <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator>-Aufgabe bettet mindestens eine Ressource (*JPG*, *ICO*, *BMP*, XAML im Binärformat und andere Erweiterungstypen) in eine *RESOURCES*-Datei ein.

## <a name="task-parameters"></a>Aufgabenparameter

|Parameter|Beschreibung|
|---------------|-----------------|
|`OutputPath`|Erforderlicher **String**-Parameter.<br /><br /> Gibt den Pfad des Ausgabeverzeichnisses an. Wenn der Pfad kein absoluter Pfad ist, wird er als relativer Pfad zum Stammverzeichnis des Projekts behandelt.|
|`OutputResourcesFile`|Erforderlicher **ITaskItem[]**-Ausgabeparameter.<br /><br /> Gibt Pfad und Namen der generierten *RESOURCES*-Datei an. Wenn der Pfad kein absoluter Pfad ist, wird die *RESOURCES*-Datei relativ zum Stammverzeichnis des Projekts generiert.|
|`ResourcesFiles`|Erforderlicher **ITaskItem[]** -Parameter.<br /><br /> Gibt eine oder mehrere Ressourcen zum Einbetten in die generierte *RESOURCES*-Datei an.|

## <a name="example"></a>Beispiel

 Im folgenden Beispiel wird eine *RESOURCES*-Datei mit einer einzelnen *BMP*-Ressource generiert. Die *BMP*-Ressource wird in einem Verzeichnis generiert, das relativ zum Stammverzeichnis des Projekts ist.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="ResourcesGeneratorTask">
    <ResourcesGenerator
      ResourceFiles="Resource1.bmp"
      OutputPath="myresources"
      OutputResourcesFile="myresources\my.resources" />
  </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

- [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)
- [Referenz zu MSBuild-Tasks](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Erstellen einer WPF-Anwendung (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)