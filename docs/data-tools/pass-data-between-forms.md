---
title: Übergeben von Daten zwischen Formularen
description: In dieser Windows Forms exemplarischen Vorgehensweise finden Sie Schritt-für-Schritt-Anleitungen zum Übergeben von Daten aus einer Form in eine andere.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 9aad1bff0b70f87ff271f6d09cc7f8d34179136d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858565"
---
# <a name="pass-data-between-forms"></a>Übergeben von Daten zwischen Formularen

Diese exemplarische Vorgehensweise enthält eine Schritt-für-Schritt-Anleitung für die Datenübergabe von einem Formular zum anderen. Mithilfe der Tabellen Customers und Orders von Northwind können Benutzer einen Kunden auswählen, und in einem zweiten Formular werden die Bestellungen des ausgewählten Kunden angezeigt. In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie eine Methode auf dem zweiten Formular erstellen, die Daten aus dem ersten Formular empfängt.

> [!NOTE]
> Diese exemplarische Vorgehensweise zeigt nur eine Möglichkeit der Datenübergabe zwischen Formularen. Es gibt weitere Optionen für das Übergeben von Daten an ein Formular, einschließlich der Erstellung eines zweiten Konstruktors zum Empfangen von Daten oder das Erstellen einer öffentlichen Eigenschaft, die mit Daten aus dem ersten Formular festgelegt werden kann.

In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:

- Erstellen eines neuen Projekts vom Typ **Windows Forms-Anwendung**.

- Erstellen und Konfigurieren eines Datasets mit dem Assistenten zum Konfigurieren von [Datenquellen](../data-tools/media/data-source-configuration-wizard.png).

