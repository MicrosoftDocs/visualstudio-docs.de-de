---
title: GetWinFXPath-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die MSBuild-Aufgabe „GetWinFXPath“ verwenden, die das Verzeichnis der aktuellen .NET-Laufzeit zurückgibt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 820ca103d88cde941fe558e59ed1c78622adccd4
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436766"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath-Aufgabe

Die Aufgabe <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> gibt das Verzeichnis der aktuellen .NET-Runtime zurück.

## <a name="task-parameters"></a>Aufgabenparameter

| Parameter | Beschreibung |
|-------------------| - |
| `WinFXPath` | Optionaler **String** -Ausgabeparameter.<br /><br /> Gibt den tatsächlichen Pfad zur .NET-Runtime an. |
| `WinFXNativePath` | Erforderlicher **String** -Parameter.<br /><br /> Gibt den Pfad zur nativen .NET-Runtime an. |
| `WinFXWowPath` | Erforderlicher **String** -Parameter.<br /><br /> Gibt den Pfad zu den .NET-Assemblys im 32-Bit- **Windows on Windows** -Modul auf 64-Bit-Systemen an. |

## <a name="remarks"></a>Hinweise

 Wenn der <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath>-Task auf einem 64-Bit-Prozessor ausgeführt wird, wird der **WinFXPath** -Parametersatz auf den Pfad festgelegt, der im **WinFXWowPath** -Parameter gespeichert ist. Andernfalls wird der **WinFXPath** -Parameter auf den Pfad festgelegt, der im **WinFXNativePath** -Parameter gespeichert ist.

## <a name="example"></a>Beispiel

 Das folgende Beispiel zeigt, wie Sie die **GetWinFXPath** -Aufgabe verwenden, um den nativen Pfad zur .NET-Runtime zu ermitteln.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="GetWinFXPathTask">
    <GetWinFXPath
      WinFXNativePath="c:\WinFXNative"
      WinFXWowPath="c:\WinFXWowNative" />
  </Target>
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />
</Project>
```

## <a name="see-also"></a>Siehe auch

- [WPF-MSBuild-Referenz](../msbuild/wpf-msbuild-reference.md)
- [Referenz zu MSBuild-Tasks](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Erstellen einer WPF-Anwendung (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
