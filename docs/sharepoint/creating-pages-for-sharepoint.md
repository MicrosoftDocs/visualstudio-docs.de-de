---
title: Erstellen von Seiten für SharePoint | Microsoft-Dokumentation
description: Erstellen Sie mithilfe einer Vorlage in Visual Studio Anwendungsseiten für SharePoint. Erstellen Sie mithilfe des SharePoint-Designers Websiteseiten, Masterseiten und Seitenlayouts.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 974ddb3c68d0c2ef297c884e75300a8507f436cc
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850623"
---
# <a name="create-pages-for-sharepoint"></a>Erstellen von Seiten für SharePoint
  Sie können Anwendungsseiten, Websiteseiten, Masterseiten und Seitenlayouts für eine SharePoint-Website erstellen.

 Sie haben die Möglichkeit, mithilfe einer Vorlage in Visual Studio Anwendungsseiten zu erstellen. Erstellen Sie mithilfe des SharePoint-Designers Websiteseiten, Masterseiten und Seitenlayouts. Anschließend können Sie diese Seiten in Visual Studio importieren, um sie in einem SharePoint-Projekt zu verwenden.

 Mithilfe von Cascading Stylesheets, ECMAScript und Designs können Sie auch die Darstellung und das Verhalten von Seiten ändern.

## <a name="types-of-sharepoint-pages"></a>Typen von SharePoint-Seiten
 In der folgenden Tabelle werden die vier Haupttypen von Seiten beschrieben, die eine SharePoint-Website enthält.

|Seitentyp|BESCHREIBUNG|
|---------------|-----------------|
|Anwendungsseiten|Erstellen Sie eine Anwendungsseite, wenn die Seite benutzerdefinierten Code enthalten oder für mehrere Websites freigegeben werden soll. Andernfalls ist eine Websiteseite möglicherweise die beste Wahl.|
|Websiteseite|Erstellen Sie eine Websiteseite, wenn Sie eine der folgenden Aufgaben ausführen möchten:<br /><br /> – Hinzufügen der Seite zu einer SharePoint-Bibliothek<br />– Aktivieren der Seite, um Hostfeatures wie dynamische Webparts und Webpartzonen zu hosten<br />– Benutzern das Anpassen der Seite mithilfe des SharePoint-Designers ermöglichen<br /><br /> Erstellen Sie keine Websiteseite, wenn die Seite benutzerdefinierten Code enthalten soll. Obwohl Sie benutzerdefinierten Code zu einer Websiteseite hinzufügen können, wird der Code nicht mehr ausgeführt, wenn der Benutzer die Seite mithilfe des SharePoint-Designers anpasst.|
|Masterseiten|Erstellen Sie eine Masterseite, wenn Sie eine gemeinsame Struktur für Websiteseiten und Anwendungsseiten definieren möchten.|
|Seitenlayouts|Seitenlayouts sind für [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] spezifisch und ermöglichen es Ihnen, eine gemeinsame Struktur für Websiteseiten und Anwendungsseiten zu definieren.|

 Eine Übersicht über die einzelnen Seitentypen finden Sie unter [Baustein: Seiten und Benutzeroberfläche](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)) und [Seitenlayouts und Gestaltungsvorlagen](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14)).

## <a name="create-application-pages"></a>Erstellen von Anwendungsseiten
 Sie können Anwendungsseiten in Visual Studio erstellen, indem Sie einem SharePoint-Projekt das Element **Anwendungsseite** hinzufügen. Sie können der Seite Steuerelemente hinzufügen und anschließend Steuerelementereignisse verarbeiten, indem Sie Code hinzufügen.

 Sie können in der Codedatei der Seite Breakpoints festlegen, den Debugger starten und die Seite auf einer lokalen SharePoint-Website testen, ohne zusätzliche Konfigurationsschritte auszuführen. Weitere Informationen finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Erstellen von Websiteseiten, Masterseiten und Seitenlayouts
 Mithilfe des SharePoint-Designers können Sie Websiteseiten, Masterseiten und Seitenlayouts erstellen. Anschließend können Sie diese Seiten in Visual Studio importieren. Importieren Sie Ihre Seiten, wenn Sie die in Visual Studio verfügbaren Funktionen für die Bereitstellung oder die Quellcodeverwaltung nutzen möchten. Weitere Informationen finden Sie unter [Importieren von Elementen von einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Da es schwierig ist, diese Seiten nach dem Import zu ändern, sollten Sie diese Seiten vor dem Importieren entwerfen.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Erstellen von Cascading Stylesheets, ECMAScript und Designs
 Visual Studio stellt keine Vorlagen zum Entwickeln von Cascading Stylesheets (CSS), ECMAScript (JavaScript, JScript) oder Designdateien für SharePoint-Websites bereit. Sie können diese Dateien mithilfe des im SharePoint-SDK verfügbaren Leitfadens oder mit Tools wie dem SharePoint-Designer erstellen.

 Sie können diese Dateien direkt zu Ihrer Projektmappe hinzufügen oder sie importieren. In jedem Fall müssen Sie die entsprechenden zugeordneten Ordner für jedes Element erstellen, das Sie hinzufügen. Weitere Informationen zum Erstellen eines zugeordneten Ordners finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Details zum Erstellen von Cascading Stylesheets finden Sie unter [Verwendung von CSS-Klassen (Cascading Stylesheets) in SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14)). Weitere Informationen zum Erstellen von JavaScript- und JScript-Dateien für eine SharePoint-Projektmappe finden Sie unter [Einrichten einer Anwendungsseite für ECMAScript](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14)). Details zu diesen Designs finden Sie unter [Baustein: Seiten und Benutzeroberfläche](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)).

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Hier wird beschrieben, wie Anwendungsseiten hinzugefügt werden: *ASPX*-Inhalte werden mit einer SharePoint-Masterseite zusammengeführt.|
|[How to: Erstellen einer Anwendungsseite](../sharepoint/how-to-create-an-application-page.md)|Hier wird gezeigt, wie Sie eine ASP.NET-Seite erstellen, die auf einer SharePoint-Website ausgeführt wird.|
|[Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Hier wird erläutert, wie Sie eine ASP.NET-Webseite für eine SharePoint-Website entwerfen und debuggen.|
