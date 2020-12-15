---
title: Verwenden von MSBuild | Microsoft-Dokumentation
description: MSBuild liefert ein erweiterbares XML-Format zum Erstellen von Projektdateien, die vollständig zu erstellende Projekt Elemente, Buildaufgaben und Buildkonfigurationen beschreiben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0d5168d739e49ebfc78054ea695f8b73a3e06fbc
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487672"
---
# <a name="using-msbuild"></a>Verwenden von MSBuild
MSBuild bietet ein klar definiertes, erweiterbares XML-Format zum Erstellen von Projektdateien, die die zu erstellenden Projekt Elemente vollständig beschreiben, Buildaufgaben und Buildkonfigurationen.

## <a name="general-msbuild-considerations"></a>Allgemeine Überlegungen zu MSBuild
 MSBuild-Projektdateien, z [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] . b. csproj-und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] VBPROJ-Dateien, enthalten Daten, die zur Buildzeit verwendet werden. Sie können jedoch auch Daten enthalten, die zur Entwurfszeit verwendet werden. Buildzeitdaten werden mithilfe von MSBuild-primitiven gespeichert, einschließlich [Item-Element (MSBuild)](../../msbuild/item-element-msbuild.md) und [Property-Element (MSBuild)](../../msbuild/property-element-msbuild.md). Entwurfszeit Daten, bei denen es sich um Daten handelt, die für den Projekttyp und alle zugehörigen Projekt Untertypen spezifisch sind, werden in frei Form-XML-Code gespeichert.

 MSBuild verfügt nicht über systemeigene Unterstützung für Konfigurationsobjekte, stellt jedoch bedingte Attribute zum Angeben von Konfigurations spezifischen Daten bereit. Beispiel:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Weitere Informationen zu bedingten Attributen finden Sie unter [bedingte Konstrukte](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Erweitern von MSBuild für den Projekttyp
 MSBuild-Schnittstellen und-APIs können in zukünftigen Versionen von geändert werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Daher ist es ratsam, die MPF-Klassen (Managed Package Framework) zu verwenden, da Sie Schutz vor Änderungen bereitstellen.

 Das Managed Package Framework for Projects (mpfproj) stellt Hilfsklassen zum Erstellen und Verwalten eines neuen Projekt Systems bereit. Den Quellcode und die Kompilierungs Anweisungen finden Sie unter [MPF for Projects-Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Die projektspezifischen MPF-Klassen lauten wie folgt:

|Klasse|Implementierung|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement` die Klasse ist ein Wrapper für MSBuild-Elemente.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Einzel Datei-Generatoren im Vergleich zu MSBuild-Aufgaben
 Auf Einzel Datei-Generatoren kann nur zur Entwurfszeit zugegriffen werden, MSBuild-Aufgaben können jedoch zur Entwurfszeit und zur Buildzeit verwendet werden. Verwenden Sie für maximale Flexibilität daher MSBuild-Aufgaben, um Code zu transformieren und zu generieren. Weitere Informationen finden Sie unter [benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Weitere Informationen
- [MSBuild-Referenz](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md)
