---
title: Erstellen Sie ein DataSet mit dem DataSet-Designer
description: Erstellen Sie in dieser exemplarischen Vorgehensweise ein DataSet mit dem DataSet-Designer. Erfahren Sie, wie Sie ein neues Projekt erstellen und diesem ein neues DataSet-Element hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b1fe1d75673dc47f423cf398118230cd1530def0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866228"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Exemplarische Vorgehensweise: Erstellen eines Datasets mit dem DataSet-Designer

In dieser exemplarischen Vorgehensweise erstellen Sie ein DataSet mit dem **DataSet-Designer**. Der Artikel führt Sie durch den Prozess zum Erstellen eines neuen Projekts und zum Hinzufügen eines neuen **datasetelements** . Sie erfahren, wie Sie Tabellen basierend auf Tabellen in einer Datenbank erstellen, ohne einen Assistenten zu verwenden.

## <a name="prerequisites"></a>Voraussetzungen

In dieser exemplarischen Vorgehensweise werden SQL Server Express localdb-und Northwind-Beispieldatenbank verwendet.

1. Wenn Sie nicht über SQL Server Express localdb verfügen, installieren Sie es entweder über die [SQL Server Express Downloadseite](https://www.microsoft.com/sql-server/sql-server-editions-express)oder über das **Visual Studio-Installer**. Im Visual Studio-Installer können SQL Server Express localdb als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** oder als einzelne Komponente installiert werden.

2. Installieren Sie die Beispieldatenbank Northwind, indem Sie die folgenden Schritte ausführen:

    1. Öffnen Sie in Visual Studio das Fenster **SQL Server-Objekt-Explorer** . (SQL Server-Objekt-Explorer wird als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** im Visual Studio-Installer installiert.) Erweitern Sie den Knoten **SQL Server** . Klicken Sie mit der rechten Maustaste auf die localdb-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren Sie das [Northwind-Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Mit diesem T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript in den Abfrage-Editor ein, und klicken Sie dann auf die Schaltfläche **Ausführen** .

       Nach kurzer Zeit wird die Ausführung der Abfrage abgeschlossen, und die Datenbank Northwind wird erstellt.

## <a name="create-a-new-windows-forms-application-project"></a>Erstellen eines neuen Windows Forms-Anwendungsprojekts

1. Wählen Sie in Visual Studio im Menü **Datei** die Optionen **Neu** > **Projekt** aus.

2. Erweitern Sie entweder **Visual c#** oder **Visual Basic** im linken Bereich, und wählen Sie dann **Windows-Desktop** aus.

3. Wählen Sie im mittleren Bereich den **Windows Forms App** -Projekttyp aus.

4. Nennen Sie das Projekt **DatasetDesignerWalkthrough**, und wählen Sie dann **OK** aus.

     Visual Studio fügt das Projekt **Projektmappen-Explorer** hinzu und zeigt im Designer ein neues Formular an.

## <a name="add-a-new-dataset-to-the-application"></a>Hinzufügen eines neuen Datasets zur Anwendung

1. Wählen Sie im Menü **Projekt** den Eintrag **Neues Element hinzufügen** aus.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

2. Wählen Sie im linken Bereich **Daten** aus, und wählen Sie dann im mittleren Bereich **DataSet** aus.

3. Nennen Sie das DataSet **NorthwindDataSet**, und wählen Sie dann **Hinzufügen** aus.

     Visual Studio fügt dem Projekt eine Datei mit dem Namen " **NorthwindDataSet. xsd** " hinzu und öffnet Sie in der **DataSet-Designer**.

## <a name="create-a-data-connection-in-server-explorer"></a>Erstellen einer Datenverbindung in Server-Explorer

1. Klicken Sie im Menü **Ansicht** auf **Server-Explorer**.

2. Klicken Sie im **Server-Explorer** auf die Schaltfläche **Mit Datenbank verbinden**.

3. Erstellen Sie eine Verbindung mit der Beispieldatenbank Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Erstellen der Tabellen im DataSet

In diesem Abschnitt wird erläutert, wie Tabellen dem DataSet hinzugefügt werden.

### <a name="to-create-the-customers-table"></a>So erstellen Sie die Tabelle Customers

1. Erweitern Sie die Datenverbindung, die Sie im **Server-Explorer** erstellt haben, und erweitern Sie dann den Knoten **Tabellen**.

2. Ziehen Sie die Tabelle **Customers** aus dem **Server-Explorer** auf den **DataSet-Designer**.

     Dem Dataset werden die Datentabelle **Customers** und ein **CustomersTableAdapter** hinzugefügt.

### <a name="to-create-the-orders-table"></a>So erstellen Sie die Tabelle Orders

- Ziehen Sie die Tabelle **Orders** aus dem **Server-Explorer** auf den **DataSet-Designer**.

     Dem Dataset werden die Datentabelle **Orders**, ein **OrdersTableAdapter** und eine Datenbeziehung zwischen den Tabellen **Customers** und **Orders** hinzugefügt.

### <a name="to-create-the-orderdetails-table"></a>So erstellen Sie die Tabelle OrderDetails

- Ziehen Sie die Tabelle **Order Details** aus dem **Server-Explorer** auf den **DataSet-Designer**.

     Dem Dataset werden die Datentabelle **Order Details** , **orderdetailstableadapter** und eine Daten Beziehung zwischen den Tabellen **Orders** und **Order Details** hinzugefügt.

## <a name="next-steps"></a>Nächste Schritte

- Speichern Sie das DataSet.

- Wählen Sie im Fenster **Datenquellen** Elemente aus, und ziehen Sie sie auf ein Formular. Weitere Informationen finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- Fügen Sie den TableAdapters weitere Abfragen hinzu.

- Fügen Sie dem <xref:System.Data.DataTable.ColumnChanging>-Ereignis oder dem <xref:System.Data.DataTable.RowChanging>-Ereignis der im Dataset enthaltenen Datentabellen Anweisungen für eine Validierung hinzu. Weitere Informationen finden Sie unter Überprüfen von [Daten in Datasets](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Weitere Informationen

- [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Überprüfen von Daten](../data-tools/validate-data-in-datasets.md)
