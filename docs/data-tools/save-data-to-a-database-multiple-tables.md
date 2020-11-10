---
title: Speichern von Daten in einer Datenbank (mehrere Tabellen)
description: In dieser exemplarischen Vorgehensweise können Sie Daten aus mehreren Tabellen in einer Datenbank mithilfe von datasettools in Visual Studio speichern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 2f6401fedc3158e2743f08775da93faf2ddfee73
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436041"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Speichern von Daten in einer Datenbank (mehrere Tabellen)

Eines der häufigsten Szenarios in der Anwendungsentwicklung ist das Anzeigen von Daten auf einem Formular in einer Windows-Anwendung, das Bearbeiten der Daten und das Senden der aktualisierten Daten zurück an die Datenbank. In dieser exemplarischen Vorgehensweise wird ein Formular erstellt, in dem Daten aus zwei verknüpften Tabellen angezeigt werden. Darüber hinaus wird gezeigt, wie Datensätze bearbeitet und Änderungen wieder in der Datenbank gespeichert werden. In diesem Beispiel werden die Tabellen `Customers` und `Orders` aus der Beispieldatenbank Northwind verwendet.

Sie können Daten in der Anwendung wieder in der Datenbank speichern, indem Sie die `Update`-Methode eines TableAdapter aufrufen. Wenn Sie Tabellen aus dem **Datenquellen** Fenster auf ein Formular ziehen, wird der Code, der zum Speichern der Daten erforderlich ist, automatisch hinzugefügt. Alle weiteren Tabellen, die zu einem Formular hinzugefügt werden, müssen manuell hinzugefügt werden. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Code hinzugefügt wird, um Aktualisierungen aus mehreren Tabellen zu speichern.

In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:

- Erstellen und Konfigurieren einer Datenquelle in der Anwendung mit dem Assistenten zum Konfigurieren von [Datenquellen](../data-tools/media/data-source-configuration-wizard.png).

