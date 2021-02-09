---
title: Erstellen einer Datenbankdatei und Verwenden des Tabellen-Designers
description: Tutorial, in dem das Hinzufügen von Tabellen und Fremdschlüsseln zu einer Datenbank mithilfe Tabellen-Designer in Visual Studio beschrieben wird. Außerdem wird gezeigt, wie Daten über die grafische Benutzeroberfläche hinzugefügt werden.
ms.date: 09/19/2019
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ed0df13f1dd281fcf56056809419af5d7ed6d3dc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867203"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Create a database and add tables in Visual Studio (Erstellen einer Datenbank und Hinzufügen von Tabellen in Visual Studio)

Sie können Visual Studio verwenden, um eine lokale Datenbankdatei in SQL Server Express localdb zu erstellen und zu aktualisieren. Sie können auch eine Datenbank erstellen, indem Sie Transact-SQL-Anweisungen im **SQL Server-Objekt-Explorer** Tool Fenster in Visual Studio ausführen. In diesem Thema erstellen wir eine *MDF* -Datei und fügen Tabellen und Schlüssel hinzu, indem wir die Tabellen-Designer verwenden.

## <a name="prerequisites"></a>Voraussetzungen

Um diese exemplarische Vorgehensweise abzuschließen, benötigen Sie die in Visual Studio installierten Workloads für die **.net-Desktop Entwicklung** und die **Datenspeicherung und-Verarbeitung** . Um Sie zu installieren, öffnen Sie **Visual Studio-Installer** , und wählen Sie **ändern** (oder **mehr**  >  **ändern**) neben der Version von Visual Studio aus, die Sie ändern möchten.

> [!NOTE]
> Die Verfahren in diesem Artikel gelten nur für .NET Framework Windows Forms-Projekte, nicht für .net Core-Windows Forms-Projekte.

## <a name="create-a-project-and-a-local-database-file"></a>Erstellen eines Projekts und einer lokalen Datenbankdatei

1. Erstellen Sie ein neues Projekt **Windows Forms app (.NET Framework)** , und nennen Sie es **SampleDatabaseWalkthrough**.

2. Wählen Sie in der Menüleiste die Option **Projekt**  >  **Neues Element hinzufügen** aus.

3. Scrollen Sie in der Liste der Element Vorlagen nach unten, und wählen Sie **Dienst basierte Datenbank** aus.

   ![Dialogfeld "Elementvorlagen"](../data-tools/media/raddata-vsitemtemplates.png)

4. Nennen Sie die Datenbank **SampleDatabase**, und klicken Sie dann auf **Hinzufügen**.

### <a name="add-a-data-source"></a>Hinzufügen einer Datenquelle

1. Wenn das **Datenquellen** Fenster nicht geöffnet ist, öffnen Sie es, indem Sie **UMSCHALT** + **alt** + **D** drücken oder   >  in der Menüleiste **andere Windows**-  >  **Datenquellen** anzeigen auswählen.

1. Wählen Sie im **Datenquellen** Fenster die Option **neue Datenquelle hinzufügen** aus.

   ![Hinzufügen einer neuen Datenquelle in Visual Studio](media/add-new-data-source.png)

   Der **Assistent zum Konfigurieren von Datenquellen** wird geöffnet.

1. Wählen Sie auf der Seite **Daten Quellentyp auswählen** die Option **Datenbank** aus, und klicken Sie dann auf **weiter**.

1. Wählen Sie auf der Seite **Datenbankmodell auswählen** die Option **weiter** aus, um die Standardeinstellung (DataSet) zu übernehmen.

1. Wählen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** aus die Datei **SampleDatabase. mdf** in der Dropdown Liste aus, und klicken Sie dann auf **weiter**.

1. Wählen Sie auf der Seite **Verbindungs Zeichenfolge in der Anwendungs Konfigurationsdatei speichern die** Option **weiter** aus.

1. Auf der Seite **Datenbankobjekte auswählen** sehen Sie eine Meldung, die besagt, dass die Datenbank keine Objekte enthält. Klicken Sie auf **Fertig stellen**.

### <a name="view-properties-of-the-data-connection"></a>Anzeigen der Eigenschaften der Datenverbindung

Sie können die Verbindungs Zeichenfolge für die Datei *SampleDatabase. mdf* anzeigen, indem Sie die Eigenschaftenfenster der Datenverbindung öffnen:

