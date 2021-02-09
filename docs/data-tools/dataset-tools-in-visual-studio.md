---
title: Datasettools
description: Überprüfen Sie die in Visual Studio verfügbaren DataSet-Tools. Weitere Informationen finden Sie unter datasetworkflow, Datasets und N-Ebenen-Architektur sowie Datasets und XML.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 4e711d60010117f3a5081470ab8e6e656a7e6e90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866995"
---
# <a name="dataset-tools-in-visual-studio"></a>Datasettools in Visual Studio

> [!NOTE]
> Bei Datasets und verknüpften Klassen handelt es sich um Legacy-.NET-Technologien aus den frühen 2000er-Jahren, mit denen Anwendungen mit Daten im Arbeitsspeicher arbeiten können, während die Anwendungen von der Datenbank getrennt werden Sie sind besonders nützlich für Anwendungen, die es Benutzern ermöglichen, Daten zu ändern und die Änderungen wieder in der Datenbank zu speichern. Obwohl es sich bei Datasets um eine sehr erfolgreiche Technologie handelt, empfiehlt es sich, dass neue .NET-Anwendungen Entity Framework verwenden. Entity Framework bietet eine natürlichere Möglichkeit zum Arbeiten mit tabellarischen Daten als Objekt Modelle und verfügt über eine einfachere Programmierschnittstelle.

Ein `DataSet` -Objekt ist ein in-Memory-Objekt, das im Wesentlichen eine Mini Datenbank ist. Es enthält `DataTable` `DataColumn` -,-und- `DataRow` Objekte, in denen Sie Daten aus einer oder mehreren Datenbanken speichern und ändern können, ohne dass eine offene Verbindung aufrechterhalten werden muss. Das Dataset verwaltet Informationen zu Änderungen an den Daten, sodass Updates nachverfolgt und zurück an die Datenbank gesendet werden können, wenn die Anwendung wieder verbunden wird.

Datasets und zugehörige Klassen werden im- <xref:System.Data?displayProperty=fullName> Namespace in der .NET-API definiert. Sie können Datasets mithilfe von ADO.NET dynamisch im Code erstellen und ändern. In der Dokumentation in diesem Abschnitt wird gezeigt, wie mit Datasets mithilfe von Visual Studio-Designern gearbeitet wird. Datasets, die über Designer erstellt werden, verwenden **TableAdapter** -Objekte, um mit der Datenbank zu interagieren. Datasets, die Programm gesteuert erstellt werden, verwenden **DataAdapter** -Objekte. Informationen zum programmgesteuerten Erstellen von Datasets finden Sie unter [DataAdapters und DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

Wenn Ihre Anwendung nur Daten aus einer Datenbank lesen und keine Updates, Hinzufügungen oder Löschungen ausführen muss, können Sie in der Regel eine bessere Leistung erzielen, indem Sie ein-Objekt verwenden, `DataReader` um Daten in ein generisches `List` Objekt oder ein anderes Sammlungsobjekt abzurufen. Wenn Sie die Daten anzeigen, können Sie die Benutzeroberfläche an die Sammlung binden.

## <a name="dataset-workflow"></a>DataSet-Workflow

Visual Studio stellt Tools bereit, um die Arbeit mit Datasets zu vereinfachen. Der grundlegende End-to-End-Workflow lautet wie folgt:

- Verwenden Sie das [Fenster Datenquellen](add-new-data-sources.md#data-sources-window) , um ein neues Dataset aus einer oder mehreren Datenquellen zu erstellen. Verwenden Sie die **DataSet-Designer** , um das DataSet zu konfigurieren und seine Eigenschaften festzulegen. Beispielsweise müssen Sie angeben, welche Tabellen aus der Datenquelle eingeschlossen werden sollen und welche Spalten aus jeder Tabelle enthalten sein sollen. Wählen Sie sorgfältig aus, um den Speicherplatz zu sparen, der für das DataSet erforderlich ist. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Geben Sie die Beziehungen zwischen den Tabellen an, sodass Fremdschlüssel ordnungsgemäß verarbeitet werden. Weitere Informationen finden Sie unter [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

- Verwenden Sie den **TableAdapter-Konfigurations-Assistenten** , um die Abfrage oder die gespeicherte Prozedur anzugeben, die das DataSet auffüllt, und welche Daten Bank Vorgänge (aktualisieren, löschen usw.) implementiert werden. Weitere Informationen finden Sie in den folgenden Themen:

  - [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Bearbeiten von Daten in Datasets](../data-tools/edit-data-in-datasets.md)

  - [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md)

  - [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)

- Abfragen und Durchsuchen der Daten im DataSet. Weitere Informationen finden Sie unter [Abfragen von Datasets](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] aktiviert [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) über Daten in einem- <xref:System.Data.DataSet> Objekt. Weitere Informationen finden Sie unter [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

- Verwenden Sie das Fenster **Datenquellen** , um Steuerelemente der Benutzeroberfläche an das DataSet oder die einzelnen Spalten zu binden und um anzugeben, welche Spalten vom Benutzer bearbeitet werden können. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Datasets und N-Tier-Architektur

Informationen zu Datasets in n-Tier-Anwendungen finden Sie unter [Arbeiten mit Datasets in n-Tier-Anwendungen](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Datasets und XML

Informationen zum Umstellen von Datasets in und aus XML finden [Sie unter Lesen von XML-Daten in ein DataSet](../data-tools/read-xml-data-into-a-dataset.md) und [Speichern eines Datasets als XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
