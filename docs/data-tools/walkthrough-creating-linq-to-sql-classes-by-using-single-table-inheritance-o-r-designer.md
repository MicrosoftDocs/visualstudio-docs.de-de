---
title: LINQ to SQL Klassen mit Vererbung einer einzelnen Tabelle
description: In dieser exemplarischen Vorgehensweise erstellen Sie LINQ to SQL Klassen, indem Sie die Vererbung einer einzelnen Tabelle im Visual Studio-objektrelationaler Designer (O/R-Designer) verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b83fd664cb2969c12d69e1e818f61190deed3804
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998238"
---
# <a name="walkthrough-create-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Exemplarische Vorgehensweise: Erstellen von LINQ to SQL Klassen mithilfe einer Vererbung für eine einzelne Tabelle (O/R-Designer)
Die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) unterstützen die Vererbung einer einzelnen Tabelle, da Sie in der Regel in relationalen Systemen implementiert ist. In dieser exemplarischen Vorgehensweise werden die allgemeinen Schritte beschrieben, die im Thema Gewusst [wie: Konfigurieren der Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) erläutert werden, und es werden echte Daten bereitgestellt, um die Verwendung der Vererbung in zu veranschaulichen [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] .

In dieser exemplarischen Vorgehensweise führen Sie die folgenden Aufgaben aus:

- Erstellen einer Datenbanktabelle und Hinzufügen von Daten.

- Erstellen einer Windows Forms-Anwendung.

