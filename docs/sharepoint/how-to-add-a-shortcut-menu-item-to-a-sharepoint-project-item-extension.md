---
title: Kontextmenü Element zur SharePoint-Projekt Element Erweiterung hinzufügen
titleSuffix: ''
description: Fügen Sie einem vorhandenen SharePoint-Projekt Element ein Kontextmenü Element hinzu, indem Sie in Visual Studio eine Projekt Element Erweiterung verwenden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: eba366ecf777697a0c63999d8addf099fecca976
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923613"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>Gewusst wie: Hinzufügen eines Kontextmenü Elements zu einer SharePoint-Projekt Element Erweiterung
  Sie können einem vorhandenen SharePoint-Projekt Element ein Kontextmenü Element hinzufügen, indem Sie eine Projekt Element Erweiterung verwenden. Das Menü Element wird angezeigt, wenn ein Benutzer mit der rechten Maustaste auf das Projekt Element in **Projektmappen-Explorer** klickt.

 Bei den folgenden Schritten wird davon ausgegangen, dass Sie bereits eine Projekt Element Erweiterung erstellt haben. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>So fügen Sie ein Kontextmenü Element in einer Projekt Element Erweiterung hinzu

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> Behandeln Sie das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> Ereignis des *projectItemType* -Parameters in der-Methode Ihrer Implementierung.

2. Fügen Sie im Ereignishandler für das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> Ereignis der- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> oder-Auflistung <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> des Ereignis Argument-Parameters ein neues-Objekt hinzu.

3. <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>Führen Sie im Ereignishandler für das neue- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> Objekt die Tasks aus, die Sie ausführen möchten, wenn ein Benutzer auf das Kontextmenü Element klickt.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie dem Ereignis Empfänger-Projekt Element ein Kontextmenü Element hinzugefügt wird. Wenn der Benutzer in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt Element klickt und auf das Menü Element **Ausgabefenster Nachricht schreiben** klickt, zeigt Visual Studio eine Meldung im **Ausgabe** Fenster an.

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]

 In diesem Beispiel wird der SharePoint-Projekt Dienst verwendet, um die Nachricht in das **Ausgabe** Fenster zu schreiben. Weitere Informationen finden Sie unter [Verwenden des SharePoint-Projekt Dienstanbieter](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert ein Klassen Bibliotheksprojekt, das Verweise auf die folgenden Assemblys enthält:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sie ein Erweiterungspaket (VSIX) für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter Bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Erstellen einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Gewusst wie: Hinzufügen einer Eigenschaft zu einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Erweitern von SharePoint-Projekt Elementen](../sharepoint/extending-sharepoint-project-items.md)
- [Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projekt Elementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
