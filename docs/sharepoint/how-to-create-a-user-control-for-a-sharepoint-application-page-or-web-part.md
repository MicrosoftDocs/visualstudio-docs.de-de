---
title: Benutzer Steuerelement für SharePoint-App-Seite oder Webpart erstellen
titleSuffix: ''
description: Erstellen Sie benutzerdefinierte Benutzer Steuerelemente, die benutzerdefinierte Funktionen für die SharePoint-Lösung bereitstellen, und verwenden Sie diese Funktionalität auf einem Webpart oder einer Anwendungsseite.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 43386f3ba450058d6aaf8ab180e331d2f303a235
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925580"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>How to: Erstellen eines Benutzersteuerelements für eine SharePoint-Anwendungsseite oder ein SharePoint-Webpart
  Sie können benutzerdefinierte Benutzersteuerelemente erstellen, die benutzerdefinierte Funktionalität für die SharePoint-Lösung bereitstellen, und Sie können diese Funktion im Projekt wiederverwenden. Sie können die Benutzersteuerelemente in einem Webpart oder einer Anwendungsseite verwenden, weitere ASP.NET- und SharePoint-Steuerelemente hinzufügen und Eigenschaften sowie Methoden für das Steuerelement definieren. Weitere Informationen zu Benutzer Steuerelementen finden Sie unter [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungs Seiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) und Benutzer Steuerelemente [und Server Steuerelemente in SharePoint](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/).

### <a name="to-create-a-user-control-for-sharepoint"></a>So erstellen Sie ein Benutzersteuerelement für SharePoint

1. Öffnen oder erstellen Sie in Visual Studio ein SharePoint-Projekt.

     Siehe [SharePoint-Projekt-und Projekt Element Vorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Wählen Sie im **Projektmappen-Explorer** den Projektknoten aus.

3. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

4. Wählen Sie im Bereich **installiert** den Knoten **Office/SharePoint** aus.

5. Wählen Sie in der Liste der SharePoint-Vorlagen die Option **Benutzer Steuerelement (nur Farm Lösung)** aus.

    > [!NOTE]
    > Benutzersteuerelemente funktionieren nur in Farmlösungen.

6. Geben Sie im Feld **Name** einen Namen für das Benutzer Steuerelement an, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     Visual Studio fügt dem Projekt mehrere Ordner und Dateien hinzu. Weitere Informationen zu diesen Dateien finden Sie unter [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungs Seiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

     Standardmäßig wird die Benutzer Steuerelement Datei in der **Quell** Ansicht des Visual Web Developer-Designers angezeigt. In dieser Ansicht können Sie das XML-Markup des Steuerelements bearbeiten. Sie können zur **Entwurfs** Ansicht wechseln, wenn Sie das Steuerelement visuell entwerfen möchten, indem Sie Steuerelemente aus der **Toolbox** ziehen. Siehe [Entwurfs Ansicht, Webseiten-Designer](/previous-versions/aspnet/ms178149\(v\=vs.100\)).

7. Wenn Sie Ereignisse behandeln, die im Steuerelement auftreten, fügen Sie der Codedatei des Benutzersteuerelements Code hinzu.

     Diese Datei wird in **Projektmappen-Explorer** unter der Benutzer Steuerelement Datei angezeigt und hat abhängig von der Sprache des Projekts eine CS-oder *VB* -Erweiterung *.*

## <a name="see-also"></a>Weitere Informationen
- [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
