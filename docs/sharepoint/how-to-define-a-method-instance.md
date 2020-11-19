---
title: 'Vorgehensweise: Definieren einer Methoden Instanz | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie eine Methoden Instanz für eine Methode in Ihrem Business Data Connectivity-Modell (BDC) definieren.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 751683873d98e6c7aedc7228e0a91fb59117993b
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903623"
---
# <a name="how-to-define-a-method-instance"></a>Gewusst wie: Definieren einer Methoden Instanz
  Sie müssen mindestens eine Methoden Instanz für jede Methode im Modell definieren.

 Fügen Sie mithilfe des Fensters **BDC-Methoden Details** eine Methoden Instanz hinzu. Wenn Sie die-Methoden Instanz hinzufügen, fügt Visual Studio dem XML-Code der `<MethodInstance>` Modelldatei in Ihrem Projekt ein-Element hinzu. Weitere Informationen zu den Attributen eines- `<MethodInstance>` Elements finden Sie unter [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

### <a name="to-define-a-method-instance"></a>So definieren Sie eine Methoden Instanz

1. Erweitern Sie im Fenster **BDC-Methoden Details** den Knoten einer Methode, und erweitern Sie dann den Knoten **Instanzen** .

2. Wählen Sie in der Liste **Methoden Instanz hinzufügen** die Option **Finder-Instanz erstellen** aus.

     Unterhalb des Knotens **Instanzen** wird eine neue Methoden Instanz angezeigt.

3. Wählen Sie in der Menüleiste **Ansicht**  >  **Eigenschaften Fenster** aus.

4. Legen Sie im **Eigenschaften** Fenster die Eigenschaften der Methoden Instanz fest. Weitere Informationen zu den einzelnen Eigenschaften finden Sie unter [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über die BDC-Modell Entwurfs Tools](../sharepoint/bdc-model-design-tools-overview.md)
- [Gewusst wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Gewusst wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
