---
title: Datenklassenvererbung (O/R-Designer)
description: Arbeiten Sie mit der Daten Klassen Vererbung in objektrelationaler Designer (O/R-Designer), einem LINQ to SQL-Klassen Tool in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: aba03be7014880618d32be250e08c735622d8c4d
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436575"
---
# <a name="data-class-inheritance-or-designer"></a>Datenklassenvererbung (O/R-Designer)

Wie andere Objekte auch können LINQ to SQL-Klassen vererben und von anderen Klassen abgeleitet werden. Im Code können Sie Vererbungsbeziehungen zwischen Objekten angeben, indem Sie deklarieren, dass eine Klasse von einer anderen erbt. Vererbungsbeziehungen werden in einer Datenbank auf verschiedene Arten erstellt. Der **objektrelationaler Designer** ( **O/R-Designer** ) unterstützt das Konzept der Vererbung einer einzelnen Tabelle, da es häufig in relationalen Systemen implementiert wird.

Bei der Vererbung einer einzelnen Tabelle gibt es eine einzelne Datenbanktabelle, die Spalten sowohl für Basisklassen als auch für abgeleitete Klassen enthält. Bei relationalen Daten enthält eine Unterscheidungsspalte den Wert, der festlegt, zu welcher Klasse ein bestimmter Datensatz gehört. Angenommen, eine `Persons` Tabelle enthält alle Personen, die von einem Unternehmen verwendet werden. Einige Personen sind Mitarbeiter, andere Führungskräfte. Die `Persons` Tabelle enthält eine Spalte mit dem Namen `Type` , die für Manager den Wert 1 und für Mitarbeiter den Wert 2 hat. Die `Type` Spalte ist die diskriminatorspalte. In diesem Szenario können Sie eine Unterklasse von Mitarbeitern erstellen und die Klasse nur mit Datensätzen füllen, deren `Type` Wert 2 ist.

Wenn Sie die Vererbung in Entitätsklassen unter Verwendung von [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] konfigurieren, ziehen Sie die einzelne Tabelle, die die Vererbungsdaten enthält, zweimal auf den Designer: einmal für jede Klasse in der Vererbungshierarchie. Nachdem Sie dem Designer die Tabellen hinzugefügt haben, verbinden Sie sie mit einem Vererbungselement aus der Toolbox des **objektrelationaler Designers** und legen dann die vier Vererbungseigenschaften im Fenster **Eigenschaften** fest.

## <a name="inheritance-properties"></a>Vererbungseigenschaften

In der folgenden Tabelle sind die Vererbungseigenschaften mit den jeweiligen Beschreibungen aufgeführt:

|Eigenschaft|BESCHREIBUNG|
|--------------|-----------------|
|**Diskriminatoreigenschaft**|Die (der Spalte zugeordnete) Eigenschaft, durch die bestimmt wird, zu welcher Klasse der aktuelle Datensatz gehört.|
|**Basisklassen-Diskriminatorwert**|Der Wert (in der als **diskriminatoreigenschaft** bezeichneten Spalte), der bestimmt, dass ein Datensatz von der Basisklasse ist.|
|**Diskriminatorwert der abgeleiteten Klasse**|Der Wert (in der als **Diskriminatoreigenschaft** bezeichneten Eigenschaft), durch den bestimmt wird, dass ein Datensatz der abgeleiteten Klasse angehört.|
|**Vererbungsstandard**|Die Klasse, die aufgefüllt wird, wenn der Wert in der als **diskriminatoreigenschaft** bezeichneten Eigenschaft nicht mit dem **basisklassendiskriminatorwert** oder dem **Diskriminatorwert der abgeleiteten Klasse** identisch ist.|

Das Erstellen eines Objektmodells, das Vererbung verwendet und sich auf relationale Daten bezieht, kann etwas verwirrend sein. Dieses Thema enthält Informationen über die grundlegenden Begriffe und einzelnen Eigenschaften, die zum Konfigurieren der Vererbung erforderlich sind. Die folgenden Themen bieten eine genauere Erläuterung zum Konfigurieren der Vererbung mit dem **O/R-Designer**.

|Thema|BESCHREIBUNG|
|-----------|-----------------|
|[Vorgehensweise: Konfigurieren der Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Beschreibt das Konfigurieren von Entitäts Klassen, die die Vererbung einer einzelnen Tabelle mithilfe des **O/R-Designers** verwenden.|
|[Exemplarische Vorgehensweise: Erstellen von LINQ to SQL Klassen mithilfe einer Vererbung für eine einzelne Tabelle (O/R-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Enthält Schritt-für-Schritt-Anleitungen zum Konfigurieren von Entitäts Klassen, die die Vererbung einer einzelnen Tabelle mithilfe des **O/R-Designers** verwenden.|

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Walkthrough: Creating LINQ to SQL classes (O-R Designer) (Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O/R-Designer))](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL Klassen mithilfe einer Vererbung für eine einzelne Tabelle (O/R-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Erste Schritte](/dotnet/framework/data/adonet/sql/linq/getting-started)
