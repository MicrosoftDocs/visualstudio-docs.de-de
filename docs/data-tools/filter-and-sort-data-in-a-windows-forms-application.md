---
title: Filtern und Sortieren von Daten in einer Windows Forms-Anwendung
description: Filtern und Sortieren von Daten in einer Windows Forms Anwendung. Legen Sie die Eigenschaft Filter auf einen Zeichen folgen Ausdruck fest, der die gewünschten Datensätze zurückgibt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b1708d6871f1acdf437895563d9b5a39dbe93f21
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858851"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtern und Sortieren von Daten in einer Windows Forms-Anwendung

Daten können gefiltert werden, indem die <xref:System.Windows.Forms.BindingSource.Filter%2A>-Eigenschaft auf einen Zeichenfolgenausdruck festlegt wird, der die gewünschten Datensätze zurückgibt.

Sie sortieren die Daten, indem Sie die- <xref:System.Windows.Forms.BindingSource.Sort%2A> Eigenschaft auf den Namen der Spalte festlegen, nach der sortiert werden soll. Fügen Sie die `DESC` Sortierung in absteigender Reihenfolge an, oder fügen Sie eine Sortierung `ASC` in aufsteigender Reihenfolge ein.

> [!NOTE]
> Wenn die Anwendung keine Komponenten verwendet <xref:System.Windows.Forms.BindingSource> , können Sie Daten mithilfe von Objekten Filtern und Sortieren <xref:System.Data.DataView> . Weitere Informationen finden Sie unter ["DataViews"](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>So filtern Sie Daten mithilfe einer BindingSource-Komponente

- Legen Sie die <xref:System.Windows.Forms.BindingSource.Filter%2A>-Eigenschaft auf den zurückzugebenden Ausdruck fest. Im folgenden Code werden beispielsweise Kunden mit einem `CompanyName` zurückgegeben, der mit "B" beginnt:

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>So sortieren Sie Daten mithilfe einer BindingSource-Komponente

- Legen Sie die <xref:System.Windows.Forms.BindingSource.Sort%2A>-Eigenschaft auf die Spalte fest, nach der sortiert werden soll. Im folgenden Code werden beispielsweise Kunden in der Spalte `CompanyName` in absteigender Reihenfolge sortiert:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Weitere Informationen

- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