- Hinzufügen einer [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Datei zu einem Projekt.

- Erstellen neuer Entitätsklassen.

- Konfigurieren der Entitätsklassen zur Verwendung von Vererbung.

- Abfragen der geerbten Klasse.

- Anzeigen der Daten in einem Windows Form.

## <a name="create-a-table-to-inherit-from"></a>Erstellen einer Tabelle, von der geerbt werden soll
Um zu sehen, wie die Vererbung funktioniert, erstellen Sie eine kleine `Person` Tabelle, verwenden Sie als Basisklasse, und erstellen Sie dann ein `Employee` Objekt, das von ihr erbt.

### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>So erstellen Sie eine Basistabelle zur Veranschaulichung der Vererbung

1. Klicken Sie in **Server-Explorer** oder **Datenbank-Explorer** mit der rechten Maustaste auf den Knoten **Tabellen** , und klicken Sie auf **neue Tabelle hinzufügen**.

    > [!NOTE]
    > Sie können die Northwind-Datenbank oder eine andere Datenbank verwenden, der Sie eine Tabelle hinzufügen können.

2. Fügen Sie in der **Tabellen-Designer** der Tabelle die folgenden Spalten hinzu:

    |Spaltenname|Datentyp|NULL-Werte zulassen|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**False**|
    |**Type**|**int**|**Wahr**|
    |**Vorname**|**nvarchar(200)**|**False**|
    |**Nachname**|**nvarchar(200)**|**False**|
    |**Manager**|**int**|**Wahr**|

3. Legen Sie die ID-Spalte als Primärschlüssel fest.

4. Speichern Sie die Tabelle unter dem Namen **Person**.

## <a name="add-data-to-the-table"></a>Hinzufügen von Daten zur Tabelle
Um sicherstellen zu können, dass die Vererbung ordnungsgemäß konfiguriert ist, muss die Tabelle Daten für jede Klasse in der Vererbung einer einzelnen Tabelle enthalten.

### <a name="to-add-data-to-the-table"></a>So fügen Sie der Tabelle Daten hinzu

1. Öffnen Sie die Tabelle in der Datenansicht. (Klicken Sie mit der rechten Maustaste auf die Tabelle **Person** in **Server-Explorer** oder **Datenbank-Explorer** und klicken Sie dann auf **Tabellendaten anzeigen**.)

2. Kopieren Sie die folgenden Daten in die Tabelle. (Sie können Sie kopieren und in die Tabelle einfügen, indem Sie im **Ergebnis** Bereich die gesamte Zeile auswählen.)

    |**ID**|**Typ**|**Vorname**|**Nachname**|**Manager**|
    |-|-|-|-|-|
    |**1**|**1**|**Anna**|**Wallace**|**NULL**|
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|
    |**3**|**1**|**Yael**|**Peled**|**NULL**|
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|
    |**5**|**2**|**Andreas**|**Hauser**|**1**|
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|
    |**9**|**2**|**Tai**|**Yee**|**2**|
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|
    |**11**|**2**|**Mindy**|**Martin**|**3**|
    |**12**|**2**|**Ken**|**Kwok**|**3**|

## <a name="create-a-new-project"></a>Erstellen eines neuen Projekts
Nachdem Sie die Tabelle erstellt haben, erstellen Sie ein neues Projekt zur Darstellung der Konfiguration von Vererbung.

### <a name="to-create-the-new-windows-forms-application"></a>So erstellen Sie die neue Windows Forms Anwendung

1. Wählen Sie in Visual Studio im Menü **Datei** die Optionen **Neu** > **Projekt** aus.

2. Erweitern Sie entweder **Visual c#** oder **Visual Basic** im linken Bereich, und wählen Sie dann **Windows-Desktop** aus.

3. Wählen Sie im mittleren Bereich den **Windows Forms App** -Projekttyp aus.

4. Nennen Sie das Projekt " **vererancewalkthrough**", und wählen Sie dann **OK** aus.

     Das **InheritanceWalkthrough**-Projekt wird erstellt und dem **Projektmappen-Explorer** hinzugefügt.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Hinzufügen einer LINQ to SQL-Klassendatei zum Projekt

### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>So fügen Sie dem Projekt eine LINQ to SQL-Datei hinzu

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2. Klicken Sie auf die Vorlage **LINQ to SQL-Klassen** und dann auf **Hinzufügen**.

     Die *DBML* -Datei wird dem Projekt hinzugefügt, und der **O/R-Designer** wird geöffnet.

## <a name="create-the-inheritance-by-using-the-or-designer"></a>Erstellen der Vererbung mithilfe des O/R-Designers
Konfigurieren Sie die Vererbung, indem Sie aus der **Toolbox** ein Objekt aus dem Bereich **Vererbung** auf die Entwurfsoberfläche ziehen.

### <a name="to-create-the-inheritance"></a>So erstellen Sie die Vererbung

1. Navigieren Sie in **Server-Explorer** oder **Datenbank-Explorer** zu der **Person** -Tabelle, die Sie zuvor erstellt haben.

2. Ziehen Sie die **Person** -Tabelle auf die Entwurfs Oberfläche des **O/R-Designers** .

3. Ziehen Sie eine zweite **Person** -Tabelle auf den **O/R-Designer** , und ändern Sie den Namen in **Employee**.

4. Löschen Sie die **Manager**-Eigenschaft aus dem Objekt **Person**.

5. Löschen Sie die Eigenschaften **Type**, **ID**, **FirstName** und **LastName** aus dem Objekt **Employee**. (Mit anderen Worten: Entfernen Sie alle Eigenschaften außer **Manager**.)

6. Erstellen Sie von der Registerkarte **Objektrelationaler Designer** der **Toolbox** eine **Vererbung** zwischen dem **Person**-Objekt und dem **Employee**-Objekt. Klicken Sie dazu in der **Toolbox** auf das Element **Vererbung**, und lassen Sie die Maustaste los. Klicken Sie anschließend im **O/R-Designer** auf das **Employee** -Objekt und dann auf das **Person** -Objekt. Der Pfeil in der Vererbungs Zeile zeigt dann auf das **Person** -Objekt.

7. Klicken Sie auf die Linie der **Vererbung** auf der Entwurfsoberfläche.

8. Legen Sie die Eigenschaft **Diskriminatoreigenschaft** auf **Type** fest.

9. Legen Sie die Eigenschaft **Diskrimatorwert der abgeleiteten Klasse** auf **2** fest.

10. Legen Sie die Eigenschaft **Basisklassen-Diskrimatorwert** auf **1** fest.

11. Legen Sie die **Vererbungsstandard**-Eigenschaft auf **Person** fest.

12. Erstellen Sie das Projekt.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Abfragen der geerbten Klasse und Anzeigen der Daten im Formular
Nun fügen Sie dem Formular Code hinzu, mit dem eine bestimmte Klasse im Objektmodell abgefragt wird.

### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>So erstellen Sie eine LINQ-Abfrage und zeigen die Ergebnisse im Formular an

1. Ziehen Sie eine **ListBox** auf **Form1**.

2. Doppelklicken Sie auf das Formular, um einen `Form1_Load`-Ereignishandler zu erstellen.

3. Fügen Sie dem `Form1_Load` -Ereignishandler folgenden Code hinzu:

    ```vb
    Dim dc As New DataClasses1DataContext
    Dim results = From emp In dc.Persons _
        Where TypeOf emp Is Employee _
        Select emp

    For Each Emp As Employee In results
        ListBox1.Items.Add(Emp.LastName)
    Next
    ```

    ```csharp
    NorthwindDataContext dc = new DataClasses1DataContext();
    var results = from emp in dc.Persons
                  where emp is Employee
                  select emp;

    foreach(Employee Emp in results)
    {
        listBox1.Items.Add(Emp.LastName)
    }
    ```

## <a name="test-the-application"></a>Testen der Anwendung
Führen Sie die Anwendung aus, und überprüfen Sie, ob die im Listenfeld angezeigten Datensätze alle Mitarbeiter sind (Datensätze mit dem Wert 2 in der Spalte **Typ** ).

### <a name="to-test-the-application"></a>So testen Sie die Anwendung

1. Drücken Sie **F5**.

2. Vergewissern Sie sich, dass in der Spalte **Typ** nur Datensätze mit dem Wert 2 angezeigt werden.

3. Schließen Sie das Formular. (Klicken Sie im Menü **Debuggen** auf **Debugging Debuggen**.)

## <a name="see-also"></a>Weitere Informationen

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Walkthrough: Creating LINQ to SQL classes (O-R Designer) (Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O/R-Designer))](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktionen zum Aktualisieren, Einfügen und Löschen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Gewusst wie: Generieren des Objektmodells in Visual Basic oder C #](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)
