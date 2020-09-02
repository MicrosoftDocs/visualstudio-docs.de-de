---
title: Binden von WPF-Steuerelementen an ein DataSet | Microsoft-Dokumentation
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
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 937e28e923c26a72940b0181da16cf34199bb9aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852155"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Binden von WPF-Steuerelementen an ein Dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise erstellen Sie eine WPF-Anwendung, die datengebundene Steuerelemente enthält. Die Steuerelemente sind an Produktdatensätze gebunden, die in einem Dataset gekapselt sind. Sie fügen außerdem Schaltflächen hinzu, mit denen es möglich ist, Produkte zu durchsuchen und Änderungen an Produktdatensätzen zu speichern.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen einer WPF-Anwendung und eines Datasets, das aus Daten in der Beispieldatenbank AdventureWorksLT generiert wird.

- Erstellen mehrerer datengebundener Steuerelemente durch Ziehen einer Datentabelle aus dem **Datenquellenfenster** zu einem Fenster im WPF-Designer.

- Erstellen von Schaltflächen, mit denen die Navigation vorwärts und rückwärts durch die Produktdatensätze möglich ist.

- Erstellen einer Schaltfläche, die Änderungen durch Kunden an den Produktdatensätzen in der Tabelle und der darunterliegenden Datenquelle speichert.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- Zugriff auf eine laufende Instanz von SQL Server oder SQL Server Express, an die eine AdventureWorksLT-Beispieldatenbank angefügt ist. Sie können die AdventureWorksLT-Datenbank von der [CodePlex-Website](https://codeplex.com/SqlServerSamples)herunterladen.

  Vorkenntnisse der folgenden Konzepte sind ebenfalls hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- DataSets und TableAdapters. Weitere Informationen finden Sie unter [DataSet-Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Arbeiten mit dem WPF-Designer. Weitere Informationen finden Sie unter [Übersicht über WPF-und Silverlight-Designer](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- WPF-Datenbindung. Weitere Informationen finden Sie unter [Übersicht über die Datenbindung](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="create-the-project"></a>Erstellen eines Projekts
 Erstellen eines neuen WPF-Projekts. Das Projekt zeigt Produktdatensätze.

#### <a name="to-create-the-project"></a>So erstellen Sie das Projekt

1. Starten Sie Visual Studio.

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

3. Erweitern Sie **Visual Basic** oder** Visual C#**, und wählen Sie dann **Windows** aus.

4. Wählen Sie die Projektvorlage **WPF-Anwendung** aus.

5. Geben Sie im Feld **Name**`AdventureWorksProductsEditor` ein, und klicken Sie auf **OK**.

     Visual Studio erstellt das `AdventureWorksProductsEditor` Projekt.

## <a name="create-a-dataset-for-the-application"></a>Erstellen eines Datasets für die Anwendung
 Ehe Sie datengebundene Steuerelemente erstellen können, müssen Sie ein Datenmodell für die Anwendung definieren und es dem **Datenquellenfenster** hinzufügen. In dieser exemplarischen Vorgehensweise erstellen Sie ein Dataset als Datenmodell.

#### <a name="to-create-a-dataset"></a>So erstellen Sie ein Dataset

1. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

     Das Fenster **Datenquellen** wird geöffnet.

2. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

     Der Assistent zum **Konfigurieren von Datenquellen** wird geöffnet.

3. Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie dann auf **Weiter**.

4. Wählen Sie auf der Seite **Wählen Sie ein Datenbankmodell aus** die Option **DataSet** aus, und klicken Sie dann auf **Weiter**.

5. Wählen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** eine der folgenden Optionen aus:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „AdventureWorksLT“ verfügbar ist, wählen Sie diese aus, und klicken Sie anschließend auf **Weiter**.

    - Klicken Sie **Neue Verbindung**, und erstellen Sie eine Verbindung zur Datenbank AdventureWorksLT.

6. Wählen Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** das Kontrollkästchen **Ja, Verbindung speichern unter**, und klicken Sie anschließend auf **Weiter**.

7. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Punkt **Tabellen**, und wählen Sie dann die Tabelle **Product (SalesLT)** aus.

8. Klicken Sie auf **Fertig stellen**.

     Visual Studio fügt dem Projekt eine neue Datei "AdventureWorksLTDataSet. xsd" hinzu und fügt dem **Datenquellen** Fenster ein entsprechendes **AdventureWorksLTDataSet** -Element hinzu. Die Datei AdventureWorksLTDataSet.xsd definiert ein typisiertes Dataset namens `AdventureWorksLTDataSet` und einen TableAdapter namens `ProductTableAdapter`. Weiter unten in dieser exemplarischen Vorgehensweise verwenden Sie `ProductTableAdapter` für das Füllen des Datasets mit Daten und speichern die Änderungen zurück in die Datenbank.

9. Erstellen Sie das Projekt.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Bearbeiten der Standard Füllmethode des TableAdapter
 Verwenden Sie zum Füllen des Datasets die `Fill`-Methode des `ProductTableAdapter`. Standardmäßig füllt die `Fill`-Methode die `ProductDataTable` im `AdventureWorksLTDataSet` mit allen Datenzeilen aus der Product-Tabelle. Sie können diese Methode modifizieren, sodass nur eine Teilmenge von Zeilen zurückgeben wird. Ändern Sie für diese exemplarische Vorgehensweise die `Fill`-Methode, sodass nur Zeilen für Produkte zurückgegeben werden, die Fotos haben.

#### <a name="to-load-product-rows-that-have-photos"></a>So laden Sie Produktzeilen, die Fotos haben

1. Öffnen Sie im **Projektmappen-Explorer** die Datei AdventureWorksLTDataSet.xsd.

     Der DataSet-Designer wird geöffnet.

2. Klicken Sie im Designer mit der rechten Maustaste auf die Abfrage **Fill, GetData (),** und wählen Sie **Konfigurieren**aus.

     Der **TableAdapter-Konfigurations-Assistent** wird geöffnet.

3. Fügen Sie auf der Seite **SQL-Anweisung eingeben** die folgende WHERE-Klausel nach der `SELECT`-Anweisung im Textfeld ein.

    ```
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. Klicken Sie auf **Fertig stellen**.

## <a name="define-the-user-interface"></a>Definieren der Benutzeroberfläche
 Fügen Sie dem Fenster eine Reihe von Schaltflächen hinzu, indem Sie XAML im WPF-Designer ändern. Später in dieser exemplarischen Vorgehensweise fügen Sie dann Code hinzu, mit dem Anwender durch Produktdatensätze blättern und Änderungen daran mithilfe dieser Schaltflächen speichern können.

#### <a name="to-define-the-user-interface-of-the-window"></a>Die Benutzeroberfläche des Fensters definieren

1. Doppelklicken Sie in **Projektmappen-Explorer**auf die Datei MainWindow. XAML.

     Das Fenster wird automatisch im WPF-Designer geöffnet.

2. Fügen Sie in der [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]-Ansicht des Designers den folgenden Code zwischen den `<Grid>`-Tags hinzu:

    ```
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="625" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3. Erstellen Sie das Projekt.

## <a name="createdata-bound-controls"></a>Daten gebundene Steuerelemente
 Erstellen Sie Steuerelemente, die Kundendaten Sätze anzeigen, indem `Product` Sie die Tabelle aus dem **Datenquellen** Fenster in den WPF-Designer ziehen.

#### <a name="to-create-data-bound-controls"></a>So erstellen Sie datengebundene Steuerelemente

1. Klicken Sie im **Datenquellenfenster** das Dropdownmenü für den Knoten **Product**, und klicken Sie auf **Details**.

2. Erweitern Sie den **Product**-Knoten.

3. In diesem Beispiel werden einige Felder nicht angezeigt. Klicken Sie also das Dropdownmenü neben den folgenden Knoten, und wählen Sie **Keine**:

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - rowguid

    - ModifiedDate

4. Klicken Sie auf das Dropdownmenü neben dem Knoten-**ThumbNailPhoto**, und wählen Sie **Bild**.

    > [!NOTE]
    > Standardmäßig haben Elemente im Fenster **Datenquellen**, die Bilder repräsentieren, als Steuerelementsatz **Kein** ausgewählt. Dies ist deshalb so, weil Bilder als Bytearrays in Datenbanken gespeichert werden und alles enthalten können, von einer einfachen Array an Bytes bis zur ausführbaren Datei einer großen Anwendung.

5. Ziehen Sie aus dem Fenster **Datenquellen** den Knoten **Product** auf das Raster unter der Zeile, in der die Schaltflächen sind.

     Visual Studio erzeugt XAML, der mehrere Steuerelemente definiert, die an Daten in der Tabelle **Products** gebunden sind. Es generiert außerdem Code, der die Daten lädt. Weitere Informationen über den generierten XAML-Code und Code finden [Sie unterbinden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

6. Klicken Sie im Designer auf das Textfeld neben der Bezeichnung **Product ID**.

7. Aktivieren Sie im Fenster **Eigenschaften** das Kontrollkästchen neben der Eigenschaft **IsReadOnly**.

## <a name="navigating-product-records"></a>Navigieren in Produktdaten Sätzen
 Fügen Sie Code hinzu, mit dem Benutzer durch Produktdaten Sätze scrollen können, indem Sie die Schaltflächen verwenden **\<** and **>** .

#### <a name="to-enable-users-to-navigate-product-records"></a>Benutzern das Navigieren durch Product Records ermöglichen

1. Doppelklicken Sie im Designer **<** auf die Schaltfläche auf der Fenster Oberfläche.

     Visual Studio öffnet die CodeBehind-Datei und erstellt einen neuen `backButton_Click`-Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click>-Ereignis.

2. Ändern Sie den `Window_Loaded`-Ereignishandler, sodass `ProductViewSource`, `AdventureWorksLTDataSet` und `AdventureWorksLTDataSetProductTableAdapter` sich außerhalb der Methode befinden und für das gesamte Formular zugänglich sind. Deklarieren Sie nur diese als Global für das Formular, und weisen Sie diese innerhalb des `Window_Loaded` Ereignis Handlers ähnlich dem folgenden zu:

     [!code-csharp[Data_WPFDATASET#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#1)]
     [!code-vb[Data_WPFDATASET#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#1)]

3. Fügen Sie dem `backButton_Click` -Ereignishandler folgenden Code hinzu:

     [!code-csharp[Data_WPFDATASET#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFDATASET#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#2)]

4. Kehren Sie zum Designer zurück, und doppelklicken Sie auf die **>** Schaltfläche.

5. Fügen Sie dem `nextButton_Click` -Ereignishandler folgenden Code hinzu:

     [!code-csharp[Data_WPFDATASET#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFDATASET#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#3)]

## <a name="savechanges-to-product-records"></a>SaveChanges für Produktdaten Sätze
 Fügen Sie Code hinzu, mit dem Benutzer Änderungen an Product Records mithilfe der Taste **Änderungen speichern** speichern können.

#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Die Möglichkeit zum Speichern von Änderungen zu Product Records hinzufügen

1. Doppelklicken Sie im Designer auf die Schaltfläche **Änderungen speichern**.

     Visual Studio öffnet die CodeBehind-Datei und erstellt einen neuen `saveButton_Click`-Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click>-Ereignis.

2. Fügen Sie dem `saveButton_Click` -Ereignishandler folgenden Code hinzu:

     [!code-csharp[Data_WPFDATASET#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFDATASET#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#4)]

    > [!NOTE]
    > In diesem Beispiel wird die Methode `Save` des `TableAdapter` für das Speichern von Änderungen verwendet. Das ist in dieser exemplarischen Vorgehensweise angebracht, denn es wird nur eine Datentabelle geändert. Wenn Sie Änderungen an mehreren Datentabellen speichern möchten, können Sie alternativ die Methode `UpdateAll` des `TableAdapterManager` einsetzen, die Visual Studio mit dem Dataset generiert. Weitere Informationen finden Sie unter [Übersicht über den TableAdapterManager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).

## <a name="test-the-application"></a>Testen der App
 Erstellen Sie die Anwendung, und führen Sie sie aus. Stellen Sie sicher, dass Sie Produktdatensätze anzeigen und ändern können.

#### <a name="to-test-the-application"></a>So testen Sie die Anwendung

1. Drücken Sie **F5**.

     Die Anwendung wird erstellt und ausgeführt. Überprüfen Sie Folgendes:

    - Die Textfelder zeigen Daten aus dem ersten Produktdatensatz, der ein Foto hat. Dieses Produkt hat die ID 713 und heißt **Long-Sleeve Logo Jersey, S**.

    - Sie können auf die **>** Schaltflächen oder klicken **<** , um durch andere Produktdaten Sätze zu navigieren.

2. Ändern Sie in einem der Datensätze im Feld **Größe** den Wert, und klicken Sie anschließend auf **Änderungen speichern**.

3. Schließen Sie die Anwendung, und starten Sie dann die Anwendung in Visual Studio erneut, indem Sie **F5** drücken.

4. Navigieren Sie zum Produktdatensatz, den Sie geändert haben und prüfen Sie, ob die Änderung gespeichert wurde.

5. Schließen Sie die Anwendung.

## <a name="next-steps"></a>Nächste Schritte
 Nach Abschluss dieser exemplarischen Vorgehensweise können Sie folgende Aufgaben ausführen:

- Erfahren Sie, wie Sie das **Datenquellenfenster** in Visual Studio für die Bindung von WPF-Steuerelementen an andere Typen von Datenquellen verwenden. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Erfahren Sie, wie Sie das **Datenquellenfenster** in Visual Studio für die Anzeige zugehöriger Daten (das heißt, Daten in einer Beziehung zwischen übergeordneten und untergeordneten Daten) in WPF-Steuerelementen verwenden. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Anzeigen verknüpfter Daten in einer WPF-Anwendung](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).

## <a name="see-also"></a>Weitere Informationen
 [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [DataSet-Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) [WPF-und Silverlight-Designer Übersicht Übersicht](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62) über die [Datenbindung](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)
