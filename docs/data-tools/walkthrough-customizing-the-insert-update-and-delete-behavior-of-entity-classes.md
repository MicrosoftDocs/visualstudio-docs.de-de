---
title: Anpassen von Insert/Update/Delete-Verhalten
description: Passen Sie in dieser exemplarischen Vorgehensweise das Einfüge-, Aktualisierungs-und Lösch Verhalten von Entitäts Klassen mithilfe der LINQ (Language-Integrated Query) in SQL-Tools in Visual Studio an.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cac9f27263fc7d316d308f1f8d906751f419f104
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94997926"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>Exemplarische Vorgehensweise: Anpassen des Einfüge-, Aktualisierungs-und Lösch Verhaltens von Entitäts Klassen

Die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) stellen eine visuelle Entwurfs Oberfläche zum Erstellen und Bearbeiten von LINQ to SQL Klassen (Entitäts Klassen) bereit, die auf Objekten in einer Datenbank basieren. Mithilfe [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)können Sie die LINQ-Technologie verwenden, um auf SQL-Datenbanken zuzugreifen. Weitere Informationen finden Sie unter [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/).

Standardmäßig wird die Logik zum Durchführen von Updates durch die LINQ to SQL-Laufzeit bereitgestellt. Die Laufzeit erstellt die `Insert` Standard `Update` -,-und- `Delete` Anweisungen auf der Grundlage des Schemas der Tabelle (Spaltendefinitionen und Primärschlüssel Informationen). Wenn Sie das Standardverhalten nicht verwenden möchten, können Sie das Updateverhalten konfigurieren und für erforderliche Einfüge-, Update- und Löschvorgänge, die für das Arbeiten mit Daten in der Datenbank notwendig sind, spezielle gespeicherte Prozeduren festlegen. Diese Vorgehensweise ist auch dann sinnvoll, wenn kein Standardverhalten erzeugt wird, z. B. wenn die Entitätsklassen Ansichten zugeordnet sind. Das standardmäßige Updateverhalten kann auch dann überschrieben werden, wenn für die Datenbank der Tabellenzugriff über gespeicherte Prozeduren erforderlich ist. Weitere Informationen finden Sie unter [Anpassen von Vorgängen mithilfe von gespeicherten Prozeduren](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> Für diese exemplarische Vorgehensweise ist die Verfügbarkeit der gespeicherten Prozeduren **InsertCustomer**, **UpdateCustomer** und **DeleteCustomer** für die Datenbank „Northwind“ erforderlich.

Diese exemplarische Vorgehensweise enthält die Schritte, die Sie befolgen müssen, um das standardmäßige LINQ to SQL Laufzeitverhalten zum Speichern von Daten in einer Datenbank mithilfe gespeicherter Prozeduren zu überschreiben.

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie die folgenden Aufgaben ausführen:

- Erstellen Sie eine neue Windows Forms Anwendung, und fügen Sie Ihr eine LINQ to SQL-Datei hinzu.

- Erstellen Sie eine Entitäts Klasse, die der Tabelle Northwind zugeordnet ist `Customers` .

- Erstellen Sie eine Objektdaten Quelle, die auf die LINQ to SQL- `Customer` Klasse verweist.

- Erstellen Sie ein Windows Form, das eine enthält <xref:System.Windows.Forms.DataGridView> , die an die-Klasse gebunden ist `Customer` .

- Implementieren der Speicherfunktion für das Formular.

- Erstellen <xref:System.Data.Linq.DataContext> Sie Methoden, indem Sie dem **O/R-Designer** gespeicherte Prozeduren hinzufügen.

- Konfigurieren Sie die- `Customer` Klasse für die Verwendung gespeicherter Prozeduren, um Einfügungen, Aktualisierungen und Löschungen

## <a name="prerequisites"></a>Voraussetzungen

In dieser exemplarischen Vorgehensweise werden SQL Server Express localdb-und Northwind-Beispieldatenbank verwendet.

1. Wenn Sie nicht über SQL Server Express localdb verfügen, installieren Sie es entweder über die [SQL Server Express Downloadseite](https://www.microsoft.com/sql-server/sql-server-editions-express)oder über das **Visual Studio-Installer**. Im **Visual Studio-Installer** können Sie SQL Server Express localdb als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** oder als einzelne Komponente installieren.

2. Installieren Sie die Beispieldatenbank Northwind, indem Sie die folgenden Schritte ausführen:

    1. Öffnen Sie in Visual Studio das Fenster **SQL Server-Objekt-Explorer** . (**SQL Server-Objekt-Explorer** als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** im **Visual Studio-Installer** installiert.) Erweitern Sie den Knoten **SQL Server** . Klicken Sie mit der rechten Maustaste auf die localdb-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren Sie das [Northwind-Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Mit diesem T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript in den Abfrage-Editor ein, und klicken Sie dann auf die Schaltfläche **Ausführen** .

       Nach kurzer Zeit wird die Ausführung der Abfrage abgeschlossen und die Datenbank Northwind erstellt.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Erstellen einer Anwendung und Hinzufügen von LINQ to SQL-Klassen

Da Sie mit LINQ to SQL Klassenarbeiten und die Daten in einem Windows Form anzeigen, erstellen Sie eine neue Windows Forms Anwendung, und fügen Sie eine LINQ to SQL Klassen-Datei hinzu.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>So erstellen Sie ein neues Windows Forms-Anwendungsprojekt, das LINQ to SQL Klassen enthält

1. Wählen Sie in Visual Studio im Menü **Datei** die Optionen **Neu** > **Projekt** aus.

2. Erweitern Sie entweder **Visual c#** oder **Visual Basic** im linken Bereich, und wählen Sie dann **Windows-Desktop** aus.

3. Wählen Sie im mittleren Bereich den **Windows Forms App** -Projekttyp aus.

4. Nennen Sie das Projekt **UpdatingwithSProcsWalkthrough**, und wählen Sie dann **OK** aus.

     Das Projekt **UpdatingwithSProcsWalkthrough** wird erstellt und zum **Projektmappen-Explorer** hinzugefügt.

4. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

5. Klicken Sie auf die Vorlage **LINQ to SQL-Klassen**, und geben Sie im Feld **Name** den Namen **Northwind.dbml** ein.

6. Klicken Sie auf **Hinzufügen**.

     Eine leere LINQ to SQL Klassendatei (**Northwind. dbml**) wird dem Projekt hinzugefügt, und der **O/R-Designer** wird geöffnet.

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Erstellen der Customer-Entitäts Klasse und der Objektdaten Quelle

Erstellen Sie LINQ to SQL Klassen, die Datenbanktabellen zugeordnet sind, indem Sie Tabellen von **Server-Explorer** oder **Datenbank-Explorer** auf den **O/R-Designer** ziehen. Sie erhalten LINQ to SQL-Entitätsklassen, die den Tabellen in der Datenbank zugeordnet sind. Nachdem die Entitätsklassen erstellt wurden, können sie wie andere Klassen mit öffentlichen Eigenschaften als Objektdatenquellen dienen.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>So erstellen Sie eine Customer-Entitätsklasse und konfigurieren damit eine Datenquelle

1. Suchen Sie in **Server-Explorer** oder **Datenbank-Explorer** die **Customer** -Tabelle in der SQL Server-Version der Beispieldatenbank Northwind.

2. Ziehen Sie den Knoten **Customers** aus **Server-Explorer** oder **Datenbank-Explorer** auf die Oberfläche des **O/R-Designers* .

     Eine Entitätsklasse mit dem Namen **Customer** wird erstellt. Sie verfügt über Eigenschaften, die den Spalten in der Tabelle Customers entsprechen. Die Entitätsklasse wird **Customer** (nicht **Customers**) genannt, da sie einem einzelnen Kunden aus der Tabelle „Customers“ entspricht.

    > [!NOTE]
    > Dieses Umbenennungsverhalten wird als *Pluralisierung* bezeichnet. Sie kann im [Dialogfeld Optionen](../ide/reference/options-dialog-box-visual-studio.md)aktiviert oder deaktiviert werden. Weitere Informationen finden Sie unter Gewusst [wie: Aktivieren und Deaktivieren der Pluralisierung (O/R-Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. Klicken Sie im Menü **Erstellen** auf **UpdatingwithSProcsWalkthrough erstellen**, um das Projekt zu erstellen.

4. Um das Fenster **Datenquellen** zu öffnen, klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

5. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

6. Klicken Sie auf der Seite **Datenquellentyp auswählen** auf **Objekt**, und klicken Sie dann auf **Weiter**.

7. Erweitern Sie den Knoten **UpdatingwithSProcsWalkthrough**, suchen Sie die Klasse **Customer**, und wählen Sie diese aus.

    > [!NOTE]
    > Wenn die Klasse **Customer** nicht verfügbar ist, beenden Sie den Assistenten, erstellen Sie das Projekt, und führen Sie den Assistenten erneut aus.
8. Klicken Sie auf **Fertig stellen**, um die Datenquelle zu erstellen, und fügen Sie die Entitätsklasse **Customer** zum Fenster **Datenquellen** hinzu.

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Erstellen eines DataGridView-Steuerelemente zum Anzeigen der Kundendaten in einem Windows Form

Erstellen Sie Steuerelemente, die an Entitäts Klassen gebunden sind, indem Sie LINQ to SQL Datenquellen Elemente aus dem **Datenquellen** Fenster auf ein Windows Form ziehen.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>So fügen Sie Steuerelemente hinzu, die an Entitätsklassen gebunden sind

1. Öffnen Sie **Form1** in Designansicht.

2. Ziehen Sie den Knoten **Customer** aus dem Fenster **Datenquellen** auf **Form1**.

    > [!NOTE]
    > Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**, um das Fenster **Datenquellen** anzuzeigen.

3. Öffnen Sie **Form1** im Code-Editor.

4. Fügen Sie den folgenden Code in das Formular ein, das dem Formular außerhalb einer bestimmten Methode, aber innerhalb der- `Form1` Klasse entspricht:

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();
    ```

5. Erstellen Sie einen Ereignishandler für das `Form_Load`-Ereignis, und fügen Sie dem Handler den folgenden Code hinzu:

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;
    ```

## <a name="implement-save-functionality"></a>Implementieren der Speicher Funktionalität

Die Schaltfläche zum Speichern ist standardmäßig nicht aktiviert, und die Speicherfunktionalität ist nicht implementiert. Auch wird bei Erstellung datengebundener Steuerelemente für Objektdatenquellen nicht automatisch Code hinzugefügt, um geänderte Daten in der Datenbank zu speichern. In diesem Abschnitt wird erläutert, wie die Schaltfläche speichern aktiviert und die Speicher Funktionalität für LINQ to SQL Objekte implementiert wird.

### <a name="to-implement-save-functionality"></a>So implementieren Sie die Speicherfunktionalität

1. Öffnen Sie **Form1** in Designansicht.

2. Wählen Sie im **CustomersBindingNavigator** die Schaltfläche zum Speichern (die Schaltfläche mit dem Diskettensymbol) aus.

3. Legen Sie im Fenster **Eigenschaften** die Eigenschaft **Aktiviert** auf **True** fest.

4. Doppelklicken Sie auf die Schaltfläche zum Speichern, um einen Ereignishandler zu erstellen und zum Code-Editor zu wechseln.

5. Fügen Sie dem Ereignishandler für die Schaltfläche zum Speichern den folgenden Code hinzu:

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Überschreiben des Standard Verhaltens für die Durchführung von Aktualisierungen (Einfügungen, Updates und Löschungen)

### <a name="to-override-the-default-update-behavior"></a>So überschreiben Sie das standardmäßige Updateverhalten

1. Öffnen Sie die Datei LINQ to SQL im **O/R-Designer**. (Doppelklicken Sie im **Projektmappen-Explorer** auf die Datei **Northwind.dbml**.)

2. Erweitern Sie im **Server-Explorer** oder **Datenbank-Explorer** den Knoten **Gespeicherte Prozeduren** der Datenbank „Northwind“, und suchen Sie die gespeicherten Prozeduren **InsertCustomers**, **UpdateCustomers** und **DeleteCustomers**.

3. Ziehen Sie alle drei gespeicherten Prozeduren auf den **O/R-Designer**.

     Die gespeicherten Prozeduren werden dem Methodenbereich als <xref:System.Data.Linq.DataContext>-Methoden hinzugefügt. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Wählen Sie im **O/R-Designer** die Entitäts Klasse **Customer** aus.

5. Wählen Sie im Fenster **Eigenschaften** die Eigenschaft **Einfügen** aus.

6. Klicken Sie auf die Auslassungszeichen (**...**) neben **Laufzeit verwenden**, um das Dialogfeld **Verhalten konfigurieren** zu öffnen.

7. Klicken Sie auf **Anpassen**.

8. Wählen Sie aus der Liste **Anpassen** die **InsertCustomers**-Methode aus.

9. Klicken Sie auf **Anwenden**, um die Konfiguration für die ausgewählte Klasse und das ausgewählte Verhalten zu speichern.

    > [!NOTE]
    > Sie können mit der Konfiguration des Verhaltens jeder Klasse/Verhalten-Kombination fortfahren, solange Sie nach jeder Änderung auf **Anwenden** klicken. Wenn Sie die Klasse oder das Verhalten ändern, bevor Sie auf Übernehmen klicken, wird ein Warn Dialogfeld angezeigt, in dem Sie die Möglichkeit **haben, Änderungen** anzuwenden.

10. Wählen Sie aus der Liste **Verhalten** die Option **Aktualisieren** aus.

11. Klicken Sie auf **Anpassen**.

12. Wählen Sie in der Liste **Anpassen** die **UpdateCustomers**-Methode aus.

     Überprüfen Sie die Liste der **Methodenargumente** und **Klasseneigenschaften**, und beachten Sie, dass für einige Spalten in der Tabelle zwei **Methodenargumente** sowie zwei **Klasseneigenschaften** vorhanden sind. Dies macht es einfacher, Änderungen zu verfolgen und Anweisungen zur Überprüfung von Parallelitätsverletzungen zu erstellen.

13. Ordnen Sie das **Original_CustomerID**-Methodenargument der Klasseneigenschaft **CustomerID (Original)** zu.

    > [!NOTE]
    > Standardmäßig werden Methodenargumente Klasseneigenschaften zugeordnet, wenn die Namen übereinstimmen. Wenn Eigenschaftsnamen geändert werden und nicht mehr mit der-Tabelle und der-Entitäts Klasse übereinstimmen, müssen Sie möglicherweise die entsprechende Klassen Eigenschaft auswählen, der zugeordnet werden soll, wenn der **O/R-Designer** die richtige Zuordnung nicht ermitteln kann. Wenn die Methodenargumente nicht über gültige Klasseneigenschaften für die Zuordnung verfügen, können Sie zusätzlich den Wert **Klasseneigenschaften** auf **(Keine)** festlegen.

14. Klicken Sie auf **Anwenden**, um die Konfiguration für die ausgewählte Klasse und das ausgewählte Verhalten zu speichern.

15. Wählen Sie aus der Liste **Verhalten** die Option **Löschen** aus.

16. Klicken Sie auf **Anpassen**.

17. Wählen Sie in der Liste **Anpassen** die **DeleteCustomers**-Methode aus.

18. Ordnen Sie das **Original_CustomerID**-Methodenargument der Klasseneigenschaft **CustomerID (Original)** zu.

19. Klicken Sie auf **OK**.

> [!NOTE]
> Obwohl es für diese spezielle Exemplarische Vorgehensweise kein Problem ist, sollten Sie beachten, dass LINQ to SQL von der Datenbank generierte Werte automatisch für Identitäts-(automatische Inkrement), ROWGUIDCOL (Daten Bank generierte GUID) und Zeitstempel-Spalten bei Einfügungen und Aktualisierungen verarbeitet. Datenbankgenerierte Werte in anderen Spaltentypen führen unerwartet zu einem NULL-Wert. Um die Daten Bank generierten Werte zurückzugeben, sollten Sie manuell <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> auf `true` und <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> auf einen der folgenden Werte festlegen: [AutoSync. Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync. OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)oder [AutoSync. OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="test-the-application"></a>Testen der Anwendung

Führen Sie die Anwendung erneut aus, um zu überprüfen, ob der Kundendatensatz in der Datenbank von der gespeicherten Prozedur **UpdateCustomers** ordnungsgemäß aktualisiert wird.

1. Drücken Sie **F5**.

2. Ändern Sie einen Datensatz im Raster, um das Updateverhalten zu testen.

3. Fügen Sie einen neuen Datensatz hinzu, um das Einfügeverhalten zu testen.

4. Klicken Sie auf die Speichern-Schaltfläche, um die Änderungen in der Datenbank zu speichern.

5. Schließen Sie das Formular.

6. Drücken Sie **F5** , und überprüfen Sie, ob der aktualisierte Datensatz und der neu eingefügte Datensatz persistent sind

7. Löschen Sie den in Schritt 3 erstellten neuen Datensatz, um das Löschverhalten zu testen.

8. Klicken Sie auf die Schaltfläche „Speichern“, um die Änderungen zu übermitteln und den gelöschten Datensatz aus der Datenbank zu entfernen.

9. Schließen Sie das Formular.

10. Drücken Sie **F5** , und überprüfen Sie, ob der gelöschte Datensatz aus der Datenbank entfernt wurde.

    > [!NOTE]
    > Wenn Ihre Anwendung SQL Server Express Edition verwendet, werden beim Drücken von **F5** in Schritt 10 die Änderungen möglicherweise nicht angezeigt. Dies ist abhängig vom Wert der Eigenschaft **Ins Ausgabeverzeichnis kopieren** der Datenbankdatei.

## <a name="next-steps"></a>Nächste Schritte

Abhängig von den Anforderungen Ihrer Anwendung können Sie nach der Erstellung LINQ to SQL Entitäts Klassen mehrere Schritte ausführen. Hier sind einige Verbesserungen, die Sie an dieser Anwendung vornehmen können:

- Implementieren der Parallelitätsprüfung während der Durchführung von Updates. Weitere Informationen finden Sie unter vollständige Parallelität [: Übersicht](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Hinzufügen von LINQ-Abfragen, um Daten zu filtern. Weitere Informationen finden [Sie unter Einführung in LINQ-Abfragen (c#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Weitere Informationen

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext-Methoden](../data-tools/datacontext-methods-o-r-designer.md)
- [Gewusst wie: Zuweisen von gespeicherten Prozeduren zum Ausführen von Aktualisierungen, Einfügungen und Löschungen](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [LINQ to SQL-Abfragen](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)
