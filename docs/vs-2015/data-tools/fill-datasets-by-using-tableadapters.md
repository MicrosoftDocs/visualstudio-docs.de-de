---
title: Auffüllen von Datasets mit TableAdapters | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fd1dcf464b7628e345845ca9f371ef6de1efe88
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672352"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Füllen von Datasets mit TableAdapters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine TableAdapter-Komponente füllt ein DataSet mit Daten aus der Datenbank auf Grundlage einer oder mehrerer von Ihnen angegebenen Abfragen oder gespeicherten Prozeduren auf. TableAdapters können auch Hinzufügungen, Updates und Löschungen in der Datenbank durchführen, um Änderungen beizubehalten, die Sie am DataSet vornehmen. Sie können auch globale Befehle ausgeben, die nicht mit einer bestimmten Tabelle verknüpft sind.

> [!NOTE]
> TableAdapters werden von Visual Studio-Designern generiert. Wenn Sie Datasets Programm gesteuert erstellen, verwenden Sie DataAdapter, bei dem es sich um eine .NET Framework Klasse handelt.

 Ausführliche Informationen zu TableAdapter-Vorgängen finden Sie direkt in einem der folgenden Themen:

|Thema|BESCHREIBUNG|
|-----------|-----------------|
|[Erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md)|Verwenden der Designer zum Erstellen und Konfigurieren von TableAdapters|
|[Erstellen von parametrisierten TableAdapter-Abfragen](../data-tools/create-parameterized-tableadapter-queries.md)|So ermöglichen Sie Benutzern das Bereitstellen von Argumenten für TableAdapter-Prozeduren oder-Abfragen|
|[Direktes Zugreifen auf die Datenbank mit einem TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Verwenden der DBDirect-Methoden von TableAdapters|
|[Deaktivieren von Einschränkungen beim Auffüllen von Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Arbeiten mit Foreign Key-Einschränkungen beim Aktualisieren von Daten|
|[Erweitern der Funktionalität eines TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Hinzufügen von benutzerdefiniertem Code zu TableAdapters|
|[Laden von Daten in ein Dataset](../data-tools/read-xml-data-into-a-dataset.md)|Arbeiten mit XML|

## <a name="tableadapters-overview"></a>Übersicht über TableAdapters
 TableAdapters sind vom Designer generierte Komponenten, die eine Verbindung mit einer Datenbank herstellen, Abfragen oder gespeicherte Prozeduren ausführen und Ihre Datentabelle mit den zurückgegebenen Daten ausfüllen. TableAdapters senden auch aktualisierte Daten aus Ihrer Anwendung zurück an die Datenbank. Sie können beliebig viele Abfragen auf einem TableAdapter ausführen, solange Daten zurückgegeben werden, die dem Schema der Tabelle entsprechen, der der TableAdapter zugeordnet ist. Das folgende Diagramm zeigt, wie TableAdapters mit Datenbanken und anderen Objekten im Arbeitsspeicher interagieren:

 ![Datenfluss in einer Clientanwendung](../data-tools/media/clientdatadiagram.gif "Clientdatadiagram")

 Obwohl TableAdapters mit dem **DataSet-Designer**entworfen wurden, werden die TableAdapter-Klassen nicht als geschsted Klassen von generiert  <xref:System.Data.DataSet> . Sie befinden sich in separaten Namespaces, die für jedes Dataset spezifisch sind. Wenn Sie z. b. ein DataSet mit dem Namen haben `NorthwindDataSet` , befinden sich die TableAdapters, die s in zugeordnet sind,  <xref:System.Data.DataTable> im- `NorthwindDataSet` `NorthwindDataSetTableAdapters` Namespace. Um programmgesteuert auf einen speziellen TableAdapter zuzugreifen, müssen Sie eine neue Instanz des TableAdapter deklarieren. Beispiel:

 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]

## <a name="associated-datatable-schema"></a>Zugeordnetes DataTable-Schema
 Wenn Sie einen TableAdapter erstellen, definieren Sie mit der ersten Abfrage oder gespeicherten Prozedur das Schema der zugeordneten TableAdapter <xref:System.Data.DataTable> . Sie führen diese anfängliche Abfrage oder gespeicherte Prozedur aus, indem Sie die-Methode des TableAdapter aufrufen `Fill` (die die zugeordneten TableAdapter-Daten füllt <xref:System.Data.DataTable> ). Alle Änderungen, die an der Haupt Abfrage des TableAdapters vorgenommen werden, werden im Schema der zugeordneten Datentabelle widergespiegelt. Wenn Sie z. b. eine Spalte aus der Haupt Abfrage entfernen, wird auch die Spalte aus der zugeordneten Datentabelle entfernt. Wenn zusätzliche Abfragen für den TableAdapter SQL-Anweisungen verwenden, die Spalten zurückgeben, die nicht in der Haupt Abfrage vorhanden sind, versucht der Designer, die Spalten Änderungen zwischen der Haupt Abfrage und den zusätzlichen Abfragen zu synchronisieren. Weitere Informationen finden Sie unter Gewusst [wie: Bearbeiten von TableAdapters](https://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).

## <a name="tableadapter-update-commands"></a>Aktualisierungsbefehle für TableAdapter
 Die Aktualisierungs Funktionalität eines TableAdapters hängt davon ab, wie viele Informationen in der Haupt Abfrage des TableAdapter-Assistenten verfügbar sind. Beispielsweise sind TableAdapters, die so konfiguriert sind, dass sie Werte aus mehreren Tabellen (JOINs), Skalarwerte, Ansichten oder die Ergebnisse von Aggregatfunktionen abrufen, bei der Erstellung anfänglich nicht in der Lage, Aktualisierungen an die zugrunde liegende Datenbank zurückzusenden. Sie können jedoch die Befehle INSERT, Update und DELETE manuell im **Eigenschaften** Fenster konfigurieren.

## <a name="tableadapter-queries"></a>TableAdapter-Abfragen
 ![TableAdapter mit mehreren Abfragen](../data-tools/media/tableadapter.gif "TableAdapter")

 TableAdapters können mehrere Abfragen enthalten, um die zugehörigen Datentabellen auszufüllen. Sie können so viele Abfragen für einen TableAdapter definieren, wie für die Anwendung erforderlich sind, solange jede Abfrage Daten zurückgibt, die demselben Schema entsprechen wie die zugeordnete Datentabelle. Diese Funktion ermöglicht es einem TableAdapter, basierend auf unterschiedlichen Kriterien unterschiedliche Ergebnisse zu laden.

 Wenn Ihre Anwendung z. b. eine Tabelle mit Kundennamen enthält, können Sie eine Abfrage erstellen, die die Tabelle mit jedem Kundennamen füllt, der mit einem bestimmten Buchstaben beginnt, und einen anderen, der die Tabelle mit allen Kunden füllt, die sich im selben Zustand befinden. Zum Auffüllen einer `Customers` Tabelle mit Kunden in einem bestimmten Zustand können Sie eine Abfrage erstellen, `FillByState` die einen Parameter für den Statuswert wie folgt annimmt: `SELECT * FROM Customers WHERE State = @State` . Sie führen die Abfrage aus, indem Sie die `FillByState` -Methode aufrufen und den Parameterwert wie folgt übergeben: `CustomerTableAdapter.FillByState("WA")` .

 Zusätzlich zum Hinzufügen von Abfragen, die Daten desselben Schemas zurückgeben wie die Datentabelle des TableAdapter, können Sie Abfragen hinzufügen, die skalare (einzelne) Werte zurückgeben. Beispielsweise ist eine Abfrage, die die Anzahl der Kunden () zurückgibt, `SELECT Count(*) From Customers` für eine gültig, `CustomersTableAdapter,` Obwohl die zurückgegebenen Daten nicht dem Schema der Tabelle entsprechen.

## <a name="clearbeforefill-property"></a>ClearBeforeFill-Eigenschaft
 Jedes Mal, wenn Sie eine Abfrage ausführen, um die Datentabelle eines TableAdapters auszufüllen, werden die vorhandenen Datenstandard mäßig gelöscht, und nur die Ergebnisse der Abfrage werden in die Tabelle geladen. Legen Sie die-Eigenschaft des TableAdapter `ClearBeforeFill` auf fest, `false` Wenn Sie die von einer Abfrage zurückgegebenen Daten an die vorhandenen Daten in einer Datentabelle hinzufügen oder zusammenführen möchten. Unabhängig davon, ob Sie die Daten löschen, müssen Sie Aktualisierungen explizit an die Datenbank zurücksenden, wenn Sie Sie beibehalten möchten. Denken Sie daran, Änderungen an den Daten in der Tabelle zu speichern, bevor Sie eine andere Abfrage ausführen, die die Tabelle füllt. Weitere Informationen finden Sie unter [Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>TableAdapter-Vererbung
 Mit TableAdapters werden die Funktionen von Standarddaten Adaptern erweitert, indem eine konfigurierte Klasse gekapselt wird <xref:System.Data.Common.DataAdapter> ? qualifyhint = false&AutoUpgrade = true. Standardmäßig erbt der TableAdapter von der <xref:System.ComponentModel.Component> -Klasse und kann nicht in die- <xref:System.Data.Common.DataAdapter> Klasse umgewandelt werden. Wenn ein TableAdapter in die Klasse umgewandelt wird, führt dies zu <xref:System.Data.Common.DataAdapter> einem <xref:System.InvalidCastException> Fehler? qualifyhint = false&AutoUpgrade = true. Wenn Sie die Basisklasse eines TableAdapters ändern möchten, können Sie eine Klasse eingeben, die von <xref:System.ComponentModel.Component> in der **Basisklassen** Eigenschaft des TableAdapter in der **DataSet-Designer**abgeleitet ist.

## <a name="tableadapter-methods-and-properties"></a>TableAdapter-Methoden und -Eigenschaften
 Die TableAdapter-Klasse ist nicht Teil des [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Dies bedeutet, dass Sie Sie nicht in der Dokumentation oder der **Objektkatalog**nachschlagen können. Sie wird zur Entwurfszeit erstellt, wenn Sie einen der zuvor erwähnten Assistenten verwenden. Der Name, der einem TableAdapter bei der Erstellung zugewiesen wird, basiert auf dem Namen der Tabelle, mit der Sie arbeiten. Wenn Sie z. b. einen TableAdapter auf der Grundlage einer Tabelle in einer Datenbank mit dem Namen erstellen `Orders` , wird der TableAdapter benannt `OrdersTableAdapter` . Sie können den Klassennamen für den TableAdapter ändern, indem Sie die **Name**-Eigenschaft im **DataSet-Designer** verwenden.

 Im folgenden finden Sie die häufig verwendeten Methoden und Eigenschaften von TableAdapters:

|Member|BESCHREIBUNG|
|------------|-----------------|
|`TableAdapter.Fill`|Füllt die dem TableAdapter zugeordnete Datentabelle mit den Ergebnissen des SELECT-Befehls für den TableAdapter auf.|
|`TableAdapter.Update`|Sendet Änderungen an die Datenbank zurück und gibt eine ganze Zahl zurück, die die Anzahl der von der Aktualisierung betroffenen Zeilen darstellt. Weitere Informationen finden Sie unter [Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Gibt einen neuen zurück <xref:System.Data.DataTable> , der mit Daten gefüllt ist.|
|`TableAdapter.Insert`|Erstellt eine neue Zeile in der Datentabelle. Weitere Informationen finden Sie unter [Einfügen neuer Datensätze in eine Datenbank](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Bestimmt, ob eine Datentabelle geleert wird, bevor Sie eine der `Fill`-Methoden aufrufen.|

## <a name="tableadapter-update-method"></a>TableAdapter-Aktualisierungsmethode
 TableAdapters verwenden zum Lesen und Schreiben in Datenbanken Datenbefehle. Die anfängliche `Fill` (Main)-Abfrage des TableAdapter wird als Grundlage für das Erstellen des Schemas der zugeordneten Datentabelle sowie der `InsertCommand` Befehle, und verwendet, die `UpdateCommand` `DeleteCommand` der Methode zugeordnet sind `TableAdapter.Update` . Durch Aufrufen der-Methode eines TableAdapters `Update` werden die Anweisungen ausgeführt, die bei der ursprünglichen Konfiguration des TableAdapter erstellt wurden, und nicht eine der zusätzlichen Abfragen, die mit dem **Assistenten zum Konfigurieren der TableAdapter-Abfrage**hinzugefügt wurden.

 Wenn Sie einen TableAdapter verwenden, führt er effektiv dieselben Operationen mit den Befehlen aus, die Sie normalerweise ausführen würden. Wenn Sie z. b. die-Methode des Adapters aufzurufen `Fill` , führt der Adapter den Daten Befehl in seiner `SelectCommand` -Eigenschaft aus und verwendet einen Daten Reader (z. b <xref:System.Data.SqlClient.SqlDataReader> .), um das Resultset in die Datentabelle zu laden. Wenn Sie die-Methode des Adapters aufzurufen, wird auf ähnliche Weise `Update` der entsprechende Befehl (in den `UpdateCommand` `InsertCommand` Eigenschaften, und `DeleteCommand` ) für jeden geänderten Datensatz in der Datentabelle ausgeführt.

> [!NOTE]
> Wenn die Hauptabfrage genügend Informationen enthält, werden beim Generieren des TableAdapter standardmäßig die Befehle `InsertCommand`, `UpdateCommand` und `DeleteCommand` erstellt. Wenn die Haupt Abfrage des TableAdapters mehr als eine einzelne Table SELECT-Anweisung ist, kann der Designer möglicherweise, und nicht generieren  `InsertCommand` `UpdateCommand` `DeleteCommand` . Wenn diese Befehle nicht generiert werden, erhalten Sie möglicherweise einen Fehler, wenn Sie die- `TableAdapter.Update` Methode ausführen.

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods
 Zusätzlich zu  `InsertCommand` , `UpdateCommand` und `DeleteCommand` werden TableAdapters mit Methoden erstellt, die direkt für die-Datenbank ausgeführt werden können. Diese Methoden (`TableAdapter.Insert`, `TableAdapter.Update` und `TableAdapter.Delete`) können direkt aufgerufen werden, um Daten in der Datenbank zu bearbeiten. Dies bedeutet, dass Sie diese einzelnen Methoden aus Ihrem Code aufrufen können und nicht aufrufen `TableAdapter.Update` , um die Einfügungen, Updates und Löschvorgänge zu behandeln, die für die zugeordnete Datentabelle ausstehen.

 Wenn Sie diese direkten Methoden nicht erstellen möchten, legen Sie die **GenerateDBDirectMethods** -Eigenschaft des TableAdapter auf `false` (im **Eigenschaften** Fenster) fest. Zusätzliche Abfragen, die dem TableAdapter hinzugefügt werden, sind eigenständige Abfragen – Sie generieren diese Methoden nicht.

## <a name="tableadapter-support-for-nullable-types"></a>TableAdapter-Unterstützung für Typen mit Nullwert
 TableAdapters unterstützen Werte zulässt `Nullable(Of T)` -Typen und `T?` . Weitere Informationen zu Nullable-Typen in Visual Basic finden Sie unter [Auf NULL festlegbare Werttypen](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). Weitere Informationen zu Typen, die NULL-Werte zulassen, finden [Sie unter Verwenden von Typen](https://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28), die NULL-Werte zulassen.

## <a name="security"></a>Sicherheit
 Wenn Sie Daten Befehle verwenden, deren- `CommandType` Eigenschaft auf festgelegt <xref:System.Data.CommandType> ist, überprüfen Sie sorgfältig Informationen, die von einem Client gesendet werden, bevor Sie ihn an die Datenbank übergeben. Böswillige Benutzer könnten versuchen, veränderte oder zusätzliche SQL-Anweisungen zu senden (einzufügen), um unautorisierten Zugriff zu erhalten oder die Datenbank zu beschädigen. Bevor Sie Benutzereingaben in eine Datenbank übertragen, sollten Sie stets überprüfen, ob die Informationen gültig sind. Es wird empfohlen, nach Möglichkeit immer parametrisierte Abfragen oder gespeicherte Prozeduren zu verwenden.

## <a name="see-also"></a>Weitere Informationen
 [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
