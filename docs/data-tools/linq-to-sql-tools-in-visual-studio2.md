---
title: Übersicht über den O/R Designer für LINQ to SQL
description: Sie erhalten eine Übersicht zu LINQ to SQL-Tools in Visual Studio. Erfahren Sie mehr über den Object Relational Designer (O/R-Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 20473125814b1ee0569579c7248b7b940cd31500
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858643"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL-Tools in Visual Studio

LINQ to SQL war die erste objektrelationale Mappingtechnologie, die von Microsoft veröffentlicht wurde. Sie funktioniert sehr gut in einfachen Szenarios und wird auch in Zukunft in Visual Studio unterstützt, jedoch nicht mehr aktiv weiterentwickelt. LINQ to SQL eignet sich für die Verwaltung von Legacyanwendungen, die diese Technologie bereits verwenden, oder von einfachen Anwendungen, die SQL Server verwenden und keine Mappings von mehreren Tabellen erfordern. Im Allgemeinen sollten neue Anwendungen das Entity Framework verwenden, wenn eine objektrelationale Mapperebene erforderlich ist.

## <a name="install-the-linq-to-sql-tools"></a>Installieren der LINQ to SQL-Tools

In Visual Studio werden LINQ to SQL-Klassen, die SQL-Tabellen darstellen, mithilfe des **objektrelationalen Designers** (**O/R-Designer**) erstellt. Der O/R-Designer ist die Benutzeroberfläche, in der Sie DBML-Dateien bearbeiten können. Für die Bearbeitung von DBML-Dateien mit einer Designeroberfläche sind die LINQ to SQL-Tools erforderlich, die nicht im Lieferumfang der Visual Studio-Workloads enthalten sind.

Wenn Sie die LINQ to SQL-Tools installieren möchten, müssen Sie den Visual Studio-Installer starten, Sie auf **Ändern** sowie auf die Registerkarte **Einzelne Komponenten** klicken und in der Kategorie **Codetools** die Option **LINQ to SQL-Tools** auswählen.

## <a name="what-is-the-or-designer"></a>Was ist der O/R-Designer?

Die Entwurfsoberfläche des **O/R-Designers** gliedert sich in zwei verschiedene Bereiche: den Entitätenbereich auf der linken Seite und den Methodenbereich auf der rechten. Der Entitätenbereich ist die Hauptentwurfsoberfläche, auf der Entitätsklassen, Zuordnungen und Vererbungshierarchien angezeigt werden. Der Methodenbereich ist die Entwurfsoberfläche, auf der die <xref:System.Data.Linq.DataContext>-Methoden angezeigt werden, die gespeicherten Prozeduren und Funktionen zugeordnet sind.

Der **O/R-Designer** stellt eine visuelle Entwurfsoberfläche zum Erstellen von [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)-Entitätsklassen und -Zuordnungen (Beziehungen) bereit, die auf Objekten in einer Datenbank basieren. Mit anderen Worten: Der **O/R-Designer** erstellt innerhalb einer Anwendung ein Objektmodell, das die Objekte in einer Datenbank zuordnet. Außerdem generiert das Modell eine stark typisierte <xref:System.Data.Linq.DataContext>-Klasse, das Daten an die Entitätsklassen sendet und aus der Datenbank empfängt. Der **O/R-Designer** stellt auch Funktionen bereit, um gespeicherte Prozeduren und Funktionen zu <xref:System.Data.Linq.DataContext>-Methoden zuzuordnen, um Daten zurückzugeben und Entitätsklassen aufzufüllen. Abschließend bietet der **O/R-Designer** die Möglichkeit, Vererbungsbeziehungen zwischen Entitätsklassen zu entwerfen.

## <a name="open-the-or-designer"></a>Öffnen des O/R-Designers

Klicken Sie auf **Projekt** > **Neues Element hinzufügen**, und wählen Sie dann aus der Liste der Projektelemente **LINQ to SQL-Klassen** aus:

![LINQ to SQL-Klassen](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio erstellt eine *DBML*-Datei und fügt sie Ihrer Projektmappe hinzu. Hierbei handelt es sich um die XML-Mappingdatei und die zugehörigen Codedateien.

![LINQ to SQL-Klassen im Projektmappen-Explorer](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Wenn Sie die *DBML*-Datei auswählen, zeigt Visual Studio die Benutzeroberfläche des **O/R-Designers** an, in der Sie das Modell visuell erstellen können. Die folgende Abbildung zeigt den Designer, nachdem die Northwind-Tabellen `Customers` und `Orders` aus dem **Server-Explorer** gezogen wurden. Beachten Sie die Beziehung zwischen den Tabellen.

![LINQ to SQL-Designer](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> Der **O/R-Designer** erstellt einfache objektrelationale Mappings, da er nur 1:1-Mappingbeziehungen unterstützt. Das heißt, dass eine Entitätsklasse nur über eine 1:1-Zuordnungsbeziehung zu einer Datenbanktabelle oder -ansicht verfügen kann. Komplexe Mappings, z. B. das Mapping einer Entitätsklasse zu einer verknüpften Tabelle, werden nicht unterstützt. Für komplexe Mappings müssen Sie das Entity Framework verwenden. Darüber hinaus ist der Designer ein unidirektionaler Code-Generator. Das bedeutet, dass in der Codedatei nur Änderungen der Designeroberfläche wiedergegeben werden. Manuelle Änderungen der Codedatei werden nicht im **O/R-Designer** angezeigt. In der Codedatei vorgenommene manuelle Änderungen werden überschrieben, wenn der Designer gespeichert und Code erneut generiert wird. Weitere Informationen zum Hinzufügen von Benutzercode und zum Erweitern der vom **O/R-Designer** generierten Klassen finden Sie unter [Vorgehensweise: Erweitern von mit dem O/R-Designer erstelltem Code](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Erstellen und Konfigurieren von DataContext

Nachdem Sie einem Projekt ein Element aus **LINQ to SQL-Klassen** hinzugefügt und den **O/R-Designer** geöffnet haben, stellt die leere Entwurfsoberfläche eine leere <xref:System.Data.Linq.DataContext>-Klasse dar, das konfiguriert werden soll. Die Klasse <xref:System.Data.Linq.DataContext> wird mithilfe der Verbindungsinformationen des ersten Elements konfiguriert, das auf die Entwurfsoberfläche gezogen wird. Deshalb wird die Klasse <xref:System.Data.Linq.DataContext> mithilfe der Verbindungsinformationen des ersten Elements konfiguriert, das auf der Entwurfsoberfläche abgelegt wird. Weitere Informationen zur Klasse <xref:System.Data.Linq.DataContext> finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Erstellen von Entitätsklassen für Mappings zwischen Datenbanktabellen und -sichten

Sie können Entitätsklassen erstellen, die Tabellen und Sichten zugeordnet sind, indem Sie Datenbanktabellen und -sichten aus dem **Server-Explorer** oder **Datenbank-Explorer** in den **O/R-Designer** ziehen. Wie im vorherigen Abschnitt angegeben, wird die Klasse <xref:System.Data.Linq.DataContext> mithilfe der Verbindungsinformationen des ersten Elements konfiguriert, das auf die Entwurfsoberfläche gezogen wird. Wenn ein nachfolgendes Element mit einer anderen Verbindung dem **O/R-Designer** hinzugefügt wird, können Sie die Verbindung für <xref:System.Data.Linq.DataContext> ändern. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von LINQ to SQL-Klassen, die Tabellen und Ansichten zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Erstellen von DataContext-Methoden zum Aufrufen von gespeicherten Prozeduren und Funktionen

Sie können <xref:System.Data.Linq.DataContext>-Methoden erstellen, die gespeicherte Prozeduren und Funktionen aufrufen (ihnen zugeordnet sind), indem Sie diese aus dem **Server-Explorer** oder dem **Datenbank-Explorer** in den **O/R-Designer** ziehen. Gespeicherte Prozeduren und Funktionen werden dem **O/R-Designer** als Methoden von <xref:System.Data.Linq.DataContext> hinzugefügt.

> [!NOTE]
> Wenn Sie gespeicherte Prozeduren und Funktionen aus dem **Server-Explorer** oder **Datenbank-Explorer** in den **O/R-Designer** ziehen, unterscheidet sich der Rückgabetyp der generierten <xref:System.Data.Linq.DataContext>-Methode je nach dem Ablageort des Elements. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurieren von DataContext zum Speichern von Daten zwischen Entitätsklassen und einer Datenbank mithilfe von gespeicherten Prozeduren

Wie bereits angemerkt wurde, können <xref:System.Data.Linq.DataContext>-Methoden erstellt werden, die gespeicherte Prozeduren und Funktionen aufrufen. Zudem können auch gespeicherte Prozeduren zuordnen, die für das LINQ to SQL-Standardlaufzeitverhalten verwendet werden, das Einfüge-, Update- und Löschvorgänge ausführt. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktionen zum Aktualisieren, Einfügen und Löschen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Vererbung und der O/R-Designer

Wie andere Objekte auch können LINQ to SQL-Klassen vererben und von anderen Klassen abgeleitet werden. Vererbungsbeziehungen werden in einer Datenbank auf verschiedene Arten erstellt. Der **O/R-Designer** unterstützt das häufig in relationalen Systemen implementierte Konzept der Einzeltabellenvererbung (Single-Table Inheritance). Weitere Informationen finden Sie unter [Vorgehensweise: Configure inheritance by using the O/R Designer (Vorgehensweise: Konfigurieren der Vererbung mit dem O/R-Designer)](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>LINQ to SQL-Abfragen

Die vom **O/R-Designer** erstellten Entitätsklassen sind für die [Language Integrated Query-Syntax (LINQ)](/dotnet/csharp/linq/) konzipiert. Weitere Informationen finden Sie unter [Vorgehensweise: Abfragen von Informationen](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Trennen des erstellten DataContext- und Entitätsklassencodes in verschiedene Namespaces

Der **O/R-Designer** stellt die Eigenschaften **Kontextnamespace** und **Entitätsnamespace** für <xref:System.Data.Linq.DataContext> bereit. Mit diesen Eigenschaften wird festgelegt in welchen Namespace der <xref:System.Data.Linq.DataContext> und der Entitätsklassencode generiert werden. Standardmäßig sind diese Eigenschaften leer, und der <xref:System.Data.Linq.DataContext> und die Entitätsklassen werden in den Namespace der Anwendung generiert. Geben Sie einen Wert in die Eigenschaften **Context Namespace** und/oder **Entity Namespace** ein, um den Code in einem anderen Namespace als dem der Anwendung zu generieren.

## <a name="reference-content"></a>Referenzinhalt

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Weitere Informationen

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Häufig gestellte Fragen (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)
