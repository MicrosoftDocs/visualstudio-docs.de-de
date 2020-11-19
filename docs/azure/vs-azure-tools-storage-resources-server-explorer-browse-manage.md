---
title: Durchsuchen und Verwalten von Speicherressourcen
description: Durchsuchen und Verwalten von Speicherressourcen mit dem Server-Explorer
ms.custom: SEO-VS-2020
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: ae45fafb562387720b652e0921624bc859ea5920
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902219"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Durchsuchen und Verwalten von Speicherressourcen mit dem Server-Explorer

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Übersicht

Wenn Sie die Azure-Tools für Microsoft Visual Studio installiert haben, können Sie Blob-, Warteschlangen- und Tabellendaten von Ihren Speicherkonten für Azure aus anzeigen. Der Knoten Azure **Storage** in Server-Explorer zeigt Daten an, die sich in Ihrem lokalen speicheremulatorkonto und ihren anderen Azure-Speicher Konten befinden.

Um Server-Explorer in Visual Studio anzuzeigen, wählen Sie in der Menüleiste **View** die Option  >  **Server-Explorer** anzeigen aus. Der Knoten **Storage** zeigt alle Speicherkonten an, die unter jedem Azure-Abonnement oder -Zertifikat vorhanden sind, mit dem Sie verbunden sind. Wird das Speicherkonto nicht angezeigt, befolgen Sie die Anweisungen am [Ende des Artikels](#add-storage-accounts-by-using-server-explorer), um das Konto hinzuzufügen.

Ab dem Azure SDK 2.7 können Sie auch den Cloud-Explorer zum Anzeigen und Verwalten von Azure-Ressourcen verwenden. Weitere Informationen finden Sie unter [Verwalten von Azure-Ressourcen mit Cloud-Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Anzeigen und Verwalten von Speicherressourcen in Visual Studio

Der Server-Explorer zeigt automatisch eine Liste von Blobs, Warteschlangen und Tabellen in Ihrem Speicheremulatorkonto an. Das speicheremulatorkonto wird in Server-Explorer unter dem Knoten " **Speicher** " als **Entwicklungs** Knoten aufgeführt.

Erweitern Sie zum Anzeigen der Ressourcen des Speicheremulatorkontos den Knoten **Entwicklung** . Wenn der Speicheremulator nicht gestartet wurde, wird er automatisch gestartet, wenn Sie den Knoten **Entwicklung** erweitern. Dieser Prozess kann mehrere Sekunden dauern. Sie können weiterhin in anderen Bereichen von Visual Studio arbeiten, während der Speicheremulator gestartet wird.

Erweitern Sie zum Anzeigen von Ressourcen in einem Speicherkonto den Knoten des Speicherkontos im Server-Explorer. Dort werden die Knoten **Blobs**, **Warteschlagen** und **Tabellen** angezeigt.

## <a name="work-with-blob-resources"></a>Arbeiten mit Blobressourcen

Der Knoten **Blobs** zeigt eine Liste der Container für das ausgewählte Speicherkonto an. Blobcontainer enthalten Blobdateien, und Sie können diese Blobs in Ordnern und Unterordnern organisieren. Weitere Informationen finden Sie unter [Verwenden von Blob-Speicher aus .NET](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>So erstellen Sie einen Blobcontainer

1. Öffnen Sie das Kontextmenü für den Knoten **Blobs**, und wählen Sie dann **Blobcontainer erstellen**.
1. Geben Sie im Dialogfeld **Blobcontainer erstellen** den Namen des neuen Containers ein.
1. Drücken Sie die EINGABETASTE auf der Tastatur, oder klicken bzw. tippen Sie außerhalb des Namensfelds, um den Blobcontainer zu speichern.

   > [!NOTE]
   > Der Blobcontainername muss mit einer Zahl (0-9) oder einem Kleinbuchstaben (a-z) beginnen.

### <a name="to-delete-a-blob-container"></a>So löschen Sie einen Blobcontainer

Öffnen Sie das Kontextmenü für den Blobcontainer, den Sie entfernen möchten, und wählen Sie **Löschen**.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>So zeigen Sie eine Liste der Elemente in einem Blobcontainer an

Öffnen Sie das Kontextmenü für einen Blobcontainernamen in der Liste, und wählen Sie dann **Öffnen**.

Wenn Sie den Inhalt eines Blobcontainers anzeigen, wird er auf einer Registerkarte angezeigt, die als Blobcontaineransicht bezeichnet wird.

![Blobcontaineransicht](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Sie können die folgenden Vorgänge für Blobs mithilfe der Schaltflächen in der rechten oberen Ecke der Blobcontaineransicht ausführen:

* Eingeben und Anwenden eines Filterwerts
* Aktualisieren der Liste der Blobs im Container
* Laden Sie eine Datei hoch.
* Löschen eines Blobs (Beim Löschen einer Datei aus einem Blobcontainer wird nicht die zugrunde liegende Datei gelöscht. Sie wird lediglich aus dem Blobcontainer entfernt.)
* Öffnen eines Blobs
* Speichern eines Blobs auf dem lokalen Computer

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>So erstellen Sie einen Ordner oder Unterordner in einem Blobcontainer

1. Wählen Sie in **Cloud-Explorer** den BlobContainer aus. Wählen Sie im Containerfenster die Schaltfläche **Blob hochladen** aus.

1. Wählen Sie im Dialogfeld **Neue Datei hochladen** die Schaltfläche **Durchsuchen**, um die Datei anzugeben, die Sie hochladen möchten. Geben Sie dann einen Ordnernamen im Feld **Ordner (optional)** ein.

   ![Hochladen einer Datei in einen Blobordner](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Sie können den Containerordnern Unterordner hinzufügen, indem Sie den Schritt wie beschrieben erneut durchführen. Wenn Sie keinen Ordnernamen angeben, wird die Datei auf der obersten Ebene des Blobcontainers hochgeladen. Die Datei wird im angegebenen Ordner im Container angezeigt.

   ![Ordner, der einem Blobcontainer hinzugefügt wurde](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Doppelklicken Sie auf den Ordner, oder drücken Sie die EINGABETASTE, um den Inhalt des Ordners anzuzeigen. Wenn Sie sich im Ordner des Containers befinden, können Sie in das Stammverzeichnis des Containers zurückkehren, indem Sie die Schaltfläche **Übergeordnetes Verzeichnis öffnen** (Pfeilschaltfläche) wählen.

### <a name="to-delete-a-container-folder"></a>So löschen Sie einen Containerordner

Löschen Sie alle Dateien im Ordner.

Da es sich bei Ordnern in Blobcontainern um virtuelle Ordner handelt, ist es nicht möglich, einen leeren Ordner zu erstellen. Zudem können Sie einen Ordner nicht zum Löschen der jeweiligen Dateiinhalte löschen. Stattdessen müssen Sie den gesamten Inhalt eines Ordners löschen, um den Ordner selbst zu löschen.

### <a name="to-filter-blobs-in-a-container"></a>So filtern Sie Blobs in einem Container

Sie können die angezeigten Blobs filtern, indem Sie ein gemeinsames Präfix angeben.

Wenn Sie beispielsweise das Präfix **hello** in das Filtertextfeld eingeben und dann die Schaltfläche **Ausführen** (**!**) wählen, werden nur Blobs angezeigt, die mit „hello“ beginnen.

![Filtertextfeld](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

Beim Filtertextfeld muss die Groß-/Kleinschreibung beachtet werden. Filtervorgänge mit Platzhalterzeichen werden nicht unterstützt. Blobs können nur nach Präfix gefiltert werden. Das Präfix kann ein Trennzeichen einschließen, wenn Sie Blobs in einer virtuellen Hierarchie mithilfe eines Trennzeichens organisieren. Zum Beispiel werden durch Filtern nach dem Präfix „HelloFabric/“ alle Blobs zurückgegeben, die mit dieser Zeichenfolge beginnen.

### <a name="to-download-blob-data"></a>So laden Sie Blobdaten herunter

Verwenden Sie in **Cloud-Explorer** eine der folgenden Methoden:

* Öffnen Sie das Kontextmenü für ein oder mehrere Blobs, und wählen Sie dann **Öffnen**.
* Wählen Sie den Blobnamen und anschließend die Schaltfläche **Öffnen** aus.
* Doppelklicken Sie auf den Blobnamen.

Der Status eines Blob-Downloads wird im Fenster **Azure-Aktivitätsprotokoll** angezeigt.

Das Blob wird im Standard-Editor für diesen Dateityp geöffnet. Wenn das Betriebssystem den Dateityp erkennt, wird die Datei in einer lokal installierten Anwendung geöffnet. Andernfalls werden Sie aufgefordert, eine für den Dateityp des Blobs geeignete Anwendung auszuwählen. Die beim Herunterladen von Blobs erstellte lokale Datei ist als schreibgeschützt gekennzeichnet.

Blobdaten werden lokal zwischengespeichert und im Azure Blob Storage mit dem Zeitpunkt der letzten Änderung des Blobs verglichen. Wenn das Blob aktualisiert wurde, seit es zum letzten Mal heruntergeladen wurde, wird es erneut heruntergeladen. Andernfalls wird das Blob vom lokalen Datenträger geladen.

Standardmäßig wird ein Blob in ein temporäres Verzeichnis heruntergeladen. Um Blobs in ein bestimmtes Verzeichnis herunterzuladen, öffnen Sie das Kontextmenü für die ausgewählten Blobnamen, und wählen Sie **Speichern unter**. Wenn Sie ein Blob auf diese Weise speichern, wird die Blobdatei nicht geöffnet, und die lokale Datei wird mit Lese-/Schreibattributen erstellt.

### <a name="to-upload-blobs"></a>So laden Sie Blobs hoch

Klicken Sie zum Hochladen von Blobs auf die Schaltfläche **Blob hochladen**, wenn der Container für die Anzeige in der Blobcontaineransicht geöffnet ist.

Sie können eine oder mehrere Dateien eines beliebigen Typs zum Hochladen auswählen. Im Fenster **Azure-Aktivitätsprotokoll** wird der Uploadstatus angezeigt. Weitere Informationen zum Arbeiten mit Blobdaten finden Sie unter [Erste Schritte mit Azure Blob Storage mit .NET](/azure/storage/blobs/storage-quickstart-blobs-dotnet).

### <a name="to-view-logs-transferred-to-blobs"></a>So zeigen Sie an Blobs übertragene Protokolle an

Wenn Sie mithilfe der Azure-Diagnose Daten von der Azure-Anwendung protokollieren und Protokolle an das Speicherkonto übertragen haben, werden Container angezeigt, die von Azure für diese Protokolle erstellt wurden. Das Anzeigen dieser Protokolle im Server-Explorer ist eine einfache Möglichkeit, um Probleme mit Ihrer Anwendung zu erkennen, insbesondere wenn sie für Azure bereitgestellt wurde.

Weitere Informationen zu Azure-Diagnose finden Sie unter [Sammeln von Protokollierungsdaten mit der Azure-Diagnose](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="to-get-the-url-for-a-blob"></a>So rufen Sie die URL für ein Blob ab

Öffnen Sie das Kontextmenü des Blobs, und wählen Sie dann **URL kopieren** aus.

### <a name="to-edit-a-blob"></a>So bearbeiten Sie ein Blob

Wählen Sie das BLOB aus, und wählen Sie dann die Schaltfläche **BLOB öffnen** aus.

Die Datei wird an einen temporären Speicherort heruntergeladen und auf dem lokalen Computer geöffnet. Laden Sie das Blob nach dem Ändern erneut hoch.

## <a name="work-with-queue-resources"></a>Arbeiten mit Warteschlangenressourcen

Speicherdienstwarteschlangen werden in einem Azure-Speicherkonto gehostet. Dieses ermöglicht die Kommunikation der Clouddienstrollen untereinander und mit anderen Diensten über einen Nachrichtenübergabemechanismus. Greifen Sie auf die Warteschlange programmgesteuert über einen Clouddienst und einen Webdienst für externe Clients zu. Oder greifen Sie mit dem Server-Explorer in Visual Studio direkt auf die Warteschlange zu.

Wenn Sie einen Clouddienst entwickeln, in dem Warteschlangen verwendet werden, können Sie Warteschlangen mit Visual Studio erstellen und interaktiv mit ihnen arbeiten, während Sie Ihren Code entwickeln und testen.

Im Server-Explorer können Sie die Warteschlangen in einem Speicherkonto anzeigen, Warteschlangen erstellen und löschen, eine Warteschlange zum Anzeigen von Nachrichten öffnen und einer Warteschlange Nachrichten hinzufügen. Ist eine Warteschlange zum Anzeigen geöffnet, können Sie die einzelnen Nachrichten anzeigen. Mit den Schaltflächen in der linken oberen Ecke können Sie die folgenden Aktionen für die Warteschlange ausführen:

* Aktualisieren der Ansicht der Warteschlange
* Fügen Sie eine Meldung in die Warteschlange hinzu.
* Entfernen der obersten Nachricht aus der Warteschlange
* Löschen der gesamten Warteschlange

Die folgende Abbildung zeigt eine Warteschlange, die zwei Nachrichten enthält:

![Anzeigen einer Warteschlange](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Weitere Informationen zu Speicherdienstwarteschlangen finden Sie unter [Erste Schritte mit Azure Queue Storage mit .NET](/azure/storage/queues/storage-dotnet-how-to-use-queues). Weitere Informationen zum Webdienst für Speicherdienstwarteschlangen finden Sie unter [Konzepte des Warteschlangendiensts](/rest/api/storageservices/Queue-Service-Concepts). Informationen dazu, wie Nachrichten mithilfe von Visual Studio an eine Speicherdienstwarteschlange gesendet werden, finden Sie unter [Senden von Nachrichten an eine Speicherdienstwarteschlange](/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Speicherdienstwarteschlangen unterscheiden sich von Azure Service Bus-Warteschlangen. Weitere Informationen zu Service Bus Warteschlangen finden Sie unter [Service Bus Warteschlangen, Themen und Abonnements](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Arbeiten mit Tabellenressourcen

Mit Azure Table Storage können Sie große Mengen strukturierter Daten speichern. Der Dienst ist ein NoSQL-Datenspeicher, der authentifizierte Aufrufe von innerhalb und außerhalb der Azure-Cloud akzeptiert. Azure-Tabellen sind hervorragend zur Speicherung strukturierter nicht relationaler Daten geeignet.

### <a name="to-create-a-table"></a>So erstellen Sie eine Tabelle

1. Wählen Sie in **Cloud-Explorer** den Knoten **Tabellen** des Speicher Kontos aus, und klicken Sie dann auf **Tabelle erstellen**.
1. Geben Sie im Dialogfeld **Tabelle erstellen** einen Namen für die Tabelle ein.

### <a name="to-view-table-data"></a>So zeigen Sie Tabellendaten an

1. Öffnen Sie in **Cloud-Explorer** den Knoten **Azure** , und öffnen Sie dann den Knoten **Speicher** .
1. Öffnen Sie den für Sie relevanten Speicherkontoknoten, und öffnen Sie dann den Knoten **Tabellen** , um eine Liste der Tabellen für das Speicherkonto anzuzeigen.
1. Öffnen Sie das Kontextmenü für eine Tabelle, und wählen Sie dann **Tabelle anzeigen**.

    ![Eine Azure-Tabelle im Projektmappen-Explorer](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

Die Tabelle ist in Entitäten (Anzeige in Zeilen) und Eigenschaften (Anzeige in Spalten) organisiert. Die folgende Abbildung zeigt beispielsweise Entitäten, die im Tabellen-Designer aufgeführt sind.

### <a name="to-edit-table-data"></a>So bearbeiten Sie Tabellendaten

Öffnen Sie in **Tabellen-Designer** das Kontextmenü für eine Entität (eine einzelne Zeile) oder eine Eigenschaft (eine einzelne Zelle), und wählen Sie dann **Bearbeiten** aus.

![Hinzufügen oder Bearbeiten einer Tabellenentität](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Entitäten in einer einzelnen Tabelle müssen nicht denselben Eigenschaftensatz (Spalten) aufweisen. Beachten Sie beim Anzeigen und Bearbeiten von Tabellendaten folgende Einschränkungen:

* Binäre Daten (`type byte[]`) können zwar nicht angezeigt oder bearbeitet, sie können aber in einer Tabelle gespeichert werden.
* Die **PartitionKey** -oder **RowKey** -Werte können nicht bearbeitet werden, da der Azure-Tabellen Speicher diesen Vorgang nicht unterstützt.
* Sie können keine Eigenschaft mit dem Namen **Timestamp** erstellen. Azure-Speicherdienste verwenden eine Eigenschaft mit diesem Namen.
* Wenn Sie einen **DateTime** -Wert eingeben, müssen Sie einem Format folgen, das den Regions-und Spracheinstellungen des Computers entspricht (z. b. mm/dd/yyyy HH: mm: SS [am | PM] für Englisch (USA)).

### <a name="to-add-entities"></a>So fügen Sie Entitäten hinzu

1. Wählen Sie in **Tabellen-Designer** die Schaltfläche **Entität hinzufügen** aus.

    ![Schaltfläche „Entität hinzufügen“](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. Geben Sie im Dialogfeld **Entität hinzufügen** die Werte der **PartitionKey**- und **RowKey**-Eigenschaften ein.

    ![Dialogfeld „Entität hinzufügen“](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Gehen Sie bei der Eingabe der Werte mit Bedacht vor. Nach dem Schließen des Dialogfelds können sie nicht mehr geändert werden. Zum Ändern muss die Entität gelöscht und erneut hinzugefügt werden.

### <a name="to-filter-entities"></a>So filtern Sie Entitäten

Mit dem Abfrage-Generator können Sie den Satz von Entitäten anpassen, der in einer Tabelle angezeigt wird.

1. Öffnen Sie zum Öffnen des Abfrage-Generators eine Tabelle für die Anzeige.
1. Wählen Sie in der Symbolleiste der Tabellenansicht die Schaltfläche **Abfrage-Generator** aus.

    Das Dialogfeld **Abfrage-Generator** wird angezeigt. Im Folgenden ist eine mit dem Abfrage-Generator erstellte Abfrage abgebildet.

    ![Abfrage-Generator](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Schließen Sie das Dialogfeld, wenn Sie die Abfrage erstellt haben. Die resultierende Textform der Abfrage wird in einem Textfeld als WCF Data Services-Filter angezeigt.
1. Klicken Sie auf das grüne Dreieckssymbol, um die Abfrage auszuführen.

Sie können im Tabellen-Designer angezeigte Entitätsdaten filtern, indem Sie im Filtertextfeld direkt eine WCF Data Services-Filterzeichenfolge eingeben. Diese Art von Zeichenfolge ist mit einer SQL-WHERE-Klausel vergleichbar, wird jedoch als HTTP-Anforderung an den Server gesendet. Weitere Informationen zum Erstellen von Filter Zeichenfolgen finden Sie unter [Erstellen von Filter Zeichenfolgen für den Tabellen-Designer](vs-azure-tools-table-designer-construct-filter-strings.md).

Die folgende Abbildung zeigt ein Beispiel für eine gültige Filterzeichenfolge:

![Filterzeichenfolge](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Aktualisieren von Speicherdaten

Wenn der Server-Explorer eine Verbindung mit einem Speicherkonto herstellt oder Daten daraus abruft, kann es bis zu einer Minute dauern, bis der Vorgang abgeschlossen ist. Wenn Server-Explorer keine Verbindung herstellen kann, tritt möglicherweise ein Timeout des Vorgangs auf. Während Daten abgerufen werden, können Sie weiterhin in anderen Bereichen von Visual Studio arbeiten. Wenn der Vorgang zu lange dauert, klicken Sie zum Abbrechen in der Symbolleiste des Server-Explorers auf die Schaltfläche **Aktualisieren beenden**.

### <a name="to-refresh-blob-container-data"></a>So aktualisieren Sie Blobcontainerdaten

* Wählen Sie unter **Storage** den Knoten **Blobs** und dann auf der Symbolleiste des Server-Explorers die Schaltfläche **Aktualisieren**.
* Um die angezeigte Liste der Blobs zu aktualisieren, wählen Sie die Schaltfläche **Ausführen**.

### <a name="to-refresh-table-data"></a>So aktualisieren Sie Tabellendaten

* Wählen Sie unter **Storage** den Knoten **Tabellen** und dann auf der Symbolleiste des Server-Explorers die Schaltfläche **Aktualisieren**.
* Um die Liste der Entitäten zu aktualisieren, die in **Tabellen-Designer** angezeigt wird, wählen Sie die Schaltfläche **Ausführen** in Tabellen-Designer aus.

### <a name="to-refresh-queue-data"></a>So aktualisieren Sie Warteschlangendaten

Wählen Sie unter **Storage** den Knoten **Warteschlangen** und dann auf der Symbolleiste des Server-Explorers die Schaltfläche **Aktualisieren**.

### <a name="to-refresh-all-items-in-a-storage-account"></a>So aktualisieren Sie alle Elemente in einem Speicherkonto

Wählen Sie den Kontonamen und dann die Schaltfläche **Aktualisieren** in der Symbolleiste des Server-Explorers aus.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Hinzufügen von Speicherkonten mithilfe des Server-Explorers

Es gibt zwei Möglichkeiten, Speicherkonten mithilfe des Server-Explorers hinzuzufügen. Sie können in Ihrem Azure-Abonnement ein Speicherkonto erstellen, oder Sie können ein vorhandenes Speicherkonto anfügen.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>So erstellen Sie ein Speicherkonto mit dem Server-Explorer

1. Öffnen Sie im Server-Explorer das Kontextmenü für den Knoten **Speicher**, und wählen Sie dann **Speicherkonto erstellen**.

1. Wählen Sie im Dialogfeld **Speicherkonto erstellen** die folgenden Informationen aus, oder geben Sie sie ein:

   * Das Azure-Abonnement, dem Sie das Speicherkonto hinzufügen möchten
   * Den Namen, den Sie für das neue Speicherkonto verwenden möchten
   * Die Region oder Affinitätsgruppe (z. B. USA, Westen oder Ostasien)
   * Den Typ der Replikation, den Sie für das Speicherkonto verwenden möchten, zum Beispiel „Lokal redundant“

   ![Erstellen eines Azure-Speicherkontos](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. Klicken Sie auf **Erstellen**.

Das neue Speicherkonto wird im Projektmappen-Explorer in der Liste **Speicher** angezeigt.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>So fügen Sie ein vorhandenes Speicherkonto mithilfe des Server-Explorers an

1. Öffnen Sie im Server-Explorer das Kontextmenü für den Azure **Storage**-Knoten, und wählen Sie dann **Externen Speicher anfügen** aus.

    ![Hinzufügen eines vorhandenen Speicherkontos](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. Wählen Sie im Dialogfeld **Speicherkonto erstellen** die folgenden Informationen aus, oder geben Sie sie ein:

   * Den Namen des vorhandenen Speicherkontos, das Sie anfügen möchten.
   * Den Schlüssel für das ausgewählte Speicherkonto. Dieser Wert wird für gewöhnlich bereitgestellt, wenn Sie ein Speicherkonto auswählen. Wenn Visual Studio sich den Speicherkontoschlüssel merken soll, aktivieren Sie das Kontrollkästchen **Kontoschlüssel merken**.
   * Das Protokoll, das zum Herstellen einer Verbindung mit dem Speicherkonto verwendet wird, beispielsweise HTTP, HTTPS oder ein benutzerdefinierter Endpunkt. Weitere Informationen über benutzerdefinierte Endpunkte finden Sie unter [Konfigurieren von Verbindungszeichenfolgen](/azure/storage/common/storage-configure-connection-string).

### <a name="to-view-the-secondary-endpoints"></a>So zeigen Sie die sekundären Endpunkte an

Wenn Sie ein Speicherkonto mithilfe der Replikationsoption **Lesezugriff geografisch redundant** erstellt haben, können Sie dessen sekundäre Endpunkte anzeigen. Öffnen Sie dazu das Kontextmenü für den Kontonamen, und klicken Sie dann auf **Eigenschaften**.

![Sekundäre Speicherendpunkte](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>So entfernen Sie ein Speicherkonto aus dem Server-Explorer

Öffnen Sie im Server-Explorer das Kontextmenü für den Kontonamen, und wählen Sie **Löschen**.

Wenn Sie ein Speicherkonto löschen, werden auch alle gespeicherten Schlüsselinformationen für dieses Konto entfernt.

Das Löschen eines Speicherkontos aus dem Server-Explorer hat keine Auswirkungen auf das Speicherkonto oder die darin enthaltenen Daten. Es wird lediglich der Verweis aus dem Server-Explorer entfernt. Verwenden Sie das [Azure-Portal](https://portal.azure.com/), um ein Speicherkonto dauerhaft zu löschen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen dazu, wie Microsoft Azure Storage-Dienste verwendet werden, finden Sie unter [Zugreifen auf Microsoft Azure Storage-Dienste](/azure/storage/common/storage-introduction).
