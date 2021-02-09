---
title: Abfragedatasets
description: Grundlegendes zu Abfrage Datasets. Informationen zur Groß-/Kleinschreibung von Datasets. Suchen einer bestimmten Zeile in einer Datentabelle, suchen nach Zeilen nach Spaltenwerten und Zugreifen auf zugehörige Datensätze.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 4342af681f8e2cc38855bec6041e8b4cd83dcf5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866618"
---
# <a name="query-datasets"></a>Abfragedatasets
Um bestimmte Datensätze in einem DataSet zu suchen, verwenden `FindBy` Sie die-Methode für die Datentabelle, schreiben Sie Ihre eigene foreach-Anweisung, um die Zeilen Auflistung der Tabelle zu durchlaufen, oder verwenden Sie [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

## <a name="dataset-case-sensitivity"></a>Berücksichtigung der Groß-/Kleinschreibung
In einem DataSet wird die Groß-/Kleinschreibung von Tabellen-und Spaltennamen standardmäßig nicht beachtet – d. h., eine Tabelle in einem DataSet mit dem Namen "Customers" kann auch als "Customers" bezeichnet werden. Dies entspricht den Benennungs Konventionen in vielen Datenbanken, einschließlich SQL Server. In SQL Server ist das Standardverhalten, dass die Namen von Datenelementen nicht nur in der Groß-/Kleinschreibung unterschieden werden können.

> [!NOTE]
> Anders als bei Datasets wird bei XML-Dokumenten die Groß-/Kleinschreibung beachtet, sodass bei den in Schemas definierten Namen von Datenelementen die Groß-/Kleinschreibung Beispielsweise ermöglicht das Schema Protokoll dem Schema, eine Tabelle mit dem Namen "Customers" und eine andere Tabelle mit dem Namen "Customers" zu definieren. Dies kann zu Namenskonflikten führen, wenn ein Schema, das Elemente enthält, die sich nur nach Groß-/Kleinschreibung unterscheiden, zum Generieren einer DataSet-Klasse verwendet

Die Berücksichtigung der Groß-/Kleinschreibung kann jedoch ein Faktor für die Interpretation von Daten innerhalb des Datasets sein. Wenn Sie z. b. Daten in einer DataSet-Tabelle filtern, geben die Suchkriterien möglicherweise andere Ergebnisse zurück, je nachdem, ob beim Vergleich die Groß-/Kleinschreibung beachtet wird. Sie können die Berücksichtigung der Groß-/Kleinschreibung beim Filtern, durchsuchen und Sortieren steuern, indem Sie die-Eigenschaft des Datasets festlegen <xref:System.Data.DataSet.CaseSensitive%2A> . Alle Tabellen im Dataset erben standardmäßig den Wert dieser Eigenschaft. (Sie können diese Eigenschaft für jede einzelne Tabelle überschreiben, indem Sie die-Eigenschaft der Tabelle festlegen <xref:System.Data.DataTable.CaseSensitive%2A> .)

## <a name="locate-a-specific-row-in-a-data-table"></a>Suchen einer bestimmten Zeile in einer Datentabelle

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>So suchen Sie eine Zeile in einem typisierten DataSet mit einem Primärschlüssel Wert

- Um eine Zeile zu finden, verwenden Sie die stark typisierte `FindBy` Methode, die den Primärschlüssel der Tabelle verwendet.

     Im folgenden Beispiel `CustomerID` ist die Spalte der Primärschlüssel der `Customers` Tabelle. Dies bedeutet, dass die generierte `FindBy` Methode ist `FindByCustomerID` . Das Beispiel zeigt, wie einer <xref:System.Data.DataRow> Variablen mithilfe der generierten Methode eine bestimmte zugewiesen wird `FindBy` .

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>So suchen Sie eine Zeile in einem nicht typisierten DataSet mit einem Primärschlüssel Wert

- Aufrufen der- <xref:System.Data.DataRowCollection.Find%2A> Methode einer Auflistung <xref:System.Data.DataRowCollection> , wobei der Primärschlüssel als Parameter übergeben wird.

     Im folgenden Beispiel wird gezeigt, wie eine neue Zeile mit `foundRow` dem Namen deklariert und der Rückgabewert der <xref:System.Data.DataRowCollection.Find%2A> Methode zugewiesen wird. Wenn der Primärschlüssel gefunden wird, wird der Inhalt von Spalten Index 1 in einem Meldungs Feld angezeigt.

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>Suchen nach Zeilen nach Spaltenwerten

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>So suchen Sie Zeilen basierend auf den Werten in einer Spalte

- Datentabellen werden mit der- <xref:System.Data.DataTable.Select%2A> Methode erstellt, die <xref:System.Data.DataRow> basierend auf dem an die-Methode weiter gegebenen Ausdruck ein Array von s zurückgibt <xref:System.Data.DataTable.Select%2A> . Weitere Informationen zum Erstellen gültiger Ausdrücke finden Sie im Abschnitt "Ausdrucks Syntax" der Seite zur- <xref:System.Data.DataColumn.Expression%2A> Eigenschaft.

     Im folgenden Beispiel wird gezeigt, wie die- <xref:System.Data.DataTable.Select%2A> Methode von verwendet wird <xref:System.Data.DataTable> , um nach bestimmten Zeilen zu suchen.

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>Zugreifen auf verwandte Datensätze
Wenn Tabellen in einem DataSet verknüpft sind, kann ein- <xref:System.Data.DataRelation> Objekt die zugehörigen Datensätze in einer anderen Tabelle verfügbar machen. Beispielsweise kann ein DataSet, das `Customers` -und-Tabellen enthält, `Orders` verfügbar gemacht werden.

Sie können ein- <xref:System.Data.DataRelation> Objekt verwenden, um verwandte Datensätze zu suchen, indem Sie die- <xref:System.Data.DataRow.GetChildRows%2A> Methode eines <xref:System.Data.DataRow> in der übergeordneten Tabelle aufrufen. Diese Methode gibt ein Array mit verknüpften untergeordneten Datensätzen zurück. Oder Sie können die- <xref:System.Data.DataRow.GetParentRow%2A> Methode eines in der untergeordneten Tabelle aufzurufen <xref:System.Data.DataRow> . Diese Methode gibt ein einzelnes <xref:System.Data.DataRow> aus der übergeordneten Tabelle zurück.

Diese Seite enthält Beispiele für die Verwendung typisierter Datasets. Weitere Informationen zum Navigieren in Beziehungen in nicht typisierten Datasets finden Sie unter [Navigieren in DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).

> [!NOTE]
> Wenn Sie in einer Windows Forms Anwendung arbeiten und die Daten Bindungsfunktionen zum Anzeigen von Daten verwenden, kann das vom Designer generierte Formular ausreichend Funktionalität für Ihre Anwendung bereitstellen. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Informationen hierzu finden Sie unter [Beziehungen in Datasets](relationships-in-datasets.md).

Die folgenden Codebeispiele veranschaulichen, wie Sie in typisierten Datasets nach oben und unten navigieren. In den Codebeispielen werden typisierte <xref:System.Data.DataRow> s ( `NorthwindDataSet.OrdersRow` ) und die generierten FindBy-Methoden "*PrimaryKey* ()" verwendet `FindByCustomerID` , um eine gewünschte Zeile zu suchen und die zugehörigen Datensätze zurückzugeben. Die Beispiele werden nur dann ordnungsgemäß kompiliert und ausgeführt, wenn Folgendes vorhanden ist:

- Eine Instanz eines Datasets `NorthwindDataSet` mit dem Namen mit einer `Customers` Tabelle.

- Eine- `Orders` Tabelle.

- Eine Beziehung namens, `FK_Orders_Customers` die die beiden Tabellen in Beziehung gesetzt.

Außerdem müssen beide Tabellen mit Daten aufgefüllt werden, damit alle Datensätze zurückgegeben werden können.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>So geben Sie die untergeordneten Datensätze eines ausgewählten übergeordneten Datensatzes zurück

- Ruft die <xref:System.Data.DataRow.GetChildRows%2A> -Methode einer bestimmten `Customers` Daten Zeile auf und gibt ein Array von Zeilen aus der- `Orders` Tabelle zurück:

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>So geben Sie den übergeordneten Datensatz eines ausgewählten untergeordneten Datensatzes zurück

- Ruft die <xref:System.Data.DataRow.GetParentRow%2A> -Methode einer bestimmten `Orders` Daten Zeile auf und gibt eine einzelne Zeile aus der- `Customers` Tabelle zurück:

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Weitere Informationen

- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
