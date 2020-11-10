---
title: SGen-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe der Aufgabe „SGen“ das XML Serializer Generator-Tool (Sgen.exe) umschließt, um eine XML-Serialisierungsassembly für Typen zu erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de2437306dba50a1f93b0b94d86af6351b17c0b6
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048349"
---
# <a name="sgen-task"></a>SGen-Aufgabe

Erstellt eine XML-Serialisierungsassembly für Typen in der angegebenen Assembly. Diese Aufgabe umschließt das XML Serializer Generator-Tool ( *Sgen.exe* ). Weitere Informationen finden Sie unter [XML Serializer Generator-Tool (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `SGen` -Aufgabe beschrieben.

| Parameter | Beschreibung |
|-----------------------------| - |
| `BuildAssemblyName` | Erforderlicher `String` -Parameter.<br /><br /> Die Assembly, für die Serialisierungscode generiert werden soll. |
| `BuildAssemblyPath` | Erforderlicher `String` -Parameter.<br /><br /> Der Pfad der Assembly, für die Serialisierungscode generiert werden soll. |
| `DelaySign` | Optionaler `Boolean`-Parameter.<br /><br /> Ist der Wert `true`, gibt dies an, dass Sie nur den öffentlichen Schlüssel in die Assembly platzieren möchten. Ist der Wert `false`, gibt dies an, dass die Assembly vollständig signiert werden soll.<br /><br /> Dieser Parameter hat nur dann Auswirkungen, wenn Sie ihn entweder mit dem `KeyFile`- oder `KeyContainer`-Parameter verwenden. |
| `KeyContainer` | Optionaler `String`-Parameter.<br /><br /> Gibt einen Container an, der ein Schlüsselpaar enthält. Dieser wird zum Signieren der Assembly verwendet, indem ein öffentlicher Schlüssel in das Assemblymanifest eingefügt wird. Dann wird die endgültige Assembly von der Aufgabe mit dem privaten Schlüssel signiert. |
| `KeyFile` | Optionaler `String`-Parameter.<br /><br /> Gibt ein Schlüsselpaar oder einen öffentlichen Schlüssel an, das bzw. der zum Signieren einer Assembly verwendet werden soll. Der Compiler fügt den öffentlichen Schlüssel in das Assemblymanifest ein und signiert anschließend die endgültige Assembly mit dem privaten Schlüssel. |
| `Platform` | Optionaler `String`-Parameter.<br /><br /> Ruft die Compiler-Plattform ab, die zum Generieren der Ausgabeassembly verwendet wird, oder legt sie fest. Dieser Parameter kann den Wert `x86`, `x64` oder `anycpu` haben. Der Standardwert ist `anycpu`. |
| `References` | Optionaler `String[]`-Parameter.<br /><br /> Gibt die Assemblys an, auf die von den Typen, die XML-Serialisierung erfordern, verwiesen wird. |
| `SdkToolsPath` | Optionaler `String`-Parameter.<br /><br /> Legt den Pfad zu den SDK-Tools fest, wie z.B. *resgen.exe*. |
| `SerializationAssembly` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die generierte Serialisierungsassembly. |
| `SerializationAssemblyName` | Optionaler `String`-Parameter.<br /><br /> Gibt den Namen der generierten Serialisierungsassembly an. |
| `ShouldGenerateSerializer` | Erforderlicher `Boolean` -Parameter.<br /><br /> Wenn `true`, sollte die SGen-Aufgabe eine Serialisierungsassembly generieren. |
| `Timeout` | Optionaler `Int32`-Parameter.<br /><br /> Gibt die Zeitdauer in Millisekunden an, nach der die ausführbare Datei der Aufgabe beendet wird. Der Standardwert ist `Int.MaxValue`. Dieser gibt an, dass es kein Zeitlimit gibt. |
| `ToolPath` | Optionaler `String`-Parameter.<br /><br /> Legt den Speicherort fest, von wo aus die Aufgabe die zugrunde liegende ausführbare Datei ( *sgen.exe* ) lädt. Wenn dieser Parameter nicht angegeben ist, verwendet die Aufgabe den SDK-Installationspfad der Version des Frameworks, die von MSBuild ausgeführt wird. |
| `Types` | Optionaler `String[]`-Parameter.<br /><br /> Ruft eine Liste der spezifischen Typen ab, für die Serialisierungscode generiert werden soll, oder legt sie fest. SGen generiert nur für diese Typen Serialisierungscode. |
| `UseProxyTypes` | Erforderlicher `Boolean` -Parameter.<br /><br /> Wenn `true`, generiert die SGen-Aufgabe Serialisierungscode ausschließlich für die Proxytypen des XML-Webdiensts. |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="see-also"></a>Siehe auch

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
