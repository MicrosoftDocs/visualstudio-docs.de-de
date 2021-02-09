---
title: Einfügen neuer Datensätze in eine Datenbank
description: Einfügen neuer Datensätze in eine Datenbank mithilfe der TableAdapter. Update-Methode, einer der DBDirect-Methoden des TableAdapter oder Befehls Objekten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 8b5228d463bebf7ed57c68cbcf16a1d767d94917
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858669"
---
# <a name="insert-new-records-into-a-database"></a>Einfügen neuer Datensätze in eine Datenbank

Wenn Sie neue Datensätze in eine Datenbank einfügen möchten, können Sie die `TableAdapter.Update` -Methode oder eine der DBDirect-Methoden des TableAdapter (insbesondere die- `TableAdapter.Insert` Methode) verwenden. Weitere Informationen finden Sie unter [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Wenn Ihre Anwendung keine TableAdapters verwendet, können Sie Befehls Objekte (z. b.  <xref:System.Data.SqlClient.SqlCommand> ) verwenden, um neue Datensätze in die Datenbank einzufügen.

Wenn Ihre Anwendung Datasets verwendet, um Daten zu speichern, verwenden Sie die- `TableAdapter.Update` Methode. Die- `Update` Methode sendet alle Änderungen (Updates, Einfügungen und Löschungen) an die Datenbank.

Wenn Ihre Anwendung Objekte zum Speichern von Daten verwendet oder Sie eine präzisere Kontrolle über das Erstellen neuer Datensätze in der Datenbank wünschen, verwenden Sie die- `TableAdapter.Insert` Methode.

Wenn der TableAdapter nicht über eine- `Insert` Methode verfügt, bedeutet dies, dass entweder der TableAdapter für die Verwendung gespeicherter Prozeduren konfiguriert ist oder seine- `GenerateDBDirectMethods` Eigenschaft auf festgelegt ist `false` . Legen Sie die-Eigenschaft des TableAdapter in `GenerateDBDirectMethods` `true` der **DataSet-Designer** auf fest, und speichern Sie dann das DataSet. Dadurch wird der TableAdapter neu generiert. Wenn der TableAdapter immer noch nicht über eine- `Insert` Methode verfügt, stellt die Tabelle wahrscheinlich nicht genügend Schema Informationen zur Verfügung, um zwischen einzelnen Zeilen zu unterscheiden (es kann z. b. kein Primärschlüssel für die Tabelle festgelegt werden).

## <a name="insert-new-records-by-using-tableadapters"></a>Einfügen neuer Datensätze mithilfe von TableAdapters

TableAdapters bieten verschiedene Möglichkeiten zum Einfügen neuer Datensätze in eine Datenbank, abhängig von den Anforderungen Ihrer Anwendung.

Wenn Ihre Anwendung Datasets verwendet, um Daten zu speichern, können Sie einfach neue Datensätze zu den gewünschten <xref:System.Data.DataTable> im DataSet hinzufügen und dann die-Methode aufzurufen `TableAdapter.Update` . Die- `TableAdapter.Update` Methode sendet alle Änderungen im <xref:System.Data.DataTable> an die Datenbank (einschließlich der geänderten und gelöschten Datensätze).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>So fügen Sie mithilfe der TableAdapter. Update-Methode neue Datensätze in eine Datenbank ein

1. Fügen Sie der gewünschten neue Datensätze hinzu, <xref:System.Data.DataTable> indem Sie ein neues erstellen <xref:System.Data.DataRow> und es der-Auflistung hinzufügen <xref:System.Data.DataTable.Rows%2A> .

2. Nachdem die neuen Zeilen hinzugefügt <xref:System.Data.DataTable> wurden, wird die- `TableAdapter.Update` Methode aufgerufen. Sie können die zu Aktualisier Ende Datenmenge steuern, indem Sie entweder ein gesamtes <xref:System.Data.DataSet> , ein <xref:System.Data.DataTable> , ein Array von <xref:System.Data.DataRow> s oder einen einzelnen übergeben <xref:System.Data.DataRow> .

   Der folgende Code zeigt, wie ein neuer Datensatz zu einem hinzugefügt <xref:System.Data.DataTable> und anschließend die-Methode aufgerufen wird `TableAdapter.Update` , um die neue Zeile in der Datenbank zu speichern. (In diesem Beispiel wird die- `Region` Tabelle in der Northwind-Datenbank verwendet.)

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>So fügen Sie mithilfe der TableAdapter. Insert-Methode neue Datensätze in eine Datenbank ein

Wenn Ihre Anwendung Objekte zum Speichern von Daten verwendet, können Sie die-Methode verwenden, `TableAdapter.Insert` um neue Zeilen direkt in der Datenbank zu erstellen. Die- `Insert` Methode akzeptiert die einzelnen Werte für jede Spalte als Parameter. Durch Aufrufen der-Methode wird ein neuer Datensatz in die Datenbank eingefügt, wobei die Parameterwerte übergeben werden.

- Wenden Sie die-Methode des TableAdapter `Insert` an, und übergeben Sie die Werte für jede Spalte als Parameter.

Das folgende Verfahren veranschaulicht die Verwendung der- `TableAdapter.Insert` Methode zum Einfügen von Zeilen. In diesem Beispiel werden Daten in die- `Region` Tabelle der Northwind-Datenbank eingefügt.

> [!NOTE]
> Wenn keine Instanz verfügbar ist, instanziieren Sie den TableAdapter, den Sie verwenden möchten.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Einfügen neuer Datensätze mithilfe von Befehls Objekten

Mithilfe von Befehls Objekten können Sie neue Datensätze direkt in eine Datenbank einfügen.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>So fügen Sie mithilfe von Befehls Objekten neue Datensätze in eine Datenbank ein

- Erstellen Sie ein neues Befehls Objekt, und legen Sie dann die `Connection` `CommandType` Eigenschaften, und fest `CommandText` .

Im folgenden Beispiel wird veranschaulicht, wie Datensätze mithilfe des Befehls Objekts in eine Datenbank eingefügt werden. Es fügt Daten in die `Region` Tabelle in der Northwind-Datenbank ein.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-security"></a>.NET-Sicherheit

Sie müssen Zugriff auf die Datenbank haben, mit der Sie eine Verbindung herstellen möchten, sowie die Berechtigung zum Ausführen von Einfügungen in die gewünschte Tabelle.

## <a name="see-also"></a>Weitere Informationen

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
