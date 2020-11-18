---
title: Hinzufügen eines Kontextmenü Elements zu einem benutzerdefinierten SharePoint-Projekt Elementtyp
titleSuffix: ''
description: Erfahren Sie, wie Sie einem benutzerdefinierten SharePoint-Projekt Elementtyp ein Kontextmenü Element hinzufügen. Das Menü Element wird angezeigt, wenn Sie mit der rechten Maustaste auf das Projekt Element in Projektmappen-Explorer klicken.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2916b806c6e149a9c0cbe2495a7edabcfc883e7e
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850077"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Gewusst wie: Hinzufügen eines Kontextmenü Elements zu einem benutzerdefinierten SharePoint-Projekt Elementtyp
  Wenn Sie einen benutzerdefinierten SharePoint-Projekt Elementtyp definieren, können Sie dem Projekt Element ein Kontextmenü Element hinzufügen. Das Menü Element wird angezeigt, wenn ein Benutzer mit der rechten Maustaste auf das Projekt Element in **Projektmappen-Explorer** klickt.

 Bei den folgenden Schritten wird davon ausgegangen, dass Sie bereits einen eigenen SharePoint-Projekt Elementtyp definiert haben. Weitere Informationen finden Sie unter Gewusst [wie: Definieren eines SharePoint-Projekt Elementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>So fügen Sie einem benutzerdefinierten Projekt Elementtyp ein Kontextmenü Element hinzu

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Behandeln Sie das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> Ereignis des *projectItemTypeDefinition* -Parameters in der-Methode Ihrer Implementierung.

2. Fügen Sie im Ereignishandler für das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> Ereignis der- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> oder-Auflistung <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> des Ereignis Argument-Parameters ein neues-Objekt hinzu.

3. <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>Führen Sie im Ereignishandler für das neue- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> Objekt die Tasks aus, die Sie ausführen möchten, wenn ein Benutzer das Kontextmenü Element auswählt.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie einem benutzerdefinierten Projekt Elementtyp ein Kontextmenü Element hinzugefügt wird. Wenn der Benutzer das Kontextmenü aus dem Projekt Element in **Projektmappen-Explorer** öffnet und das Menü Element **Nachricht in Ausgabefenster schreiben** auswählt, zeigt Visual Studio im **Ausgabe** Fenster eine Meldung an.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]

 In diesem Beispiel wird der SharePoint-Projekt Dienst verwendet, um die Nachricht in das **Ausgabe** Fenster zu schreiben. Weitere Informationen finden Sie unter [Verwenden des SharePoint-Projekt Dienstanbieter](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert ein Klassen Bibliotheksprojekt, das Verweise auf die folgenden Assemblys enthält:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Bereitstellen des Projekt Elements
 Um anderen Entwicklern die Verwendung des Projekt Elements zu ermöglichen, erstellen Sie eine Projektvorlage oder eine Projekt Element Vorlage. Weitere Informationen finden Sie unter [Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Erstellen Sie zum Bereitstellen des Projekt Elements ein [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterungspaket (VSIX) für die Assembly, die Vorlage und alle anderen Dateien, die Sie mit dem Projekt Element verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch
- [Gewusst wie: Definieren eines SharePoint-Projekt Elementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Gewusst wie: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projekt Elementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Definieren von benutzerdefinierten SharePoint-Projekt Elementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)
