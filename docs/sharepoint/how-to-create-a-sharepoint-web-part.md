---
title: 'Vorgehensweise: Erstellen eines SharePoint-Webparts | Microsoft-Dokumentation'
description: Erstellen und Anpassen eines Webparts mithilfe eines Designers oder durch Hinzufügen eines Webpartelements zu einem SharePoint-Projekt und anschließendes Bearbeiten der Codedatei für das Webpart.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 13039520299d52e6f6a704567cf1cdc5ccfd66db
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903701"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>How to: Erstellen eines SharePoint-Webparts
  Sie können ein Webpart erstellen und anpassen, indem Sie einem SharePoint-Projekt ein **Webpartelement** hinzufügen und dann die Codedatei für das Webpart oder mithilfe eines Designers bearbeiten. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen eines SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

### <a name="to-create-a-sharepoint-web-part"></a>So erstellen Sie ein SharePoint-Webpart

1. Erstellen oder öffnen Sie ein SharePoint-Projekt.

     Weitere Informationen finden Sie unter [SharePoint-Projekt-und Projekt Element Vorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Wählen Sie in **Projektmappen-Explorer** den SharePoint-Projekt Knoten aus, und wählen Sie dann **Projekt**  >  **Neues Element hinzufügen** aus.

3. Erweitern Sie im Dialogfeld **Neues Element hinzufügen** den Knoten **SharePoint** , und wählen Sie dann den Knoten **2010** aus.

4. Wählen Sie in der Liste der SharePoint-Vorlagen **Webpart** aus.

5. Geben Sie im Feld **Name** einen Namen für das Webpart an, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     Das Webpart wird in **Projektmappen-Explorer** angezeigt. Weitere Informationen zu den Dateien, die ein Webpart enthält, finden Sie unter [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

6. Öffnen Sie in **Projektmappen-Explorer** die Codedatei für das Webpart, das Sie soeben erstellt haben.

     Wenn der Name des Webparts z. b. *WebPart1* lautet, öffnen Sie *WebPart1. vb* (in Visual Basic) oder *WebPart1.cs* (in c#).

7. Fügen Sie in der Codedatei der <xref:System.Web.UI.Control.CreateChildControls%2A>-Methode Steuerelemente hinzu.

     Ein Beispiel finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Webparts für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).

## <a name="see-also"></a>Weitere Informationen
- [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [How to: Erstellen eines SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint mithilfe eines Designers](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
