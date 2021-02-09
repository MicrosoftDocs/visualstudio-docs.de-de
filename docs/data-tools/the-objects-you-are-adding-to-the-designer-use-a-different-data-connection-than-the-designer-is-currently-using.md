---
title: Objekte verwenden eine andere Verbindung
description: Die dem Designer hinzugefügten Objekte verwenden eine andere Datenverbindung als der Designer. Informationen zu dieser Visual Studio O/R-Designer-Meldung anzeigen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 22f982449ceb1d0ec5a6d960380d76dc11f66b09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858357"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Die dem Designer hinzugefügten Objekte verwenden eine andere Datenverbindung als der Designer.

Die dem Designer hinzugefügten Objekte verwenden eine andere Datenverbindung als die derzeit vom Designer verwendete. Soll die vom Designer verwendete Verbindung ersetzt werden?

Wenn Sie dem **objektrelationaler Designer** (**O/R-Designer**) Elemente hinzufügen, verwenden alle Elemente eine freigegebene Datenverbindung. (Die Entwurfs Oberfläche stellt das dar <xref:System.Data.Linq.DataContext> , das eine einzelne Verbindung für alle-Objekte auf der-Oberfläche verwendet.) Wenn Sie dem Designer ein Objekt hinzufügen, das eine Datenverbindung verwendet, die von der derzeit vom Designer verwendeten Datenverbindung abweicht, wird diese Meldung angezeigt. Zur Behebung dieses Fehlers können Sie auswählen, dass die vorhandene Verbindung beibehalten werden soll. Wenn Sie diese Auswahl treffen, wird das ausgewählte Objekt nicht hinzugefügt. Sie können auch auswählen, dass das Objekt hinzugefügt und die <xref:System.Data.Linq.DataContext>-Verbindung auf die neue Verbindung festgelegt wird.

## <a name="connection-options"></a>Verbindungsoptionen

- Um die vorhandene Verbindung durch die Verbindung zu ersetzen, die vom ausgewählten Objekt verwendet wird, klicken Sie auf **Ja**.

   Das ausgewählte Objekt wird dem **O/R-Designer** hinzugefügt, und die *DataContext. Connection* wird auf die neue Verbindung festgelegt.

   > [!NOTE]
   > Wenn Sie auf **Ja** klicken, werden alle Entitäts Klassen im **O/R-Designer** der neuen Verbindung zugeordnet.

- Um die vorhandene Verbindung weiterhin zu verwenden und das Hinzufügen des ausgewählten Objekts abzubrechen, klicken Sie auf **Nein**.

   Die Aktion wird abgebrochen. Die *DataContext. Connection* bleibt auf die vorhandene Verbindung festgelegt.

## <a name="see-also"></a>Weitere Informationen

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
