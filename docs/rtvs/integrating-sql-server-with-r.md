---
title: Integration von SQL Server in R
description: Visual Studio unterstützt das Erstellen und Ausführen von SQL-Abfragen aus R und die Möglichkeiten von R zum Arbeiten mit gespeicherten Prozeduren.
ms.date: 06/25/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: c0aedbccdb82bd91fe201a23b6201a3cdd7db283
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908679"
---
# <a name="work-with-sql-server-and-r"></a>Arbeiten mit SQL Server und R

Dank der hervorragenden Unterstützung von Visual Studio für SQL Server können Datenanalysten mit R- und SQL-Datenbanken arbeiten, da sie SQL-Abfragen erstellen und ausführen und mit gespeicherten Prozeduren arbeiten können.

> [!Note]
> Um mit SQL und R zu arbeiten, müssen Sie die SQL Server-Datentools installiert haben:
> - Visual Studio 2017: Führen Sie das Installationsprogramm von Visual Studio aus, und wählen Sie den Datenspeicher und die Verarbeitungsworkload aus, die SQL Server-Datentools enthält.
> - Visual Studio 2015: Befolgen Sie die Anweisungen unter [SQL Server Data Tools herunterladen](/sql/ssdt/download-sql-server-data-tools-ssdt).

:::row:::
    :::column:::
        ![Kamerasymbol für Video](../install/media/video-icon.png "Video ansehen")
    :::column-end:::
    :::column:::
        [Sehen Sie sich ein Video an (youtube.com)](https://www.youtube.com/watch?v=n4AYr0QIwdQ), um eine Übersicht über SQL Server und R zu erhalten (3 m 03s).
    :::column-end:::
:::row-end:::

## <a name="create-and-run-sql-queries"></a>Erstellen und Ausführen von SQL-Abfragen

RTVS unterstützt das Hinzufügen von SQL-Abfragen in R-Projekten, wobei Sie die Möglichkeit haben, interaktiv SQL-Abfragen in einem separaten Kontext zu entwickeln, bis Sie die gewünschten Ergebnisse erhalten.

Wenn Sie eine SQL-Abfragedatei hinzufügen möchten, klicken Sie mit der rechten Maustaste auf das Projekt im Projektmappen-Explorer, wählen Sie **Hinzufügen** > **Neues Element** und anschließend den Dateityp **SQL-Abfrage** aus:

![Hinzufügen eines SQL-Abfrageelements zu einem Projekt](media/sql-add-item.png)

Dieser Befehl wird im Transact-SQL-Editor von Visual Studio geöffnet, wobei vollständiges IntelliSense für SQL und die Möglichkeit zum Ausführen von Abfragen bereitgestellt wird. Für diese Features müssen Sie über die Schaltfläche „Verbinden“ in der Symbolleiste des Editors eine Verbindung zu einer Datenbank herstellen oder versuchen, eine Abfrage auszuführen (**STRG**+**UMSCHALT**+**E**. Dies funktioniert auch bei einer Auswahl). Egal für welche Möglichkeit Sie sich entscheiden, es wird das Dialogfeld „Verbindung“ angezeigt:

![Dialogfeld „SQL-Verbindung“](media/sql-connection-dialog.png)

Sobald eine Verbindung hergestellt wurde, können Sie Abfragen ausführen und Ergebnisse anzeigen:

![SQL-Fenster mit Abfrageergebnissen](media/sql-query-results.png)

Der Transact-SQL-Editor unterstützt eine Vielzahl anderer Funktionen, z.B. die Darstellung des Ausführungsplans für die Abfrage und einen Abfragedebugger.
Weitere Informationen finden Sie unter [Verwenden des Transact-SQL-Editors zum Bearbeiten und Ausführen von Skripts](/previous-versions/sql/sql-server-data-tools/hh272706(v=vs.103)).

## <a name="work-with-sql-server-stored-procedures"></a>Arbeiten mit gespeicherten SQL Server-Prozeduren

Durch [SQL Server-R Services](/sql/advanced-analytics/r/sql-server-r-services) (SQL Server 2016 und höher) können Sie R-Code aus einer gespeicherten T-SQL-Prozedur einbetten und ausführen. Sie können R Code auf einem SQL Server-Computer ausführen, für von einer SQL-Abfrage zurückgegebene Daten nutzen und ein SQL-Resultset generieren, das von SQL weiterverarbeitet oder an den Client zurückgegeben werden kann.

RTVS vereinfacht den ansonsten komplizierten und fehleranfälligen Prozess zum Kombinieren von SQL und R-Code in einer SQL-Anweisung, so wie in den folgenden Abschnitten beschrieben:

- [Hinzufügen einer Datenbankverbindung](#add-a-database-connection)
- [Schreiben und Testen einer in SQL gespeicherten Prozedur](#write-and-test-a-sql-stored-procedure)
- [Veröffentlichen einer in SQL gespeicherten Prozedur](#publish-a-sql-stored-procedure)

:::row:::
    :::column:::
        ![Kamerasymbol für Video](../install/media/video-icon.png "Video ansehen")
    :::column-end:::
    :::column:::
        [Sehen Sie sich ein Video an (youtube.com)](https://www.youtube.com/watch?v=dFKIT2OitWQ), um eine Übersicht über R und gespeicherte SQL-Prozeduren zu erhalten (6m 09s).
    :::column-end:::
:::row-end:::

### <a name="add-a-database-connection"></a>Hinzufügen einer Datenbankverbindung

1. Wählen Sie **R Tools** > **Daten** > **Datenbankverbindung hinzufügen** aus, um das Dialogfeld **Verbindungseigenschaften** zu öffnen. Hier geben Sie den Namen der Datenquelle (in diesem Fall SQL Server), den Namen des Servers, den Authentifizierungsmodus und den Namen der Datenbank an. Klicken Sie auf **Testverbindung**, um Ihre Eingabe zu überprüfen, bevor Sie das Dialogfeld schließen.

    ![SQL-Verbindung (Dialogfeld)](media/sql-connection-string-dialog.png)

1. Sobald Sie auf **OK** geklickt haben, generiert Visual Studio bei einer gültigen Verbindung in einer neuen *settings.R*-Datei eine Verbindungszeichenfolge mit dem Namen `dbConnection`. RTVS fügt diese Datei automatisch hinzu (führt dies aus), damit Sie die Verbindung von R-Skripts sofort nutzen können:

![SQL-Datei „Settings.R“](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>Schreiben und Testen einer in SQL gespeicherten Prozedur

Wenn Sie eine neue gespeicherte SQL-Prozedur hinzufügen möchten, klicken Sie mit der rechten Maustaste auf Ihr Projekt, wählen Sie **Hinzufügen** > **Neues Element** und anschließend **Gespeicherte SQL-Prozedur mit R** aus der Liste der Vorlagen aus, geben Sie der Datei einen Namen, und klicken Sie auf **OK**. Der Standarddateiname lautet *SqlSProc.R*. Der Einfachheit halber wird im übrigen Abschnitt der Dateiname *StoredProcedure.R* verwendet. Wenn Sie über mehrere gespeicherte Prozeduren verfügen, muss jede dieser Dateien einen eindeutigen Dateinamen aufweisen.

RTVS erstellt für die gespeicherte Prozedur drei Dateien: eine *.R*-Datei für Ihren R-Code, eine *.Query.sql*-Datei für den SQL-Code und eine *.Template.sql*-Datei, die die beiden Dateien vereint. Die letzten beiden Dateien werden im Projektmappen-Explorer als untergeordnete Dateien der *.R*-Datei angezeigt:

![Erweiterte Projektmappen-Explorer-Ansicht der gespeicherten SQL-Prozedur mit R](media/sql-solution-explorer-expanded.png)

In der *. R*-Datei (in diesem Beispiel *StoredProcedure.R*) schreiben Sie Ihren R-Code. Der Standardinhalt ist der folgende:

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

Um es einfacher auszudrücken: Der Code erhält einen R-Datenrahmen mit dem Namen `InputDataSet` und gibt dessen Ergebnisse in `OutputDataSet` zurück. Der Vorlagencode kopiert dabei lediglich die Eingabe in die Ausgabe.

> [!Note]
> Die Namen dieser Datenrahmen werden durch die Parameter `@input_data_1_name` und `@output_data_1_name` im Aufruf der im `sp_execute_external_script`-System gespeicherten Prozedur gesteuert. Weitere Informationen zum Entwurf dieser Aufrufkonvention und einige Beispiele zum Gebrauch finden Sie unter [sp_execute_external_script (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Der andere generierte Code in den Kommentaren bietet ein kleines Testskript, das das [RODBC-Paket](https://cran.r-project.org/web/packages/RODBC/index.html) zur Übermittlung einer SQL-Anweisung an SQL Server verwendet, sie ausführt und das Resultset als R-Datenrahmen abruft. Sie können die Auskommentierung dieses Testcodes aufheben, um Ihren R-Code interaktiv für das festgelegte Resultset zu schreiben, das Sie von SQL Server erhalten.

In der *.Query.sql*-Datei (in diesem Beispiel *StoredProcedure.Query.sql*) schreiben und testen Sie die SQL-Abfrage, mit der die Daten für `InputDataSet` generiert werden. Mit dieser *SQL*-Datei stellt der Editor alle üblichen Transact-SQL-Features für Sie bereit.

Sobald Sie mit Ihrem SQL-Code zufrieden sind, integrieren Sie ihn in Ihren R-Code, indem Sie die *SQL*-Datei in den offenen Editor der *.R*-Datei ziehen. In der folgenden Abbildung wurde *StoredProcedure.Query.sql* zu dem Punkt in *StoredProcedure.R*, nach dem Komma in `sqlQuery(channel, )` gezogen:

![Lesen einer SQL-Datei in eine R-Zeichenfolgenvariable](media/sql-reference-sql-file-from-r.png)

Wie Sie sehen können, wird in diesem einfachen Schritt automatisch R-Code generiert, um die *SQL*-Datei zu öffnen, deren Inhalte in einer Zeichenfolge zu lesen und sie an das RODBC-Paket zu übergeben, das an SQL Server gesendet wird.

Sie können nun interaktiv R-Code schreiben, der den `InputDataSet`-Datenrahmen wie gewünscht verändert. Beachten Sie, dass Sie nur R-Code im Editor auswählen und an das [interaktive Fenster](interactive-repl-for-r-in-visual-studio.md) senden können, indem Sie **STRG**+**Eingabetaste** drücken.

Die *.Template.sql*-Datei (in diesem Beispiel *StoredProcedure.Template.sql*) enthält schließlich die Vorlage für die Generierung Ihres gespeicherten SQL-Prozedur:

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- Der Platzhalter `_RCODE_` wird durch die Inhalte der *.R*-Datei (z.B. *StoredProcedure.R*) ersetzt.
- Der Platzhalter `_INPUT_QUERY_` wird durch die Inhalte der *.Query.sql*-Datei (z.B. *StoredProcedure.Query.sql*) ersetzt.
- Bearbeiten Sie die `WITH RESULT SETS`-Klausel, um das Schema des von der gespeicherten Prozedur zurückgegebenen Resultsets zu beschreiben. Identifizieren Sie insbesondere die Spalten aus dem `OutputDataSet`-Datenrahmen, die Sie an den Aufrufer der gespeicherten Prozedur zurückgeben möchten.

Beispielsweise für die folgende Abfrage:

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

Sie verwenden die folgende `WITH RESULT SETS`-Klausel, um die Datentypen der Rückgabewerte anzugeben:

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>Veröffentlichen einer in SQL gespeicherten Prozedur

1. Wählen Sie den Menübefehl **R Tools** > **Daten** > **Mit Optionen veröffentlichen** aus.
1. Ändern Sie im sich öffnenden Dialogfeld **Veröffentlichen an:** in **Datenbank**, geben Sie das Ziel an, wählen Sie **Veröffentlichen** aus, und RTVS erstellt die gespeicherte Prozedur und veröffentlicht sie:

    ![Dialogfeld „Gespeicherte Prozeduren veröffentlichen“](media/sql-publish-with-options.png)

1. Wenn Sie alle gespeicherten Prozeduren in einem Projekt veröffentlichen möchten, können Sie den Befehl **R Tools** > **Daten** > **Gespeicherte Prozeduren veröffentlichen** verwenden, der auch verfügbar ist, wenn Sie mit der rechten Maustaste auf das Projekt im Projektmappen-Explorer klicken.

> [!Tip]
> Wenn Sie den Objekt-Explorer von SQL Server in Visual Studio geöffnet haben, wird Ihre veröffentlichte gespeicherte Prozedur im Ordner **Programmierbarkeit** > **Gespeicherte Prozeduren** Ihrer Datenbank angezeigt. Sie können sie auch vom Objekt-Explorer aus ausführen, indem Sie einen Rechtsklick machen und **Prozedur ausführen** auswählen oder sie interaktiv aus einem *SQL*-Abfragefenster aufrufen.