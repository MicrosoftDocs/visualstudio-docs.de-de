---
title: Erweitern der Funktionalität eines TableAdapter
description: Weitere Informationen zum Erweitern der Funktionalität eines TableAdapter durch Hinzufügen von Code zur partiellen Klassendatei von TableAdapter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6e1c594ab1f74cddb962cc2a6d4030ede1e53c8f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435077"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Erweitern der Funktionalität eines TableAdapter

Sie können die Funktionalität eines TableAdapters erweitern, indem Sie der partiellen Klassendatei von TableAdapter Code hinzufügen.

Der Code, der einen TableAdapter definiert, wird erneut generiert, wenn Änderungen am TableAdapter im **DataSet-Designer** vorgenommen werden oder wenn die Konfiguration eines TableAdapters von einem Assistenten geändert wird. Um zu verhindern, dass Ihr Code während der erneuten Generierung eines TableAdapters gelöscht wird, fügen Sie der partiellen Klassendatei von TableAdapter Code hinzu.

Partielle Klassen erlauben, dass Code für eine bestimmte Klasse auf mehrere physische Dateien aufgeteilt wird. Weitere Informationen finden Sie unter [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) oder [Partial (Type)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Suchen von TableAdapters im Code

Obwohl TableAdapters mit dem **DataSet-Designer** entworfen wurden, sind die generierten TableAdapter-Klassen keine geschposteten Klassen von <xref:System.Data.DataSet> . TableAdapters befinden sich in einem Namespace, der auf dem Namen des zugeordneten Datasets des TableAdapter basiert. Wenn die Anwendung z. b. ein DataSet `HRDataSet` mit dem Namen enthält, befinden sich die TableAdapters im- `HRDataSetTableAdapters` Namespace. (Die Benennungs Konvention folgt diesem Muster: *DataSetName*  +  `TableAdapters` ).

Im folgenden Beispiel wird angenommen, dass sich ein TableAdapter namens `CustomersTableAdapter` in einem Projekt mit dem Namen befindet `NorthwindDataSet` .

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>So erstellen Sie eine partielle Klasse für einen TableAdapter

1. Fügen Sie dem Projekt eine neue Klasse hinzu, indem Sie im Menü **Projekt** auf **Klasse hinzufügen** klicken.

2. Geben Sie der Klassen den Namen `CustomersTableAdapterExtended`.

3. Wählen Sie **Hinzufügen**.

4. Ersetzen Sie den Code durch den korrekten Namespace und den Namen der partiellen Klasse für Ihr Projekt wie folgt:

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>Siehe auch

- [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
