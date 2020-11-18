---
title: 'Gewusst wie: Hinzufügen eines Kontextmenü Elements zu SharePoint-Projekten | Microsoft-Dokumentation'
titleSuffix: ''
description: Fügen Sie einem SharePoint-Projekt in Visual Studio ein Kontextmenü Element hinzu. Das Menü Element wird angezeigt, wenn Sie mit der rechten Maustaste auf einen Projekt Knoten in Projektmappen-Explorer klicken.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 074f5b8a3ed31587b86b172ad2da000b7b81e9c3
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850064"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Gewusst wie: Hinzufügen eines Kontextmenü Elements zu SharePoint-Projekten
  Sie können einem SharePoint-Projekt ein Kontextmenü Element hinzufügen. Das Menü Element wird angezeigt, wenn ein Benutzer mit der rechten Maustaste auf einen Projekt Knoten in **Projektmappen-Explorer** klickt.

 Bei den folgenden Schritten wird davon ausgegangen, dass Sie bereits eine Projekt Erweiterung erstellt haben. Weitere Informationen finden Sie unter Vorgehens [Weise: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>So fügen Sie einem SharePoint-Projekt ein Kontextmenü Element hinzu

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Behandeln Sie das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> Ereignis des *ProjectService* -Parameters in der-Methode Ihrer Implementierung.

2. Fügen Sie im Ereignishandler für das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> Ereignis der- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> oder-Auflistung <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> des Ereignis Argument-Parameters ein neues-Objekt hinzu.

3. <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>Führen Sie im Ereignishandler für das neue- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> Objekt die Tasks aus, die Sie ausführen möchten, wenn ein Benutzer auf das Kontextmenü Element klickt.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie einem SharePoint-Projekt Knoten in **Projektmappen-Explorer** ein Kontextmenü Element hinzugefügt wird. Wenn der Benutzer mit der rechten Maustaste auf einen Projekt Knoten klickt und auf das Menü Element **an Ausgabefenster Nachricht schreiben** klickt, zeigt Visual Studio im **Ausgabe** Fenster eine Meldung an. In diesem Beispiel wird der SharePoint-Projekt Dienst verwendet, um die Meldung anzuzeigen. Weitere Informationen finden Sie unter [Verwenden des SharePoint-Projekt Dienstanbieter](../sharepoint/using-the-sharepoint-project-service.md).

 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert ein Klassen Bibliotheksprojekt, das Verweise auf die folgenden Assemblys enthält:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sie ein Erweiterungspaket (VSIX) für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch
- [Erweitern von SharePoint-Projekten](../sharepoint/extending-sharepoint-projects.md)
- [Vorgehensweise: Erstellen einer SharePoint-Projekt Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Gewusst wie: Hinzufügen einer Eigenschaft zu SharePoint-Projekten](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
