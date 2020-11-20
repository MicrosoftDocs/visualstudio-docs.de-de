---
title: Überprüfen von Daten in Datasets
description: Erfahren Sie, wie Sie Daten in Datasets validieren. Beim Validieren von Daten wird bestätigt, dass in Datenobjekte eingegebene Werte den Einschränkungen im Schema eines Datasets entsprechen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cde45c4086b93713fe6e5223c1725538c0880491
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998303"
---
# <a name="validate-data-in-datasets"></a>Überprüfen von Daten in Datasets
Beim Validieren von Daten wird bestätigt, dass die Werte, die in Datenobjekte eingegeben werden, den Einschränkungen im Schema eines Datasets entsprechen. Der Überprüfungsprozess bestätigt auch, dass diese Werte den Regeln entsprechen, die für Ihre Anwendung eingerichtet wurden. Es empfiehlt sich, Daten vor dem Senden von Aktualisierungen an die zugrunde liegende Datenbank zu validieren. Dadurch werden Fehler sowie die potenzielle Anzahl von Roundtrips zwischen einer Anwendung und der Datenbank reduziert.

Sie können überprüfen, ob die Daten, die in ein Dataset geschrieben werden, gültig sind, indem Sie Validierungs Überprüfungen in das Dataset selbst durchführen. Das DataSet kann die Daten unabhängig davon überprüfen, wie das Update ausgeführt wird – ob direkt durch Steuerelemente in einem Formular, innerhalb einer Komponente oder auf andere Weise. Da das DataSet Teil der Anwendung ist (im Gegensatz zum Database Backend), ist es ein logischer Speicherort zum Erstellen einer anwendungsspezifischen Validierung.

Der beste Ort zum Hinzufügen von Validierungen zu Ihrer Anwendung ist die partielle Klassendatei des Datasets. Öffnen Sie in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oder [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] die **DataSet-Designer** , und doppelklicken Sie auf die Spalte oder Tabelle, für die Sie die Überprüfung erstellen möchten. Diese Aktion erstellt automatisch einen <xref:System.Data.DataTable.ColumnChanging> - <xref:System.Data.DataTable.RowChanging> Ereignishandler oder einen-Ereignishandler.

## <a name="validate-data"></a>Überprüfen von Daten
Die Validierung innerhalb eines Datasets erfolgt auf folgende Weise:

- Durch Erstellen einer eigenen anwendungsspezifischen Validierung, die während der Änderungen Werte in einer einzelnen Datenspalte überprüfen kann. Weitere Informationen finden Sie unter Gewusst wie: Überprüfen von [Daten während der Spalten Änderungen](validate-data-in-datasets.md).

- Durch Erstellen einer eigenen anwendungsspezifischen Validierung, mit der Daten auf Werte überprüft werden können, während eine gesamte Daten Zeile geändert wird. Weitere Informationen finden Sie unter Gewusst wie: Überprüfen von [Daten während der Zeilen Änderungen](validate-data-in-datasets.md).

- Durch Erstellen von Schlüsseln, UNIQUE-Einschränkungen usw. als Teil der eigentlichen Schema Definition des Datasets.

- Durch Festlegen der Eigenschaften des <xref:System.Data.DataColumn> Objekts, z <xref:System.Data.DataColumn.MaxLength%2A> . b., <xref:System.Data.DataColumn.AllowDBNull%2A> und <xref:System.Data.DataColumn.Unique%2A> .

<xref:System.Data.DataTable>Beim Auftreten einer Änderung in einem Datensatz werden vom-Objekt mehrere Ereignisse ausgelöst:

- Das <xref:System.Data.DataTable.ColumnChanging> -Ereignis und das- <xref:System.Data.DataTable.ColumnChanged> Ereignis werden während und nach jeder Änderung an einer einzelnen Spalte ausgelöst. Das <xref:System.Data.DataTable.ColumnChanging> Ereignis ist hilfreich, wenn Sie Änderungen in bestimmten Spalten überprüfen möchten. Informationen über die vorgeschlagene Änderung werden als Argument mit dem Ereignis übermittelt.
- Das <xref:System.Data.DataTable.RowChanging> -Ereignis und das- <xref:System.Data.DataTable.RowChanged> Ereignis werden während und nach jeder Änderung in einer Zeile ausgelöst. Das <xref:System.Data.DataTable.RowChanging> Ereignis ist allgemeinerer. Es zeigt an, dass eine Änderung an einer beliebigen Stelle in der Zeile stattfindet, aber Sie wissen nicht, welche Spalte geändert wurde.

