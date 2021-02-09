---
title: Behandeln einer Parallelitätsausnahme
description: Behandeln Sie eine neben läufigkeits Ausnahme (System. Data. DBAN-cyexception), die ausgelöst wird, wenn zwei Benutzer gleichzeitig versuchen, dieselben Daten in einer Datenbank zu ändern.
ms.custom: SEO-VS-2020
ms.date: 09/11/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c410d9290b7e377654a9cff87f8df7524a1b7149
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866878"
---
# <a name="handle-a-concurrency-exception"></a>Behandeln einer Parallelitätsausnahme

Parallelitätsausnahmen (<xref:System.Data.DBConcurrencyException?displayProperty=fullName>) werden ausgelöst, wenn zwei Benutzer gleichzeitig versuchen, dieselben Daten in einer Datenbank zu ändern. In dieser exemplarischen Vorgehensweise erstellen Sie eine Windows-Anwendung, die veranschaulicht, wie Sie ein Abfangen <xref:System.Data.DBConcurrencyException> , die Zeile, die den Fehler verursacht hat, finden und eine Strategie zur Behandlung der Anwendung erlernen.

Diese exemplarische Vorgehensweise enthält folgende Vorgänge:

1. Erstellen Sie ein neues **Windows Forms-Anwendungs** Projekt.

2. Erstellen Sie ein neues DataSet, das auf der Northwind-Kunden Tabelle basiert.

3. Erstellen eines Formulars mit einer <xref:System.Windows.Forms.DataGridView> für die Anzeige der Daten.

4. Füllen Sie ein DataSet mit Daten aus der Customers-Tabelle in der Northwind-Datenbank aus.

5. Verwenden Sie das Feature **Tabellendaten anzeigen** in **Server-Explorer** , um auf die Daten der Kunden Tabelle zuzugreifen und einen Datensatz zu ändern.

6. Ändern Sie denselben Datensatz in einen anderen Wert, aktualisieren Sie das DataSet, und versuchen Sie, die Änderungen in die Datenbank zu schreiben, was zu einem Parallelitäts Fehler führt.

7. Fangen Sie den Fehler ab, und zeigen Sie anschließend die verschiedenen Versionen des Datensatzes an, um festzulegen, ob die Aktualisierung der Datenbank fortgesetzt oder abgebrochen werden soll.

## <a name="prerequisites"></a>Voraussetzungen

In dieser exemplarischen Vorgehensweise werden SQL Server Express localdb-und Northwind-Beispieldatenbank verwendet.

