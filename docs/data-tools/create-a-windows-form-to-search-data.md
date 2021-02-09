---
title: Erstellen eines Windows Forms zum Suchen von Daten
description: Hier finden Sie ein Beispiel zum Erstellen eines Windows Forms zum Durchsuchen von Daten. Erstellen Sie die Windows Form-Anwendung, die Datenquelle und das Formular. Parametrisierung hinzufügen. Testen der App.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: eb6e5a1ba304627c08828b6ad7bff7f6accd3980
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859111"
---
# <a name="create-a-windows-form-to-search-data"></a>Erstellen eines Windows Forms zum Suchen von Daten

Es kommt häufig vor, dass ausgewählte Daten auf einem Formular angezeigt werden, Angenommen, Sie möchten die Bestellungen für einen bestimmten Kunden oder die Details für eine bestimmte Bestellung anzeigen. In diesem Szenario gibt der Benutzer zunächst Informationen in ein Formular ein. Anschließend wird eine Abfrage mit der Eingabe des Benutzers als Parameter ausgeführt, d. h. die Daten werden auf der Grundlage einer parametrisierten Abfrage ausgewählt. Die Abfrage gibt nur die Daten zurück, die den vom Benutzer eingegebenen Kriterien entsprechen. Diese exemplarische Vorgehensweise veranschaulicht das Erstellen einer Abfrage, die Kunden in einer bestimmten Stadt zurückgibt, sowie das Anpassen der Benutzeroberfläche, damit Benutzer eine Stadt eingeben und zum Ausführen der Abfrage auf eine Schaltfläche klicken können.

Durch die Verwendung parametrisierter Abfragen wird die Effizienz der Anwendung erhöht, weil die Datenbank die Arbeit ausführt, für die sie optimiert ist, nämlich die schnelle Filterung von Datensätzen. Wenn Sie dagegen eine ganze Datenbanktabelle anfordern, sie über das Netzwerk übertragen und dann mit der Anwendungslogik die gewünschten Datensätze suchen, wird die Anwendung langsam und ineffizient.

Mit dem Dialogfeld **Suchkriterien** -Generator können Sie einem beliebigen TableAdapter (und Steuerelementen, die Parameterwerte akzeptieren und die Abfrage ausführen) parametrisierte Abfragen hinzufügen. Öffnen Sie das Dialogfeld, indem Sie im Menü **Daten** (bzw. in einem TableAdapter-Smarttag) den Befehl **Abfrage hinzufügen** auswählen.

In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:

- Erstellen und Konfigurieren der Datenquelle in der Anwendung mit dem Assistenten zum Konfigurieren von **Datenquellen** .

- Legen Sie den Ablagetyp für die Elemente im **Datenquellen** Fenster fest.

- Erstellen von Steuerelementen, mit denen Daten angezeigt werden, indem Elemente aus dem **Datenquellenfenster** auf ein Formular gezogen werden.

- Hinzufügen von Steuerelementen zum Anzeigen der Daten auf dem Formular.

- Das Dialogfeld **Suchkriterien** -Generator wird abgeschlossen.

- Eingeben von Parametern in das Formular und Ausführen der parametrisierten Abfrage.

## <a name="prerequisites"></a>Voraussetzungen

In dieser exemplarischen Vorgehensweise werden SQL Server Express localdb-und Northwind-Beispieldatenbank verwendet.

