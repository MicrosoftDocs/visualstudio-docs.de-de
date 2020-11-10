---
title: Erstellen und Konfigurieren von Datasets
description: Erstellen und Konfigurieren von Datasets in Visual Studio Ein DataSet ist ein Satz von Objekten, die Daten aus einer Datenbank im Arbeitsspeicher speichern und CRUD-Vorgänge für diese Daten unterstützen.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: how-to
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5a9a10d68b5b0617b5c4e2152cbbbb920a7c683f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435403"
---
# <a name="how-to-create-and-configure-datasets-in-visual-studio"></a>Gewusst wie: Erstellen und Konfigurieren von Datasets in Visual Studio

Ein DataSet ist ein Satz von Objekten, die Daten aus einer Datenbank im Arbeitsspeicher speichern und die Änderungs Nachverfolgung unterstützen, um Erstellungs-, Lese-, Aktualisierungs-und Löschvorgänge (CRUD) für diese Daten zu ermöglichen, ohne dass immer eine Verbindung mit der Datenbank hergestellt werden muss. Datasets wurden für einfache *Formulare über Daten* Geschäftsanwendungen entworfen. Bei neuen Anwendungen sollten Sie die Verwendung von Entity Framework zum Speichern und modellieren von Daten im Arbeitsspeicher in Erwägung gezogen. Um mit Datasets arbeiten zu können, sollten Sie über grundlegende Kenntnisse der Datenbankkonzepte verfügen.

<xref:System.Data.DataSet>Mithilfe des **Assistenten zum Konfigurieren von Datenquellen** können Sie zur Entwurfszeit eine typisierte Klasse in Visual Studio erstellen. Informationen zum programmgesteuerten Erstellen von Datasets finden Sie unter [Erstellen eines Datasets (ADO.net)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Erstellen eines neuen Datasets mit dem Assistenten zum Konfigurieren von Datenquellen

1. Öffnen Sie das Projekt in Visual Studio, und wählen Sie dann **Projekt**  >  **neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

2. Wählen Sie den Typ der Datenquelle aus, mit der eine Verbindung hergestellt werden soll.

     ![Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png)

3. Wählen Sie die Datenbank oder Datenbanken aus, die als Datenquelle für das DataSet verwendet werden sollen.

     ![Datenquelle wählen Sie eine Verbindung aus.](../data-tools/media/data-source-choose-a-connection.png)

4. Wählen Sie die Tabellen (oder einzelne Spalten), gespeicherte Prozeduren, Funktionen und Sichten aus der Datenbank aus, die im Dataset dargestellt werden soll.

     ![Datenbankobjekte auswählen](../data-tools/media/raddata-chose-objects.png)

5. Klicken Sie auf **Fertig stellen**.

   Das DataSet wird als Knoten in **Projektmappen-Explorer** angezeigt.

   ![DataSet in Projektmappen-Explorer](../data-tools/media/dataset-in-solution-explorer.png)

6. Klicken Sie in **Projektmappen-Explorer** auf den Knoten DataSet, um das Dataset im **DataSet-Designer** zu öffnen. Jede Tabelle im Dataset verfügt über ein zugeordnetes- `TableAdapter` Objekt, das im unteren Bereich dargestellt wird. Der Tabellen Adapter wird verwendet, um das DataSet zu füllen und optional Befehle an die Datenbank zu senden.

   ![DataSet-Designer](../data-tools/media/dataset-designer.png)

7. Die Beziehungs Linien, die die Tabellen verbinden, stellen Tabellen Beziehungen dar, wie in der Datenbank definiert. Foreign Key-Einschränkungen in einer Datenbank werden standardmäßig nur als Beziehung dargestellt, wobei die Update-und Löschregeln auf None festgelegt sind. Dies ist in der Regel das, was Sie möchten. Sie können jedoch auf die Zeilen klicken, um das **Beziehungs** Dialogfeld aufzurufenden, in dem Sie das Verhalten von hierarchischen Updates ändern können. Weitere Informationen finden Sie unter [Beziehungen in Datasets](../data-tools/relationships-in-datasets.md) und [hierarchische Aktualisierung](../data-tools/hierarchical-update.md).

     ![Dialogfeld "datasetbeziehung"](../data-tools/media/raddata-relation-dialog.png)

8. Klicken Sie in einer Tabelle auf eine Tabelle, einen Tabellen Adapter oder einen Spaltennamen, um die zugehörigen Eigenschaften im **Eigenschaften** Fenster anzuzeigen. Einige der Werte können hier geändert werden. Denken Sie daran, dass Sie das Dataset ändern, nicht die Quelldatenbank.

     ![DataSet-Spalten Eigenschaften](../data-tools/media/dataset-column-properties.png)

9. Sie können dem DataSet neue Tabellen oder Tabellen Adapter hinzufügen oder neue Abfragen für vorhandene Tabellen Adapter hinzufügen oder neue Beziehungen zwischen Tabellen angeben, indem Sie diese Elemente von der Registerkarte **Toolbox** ziehen. Diese Registerkarte wird angezeigt, wenn der **DataSet-Designer** den Fokus hat.

     ![DataSet-Toolbox](../data-tools/media/raddata-dataset-toolbox.png)

Als nächstes können Sie angeben, wie das DataSet mit Daten aufgefüllt werden soll. Dazu verwenden Sie den **TableAdapter-Konfigurations-Assistenten**. Weitere Informationen finden Sie unter [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Hinzufügen einer Datenbanktabelle oder eines anderen Objekts zu einem vorhandenen DataSet

In diesem Verfahren wird gezeigt, wie Sie eine Tabelle aus derselben Datenbank hinzufügen, die Sie zuvor zum Erstellen des Datasets verwendet haben.

1. Klicken Sie in **Projektmappen-Explorer** auf den Datasetknoten, um den **DataSet-Designer** in den Fokus zu bringen.

2. Klicken Sie im linken Rand von Visual Studio auf die Registerkarte **Datenquellen** , oder geben Sie im Suchfeld **Datenquellen** ein.

3. Klicken Sie mit der rechten Maustaste auf den Knoten DataSet, und wählen Sie **Datenquelle mit Assistent konfigurieren** aus.

     ![Datenquellen-Kontextmenü](../data-tools/media/data-source-context-menu.png)

4. Verwenden Sie den Assistenten, um anzugeben, welche zusätzlichen Tabellen, gespeicherten Prozeduren oder anderen Datenbankobjekte dem DataSet hinzugefügt werden sollen.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Hinzufügen einer eigenständigen Datentabelle zu einem DataSet

1. Öffnen Sie das Dataset im **DataSet-Designer**.

2. Ziehen Sie eine <xref:System.Data.DataTable> Klasse von der Registerkarte **DataSet** der **Toolbox** auf den **DataSet-Designer**.

3. Fügen Sie Spalten hinzu, um die Datentabelle zu definieren. Klicken Sie mit der rechten Maustaste auf die Tabelle, und wählen Sie Spalte **Hinzufügen**  >  **Column** Verwenden Sie das Fenster **Eigenschaften** , um den Datentyp der Spalte und ggf. einen Schlüssel festzulegen.

Eigenständige Tabellen müssen `Fill` Logik in eigenständigen Tabellen implementieren, damit Sie Sie mit Daten füllen können. Informationen zum Auffüllen von eigenständigen Datentabellen finden Sie unter Auffüllen [eines Datasets aus einem DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Siehe auch

- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Beziehungen in DataSets](../data-tools/relationships-in-datasets.md)
- [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)
- [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
