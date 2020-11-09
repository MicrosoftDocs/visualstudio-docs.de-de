---
title: Hinzufügen von Code zu TableAdapters in N-Tier-Anwendungen
description: Fügen Sie den Tabellen Adaptern in n-Tier-Anwendungen Code hinzu. Erstellen Sie eine partielle Klassendatei für TableAdapter, und fügen Sie Ihr Code hinzu (anstelle von DatasetName. DataSet. Designer).
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ed0664b78408e91eeda5b65c26615e870e2171b6
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382363"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Hinzufügen von Code zu TableAdapters in N-Tier-Anwendungen
Sie können die Funktionalität eines TableAdapters erweitern, indem Sie eine partielle Klassendatei für den TableAdapter erstellen und diesem Code hinzufügen (anstatt der Datei " *DatasetName. DataSet. Designer* " Code hinzuzufügen). Partielle Klassen ermöglichen das Aufteilen von Code für eine bestimmte Klasse in mehrere physische Dateien. Weitere Informationen finden Sie unter [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) oder [Partial (Type)](/dotnet/csharp/language-reference/keywords/partial-type).

Der Code, der einen TableAdapter definiert, wird jedes Mal generiert, wenn Änderungen am TableAdapter im Dataset vorgenommen werden. Dieser Code wird auch generiert, wenn während der Ausführung eines Assistenten, der die Konfiguration des TableAdapters ändert, Änderungen vorgenommen werden. Um zu verhindern, dass Ihr Code während der erneuten Generierung eines TableAdapters gelöscht wird, fügen Sie der partiellen Klassendatei des TableAdapter Code hinzu.

Nachdem Sie den DataSet-und TableAdapter-Code getrennt haben, ist das Ergebnis standardmäßig eine diskrete Klassendatei in jedem Projekt. Das ursprüngliche Projekt enthält eine Datei mit dem Namen *DatasetName. Designer. vb* (oder *DatasetName.Designer.cs* ), die den TableAdapter-Code enthält. Das Projekt, das in der **DataSet-Projekt** Eigenschaft festgelegt ist, verfügt über eine Datei namens *DatasetName. DataSet. Designer. vb* (oder *DatasetName.DataSet.Designer.cs* ), die den DataSet-Code enthält.

> [!NOTE]
> Bei einer Aufteilung von DataSets und TableAdapters (durch Festlegen der **DataSet-Projekt** -Eigenschaft) werden vorhandene partielle DataSet-Klassen in dem Projekt nicht automatisch verschoben. Vorhandene partielle DataSet-Klassen müssen manuell in das DataSet-Projekt verschoben werden.

> [!NOTE]
> Das DataSet bietet Funktionen zum Erstellen von <xref:System.Data.DataTable.ColumnChanging> -und- <xref:System.Data.DataTable.RowChanging> Ereignis Handlern, wenn eine Überprüfung erforderlich ist. Weitere Informationen finden Sie unter [Hinzufügen von Validierungen zu einem n-Tier-DataSet](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>So fügen Sie einem TableAdapter in einer n-Tier-Anwendung Benutzercode hinzu

1. Suchen Sie das Projekt, das die *XSD* -Datei enthält.

2. Doppelklicken Sie auf die *XSD* -Datei, um die **DataSet-Designer** zu öffnen.

3. Klicken Sie mit der rechten Maustaste auf den TableAdapter, dem Sie Code hinzufügen möchten, und wählen Sie dann **Code anzeigen** aus.

     Eine partielle Klasse wird erstellt und im Code-Editor geöffnet.

4. Fügen Sie Code in der Deklaration der partiellen Klasse hinzu

5. Im folgenden Beispiel wird gezeigt, wo der in der Code hinzugefügt wird `CustomersTableAdapter` `NorthwindDataSet` :

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Siehe auch

- [Übersicht über N-Tier-Daten Anwendungen](../data-tools/n-tier-data-applications-overview.md)
- [Hinzufügen von Code zu DataSets in N-Tier-Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Erstellen und Konfigurieren eines TableAdapters](create-and-configure-tableadapters.md)
- [Übersicht über die hierarchische Aktualisierung](hierarchical-update.md)
