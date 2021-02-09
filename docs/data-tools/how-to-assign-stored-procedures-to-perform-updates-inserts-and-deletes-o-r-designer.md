---
title: Verwenden von gespeicherten Prozeduren in LINQ to SQL zum Aktualisieren von Daten
description: Verwenden Sie gespeicherte Prozeduren im LINQ to SQL objektrelationaler Designer (O/R-Designer), um Updates, Einfügungen und Löschungen von Daten auszuführen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f0b7ab161a252e1d3a89ef856325963bddffdc56
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866852"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktionen zum Aktualisieren, Einfügen und Löschen (O/R-Designer)

Gespeicherte Prozeduren können dem **O/R-Designer** hinzugefügt und als typische <xref:System.Data.Linq.DataContext>-Methoden ausgeführt werden. Sie können auch verwendet werden, um das standardmäßige LINQ to SQL Laufzeitverhalten zu überschreiben, das Einfügungen, Updates und Löschungen durchführt, wenn Änderungen von Entitäts Klassen in einer Datenbank gespeichert werden (z. b. beim Aufrufen der- <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Methode).

> [!NOTE]
> Wenn Ihre gespeicherte Prozedur Werte zurückgibt, die an den Client zurückgesendet werden müssen (beispielsweise Werte, die in der gespeicherten Prozedur berechnet werden), sollten Sie Ausgabeparameter in Ihrer gespeicherten Prozedur erstellen. Wenn Sie keine Ausgabeparameter verwenden können, sollten Sie eine partielle Methodenimplementierung schreiben und sich nicht auf vom O/R-Designer erzeugte Überschreibungen verlassen. Member, die datenbankgenerierten Werten zugeordnet werden, müssen nach erfolgreicher Beendigung von INSERT- oder UPDATE-Vorgängen auf entsprechende Werte festgelegt werden. Weitere Informationen finden Sie unter [Zuständigkeiten des Entwicklers beim Überschreiben des Standard Verhaltens](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> LINQ to SQL behandelt von der Datenbank generierte Werte automatisch für Identitäts-(automatische Inkrement-), ROWGUIDCOL-(Daten Bank generierte GUID) und Zeitstempel-Spalten. Datenbankgenerierte Werte in anderen Spaltentypen führen unerwartet zu einem NULL-Wert. Um die Daten Bank generierten Werte zurückzugeben, sollten Sie manuell <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> auf **true** und <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> auf einen der folgenden Werte festlegen: [AutoSync. Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync. OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)oder [AutoSync. OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Konfigurieren des Aktualisierungs Verhaltens einer Entitäts Klasse

Standardmäßig wird die Logik zum Aktualisieren einer Datenbank (Einfügungen, Updates und Löschungen) mit Änderungen, die an den Daten in LINQ to SQL Entitäts Klassen vorgenommen wurden, von der LINQ to SQL Laufzeit bereitgestellt. Basierend auf dem Schema der Tabelle (den Spalten- und Primärschlüsselinformationen) werden von der Laufzeit Standardbefehle für INSERT, UPDATE und DELETE erstellt. Wenn das Standardverhalten nicht erwünscht ist, kann das Updateverhalten konfiguriert werden, indem spezielle gespeicherte Prozeduren zur Durchführung der erforderlichen Einfüge-, Update- und Löschvorgänge für die Bearbeitung der Daten in der Tabelle zugewiesen werden. Diese Vorgehensweise ist auch dann sinnvoll, wenn kein Standardverhalten erzeugt wird, z. B. wenn die Entitätsklassen Ansichten zugeordnet sind. Schließlich kann das standardmäßige Updateverhalten auch dann überschrieben werden, wenn die Datenbank den Zugriff auf Tabellen über gespeicherte Prozeduren erfordert.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>So weisen Sie gespeicherte Prozeduren zu, um das Standardverhalten einer Entitätsklasse zu überschreiben

1. Öffnen Sie die **LINQ to SQL**-Datei im Designer. (Doppelklicken Sie im **Projektmappen-Explorer** auf die **DBML**-Datei.)

2. Erweitern Sie im **Server-Explorer** oder **Datenbank-Explorer** den Knoten **Gespeicherte Prozeduren**, und suchen Sie die gespeicherten Prozeduren, die für die Einfüge-, Update- und/oder Löschbefehle der Entitätsklasse verwendet werden sollen.

3. Ziehen Sie die gespeicherte Prozedur in den **O/R-Designer**.

     Die gespeicherte Prozedur wird dem Methodenbereich als <xref:System.Data.Linq.DataContext>-Methode hinzugefügt. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Wählen Sie die Entitätsklasse aus, für die die gespeicherte Prozedur zur Durchführung von Updates verwendet werden soll.

5. Wählen Sie im Fenster **Eigenschaften** den Befehl aus, der überschrieben werden soll (**Einfügen**, **Aktualisieren** oder **Löschen**).

6. Klicken Sie auf die Auslassungszeichen (...) neben den Wörtern **Laufzeit verwenden**, um das Dialogfeld **Verhalten konfigurieren** zu öffnen.

7. Klicken Sie auf **Anpassen**.

8. Wählen Sie die gewünschte gespeicherte Prozedur in der Liste **Anpassen** aus.

9. Untersuchen Sie die Listen **Methodenargumente** und **Klasseneigenschaften**, um zu überprüfen, ob die **Methodenargumente** den entsprechenden **Klasseneigenschaften** zugeordnet sind. Ordnen Sie die ursprünglichen Methodenargumente ( `Original_<ArgumentName>` ) den ursprünglichen Eigenschaften ( `<PropertyName> (Original)` ) für die `Update` Befehle und zu `Delete` .

    > [!NOTE]
    > Standardmäßig werden Methodenargumente Klasseneigenschaften zugeordnet, wenn die Namen übereinstimmen. Wenn geänderte Eigenschaftennamen von Tabelle und Entitätsklasse nicht mehr übereinstimmen, kann es notwendig sein, die entsprechende Klasseneigenschaft für die Zuordnung auszuwählen, wenn der Designer die korrekte Zuordnung nicht ermitteln kann.

10. Klicken Sie auf **OK** oder **Übernehmen**.

    > [!NOTE]
    > Sie können das Verhalten für jede Kombination aus Klasse und Verhalten weiterhin konfigurieren, **solange Sie auf Übernehmen klicken,** nachdem Sie die Änderungen vorgenommen haben. Wenn Sie die Klasse oder das Verhalten ändern, bevor **Sie auf über** nehmen klicken, wird ein Warn Dialogfeld angezeigt, in dem Sie die Änderungen übernehmen können.

Um zur Verwendung der Standardlaufzeitlogik für Updates zurückzukehren, klicken Sie im Fenster **Eigenschaften** auf die Auslassungszeichen neben dem **Einfüge-**, **Update-** oder **Löschbefehl**, und wählen Sie dann im Dialogfeld **Verhalten konfigurieren** die Option **Laufzeit verwenden** aus.

## <a name="see-also"></a>Weitere Informationen

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext-Methoden](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [INSERT-, Update-und DELETE-Vorgänge (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)
