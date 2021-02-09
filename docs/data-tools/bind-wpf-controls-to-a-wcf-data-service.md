---
title: Binden von WPF-Steuerelementen an einen WCF-Datendienst
description: Binden von WPF-Steuerelementen an einen WCF-Datendienst in Visual Studio. Die Steuerelemente sind an Kundendaten Sätze gebunden, die in einem WCF Data Service gekapselt sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 9f3c4cc273d89b5d1fc74596f1f5565177319da7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867359"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Binden von WPF-Steuerelementen an einen WCF-Datendienst

In dieser exemplarischen Vorgehensweise erstellen Sie eine WPF-Anwendung, die datengebundene Steuerelemente enthält. Die Steuerelemente sind an Kundendaten Sätze gebunden, die in einem WCF Data Service gekapselt sind. Sie fügen außerdem die Schaltflächen hinzu, mit denen Kunden Datensätze anzeigen und ändern können.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines Entity Data Models, das aus Daten in der Beispieldatenbank AdventureWorksLT generiert wird.

- Erstellen eines WCF Data Service, der die Daten in der Entity Data Model für eine WPF-Anwendung verfügbar macht.

- Erstellen eines Satzes datengebundener Steuerelemente durch Ziehen von Elementen aus dem Fenster **Datenquellen** zum WPF-Designer.

- Erstellen von Schaltflächen, mit denen die Navigation vorwärts und rückwärts durch die Kundendatensätze möglich ist.

- Erstellen einer Schaltfläche, die Änderungen an Daten in den Steuerelementen für den WCF-Datendienst und die zugrunde liegende Datenquelle speichert.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Voraussetzungen

Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Visual Studio

- Zugriff auf eine laufende Instanz von SQL Server oder SQL Server Express, an die eine AdventureWorksLT-Beispieldatenbank angefügt ist. Sie können die AdventureWorksLT-Datenbank von der [CodePlex-Website](https://archive.codeplex.com/?p=SqlServerSamples)herunterladen.

Vorkenntnisse der folgenden Konzepte sind ebenfalls hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview).

- Datenmodelle in [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].

- Entity Data Models und der ADO.NET Entity Framework. Weitere Informationen finden Sie unter [Entity Framework Übersicht](/dotnet/framework/data/adonet/ef/overview).

