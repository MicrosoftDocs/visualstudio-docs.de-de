---
title: 'Vorgehensweise: Erstellen eines SharePoint-Webparts mithilfe eines Designers | Microsoft-Dokumentation'
titleSuffix: ''
description: Erstellen Sie ein Webpart, indem Sie einem SharePoint-Projekt ein visuelles Webpart-Element hinzufügen, das den Visual Web Developer-Designer in Visual Studio öffnet.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 09b237704a5b42f75c2239bd6d159e3d58e3025e
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903714"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Vorgehensweise: Erstellen eines SharePoint-Webparts mithilfe eines Designers
  Sie können ein Webpart erstellen, indem Sie einem SharePoint-Projekt ein Element für ein **visuelles Webpart** hinzufügen. Dadurch wird der Visual Web Developer-Designer in Visual Studio geöffnet, in dem Sie Steuerelemente und Code zum Webpart hinzufügen können. Visuelle Webparts funktionieren genauso wie Webparts. Der einzige Unterschied ist, dass Sie visuelle Webparts im Visual Web Developer-Designer entwerfen.

### <a name="to-create-a-project-for-visual-web-parts"></a>So erstellen Sie ein Projekt für visuelle Webparts

1. Klicken Sie in der Menüleiste auf **Datei** >**Neu** > **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Erweitern Sie im Dialogfeld **Neues Projekt** unter **Visual c#** oder **Visual Basic** den Knoten **Office/SharePoint** , und wählen Sie dann die Kategorie **SharePoint-Lösungen** aus.

3. Wählen Sie in der Liste der Projektvorlagen die Option **SharePoint 2013-visuelles Webpart** aus, und klicken Sie dann auf die Schaltfläche **OK** .

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt.

4. Geben Sie auf der Seite **Standort und Sicherheitsebene für Debugging angeben** die URL einer SharePoint-Website an, die sich auf dem lokalen Computer befindet, und klicken Sie dann auf die Schaltfläche **Fertig** stellen.

     In **Projektmappen-Explorer** wird ein Webpart angezeigt. Nachdem Sie das Webpart im Visual Web Developer-Designer entworfen haben, testen Sie es auf der Site, die Sie angeben.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>So fügen Sie einem vorhandenen SharePoint-Projekt ein visuelles Webpart hinzu

1. Wählen Sie in der Menüleiste **Projekt**  >  **Neues Element hinzufügen** aus.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** den Knoten **Office/SharePoint** aus.

3. Wählen Sie in der Liste der Projektvorlagen die Option **visuelles Webpart** aus, benennen Sie Sie, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     In **Projektmappen-Explorer** wird Ihr Webpart angezeigt. Nachdem Sie das Webpart im Visual Web Developer-Designer entworfen haben, testen Sie es auf der Site, die Sie angeben.

## <a name="see-also"></a>Weitere Informationen
- [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [How to: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint mithilfe eines Designers](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
