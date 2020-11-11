---
title: 'Exemplarische Vorgehensweise: Speichern von Daten im Rahmen einer Transaktion'
description: In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie Daten in einer Transaktion mithilfe des System. Transactions-Namespace in Visual Studio speichern.
ms.custom: SEO-VS-2020
ms.date: 09/08/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1bb0262139e2096cf55ae7581ef854a57c67d22a
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434544"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Exemplarische Vorgehensweise: Speichern von Daten im Rahmen einer Transaktion

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Daten mithilfe des-Namespace in einer Transaktion gespeichert werden <xref:System.Transactions> . In dieser exemplarischen Vorgehensweise erstellen Sie eine Windows Forms-Anwendung. Mit dem Assistenten zum Konfigurieren von Datenquellen können Sie in der Beispieldatenbank Northwind ein Dataset für zwei Tabellen erstellen. Sie fügen einem Windows Form Daten gebundene Steuerelemente hinzu, und Sie ändern den Code für die Schaltfläche "Save" (speichern) des bindingnavigators, um die Datenbank in einem Transaktionsbereich zu aktualisieren.

## <a name="prerequisites"></a>Voraussetzungen

In dieser exemplarischen Vorgehensweise werden SQL Server Express localdb-und Northwind-Beispieldatenbank verwendet.

