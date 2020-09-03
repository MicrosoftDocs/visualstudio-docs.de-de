---
title: Erstellen und Konfigurieren von TableAdapters | Microsoft-Dokumentation
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
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a2136960dfcbbbcf63fbefeb16d527793d4b939
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72631035"
---
# <a name="create-and-configure-tableadapters"></a>Erstellen und Konfigurieren eines TableAdapters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TableAdapters ermöglichen die Kommunikation zwischen der Anwendung und einer Datenbank. Sie stellen eine Verbindung mit der Datenbank her, führen Abfragen oder gespeicherte Prozeduren aus und geben entweder eine neue Datentabelle zurück oder füllen eine vorhandene <xref:System.Data.DataTable> mit den zurückgegebenen Daten. TableAdapters können auch aktualisierte Daten von der Anwendung an die Datenbank zurücksenden.

 TableAdapters werden für Sie erstellt, wenn Sie eine der folgenden Aktionen ausführen:

- Führen Sie den [Assistenten zum Konfigurieren von Datenquellen](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) aus, und wählen Sie den Daten Quellentyp **Datenbank** oder **Webdienst** aus.

- Ziehen Sie Datenbankobjekte aus [Server-Explorer](https://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) in den **DataSet-Designer**.

  Sie können einen neuen TableAdapter erstellen und ihn mit einer Datenquelle konfigurieren, indem Sie einen TableAdapter aus der Toolbox in einen leeren Bereich auf der **DataSet-Designer** Oberfläche ziehen.

  Eine Einführung in TableAdapters finden Sie unter [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>Verwenden des TableAdapter-Konfigurations-Assistenten
 Führen Sie den **TableAdapter-Konfigurations-Assistenten** aus, um TableAdapters und die zugehörigen DataTables zu erstellen oder zu bearbeiten. Sie können einen vorhandenen TableAdapter konfigurieren, indem Sie im **DataSet-Designer**mit der rechten Maustaste darauf klicken.

 ![Assistent zum Konfigurieren von raddata-Tabellen Adaptern](../data-tools/media/raddata-table-adapter-configuration-wizard.png "Assistent zum Konfigurieren von raddata-Tabellen Adaptern")

 Wenn Sie einen neuen TableAdapter aus der Toolbox ziehen, wenn die **DataSet-Designer** im Fokus ist, werden Sie vom Assistenten aufgefordert, anzugeben, mit welcher Datenquelle der TableAdapter eine Verbindung herstellen soll und welche Art von Befehlen für die Kommunikation mit der Datenbank, SQL-Anweisungen oder gespeicherten Prozeduren verwendet werden sollen. Dies wird nicht angezeigt, wenn Sie einen TableAdapter konfigurieren, der bereits einer Datenquelle zugeordnet ist.

- Die Verwendung der **Create Methods-Methode zum direkten Senden von Updates an die Daten Bank** Option entspricht dem Festlegen der- `GenerateDBDirectMethods` Eigenschaft auf true. Die Option ist nicht verfügbar, wenn die ursprüngliche SQL-Anweisung nicht genügend Informationen bereitstellt oder die Abfrage keine aktualisierbare Abfrage darstellt. Diese Situation kann z. b. bei Verknüpfungs **Abfragen und Abfragen eintreten,** die einen einzelnen (skalaren) Wert zurückgeben.

- Sie haben die Möglichkeit, eine neue gespeicherte Prozedur in der zugrunde liegenden Datenbank zu erstellen, wenn Sie über die richtigen Berechtigungen für die Datenbank verfügen. Wenn Sie nicht über diese Berechtigungen verfügen, ist dies keine Option.

- Sie können auch vorhandene gespeicherte Prozeduren für die Befehle **Select**, **Insert**, **Update**und **Delete** des TableAdapter ausführen. Die gespeicherte Prozedur, die dem **Update** -Befehl zugewiesen ist, wird z. b. ausgeführt, wenn die- `TableAdapter.Update()` Methode aufgerufen wird.

     Ordnen Sie die Parameter der ausgewählten gespeicherten Prozedur den entsprechenden Spalten in der Datentabelle zu. Wenn Ihre gespeicherte Prozedur z. b. einen Parameter mit dem Namen akzeptiert, der `@CompanyName` an die `CompanyName` Spalte in der Tabelle übergeben wird, legen Sie die **Quell Spalte** des- `@CompanyName` Parameters auf fest `CompanyName` .

    > [!NOTE]
    > Die gespeicherte Prozedur, die dem SELECT-Befehl zugewiesen ist, wird ausgeführt, indem Sie die-Methode des TableAdapter aufrufen, den Sie im nächsten Schritt des Assistenten benennen. Die Standardmethode ist `Fill` , sodass der Code, der normalerweise zum Ausführen der SELECT-Prozedur verwendet wird, lautet `TableAdapter.Fill(tableName)` . Wenn Sie den Standardnamen von ändern `Fill` , ersetzen Sie `Fill` durch den Namen, den Sie zuweisen, und ersetzen Sie "TableAdapter" durch den tatsächlichen Namen des TableAdapters (z `CustomersTableAdapter` . b.).

- Die **erweiterten Optionen** im Assistenten ermöglichen es Ihnen, INSERT-, Update-und DELETE-Anweisungen auf der Grundlage der SELECT-Anweisung zu generieren, die auf der Seite **SQL-Anweisungen generieren** definiert ist. Verwenden Sie optimistische Parallelität, und geben Sie an, ob die Datentabelle nach dem Ausführen der Anweisungen zum Einfügen und aktualisieren aktualisiert werden soll.

## <a name="configure-a-tableadapters-fill-method"></a>Konfigurieren der Fill-Methode eines TableAdapters
 Manchmal möchten Sie möglicherweise das Schema der Tabelle "TableAdapter" ändern. Zu diesem Zweck ändern Sie die primäre Methode des TableAdapter `Fill` . TableAdapters werden mit einer primären `Fill` Methode erstellt, die das Schema der zugeordneten Datentabelle definiert. Die primäre `Fill` Methode basiert auf der Abfrage oder gespeicherten Prozedur, die Sie bei der ursprünglichen Konfiguration des TableAdapters eingegeben haben. Dabei handelt es sich um die erste (oberste) Methode unter der Datentabelle im DataSet-Designer.

 ![TableAdapter mit mehreren Abfragen](../data-tools/media/tableadapter.gif "TableAdapter")

 Alle Änderungen, die Sie an der Main-Methode des TableAdapter vornehmen, `Fill` werden im Schema der zugeordneten Datentabelle widergespiegelt. Wenn Sie z. b. eine Spalte aus der Abfrage in der Main-Methode entfernen, wird `Fill` auch die Spalte aus der zugeordneten Datentabelle entfernt. Außerdem wird durch das Entfernen der Spalte aus der Main- `Fill` Methode die Spalte aus allen weiteren Abfragen für den TableAdapter entfernt.

 Mit dem Konfigurations-Assistenten für TableAdapter-Abfragen können Sie weitere Abfragen für den TableAdapter erstellen und bearbeiten. Diese zusätzlichen Abfragen müssen dem Tabellen Schema entsprechen, es sei denn, Sie geben einen Skalarwert zurück.  Die zusätzlichen Abfragen haben einen Namen, den Sie angeben (z `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")` . b.).

#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>So starten Sie den Konfigurations-Assistenten für TableAdapter-Abfragen mit einer neuen Abfrage

1. Öffnen Sie das Dataset im **DataSet-Designer**.

2. Wenn Sie eine neue Abfrage erstellen, ziehen Sie ein **Abfrage** Objekt von der Registerkarte **DataSet** der **Toolbox** auf ein <xref:System.Data.DataTable> , oder wählen Sie im Kontextmenü des TableAdapters die Option **Abfrage hinzufügen** aus. Sie können ein **Abfrage** Objekt auch in einen leeren Bereich der **DataSet-Designer**ziehen, wodurch ein TableAdapter ohne zugeordnete erstellt wird <xref:System.Data.DataTable> . Diese Abfragen können nur einzelne (skalare) Werte zurückgeben oder Update-, INSERT-oder DELETE-Befehle für die Datenbank ausführen.

3. Wählen oder erstellen Sie auf dem Bildschirm **Wählen Sie Ihre Datenverbindung** aus die Verbindung, die von der Abfrage verwendet wird.

    > [!NOTE]
    > Dieser Bildschirm wird nur angezeigt, wenn der Designer nicht ermitteln kann, welche Verbindung verwendet werden soll oder wenn keine Verbindungen verfügbar sind.

4. Wählen Sie auf der Seite **Wählen Sie einen Befehlstyp** aus die folgenden Methoden zum Abrufen von Daten aus der Datenbank aus:

    - Mithilfe von **SQL-Anweisungen** können Sie eine SQL-Anweisung eingeben, um die Daten aus der Datenbank auszuwählen.

    - **Erstellen einer neuen gespeicherten Prozedur** ermöglicht es Ihnen, dass der Assistent eine neue gespeicherte Prozedur (in der Datenbank) basierend auf der angegebenen SELECT-Anweisung erstellt.

    - **Vorhandene gespeicherte Prozeduren verwenden** ermöglicht das Ausführen einer vorhandenen gespeicherten Prozedur, wenn die Abfrage ausgeführt wird.

#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>So starten Sie den Konfigurations-Assistenten für TableAdapter-Abfragen für eine vorhandene Abfrage

- Wenn Sie eine vorhandene TableAdapter-Abfrage bearbeiten, klicken Sie mit der rechten Maustaste auf die Abfrage, und klicken Sie dann im Kontextmenü auf **Konfigurieren** .

    > [!NOTE]
    > Wenn Sie mit der rechten Maustaste auf die Haupt Abfrage eines TableAdapters klicken, werden TableAdapter und Schema neu konfiguriert <xref:System.Data.DataTable> . Wenn Sie mit der rechten Maustaste auf eine zusätzliche Abfrage in einem TableAdapter klicken, wird jedoch nur die ausgewählte Abfrage konfiguriert. Der **TableAdapter-Konfigurations-Assistent** konfiguriert die TableAdapter-Definition neu, während der Konfigurations-Assistent für TableAdapter-Abfragen nur die ausgewählte Abfrage neu konfiguriert.

#### <a name="to-add-a-global--query-to-a-tableadapter"></a>So fügen Sie einem TableAdapter eine globale Abfrage hinzu

- *Globale Abfragen* sind SQL-Abfragen, die entweder einen einzelnen (skalaren) Wert oder keinen Wert zurückgeben. Normalerweise führen globale Funktionen Daten Bank Vorgänge aus, z. b. Einfügungen, Updates und Löschungen Außerdem aggregieren Sie Informationen, wie z. b. die Anzahl von Kunden in einer Tabelle oder die Gesamtgebühren für alle Elemente in einer bestimmten Reihenfolge.

     Sie fügen globale Abfragen hinzu, indem Sie ein **Abfrage** Objekt von der Registerkarte **DataSet** der **Toolbox** auf einen leeren Bereich der **DataSet-Designer**ziehen.

- Stellen Sie eine Abfrage bereit, die den gewünschten Task ausführt, z `SELECT COUNT(*) AS CustomerCount FROM Customers` . b..

    > [!NOTE]
    > Wenn Sie ein **Abfrage** Objekt direkt auf den **DataSet-Designer** ziehen, wird eine Methode erstellt, die nur einen Skalarwert (Single) zurückgibt. Die von Ihnen ausgewählte Abfrage oder gespeicherte Prozedur gibt möglicherweise mehr als einen einzelnen Wert zurück, die vom Assistenten erstellte Methode gibt jedoch nur einen einzelnen Wert zurück. Beispielsweise kann die Abfrage die erste Spalte der ersten Zeile der zurückgegebenen Daten zurückgeben.

## <a name="see-also"></a>Weitere Informationen
 [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
