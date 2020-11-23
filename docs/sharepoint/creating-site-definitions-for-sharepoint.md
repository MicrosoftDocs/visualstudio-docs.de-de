---
title: Erstellen von Websitedefinitionen für SharePoint | Microsoft-Dokumentation
description: Erstellen Sie Websitedefinitionen für SharePoint. Websitedefinitionen bestimmen nicht nur die Darstellung und das Verhalten der SharePoint-Website, sondern auch Standardinhalte und -funktionen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7585a4b80322afb37e816758fc7074806a443676
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850571"
---
# <a name="create-site-definitions-for-sharepoint"></a>Erstellen von Websitedefinitionen für SharePoint
  Mit dem SharePoint-Projekt für eine Websitedefinition in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] können Sie eine *Websitedefinition* erstellen, die als Grundlage für eine neue SharePoint-Website dient. Diese Definitionen bestimmen nicht nur die Darstellung und das Verhalten der SharePoint-Website, sondern auch die Standardinhalte und -funktionen. In der Definition können Sie vorkonfigurierte Listen, Inhaltstypen, Ereignisempfänger, Images und andere Elemente platzieren. SharePoint enthält einige Websitedefinitionen wie beispielsweise BLOG. Wenn Sie eine Website basierend auf der BLOG-Websitedefinition erstellen, enthält die Website die Listen, Webparts und andere Elemente, die für eine Blogwebsite erforderlich sind.

 Weitere Informationen zu Websitedefinitionen finden Sie unter [Websitetypen: WebTemplates und Websitedefinitionen](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14)).

## <a name="site-definition-projects"></a>Websitedefinitionsprojekte
 Websitedefinitionsprojekte in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bieten nur die für eine SharePoint-Website benötigten grundlegenden Dateien und keine Standardfunktionen. Sie müssen Dateien und Inhalte hinzufügen, um die gewünschte Funktionalität bereitstellen zu können. Sie können die Website manuell erstellen, indem Sie die benötigten Dateien erstellen und hinzufügen.

## <a name="feature-stapling"></a>Funktionsanheftung
 Ein Vorteil beim Erstellen von Websitedefinitionen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] besteht darin, dass automatisch die *Funktionsanheftung* verwendet wird. Bei der Funktionsanheftung wird eine Funktion an eine Websitedefinition angefügt, anstatt die Funktionalität in die Websitedefinition selbst einzubetten. Auf diese Weise können Sie die Funktion zu jeder Website hinzufügen, die mithilfe der Websitedefinition erstellt wurde, ohne die ursprüngliche Websitedefinition zu ändern. Weitere Informationen finden Sie unter [Funktionsanheftung](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12)).

## <a name="site-definition-project-components"></a>Komponenten des Websitedefinitionsprojekts
 Wenn Sie eine Websitedefinitionslösung erstellen, werden die folgenden Standarddateien zum Knoten **SiteDefinition** hinzugefügt.

|Dateiname|Beschreibung|
|---------------|-----------------|
|*default.aspx*|Dies ist die ASPX-Standardhomepage für die neue SharePoint-Website.|
|*onet.xml*|Hiermit werden die Konfiguration der neuen Website, die Komponenten der Websitedefinitionsvorlage und das Standardverhalten angegeben. Diese Einstellungen können Attribute wie beispielsweise aktivierte Inhaltstypen, die Standardlistenansichten, Dokumentvorlagendateien und Webparts umfassen, die auf der Website enthalten sind. Im Abschnitt `Modules` werden standardmäßig die zur SharePoint-Website hinzuzufügenden Dateien sowie deren Konfiguration aufgelistet.|
|*webtemp_\<SiteDefinitionName>.xml*|Hiermit werden die Websitedefinitionskonfigurationen angegeben, die im Abschnitt **Vorlagenauswahl** auf der Seite **Neue SharePoint-Website** angezeigt werden.|

 Alle Websitedefinitionen werden standardmäßig im Ordner *\<drive:>\Programme\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* gespeichert. Jede Websitedefinition hat ihren eigenen Unterordner.

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Exemplarische Vorgehensweise: Erstellen eines einfachen Projekts für eine Websitedefinition](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Hier wird die Erstellung eines einfachen Websitedefinitionsprojekts in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ausführlich erläutert.|
|[How to: Erstellen einer benutzerdefinierten Websitedefinition und -konfiguration](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|Hier wird beschrieben, wie Sie eine benutzerdefinierte Websitedefinition in SharePoint erstellen, indem Sie eine vorhandene Websitedefinition kopieren und dann ändern.|
|[*WebTemp.xml*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|In diesem Artikel wird die ursprüngliche Datei beschrieben, die die Websitedefinitionen angibt, die im Abschnitt **Vorlagenauswahl** der Seite **Neue SharePoint-Website** verfügbar sind.|
|[Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md)|Hier wird beschrieben, wie Sie Ihre SharePoint-Lösungen für die globale Verwendung vorbereiten.|
|[Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|In diesem Artikel wird beschrieben, wie Sie Teile einer SharePoint-Website erstellen, die von Benutzern geändert werden können.|
|[Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Hier wird beschrieben, wie Sie wiederverwendbare Steuerelemente erstellen, die auf Anwendungsseiten und in Webparts ausgeführt werden.|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|Hier wird die Verwendung des Designers erläutert, der angezeigt wird, wenn Sie im Projekt eine Webseite öffnen.|
|[Übersicht über ASP.NET-Webseiten](/previous-versions/aspnet/428509ah(v=vs.100))|Hier werden allgemeine Informationen zur Struktur von [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]-Webseiten, der Verarbeitung von Seiten durch [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] und dem Anzeigen des Markups durch [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] bereitgestellt, das den XHTML-Standards entspricht.|
|[ASP.NET-Webseitensyntax](/previous-versions/aspnet/k33801s3(v=vs.100))|In diesem Artikel werden die Markupelemente beschrieben, aus denen eine ASP.NET-Seite besteht.|
|[Programmieren von ASP.NET-Webseiten](/previous-versions/aspnet/0yt4zca8(v=vs.100))|Hier werden Informationen zum Erstellen von Ereignishandlern auf [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]-Seiten und zum Arbeiten mit Clientskripts bereitgestellt.|
|[Programmieren in Windows SharePoint-Diensten](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|Hier wird erläutert, wie Sie das verwaltete Objektmodell verwenden können, das in [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] bereitgestellt wird.|

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
