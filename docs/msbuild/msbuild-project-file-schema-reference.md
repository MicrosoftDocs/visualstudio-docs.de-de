---
title: Referenz zum MSBuild-Projektdateischema | Microsoft-Dokumentation
description: Tabelle mit allen XML-Schemaelementen von MSBuild sowie ihren verfügbaren Attributen und untergeordneten Elementen
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b3451101d6ab2483960731281763167c0cd1629c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918975"
---
# <a name="msbuild-project-file-schema-reference"></a>Referenz zum MSBuild-Projektdateischema

Stellt eine Tabelle mit allen XML-Schemaelementen von MSBuild sowie ihren verfügbaren Attributen und untergeordneten Elementen bereit.

 MSBuild verwendet Projektdateien, um der Build-Engine anzuzeigen, was wie erstellt werden soll. MSBuild-Projektdateien sind XML-Dateien, für die das MSBuild-XML-Schema gilt. Dieser Abschnitt beschreibt die XML-Schemadefinitionsdatei (*XSD*) für MSBuild.

Der Schemalink ist in MSBuild-Projektdateien ab Visual Studio 2017 nicht erforderlich. Wenn er vorhanden ist, sollte er unabhängig der Version von Visual Studio ` http://schemas.microsoft.com/developer/msbuild/2003` sein.

## <a name="msbuild-xml-schema-elements"></a>XML-Schemaelemente von MSBuild

 Die folgende Tabelle enthält alle XML-Schemaelemente von MSBuild sowie die untergeordneten Elemente und Attribute.

|Element|Untergeordnete Elemente|Attribute|
|-------------|--------------------|----------------|
|[Choose-Element (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> When|--|
|[Import-Element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Bedingung<br /><br /> Project|
|[ImportGroup-Element](../msbuild/importgroup-element.md)|Importieren|Bedingung|
|[Item-Element (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Bedingung<br /><br /> Exclude<br /><br /> Einschließen<br /><br /> Remove (Entfernen)|
|[ItemDefinitionGroup-Element (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Element*|Bedingung|
|[ItemGroup-Element (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Element*|Bedingung|
|[ItemMetadata-Element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Element*|Bedingung|
|[OnError-Element (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Bedingung<br /><br /> ExecuteTargets|
|[Otherwise-Element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Output-Element (MSBuild)](../msbuild/output-element-msbuild.md)|--|Bedingung<br /><br /> Artikelname<br /><br /> PropertyName<br /><br /> TaskParameter|
|[Parameter-Element](../msbuild/parameter-element.md)|--|Output<br /><br /> ParameterType<br /><br /> Erforderlich|
|[ParameterGroup-Element](../msbuild/parametergroup-element.md)|*Parameter*|--|
|[Project-Element (MSBuild)](../msbuild/project-element-msbuild.md)|Choose<br /><br /> Importieren<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Target<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> Sdk<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[ProjectExtensions-Element (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Property-Element (MSBuild)](../msbuild/property-element-msbuild.md)|--|Bedingung|
|[PropertyGroup-Element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Eigenschaft*|Bedingung|
|[SDK-Element (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|Name<br /><br /> Version|
|[Target-Element (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Aufgabe*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Bedingung<br /><br /> DependsOnTargets<br /><br /> Eingaben<br /><br /> KeepDuplicateOutputs<br /><br /> Name<br /><br /> Ausgaben<br /><br /> Gibt zurück|
|[Task-Element von „Target“ (MSBuild)](../msbuild/task-element-msbuild.md)|Output|Bedingung<br /><br /> ContinueOnError<br /><br /> *Parameter*|
|[Task-Element von „UsingTask“ (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Daten*|Auswerten|
|[UsingTask-Element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> Aufgabe|AssemblyFile<br /><br /> AssemblyName<br /><br /> Bedingung<br /><br /> TaskFactory<br /><br /> TaskName|
|[When-Element (MSBuild)](../msbuild/when-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|Bedingung|

## <a name="see-also"></a>Weitere Informationen

- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Bedingungen](../msbuild/msbuild-conditions.md)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
