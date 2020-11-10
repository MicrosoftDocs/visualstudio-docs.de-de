---
title: Speichern von Daten mit den TableAdapter-DBDirect-Methoden
description: Führen Sie in dieser exemplarischen Vorgehensweise SQL-Anweisungen direkt für eine Datenbank aus, indem Sie die DBDirect-Methoden eines TableAdapters verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5d79b2081e2d30d77ae3507884b44421f0f14bae
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434570"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Speichern von Daten mit den TableAdapter-DBDirect-Methoden

Diese exemplarische Vorgehensweise enthält ausführliche Anweisungen zum Ausführen von SQL-Anweisungen direkt für eine-Datenbank mithilfe der DBDirect-Methoden eines TableAdapter. Die DBDirect-Methoden eines TableAdapters bieten ein sehr gutes Maß an Kontrolle über Änderungen an der Datenbank. Sie können Sie verwenden, um bestimmte SQL-Anweisungen und gespeicherte Prozeduren auszuführen, indem Sie die einzelnen `Insert` `Update` Methoden, und nach `Delete` Bedarf von der Anwendung aufrufen (im Gegensatz zur überladenen `Update` Methode, die die Update-, INSERT-und DELETE-Anweisungen in einem Aufruf ausführt).

Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

- Erstellen Sie eine neue **Windows Forms Anwendung**.

- Erstellen und konfigurieren Sie mit dem Assistenten zum Konfigurieren von [Datenquellen](../data-tools/media/data-source-configuration-wizard.png)ein DataSet.