1. Wenn Sie nicht über SQL Server Express localdb verfügen, installieren Sie es entweder über die [SQL Server Express Downloadseite](https://www.microsoft.com/sql-server/sql-server-editions-express)oder über das **Visual Studio-Installer**. Im **Visual Studio-Installer** können Sie SQL Server Express localdb als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** oder als einzelne Komponente installieren.

2. Installieren Sie die Beispieldatenbank Northwind, indem Sie die folgenden Schritte ausführen:

    1. Öffnen Sie in Visual Studio das Fenster **SQL Server-Objekt-Explorer** . (SQL Server-Objekt-Explorer wird als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** im Visual Studio-Installer installiert.) Erweitern Sie den Knoten **SQL Server** . Klicken Sie mit der rechten Maustaste auf die localdb-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren Sie das [Northwind-Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Mit diesem T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript in den Abfrage-Editor ein, und klicken Sie dann auf die Schaltfläche **Ausführen** .

       Nach kurzer Zeit wird die Ausführung der Abfrage abgeschlossen und die Datenbank Northwind erstellt.

## <a name="create-a-new-project"></a>Erstellen eines neuen Projekts

Erstellen Sie zunächst eine neue Windows Forms Anwendung:

1. Wählen Sie in Visual Studio im Menü **Datei** die Optionen **Neu** > **Projekt** aus.

2. Erweitern Sie entweder **Visual c#** oder **Visual Basic** im linken Bereich, und wählen Sie dann **Windows-Desktop** aus.

3. Wählen Sie im mittleren Bereich den **Windows Forms App** -Projekttyp aus.

4. Nennen Sie das **Projekt,** und wählen Sie dann **OK** aus.

     Das **Projekt "** Projekt" wird erstellt und zu **Projektmappen-Explorer** hinzugefügt, und im Designer wird ein neues Formular geöffnet.

## <a name="create-the-northwind-dataset"></a>Erstellen des Northwind-Datasets

Erstellen Sie als nächstes ein DataSet mit dem Namen **NorthwindDataSet**:

1. Wählen Sie im Menü **Daten** die Option **neue Datenquelle hinzufügen** aus.

   Der Assistent zum Konfigurieren von Datenquellen wird geöffnet.

2. Wählen Sie auf dem Bildschirm **Daten Quellentyp auswählen** die Option **Datenbank** aus.

   ![Assistent zum Konfigurieren von Datenquellen in Visual Studio](media/data-source-configuration-wizard.png)

3. Wählen Sie in der Liste der verfügbaren Verbindungen eine Verbindung mit der Beispieldatenbank Northwind aus. Wenn die Verbindung in der Liste der Verbindungen nicht verfügbar ist, wählen Sie **neue Verbindung** aus.

    > [!NOTE]
    > Wenn Sie eine Verbindung mit einer lokalen Datenbankdatei herstellen, wählen Sie **Nein** aus, wenn Sie gefragt werden, ob Sie die Datei dem Projekt hinzufügen möchten.

4. Wählen Sie auf der Seite **Verbindungs Zeichenfolge in der Anwendungs Konfigurationsdatei speichern** die Option **weiter** aus.

5. Erweitern Sie den Knoten **Tabellen** , und wählen Sie die Tabelle **Customers** aus. Der Standardname für das DataSet sollte **NorthwindDataSet** lauten.

6. Wählen Sie **Fertig** stellen aus, um das DataSet dem Projekt hinzuzufügen.

## <a name="create-a-data-bound-datagridview-control"></a>Erstellen eines Daten gebundenen DataGridView-Steuer Elements

In diesem Abschnitt erstellen Sie einen, <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> indem Sie das **Customers** -Element aus dem **Datenquellen** Fenster auf das Windows Form ziehen.

1. Um das Fenster **Datenquellen** zu öffnen, wählen Sie im Menü **Daten** die Option **Datenquellen anzeigen** aus.

2. Erweitern Sie im Fenster **Datenquellen** den Knoten **NorthwindDataSet** , und wählen Sie dann die Tabelle **Customers** aus.

3. Wählen Sie im Tabellen Knoten den Pfeil nach unten aus, und wählen Sie dann in der Dropdown Liste die Option **DataGridView** aus.

4. Ziehen Sie die Tabelle auf einen leeren Bereich des Formulars.

     Ein <xref:System.Windows.Forms.DataGridView> Steuerelement mit dem Namen **CustomersDataGridView** und ein mit <xref:System.Windows.Forms.BindingNavigator> dem Namen **CustomersBindingNavigator** werden dem Formular hinzugefügt, das an das-Element gebunden ist <xref:System.Windows.Forms.BindingSource> . Dies wird wiederum an die Customers-Tabelle im NorthwindDataSet gebunden.

## <a name="test-the-form"></a>Testen des Formulars

Sie können das Formular jetzt testen, um sicherzustellen, dass das Verhalten bisher wie erwartet ausfällt:

1. Drücken Sie **F5** , um die Anwendung auszuführen.

     Das Formular wird mit einem-Steuerelement angezeigt <xref:System.Windows.Forms.DataGridView> , das mit Daten aus der Customers-Tabelle gefüllt ist.

2. Klicken Sie im Menü **Debuggen** auf **Stop Debugging** (Debuggen beenden).

## <a name="handle-concurrency-errors"></a>Behandeln von Parallelitäts Fehlern

Wie Sie Fehler behandeln, hängt von den spezifischen Geschäftsregeln ab, die Ihre Anwendung steuern. In dieser exemplarischen Vorgehensweise verwenden wir die folgende Strategie als Beispiel für die Behandlung des Parallelitäts Fehlers.

Die Anwendung zeigt dem Benutzer drei Versionen des Datensatzes:

- Den aktuellen Datensatz in der Datenbank

- Der ursprüngliche Datensatz, der in das DataSet geladen wird.

- Die vorgeschlagenen Änderungen im Dataset

Der Benutzer kann dann die Datenbank mit der vorgeschlagenen Version überschreiben oder aber die Aktualisierung abbrechen und das Dataset mit den neuen Werten aus der Datenbank aktualisieren.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>So aktivieren Sie die Behandlung von Parallelitätsfehlern

1. Erstellen Sie einen benutzerdefinierten Fehlerhandler.

2. Zeigen Sie die Auswahloptionen für den Benutzer an.

3. Verarbeiten Sie die Eingabe des Benutzers.

4. Senden Sie die Aktualisierung erneut, oder setzen Sie die Daten im Dataset zurück.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Hinzufügen von Code zur Behandlung der Parallelitäts Ausnahme

Wenn Sie versuchen, ein Update auszuführen, und eine Ausnahme ausgelöst wird, sollten Sie in der Regel mit den Informationen arbeiten, die von der ausgelöste Ausnahme bereitgestellt werden. In diesem Abschnitt fügen Sie Code hinzu, mit dem versucht wird, die Datenbank zu aktualisieren. Außerdem werden alle ausgelösten <xref:System.Data.DBConcurrencyException> und anderen Ausnahmen behandelt.

> [!NOTE]
> Die `CreateMessage` `ProcessDialogResults` Methoden und werden später in der exemplarischen Vorgehensweise hinzugefügt.

1. Fügen Sie unter der `Form1_Load`-Methode folgenden Code hinzu:

   [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
   [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2. Ersetzen Sie die `CustomersBindingNavigatorSaveItem_Click`-Methode, um die `UpdateDatabase`-Methode aufzurufen, sodass sich Folgendes ergibt:

   [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
   [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Anzeigen der Auswahloptionen für den Benutzer

Durch den soeben geschriebenen Code wird die `CreateMessage`-Prozedur aufgerufen, um Fehlerinformationen für den Benutzer anzuzeigen. In dieser exemplarischen Vorgehensweise verwenden Sie ein Meldungs Feld, um die verschiedenen Versionen des Datensatzes für den Benutzer anzuzeigen. Dadurch kann der Benutzer auswählen, ob der Datensatz mit den Änderungen überschrieben oder der Bearbeitungsvorgang abgebrochen werden soll. Wenn der Benutzer durch Klicken auf eine Schaltfläche eine Option im Meldungsfeld ausgewählt hat, wird die Antwort an die `ProcessDialogResult`-Methode übergeben.

Erstellen Sie die Meldung, indem Sie dem **Code-Editor** folgenden Code hinzufügen. Geben Sie diesen Code unter der `UpdateDatabase`-Methode ein:

[!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
[!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Verarbeiten der Antwort des Benutzers

Außerdem benötigen Sie Code, um die Antwort des Benutzers auf das Meldungs Feld zu verarbeiten. Die Optionen lauten entweder, um den aktuellen Datensatz in der Datenbank mit der vorgeschlagenen Änderung zu überschreiben, oder die lokalen Änderungen verwerfen und die Datentabelle mit dem Datensatz aktualisieren, der sich derzeit in der Datenbank befindet. Wenn der Benutzer **Ja** auswählt, <xref:System.Data.DataTable.Merge%2A> wird die-Methode aufgerufen, wobei das *preserveChanges* -Argument auf **true** festgelegt ist. Dies bewirkt, dass der Aktualisierungs Versuch erfolgreich ist, da die ursprüngliche Version des Datensatzes jetzt mit dem Datensatz in der Datenbank übereinstimmt.

Fügen Sie unter dem Code, der im vorherigen Abschnitt hinzugefügt wurde, den folgenden Code hinzu:

[!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
[!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form-behavior"></a>Testen des Formular Verhaltens

Sie können das Formular jetzt testen, um sicherzustellen, dass das Verhalten wie erwartet ausfällt. Um eine Parallelitäts Verletzung zu simulieren, ändern Sie die Daten in der Datenbank nach dem Auffüllen von NorthwindDataSet.

1. Drücken Sie **F5** , um die Anwendung auszuführen.

2. Wenn das Formular angezeigt wird, führen Sie es weiterhin, und wechseln Sie zur Visual Studio-IDE.

3. Wählen Sie im Menü **Ansicht** den Eintrag **Server-Explorer** aus.

4. Erweitern Sie im **Server-Explorer** die Verbindung, die von der Anwendung verwendet wird, und erweitern Sie den Knoten **Tabellen**.

5. Klicken Sie mit der rechten Maustaste auf die Tabelle **Customers** , und wählen Sie dann **Tabellendaten anzeigen** aus.

6. Ändern Sie im ersten Datensatz (**ALFKI**) **ContactName** in **Maria Anders2**.

    > [!NOTE]
    > Navigieren Sie zu einer anderen Zeile, um einen Commit für die Änderung auszuführen.

7. Wechseln Sie in das laufende Formular von "Configuration Manager Walkthrough".

8. Ändern Sie im ersten Datensatz im Formular (**ALFKI**) **ContactName** in **Maria Anders1**.

9. Wählen Sie die Schaltfläche **Speichern** aus.

     Der Parallelitätsfehler wird ausgelöst, und das Meldungsfeld wird angezeigt.

   Wenn Sie **Nein** auswählen, wird das Update abgebrochen, und das DataSet wird mit den Werten aktualisiert, die derzeit in der Datenbank gespeichert sind. Wenn Sie **Ja** auswählen, wird der vorgeschlagene Wert in die Datenbank geschrieben.

## <a name="see-also"></a>Weitere Informationen

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