- Wählen Sie  >  **SQL Server-Objekt-Explorer** Ansicht aus, um das Fenster **SQL Server-Objekt-Explorer** zu öffnen. Erweitern Sie **(localdb) \mssqllocaldb**  >  -**Datenbanken**, klicken Sie mit der rechten Maustaste auf *SampleDatabase. mdf* , und wählen Sie **Eigenschaften** aus.

- Sie können auch **View**  >  **Server-Explorer** auswählen, wenn dieses Fenster nicht bereits geöffnet ist. Öffnen Sie die Eigenschaftenfenster, indem Sie den Knoten **Datenverbindungen** erweitern, klicken Sie mit der rechten Maustaste auf *SampleDatabase. mdf*, und wählen Sie dann **Eigenschaften** aus.

  > [!TIP]
  > Wenn Sie den Knoten Datenverbindungen nicht erweitern können oder die Verbindung SampleDatabase. mdf nicht aufgeführt ist, wählen Sie auf der Server-Explorer Symbolleiste die Schaltfläche **Verbindung mit Datenbank herstellen** aus. Stellen Sie im Dialogfeld **Verbindung hinzufügen** sicher, dass unter **Datenquelle** **Microsoft SQL Server Datenbankdatei** ausgewählt ist, und wählen Sie dann die Datei SampleDatabase. mdf aus, und wählen Sie Sie aus. Schließen Sie die Verbindung hinzu, indem Sie auf **OK klicken**.

## <a name="create-tables-and-keys-by-using-table-designer"></a>Erstellen von Tabellen und Schlüsseln mit Tabellen-Designer

In diesem Abschnitt erstellen Sie zwei Tabellen, einen Primärschlüssel in jeder Tabelle und einige Zeilen mit Beispiel Daten. Außerdem erstellen Sie einen Fremdschlüssel, um anzugeben, wie Datensätze in einer Tabelle den Datensätzen in der anderen Tabelle entsprechen.

### <a name="create-the-customers-table"></a>Erstellen der Tabelle "Customers"

1. Erweitern Sie in **Server-Explorer** den Knoten **Datenverbindungen** , und erweitern Sie dann den Knoten **SampleDatabase. mdf** .

   Wenn Sie den Knoten Datenverbindungen nicht erweitern können oder die Verbindung SampleDatabase. mdf nicht aufgeführt ist, wählen Sie auf der Server-Explorer Symbolleiste die Schaltfläche **Verbindung mit Datenbank herstellen** aus. Stellen Sie im Dialogfeld **Verbindung hinzufügen** sicher, dass unter **Datenquelle** **Microsoft SQL Server Datenbankdatei** ausgewählt ist, und wählen Sie dann die Datei SampleDatabase. mdf aus, und wählen Sie Sie aus. Schließen Sie die Verbindung hinzu, indem Sie auf **OK klicken**.

2. Klicken Sie mit der rechten Maustaste auf **Tabellen** , und wählen Sie **neue Tabelle hinzufügen**

   Der Tabellen-Designer wird geöffnet und zeigt ein Raster mit einer standardmäßigen Zeile an, die eine einzelne Spalte in der Tabelle darstellt, die Sie erstellen. Durch Hinzufügen von Zeilen zum Raster fügen Sie zusätzliche Spalten in der Tabelle hinzu.

3. Im Raster fügen Sie eine Zeile für jeden der folgenden Einträge hinzu:

   |Spaltenname|Datentyp|NULL zulassen|
   |-----------------|---------------|-----------------|
   |`CustomerID`|`nchar(5)`|False (gelöscht)|
   |`CompanyName`|`nvarchar(50)`|False (gelöscht)|
   |`ContactName`|`nvarchar (50)`|True (ausgewählt)|
   |`Phone`|`nvarchar (24)`|True (ausgewählt)|

4. Klicken Sie mit der rechten Maustaste auf die `CustomerID` Zeile, und wählen Sie dann **Primärschlüssel festlegen** aus.

5. Klicken Sie mit der rechten Maustaste auf die Standardzeile ( `Id` ), und wählen Sie dann **Löschen** aus.

6. Benennen Sie die Tabelle "Customers", indem Sie die erste Zeile im Skriptbereich entsprechend dem folgenden Beispiel aktualisieren:

   ```sql
   CREATE TABLE [dbo].[Customers]
   ```

   Die Ausgabe sollte in etwa wie folgt aussehen:

   ![Tabellen-Designer](../data-tools/media/table-designer.png)

7. Wählen Sie in der oberen linken Ecke **Tabellen-Designer** die Option **Aktualisieren** aus.

