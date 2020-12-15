---
title: Verwenden des Managed Package Frameworks für einen Projekttyp (c#)
description: Erfahren Sie mehr über das verwaltete Paket Framework, das .NET-Klassen bereitstellt, die Sie verwenden oder von erben können, um Ihre eigenen Projekttypen zu implementieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b425962ed0f664b8255b6489ac8f0d38be7c13c
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487542"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Verwenden des Managed Package Framework zum Implementieren eines Projekttyps (C#)
Das Managed Package Framework (MPF) stellt c#-Klassen bereit, die Sie verwenden oder von erben können, um Ihre eigenen Projekttypen zu implementieren. Das MPF implementiert viele der Schnittstellen, die Visual Studio für einen Projekttyp erwartet, sodass Sie sich auf die Implementierung der Einzelheiten Ihres Projekt Typs konzentrieren können.

## <a name="using-the-mpf-project-source-code"></a>Verwenden des MPF-Projekt Quellcodes
 Das Managed Package Framework for Projects (mpfproj) stellt Hilfsklassen zum Erstellen und Verwalten eines neuen Projekt Systems bereit. Im Gegensatz zu anderen Klassen im MPF sind die Projektklassen nicht in den Assemblys enthalten, die im Lieferumfang von Visual Studio enthalten sind. Stattdessen werden die Projektklassen als Quellcode bei [MPF für Projekte 2013](https://github.com/tunnelvisionlabs/MPFProj10)bereitgestellt.

 Gehen Sie folgendermaßen vor, um dieses Projekt der VSPackage-Projekt Mappe hinzuzufügen:

1. Laden Sie die mpfproj-Dateien in " *mpfprojectdir*" herunter.

2. Ändern Sie in der Datei " *mpfprojectdir*\dev10\src\csharp\projectbase.File" den folgenden Block:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Erstellen Sie ein VSPackage-Projekt.

2. Entladen Sie das VSPackage-Projekt.

3. Bearbeiten Sie die Datei "VSPackage. csproj", indem Sie den folgenden Block vor den anderen Blöcken hinzufügen `<Import>` :

```
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />
  <PropertyGroup>
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.
    <TargetRegistryRoot></TargetRegistryRoot>-->
    <RegisterOutputPackage>true</RegisterOutputPackage>
    <RegisterWithCodebase>true</RegisterWithCodebase>
  </PropertyGroup>
```

1. Speichern Sie das Projekt.

2. Schließen und öffnen Sie die VSPackage-Projekt Mappe erneut.

3. Öffnen Sie das VSPackage-Projekt erneut. Ein neues Verzeichnis mit dem Namen projectbase sollte angezeigt werden.

4. Fügen Sie dem VSPackage-Projekt den folgenden Verweis hinzu:

     Microsoft. Build. Tasks. 4.0

5. Erstellen Sie das Projekt.

## <a name="hierarchy-classes"></a>Hierarchie Klassen
 In der folgenden Tabelle werden die Klassen in der "mpfproj" zusammengefasst, die Projekt Hierarchien unterstützen. Weitere Informationen finden Sie unter [Hierarchien und Auswahl](../../extensibility/internals/hierarchies-and-selection.md).

|Klassenname|
|----------------|
|`Microsoft.VisualStudio.Package.HierarchyNode`|
|`Microsoft.VisualStudio.Package.ProjectNode`|
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|
|`Microsoft.VisualStudio.Package.FileNode`|
|`Microsoft.VisualStudio.Package.FolderNode`|
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|
|`Microsoft.VisualStudio.Package.ReferenceNode`|
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|
|`Microsoft.VisualStudio.Package.ComReferenceNode`|
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|
|`Microsoft.VisualStudio.Package.BuildDependency`|

## <a name="document-handling-classes"></a>Document-Handling-Klassen
 In der folgenden Tabelle werden die-Klassen im MPF aufgelistet, die die Verarbeitung von Dokumenten unterstützen. Weitere Informationen finden Sie unter [Öffnen und Speichern von Projekt Elementen](../../extensibility/internals/opening-and-saving-project-items.md).

|Klassenname|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Konfigurations-und Ausgabe Klassen
 In der folgenden Tabelle sind die-Klassen im MPF aufgeführt, mit denen Projekttypen mehrere Konfigurationen unterstützen können, wie z. b. Debug und Release, und Auflistungen der Projekt Ausgabe. Weitere Informationen finden Sie unter [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md).

|Klassenname|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Automation-Support-Klassen
 In der folgenden Tabelle werden die-Klassen im MPF aufgelistet, die Automation unterstützen, sodass Benutzer Ihres Projekt Typs Add-Ins schreiben können.

|Klassenname|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Eigenschaften Klassen
 In der folgenden Tabelle werden die Klassen im MPF aufgelistet, mit denen Projekttypen Eigenschaften hinzufügen können, die Benutzer in einem Eigenschaften Browser durchsuchen und ändern können.

|Klassenname|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