1. Wenn Sie nicht über SQL Server Express localdb verfügen, installieren Sie es entweder über die [SQL Server Express Downloadseite](https://www.microsoft.com/sql-server/sql-server-editions-express)oder über das **Visual Studio-Installer**. Im **Visual Studio-Installer** können Sie SQL Server Express localdb als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** oder als einzelne Komponente installieren.

2. Installieren Sie die Beispieldatenbank Northwind, indem Sie die folgenden Schritte ausführen:

    1. Öffnen Sie in Visual Studio das Fenster **SQL Server-Objekt-Explorer** . (SQL Server-Objekt-Explorer wird als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** im **Visual Studio-Installer** installiert.) Erweitern Sie den Knoten **SQL Server** . Klicken Sie mit der rechten Maustaste auf die localdb-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren Sie das [Northwind-Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Mit diesem T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript in den Abfrage-Editor ein, und klicken Sie dann auf die Schaltfläche **Ausführen** .

       Nach kurzer Zeit wird die Ausführung der Abfrage abgeschlossen und die Datenbank Northwind erstellt.

## <a name="create-the-windows-forms-application"></a>Erstellen der Windows Forms Anwendung

Erstellen Sie ein neues **Windows Forms-App** -Projekt für c# oder Visual Basic. Weisen Sie dem Projekt den Namen **WindowsSearchForm** zu.

## <a name="create-the-data-source"></a>Erstellen der Datenquelle

Bei diesem Schritt wird eine Datenquelle aus einer Datenbank erstellt. Hierbei wird der **Assistent zum Konfigurieren von Datenquellen** verwendet:

1. Um das Fenster **Datenquellen** zu öffnen, klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

2. Wählen Sie im **Datenquellen** Fenster die Option **neue Datenquelle hinzufügen** aus, um den Assistenten zum **Konfigurieren von Datenquellen** zu starten.

3. Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.

4. Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** einen der folgenden Schritte aus:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

    - Klicken Sie auf **Neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu öffnen.

5. Falls die Datenbank ein Kennwort erfordern sollte, aktivieren Sie die Option für die Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.

6. Klicken Sie auf der Seite **Save connection string to the Application Configuration file** (Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern) auf **Weiter**.

7. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.

8. Wählen Sie die Tabelle **Customers** aus, und klicken Sie anschließend auf **Fertig stellen**.

     **NorthwindDataSet** wird dem Projekt hinzugefügt, und die **Customers**-Tabelle wird im **Datenquellenfenster** angezeigt.

## <a name="create-the-form"></a> Erstellen eines Formulars

Sie können die Daten gebundenen Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellen** Fenster auf das Formular ziehen:

1. Erweitern Sie im **Datenquellenfenster** den Knoten **Customers**.

2. Ziehen Sie den Knoten **Customers** aus dem **Datenquellenfenster** auf das Formular.

     Auf dem Formular werden <xref:System.Windows.Forms.DataGridView> und ein ToolStrip-Element (<xref:System.Windows.Forms.BindingNavigator>) angezeigt, mit denen Sie durch die Datensätze auf dem Formular navigieren können. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Hinzufügen der Parametrisierung (Suchfunktion) zur Abfrage

Mit dem Dialogfeld **Suchkriterien** -Generator können Sie der ursprünglichen Abfrage eine WHERE-Klausel hinzufügen:

1. Wählen Sie das Steuerelement <xref:System.Windows.Forms.DataGridView> aus. Wählen Sie anschließend im Menü **Daten** die Option **Abfrage hinzufügen** aus.

2. Geben Sie im Dialogfeld **Suchkriterien** -Generator im Bereich **neuer Abfrage Name den Namen** **FillByCity** ein.

3. Fügen Sie der Abfrage im Bereich **Abfragetext** die Zeichenfolge `WHERE City = @City` hinzu.

     Die Abfrage müsste ungefähr wie folgt aussehen:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Zugriffs-und OLE DB Datenquellen verwenden das Fragezeichen ('? ') zum Angeben von Parametern, sodass die WHERE-Klausel wie folgt aussieht: `WHERE City = ?` .

4. Klicken Sie auf **OK**, um das Dialogfeld **Suchkriterien-Generator** zu schließen.

     Dem Formular wird ein **FillByCityToolStrip** hinzugefügt.

## <a name="test-the-application"></a>Testen der Anwendung

Wenn Sie die Anwendung ausführen, wird das Formular geöffnet, und der Parameter wird als Eingabe bereit genommen:

1. Drücken Sie **F5**, um die Anwendung auszuführen.

2. Geben Sie **London** in das Textfeld **City** ein, und klicken Sie dann auf **FillByCity**.

     Das Datenraster wird mit Kunden aufgefüllt, die die Kriterien erfüllen. In diesem Beispiel zeigt das Datenraster nur Kunden an, die den Wert **London** in der Spalte **City** aufweisen.

## <a name="next-steps"></a>Nächste Schritte

Je nach den Anforderungen der Anwendung können nach dem Erstellen eines parametrisierten Formulars weitere Schritte sinnvoll sein. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:

- Hinzufügen von Steuerelementen, die verknüpfte Daten anzeigen. Weitere Informationen finden Sie unter [Beziehungen in Datasets](relationships-in-datasets.md).

- Hinzufügen oder Entfernen von Datenbankobjekten aus dem Dataset durch Bearbeiten. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
