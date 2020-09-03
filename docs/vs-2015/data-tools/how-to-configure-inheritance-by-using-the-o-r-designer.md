---
title: 'Vorgehensweise: Konfigurieren der Vererbung mit dem O-R-Designer | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f8c08546fdf96c755b3adb80021ab7269509739
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654703"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Vorgehensweise: Konfigurieren der Vererbung mit dem O/R-Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) unterstützt das häufig in relationalen Systemen implementierte Konzept der Vererbung einer einzelnen Tabelle. Bei der Vererbung einer einzelnen Tabelle gibt es eine einzelne Datenbanktabelle, die Felder sowohl für übergeordnete Informationen als auch für untergeordnete Informationen enthält. Bei relationalen Daten enthält eine Unterscheidungsspalte den Wert, der festlegt, zu welcher Klasse ein bestimmter Datensatz gehört.

 Betrachten Sie beispielsweise die Tabelle "Persons", die alle in einem Unternehmen beschäftigten Personen enthält. Einige Personen sind Mitarbeiter, andere Führungskräfte. Die Tabelle "Persons" enthält die Spalte `EmployeeType`, die für Führungskräfte den Wert 1 und für Mitarbeiter den Wert 2 enthält. Diese Spalte dient als Unterscheidungsspalte. In diesem Szenario können Sie eine Unterklasse von Mitarbeitern erstellen und die Klasse nur mit Datensätzen füllen, die einen `EmployeeType`-Wert von 2 aufweisen. Sie können aus der jeweiligen Klasse auch die nicht zutreffenden Spalten entfernen.

 Das Erstellen eines Objektmodells, das Vererbung verwendet (und sich auf relationale Daten bezieht), kann etwas verwirrend sein. Im folgenden Verfahren werden die erforderlichen Schritte zum Konfigurieren von Vererbung mit dem O/R-Designer dargestellt. Da es möglicherweise schwierig ist, generische Schritte nachzuvollziehen, ohne sich auf eine vorhandene Tabelle und die zugehörigen Spalten zu beziehen, wird auch eine exemplarische Vorgehensweise zur Verfügung gestellt, in der echte Daten verwendet werden. Ausführliche Schritt-für-Schritt-Anleitungen zum Konfigurieren der Vererbung mithilfe von finden Sie unter Exemplarische Vorgehensweise [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] [: Erstellen von LINQ to SQL Klassen mithilfe einer Vererbung für eine einzelne Tabelle (O/R-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

### <a name="to-create-inherited-data-classes"></a>So erstellen Sie geerbte Datenklassen

1. Öffnen [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Sie das, indem Sie einem vorhandenen Visual Basic-oder c#-Projekt ein **LINQ to SQL Classes** -Element hinzufügen.

2. Ziehen Sie die Tabelle, die Sie als Basisklasse verwenden möchten, auf den [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

3. Ziehen Sie eine zweite Kopie der Tabelle auf das, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] und benennen Sie Sie um. Sie dient als abgeleitete Klasse bzw. Unterklasse.

4. Klicken Sie in der **Toolbox** auf der Registerkarte **Objektrelationaler Designer** auf **Vererbung**, klicken Sie dann auf die Unterklasse (die umbenannte Tabelle), und stellen Sie eine Verbindung mit der Basisklasse her.

    > [!NOTE]
    > Klicken Sie in der **Toolbox** auf das Element **Vererbung**, und lassen Sie die Maustaste los. Klicken Sie auf die zweite Kopie der in Schritt 3 erstellten Klasse, und klicken Sie dann auf die erste Klasse, die Sie in Schritt 2 erstellt haben. Der Pfeil der Vererbungslinie zeigt dann auf die erste Klasse.

5. Löschen Sie in jeder Klasse die Objekteigenschaften, die nicht angezeigt werden sollen und die nicht für Zuordnungen verwendet werden. Sie erhalten eine Fehlermeldung, wenn Sie versuchen, die für Zuordnungen verwendeten Objekteigenschaften zu löschen: [die Eigenschaft \<property name> kann nicht gelöscht werden, weil \<association name> Sie an der Zuordnung teilnimmt ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Da eine abgeleitete Klasse die in der Basisklasse definierten Eigenschaften erbt, dürfen in den Klassen nicht dieselben Spalten definiert sein. (Spalten werden als Eigenschaften implementiert.) Sie können die Erstellung von Spalten in der abgeleiteten Klasse aktivieren, indem Sie den Vererbungs Modifizierer für die Eigenschaft in der Basisklasse festlegen. Weitere Informationen finden Sie unter [nicht im Build: Überschreiben von Eigenschaften und Methoden](https://msdn.microsoft.com/2167e8f5-1225-4b13-9ebd-02591ba90213).

6. Wählen Sie im [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] die Vererbungslinie aus.

7. Legen Sie im Fenster **Eigenschaften** die **diskriminatoreigenschaft** auf den Spaltennamen fest, der verwendet wird, um die Datensätze in ihren Klassen zu unterscheiden.

8. Legen Sie die Eigenschaft **Abgeleiteter Klassendiskriminatorwert** auf den Wert in der Datenbank fest, der den Datensatz als den geerbten Typ kennzeichnet. (Dies ist der Wert, der in der Unterscheidungsspalte gespeichert und mit dem die geerbte Klasse gekennzeichnet wird.)

9. Legen Sie die Eigenschaft **Basisklassen-Diskriminatorwert** auf den Wert fest, der den Datensatz als Basistyp kennzeichnet. (Dies ist der eigentliche Wert, der in der Unterscheidungsspalte gespeichert und mit dem die Basisklasse gekennzeichnet wird.)

10. Wahlweise können Sie auch die Eigenschaft **Vererbungsstandard** festlegen, um in einer Vererbungshierarchie einen Typ zu kennzeichnen, der beim Laden von Spalten verwendet wird, die keinem definierten Vererbungscode entsprechen. Anders ausgedrückt: Wenn ein Datensatz in der Unterscheidungs Spalte einen Wert enthält, der nicht mit dem Wert in den Eigenschaften der **Diskriminatorwert der abgeleiteten Klasse** oder den **Basisklassen-Diskriminatorwert** -Eigenschaften identisch ist, wird der Datensatz in den als **Vererbungs Standard**bezeichneten Typ geladen.

## <a name="see-also"></a>Weitere Informationen
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Exemplarische Vorgehensweise [: Erstellen von LINQ to SQL Klassen (o-r-Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [Pave neues für die Daten Anwendungsentwicklung in Visual Studio 2012](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1) [zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) Exemplarische Vorgehensweise [: Erstellen von LINQ to SQL Klassen mithilfe einer Vererbung für eine einzelne Tabelle (o/r-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) [nicht im Build: Vererbung in Visual Basic](https://msdn.microsoft.com/e5e6e240-ed31-4657-820c-079b7c79313c) [Vererbung](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)