- WPF-Datenbindung. Weitere Informationen finden Sie unter [Übersicht über die Datenbindung](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Erstellen des Dienst Projekts

1. Starten Sie diese exemplarische Vorgehensweise durch Erstellen eines c#-oder Visual Basic **ASP.NET-Webanwendungs** Projekts. Nennen Sie das Projekt **AdventureWorksService**.

2. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Default.aspx**, und wählen Sie **Löschen** aus. Diese Datei ist für die exemplarische Vorgehensweise nicht erforderlich.

## <a name="create-an-entity-data-model-for-the-service"></a>Erstellen eines Entity Data Model für den Dienst

Zum verfügbar machen von Daten für eine Anwendung mithilfe eines WCF Data Service müssen Sie ein Datenmodell für den Dienst definieren. Der WCF Data Service unterstützt zwei Arten von Datenmodellen: Entitäts Datenmodelle und benutzerdefinierte Datenmodelle, die mit Common Language Runtime (CLR)-Objekten definiert werden, die die- <xref:System.Linq.IQueryable%601> Schnittstelle implementieren. In dieser exemplarischen Vorgehensweise erstellen Sie ein Entity Data Model für das Datenmodell.

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2. Klicken Sie in der Liste „Installierte Vorlagen“ auf **Daten**, und wählen Sie dann das Projektelement **ADO.NET Entity Data Model** aus.

3. Ändern Sie den Namen in `AdventureWorksModel.edmx` , und klicken Sie auf **Hinzufügen**.

     Der **Assistent für Entity Data Model** wird geöffnet.

4. Klicken Sie auf der Seite **Modellinhalt auswählen** auf **Aus Datenbank generieren**, und klicken Sie auf **Weiter**.

5. Wählen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** eine der folgenden Optionen aus:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank "AdventureWorksLT" verfügbar ist, wählen Sie diese aus.

    - Klicken Sie **Neue Verbindung**, und erstellen Sie eine Verbindung zur Datenbank AdventureWorksLT.

6. Achten Sie darauf, dass auf der Seite **Wählen Sie Ihre Datenverbindung aus** die Option **Entitätsverbindungseinstellungen in App.Config speichern unter**, und klicken Sie dann auf **Weiter**.

7. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Punkt **Tabellen**, und wählen Sie dann die Tabelle **SalesOrderHeader** aus.

8. Klicken Sie auf **Fertig stellen**.

## <a name="create-the-service"></a>Erstellen des Diensts

Erstellen Sie einen WCF Data Service, um die Daten in der Entity Data Model für eine WPF-Anwendung verfügbar zu machen:

1. Wählen Sie im Menü **Projekt** den Eintrag **Neues Element hinzufügen** aus.

2. Klicken Sie in der Liste **Installierte Vorlagen** auf **Web**, und wählen Sie dann das Projektelement **WCF Data Service** aus.

3. Geben Sie im Feld **Name den Namen** ein `AdventureWorksService.svc` , und klicken Sie auf **Hinzufügen**.

     Visual Studio fügt dem `AdventureWorksService.svc` Projekt das hinzu.

## <a name="configure-the-service"></a>Konfigurieren des Diensts

Damit der Dienst mit dem von Ihnen erstellten Entity Data Model funktioniert, muss er konfiguriert werden.

1. Ersetzen Sie in der `AdventureWorks.svc` Codedatei die **AdventureWorksService** -Klassen Deklaration durch den folgenden Code.

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     Dieser Code aktualisiert die **AdventureWorksService** -Klasse, sodass Sie von einem abgeleitet wird, <xref:System.Data.Services.DataService%601> der die `AdventureWorksLTEntities` Objekt Kontext Klasse in ihrer Entity Data Model verarbeitet. Außerdem aktualisiert er die Methode `InitializeService`, sodass Clients des Diensts vollen Lese-/Schreibzugriff auf die `SalesOrderHeader`-Entität haben.

2. Erstellen Sie das Projekt und überprüfen Sie, ob es fehlerfrei erstellt wird.

## <a name="create-the-wpf-client-application"></a>Erstellen der WPF-Client Anwendung

Um die Daten aus dem WCF Data Service anzuzeigen, erstellen Sie eine neue WPF-Anwendung mit einer Datenquelle, die auf dem Dienst basiert. Später in dieser exemplarischen Vorgehensweise werden Sie datengebundene Steuerelemente zur Anwendung hinzufügen.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Lösungsknoten, dann auf **Hinzufügen**, und wählen Sie dann **Neues Projekt** aus.

2. Erweitern Sie im Dialogfeld **Neues Projekt** den Punkt **Visual C#** oder **Visual Basic**, und wählen Sie dann **Windows**.

3. Wählen Sie die Projektvorlage **WPF-Anwendung** aus.

4. Geben Sie im Feld **Name** die Bezeichnung `AdventureWorksSalesEditor` ein, und klicken Sie auf **OK**.

   Visual Studio fügt das `AdventureWorksSalesEditor` Projekt der Projekt Mappe hinzu.

5. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

   Das Fenster **Datenquellen** wird geöffnet.

6. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

   Der Assistent zum **Konfigurieren von Datenquellen** wird geöffnet.

7. Wählen Sie auf der Seite **Datenquellentyp auswählen** des Assistenten **Dienst**, und klicken Sie auf **Weiter**.

8. Klicken Sie im Dialogfeld **Dienstverweis hinzufügen** auf **Ermitteln**.

   Visual Studio durchsucht die aktuelle Projekt Mappe nach verfügbaren Diensten und fügt `AdventureWorksService.svc` Sie der Liste der verfügbaren Dienste im Feld **Dienste** hinzu.

9. Geben Sie im Feld **Namespace** die Zeichenfolge **AdventureWorksService** ein.

10. Geben Sie im Feld **Dienste** den Namen **AdventureWorksService.svc** ein, und klicken Sie auf **OK**.

    Visual Studio lädt die Dienstinformation herunter und kehrt dann zum **Assistenten zum Konfigurieren von Datenquellen** zurück.

11. Klicken Sie auf der Seite **Dienstverweis hinzufügen** auf **Fertig stellen**.

    Visual Studio fügt Knoten hinzu, der die vom Dienst zurückgegebenen Daten im Fenster **Datenquellen** anzeigt.

## <a name="define-the-user-interface"></a>Definieren der Benutzeroberfläche

Fügen Sie dem Fenster eine Reihe von Schaltflächen hinzu, indem Sie XAML im WPF-Designer ändern. Später in dieser exemplarischen Vorgehensweise fügen Sie dann Code hinzu, mit dem Anwender die Verkaufsdatensätze mithilfe dieser Schaltflächen anzeigen und ändern können.

1. Doppelklicken Sie im **Projektmappen-Explorer****MainWindow.xaml**.

   Das Fenster wird automatisch im WPF-Designer geöffnet.

2. Fügen Sie in der [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]-Ansicht des Designers den folgenden Code zwischen den `<Grid>`-Tags hinzu:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="525" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Erstellen Sie das Projekt.

## <a name="create-the-data-bound-controls"></a>Erstellen der Daten gebundenen Steuerelemente

Erstellen Sie Steuerelemente, die Kundendaten Sätze anzeigen, indem `SalesOrderHeaders` Sie den Knoten aus dem **Datenquellen** Fenster in den Designer ziehen.

1. Klicken Sie im Fenster **Datenquellen** das Dropdownmenü für den Knoten **SalesOrderHeaders**, und wählen Sie **Details**.

2. Erweitern Sie den Knoten **SalesOrderHeaders**.

3. In diesem Beispiel werden einige Felder nicht angezeigt. Klicken Sie also das Dropdownmenü neben den folgenden Knoten, und wählen Sie **Keine**:

    - **CreditCardApprovalCode**

    - **ModifiedDate**

    - **OnlineOrderFlag**

    - **RevisionNumber**

    - **ROWGUID**

    Durch diese Aktion wird Visual Studio daran gehindert, im nächsten Schritt datengebundene Steuerelemente für diese Knoten zu erstellen. In dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass der Endbenutzer diese Daten nicht sehen muss.

4. Ziehen Sie aus dem Fenster **Datenquellen** den Knoten **SalesOrderHeaders** auf das Raster unter der Zeile, in der die Schaltflächen sind.

     Visual Studio erzeugt XAML und Code, der einen Satz von Steuerelementen erstellt, die mit Daten in der Tabelle **Product** verbunden sind. Weitere Informationen über den generierten XAML-Code und Code finden [Sie unterbinden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5. Klicken Sie im Designer auf das Textfeld neben der Bezeichnung **Customer ID**.

6. Aktivieren Sie im Fenster **Eigenschaften** das Kontrollkästchen neben der Eigenschaft **IsReadOnly**.

7. Legen Sie die Eigenschaft **IsReadOnly** für jedes der folgenden Textfelder fest:

    - **Bestellnummer**

    - **Sales Order ID**

    - **Sales Order Number**

## <a name="load-the-data-from-the-service"></a>Laden Sie die Daten aus dem Dienst

Verwenden Sie das Dienst Proxy Objekt, um Umsatzdaten aus dem Dienst zu laden. Weisen Sie dann die zurückgegebenen Daten der Datenquelle für die <xref:System.Windows.Data.CollectionViewSource> im WPF-Fenster zu.

1. Im Designer zum Erstellen der `Window_Loaded` Ereignishandler, doppelklicken Sie auf den Text, der gelesen: **MainWindow**.

2. Ersetzen Sie den Ereignishandler durch den folgenden Code. Achten Sie darauf, dass Sie die Adresse *localhost* in diesem Code durch die lokale Hostadresse Ihres Entwicklungscomputers ersetzen.

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>Navigieren in Sales Records

Fügen Sie Code hinzu, mit dem Benutzer mithilfe der Schaltflächen durch Umsatzdaten Sätze scrollen können **\<** and **>** .

1. Doppelklicken Sie im Designer **<** auf die Schaltfläche auf der Fenster Oberfläche.

     Visual Studio öffnet die CodeBehind-Datei und erstellt einen neuen `backButton_Click`-Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click>-Ereignis.

2. Fügen Sie dem generierten `backButton_Click`-Ereignishandler folgenden Code hinzu:

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3. Kehren Sie zum Designer zurück, und doppelklicken Sie auf die **>** Schaltfläche.

     Visual Studio öffnet die CodeBehind-Datei und erstellt einen neuen `nextButton_Click`-Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click>-Ereignis.

4. Fügen Sie dem generierten `nextButton_Click`-Ereignishandler folgenden Code hinzu:

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="save-changes-to-sales-records"></a>Änderungen an Verkaufsdaten Sätzen speichern

Fügen Sie Code hinzu, mit dem Benutzer Änderungen an Sales Records sowohl anzeigen als auch mithilfe der Schaltfläche **Änderungen speichern** speichern können.

1. Doppelklicken Sie im Designer auf die Schaltfläche **Änderungen speichern** .

     Visual Studio öffnet die CodeBehind-Datei und erstellt einen neuen `saveButton_Click`-Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click>-Ereignis.

2. Fügen Sie dem `saveButton_Click`-Ereignishandler den folgenden Code hinzu.

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="test-the-application"></a>Testen der Anwendung

Erstellen Sie die Anwendung und führen Sie sie aus; prüfen Sie, ob Sie Kundendatensätze anzeigen und ändern können:

1. Klicken Sie im Menü **Erstellen** auf Projekt Mappe **Erstellen**. Überprüfen Sie, ob die Lösung ohne Fehler erstellt wurde.

2. Drücken Sie **STRG** + **F5**.

     Visual Studio startet das Projekt **AdventureWorksService** ohne es zu debuggen.

3. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **AdventureWorksSalesEditor**.

4. Klicken Sie im Kontextmenü (Kontextmenü) unter **Debuggen** auf **neue Instanz starten**.

     Die Anwendung wird ausführt. Überprüfen Sie Folgendes:

    - Die Textfelder zeigen unterschiedliche Datenfelder aus dem ersten Verkaufsdatensatz an, der die Sales Order ID **71774** vorweist.

    - Sie können auf die **>** Schaltflächen oder klicken **<** , um durch andere Verkaufsdaten Sätze zu navigieren.

5. Geben Sie Text in einen der Verkaufsdatensätze im Feld **Comment** ein, und klicken Sie anschließend auf **Änderungen speichern**.

6. Schließen Sie die Anwendung und starten Sie sie dann erneut aus Visual Studio.

7. Navigieren Sie zum Verkaufsdatensatz, den Sie geändert haben und überprüfen Sie, dass die Änderung nach dem Schließen und erneut Öffnen noch vorhanden ist.

8. Schließen Sie die Anwendung.

## <a name="next-steps"></a>Nächste Schritte

Nach Abschluss dieser exemplarischen Vorgehensweise können Sie folgende Aufgaben ausführen:

- Erfahren Sie, wie Sie das **Datenquellenfenster** in Visual Studio für die Bindung von WPF-Steuerelementen an andere Typen von Datenquellen verwenden. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an ein DataSet](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Erfahren Sie, wie Sie das **Datenquellenfenster** in Visual Studio für die Anzeige zugehöriger Daten (das heißt, Daten in einer Beziehung zwischen übergeordneten und untergeordneten Daten) in WPF-Steuerelementen verwenden. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Anzeigen verknüpfter Daten in einer WPF-Anwendung](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Weitere Informationen

- [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Binden von WPF-Steuerelementen an ein Dataset](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [Übersicht über WCF (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Übersicht über Entity Framework (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Übersicht über die Datenbindung (.NET Framework)](/dotnet/desktop-wpf/data/data-binding-overview)
