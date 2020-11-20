---
title: Erstellen eines WCF Data Service mit WPF-& Entity Framework
description: Erstellen Sie einen WCF Data Service mit WPF und Entity Framework, der in einer ASP.NET-Webanwendung gehostet wird, und greifen Sie dann über eine Windows Forms Anwendung darauf zu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c8c9ced0b589b28f1cd21de4a862c6f11dc6e03e
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998264"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Exemplarische Vorgehensweise: Erstellen von und Zugreifen auf einen WCF-Datendienst mit WPF und Entity Framework
In dieser exemplarischen Vorgehensweise wird dargestellt, wie ein einfacher [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] erstellt wird, der in einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung gehostet wird, und wie dann von einer Windows Forms-Anwendung aus darauf zugegriffen wird.

In dieser exemplarischen Vorgehensweise haben Sie Folgendes:

- Eine Webanwendung erstellen, um einen [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] zu hosten.

- Erstellen Sie eine [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] , die die `Customers` Tabelle in der Northwind-Datenbank darstellt.

- Erstellen Sie eine [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Eine Clientanwendung erstellen und dieser einen Verweis auf den [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] hinzufügen.

- Die Datenbindung zum Dienst aktivieren und die Benutzeroberfläche erstellen.

- Optional Filterfunktionen zur Anwendung hinzufügen.

## <a name="prerequisites"></a>Voraussetzungen
In dieser exemplarischen Vorgehensweise werden SQL Server Express localdb-und Northwind-Beispieldatenbank verwendet.

1. Wenn Sie nicht über SQL Server Express localdb verfügen, installieren Sie es entweder über die [SQL Server Express Downloadseite](https://www.microsoft.com/sql-server/sql-server-editions-express)oder über das **Visual Studio-Installer**. Im **Visual Studio-Installer** können Sie SQL Server Express localdb als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** oder als einzelne Komponente installieren.

2. Installieren Sie die Beispieldatenbank Northwind, indem Sie die folgenden Schritte ausführen:

    1. Öffnen Sie in Visual Studio das Fenster **SQL Server-Objekt-Explorer** . (**SQL Server-Objekt-Explorer** wird als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** im Visual Studio-Installer installiert.) Erweitern Sie den Knoten **SQL Server** . Klicken Sie mit der rechten Maustaste auf die localdb-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren Sie das [Northwind-Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Mit diesem T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript in den Abfrage-Editor ein, und klicken Sie dann auf die Schaltfläche **Ausführen** .

       Nach kurzer Zeit wird die Ausführung der Abfrage abgeschlossen und die Datenbank Northwind erstellt.

## <a name="creating-the-service"></a>Erstellen des Diensts
Um einen [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] zu erstellen, fügen Sie ein Webprojekt hinzu. Dann erstellen Sie ein [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] und anschließend den Dienst aus dem Modell.

Im ersten Schritt fügen Sie ein Webprojekt zum Hosten des Diensts hinzu.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-the-web-project"></a>So erstellen Sie das Webprojekt

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

2. Erweitern Sie im Dialogfeld **Neues Projekt** die Knoten **Visual Basic** oder **Visual C#** sowie **Web**, und wählen Sie dann die Vorlage **ASP.NET-Webanwendung** aus.

3. Geben Sie **NorthwindWeb** im Textfeld **Name** ein, und wählen Sie dann die Schaltfläche **OK**.

4. Wählen Sie im Dialogfeld **Neues ASP.NET-Projekt** aus der Liste **Vorlage auswählen** die Option **Leer**, und klicken Sie dann auf die Schaltfläche **OK**.

Im nächsten Schritt erstellen Sie einen [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] , der die `Customers` Tabelle in der Northwind-Datenbank darstellt.

### <a name="to-create-the-entity-data-model"></a>So erstellen Sie das Entity Data Model

1. Wählen Sie in der Menüleiste **Projekt**  >  **Neues Element hinzufügen** aus.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** den Knoten **Daten** und anschließend das Element **ADO.NET Entity Data Model** aus.

3. Geben Sie im Textfeld **Name** ein `NorthwindModel` , und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     Der Assistent für Entity Data Model wird angezeigt.

4. Wählen Sie im Entity Data Model-Assistenten auf der Seite **Modellinhalte auswählen** das Element **EF-Designer aus Datenbank** aus, und klicken Sie dann auf **Weiter**.

5. Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** einen der folgenden Schritte aus:

    - Wenn eine Datenverbindung mit der Beispieldatenbank Northwind in der Dropdownliste verfügbar ist, wählen Sie sie aus.

         - oder -

    - Wählen Sie die Schaltfläche **Neue Verbindung**, um eine neue Datenverbindung zu konfigurieren. Weitere Informationen finden Sie unter [Hinzufügen neuer Verbindungen](../data-tools/add-new-connections.md).

6. Wenn für die Datenbank ein Kennwort erforderlich ist, klicken Sie auf das Optionsfeld **Ja, vertrauliche Daten in die Verbindungszeichenfolge einschließen** und dann auf die Schaltfläche **Weiter**.

    > [!NOTE]
    > Wenn ein Dialogfeld angezeigt wird, klicken Sie auf **Ja**, um die Datei im Projekt zu speichern.

7. Wählen Sie auf der Seite **Wählen Sie Ihre Version** das Optionsfeld **Entity Framework 5.0** aus, und klicken Sie dann auf die Schaltfläche **Weiter**.

    > [!NOTE]
    > Um die aktuelle Version vom Entity Framework 6 mit WCF-Diensten zu verwenden, müssen Sie das WCF Data Services Entity Framework Provider NuGet-Paket installieren. Weitere Informationen finden [Sie unter Verwenden von WCF Data Services 5.6.0 mit Entity Framework 6 +](https://devblogs.microsoft.com/odata/using-wcf-data-services-5-6-0-with-entity-framework-6/).

8. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**, aktivieren Sie das Kontrollkästchen **Customers**, und wählen Sie dann die Schaltfläche **Fertig stellen**.

     Das Diagramm des Entitäts Modells wird angezeigt, und dem Projekt wird eine *NorthwindModel. edmx* -Datei hinzugefügt.

Im nächsten Schritt erstellen und testen Sie den Datendienst.

### <a name="to-create-the-data-service"></a>So erstellen Sie den Datendienst

1. Wählen Sie in der Menüleiste **Projekt**  >  **Neues Element hinzufügen** aus.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** den Knoten **Web** und anschließend das Element **WCF Data Service 5.6**.

3. Geben Sie im Textfeld **Name** ein `NorthwindCustomers` , und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     Die Datei **NorthwindCustomers.svc** wird im **Code-Editor** angezeigt.

4. Suchen Sie im **Code-Editor`TODO:` den ersten**-Kommentar, und ersetzen Sie den Code durch Folgendes:

     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]

5. Ersetzen Sie die Kommentare im `InitializeService`-Ereignishandler durch folgenden Code:

     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]

6. Wählen Sie in der Menüleiste **Debuggen**  >  **Starten ohne Debugging** aus, um den Dienst auszuführen. Ein Browserfenster wird geöffnet, und das XML-Schema für den Dienst wird angezeigt.

7. Geben Sie in der **Adress** Leiste `Customers` am Ende der URL für **NorthwindCustomers. svc** ein, und drücken Sie dann die **Eingabe** Taste.

     Eine XML-Darstellung der Daten in der `Customers` Tabelle wird angezeigt.

    > [!NOTE]
    > In einigen Fällen interpretiert Internet Explorer die Daten fälschlicherweise als RSS-Feed. Sie müssen sicherstellen, dass die Option zum Anzeigen von RSS-Feeds deaktiviert ist. Weitere Informationen finden Sie unter [Troubleshooting service references (Problembehandlung bei Dienstverweisen)](../data-tools/troubleshooting-service-references.md).

8. Schließen Sie das Browserfenster.

In den nächsten Schritten erstellen Sie eine Windows Forms Client Anwendung, um den Dienst zu nutzen.

## <a name="creating-the-client-application"></a>Erstellen der Clientanwendung
Zum Erstellen der Clientanwendung fügen Sie ein zweites Projekt hinzu, dem Sie einen Dienstverweis hinzufügen. Daraufhin konfigurieren Sie eine Datenquelle und erstellen eine Benutzeroberfläche zum Anzeigen der Daten des Diensts.

Im ersten Schritt fügen Sie ein Windows Forms-Projekt zur Projekt Mappe hinzu und legen es als Startprojekt fest.

### <a name="to-create-the-client-application"></a>So erstellen Sie die Clientanwendung

1. Wählen Sie in der Menüleiste Datei, **Add**  >  **Neues Projekt** hinzufügen aus.

2. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual Basic** oder **Visual c#** , wählen Sie den Knoten **Windows** aus, und wählen Sie dann **Windows Forms Anwendung** aus.

3. Geben Sie im Textfeld **Name**`NorthwindClient` ein, und wählen Sie dann die Schaltfläche **OK** aus.

4. Wählen Sie im **Projektmappen-Explorer** den **NorthwindClient**-Projektknoten.

5. Wählen Sie in der Menüleiste **Projekt**, **Als Startprojekt festlegen** aus.

Im nächsten Schritt fügen Sie dem im Webprojekt einen Dienst Verweis hinzu [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] .

### <a name="to-add-a-service-reference"></a>So fügen Sie einen Dienstverweis hinzu

1. Wählen Sie in der Menüleiste **Projekt**  >  **Dienstverweis hinzufügen** aus.

2. Wählen Sie im Dialogfeld **Dienstverweis hinzufügen** die Schaltfläche **Ermitteln** aus.

     Die URL für den NorthwindCustomers-Dienst wird im Feld **Adresse** angezeigt.

3. Klicken Sie auf die Schaltfläche **OK**, um den Dienstverweis hinzuzufügen.

Im nächsten Schritt konfigurieren Sie eine Datenquelle, um die Datenbindung an den Dienst zu ermöglichen.

### <a name="to-enable-data-binding-to-the-service"></a>So aktivieren Sie die Datenbindung zum Dienst

1. Wählen Sie in der Menüleiste **View**  >  **andere Windows**-  >  **Datenquellen** anzeigen aus.

   Das Fenster **Datenquellen** wird geöffnet.

2. Wählen Sie im Fenster **Datenquellen** die Schaltfläche **Neue Datenquelle hinzufügen**.

3. Wählen Sie auf der Seite **Datenquellentyp auswählen** unter **Assistent zum Konfigurieren von Datenquellen** den Typ **Objekt** und dann die Schaltfläche **Weiter**.

4. Erweitern Sie auf der Seite **Datenobjekte auswählen** den Knoten **NorthwindClient**, und erweitern Sie dann den Knoten **NorthwindClient.ServiceReference1**.

5. Aktivieren Sie das Kontrollkästchen **Customer**, und wählen Sie dann **Fertig stellen**.

Im nächsten Schritt erstellen Sie die Benutzeroberfläche, auf der die Daten aus dem Dienst angezeigt werden.

### <a name="to-create-the-user-interface"></a>So erstellen Sie die Benutzeroberfläche

1. Im Fenster **Datenquellen** öffnen Sie das Kontextmenü für den Knoten **Customers** und wählen **Kopieren** aus.

2. Öffnen Sie im Formular-Designer **Form1.vb** oder **Form1.cs** das Kontextmenü, und wählen Sie **Einfügen** aus.

    Ein <xref:System.Windows.Forms.DataGridView>-Steuerelement, eine <xref:System.Windows.Forms.BindingSource>-Komponente und eine <xref:System.Windows.Forms.BindingNavigator>-Komponente werden dem Formular hinzugefügt.

3. Wählen Sie das **CustomersDataGridView**-Steuerelement aus, und legen Sie dann im Fenster **Eigenschaften** die Eigenschaft **Andocken** auf **Füllbereich** fest.

4. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Knoten **Form1** , und wählen Sie **Code anzeigen** , um den Code-Editor zu öffnen, und fügen Sie `Imports` am Anfang der Datei die folgende-oder- `Using` Anweisung hinzu:

   ```vb
   Imports NorthwindClient.ServiceReference1
   ```

   ```csharp
   using NorthwindClient.ServiceReference1;
   ```

5. Fügen Sie dem `Form1_Load` -Ereignishandler folgenden Code hinzu:

   ```vb
   Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
           Dim proxy As New NorthwindEntities _
   (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))
           Me.CustomersBindingSource.DataSource = proxy.Customers
       End Sub
   ```

   ```csharp
   private void Form1_Load(object sender, EventArgs e)
   {
   NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));
   this.CustomersBindingSource.DataSource = proxy.Customers;
   }
   ```

6. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für die **NorthwindCustomers.svc**-Datei, und wählen Sie **In Browser anzeigen** aus. Internet Explorer wird geöffnet, und das XML-Schema für den Dienst wird angezeigt.

7. Kopieren Sie die URL aus der Adressleiste von Internet Explorer.

8. Markieren Sie in dem in Schritt 4 hinzugefügten Code den Text `http://localhost:53161/NorthwindCustomers.svc/`, und ersetzen Sie diesen durch die soeben kopierte URL.

9. Wählen Sie in der Menüleiste **Debug**  >  **Debuggen Debuggen starten** aus, um die Anwendung auszuführen. Die Kundeninformationen werden angezeigt.

   Sie verfügen nun über eine funktionierende Anwendung, die eine Liste der Kunden aus dem NorthwindCustomers-Dienst anzeigt. Wenn Sie weitere Daten über den Dienst bereitstellen möchten, können Sie das [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] so bearbeiten, dass zusätzliche Tabellen aus der Northwind-Datenbank eingebunden werden.

Im nächsten optionalen Schritt erfahren Sie, wie Sie die Daten filtern, die vom Dienst zurückgegeben werden.

## <a name="adding-filtering-capabilities"></a>Hinzufügen von Filterfunktionen
In diesem Schritt passen Sie die Anwendung an, um die Daten nach der Stadt des Kunden zu filtern.

### <a name="to-add-filtering-by-city"></a>So fügen Sie Filterung anhand des Wohnorts hinzu

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für den Knoten **Form1.vb** oder **Form1.cs**, und wählen Sie dann **Öffnen** aus.

2. Fügen Sie dem Formular ein <xref:System.Windows.Forms.TextBox>- und ein <xref:System.Windows.Forms.Button>-Steuerelement aus der **Toolbox** hinzu.

3. Öffnen Sie das Kontextmenü für das- <xref:System.Windows.Forms.Button> Steuerelement, wählen Sie **Code anzeigen** aus, und fügen Sie dann den folgenden Code im- `Button1_Click` Ereignishandler hinzu:

    ```vb
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
            Dim proxy As New northwindEntities _
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))
            Dim city As String = TextBox1.Text

            If city <> "" Then
                Me.CustomersBindingSource.DataSource = From c In _
             proxy.Customers Where c.City = city
            End If

        End Sub
    ```

    ```csharp
    private void Button1_Click(object sender, EventArgs e)
    {
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));
    string city = TextBox1.Text;

    if (!string.IsNullOrEmpty(city)) {
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;
    }

    }
    ```

4. Ersetzen Sie im vorherigen Code den Text `http://localhost:53161/NorthwindCustomers.svc` durch die URL aus dem `Form1_Load`-Ereignishandler.

5. Wählen Sie in der Menüleiste **Debug**  >  **Debuggen Debuggen starten** aus, um die Anwendung auszuführen.

6. Geben Sie im Textfeld die Zeichenfolge **London** ein, und klicken Sie dann auf die Schaltfläche. Nur die Kunden aus London werden angezeigt.

## <a name="see-also"></a>Weitere Informationen

- [Windows Communication Foundation Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [How to: Hinzufügen, Aktualisieren oder Entfernen eines WCF-Datendienstverweises](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)
