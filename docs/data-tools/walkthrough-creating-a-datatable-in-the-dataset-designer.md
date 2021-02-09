---
title: Erstellen Sie eine Datentabelle im DataSet-Designer
description: Erstellen Sie in dieser exemplarischen Vorgehensweise eine Datentabelle (ohne TableAdapter), indem Sie die DataSet-Designer verwenden. Erstellen Sie eine neue Windows Forms Anwendung, und fügen Sie Ihr ein neues Dataset hinzu.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: feec31fa0a9e34ad63e0b849d09084081e5710e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858175"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Exemplarische Vorgehensweise: Erstellen einer Datentabelle in der DataSet-Designer

In dieser exemplarischen Vorgehensweise wird erläutert, wie ein <xref:System.Data.DataTable> (ohne TableAdapter) mithilfe der **DataSet-Designer** erstellt wird. Weitere Informationen zum Erstellen von Datentabellen, die TableAdapters enthalten, finden Sie unter [Erstellen und Konfigurieren von TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Erstellen einer neuen Windows Forms-Anwendung

1. Wählen Sie in Visual Studio im Menü **Datei** die Optionen **Neu** > **Projekt** aus.

2. Erweitern Sie entweder **Visual c#** oder **Visual Basic** im linken Bereich, und wählen Sie dann **Windows-Desktop** aus.

3. Wählen Sie im mittleren Bereich den **Windows Forms App** -Projekttyp aus.

4. Nennen Sie das Projekt **DataTableWalkthrough**, und wählen Sie dann **OK** aus.

     Das Projekt **DataTableWalkthrough** wird erstellt und **Projektmappen-Explorer** hinzugefügt.

## <a name="add-a-new-dataset-to-the-application"></a>Hinzufügen eines neuen Datasets zur Anwendung

1. Wählen Sie im Menü **Projekt** den Eintrag **Neues Element hinzufügen** aus.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

2. Wählen Sie im linken Bereich **Daten** aus, und wählen Sie dann im mittleren Bereich **DataSet** aus.

3. Wählen Sie **Hinzufügen** aus.

     Visual Studio fügt dem Projekt eine Datei mit dem Namen **DataSet1. xsd** hinzu und öffnet Sie in der **DataSet-Designer**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Neue Datentabelle zum DataSet hinzufügen

1. Ziehen Sie eine **Daten** Tabelle von der Registerkarte **DataSet** der **Toolbox** auf den **DataSet-Designer**.

     Eine Tabelle mit dem Namen **DataTable1** wird dem DataSet hinzugefügt.

2. Klicken Sie auf die Titelleiste von **DataTable1** , und benennen Sie Sie um `Music` .

## <a name="add-columns-to-the-datatable"></a>Hinzufügen von Spalten zur Datentabelle

1. Klicken Sie mit der rechten Maustaste auf die Tabelle **Music** . Zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Spalte**.

2. Benennen Sie die Spalte `SongID` .

3. Legen Sie im Fenster **Eigenschaften** die Eigenschaft <xref:System.Data.DataColumn.DataType%2A> auf <xref:System.Int16?displayProperty=fullName>fest.

4. Wiederholen Sie diesen Vorgang, und fügen Sie die folgenden Spalten hinzu:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Legen Sie den Primärschlüssel für die Tabelle fest.

Alle Datentabellen sollten über einen Primärschlüssel verfügen. Ein Primärschlüssel identifiziert eindeutig einen bestimmten Datensatz in einer Datentabelle.

Um den Primärschlüssel festzulegen, klicken Sie mit der rechten Maustaste auf die Spalte **SongID** , und klicken Sie dann auf **Primärschlüssel festlegen**. Neben der Spalte **SongID** wird ein Schlüsselsymbol angezeigt.

## <a name="save-your-project"></a>Speichern Ihres Projekts

Um das Projekt **DataTableWalkthrough** zu speichern, wählen Sie im Menü **Datei** die Option **Alle speichern** aus.

## <a name="see-also"></a>Weitere Informationen

- [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Validieren von Daten](../data-tools/validate-data-in-datasets.md)
