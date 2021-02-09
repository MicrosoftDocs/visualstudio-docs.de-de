---
title: 'Exemplarische Vorgehensweise: Erstellen einer N-Tier-Daten Anwendung'
description: Erstellen Sie in dieser exemplarischen Vorgehensweise eine N-Tier-Daten Anwendung. Bei N-Tier-Daten Anwendungen handelt es sich um apps, die auf Daten zugreifen und in Viele logische Schichten oder Ebenen aufgeteilt sind.
ms.custom: SEO-VS-2020
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ed395c60ec16eeff6a5aac88a99698193e8bacbd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866150"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>Exemplarische Vorgehensweise: Erstellen einer n-Tier-Daten Anwendung
*N-Tier*-Datenanwendungen sind Anwendungen, die auf Daten zugreifen und in mehrere logische Ebenen (oder *Tiers*) aufgeteilt sind. Die Aufteilung der Anwendungskomponenten in verschiedene Ebenen erhöht die Verwaltbarkeit und die Skalierbarkeit der Anwendung. Auf diese Weise wird das Einarbeiten neuer, eine einzelne Ebene betreffender Technologien vereinfacht, ein erneutes Entwerfen der Anwendung ist nicht notwendig. Zur N-Tier-Architektur gehören eine Präsentationsebene, eine mittlere Ebene und eine Datenebene. Die mittlere Ebene enthält eine Datenzugriffsschicht, eine Geschäftslogikschicht und gemeinsame Komponenten, wie beispielsweise Authentifizierung und Validierung. Die Datenschicht enthält eine relationale Datenbank. N-Tier-Anwendungen speichern vertrauliche Informationen in der Datenzugriffsschicht der mittleren Ebene, um diese von Endbenutzern, die auf die Präsentationsebene zugreifen, getrennt zu halten. Weitere Informationen finden Sie unter [Übersicht über N-Tier-Daten Anwendungen](../data-tools/n-tier-data-applications-overview.md).

Eine Möglichkeit zum Trennen der verschiedenen Ebenen einer N-Tier-Anwendung besteht im Erstellen separater Projekte für jede Ebene, die in der Anwendung enthalten sein soll. Typisierte DataSets enthalten eine `DataSet Project`-Eigenschaft, mit der festgelegt wird, in welche Projekte der erzeugte DataSet-Code und der erzeugte `TableAdapter`-Code eingefügt werden.

In dieser exemplarischen Vorgehensweise wird dargestellt, wie DataSet- und `TableAdapter`-Code mithilfe des **DataSet-Designers** in einzelne Klassenbibliotheksprojekte aufgeteilt werden. Nachdem Sie den DataSet-und TableAdapter-Code getrennt haben, erstellen Sie eine [Windows Communication Foundation Dienste und WCF Data Services im Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) -Dienst, um die Datenzugriffs Ebene aufzurufen. Zum Schluss erstellen Sie eine Windows Forms Anwendung als Präsentationsebene. Diese Ebene greift auf Daten des Datendiensts zu.

In dieser exemplarischen Vorgehensweise führen Sie die folgenden Schritte aus:

- Erstellen Sie eine neue n-Tier-Projekt Mappe, die mehrere Projekte enthält.

- Hinzufügen von zwei Klassenbibliotheksprojekten zur N-Tier-Projektmappe.

- Erstellen eines typisierten DataSets mithilfe des **Assistenten zum Konfigurieren von Datenquellen**.

- Trennen Sie die generierten [TableAdapters](create-and-configure-tableadapters.md) und den DataSet-Code in diskrete Projekte.

- Erstellen eines WCF (Windows Communication Foundation)-Diensts für Aufrufe an die Datenzugriffsebene.

- Erstellen von Dienstfunktionen, um Daten von der Datenzugriffsebene abzurufen.

- Erstellen einer Windows Forms-Anwendung, die als Präsentationsebene dient.

- Erstellen von Windows Forms-Steuerelementen, die an die Datenquelle gebunden werden.

- Schreiben von Code zum Füllen der Datentabellen.

![Link zum Video](../data-tools/media/playvideo.gif) eine Videoversion dieses Themas finden Sie unter [Video How to: Erstellen einer n-Tier-datenanwendung](/previous-versions/visualstudio/visual-studio-2008/cc178916(v=vs.90)).

