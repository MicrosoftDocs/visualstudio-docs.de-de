---
title: XSD-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild mithilfe der Aufgabe „XSD“ das XML-Schemadefinitionstool (xsd.exe) umschließt, das Schema- oder Klassendateien aus einer Quelle generiert.
ms.custom: SEO-VS-2020
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (C++))
- MSBuild (C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5aef78460197796767ec1429179e5598d0f12dbc
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047211"
---
# <a name="xsd-task"></a>XSD-Aufgabe

Umschließt das XML-Schemadefinitionstool ( *xsd.exe* ), das Schema- oder Klassendateien aus einer Quelle generiert.

> [!NOTE]
> Ab Visual Studio 2017 ist die Unterstützung von C++-Projekten für *xsd.exe* veraltet. Sie können die APIs **Microsoft.VisualC.CppCodeProvider** weiterhin verwenden, indem Sie die Datei *CppCodeProvider.dll* manuell dem globalen Assemblycache hinzufügen.

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der **XSD** -Aufgabe beschrieben.

- **AdditionalOptions**

     Optionaler **String** -Parameter.

     Eine Liste von Optionen, wie in der Befehlszeile angegeben. Beispiel: /\<option1> /\<option2> /\<option#>. Verwenden Sie diesen Parameter, um Optionen anzugeben, die nicht durch einen anderen **XSD** -Aufgabenparameter repräsentiert werden.

- **GenerateFromSchema**

  Optionaler **String** -Parameter.

  Gibt die Typen an, die aus dem angegebenen Schema generiert werden.

  Geben Sie einen der folgenden Werte an, von denen jeder einer XSD-Option entspricht.

  - **classes** -  **/classes**

  - **dataset** -  **/dataset**

- **Sprache**

     Optionaler **String** -Parameter.

     Gibt die Programmiersprache an, die für den generierten Code verwendet werden soll.

     Wählen Sie zwischen **CS** (C#, der Standard), **VB** (Visual Basic) und **JS** (JScript) aus. Sie können auch einen vollqualifizierten Namen für eine Klasse angeben, die `System.CodeDom.Compiler.CodeDomProvider Class` implementiert.

- **Namespace**

     Optionaler **String** -Parameter.

     Gibt den Laufzeitnamespace für die generierten Typen an.

- **Sources**

     Erforderlicher `ITaskItem[]`-Parameter.

     Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.

- **SuppressStartupBanner**

     Optionaler **Boolean** -Parameter.

     Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.

- **TrackerLogDirectory**

     Optionaler **String** -Parameter.

     Gibt das Verzeichnis für das Nachverfolgungsprotokoll an.

## <a name="see-also"></a>Weitere Informationen

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
