---
title: 'Vorgehensweise: Erstellen einer Anwendungsseite | Microsoft-Dokumentation'
description: Erstellen Sie eine ASP.NET-Webseite (auch als Anwendungsseite bezeichnet) in Visual Studio für eine oder mehrere SharePoint-Websites.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 74e7aab4cbc012afbf045672dbf4af248ada4c61
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925621"
---
# <a name="how-to-create-an-application-page"></a>How to: Erstellen einer Anwendungsseite
  Sie können eine ASP.NET-Webseite für eine oder mehrere SharePoint-Websites erstellen. Diese Seiten werden in SharePoint als Anwendungs Seiten bezeichnet. Anders als bei einer Website Seite enthält eine Anwendungsseite Code, der hinter der Seite ausgeführt wird. Weitere Informationen finden Sie unter [Erstellen von Anwendungs Seiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

### <a name="to-create-an-application-page"></a>So erstellen Sie eine Anwendungsseite

1. Öffnen oder erstellen Sie in Visual Studio ein SharePoint-Projekt.

     Weitere Informationen finden Sie unter [SharePoint-Projekt-und Projekt Element Vorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Wählen Sie im **Projektmappen-Explorer** den Projektknoten aus.

3. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

4. Erweitern Sie im Dialogfeld **Neues Element hinzufügen** den Knoten **SharePoint** , und wählen Sie dann das Element **2010** aus.

5. Wählen Sie in der Liste der SharePoint-Vorlagen die Option **Anwendungsseite** aus.

6. Geben Sie im Feld **Name** einen Namen für die Anwendungsseite an, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

     Visual Studio fügt dem Projekt mehrere Ordner und Dateien hinzu. Weitere Informationen zu diesen Dateien finden Sie unter [Erstellen von Anwendungs Seiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

     In der **Quell** Ansicht des Visual Web Developer-Designers wird die ASP.NET-Seiten Datei angezeigt. Sie können die Seite entwerfen, indem Sie Steuerelemente aus der **Toolbox** hinzufügen und Sie auf Platzhalter für Inhalt platzieren. Weitere Informationen finden Sie unter [Quell Ansicht, Webseiten-Designer](/previous-versions/aspnet/ms178154\(v\=vs.100\)).

7. Wenn Sie Steuerungs Ereignisse behandeln möchten, fügen Sie der Codedatei für die Anwendungsseite Code hinzu.

     Die Codedatei wird angezeigt, wenn Sie den Knoten für die ASP.net-Auslagerungs Datei erweitern und abhängig von der Sprache des Projekts eine *CS* -oder *VB* -Erweiterung haben. Ein End-to-End-Beispiel zum Erstellen einer Anwendungsseite finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer SharePoint-Anwendungsseite](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).

## <a name="see-also"></a>Weitere Informationen
- [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