1. Wenn Sie nicht über SQL Server Express localdb verfügen, installieren Sie es entweder über die [SQL Server Express Downloadseite](https://www.microsoft.com/sql-server/sql-server-editions-express)oder über das **Visual Studio-Installer**. Im Visual Studio-Installer können SQL Server Express localdb als Teil der Arbeitsauslastung der **.net-Desktop Entwicklung** oder als einzelne Komponente installiert werden.

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

4. Nennen Sie das Projekt **SavingDataInATransactionWalkthrough** , und wählen Sie dann **OK** aus.

     Das Projekt **SavingDataInATransactionWalkthrough** wird erstellt und zum **Projektmappen-Explorer** hinzugefügt.

## <a name="create-a-database-data-source"></a>Erstellen einer Datenbank-Datenquelle

In diesem Schritt wird mithilfe des **Assistenten zum Konfigurieren von Datenquellen** eine Datenquelle basierend auf den `Customers` `Orders` Tabellen und in der Beispieldatenbank Northwind erstellt.

1. Um das Fenster **Datenquellen** zu öffnen, wählen Sie im Menü **Daten** die Option **Datenquellen anzeigen** aus.

2. Wählen Sie im **Datenquellenfenster** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

3. Wählen Sie auf dem Bildschirm **Daten Quellentyp auswählen** die Option **Datenbank** aus, und klicken Sie dann auf **weiter**.

4. Führen Sie auf dem Bildschirm **Wählen Sie Ihre Datenverbindung** einen der folgenden Schritte aus:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

         \- oder -

    - Klicken Sie auf **neue Verbindung** , um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu starten und eine Verbindung mit der Datenbank Northwind herzustellen.

5. Wenn für die Datenbank ein Kennwort erforderlich ist, wählen Sie die Option zum einschließen sensibler Daten aus, und klicken Sie dann auf **weiter**.

6. Wählen Sie auf der Seite **Verbindungs Zeichenfolge in der Anwendungs Konfigurationsdatei speichern** die Option **weiter** aus.

7. Erweitern Sie auf dem Bildschirm **Wählen Sie Ihre Datenbankobjekte** aus den Knoten **Tabellen** .

8. Wählen Sie `Customers` die `Orders` Tabellen und aus, und klicken Sie dann auf **Fertig** stellen.

     Das **NorthwindDataSet** wird Ihrem Projekt hinzugefügt, und die Tabellen `Customers` und `Orders` werden im Fenster **Datenquellen** angezeigt.

## <a name="add-controls-to-the-form"></a>Hinzufügen von Steuerelementen zu dem Formular

Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem Fenster **Datenquellen** auf das Formular ziehen.

1. Erweitern Sie im Fenster **Datenquellen** den Knoten **Customers** .

2. Ziehen Sie den Hauptknoten **Customers** aus dem Fenster **Datenquellen** auf **Form1**.

   Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>-Steuerelement und ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter` , <xref:System.Windows.Forms.BindingSource> und wird <xref:System.Windows.Forms.BindingNavigator> in der Komponenten Leiste angezeigt.

3. Ziehen Sie den zugehörigen Knoten **Orders** (nicht den Haupt Knoten **Orders** , sondern den zugehörigen untergeordneten Tabellen Knoten unterhalb der Spalte **Fax** ) auf das Formular unterhalb von **CustomersDataGridView**.

   Ein <xref:System.Windows.Forms.DataGridView> wird auf dem Formular angezeigt. Ein `OrdersTableAdapter` und wird <xref:System.Windows.Forms.BindingSource> in der Komponenten Leiste angezeigt.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Fügen Sie einen Verweis auf die System. Transactions-Assembly hinzu.

Transaktionen verwenden den Namespace <xref:System.Transactions>. Eine Projektverweis zur Assembly system.transactions wird standardmäßig nicht hinzugefügt. Sie müssen das also manuell tun.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>So fügen Sie einen Verweis zur DLL-Datei System.Transactions hinzu

1. Wählen Sie im Menü **Projekt** die Option **Verweis hinzufügen** aus.

2. Wählen Sie auf der Registerkarte **.net** die Option **System. Transactions** aus, und klicken Sie dann auf **OK**.

     Dem Projekt wird ein Verweis auf **System.Transactions** hinzugefügt.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Ändern Sie den Code in der Schaltfläche "SaveItem" von BindingNavigator.

Für die erste Tabelle, die auf dem Formular abgelegt wird, wird standardmäßig Code dem- `click` Ereignis der Schaltfläche Speichern in hinzugefügt <xref:System.Windows.Forms.BindingNavigator> . Sie müssen für das Ändern weiterer Tabellen den Code manuell hinzufügen. In dieser exemplarischen Vorgehensweise wird der vorhandene Save-Code aus dem Click-Ereignishandler der Schaltfläche "Save" umgestalten. Wir erstellen außerdem einige weitere Methoden, um bestimmte Aktualisierungs Funktionen bereitzustellen, je nachdem, ob die Zeile hinzugefügt oder gelöscht werden muss.

### <a name="to-modify-the-auto-generated-save-code"></a>So ändern Sie automatisch generierten Speichern-Code

1. Wählen Sie im **CustomersBindingNavigator** die Schaltfläche **Speichern** aus (die Schaltfläche mit dem Diskettensymbol).

2. Ersetzen Sie die `CustomersBindingNavigatorSaveItem_Click`-Methode durch den folgenden Code:

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

Der Befehl für das Abgleichen zugehöriger Daten lautet wie folgt:

- Löschen Sie untergeordnete Datensätze. (Löschen Sie in diesem Fall Datensätze aus der `Orders` Tabelle.)

- Löschen Sie übergeordnete Datensätze. (Löschen Sie in diesem Fall Datensätze aus der `Customers` Tabelle.)

- Übergeordnete Datensätze einfügen. (Fügen Sie in diesem Fall Datensätze in die `Customers` Tabelle ein.)

- Untergeordnete Datensätze einfügen. (Fügen Sie in diesem Fall Datensätze in die `Orders` Tabelle ein.)

### <a name="to-delete-existing-orders"></a>So löschen Sie eine vorhandene Bestellungen

- Fügen Sie die folgende Methode `DeleteOrders` zu **Form1** hinzu:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

### <a name="to-delete-existing-customers"></a>So löschen Sie eine vorhandene Kunden

- Fügen Sie die folgende Methode `DeleteCustomers` zu **Form1** hinzu:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

### <a name="to-add-new-customers"></a>Neue Kunden hinzufügen

- Fügen Sie die folgende Methode `AddNewCustomers` zu **Form1** hinzu:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

### <a name="to-add-new-orders"></a>Neue Bestellungen hinzufügen

- Fügen Sie die folgende Methode `AddNewOrders` zu **Form1** hinzu:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Ausführen der Anwendung

Drücken Sie **F5** , um die Anwendung auszuführen.

## <a name="see-also"></a>Siehe auch

- [How to: save data by using a transaction (Vorgehensweise: Speichern von Daten mithilfe einer Transaktion)](../data-tools/save-data-by-using-a-transaction.md)
- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
