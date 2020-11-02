---
title: FXC-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Parameter, die die MSBuild-FXC-Aufgabe für HLSL-Shader-Compiler im Buildprozess verwendet.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.fxc
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), FXC task
- FXC task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: b200fde9e5bc07f654ae2bf11cd8a752efbfe123
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436693"
---
# <a name="fxc-task"></a>FXC-Aufgabe

Verwenden Sie HLSL-Shader-Compiler im Buildprozess.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter der Aufgabe **FXC** beschrieben:

|Parameter|Beschreibung|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Optionaler **string[]** -Parameter.<br/><br/>Gibt mindestens ein Verzeichnis an, das dem include-Pfad hinzugefügt werden soll. Verwenden Sie Semikolons als Trennzeichen, wenn mehrere Verzeichnisse vorhanden sind.<br/><br/>Verwenden Sie `/I[path]`.|
|**AdditionalOptions**|Optionaler **string** -Parameter|
|**AllResourcesBound**|Optionaler **bool** -Parameter.<br/><br/>Der Compiler geht davon aus, dass alle Ressourcen, auf die ein Shader ggf. verweist, gebunden sind und für die Dauer der Shaderausführung einen ordnungsgemäßen Zustand aufweisen. Verfügbar für Shadermodell 5.1 und höher.<br/><br/>Verwenden Sie `/all_resources_bound`.|
|**AssemblerOutput**|Optionaler **string** -Parameter<br/><br/>Gibt die Inhalte der Ausgabedatei für die Assemblysprache an.<br/><br/>Verwenden Sie `/Fc, /Fx`.<br/><br/>**NoListing** <br/>**AssemblyCode** : Verwenden Sie `Fc`.<br/>**AssemblyCodeAndHex** : Verwenden Sie `Fx`.|
|**AssemblerOutputFile**|Optionaler **string** -Parameter<br/><br/>Gibt den Dateinamen für die Assembly-Codelistingdatei an.|
|**CompileD2DCustomEffect**|Optionaler **bool** -Parameter.<br/><br/>Kompiliert einen benutzerdefinierten Direct2D-Effekt mit Pixelshadern. Verwenden Sie diese Option nicht für einen benutzerdefinierten Vertex- oder Computeeffekt.|
|**ConsumeExportFile**|Optionaler **string** -Parameter|
|**DisableOptimizations**|Optionaler **bool** -Parameter.<br/><br/>Deaktiviert Optimierungen.<br/><br/>`/Od` impliziert `/Gfp`, die Ausgabe ist jedoch möglicherweise nicht mit `/Od /Gfp` identisch.|
|**EnableDebuggingInformation**|Optionaler **bool** -Parameter.<br/><br/>Aktiviert Debuginformationen.|
|**EnableUnboundedDescriptorTables**|Optionaler **bool** -Parameter.<br/><br/>Informiert den Compiler, dass ein Shader ggf. eine Deklaration eines Ressourcenarrays mit einem ungebundenen Bereich enthält. Verfügbar für Shadermodell 5.1 und höher.<br/><br/>Verwenden Sie `/enable_unbounded_descriptor_tables`.|
|**EntryPointName**|Optionaler **string** -Parameter<br/><br/>Gibt den Namen des Einstiegspunkts für den Shader an.<br/><br/>Verwenden Sie `/E[name]`.|
|**GenerateExportFile**|Optionaler **string** -Parameter|
|**GenerateExportShaderProfile**|Optionaler **string** -Parameter|
|**HeaderFileOutput**|Optionaler **string** -Parameter<br/><br/>Gibt einen Namen für die Headerdatei mit Objektcode an.<br/><br/>Verwenden Sie `/Fh [name]`.|
|**ObjectFileOutput**|Optionaler **string** -Parameter<br/><br/>Gibt einen Namen für die Objektdatei an.<br/><br/>Verwenden Sie `/Fo [name]`.|
|**PreprocessorDefinitions**|Optionaler **string[]** -Parameter<br/><br/>Definiert Vorverarbeitungssymbole für Ihre Quelldatei.|
|**SetRootSignature**|Optionaler **string** -Parameter<br/><br/>Fügt die Stammsignatur an Shader-Bytecode an. Verfügbar für Shadermodell 5.0 und höher.<br/><br/>Verwenden Sie `/setrootsignature`.|
|**ShaderModel**|Optionaler **string** -Parameter<br/><br/>Gibt das Shadermodell an. Einige Shadertypen können nur mit aktuellen Shadermodellen verwendet werden.<br/><br/>Verwenden Sie `/T [type]_[model]`.|
|**ShaderType**|Optionaler **string** -Parameter<br/><br/>Gibt die Art des Shaders an.<br/><br/>Verwenden Sie `/T [type]_[model]`.<br/><br/>**Effect** : Verwenden Sie `fx`.<br/>**Vertex** : Verwenden Sie `vs`.<br/>**Pixel** : Verwenden Sie `ps`.<br/>**Geometry** : Verwenden Sie `gs`.<br/>**Hull** : Verwenden Sie `hs`.<br/>**Domain** : Verwenden Sie `ds`.<br/>**Compute** : Verwenden Sie `cs`.<br/>**Library** : Verwenden Sie `lib`.<br/>**RootSignature** : Generiert das Stammsignaturobjekt.|
|**Quelle**|Erforderlicher **ITaskItem** -Parameter.|
|**SuppressStartupBanner**|Optionaler **bool** -Parameter.<br/><br/>Unterdrückt die Anzeige des Startbanners und der Informationsmeldung.<br/><br/>Verwenden Sie `/nologo`.|
|**TrackerLogDirectory**|Optionaler **string** -Parameter|
|**TreatWarningAsError**|Optionaler **bool** -Parameter.<br/><br/>Behandelt alle Compilerwarnungen als Fehler.<br/><br/>Bei einem neuen Projekt kann es empfehlenswert sein, `/WX` in allen Kompilierungen zu verwenden. Die Auflösung aller Warnungen stellt sicher, dass möglichst wenig schwer zu findende Codefehler vorhanden sind.|
|**VariableName**|Optionaler **string** -Parameter<br/><br/>Gibt einen Namen für den Variablennamen in der Headerdatei an.<br/><br/>Verwenden Sie `/Vn [name]`.|

## <a name="see-also"></a>Weitere Informationen

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)