- Festlegen der Steuerelemente der Elemente im [Datenquellen Fenster](add-new-data-sources.md#data-sources-window). Weitere Informationen finden Sie unter [Festlegen des Steuer Elements, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Erstellen datengebundener Steuerelemente durch Ziehen von Elementen aus dem Fenster **Datenquellen** auf das Formular.

- Ändern einiger Datensätze in jeder Tabelle im DataSet.

- Ändern von Code zum Zurücksenden der aktualisierten Daten des Datasets an die Datenbank.

## <a name="prerequisites"></a>Voraussetzungen

In dieser exemplarischen Vorgehensweise werden SQL Server Express localdb-und Northwind-Beispieldatenbank verwendet.

1. Wenn Sie nicht über SQL Server Express localdb verfügen, installieren Sie es entweder über die [SQL Server Express Downloadseite](https://www.microsoft.com/sql-server/sql-server-editions-express)oder über das **Visual Studio-Installer**. Im **Visual Studio-Installer** können Sie SQL Server Express localdb als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** oder als einzelne Komponente installieren.

2. Installieren Sie die Beispieldatenbank Northwind, indem Sie die folgenden Schritte ausführen:

    1. Öffnen Sie in Visual Studio das Fenster **SQL Server-Objekt-Explorer** . (SQL Server-Objekt-Explorer wird als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** im Visual Studio-Installer installiert.) Erweitern Sie den Knoten **SQL Server** . Klicken Sie mit der rechten Maustaste auf die localdb-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren Sie das [Northwind-Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Mit diesem T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript in den Abfrage-Editor ein, und klicken Sie dann auf die Schaltfläche **Ausführen** .

       Nach kurzer Zeit wird die Ausführung der Abfrage abgeschlossen und die Datenbank Northwind erstellt.

## <a name="create-the-windows-forms-application"></a>Erstellen der Windows Forms Anwendung

Erstellen Sie ein neues **Windows Forms-App** -Projekt für c# oder Visual Basic. Nennen Sie das Projekt **UpdateMultipleTablesWalkthrough**.

## <a name="create-the-data-source"></a>Erstellen der Datenquelle

In diesem Schritt wird mit dem **Assistenten zum Konfigurieren von Datenquellen** eine Datenquelle aus der Northwind-Datenbank erstellt. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Weitere Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter Gewusst [wie: Installieren von Beispiel Datenbanken](../data-tools/installing-database-systems-tools-and-samples.md).

1. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

   Das Fenster **Datenquellen** wird geöffnet.

2. Wählen Sie im **Datenquellenfenster** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

3. Wählen Sie auf dem Bildschirm **Daten Quellentyp auswählen** die Option **Datenbank** aus, und klicken Sie dann auf **weiter**.

4. Führen Sie auf dem Bildschirm **Wählen Sie Ihre Datenverbindung** aus einen der folgenden Schritte aus:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

         \- oder -

    - Wählen Sie **Neue Verbindung** aus, um das Dialogfeld **Verbindung hinzufügen/ändern** zu öffnen.

5. Wenn für die Datenbank ein Kennwort erforderlich ist, wählen Sie die Option zum einschließen sensibler Daten aus, und klicken Sie dann auf **weiter**.

6. Wählen Sie unter **Verbindungs Zeichenfolge in der Anwendungs Konfigurationsdatei speichern** die Option **weiter** aus.

7. Erweitern Sie auf dem Bildschirm **Wählen Sie Ihre Datenbankobjekte** aus den Knoten **Tabellen** .

8. Wählen Sie die Tabellen **Customers** und **Orders** aus, und klicken Sie dann auf **Fertig** stellen.

     **NorthwindDataSet** wird dem Projekt hinzugefügt. Die Tabellen werden im Fenster **Datenquellen** angezeigt.

## <a name="set-the-controls-to-be-created"></a>Festlegen der zu erstellenden Steuerelemente

In dieser exemplarischen Vorgehensweise befinden sich die Daten in der `Customers` Tabelle in einem **Detail** Layout, in dem die Daten in einzelnen Steuerelementen angezeigt werden. Die Daten aus der `Orders` Tabelle befinden sich in einem **Raster** Layout, das in einem-Steuerelement angezeigt wird <xref:System.Windows.Forms.DataGridView> .

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>So legen Sie den Ablagetyp für die Elemente im Datenquellenfenster fest

1. Erweitern Sie im Fenster **Datenquellen** den Knoten **Customers** .

2. Wählen Sie auf dem Knoten **Customers** in der Liste Steuerelement die Option **Details** aus, um das Steuerelement der Tabelle **Customers** in einzelne Steuerelemente zu ändern. Weitere Informationen finden Sie unter [Festlegen des Steuer Elements, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Erstellen des Daten gebundenen Formulars

Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem Fenster **Datenquellen** auf das Formular ziehen.

1. Ziehen Sie den Hauptknoten **Customers** aus dem Fenster **Datenquellen** auf **Form1**.

     Auf dem Formular werden datengebundene Steuerelemente mit beschreibenden Bezeichnungen sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter` , <xref:System.Windows.Forms.BindingSource> und wird <xref:System.Windows.Forms.BindingNavigator> in der Komponenten Leiste angezeigt.

2. Ziehen Sie den Knoten **Orders** aus dem Fenster **Datenquellen** auf **Form1**.

    > [!NOTE]
    > Der verknüpfte Knoten **Orders** befindet sich unter der Spalte **Fax** und ist ein untergeordneter Knoten des Knotens **Customers**.

     Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>-Steuerelement und ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein `OrdersTableAdapter` und wird <xref:System.Windows.Forms.BindingSource> in der Komponenten Leiste angezeigt.

## <a name="add-code-to-update-the-database"></a>Hinzufügen von Code zum Aktualisieren der Datenbank

Sie können die Datenbank aktualisieren, indem Sie die `Update`-Methoden der TableAdapters **Customers** und **Orders** aufrufen. Standardmäßig wird ein Ereignishandler für die Schaltfläche **Speichern** der dem <xref:System.Windows.Forms.BindingNavigator> Code des Formulars hinzugefügt, um Updates an die Datenbank zu senden. Diese Prozedur ändert den Code, um Updates in der richtigen Reihenfolge zu senden. Dadurch ist es nicht mehr möglich, referenzielle Integritäts Fehler zu erhöhen. Mit dem Code wird außerdem die Fehlerbehandlung implementiert, indem der Aktualisierungsaufruf mit einem Try-Catch-Block umschlossen wird. Sie können den Code entsprechend den Anforderungen der Anwendung anpassen.

> [!NOTE]
> Aus Gründen der Übersichtlichkeit wird in dieser exemplarischen Vorgehensweise keine Transaktion verwendet. Wenn Sie jedoch zwei oder mehr verknüpfte Tabellen aktualisieren, schließen Sie die gesamte Aktualisierungs Logik in eine Transaktion ein. Eine Transaktion ist ein Prozess, mit dem sichergestellt wird, dass alle zugehörigen Änderungen an einer Datenbank erfolgreich sind, bevor für Änderungen ein Commit ausgeführt wird. Weitere Informationen finden Sie unter [Transaktionen und](/dotnet/framework/data/adonet/transactions-and-concurrency)Parallelität.

### <a name="to-add-update-logic-to-the-application"></a>So fügen Sie der Anwendung Aktualisierungslogik hinzu

1. Klicken Sie auf die Schaltfläche **Speichern** <xref:System.Windows.Forms.BindingNavigator> . Dadurch wird der Code-Editor für den- `bindingNavigatorSaveItem_Click` Ereignishandler geöffnet.

2. Ändern Sie den Code im Ereignishandler, sodass die `Update`-Methoden der verknüpften TableAdapters aufgerufen werden. Mit folgendem Code werden zunächst drei temporäre Datentabellen zum Speichern der aktualisierten Informationen für jeden <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added> und <xref:System.Data.DataRowState.Modified>) erstellt. Die Updates werden in der richtigen Reihenfolge ausgeführt. Der Code sollte wie folgt aussehen:

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>Testen der Anwendung

1. Drücken Sie **F5**.

2. Nehmen Sie in jeder Tabelle einige Änderungen an den Daten eines oder mehrerer Datensätze vor.

3. Klicken Sie auf die Schaltfläche **Speichern**.

4. Überprüfen Sie die Werte in der Datenbank, um sicherzustellen, dass die Änderungen gespeichert wurden.

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
