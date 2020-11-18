---
title: Übersicht über die BDC-Modell Entwurfs Tools | Microsoft-Dokumentation
description: Lesen Sie eine Übersicht über die Entwurfs Tools, die mit einem Business Data Connectivity (BDC)-Modell verwendet werden können. Erfahren Sie mehr über den BDC-Designer, das BDC-Methoden Detailfenster und den BDC-Explorer.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b6e78b6809d3136c0db1f558d175706dc0ecd75b
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850311"
---
# <a name="bdc-model-design-tools-overview"></a>Übersicht über die BDC-Modell Entwurfs Tools
  Sie können ein BDC-Modell (Business Data Connectivity) mit dem BDC-Designer, dem Fenster der **BDC-Methoden Details** und dem **BDC-Explorer** entwerfen.

 Mit dem **BDC-Explorer** können Sie das Modell durchsuchen, das Modell durchsuchen und Typdeskriptoren definieren.

## <a name="bdc-designer"></a>BDC-Designer
 Mit dem BDC-Designer können Sie die Entitäten im Modell definieren und deren Beziehungen untereinander visuell anordnen. Mit dem BDC-Designer können Sie folgende Aufgaben ausführen:

- Fügen Sie dem Modell Entitäten hinzu.

- Entfernen Sie Entitäten aus dem Modell.

- Definieren von Beziehungen zwischen Entitäten.

  Um den BDC-Designer zu öffnen, doppelklicken Sie auf die Modelldatei in Ihrem Projekt, oder öffnen Sie das Kontextmenü für die Modelldatei, und wählen Sie dann **Öffnen** aus. Fügen Sie dem Modell eine Entität hinzu, indem Sie eine **Entität** aus der **Toolbox** auf den Designer ziehen oder kopieren. Wählen **Sie zum Erstellen** einer Zuordnung zwischen zwei Entitäten das Zuordnungs Steuerelement in der **Toolbox** aus, wählen Sie die erste Entität aus, und wählen Sie dann die zweite Entität aus.

## <a name="bdc-method-details-window"></a>BDC-Methoden Details (Fenster)
 Verwenden Sie das Fenster **Details der BDC-Methode** , um die Parameter, Instanzen und Filter Deskriptoren einer Methode zu definieren.

 Im Fenster " **BDC** -Methoden Details" können Sie schnell Finder-, spezifische Finder-, Ersteller-, Updater-und Deleter-Methoden generieren. Wenn Sie diese Methoden generieren, fügt Visual Studio der Methode Metadaten, z. b. Parameter, Instanzen und Typdeskriptoren, hinzu. Sie können diese Metadaten ändern, um ihr bestimmtes Szenario zu erfüllen.

 Um das Fenster " **Details der BDC-Methode** " zu öffnen, wählen Sie in der Menüleiste **View**  >  **andere Windows**-  >  **BDC-Methoden Details** anzeigen aus.

 Um Methoden im Fenster " **BDC-Methoden Details** " anzuzeigen, wählen Sie die Entität im BDC-Designer aus. Die Methoden der ausgewählten Entität werden im Fenster " **BDC** -Methoden Details" angezeigt. Wenn Sie keine Entität im BDC-Designer auswählen, werden im Fenster " **BDC-Methoden Details** " keine Informationen angezeigt.

 Erweitern oder reduzieren Sie Knoten im Fenster **Details der BDC-Methode** , um Parameter, Instanzen und Filter Deskriptoren zu definieren. Verwenden Sie den **BDC-Explorer** , um Typdeskriptoren zu definieren.

## <a name="bdc-explorer"></a>BDC-Explorer
 Der **BDC-Explorer** zeigt die Elemente an, die das Modell bilden. Um den **BDC-Explorer** zu öffnen, klicken Sie in der **View** Menüleiste auf  >  **anderen Windows**  >  **BDC-Explorer** anzeigen. Um das Modell zu durchsuchen, erweitern Sie die Knoten im **BDC-Explorer**. Jeder Knoten stellt ein Element im XML-Code der Modelldatei dar.

 Wenn Sie Knoten im **BDC-Explorer** auswählen, werden die Eigenschaften der einzelnen Knoten, die Sie auswählen, im **Eigenschaften** Fenster angezeigt. Viele dieser Eigenschaften entsprechen Attributen in der Modelldatei. Sie können das Modell durchsuchen, indem Sie im oberen Bereich des **BDC-Explorers** das Suchfeld verwenden.

> [!NOTE]
> Der **BDC-Explorer** zeigt keine Bezeichner, benutzerdefinierten Eigenschaften, lokalisierten Zeichen folgen, Zuordnungs Gruppen, Aktionen, Filter Deskriptoren, Aktions Steuerungs Listen und die Standardparameter Werte an.

### <a name="define-type-descriptors"></a>Typdeskriptoren definieren
 Verwenden Sie den **BDC-Explorer** , um Typdeskriptoren zu definieren. Mit dem BDC-Explorer können Sie einen Typdeskriptor einmal definieren und diesen Typdeskriptor dann an anderer Stelle im Modell wieder verwenden. Um dies zu erreichen, kopieren Sie einen Typdeskriptor, und fügen Sie ihn in einen beliebigen anderen Parameter oder Typdeskriptor ein.

> [!NOTE]
> Änderungen an einem ursprünglichen Typdeskriptor wirken sich nicht auf die Kopien dieses Typdeskriptors aus.

 Weitere Informationen finden Sie unter Gewusst [wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)
- [Gewusst wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)
- [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)
- [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)
- [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)
- [Erstellen einer Zuordnung zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md)
- [Exemplarische Vorgehensweise: Erstellen einer externen Liste in SharePoint mithilfe von Geschäftsdaten](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
- [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
