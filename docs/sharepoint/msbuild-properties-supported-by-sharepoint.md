---
title: Von SharePoint unterstützte MSBuild-Eigenschaften | Microsoft-Dokumentation
description: Lesen Sie eine Liste der Namen und Beschreibungen von MSBuild-Eigenschaften, die von unterstützt werden und für SharePoint spezifisch sind.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 20458cc7047e913e13f4594380d4b4946b44ec17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938511"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Von SharePoint unterstützte MSBuild-Eigenschaften
  Jede [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Eigenschaft, die in der Datei "Microsoft. VisualStudio. SharePoint. targets", in der Projektdatei oder in der Projekt Benutzerdatei definiert ist, kann in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekten verwendet werden. Zusätzlich zu den allgemeinen [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Eigenschaften, die vom Projekt bereitgestellt werden, definiert SharePoint zusätzliche Eigenschaften, die für SharePoint-Projekte spezifisch sind.

 Eine Liste der allgemeinen [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Eigenschaften finden Sie unter [allgemeine MSBuild-Projekteigenschaften](/previous-versions/dotnet/netframework-4.0/bb629394(v=vs.100)). Eine vollständige Liste der Eigenschaften, die von ihrer Programmiersprache unterstützt werden, finden Sie in der *Targets* -Datei, der Projektdatei (*csproj* -oder *vbproj*-Datei) oder der Projekt Benutzerdatei (*csproj. User* oder *. vbproj. User*).

## <a name="msbuild-properties-specific-to-sharepoint"></a>Für SharePoint spezifische MSBuild-Eigenschaften
 In der folgenden Tabelle werden die [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Eigenschaften aufgelistet, die speziell für SharePoint-Projekte in gelten [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Es sind andere Eigenschaften vorhanden, Sie sind jedoch für die interne Verwendung vorgesehen.

|Eigenschaftenname|BESCHREIBUNG|
|-------------------|-----------------|
|Sharepointsiteurl|Eine Zeichenfolge, die [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] für die SharePoint-Site darstellt.|
|Sandboxedsolution|Ein boolescher Wert, der angibt, ob die Projekt Mappe eine Sandkasten Lösung ist.|
|Activedeploymentconfiguration|Die aktive Bereitstellungs Konfiguration.|
|Includeassemblyinpackage|Ein boolescher Wert, der angibt, ob die Assembly in der Paketdatei enthalten ist.|
|Predeploymentcommand|Ein Zeichen folgen Wert, der den Befehl darstellt, der im Befehls Schritt vor der Bereitstellung ausgeführt werden soll.|
|Postdeploymentcommand|Ein Zeichen folgen Wert, der den Befehl darstellt, der im Befehls Schritt nach der Bereitstellung ausgeführt werden soll.|
|Custombeforesharepointtargets|Eine Zeichenfolge, die den Pfad einer [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Zieldatei darstellt. Wenn die Zieldatei vorhanden und definiert ist, wird Sie vor SharePoint-Daten importiert. Mit dieser Eigenschaft können Sie den Paket Prozess anpassen, indem Sie Paketierungs bezogene Eigenschaften vordefinieren, ohne die bereitgestellte SharePoint-Zieldatei zu ändern, aber die Zieldatei gilt weiterhin für alle SharePoint-Projekte.|
|Customaftersharepointtargets|Eine Zeichenfolge, die den Pfad einer [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Zieldatei darstellt. Wenn die Zieldatei vorhanden und definiert ist, wird Sie nach allen Daten des SharePoint-Targets importiert. Mit dieser Eigenschaft können Sie den Paket Prozess anpassen, indem Sie Paketierungs bezogene Eigenschaften und Ziele überschreiben, ohne die bereitgestelltes SharePoint-Zieldatei ändern zu müssen. die Zieldatei gilt jedoch weiterhin für alle SharePoint-Projekte.|
|LayoutPath|Eine Zeichenfolge, die das Stammverzeichnis darstellt, in dem die einzelnen zu verpackenden Dateien temporär platziert werden, bevor Sie der *wsp* -Datei hinzugefügt werden. Dieser Pfad kann nützlich sein, wenn Sie die Ziele "beforelayout" und "AfterLayout" überschreiben, um zu Paketier Ende Dateien hinzuzufügen, zu entfernen oder zu ändern, da Sie Sie zum Ändern des Inhalts der *wsp* -Datei verwenden können.|
|Basepackagepath|Eine Zeichenfolge, die den Ordner darstellt, in dem das Paket abgelegt wird. Dieser Wert verwendet das Ausgabeverzeichnis des Projekts, z. b. bin\Debug.|
|Packageextension|Eine Zeichenfolge, die die Dateinamenerweiterung darstellt, die an das Paket angehängt werden soll. Der Standardwert ist WSP.|
|Assemblydeploymenttarget|Eine Zeichenfolge, die den Speicherort darstellt, an dem die Projektassembly auf dem SharePoint-Server bereitgestellt wird. Der Wert ist entweder GlobalAssemblyCache (Standard) oder WebApplication. Diese Eigenschaft kann auch in der Eigenschaftenfenster festgelegt werden.|
|Packagewithvalidation|Ein boolescher Wert, der angibt, ob die Validierung vor der Paket Erstellung ausgeführt wird. Mit dieser Eigenschaft können Sie Validierungs Fehler beim Entwickeln von Paketen ignorieren.|
|Validatepackagedependson|Eine Zeichenfolge, die zusätzliche Ziele definiert, die vor dem ValidatePackage-Ziel ausgeführt werden sollen.|
|Token replacementfileexendationen|Eine Zeichenfolge, die die Dateien definiert, deren Token während der Paket Erstellung ersetzt werden.|

## <a name="use-msbuild-properties-in-the-properties-page"></a>Verwenden von MSBuild-Eigenschaften auf der Seite "Eigenschaften"
 Aus Gründen der Flexibilität können Sie anstelle von hart codierten Zeichen folgen in den Befehls **Zeilen Feldern vor der Bereitstellung** und **nach der Bereitstellung** auf der SharePoint-Eigenschaften Seite die SharePoint-Eigenschaften als Argumente verwenden. Anstatt z. b. eine bestimmte [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] Zeichenfolge für die SharePoint-Website anzugeben, können Sie stattdessen verwenden `$(SharePointSiteUrl)` .

> [!NOTE]
> Sie können entweder die [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Variablen Syntax `$(` *propertyName* `)` oder die Syntax `%` *propertyName* der Umgebungsvariablen verwenden `%` , um eine Eigenschaft anzugeben.

## <a name="see-also"></a>Weitere Informationen

- [MSBuild-Referenz](../msbuild/msbuild-reference.md)