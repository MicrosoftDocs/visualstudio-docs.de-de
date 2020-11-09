---
title: Hinzufügen von Code zu DataSets in n-schichtigen Anwendungen
description: Hinzufügen von Code zu Datasets in n-Tier-apps in Visual Studio. Erstellen Sie eine partielle Klassendatei für ein DataSet, und fügen Sie Ihr Code hinzu (anstelle von DatasetName. DataSet. Designer).
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending DataSets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bdbd6e728ebd4adea1a18d842651e9941098249c
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382194"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Hinzufügen von Code zu DataSets in n-schichtigen Anwendungen

Sie können die Funktionalität eines Datasets erweitern, indem Sie eine partielle Klassendatei für das Dataset erstellen und diesem Code hinzufügen (anstatt dem *DataSetName* Code hinzuzufügen. DataSet. Designer-Datei). Partielle Klassen ermöglichen das Aufteilen von Code für eine bestimmte Klasse in mehrere physische Dateien. Weitere Informationen finden Sie unter [partielle](/dotnet/visual-basic/language-reference/modifiers/partial) oder [partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

Der Code, mit dem ein Dataset definiert wird, wird jedes Mal generiert, wenn Änderungen an der datasetdefinition (im typisierten DataSet) vorgenommen werden. Dieser Code wird auch generiert, wenn Sie während der Ausführung eines Assistenten, der die Konfiguration eines Datasets ändert, Änderungen vornehmen. Um zu verhindern, dass Ihr Code während der erneuten Generierung eines Datasets gelöscht wird, fügen Sie der partiellen Klassendatei des Datasets Code hinzu.

Nachdem Sie den DataSet-und TableAdapter-Code getrennt haben, ist das Ergebnis standardmäßig eine diskrete Klassendatei in jedem Projekt. Das ursprüngliche Projekt enthält eine Datei mit dem Namen *DatasetName. Designer. vb* (oder *DatasetName.Designer.cs* ), die den TableAdapter-Code enthält. Das Projekt, das in der **DataSet-Projekt** Eigenschaft festgelegt ist, verfügt über eine Datei namens *DatasetName. DataSet. Designer. vb* (oder *DatasetName.DataSet.Designer.cs* ). Diese Datei enthält den DataSet-Code.

> [!NOTE]
> Beim Trennen von Datasets und TableAdapters (durch Festlegen der **DataSet-Projekt** Eigenschaft) werden vorhandene partielle DataSet-Klassen in dem Projekt nicht automatisch verschoben. Vorhandene partielle DataSet-Klassen müssen manuell in das DataSet-Projekt verschoben werden.

> [!NOTE]
> Wenn Validierungscode hinzugefügt werden muss, stellt das typisierte DataSet Funktionen zum Erstellen von <xref:System.Data.DataTable.ColumnChanging> -und- <xref:System.Data.DataTable.RowChanging> Ereignis Handlern bereit. Weitere Informationen finden Sie unter [Hinzufügen von Validierungen zu einem n-Tier-DataSet](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>So fügen Sie Datasets in n-Tier-Anwendungen Code hinzu

1. Suchen Sie das Projekt, das die *XSD* -Datei enthält.

2. Wählen Sie die **XSD** -Datei aus, um das DataSet zu öffnen.

3. Klicken Sie mit der rechten Maustaste auf die Datentabelle, der Sie Code hinzufügen möchten (der Tabellenname in der Titelleiste), und wählen Sie dann **Code anzeigen** aus.

     Eine partielle Klasse wird erstellt und im Code-Editor geöffnet.

4. Fügen Sie Code in der Deklaration der partiellen Klasse hinzu

     Im folgenden Beispiel wird gezeigt, wo der customersdatbare-Datei in NorthwindDataSet Code hinzugefügt wird:

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```

    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>Siehe auch

- [Übersicht über N-Tier-Daten Anwendungen](../data-tools/n-tier-data-applications-overview.md)
- [Hinzufügen von Code zu TableAdapters in N-Tier-Anwendungen](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Erstellen und Konfigurieren eines TableAdapters](create-and-configure-tableadapters.md)
- [Übersicht über die hierarchische Aktualisierung](hierarchical-update.md)
- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