8. Wählen Sie im Dialogfeld **Vorschau der Daten Bank Updates** die Option **Datenbank aktualisieren** aus.

   Die Customers-Tabelle wird in der lokalen Datenbankdatei erstellt.

### <a name="create-the-orders-table"></a>Erstellen der Tabelle "Orders"

1. Fügen Sie eine weitere Tabelle hinzu, und fügen Sie dann in der folgenden Tabelle eine Zeile für jeden Eintrag hinzu:

   |Spaltenname|Datentyp|NULL zulassen|
   |-----------------|---------------|-----------------|
   |`OrderID`|`int`|False (gelöscht)|
   |`CustomerID`|`nchar(5)`|False (gelöscht)|
   |`OrderDate`|`datetime`|True (ausgewählt)|
   |`OrderQuantity`|`int`|True (ausgewählt)|

2. Legen Sie **OrderID** als Primärschlüssel fest, und löschen Sie dann die Standardzeile.

3. Benennen Sie die Tabelle "Orders", indem Sie die erste Zeile im Skriptbereich entsprechend dem folgenden Beispiel aktualisieren:

   ```sql
   CREATE TABLE [dbo].[Orders]
   ```

4. Wählen Sie in der oberen linken Ecke des **Tabellen-Designer** die Option **Aktualisieren** aus.

5. Wählen Sie im Dialogfeld **Vorschau der Daten Bank Updates** die Option **Datenbank aktualisieren** aus.

   Die Tabelle Orders wird in der lokalen Datenbankdatei erstellt. Wenn Sie den Knoten **Tabellen** in Server-Explorer erweitern, werden die beiden Tabellen angezeigt:

   ![Tabellen Knoten erweitert in Server-Explorer](media/server-explorer-tables-node.png)

### <a name="create-a-foreign-key"></a>Erstellen eines fremd Schlüssels

1. Klicken Sie im Kontext Bereich auf der rechten Seite des Tabellen-Designer Rasters für die Tabelle Orders mit der rechten Maustaste auf **Fremdschlüssel** , und wählen Sie **neuen Fremdschlüssel hinzufügen** aus.

   ![Hinzufügen eines fremd Schlüssels in Tabellen-Designer in Visual Studio](../data-tools/media/add-foreign-key.png)

2. Ersetzen Sie im angezeigten Textfeld den Text **ToTable** durch **Customers**.

3. Aktualisieren Sie im Bereich T-SQL die letzte Zeile, sodass Sie mit dem folgenden Beispiel übereinstimmt:

   ```sql
   CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
   ```

4. Wählen Sie in der oberen linken Ecke des **Tabellen-Designer** die Option **Aktualisieren** aus.

5. Wählen Sie im Dialogfeld **Vorschau der Daten Bank Updates** die Option **Datenbank aktualisieren** aus.

   Der Fremdschlüssel wird erstellt.

## <a name="populate-the-tables-with-data"></a>Auffüllen der Tabellen mit Daten

1. Erweitern Sie in **Server-Explorer** oder **SQL Server-Objekt-Explorer** den Knoten für die Beispieldatenbank.

2. Öffnen Sie das Kontextmenü für den Knoten **Tabellen** , wählen Sie **Aktualisieren** aus, und erweitern Sie dann den Knoten **Tabellen** .

3. Öffnen Sie das Kontextmenü für die Tabelle Customers, und wählen Sie dann **Tabellendaten anzeigen** aus.

4. Fügen Sie für einige Kunden die gewünschten Daten hinzu.

    Sie können fünf beliebige Zeichen für die Kunden-IDs angeben, wählen Sie aber mindestens eine aus, an die Sie sich noch erinnern können, um sie später in dieser Prozedur zu verwenden.

5. Öffnen Sie das Kontextmenü für die Tabelle Orders, und wählen Sie dann **Tabellendaten anzeigen** aus.

6. Fügen Sie Daten für einige Aufträge hinzu.

    > [!IMPORTANT]
    > Überprüfen Sie, ob alle Bestellnummern und -mengen ganze Zahlen sind und ob jede Kunden-ID mit einem Wert übereinstimmt, den Sie in der Spalte **CustomerID** in der Tabelle „Customers“ angegeben haben.

7. Klicken Sie in der Menüleiste auf **Datei**  >  **Alle speichern**.

## <a name="see-also"></a>Weitere Informationen

- [Zugreifen auf Daten in Visual Studio](accessing-data-in-visual-studio.md)
