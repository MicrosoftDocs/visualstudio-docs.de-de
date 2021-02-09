---
title: Deaktivieren von Einschränkungen beim Auffüllen von Datasets
description: Informationen zum Deaktivieren von Einschränkungen beim Auffüllen eines Datasets. Unterbrechen Sie Update Einschränkungen Programm gesteuert oder mithilfe der DataSet-Designer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 177176250d484787ad90825226a0046fb3e099a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858293"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Deaktivieren von Einschränkungen beim Auffüllen von Datasets

Wenn ein DataSet Einschränkungen enthält (z. b. Foreign Key-Einschränkungen), können Sie Fehler im Zusammenhang mit der Reihenfolge der Vorgänge, die für das DataSet ausgeführt werden, hervorrufen. Beispielsweise kann das Laden von untergeordneten Datensätzen vor dem Laden verknüpfter übergeordneter Datensätze gegen eine Einschränkung verstoßen und einen Fehler verursachen. Sobald Sie einen untergeordneten Datensatz laden, überprüft die Einschränkung das Vorhandensein des übergeordneten Datensatzes und löst einen Fehler aus.

Ohne einen Mechanismus, der die vorübergehende Aufhebung der Einschränkung zulässt, würde der Fehler bei jedem Versuch ausgelöst, einen Datensatz in die untergeordnete Tabelle zu laden. Es besteht außerdem die Möglichkeit, alle Einschränkungen in einem Dataset mit der <xref:System.Data.DataRow.BeginEdit%2A>-Eigenschaft und der <xref:System.Data.DataRow.EndEdit%2A>-Eigenschaft aufzuheben.

> [!NOTE]
> Validierungs Ereignisse (z. b. <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.RowChanging> ) werden nicht ausgelöst, wenn Einschränkungen deaktiviert werden.

## <a name="to-suspend-update-constraints-programmatically"></a>So heben Sie Aktualisierungseinschränkungen programmgesteuert auf

- Im folgenden Beispiel wird veranschaulicht, wie die Einschränkungsüberprüfung in einem Dataset vorübergehend deaktiviert wird:

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>So heben Sie Aktualisierungseinschränkungen mit dem Dataset-Designer auf

1. Öffnen Sie das Dataset im **DataSet-Designer**. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Datasets in der DataSet-Designer](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Legen Sie im Fenster **Eigenschaften** die Eigenschaft <xref:System.Data.DataSet.EnforceConstraints%2A> auf `false`fest.

## <a name="see-also"></a>Weitere Informationen

- [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Beziehungen in DataSets](../data-tools/relationships-in-datasets.md)
