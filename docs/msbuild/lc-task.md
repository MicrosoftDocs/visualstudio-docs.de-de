---
title: LC-Aufgabe | Microsoft-Dokumentation
description: Hier erfahren Sie, wie MSBuild die LC-Aufgabe verwendet, um die Datei „LC.exe“ zu umschließen, die eine LICENSE-Datei aus einer LICX-Datei generiert.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70c996d5a8d1d4bf296a395bfb64ead6eba1bb01
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903573"
---
# <a name="lc-task"></a>LC-Aufgabe

Umschließt *LC.exe* , wodurch eine *LICENSE* -Datei aus einer *LICX* -Datei generiert wird. Weitere Informationen zu *LC.exe* finden Sie unter [LC.exe (Lizenzcompiler)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter für die `LC`-Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`LicenseTarget`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt die ausführbare Datei an, für die die *LICENSES* -Dateien generiert werden.|
|`NoLogo`|Optionaler `Boolean`-Parameter.<br /><br /> Unterdrückt die Anzeige des Startbanners von Microsoft.|
|`OutputDirectory`|Optionaler `String`-Parameter.<br /><br /> Gibt das Verzeichnis an, in dem die *LICENSES* -Ausgabedateien gespeichert werden sollen.|
|`OutputLicense`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Ausgabeparameter.<br /><br /> Gibt den Namen der *LICENSES* -Datei an. Wenn Sie keinen Namen angeben, wird der Name der *LICX* -Datei verwendet, und die *LICENSES* -Datei wird in dem Verzeichnis gespeichert, das die *LICX* -Datei enthält.|
|`ReferencedAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die referenzierten Komponenten an, die beim Generieren der *LICENSE* -Datei geladen werden sollen.|
|`SdkToolsPath`|Optionaler `String`-Parameter.<br /><br /> Legt den Pfad zu den SDK-Tools fest, wie z.B. *resgen.exe*.|
|`Sources`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die Elemente mit lizenzierten Komponenten an, die in die *LICENSES* -Datei aufgenommen werden sollen. Weitere Informationen finden Sie in der Dokumentation zum `/complist`-Schalter in [Lc.exe (License Compiler)](/dotnet/framework/tools/lc-exe-license-compiler) (Lc.exe [Lizenzcompiler]).|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die `LC`-Aufgabe zum Kompilieren von Lizenzen verwendet.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
<!-- Item declarations, etc -->

    <Target Name="CompileLicenses">
        <LC
            Sources="@(LicxFile)"
            LicenseTarget="$(TargetFileName)"
            OutputDirectory="$(IntermediateOutputPath)"
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">

            <Output
                TaskParameter="OutputLicenses"
                ItemName="CompiledLicenseFile"/>
        </LC>
    </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
