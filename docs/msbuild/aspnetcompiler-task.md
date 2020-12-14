---
title: Verwenden der AspNetCompiler-Aufgabe zum Vorkompilieren von ASP.NET
description: Verwenden Sie die MSBuild-Aufgabe „AspNetCompiler“, um „aspnet_compiler.exe“ zu umschließen. Dieses Hilfsprogramm wird zum Vorkompilieren von ASP.NET-Anwendungen verwendet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: e77316628f2251fd44d27edaec4c91354fd81a4b
ms.sourcegitcommit: 02445b684e69c1a665a7e06e9b46072d3fcd7ba6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96516092"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler-Aufgabe

Die Aufgabe `AspNetCompiler` schließt *aspnet_compiler.exe* ein, ein Hilfsprogramm zum Vorkompilieren von ASP.NET-Anwendungen.

## <a name="task-parameters"></a>Aufgabenparameter

In der folgenden Tabelle werden die Parameter der `AspNetCompiler` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn dieser Parameter `true` ist, erlaubt die Assembly mit starkem Namen Aufrufer, die nicht voll vertrauenswürdig sind.|
|`Clean`|Optionaler `Boolean`-Parameter<br /><br /> Wenn dieser Parameter `true` ist, wird die vorkompilierte Anwendung bereinigt erstellt. Zuvor kompilierte Komponenten werden erneut kompiliert. Der Standardwert ist `false`. Dieser Parameter entspricht dem **-c**-Schalter in *aspnet_compiler.exe*.|
|`Debug`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn dieser Parameter `true` ist, werden während der Kompilierung Debuginformationen (PDB-Datei) ausgegeben. Der Standardwert ist `false`. Dieser Parameter entspricht dem **-d**-Schalter in *aspnet_compiler.exe*.|
|`DelaySign`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn dieser Parameter `true` ist, wird die Assembly bei ihrer Erstellung nicht vollständig signiert.|
|`FixedNames`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn dieser Parameter `true` ist, erhalten die kompilierten Assemblys feste Namen.|
|`Force`|Optionaler `Boolean`-Parameter<br /><br /> Wenn dieser Parameter `true` ist, überschreibt die Aufgabe das Zielverzeichnis, wenn es bereits vorhanden ist. Vorhandene Inhalte gehen verloren. Der Standardwert ist `false`. Dieser Parameter entspricht dem **-f**-Schalter in *aspnet_compiler.exe*.|
|`KeyContainer`|Optionaler `String`-Parameter.<br /><br /> Gibt einen Schlüsselcontainer mit starkem Namen an.|
|`KeyFile`|Optionaler `String`-Parameter.<br /><br /> Legt den physischen Pfad zur Schlüsseldatei mit starkem Namen fest.|
|`MetabasePath`|Optionaler `String`-Parameter.<br /><br /> Legt den vollständigen IIS-Metabasispfad der Anwendung fest. Dieser Parameter kann nicht mit Parameter `VirtualPath` oder `PhysicalPath` kombiniert werden. Dieser Parameter entspricht dem **-m**-Schalter in *aspnet_compiler.exe*.|
|`PhysicalPath`|Optionaler `String`-Parameter.<br /><br /> Legt den physischen Pfad der zu kompilierenden Anwendung fest. Wenn dieser Parameter nicht vorhanden ist, wird die IIS-Metabasis verwendet, um die Anwendung zu suchen. Dieser Parameter entspricht dem **-p**-Schalter in *aspnet_compiler.exe*.|
|`TargetFrameworkMoniker`|Optionaler `String`-Parameter.<br /><br /> Legt den TargetFrameworkMoniker fest, der angibt, welche .NET Framework-Version von *aspnet_compiler.exe* verwendet werden soll. Akzeptiert nur .NET Framework-Moniker.|
|`TargetPath`|Optionaler `String`-Parameter.<br /><br /> Legt den physischen Pfad fest, unter dem die Anwendung kompiliert wird. Wenn nicht angegeben, wird die Anwendung direkt vorkompiliert.|
|`Updateable`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn dieser Parameter `true` ist, ist die vorkompilierte Anwendung aktualisierbar.  Der Standardwert ist `false`. Dieser Parameter entspricht dem **-u**-Schalter in *aspnet_compiler.exe*.|
|`VirtualPath`|Optionaler `String`-Parameter.<br /><br /> Der virtuelle Pfad der zu kompilierenden Anwendung. Wenn `PhysicalPath` festgelegt ist, wird der physische Pfad verwendet, um die Anwendung zu suchen. Andernfalls wird die IIS-Metabasis verwendet, und es wird angenommen, dass sich die Anwendung am Standardspeicherort befindet. Dieser Parameter entspricht dem **-v**-Schalter in *aspnet_compiler.exe*.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die `AspNetCompiler`-Aufgabe zum Vorkompilieren einer ASP.NET-Anwendung verwendet.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="PrecompileWeb">
        <AspNetCompiler
            VirtualPath="/MyWebSite"
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"
            TargetPath="c:\precompiledweb\MyWebSite\"
            Force="true"
            Debug="true"
        />
    </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

* [Aufgaben](../msbuild/msbuild-tasks.md)
* [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
* [ASP.NET-Kompilierungstool (aspnet_compiler.exe)](/previous-versions/ms229863(v=vs.100))