Standardmäßig löst jede Änderung an einer Spalte vier Ereignisse aus. Das erste ist das <xref:System.Data.DataTable.ColumnChanging> -Ereignis und das- <xref:System.Data.DataTable.ColumnChanged> Ereignis für die jeweilige Spalte, die geändert wird. Als nächstes werden <xref:System.Data.DataTable.RowChanging> die <xref:System.Data.DataTable.RowChanged> Ereignisse und angezeigt. Wenn mehrere Änderungen an der Zeile vorgenommen werden, werden die Ereignisse für jede Änderung ausgelöst.

> [!NOTE]
> Die-Methode der Daten Zeile deaktiviert <xref:System.Data.DataRow.BeginEdit%2A> das <xref:System.Data.DataTable.RowChanging> -Ereignis und das- <xref:System.Data.DataTable.RowChanged> Ereignis, nachdem sich jede einzelne Spalte geändert hat. In diesem Fall wird das-Ereignis erst ausgelöst, <xref:System.Data.DataRow.EndEdit%2A> Wenn die-Methode aufgerufen wurde, wenn das <xref:System.Data.DataTable.RowChanging> -Ereignis und das-Ereignis <xref:System.Data.DataTable.RowChanged> nur einmal ausgelöst werden. Weitere Informationen finden Sie unter [Deaktivieren von Einschränkungen beim Auffüllen eines Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

Welches Ereignis Sie auswählen, hängt davon ab, wie präzise die Validierung sein soll. Wenn es wichtig ist, dass Sie einen Fehler sofort abfangen, wenn eine Spalte geändert wird, erstellen Sie die Überprüfung mithilfe des- <xref:System.Data.DataTable.ColumnChanging> Ereignisses. Verwenden Sie andernfalls das- <xref:System.Data.DataTable.RowChanging> Ereignis, das dazu führen kann, dass mehrere Fehler gleichzeitig abgefangen werden. Wenn die Daten außerdem so strukturiert sind, dass der Wert einer Spalte basierend auf dem Inhalt einer anderen Spalte überprüft wird, führen Sie die Überprüfung während des <xref:System.Data.DataTable.RowChanging> Ereignisses aus.

Wenn Datensätze aktualisiert werden, löst das- <xref:System.Data.DataTable> Objekt Ereignisse aus, auf die Sie reagieren können, wenn Änderungen auftreten und nachdem Änderungen vorgenommen wurden.

Wenn Ihre Anwendung ein typisiertes DataSet verwendet, können Sie stark typisierte Ereignishandler erstellen. Dadurch werden vier weitere typisierte Ereignisse hinzugefügt, für die Sie Handler erstellen können: `dataTableNameRowChanging` , `dataTableNameRowChanged` , `dataTableNameRowDeleting` und `dataTableNameRowDeleted` . Diese typisierten Ereignishandler übergeben ein Argument, das die Spaltennamen der Tabelle enthält, die das Schreiben und Lesen von Code vereinfachen.

## <a name="data-update-events"></a>Daten Aktualisierungs Ereignisse

|event|BESCHREIBUNG|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Der Wert in einer Spalte wird geändert. Das Ereignis übergibt die Zeile und die Spalte zusammen mit dem vorgeschlagenen neuen Wert.|
|<xref:System.Data.DataTable.ColumnChanged>|Der Wert in einer Spalte wurde geändert. Das Ereignis übergibt die Zeile und die Spalte zusammen mit dem vorgeschlagenen Wert an Sie.|
|<xref:System.Data.DataTable.RowChanging>|Die an einem-Objekt vorgenommenen Änderungen <xref:System.Data.DataRow> werden im Begriff, wieder in das DataSet zurückgegeben. Wenn Sie die-Methode nicht aufgerufen haben <xref:System.Data.DataRow.BeginEdit%2A> , <xref:System.Data.DataTable.RowChanging> wird das-Ereignis für jede Änderung an einer Spalte ausgelöst, unmittelbar nachdem das- <xref:System.Data.DataTable.ColumnChanging> Ereignis ausgelöst wurde. Wenn Sie <xref:System.Data.DataRow.BeginEdit%2A> vor dem vornehmen von Änderungen aufgerufen haben, wird das- <xref:System.Data.DataTable.RowChanging> Ereignis nur ausgelöst, wenn Sie die- <xref:System.Data.DataRow.EndEdit%2A> Methode aufrufen.<br /><br /> Das Ereignis übergibt die Zeile zusammen mit einem Wert, der angibt, welcher Aktionstyp (Änderung, einfügen usw.) ausgeführt wird.|
|<xref:System.Data.DataTable.RowChanged>|Eine Zeile wurde geändert. Das Ereignis übergibt die Zeile zusammen mit einem Wert, der angibt, welcher Aktionstyp (Änderung, einfügen usw.) ausgeführt wird.|
|<xref:System.Data.DataTable.RowDeleting>|Eine Zeile wird gelöscht. Das Ereignis übergibt die Zeile zusammen mit einem Wert, der angibt, welcher Typ von Aktion (Delete) ausgeführt wird.|
|<xref:System.Data.DataTable.RowDeleted>|Eine Zeile wurde gelöscht. Das Ereignis übergibt die Zeile zusammen mit einem Wert, der angibt, welcher Typ von Aktion (Delete) ausgeführt wird.|

Die <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> -,-und- <xref:System.Data.DataTable.RowDeleting> Ereignisse werden während des Aktualisierungs Vorgangs ausgelöst. Sie können diese Ereignisse verwenden, um Daten zu validieren oder andere Verarbeitungs Typen auszuführen. Da das Update während dieser Ereignisse gerade verarbeitet wird, können Sie es durch Auslösen einer Ausnahme abbrechen, wodurch das Beenden des Updates verhindert wird.

Die <xref:System.Data.DataTable.ColumnChanged> <xref:System.Data.DataTable.RowChanged> Ereignisse, und <xref:System.Data.DataTable.RowDeleted> sind Benachrichtigungs Ereignisse, die ausgelöst werden, wenn das Update erfolgreich abgeschlossen wurde. Diese Ereignisse sind hilfreich, wenn Sie basierend auf einem erfolgreichen Update weitere Aktionen ausführen möchten.

## <a name="validate-data-during-column-changes"></a>Validieren von Daten während der Spalten Änderungen

> [!NOTE]
> Der **DataSet-Designer** erstellt eine partielle Klasse, in der Validierungs Logik einem DataSet hinzugefügt werden kann. Das vom Designer generierte Dataset löscht oder ändert keinen Code in der partiellen Klasse.

Sie können Daten überprüfen, wenn sich der Wert in einer Datenspalte ändert, indem Sie auf das- <xref:System.Data.DataTable.ColumnChanging> Ereignis reagieren. Wenn dieses Ereignis ausgelöst wird, übergibt dieses Ereignis ein Ereignis Argument ( <xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A> ), das den Wert enthält, der für die aktuelle Spalte vorgeschlagen wird. Basierend auf dem Inhalt von `e.ProposedValue` können Sie folgende Aktionen ausführen:

- Den vorgeschlagenen Wert annehmen, indem Sie nichts tun.

- Ablehnen Sie den vorgeschlagenen Wert, indem Sie den Spalten Fehler ( <xref:System.Data.DataRow.SetColumnError%2A> ) aus dem Ereignishandler für die Spalten Änderung festlegen.

- Optional können Sie ein <xref:System.Windows.Forms.ErrorProvider>-Steuerelement verwenden, um dem Benutzer eine Fehlermeldung anzuzeigen. Weitere Informationen finden Sie unter [ErrorProvider Component (ErrorProvider-Komponente)](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

Die Validierung kann auch während des Ereignisses ausgeführt werden <xref:System.Data.DataTable.RowChanging> .

## <a name="validate-data-during-row-changes"></a>Validieren von Daten während der Zeilen Änderungen
Sie können Code schreiben, um sicherzustellen, dass alle zu validierenden Spalten Daten enthalten, die den Anforderungen der Anwendung entsprechen. Legen Sie hierzu die Spalte fest, um anzugeben, dass Sie einen Fehler enthält, wenn ein vorgeschlagene Wert nicht zulässig ist. In den folgenden Beispielen wird ein Spaltenfehler festgelegt, wenn für die `Quantity`-Spalte ein Wert von 0 oder weniger gilt. Die Ereignishandler für Zeilenänderungen sollten den folgenden Beispielen entsprechen.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>So validieren Sie Daten bei Zeilenänderungen (Visual Basic)

1. Öffnen Sie das Dataset im **DataSet-Designer**. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Datasets in der DataSet-Designer](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Doppelklicken Sie auf die Titelleiste der zu validierenden Tabelle. Durch diese Aktion wird der <xref:System.Data.DataTable.RowChanging>-Ereignishandler der <xref:System.Data.DataTable> in der Datei für die partielle Klasse des Datasets automatisch erstellt.

    > [!TIP]
    > Doppelklicken Sie links neben den Tabellennamen, um den Ereignishandler für Zeilenänderungen zu erstellen. Wenn Sie auf den Tabellennamen doppelklicken, können Sie ihn bearbeiten.

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

### <a name="to-validate-data-when-a-row-changes-c"></a>So validieren Sie Daten bei Zeilenänderungen (C#)

1. Öffnen Sie das Dataset im **DataSet-Designer**. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Datasets in der DataSet-Designer](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Doppelklicken Sie auf die Titelleiste der zu validierenden Tabelle. Durch diese Aktion wird eine Datei für die partielle Klasse der <xref:System.Data.DataTable> erstellt.

    > [!NOTE]
    > Der **DataSet-Designer** erstellt nicht automatisch einen Ereignishandler für das <xref:System.Data.DataTable.RowChanging>-Ereignis. Sie müssen eine Methode erstellen, um das Ereignis zu behandeln <xref:System.Data.DataTable.RowChanging> , und Code ausführen, um das Ereignis in der Initialisierungs Methode der Tabelle einzuschließen.

3. Kopieren Sie den folgenden Code in die partielle Klasse:

    ```csharp
    public override void EndInit()
    {
        base.EndInit();
        Order_DetailsRowChanging += TestRowChangeEvent;
    }

    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)
    {
        if ((short)e.Row.Quantity <= 0)
        {
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
        }
        else
        {
            e.Row.SetColumnError("Quantity", "");
        }
    }
    ```

## <a name="to-retrieve-changed-rows"></a>So rufen Sie geänderte Zeilen ab
Jede Zeile in einer Datentabelle verfügt über eine- <xref:System.Data.DataRow.RowState%2A> Eigenschaft, die den aktuellen Status der Zeile nachverfolgt, indem die Werte in der- <xref:System.Data.DataRowState> Enumeration verwendet werden. Sie können geänderte Zeilen aus einem DataSet oder einer Datentabelle zurückgeben, indem Sie die- `GetChanges` Methode eines oder eines aufrufen <xref:System.Data.DataSet> <xref:System.Data.DataTable> . Sie können überprüfen, ob vor dem Aufrufen von Änderungen vorhanden sind, `GetChanges` indem Sie die- <xref:System.Data.DataSet.HasChanges%2A> Methode eines Datasets aufrufen.

> [!NOTE]
> Nachdem Sie die Änderungen an einem DataSet oder einer Datentabelle (durch Aufrufen der- <xref:System.Data.DataSet.AcceptChanges%2A> Methode) übernommen haben, `GetChanges` gibt die Methode keine Daten zurück. Wenn die Anwendung geänderte Zeilen verarbeiten muss, müssen Sie die Änderungen verarbeiten, bevor Sie die- `AcceptChanges` Methode aufrufen.

Wenn Sie die- <xref:System.Data.DataSet.GetChanges%2A> Methode eines Datasets oder einer Datentabelle aufrufen, wird ein neues DataSet oder eine Datentabelle zurückgegeben, das nur geänderte Datensätze enthält. Wenn Sie bestimmte Datensätze – z. b. nur neue Datensätze oder nur geänderte Datensätze – erhalten möchten, können Sie einen Wert aus der- <xref:System.Data.DataRowState> Enumeration als Parameter an die- `GetChanges` Methode übergeben.

Verwenden Sie die- <xref:System.Data.DataRowVersion> Enumeration, um auf die verschiedenen Versionen einer Zeile zuzugreifen (z. b. die ursprünglichen Werte, die sich vor der Verarbeitung in einer Zeile befanden).

### <a name="to-get-all-changed-records-from-a-dataset"></a>So erhalten Sie alle geänderten Datensätze aus einem DataSet

- Ruft die- <xref:System.Data.DataSet.GetChanges%2A> Methode eines Datasets auf.

     Im folgenden Beispiel wird ein neues Dataset mit dem Namen erstellt `changedRecords` und mit allen geänderten Datensätzen aus einem anderen Dataset mit dem Namen aufgefüllt `dataSet1` .

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

### <a name="to-get-all-changed-records-from-a-data-table"></a>So erhalten Sie alle geänderten Datensätze aus einer Datentabelle

- Ruft die- <xref:System.Data.DataTable.GetChanges%2A> Methode einer Datentabelle auf.

     Im folgenden Beispiel wird eine neue Datentabelle mit dem Namen erstellt `changedRecordsTable` und mit allen geänderten Datensätzen aus einer anderen Datentabelle mit dem Namen aufgefüllt `dataTable1` .

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>So erhalten Sie alle Datensätze mit einem bestimmten Zeilen Status

- Ruft die `GetChanges` -Methode eines Datasets oder einer Datentabelle auf und übergibt einen- <xref:System.Data.DataRowState> Enumerationswert als Argument.

     Im folgenden Beispiel wird gezeigt, wie Sie ein neues DataSet `addedRecords` mit dem Namen erstellen und nur mit Datensätzen auffüllen, die dem `dataSet1` DataSet hinzugefügt wurden.

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     Im folgenden Beispiel wird gezeigt, wie alle Datensätze zurückgegeben werden, die der Tabelle kürzlich hinzugefügt wurden `Customers` :

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>Zugreifen auf die ursprüngliche Version einer DataRow
Wenn an Datenzeilen Änderungen vorgenommen werden, werden im Dataset sowohl die ursprüngliche (<xref:System.Data.DataRowVersion.Original>) als auch die neue (<xref:System.Data.DataRowVersion.Current>) Version der Zeile beibehalten. Vor dem Aufruf der `AcceptChanges`-Methode kann die Anwendung z. B. auf die verschiedenen (in der <xref:System.Data.DataRowVersion>-Enumeration definierten) Versionen eines Datensatzes zugreifen und die Änderungen entsprechend verarbeiten.

> [!NOTE]
> Unterschiedliche Versionen einer Zeile sind erst vorhanden, nachdem Sie bearbeitet wurde und bevor die- `AcceptChanges` Methode aufgerufen wurde. Nach dem Aufruf der `AcceptChanges`-Methode sind die ursprüngliche und die aktuelle Version identisch.

Wenn Sie den <xref:System.Data.DataRowVersion>-Wert zusammen mit dem Spaltenindex (oder dem Spaltennamen als Zeichenfolge) übergeben, wird der Wert der spezifischen Zeilenversion aus dieser Spalte zurückgegeben. Die geänderte Spalte wird während des-Ereignisses und des-Ereignisses identifiziert <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.ColumnChanged> . Dies ist ein guter Zeitpunkt, die verschiedenen Zeilen Versionen zu Validierungs Zwecken zu überprüfen. Wenn Sie jedoch Einschränkungen vorübergehend angehalten haben, werden diese Ereignisse nicht ausgelöst, und Sie müssen Programm gesteuert ermitteln, welche Spalten geändert wurden. Sie können dazu die <xref:System.Data.DataTable.Columns%2A>-Auflistung durchlaufen und die unterschiedlichen <xref:System.Data.DataRowVersion>-Werte vergleichen.

### <a name="to-get-the-original-version-of-a-record"></a>So rufen Sie die ursprüngliche Datensatzversion ab

- Greifen Sie auf den Wert einer Spalte zu, indem <xref:System.Data.DataRowVersion> Sie die der Zeile übergeben, die Sie zurückgeben möchten.

     Im folgenden Beispiel wird gezeigt, wie ein-Wert verwendet wird <xref:System.Data.DataRowVersion> , um den ursprünglichen Wert eines `CompanyName` Felds in einer zu erhalten <xref:System.Data.DataRow> :

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>Zugreifen auf die aktuelle Version einer DataRow

### <a name="to-get-the-current-version-of-a-record"></a>So rufen Sie die aktuelle Datensatzversion ab

- Greifen Sie auf den Wert einer Spalte zu, und fügen Sie dem Index einen Parameter hinzu, der die Version einer Zeile angibt, die Sie zurückgeben möchten.

     Im folgenden Beispiel wird gezeigt, wie ein-Wert verwendet wird <xref:System.Data.DataRowVersion> , um den aktuellen Wert eines `CompanyName` Felds in einer zu erhalten <xref:System.Data.DataRow> :

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>Weitere Informationen

- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Vorgehensweise: Überprüfen von Daten im Windows Forms DataGridView-Steuerelement](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Gewusst wie: Anzeigen von Fehler Symbolen für die Formular Validierung mit der Windows Forms ErrorProvider-Komponente](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)
