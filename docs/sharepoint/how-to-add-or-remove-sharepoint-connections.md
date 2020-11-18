---
title: 'Vorgehensweise: Hinzufügen oder Entfernen von SharePoint-Verbindungen | Microsoft-Dokumentation'
description: Hinzufügen oder Entfernen von SharePoint-Verbindungen über den Knoten SharePoint-Verbindungen im Fenster Server-Explorer von Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: b898dd0f9327c7589d0dac3436aec0299009221d
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850714"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>How to: Add or remove SharePoint connections (Vorgehensweise: Hinzufügen oder Entfernen von SharePoint-Verbindungen)
  Mit Server-Explorer können Sie SharePoint-Websites und Datenverbindungen durchsuchen. Bevor Sie jedoch den Inhalt einer SharePoint-Website durchsuchen können, müssen Sie Sie dem Knoten **SharePoint-Verbindungen** hinzufügen.

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>So fügen Sie dem Knoten "SharePoint-Verbindungen" eine SharePoint-Website hinzu

1. Wählen Sie in der Menüleiste **Ansicht**, **Server-Explorer** aus.

2. Wählen Sie in **Server-Explorer** den Knoten **SharePoint-Verbindungen** aus, und klicken Sie dann in der Menü **Tools** Leiste auf Extras  >  **SharePoint-Verbindung hinzufügen**.

3. Geben Sie im Feld **SharePoint-Verbindung hinzufügen** den Wert [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] für die SharePoint-Website ein (z http://testserver/sites/unittests) . b..

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>So löschen Sie eine SharePoint-Website aus dem Knoten "SharePoint-Verbindungen"

1. Wählen Sie in der Menüleiste **Ansicht**, **Server-Explorer** aus, um **Server-Explorer** zu öffnen.

2. Erweitern Sie den Knoten **SharePoint-Verbindungen** , um die SharePoint-Website anzuzeigen, die Sie aus **Server-Explorer** löschen möchten.

3. Wählen Sie den Standort aus, und wählen Sie dann in der Menü **Edit** Leiste die Option  >  **Löschen** bearbeiten aus.

    > [!NOTE]
    > Durch diesen Schritt wird die zugrunde liegende Site nicht gelöscht. Es wird nur die Verbindung aus **Server-Explorer** gelöscht.

## <a name="see-also"></a>Siehe auch
- [Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
