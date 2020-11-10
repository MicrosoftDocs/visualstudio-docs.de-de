---
title: Konfigurieren der Vererbung mit dem O/R-Designer
description: Erfahren Sie, wie Sie die Vererbung mit dem objektrelationaler Designer (O/R-Designer) konfigurieren, der die Vererbung einer einzelnen Tabelle unterstützt. Geerbte Daten Klassen wurden erstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4bc36bca3cc5bd13b3dcfad5ebed66eca7eeb019
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436332"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Vorgehensweise: Konfigurieren der Vererbung mit dem O/R-Designer
Der **objektrelationaler Designer** ( **O/R-Designer** ) unterstützt das Konzept der Vererbung einer einzelnen Tabelle, da es häufig in relationalen Systemen implementiert wird. Bei der Vererbung einer einzelnen Tabelle gibt es eine einzelne Datenbanktabelle, die Felder sowohl für übergeordnete Informationen als auch für untergeordnete Informationen enthält. Bei relationalen Daten enthält eine Unterscheidungsspalte den Wert, der festlegt, zu welcher Klasse ein bestimmter Datensatz gehört.

Angenommen, eine `Persons` Tabelle enthält alle Personen, die von einem Unternehmen verwendet werden. Einige Personen sind Mitarbeiter, andere Führungskräfte. Die `Persons` Tabelle enthält eine Spalte mit dem Namen `EmployeeType` , die für die Manager den Wert 1 und für Mitarbeiter den Wert 2 aufweist. Dies ist die diskriminatorspalte. In diesem Szenario können Sie eine Unterklasse von Mitarbeitern erstellen und die Klasse nur mit Datensätzen füllen, die einen `EmployeeType`-Wert von 2 aufweisen. Sie können aus der jeweiligen Klasse auch die nicht zutreffenden Spalten entfernen.

Das Erstellen eines Objektmodells, das Vererbung verwendet (und sich auf relationale Daten bezieht), kann etwas verwirrend sein. Im folgenden Verfahren werden die Schritte beschrieben, die zum Konfigurieren der Vererbung mit dem **O/R-Designer** erforderlich sind. Die folgenden allgemeinen Schritte ohne Verweis auf eine vorhandene Tabelle und Spalten sind möglicherweise schwierig, sodass eine exemplarische Vorgehensweise zur Verwendung von Daten bereitgestellt wird. Ausführliche Schritt-für-Schritt-Anleitungen zum Konfigurieren der Vererbung mit dem **o/r-Designer** finden Sie unter Exemplarische Vorgehensweise [: Erstellen von LINQ to SQL Klassen mithilfe einer Vererbung für eine einzelne Tabelle (o/r-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>So erstellen Sie geerbte Datenklassen

1. Öffnen Sie den **O/R-Designer** , indem Sie einem vorhandenen Visual Basic-oder c#-Projekt ein **LINQ to SQL Classes** -Element hinzufügen.

2. Ziehen Sie die Tabelle, die Sie als Basisklasse verwenden möchten, auf den **O/R-Designer**.

3. Ziehen Sie eine zweite Kopie der Tabelle auf den **O/R-Designer** , und benennen Sie Sie um. Sie dient als abgeleitete Klasse bzw. Unterklasse.

4. Klicken Sie in der **Toolbox** auf der Registerkarte **Objektrelationaler Designer** auf **Vererbung** , klicken Sie dann auf die Unterklasse (die umbenannte Tabelle), und stellen Sie eine Verbindung mit der Basisklasse her.

    > [!NOTE]
    > Klicken Sie in der **Toolbox** auf das Element **Vererbung** , und lassen Sie die Maustaste los. Klicken Sie auf die zweite Kopie der in Schritt 3 erstellten Klasse, und klicken Sie dann auf die erste Klasse, die Sie in Schritt 2 erstellt haben. Der Pfeil auf der Vererbungs Zeile verweist auf die erste Klasse.

5. Löschen Sie in jeder Klasse die Objekteigenschaften, die nicht angezeigt werden sollen und die nicht für Zuordnungen verwendet werden. Wenn Sie versuchen, die für Zuordnungen verwendeten Objekteigenschaften zu löschen, erhalten Sie einen Fehler: [die Eigenschaft \<property name> kann nicht gelöscht werden, weil \<association name> Sie an der Zuordnung teilnimmt ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Da eine abgeleitete Klasse die in der Basisklasse definierten Eigenschaften erbt, dürfen in den Klassen nicht dieselben Spalten definiert sein. (Spalten werden als Eigenschaften implementiert.) Sie können die Erstellung von Spalten in der abgeleiteten Klasse aktivieren, indem Sie den Vererbungs Modifizierer für die Eigenschaft in der Basisklasse festlegen. Weitere Informationen finden Sie unter [Grundlagen der Vererbung (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6. Wählen Sie im **O/R-Designer** die Vererbungs Zeile aus.

7. Legen Sie im Fenster **Eigenschaften** die **diskriminatoreigenschaft** auf den Spaltennamen fest, mit dem die Datensätze in den Klassen unterschieden werden.

8. Legen Sie die Eigenschaft **Abgeleiteter Klassendiskriminatorwert** auf den Wert in der Datenbank fest, der den Datensatz als den geerbten Typ kennzeichnet. (Dies ist der Wert, der in der diskriminatorspalte gespeichert wird und zum Festlegen der geerbten Klasse verwendet wird.)

9. Legen Sie die Eigenschaft **Basisklassen-Diskriminatorwert** auf den Wert fest, der den Datensatz als Basistyp kennzeichnet. (Dies ist der Wert, der in der diskriminatorspalte gespeichert wird und zum Festlegen der Basisklasse verwendet wird.)

10. Wahlweise können Sie auch die Eigenschaft **Vererbungsstandard** festlegen, um in einer Vererbungshierarchie einen Typ zu kennzeichnen, der beim Laden von Spalten verwendet wird, die keinem definierten Vererbungscode entsprechen. Anders ausgedrückt: Wenn ein Datensatz in der Unterscheidungs Spalte einen Wert enthält, der nicht mit dem Wert in den Eigenschaften der **Diskriminatorwert der abgeleiteten Klasse** oder den **Basisklassen-Diskriminatorwert** -Eigenschaften identisch ist, lädt der Datensatz in den als **Vererbungs Standard** bezeichneten Typ.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Walkthrough: Creating LINQ to SQL classes (O-R Designer) (Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O/R-Designer))](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL Klassen mithilfe einer Vererbung für eine einzelne Tabelle (O/R-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Grundlagen der Vererbung (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Vererbung](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