- Auswählen des Steuerelements, das für das Formular erstellt werden soll, wenn Elemente aus dem **Datenquellenfenster** gezogen werden. Weitere Informationen finden Sie unter [Festlegen des Steuer Elements, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Erstellen eines datengebundenen Steuerelements durch Ziehen von Elementen aus dem **Datenquellenfenster** auf das Formular.

- Erstellen eines zweiten Formulars mit einem Raster für die Datenanzeige.

- Erstellen einer TableAdapter-Abfrage für das Abrufen der Bestellungen eines bestimmten Kunden.

- Übergeben von Daten zwischen Formularen.

## <a name="prerequisites"></a>Voraussetzungen

In dieser exemplarischen Vorgehensweise werden SQL Server Express localdb-und Northwind-Beispieldatenbank verwendet.

1. Wenn Sie nicht über SQL Server Express localdb verfügen, installieren Sie es entweder über die [SQL Server Express Downloadseite](https://www.microsoft.com/sql-server/sql-server-editions-express)oder über das **Visual Studio-Installer**. Im Visual Studio-Installer können SQL Server Express localdb als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** oder als einzelne Komponente installiert werden.

2. Installieren Sie die Beispieldatenbank Northwind, indem Sie die folgenden Schritte ausführen:

    1. Öffnen Sie in Visual Studio das Fenster **SQL Server-Objekt-Explorer** . (SQL Server-Objekt-Explorer wird als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** im Visual Studio-Installer installiert.) Erweitern Sie den Knoten **SQL Server** . Klicken Sie mit der rechten Maustaste auf die localdb-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren Sie das [Northwind-Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Mit diesem T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript in den Abfrage-Editor ein, und klicken Sie dann auf die Schaltfläche **Ausführen** .

       Nach kurzer Zeit wird die Ausführung der Abfrage abgeschlossen und die Datenbank Northwind erstellt.

## <a name="create-the-windows-forms-app-project"></a>Erstellen des Windows Forms-App-Projekts

1. Wählen Sie in Visual Studio im Menü **Datei** die Optionen **Neu** > **Projekt** aus.

2. Erweitern Sie entweder **Visual c#** oder **Visual Basic** im linken Bereich, und wählen Sie dann **Windows-Desktop** aus.

3. Wählen Sie im mittleren Bereich den **Windows Forms App** -Projekttyp aus.

4. Nennen Sie das Projekt **PassingDataBetweenForms**, und wählen Sie dann **OK** aus.

     Das Projekt **PassingDataBetweenForms** wird erstellt und zum **Projektmappen-Explorer** hinzugefügt.

## <a name="create-the-data-source"></a>Erstellen der Datenquelle

1. Um das Fenster **Datenquellen** zu öffnen, klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

2. Wählen Sie im **Datenquellen** Fenster die Option **neue Datenquelle hinzufügen** aus, um den Assistenten zum **Konfigurieren von Datenquellen** zu starten.

3. Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.

4. Stellen Sie sicher, dass **Dataset** auf der Seite **Datenbankmodell auswählen** festgelegt ist, und klicken Sie dann auf **Weiter**.

5. Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** aus einen der folgenden Schritte aus:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

    - Klicken Sie auf **Neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu öffnen.

6. Falls die Datenbank ein Kennwort erfordern sollte und die Option für die Einbeziehung vertraulicher Daten aktiviert ist, wählen Sie die Option aus, und klicken Sie dann auf **Weiter**.

7. Klicken Sie auf der Seite **Save connection string to the Application Configuration file** (Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern) auf **Weiter**.

8. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.

9. Wählen Sie die Tabellen **Customers** und **Orders** aus, und klicken Sie dann auf **Fertig stellen**.

     Das **NorthwindDataSet** wird dem Projekt hinzugefügt, und die Tabellen **Customers** und **Orders** werden im **Datenquellenfenster** angezeigt.

## <a name="create-the-first-form-form1"></a>Erstellen des ersten Formulars (Form1)

Sie können ein datengebundenes Raster erstellen (ein <xref:System.Windows.Forms.DataGridView>-Steuerelement), indem Sie den Knoten **Customers** aus dem **Datenquellenfenster** auf das Formular ziehen.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>So erstellen Sie ein datengebundenes Raster auf dem Formular

- Ziehen Sie den Hauptknoten **Customers** aus dem Fenster **Datenquellen** auf **Form1**.

     Eine <xref:System.Windows.Forms.DataGridView> und eine Toolleiste (<xref:System.Windows.Forms.BindingNavigator>) zum Navigieren durch Datensätze wird auf **Form1** angezeigt. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.

## <a name="create-the-second-form"></a>Erstellen des zweiten Formulars

Erstellen Sie ein zweites Formular, an das Daten übergeben werden.

1. Wählen Sie aus dem Menü **Projekt** die Option **Windows Form hinzufügen** aus.

2. Übernehmen Sie den Standardnamen **Form2**, und klicken Sie auf **Hinzufügen**.

3. Ziehen Sie den Hauptknoten **Orders** aus dem **Datenquellenfenster** auf **Form2**.

     Eine <xref:System.Windows.Forms.DataGridView> und eine Toolleiste (<xref:System.Windows.Forms.BindingNavigator>) zum Navigieren durch Datensätze wird auf **Form2** angezeigt. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.

4. Löschen Sie **OrdersBindingNavigator** aus der Komponentenleiste.

     **OrdersBindingNavigator** wird von **Form2** entfernt.

## <a name="add-a-tableadapter-query"></a>Hinzufügen einer TableAdapter-Abfrage

Fügen Sie Form2 eine TableAdapter-Abfrage hinzu, um die Bestellungen für den ausgewählten Kunden auf Form1 zu laden.

1. Doppelklicken Sie im **Projektmappen-Explorer** auf die Datei **NorthwindDataSet.xsd**.

2. Klicken Sie mit der rechten Maustaste auf **OrdersTableAdapter**, und wählen Sie **Abfrage hinzufügen** aus.

3. Übernehmen Sie die Standardeinstellung für **SQL-Anweisung verwenden**, und klicken Sie anschließend auf **Weiter**.

4. Übernehmen Sie die Standardeinstellung für **SELECT-Anweisung, die Zeilen zurückgibt**, und klicken Sie anschließend auf **Weiter**.

5. Fügen Sie eine WHERE-Klausel zur Abfrage hinzu, sodass `Orders` auf Grundlage der `CustomerID` zurückgeben wird. Die Abfrage müsste ungefähr wie folgt aussehen:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Überprüfen Sie die korrekte Parametersyntax für Ihre Datenbank. In Microsoft Access würde die WHERE-Klausel wie folgt aussehen: `WHERE CustomerID = ?`.

6. Klicken Sie auf **Weiter**.

7. Geben Sie für den **datatablemethod-Namen ausfüllen den Namen ein** `FillByCustomerID` .

8. Löschen Sie die Option **DataTable zurückgeben**, und klicken Sie anschließend **Weiter**.

9. Klicken Sie auf **Fertig stellen**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Erstellen Sie eine Methode auf Form2, an die Daten übergeben werden.

1. Klicken Sie mit der rechten Maustaste auf **Form2**, und klicken Sie auf **Code anzeigen**, um **Form2** im **Code-Editor** zu öffnen.

2. Fügen Sie den folgenden Code zu **Form2** nach der `Form2_Load`-Methode hinzu:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Erstellen einer Methode auf Form1 zum Übergeben von Daten und Anzeigen von Form2

1. Klicken Sie in **Form1** mit der rechten Maustaste auf das Customer-Datenraster, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie im Fenster **Eigenschaften** auf **Ereignisse**.

3. Doppelklicken Sie das Ereignis **CellDoubleClick**.

     Der Code-Editor wird angezeigt.

4. Aktualisieren Sie die Methodendefinition, sodass sie dem folgenden Beispiel entspricht:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-app"></a>Ausführen der App

- Drücken Sie **F5**, um die Anwendung auszuführen.

- Doppelklicken Sie einen Kundendatensatz in **Form1**, sodass dieser in **Form2** mit den Bestellungen dieses Kunden geöffnet wird.

## <a name="next-steps"></a>Nächste Schritte

Entsprechend den Anforderungen an Ihre Anwendung können Sie nach dem Übergeben der Daten zwischen den Formularen noch weitere Schritte ausführen. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:

- Hinzufügen oder Entfernen von Datenbankobjekten aus dem Dataset durch Bearbeiten. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Hinzufügen einer Funktion für das Zurückspeichern von Daten in der Datenbank. Weitere Informationen finden Sie unter [Speichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Weitere Informationen

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
