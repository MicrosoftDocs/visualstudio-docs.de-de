---
title: Erweitern von SharePoint-Projekt Elementen | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f60c95418379399196c461e055645ae7c85a473e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967395"
---
# <a name="extend-sharepoint-project-items"></a>Erweitern von SharePoint-Projekt Elementen
  Erstellen Sie eine Projekt Element Erweiterung, wenn Sie einer Art von SharePoint-Projekt Element, das bereits in Visual Studio installiert ist, Funktionen hinzufügen möchten. Sie können z. b. eine Erweiterung für die integrierten **Ereignis Empfänger** -oder **Listen Definitions** Projekt Elemente in Visual Studio erstellen, oder Sie können eine Erweiterung für einen benutzerdefinierten Projekt Elementtyp erstellen. Sie können auch eine Erweiterung für alle Typen von SharePoint-Projekt Elementen erstellen.

## <a name="tasks-for-extending-sharepoint-project-items"></a>Aufgaben zum Erweitern von SharePoint-Projekt Elementen
 Um ein Projekt Element zu erweitern, erstellen Sie eine Visual Studio-Erweiterungsassembly, die die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> Schnittstelle implementiert. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

 Wenn Sie ein Projekt Element erweitern, können Sie dem Projekt Element auch die folgenden Funktionen hinzufügen:

- Fügen Sie dem Projekt Element ein Kontextmenü Element hinzu. Das Menü Element wird angezeigt, wenn Sie das Kontextmenü für das Projekt Element in **Projektmappen-Explorer**öffnen. Um das Kontextmenü zu öffnen, klicken Sie mit der rechten Maustaste auf das Projekt Element, oder wählen Sie es aus, und wählen Sie dann die **UMSCHALT** + **Taste F10** . Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Kontextmenü Elements zu einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).

- Fügen Sie dem Projekt Element eine benutzerdefinierte Eigenschaft hinzu. Die-Eigenschaft wird im **Eigenschaften** Fenster angezeigt, wenn Sie das Projekt Element in **Projektmappen-Explorer**auswählen. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen einer Eigenschaft zu einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).

  Eine exemplarische Vorgehensweise, die das Erstellen, bereitstellen und Testen einer Projekt Element Erweiterung veranschaulicht, finden Sie unter Exemplarische Vorgehensweise [: Erweitern eines SharePoint-Projekt Elementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Verstehen der Beziehung zwischen Projekt Element Erweiterungen und Projekt Element Instanzen
 Wenn Sie eine Projekt Element Erweiterung erstellen, lädt Visual Studio die Erweiterung, wenn ein Projekt Element des zugeordneten Typs einem SharePoint-Projekt hinzugefügt wird. Wenn Sie z. b. eine Erweiterung für **Ereignis Empfänger** -Projekt Elemente erstellen, lädt Visual Studio die Erweiterung, wenn ein Benutzer einem Projekt ein **Ereignis Empfänger** -Projekt Element hinzufügt. Visual Studio verwendet die gleiche Instanz Ihrer Erweiterung für alle Instanzen des zugeordneten Projekt Elementtyps. Wenn der Benutzer im vorherigen Beispiel dem Projekt ein zweites **Ereignis Empfänger** -Projekt Element hinzufügt, wird die gleiche Instanz Ihrer Erweiterung zum Anpassen des zweiten Projekt Elements verwendet.

 Um auf eine bestimmte Instanz des Projekt Elementtyps zuzugreifen, den Sie erweitern, behandeln Sie eines der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> Ereignisse des *projectItemType* -Parameters in der Implementierung der- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> Methode. Um z. b. zu ermitteln, ob ein Projekt Element des Typs, den Sie erweitern, einem Projekt hinzugefügt wird, behandeln Sie das- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> Ereignis. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

## <a name="identifiers-for-sharepoint-project-items"></a>Bezeichner für SharePoint-Projekt Elemente
 Jedes SharePoint-Projekt Element verfügt über einen entsprechenden Zeichen folgen Bezeichner. Wenn Sie die folgenden Aufgaben ausführen möchten, müssen Sie den Bezeichner für ein Projekt Element kennen:

- Erstellen Sie eine Erweiterung für das Projekt Element. In diesem Fall müssen Sie den Bezeichner für das Projekt Element, das Sie erweitern möchten, an den Konstruktor von übergeben <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Übergeben Sie den Zeichen folgen Wert "*", um eine Erweiterung für alle Projekt Elementtypen zu erstellen **\\** .

- Fügen Sie das Projekt Element Programm gesteuert zu einem Projekt hinzu. In diesem Fall müssen Sie den-Bezeichner für das Projekt Element an die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> Methode übergeben.

  In der folgenden Tabelle werden die Bezeichner für die SharePoint-Projekt Elemente aufgelistet, die in Visual Studio enthalten sind.

|Projekt Elementname|Zeichen folgen Bezeichner|
|-----------------------|-----------------------|
|Geschäfts Data Catalog Modell|Microsoft. VisualStudio. SharePoint. BusinessDataConnectivity|
|Inhaltstyp|Microsoft. VisualStudio. SharePoint. ContentType|
|Ereignisempfänger|Microsoft. VisualStudio. SharePoint. EventHandler|
|Leeres Element|Microsoft. VisualStudio. SharePoint. genericelements|
|Listen Definition<br /><br /> Listen Definition aus Inhaltstyp|Microsoft. VisualStudio. SharePoint. ListDefinition|
|Listen Instanz|Microsoft. VisualStudio. SharePoint. ListInstance|
|Modul|Microsoft. VisualStudio. SharePoint. Module|
|Sequenzieller Workflow<br /><br /> Zustandsautomat-Workflow|Microsoft. VisualStudio. SharePoint. Workflow|
|Site Definition|Microsoft. VisualStudio. SharePoint. Sitedefinition|
|Visuelles Webpart|Microsoft. VisualStudio. SharePoint. visualwebpart|
|Webpart|Microsoft. VisualStudio. SharePoint. WebPart|
|Workflow Zuordnungs Formular|Microsoft. VisualStudio. SharePoint. Workflow Association|

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Erstellen einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Gewusst wie: Hinzufügen eines Kontextmenü Elements zu einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Gewusst wie: Hinzufügen einer Eigenschaft zu einer SharePoint-Projekt Element Erweiterung](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projekt Elementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [Erweitern des SharePoint-Projekt Systems](../sharepoint/extending-the-sharepoint-project-system.md)