- Wählen Sie das Steuerelement aus, das für das Formular erstellt werden soll, wenn Elemente aus dem **Datenquellenfenster** gezogen werden. Weitere Informationen finden Sie unter [Festlegen des Steuer Elements, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Erstellen eines datengebundenen Formulars durch Ziehen von Elementen aus dem **Datenquellenfenster** auf das Formular.

- Fügen Sie Methoden hinzu, um direkt auf die Datenbank zuzugreifen und Einfügungen, Updates und Löschungen auszuführen.

## <a name="prerequisites"></a>Voraussetzungen

In dieser exemplarischen Vorgehensweise werden SQL Server Express localdb-und Northwind-Beispieldatenbank verwendet.

1. Wenn Sie nicht über SQL Server Express localdb verfügen, installieren Sie es entweder über die [SQL Server Express Downloadseite](https://www.microsoft.com/sql-server/sql-server-editions-express)oder über das **Visual Studio-Installer**. Im **Visual Studio-Installer** können Sie SQL Server Express localdb als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** oder als einzelne Komponente installieren.

2. Installieren Sie die Beispieldatenbank Northwind, indem Sie die folgenden Schritte ausführen:

    1. Öffnen Sie in Visual Studio das Fenster **SQL Server-Objekt-Explorer** . (SQL Server-Objekt-Explorer wird als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** im Visual Studio-Installer installiert.) Erweitern Sie den Knoten **SQL Server** . Klicken Sie mit der rechten Maustaste auf die localdb-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren Sie das [Northwind-Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Mit diesem T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript in den Abfrage-Editor ein, und klicken Sie dann auf die Schaltfläche **Ausführen** .

       Nach kurzer Zeit wird die Ausführung der Abfrage abgeschlossen und die Datenbank Northwind erstellt.

## <a name="create-a-windows-forms-application"></a>Erstellen einer Windows Forms-Anwendung

Der erste Schritt besteht darin, eine **Windows Forms Anwendung** zu erstellen.

1. Wählen Sie in Visual Studio im Menü **Datei** die Optionen **Neu** > **Projekt** aus.

2. Erweitern Sie entweder **Visual c#** oder **Visual Basic** im linken Bereich, und wählen Sie dann **Windows-Desktop** aus.

3. Wählen Sie im mittleren Bereich den **Windows Forms App** -Projekttyp aus.

4. Nennen Sie das Projekt **TableAdapterDbDirectMethodsWalkthrough** , und wählen Sie dann **OK** aus.

     Das Projekt **TableAdapterDbDirectMethodsWalkthrough** wird erstellt und zum **Projektmappen-Explorer** hinzugefügt.

## <a name="create-a-data-source-from-your-database"></a>Erstellen einer Datenquelle aus der Datenbank

Dieser Schritt verwendet den **Assistenten zum Konfigurieren von Datenquellen** auf Grundlage der `Region`-Tabelle in der Beispieldatenbank Northwind. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Weitere Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter Gewusst [wie: Installieren von Beispiel Datenbanken](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle

1. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

   Das Fenster **Datenquellen** wird geöffnet.

2. Wählen Sie im **Datenquellenfenster** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

3. Wählen Sie auf dem Bildschirm **Daten Quellentyp auswählen** die Option **Datenbank** aus, und klicken Sie dann auf **weiter**.

4. Führen Sie auf dem Bildschirm **Wählen Sie Ihre Datenverbindung** aus einen der folgenden Schritte aus:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

         \- oder -

    - Klicken Sie auf **Neue Verbindung** , um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu öffnen.

5. Wenn für die Datenbank ein Kennwort erforderlich ist, wählen Sie die Option zum einschließen sensibler Daten aus, und klicken Sie dann auf **weiter**.

6. Wählen Sie auf der Seite **Verbindungs Zeichenfolge in der Anwendungs Konfigurationsdatei speichern** die Option **weiter** aus.

7. Erweitern Sie auf dem Bildschirm **Wählen Sie Ihre Datenbankobjekte** aus den Knoten **Tabellen** .

8. Wählen Sie die `Region` Tabelle aus, und klicken Sie dann auf **Fertig** stellen.

     Das **NorthwindDataSet** wird Ihrem Projekt hinzugefügt, und die `Region`-Tabelle wird im **Datenquellenfenster** angezeigt.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Fügen Sie dem Formular Steuerelemente hinzu, um die Daten anzuzeigen.

Erstellen Sie die datengebundenen Steuerelemente, indem Sie Elemente aus dem **Datenquellenfenster** auf das Formular ziehen.

Wenn Sie Daten gebundene Steuerelemente auf dem Windows Form erstellen möchten, ziehen Sie **den Haupt Knoten** Knoten aus dem **Datenquellen** Fenster auf das Formular.

Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>-Steuerelement und ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter` , <xref:System.Windows.Forms.BindingSource> und wird <xref:System.Windows.Forms.BindingNavigator> in der Komponenten Leiste angezeigt.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Hinzufügen von Schaltflächen, die die einzelnen TableAdapter DbDirect-Methoden aufruft

1. Ziehen Sie drei <xref:System.Windows.Forms.Button>-Steuerelemente aus der **Toolbox** auf **Form1** (unter **RegionDataGridView** ).

2. Legen Sie die folgenden Eigenschaften für **Name** und **Text** auf jeder Schaltfläche fest.

    |Name|Text|
    |----------|----------|
    |`InsertButton`|**Einfügen**|
    |`UpdateButton`|**Aktualisieren**|
    |`DeleteButton`|**Löschen**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Hinzufügen von Code für das Einfügen neuer Datensätze in die Datenbank

1. Wählen Sie **InsertButton** aus, um einen Ereignishandler für das Click-Ereignis zu erstellen und das Formular im Code-Editor zu öffnen.

2. Ersetzen Sie den Ereignishandler `InsertButton_Click`durch den folgenden Code:

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

### <a name="to-add-code-to-update-records-in-the-database"></a>Hinzufügen von Code für die Aktualisierung von Datensätzen in der Datenbank

1. Doppelklicken Sie **UpdateButton** , sodass ein Ereignishandler für Click-Ereignis erstellt wird, und öffnen Sie das Formular im Code-Editor.

2. Ersetzen Sie den Ereignishandler `UpdateButton_Click`durch den folgenden Code:

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

### <a name="to-add-code-to-delete-records-from-the-database"></a>So fügen Sie Code hinzu, um Datensätze aus der Datenbank zu löschen

1. Wählen Sie **DeleteButton** aus, um einen Ereignishandler für das Click-Ereignis zu erstellen und das Formular im Code-Editor zu öffnen.

2. Ersetzen Sie den Ereignishandler `DeleteButton_Click`durch den folgenden Code:

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>Ausführen der Anwendung

- Drücken Sie **F5** , um die Anwendung auszuführen.

- Wählen Sie die Schaltfläche **Einfügen** aus, und überprüfen Sie, ob der neue Datensatz im Raster angezeigt wird.

- Wählen Sie die Schaltfläche **Aktualisieren** aus, und überprüfen Sie, ob der Datensatz im Raster aktualisiert wurde.

- Wählen Sie die Schaltfläche **Löschen** aus, und überprüfen Sie, ob der Datensatz aus dem Raster entfernt wurde.

## <a name="next-steps"></a>Nächste Schritte

Abhängig von den Anforderungen Ihrer Anwendung können Sie nach dem Erstellen eines Daten gebundenen Formulars einige Schritte ausführen. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:

- Fügen Sie dem Formular Suchfunktionalität hinzu.

- Hinzufügen weiterer Tabellen zum Dataset durch Auswählen von **DataSet mit Assistent konfigurieren** aus dem **Datenquellenfenster**. Sie können Steuerelemente hinzufügen, die zugehörige Daten anzeigen, indem Sie die entsprechenden Knoten auf das Formular ziehen. Weitere Informationen finden Sie unter [Beziehungen in Datasets](relationships-in-datasets.md).

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