## <a name="prerequisites"></a>Voraussetzungen
In dieser exemplarischen Vorgehensweise werden SQL Server Express localdb-und Northwind-Beispieldatenbank verwendet.

1. Wenn Sie nicht über SQL Server Express localdb verfügen, installieren Sie es entweder über die [SQL Server Express Downloadseite](https://www.microsoft.com/sql-server/sql-server-editions-express)oder über das **Visual Studio-Installer**. Im **Visual Studio-Installer** können Sie SQL Server Express localdb als Teil der **.net-desktopentwicklungs-** Arbeitsauslastung oder als einzelne Komponente installieren.

2. Installieren Sie die Beispieldatenbank Northwind, indem Sie die folgenden Schritte ausführen:

    1. Öffnen Sie in Visual Studio das Fenster **SQL Server-Objekt-Explorer** . (**SQL Server-Objekt-Explorer** wird als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** im Visual Studio-Installer installiert.) Erweitern Sie den Knoten **SQL Server** . Klicken Sie mit der rechten Maustaste auf die localdb-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren Sie das [Northwind-Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Mit diesem T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript in den Abfrage-Editor ein, und klicken Sie dann auf die Schaltfläche **Ausführen** .

       Nach kurzer Zeit wird die Ausführung der Abfrage abgeschlossen und die Datenbank Northwind erstellt.

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Erstellen der n-Tier-Projekt Mappe und der Klassenbibliothek zum Speichern des Datasets (DataEntityTier)
Im ersten Schritt dieser exemplarischen Vorgehensweise werden eine Projektmappe und zwei Klassenbibliotheksprojekte erstellt. Die erste Klassenbibliothek enthält das Dataset (die generierte typisierte `DataSet` Klasse und DataTables, die die Daten der Anwendung enthalten). Dieses Projekt wird als Datenentitätsschicht der Anwendung verwendet und befindet sich normalerweise in der mittleren Ebene. Das DataSet erstellt das anfängliche DataSet und trennt den Code automatisch in die beiden Klassenbibliotheken.

> [!NOTE]
> Stellen Sie sicher, dass Projekt und Projektmappe ordnungsgemäß benannt wurden, bevor Sie auf **OK** klicken. Das erleichtert die Durchführung der exemplarischen Vorgehensweise.

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>So erstellen Sie die N-Tier-Projektmappe und die DataEntityTier-Klassenbibliothek

1. Wählen Sie in Visual Studio im Menü **Datei** die Optionen **Neu** > **Projekt** aus.

2. Erweitern Sie entweder **Visual c#** oder **Visual Basic** im linken Bereich, und wählen Sie dann **Windows-Desktop** aus.

3. Wählen Sie im mittleren Bereich den Projekttyp **Klassenbibliothek** aus.

4. Nennen Sie das Projekt **DataEntityTier**.

5. Nennen Sie die Projekt Mappe **NTierWalkthrough**, und wählen Sie dann **OK** aus.

     Eine Projektmappe NTierWalkthrough mit dem Projekt DataEntityTier wird erstellt und zum **Projektmappen-Explorer** hinzugefügt.

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Erstellen der Klassenbibliothek für die TableAdapters (DataAccessTier)
Nach dem Erstellen des Projekts DataEntityTier besteht der nächste Schritt darin, ein zweites Klassenbibliotheksprojekt zu erstellen. Dieses Projekt enthält die generierten TableAdapters und wird als *Datenzugriffs Ebene* der Anwendung bezeichnet. Die Datenzugriffsebene enthält die zum Herstellen einer Verbindung mit der Datenbank notwendigen Informationen und befindet sich normalerweise in der mittleren Ebene.

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>So erstellen Sie eine separate Klassenbibliothek für die TableAdapters

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, und wählen Sie anschließend **Hinzufügen** > **Neues Projekt** aus.

2. Wählen Sie im Dialogfeld **Neues Projekt** im mittleren Bereich die Option **Klassenbibliothek** aus.

3. Nennen Sie das Projekt **DataAccessTier** , und wählen Sie **OK** aus.

     Das Projekt DataAccessTier wird erstellt und zur Projektmappe NTierWalkthrough hinzugefügt.

## <a name="create-the-dataset"></a>Erstellen des Datasets
Der nächste Schritt besteht darin, ein typisiertes DataSet zu erstellen. Typisierte Datasets werden sowohl mit der DataSet-Klasse (einschließlich der `DataTables` Klassen) als auch mit den `TableAdapter` Klassen in einem einzelnen Projekt erstellt. (Alle Klassen werden in einer einzelnen Datei generiert.) Wenn Sie das DataSet und TableAdapters in verschiedene Projekte aufteilen, handelt es sich um die DataSet-Klasse, die in das andere Projekt verschoben wird und die `TableAdapter` Klassen im ursprünglichen Projekt verlässt. Erstellen Sie daher das Dataset im Projekt, das letztendlich die TableAdapters (das DataAccessTier-Projekt) enthalten soll. Das DataSet wird mithilfe des Assistenten zum **Konfigurieren von Datenquellen** erstellt.

> [!NOTE]
> Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Weitere Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter Gewusst [wie: Installieren von Beispiel Datenbanken](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-dataset"></a>So erstellen Sie das Dataset

1. Wählen Sie in **Projektmappen-Explorer** den **DataAccessTier** aus.

2. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

   Das Fenster **Datenquellen** wird geöffnet.

3. Wählen Sie im **Datenquellenfenster** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

4. Wählen Sie auf der Seite **Daten Quellentyp auswählen** die Option **Datenbank** aus, und klicken Sie dann auf **weiter**.

5. Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** eine der folgenden Aktionen aus:

     Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

     - oder -

     Wählen Sie **neue Verbindung** aus, um das Dialogfeld **Verbindung hinzufügen** zu öffnen.

6. Wenn für die Datenbank ein Kennwort erforderlich ist, wählen Sie die Option zum einschließen sensibler Daten aus, und klicken Sie dann auf **weiter**.

    > [!NOTE]
    > Wenn Sie eine lokale Datenbankdatei ausgewählt haben (statt eine Verbindung mit SQL Server herzustellen), werden Sie möglicherweise gefragt, ob Sie die Datei zum Projekt hinzufügen möchten. Wählen Sie **Ja** aus, um die Datenbankdatei zum Projekt hinzuzufügen.

7. Wählen Sie auf der Seite **Verbindungs Zeichenfolge in der Anwendungs Konfigurationsdatei speichern die** Option **weiter** aus.

8. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen** .

9. Aktivieren Sie die Kontrollkästchen für die Tabellen **Customers** und **Orders** , und klicken Sie dann auf **Fertig** stellen.

     Das NorthwindDataSet wird zum DataAccessTier-Projekt hinzugefügt und im Fenster **Datenquellen** angezeigt.

## <a name="separate-the-tableadapters-from-the-dataset"></a>Trennen der TableAdapters aus dem DataSet
Nach dem Erstellen des DataSets wird die generierte DataSet-Klasse von den TableAdaptern getrennt. Hierzu müssen Sie die **DataSet-Projekt**-Eigenschaft auf den Namen des Projekts festlegen, in dem die aufgeteilten DataSet-Klassen gespeichert werden sollen.

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>So trennen Sie die TableAdapter vom DataSet

1. Doppelklicken Sie im **Projektmappen-Explorer** auf **NorthwindDataSet.xsd**, um das DataSet im **DataSet-Designer** zu öffnen.

2. Wählen Sie einen leeren Bereich im Designer aus.

3. Suchen Sie den Knoten **DataSet-Projekt** im Fenster **Eigenschaften**.

4. Wählen Sie in der Liste **DataSet-Projekt** die Option **DataEntityTier** aus.

5. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

   DataSet und TableAdapter werden in die zwei Klassenbibliotheksprojekte aufgeteilt. Das Projekt, in dem das gesamte Dataset () ursprünglich enthalten war, `DataAccessTier` enthält jetzt nur die TableAdapters. Das in der **DataSet-Projekt** Eigenschaft () angegebene Projekt `DataEntityTier` enthält das typisierte DataSet: *NorthwindDataSet. DataSet. Designer. vb* (oder *NorthwindDataSet.DataSet.Designer.cs*).

> [!NOTE]
> Bei einer Aufteilung von DataSets und TableAdapters (durch Festlegen der **DataSet-Projekt**-Eigenschaft) werden vorhandene partielle DataSet-Klassen in dem Projekt nicht automatisch verschoben. Vorhandene partielle DataSet-Klassen müssen manuell in das DataSet-Projekt verschoben werden.

## <a name="create-a-new-service-application"></a>Erstellen einer neuen Dienst Anwendung
In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie mit einem WCF-Dienst auf die Datenzugriffs Ebene zugreifen. Wir erstellen also eine neue WCF-Dienst Anwendung.

### <a name="to-create-a-new-wcf-service-application"></a>So erstellen Sie eine neue WCF-Dienstanwendung

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, und wählen Sie anschließend **Hinzufügen** > **Neues Projekt** aus.

2. Wählen Sie im Dialogfeld **Neues Projekt** im linken Bereich **WCF** aus. Wählen Sie im mittleren Bereich **WCF-Dienst Bibliothek** aus.

3. Nennen Sie das Projekt **DataService** , und wählen Sie **OK** aus.

     Das Projekt DataService wird erstellt und zur Projektmappe NTierWalkthrough hinzugefügt.

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Erstellen Sie Methoden in der Datenzugriffs Ebene, um die Kunden-und Bestelldaten zurückzugeben.
Der Datendienst muss zwei Methoden in der Datenzugriffs Ebene aufrufen: `GetCustomers` und `GetOrders` . Diese Methoden geben die Northwind `Customers` -Tabelle und die- `Orders` Tabelle zurück. Erstellen Sie die `GetCustomers` -Methode und die- `GetOrders` Methode im `DataAccessTier` Projekt.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>So erstellen Sie eine Methode in der Datenzugriffsebene, die die Tabelle Customers zurückgibt

1. Doppelklicken Sie in **Projektmappen-Explorer** auf **NorthwindDataSet. xsd** , um das DataSet zu öffnen.

2. Klicken Sie mit der rechten Maustaste auf **CustomersTableAdapter** und dann auf **Abfrage hinzufügen**.

3. Übernehmen Sie auf der Seite **Wählen Sie einen Befehlstyp aus** den Standardwert **SQL-Anweisungen verwenden**, und klicken Sie auf **Weiter**.

4. Übernehmen Sie auf der Seite **Abfragetyp auswählen** den Standardwert **SELECT-Anweisung, die Zeilen zurückgibt**, und klicken Sie auf **Weiter**.

5. Übernehmen Sie auf der Seite **SQL-SELECT-Anweisung angeben** die Standardabfrage, und klicken Sie auf **Weiter**.

6. Geben Sie auf der Seite **Zu generierende Methode auswählen** für den **Methodennamen** im Abschnitt **DataTable zurückgeben** die Zeichenfolge **GetCustomers** ein.

7. Klicken Sie auf **Fertig stellen**.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>So erstellen Sie eine Methode in der Datenzugriffsebene, die die Tabelle Orders zurückgibt

1. Klicken Sie mit der rechten Maustaste auf **OrdersTableAdapter**, und klicken Sie auf **Abfrage hinzufügen**.

2. Übernehmen Sie auf der Seite **Wählen Sie einen Befehlstyp aus** den Standardwert **SQL-Anweisungen verwenden**, und klicken Sie auf **Weiter**.

3. Übernehmen Sie auf der Seite **Abfragetyp auswählen** den Standardwert **SELECT-Anweisung, die Zeilen zurückgibt**, und klicken Sie auf **Weiter**.

4. Übernehmen Sie auf der Seite **SQL-SELECT-Anweisung angeben** die Standardabfrage, und klicken Sie auf **Weiter**.

5. Geben Sie auf der Seite **Zu generierende Methoden auswählen** für den **Methodennamen** im Abschnitt **DataTable zurückgeben** die Zeichenfolge **GetOrders** ein.

6. Klicken Sie auf **Fertig stellen**.

7. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Hinzufügen eines Verweises auf die Daten Entität und die Datenzugriffsebenen zum Datendienst
Da der Datendienst Informationen von DataSet und TableAdapters erfordert, müssen Verweise auf das Projekt **DataEntityTier** und das Projekt **DataAccessTier** hinzugefügt werden.

### <a name="to-add-references-to-the-data-service"></a>So fügen Sie Verweise zum Datendienst hinzu

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **DataService**, und klicken Sie anschließend auf **Verweis hinzufügen**.

2. Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **Projekte**.

3. Wählen Sie sowohl das Projekt **DataAccessTier** als auch das Projekt **DataEntityTier** aus.

4. Klicken Sie auf **OK**.

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Hinzufügen von Funktionen zum Dienst zum Aufrufen der Methoden GetCustomers und GetOrders in der Datenzugriffs Ebene
Nachdem die Datenzugriffsebene die Methoden zur Rückgabe der Daten enthält, müssen Sie im Datendienst Methoden erstellen, um die Methoden in der Datenzugriffsebene aufzurufen.

> [!NOTE]
> In C#-Projekten muss ein Verweis auf die `System.Data.DataSetExtensions`-Assembly für die Kompilierung des nachfolgenden Codes hinzugefügt werden.

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>So erstellen Sie im Datendienst die GetCustomers-Funktion und die GetOrders-Funktion

1. Doppelklicken Sie im Projekt **DataService** auf **IService1.vb** oder **IService1.cs**.

2. Fügen Sie unter dem Kommentar **Hier Dienstvorgänge hinzufügen** folgenden Code hinzu:

    ```vb
    <OperationContract()> _
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable

    <OperationContract()> _
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable
    ```

    ```csharp
    [OperationContract]
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();

    [OperationContract]
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();
    ```

3. Doppelklicken Sie im Projekt DataService auf **IService1.vb** (oder **IService1.cs**).

4. Fügen Sie der **Service1**-Klasse den folgenden Code hinzu:

    ```vb
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
        Return CustomersTableAdapter1.GetCustomers()
    End Function

    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
        Return OrdersTableAdapter1.GetOrders()
    End Function
    ```

    ```csharp
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
             CustomersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();
        return CustomersTableAdapter1.GetCustomers();
    }
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
             OrdersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();
        return OrdersTableAdapter1.GetOrders();
    }
    ```

5. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>Erstellen einer Präsentationsebene zum Anzeigen von Daten aus dem Datendienst
Nun, da die Lösung den Datendienst enthält, der über Methoden verfügt, die die Datenzugriffs Ebene aufrufen, erstellen Sie ein weiteres Projekt, das den Datendienst aufruft und den Benutzern die Daten präsentiert. Erstellen Sie für diese exemplarische Vorgehensweise eine Windows Forms-Anwendung als Präsentationsebene der N-Tier-Anwendung.

### <a name="to-create-the-presentation-tier-project"></a>So erstellen Sie das Präsentationsebenenprojekt

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, und wählen Sie anschließend **Hinzufügen** > **Neues Projekt** aus.

2. Wählen Sie im Dialogfeld **Neues Projekt** im linken Fensterbereich **Windows-Desktop** aus. Wählen Sie im mittleren Bereich **Windows Forms App** aus.

3. Nennen Sie das Projekt **PresentationTier**, und klicken Sie auf **OK**.

    Das Projekt PresentationTier wird erstellt und zur Projektmappe NTierWalkthrough hinzugefügt.

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>Festlegen des PresentationTier-Projekts als Startprojekt
Wir legen das Projekt **PresentationTier** als Startprojekt für die Lösung fest, da es sich um die tatsächliche Client Anwendung handelt, die die Daten darstellt und mit Ihnen interagiert.

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>So legen Sie das neue Präsentationsebenenprojekt als Startprojekt fest

- Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **PresentationTier**, und klicken Sie anschließend auf **Als Startprojekt festlegen**.

## <a name="add-references-to-the-presentation-tier"></a>Verweise auf die Präsentationsebene hinzufügen
Die PresentationTier der Clientanwendung erfordert einen Dienstverweis auf den Datendienst, um auf die Methoden des Diensts zugreifen zu können. Außerdem ist ein Verweis auf das DataSet erforderlich, um die Typfreigabe des WCF-Diensts zu aktivieren. Bis Sie die Typfreigabe über den Datendienst aktivieren, ist der der partiellen DataSet-Klasse hinzugefügte Code für die Präsentationsebene nicht verfügbar. Da Sie in der Regel Code, z. b. Validierungscode, zu den Zeilen-und Spalten Änderungs Ereignissen einer Datentabelle hinzufügen, ist es wahrscheinlich, dass Sie vom Client aus auf diesen Code zugreifen möchten.

### <a name="to-add-a-reference-to-the-presentation-tier"></a>So fügen Sie einen Verweis auf die Präsentationsebene hinzu

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **PresentationTier** , und wählen Sie **Verweis hinzufügen**.

2. Wählen Sie im Dialogfeld **Verweis hinzufügen** die Registerkarte **Projekte** aus.

3. Wählen Sie **DataEntityTier** aus, und klicken Sie auf **OK**.

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>So fügen Sie einen Dienstverweis auf die Präsentationsebene hinzu

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **PresentationTier** , und wählen Sie **Dienstverweis hinzufügen** aus.

2. Klicken Sie im Dialogfeld **Dienstverweis hinzufügen** auf **ermitteln**.

3. Wählen Sie **Service1** , und klicken Sie auf **OK**.

    > [!NOTE]
    > Wenn Sie über mehrere Dienste auf dem aktuellen Computer verfügen, wählen Sie den Dienst aus, den Sie zuvor in dieser exemplarischen Vorgehensweise erstellt haben (der Dienst, der die `GetCustomers` -und- `GetOrders` Methoden enthält).

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Fügen Sie DataGridViews zum Formular hinzu, um die vom Datendienst zurückgegebenen Daten anzuzeigen.
Nachdem der Dienstverweis zum Datendienst hinzugefügt wurde, werden die vom Dienst zurückgegebenen Daten automatisch zum Fenster **Datenquellen** hinzugefügt.

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>So fügen Sie zwei datengebundene DataGridViews zum Formular hinzu

1. Wählen Sie im **Projektmappen-Explorer** das Projekt **PresentationTier** aus.

2. Erweitern Sie im Fenster **Datenquellen** das **NorthwindDataSet**, und suchen Sie den Knoten **Customers**.

3. Ziehen Sie den Knoten **Customers** auf Form1.

4. Erweitern Sie im Fenster **Datenquellen** den Knoten **Customers**, und suchen Sie den zugehörigen Knoten **Orders** (den im Knoten **Customers** geschachtelten Knoten **Orders**).

5. Ziehen Sie den zugehörigen Knoten **Orders** auf Form1.

6. Erstellen Sie einen `Form1_Load`-Ereignishandler, indem Sie auf einen leeren Bereich des Formulars doppelklicken.

7. Fügen Sie dem `Form1_Load`-Ereignishandler den folgenden Code hinzu.

    ```vb
    Dim DataSvc As New ServiceReference1.Service1Client
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)
    ```

    ```csharp
    ServiceReference1.Service1Client DataSvc =
        new ServiceReference1.Service1Client();
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());
    ```

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>Erhöhen Sie die maximale Nachrichtengröße, die vom Dienst zugelassen wird.
Der Standardwert für `maxReceivedMessageSize` ist nicht groß genug zum Speichern der Daten, die aus den `Customers` Tabellen und abgerufen werden `Orders` . In den folgenden Schritten erhöhen Sie den Wert auf 6553600. Sie ändern den Wert auf dem Client, wodurch der Dienst Verweis automatisch aktualisiert wird.

> [!NOTE]
> Die niedrigere Standardgröße dient dazu, die Anfälligkeit für Denial-of-Service (DoS)-Angriffe zu verringern. Weitere Informationen finden Sie unter <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>So erhöhen Sie den maxReceivedMessageSize-Wert

1. Doppelklicken Sie im **Projektmappen-Explorer** im Projekt **PresentationTier** auf die Datei **app.config**.

2. Suchen Sie das **maxReceivedMessage**-Größenattribut, und ändern Sie den Wert in `6553600`.

## <a name="test-the-application"></a>Testen der Anwendung
Drücken Sie **F5**, um die Anwendung auszuführen. Die Daten aus der `Customers` -Tabelle und der- `Orders` Tabelle werden vom Datendienst abgerufen und im Formular angezeigt.

## <a name="next-steps"></a>Nächste Schritte
Abhängig von den Anforderungen Ihrer Anwendung können nach dem Speichern der verknüpften Daten in der Windows-Anwendung weitere Schritte sinnvoll sein. Beispielsweise können Sie der Anwendung folgende Erweiterungen hinzufügen:

- Hinzufügen der Validierung zum DataSet.

- Hinzufügen von zusätzlichen Methoden zum Dienst für das Aktualisieren der Daten in der Datenbank.

## <a name="see-also"></a>Weitere Informationen

- [Arbeiten mit Datasets in N-Tier-Anwendungen](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)
- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
