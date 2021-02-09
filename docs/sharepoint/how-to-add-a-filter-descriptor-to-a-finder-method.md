---
title: 'Gewusst wie: Hinzufügen eines Filter Deskriptors zu einer Finder-Methode | Microsoft-Dokumentation'
description: Informationen zum Hinzufügen eines Filter Deskriptors zu einer Finder-Methode mithilfe des Fensters "BDC-Methoden Details" in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4fe2da1bc6aefefb92fbd6f7d11613372b8b7742
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879695"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Gewusst wie: Hinzufügen eines Filter Deskriptors zu einer Finder-Methode
  Filter Deskriptoren ermöglichen es Consumern des Modells, Werte vor der Ausführung an Methoden zu übergeben. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

 Ein häufiges Szenario besteht darin, dass Benutzer in SharePoint Instanzen eines externen Inhaltstyps abrufen möchten, die bestimmten Kriterien entsprechen. Sie können dieses Szenario durch Hinzufügen eines Filter Deskriptors zu einer Finder-Methode unterstützen.

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>So fügen Sie einer Finder-Methode einen Filter Deskriptor hinzu

1. Erweitern Sie im Fenster **BDC-Methoden Details** den Knoten einer Finder-Methode, erweitern Sie den Knoten **Parameter** , und fügen Sie dann einen Eingabeparameter hinzu. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md).

2. Wählen Sie im Fenster **Methoden Details** den Typdeskriptor des Parameters aus.

3. Wählen Sie in der Menüleiste **Ansicht**  >  **Eigenschaften Fenster** aus.

4. Legen Sie im Fenster **Eigenschaften** die Eigenschaft **Typname** auf einen Datentyp fest, der für den Filter geeignet ist.

     Ein Filter kann z. b. ein Bestelldatum verwenden, um die Anzahl der von der-Methode zurückgegebenen Verkaufsaufträge einzuschränken. Zur Unterstützung dieses Filters muss die **Typname** -Eigenschaft des Typdeskriptors auf **System. DateTime** festgelegt werden.

5. Erweitern Sie im Fenster **Methoden Details** den Knoten **Filter Deskriptoren** .

6. Wählen Sie in der Liste **Filter Deskriptor hinzufügen** die Option **Filter Deskriptor erstellen** aus.

     Unterhalb des Knotens **Filter Deskriptoren** wird ein neuer Filter Deskriptor angezeigt.

7. Wählen Sie in der Menüleiste **Ansicht**  >  **Eigenschaften Fenster** aus.

8. Wählen Sie im Fenster **Eigenschaften** die Eigenschaft **Typ** aus.

9. Wählen Sie in der Liste, die für die **Type** -Eigenschaft angezeigt wird, das gewünschte Filter Muster aus.

     Wenn Sie z. b. einen Filter erstellen möchten, der ein Bestelldatum verwendet, um die Anzahl der in einer Finder-Methode zurückgegebenen Verkaufsaufträge einzuschränken, wählen Sie **vergleichen** aus. Ein Vergleichs Filter stellt sicher, dass eine Finder-Methode nur Instanzen zurückgibt, die eine bestimmte Bedingung erfüllen. Weitere Informationen zu den einzelnen Filter Mustern finden Sie [unter vom BDC unterstützte Filtertypen](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14)).

10. Wählen Sie im Fenster **Eigenschaften** die Eigenschaft zugeordnete **Typdeskriptoren** aus.

11. Wählen Sie in der Liste, die für die **zugehörige Eigenschaft Typdeskriptoren** angezeigt wird, den Typdeskriptor aus, den Sie zuvor in dieser Prozedur erstellt haben. Dies verknüpft den Filter mit dem Eingabeparameter der Finder-Methode.

12. Fügen Sie der Finder-Methode, die Daten zurückgibt, Code hinzu. Sie können den Eingabeparameter als Bedingung in einer SELECT-Abfrage verwenden.

     Im folgenden Beispiel werden Verkaufsaufträge zurückgegeben, die das angegebene Bestelldatum aufweisen.

    > [!NOTE]
    > Ersetzen Sie den Wert des `ServerName` Felds durch den Namen des Servers.

     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)
- [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Gewusst wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
