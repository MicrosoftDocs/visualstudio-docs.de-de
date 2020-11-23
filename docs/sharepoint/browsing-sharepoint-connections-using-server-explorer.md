---
title: Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer | Microsoft-Dokumentation
description: Durchsuchen Sie SharePoint-Verbindungen mithilfe des Server-Explorers. Hier erfahren Sie mehr über Server-Explorer-Knoten und Befehle für Knotenkontextmenüs.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 79e8d3dbc1dab865b2ab9048cea8d13c478f2a12
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94849830"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer
  Sie können nun lokale SharePoint-Verbindungen im **Server-Explorer** durchsuchen. Mithilfe dieses Verfahrens können Sie die Komponenten einer SharePoint-Website in Ihrem System durchlaufen. Komponenten von SharePoint-Websites wie Listendefinitionen und Inhaltstypen werden in einem Knoten namens **SharePoint-Verbindungen** in der Strukturansicht des **Server-Explorers** angezeigt. Zum Anzeigen des **Server-Explorers** müssen Sie in der Menüleiste auf **Ansicht** > **Server-Explorer** klicken. Neben dem Anzeigen der Komponenten der SharePoint-Website können Sie auch Elemente entfernen, ihre Eigenschaften anzeigen oder die Strukturansicht aktualisieren, indem Sie die Befehle im Kontextmenü verwenden.

> [!IMPORTANT]
> Zum Durchsuchen einer SharePoint-Website müssen Sie ein Administrator der SharePoint-Websitesammlung sein und Visual Studio auf dem lokalen Computer als Administrator ausführen. Andernfalls wird die Website zwar im **Server-Explorer** angezeigt, jedoch können Sie den Knoten nicht erweitern. Öffnen Sie die Website in einem Webbrowser, öffnen Sie das Menü **Websiteaktionen**, klicken Sie auf **Berechtigungen**, und wählen Sie dann auf der Seite **Permissions: Team Site** (Berechtigungen: Teamwebsite) den Befehl **Websitesammlungen-Administratoren** aus der Menübandgruppe **Verwalten** aus, um zu überprüfen, ob Sie ein Administrator der Websitesammlung sind. Ihr Name wird im Textfeld angezeigt, wenn Sie ein Administrator der Websitesammlung sind. Wenn der Befehl **Websitesammlungen-Administratoren** nicht in der Menübandgruppe „Verwalten“ angezeigt wird, sind Sie kein Administrator für die Websitesammlung. In diesem Fall müssen Sie die entsprechenden Berechtigungen vom Websiteadministrator erhalten.

## <a name="server-explorer-nodes"></a>Server-Explorer-Knoten
 Jede Komponente einer SharePoint-Website wird von einem Knoten in der Strukturansicht des **Server-Explorers** unter **SharePoint-Verbindungen** dargestellt. Beispielsweise enthalten SharePoint-Standardwebsites einen Inhaltstyp namens „Discussion“ (Diskussion) der einen Diskussionstyp darstellt, der auf der Seite **Discussions** (Diskussionen) der SharePoint-Website angezeigt wird. Der Inhaltstyp „Discussion“ enthält mehrere Felder. Erweitern Sie den Knoten **ContentTypes** und dann den Knoten **Discussion**, um diese Felder im **Server-Explorer** anzuzeigen. Darunter befinden sich mehrere Feldknoten, z. B. „Body“, „Discussion Subject“ und „Title“ (Text, Diskussionsthema und Titel).

## <a name="node-shortcut-menu-commands"></a>Kontextmenübefehle für Knoten
 Jeder Knoten umfasst ein Kontextmenü, auf das Sie zugreifen können, indem Sie mit der rechten Maustaste auf den Knoten klicken oder indem Sie ihn auswählen und dann **UMSCHALT**+**F10** drücken. Zu den Knotenbefehlen gehören:

|Befehlsname|BESCHREIBUNG|
|------------------|-----------------|
|Aktualisieren|Mit diesem Befehl wird die Strukturansicht aktualisiert, damit alle Änderungen dargestellt werden, die vorgenommen wurden, seitdem der Knoten zuletzt angezeigt wurde.|
|Löschen|Mit diesem Befehl wird der ausgewählte Knoten aus der Strukturansicht entfernt. **Hinweis**:  Dieser Befehl kann nur für SharePoint-Verbindungen verwendet werden, die unter dem Knoten **SharePoint-Verbindungen** aufgeführt werden.|
|Eigenschaften|Mit diesem Befehl werden die verfügbaren Eigenschaften für den ausgewählten Knoten im Fenster **Eigenschaften** angezeigt. Alle Eigenschaften sind schreibgeschützt und nicht jedem Knoten sind Eigenschaften zugeordnet.|
|Verbindung hinzufügen|Mit diesem Befehl können Sie eine SharePoint-Website angeben, die Sie durchsuchen möchten. Dieser Befehl ist für den Knoten **SharePoint-Verbindungen** und untergeordnete Websiteknoten verfügbar.|
|In Browser anzeigen|Mit diesem Befehl wird die ausgewählte Liste im Webbrowser angezeigt. Dieser Befehl ist für einige Listen unter dem Knoten **Listen** verfügbar, der in **Listen und Bibliotheken** enthalten ist.|

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[How to: Add or remove SharePoint connections (Vorgehensweise: Hinzufügen oder Entfernen von SharePoint-Verbindungen)](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|In diesem Artikel werden die erforderlichen Schritte zum Hinzufügen einer neuen SharePoint-Website zum Knoten **SharePoint-Verbindungen** im **Server-Explorer** erläutert.|

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
