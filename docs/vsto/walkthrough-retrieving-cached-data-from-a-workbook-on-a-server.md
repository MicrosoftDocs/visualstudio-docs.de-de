---
title: 'Exemplarische Vorgehensweise: Abrufen von zwischengespeicherten Daten aus einer Arbeitsmappe auf einem Server'
description: Erfahren Sie, wie Sie Daten aus einem DataSet abrufen können, das in einer Microsoft Excel-Arbeitsmappe zwischengespeichert ist, ohne Excel mit der ServerDocument-Klasse zu starten.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], retrieving data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 818c7c9aa5edeae32859d0b5af6449b513df1c85
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937442"
---
# <a name="walkthrough-retrieve-cached-data-from-a-workbook-on-a-server"></a>Exemplarische Vorgehensweise: Abrufen von zwischengespeicherten Daten aus einer Arbeitsmappe auf einem Server
  Diese exemplarische Vorgehensweise veranschaulicht, wie Daten aus einem DataSet, das in einer Microsoft Office Excel-Arbeitsmappe zwischengespeichert ist, abgerufen werden, ohne Excel mit der-Klasse zu starten <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> .

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Definieren eines Datasets, das Daten aus der *AdventureWorksLT* -Datenbank enthält.

- Erstellen von Instanzen des Datasets in einem Excel-Arbeitsmappenprojekt und einem Konsolen Anwendungsprojekt.

- Erstellen einer <xref:Microsoft.Office.Tools.Excel.ListObject> , die an das Dataset in der Arbeitsmappe gebunden ist, und Auffüllen der <xref:Microsoft.Office.Tools.Excel.ListObject> mit Daten, wenn die Arbeitsmappe geöffnet wird.

- Hinzufügen des Datasets in der Arbeitsmappe zum Daten Cache.

- Lesen von Daten aus dem zwischengespeicherten Dataset in das Dataset in der Konsolenanwendung, ohne Excel zu starten.

  Obwohl in dieser exemplarischen Vorgehensweise davon ausgegangen wird, dass Sie den Code auf dem Entwicklungs Computer ausführen, kann der in dieser exemplarischen Vorgehensweise gezeigte Code auf einem Server verwendet werden, auf dem Excel nicht installiert ist.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Zugriff auf eine laufende Instanz von Microsoft SQL Server oder Microsoft SQL Server Express, der die AdventureWorksLT-Beispieldatenbank angefügt ist. Sie können die AdventureWorksLT-Datenbank von der [CodePlex-Website](https://archive.codeplex.com/?p=SqlServerSamples)herunterladen. Weitere Informationen zum Anhängen von Datenbanken finden Sie in den folgenden Themen:

  - Informationen zum Anfügen einer Datenbank mithilfe von SQL Server Management Studio oder SQL Server Management Studio Express finden Sie unter Vorgehens [Weise: Anfügen einer Datenbank (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Informationen zum Anfügen einer Datenbank über die Befehlszeile finden Sie unter Gewusst [wie: Anfügen einer Datenbankdatei an SQL Server Express](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Erstellen eines Klassen Bibliotheks Projekts, das ein Dataset definiert
 Um das gleiche DataSet in einem Excel-Arbeitsmappenprojekt und einer Konsolenanwendung zu verwenden, müssen Sie das Dataset in einer separaten Assembly definieren, auf die von beiden Projekten verwiesen wird. In dieser exemplarischen Vorgehensweise definieren Sie das Dataset in einem Klassen Bibliotheksprojekt.

### <a name="create-the-class-library-project"></a>Erstellen des Klassenbibliotheksprojekts

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

3. Erweitern Sie im Bereich Vorlagen den Eintrag **Visual c#** , oder **Visual Basic**, und klicken Sie dann auf **Windows**.

4. Wählen Sie in der Liste der Projektvorlagen die Option **Klassenbibliothek** aus.

5. Geben Sie im Feld **Name den Namen** **AdventureWorksDataSet** ein.

6. Klicken Sie auf **Durchsuchen**, navigieren Sie zu Ihrem Ordner *%USERPROFILE%\Eigene Dokumente* (für Windows XP und früher) oder *%UserProfile%\Documents* (für Windows Vista), und klicken Sie dann auf **Ordner auswählen**.

7. Vergewissern Sie sich, dass im Dialogfeld **Neues Projekt** das Kontrollkästchen **Verzeichnis für** Projekt Mappe erstellen deaktiviert ist.

8. Klicken Sie auf **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt das Projekt **AdventureWorksDataSet** **Projektmappen-Explorer** hinzu und öffnet die Codedatei *Class1.cs* oder *Class1. vb* .

9. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf *Class1.cs* oder *Class1. vb*, und klicken Sie dann auf **Löschen**. Diese Datei ist für diese exemplarische Vorgehensweise nicht erforderlich.

## <a name="define-a-dataset-in-the-class-library-project"></a>Definieren eines Datasets im Klassen Bibliotheksprojekt
 Definieren Sie ein typisiertes DataSet, das Daten aus der AdventureWorksLT-Datenbank für SQL Server 2005 enthält. Später in dieser exemplarischen Vorgehensweise verweisen Sie auf dieses DataSet aus einem Excel-Arbeitsmappenprojekt und einem Konsolen Anwendungsprojekt.

 Das DataSet ist ein *typisiertes DataSet* , das die Daten in der Product-Tabelle der AdventureWorksLT-Datenbank darstellt. Weitere Informationen zu typisierten Datasets finden Sie unter [DataSet-Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="define-a-typed-dataset-in-the-class-library-project"></a>Definieren eines typisierten Datasets im Klassen Bibliotheksprojekt

1. Klicken Sie in **Projektmappen-Explorer** auf das Projekt **AdventureWorksDataSet** .

2. Wenn das Fenster **Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie auf der Menüleiste **die Option**  >  **Weitere Windows**-  >  **Datenquellen** anzeigen auswählen.

3. Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

4. Klicken Sie auf **Datenbank**, und klicken Sie dann auf **Weiter**.

5. Wenn Sie über eine vorhandene Verbindung mit der AdventureWorksLT-Datenbank verfügen, wählen Sie diese Verbindung aus, und klicken Sie auf **weiter**.

    Klicken Sie andernfalls auf **Neue Verbindung**, und erstellen Sie die neue Verbindung im Dialogfeld **Verbindung hinzufügen** . Weitere Informationen finden Sie unter [Hinzufügen neuer Verbindungen](../data-tools/add-new-connections.md).

6. Klicken Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** auf **Weiter**.

7. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen** , und wählen Sie **Product (SalesLT)** aus.

8. Klicken Sie auf **Fertig stellen**.

    Die Datei " *AdventureWorksLTDataSet. xsd* " wird dem Projekt " **AdventureWorksDataSet** " hinzugefügt. In dieser Datei sind die folgenden Elemente definiert:

   - Ein typisiertes Dataset namens `AdventureWorksLTDataSet`. Dieses DataSet stellt den Inhalt der Product-Tabelle in der AdventureWorksLT-Datenbank dar.

   - Ein TableAdapter mit dem Namen `ProductTableAdapter` . Dieser TableAdapter kann verwendet werden, um Daten in zu lesen und zu schreiben `AdventureWorksLTDataSet` . Weitere Informationen finden Sie unter [Übersicht über TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise verwenden Sie beide Objekte.

9. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **AdventureWorksDataSet** , und klicken Sie auf **Erstellen**.

     Vergewissern Sie sich, dass das Projekt ohne Fehler erstellt wurde.

## <a name="create-an-excel-workbook-project"></a>Erstellen eines Excel-Arbeitsmappenprojekts
 Erstellen Sie ein Excel-Arbeitsmappenprojekt für die-Schnittstelle zu den Daten. Später in dieser exemplarischen Vorgehensweise erstellen Sie einen, <xref:Microsoft.Office.Tools.Excel.ListObject> der die Daten anzeigt, und Sie fügen dem Daten Cache in der Arbeitsmappe eine Instanz des Datasets hinzu.

### <a name="create-the-excel-workbook-project"></a>Erstellen des Excel-Arbeitsmappenprojekts

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf die Projekt **Mappe AdventureWorksDataSet** , zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt**.

2. Erweitern Sie im Vorlagenbereich **Visual C#** oder **Visual Basic** und dann **Office/SharePoint**.

3. Wählen Sie unter dem erweiterten Knoten **Office/SharePoint** den Knoten **Office-Add-Ins** aus.

4. Wählen Sie in der Liste der Projektvorlagen das Projekt **Excel 2010-Arbeitsmappe** oder **Excel 2013-Arbeitsmappe** aus.

5. Geben Sie im Feld **Name den Namen** **AdventureWorksReport** ein. Ändern Sie den Speicherort nicht.

6. Klicken Sie auf **OK**.

     Der **Projekt-Assistent aus Visual Studio Tools for Office** wird geöffnet.

7. Stellen Sie sicher, dass **Create a New Document** ausgewählt ist, und klicken Sie auf **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Öffnet die **AdventureWorksReport** -Arbeitsmappe im Designer und fügt das Projekt **AdventureWorksReport** **Projektmappen-Explorer** hinzu.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Hinzufügen des Datasets zu Datenquellen im Excel-Arbeitsmappenprojekt
 Bevor Sie das Dataset in der Excel-Arbeitsmappe anzeigen können, müssen Sie das Dataset zuerst den Datenquellen im Excel-Arbeitsmappenprojekt hinzufügen.

1. Doppelklicken Sie in **Projektmappen-Explorer** unter dem Projekt **AdventureWorksReport** auf *Sheet1.cs* oder *Sheet1. vb* .

     Die Arbeitsmappe wird im Designer geöffnet.

2. Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.

     Der **Assistent zum Konfigurieren von Datenquellen** wird geöffnet.

3. Klicken Sie auf **Objekt** und dann auf **weiter**.

4. Klicken Sie auf der Seite **Wählen Sie das Objekt aus, an das die Bindung** erfolgen soll auf **Verweis hinzufügen**.

5. Klicken Sie auf der Registerkarte **Projekte** auf **AdventureWorksDataSet** , und klicken Sie dann auf **OK**.

6. Klicken Sie im **AdventureWorksDataSet** -Namespace der **AdventureWorksDataSet** -Assembly auf **AdventureWorksLTDataSet** , und klicken Sie dann auf **Fertig** stellen.

     Das Fenster **Datenquellen** wird geöffnet, und **AdventureWorksLTDataSet** wird der Liste mit den Datenquellen hinzugefügt.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Erstellen eines ListObject, das an eine Instanz des Datasets gebunden ist
 Um das Dataset in der Arbeitsmappe anzuzeigen, erstellen Sie ein-Element, <xref:Microsoft.Office.Tools.Excel.ListObject> das an eine Instanz des Datasets gebunden ist. Weitere Informationen zum Binden von Steuerelementen an Daten finden Sie unter [Binden von Daten an Steuerelemente in Office](../vsto/binding-data-to-controls-in-office-solutions.md)-Projektmappen.

1. Erweitern Sie im Fenster **Datenquellen** den Knoten **AdventureWorksLTDataSet** unter **AdventureWorksDataSet**.

2. Wählen Sie den Knoten **Product** aus, klicken Sie auf den angezeigten Dropdown Pfeil, und wählen Sie in der Dropdown Liste **ListObject** aus.

     Wenn der Dropdown Pfeil nicht angezeigt wird, vergewissern Sie sich, dass die Arbeitsmappe im Designer geöffnet ist.

3. Ziehen Sie die **Product** -Tabelle in die Zelle a1.

     Im <xref:Microsoft.Office.Tools.Excel.ListObject> Arbeitsblatt wird ein-Steuerelement `productListObject` mit dem Namen erstellt, beginnend in Zelle a1. Gleichzeitig werden dem Projekt ein Datasetobjekt namens `adventureWorksLTDataSet` und ein <xref:System.Windows.Forms.BindingSource> -Objekt namens `productBindingSource` hinzugefügt. Das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement ist an das <xref:System.Windows.Forms.BindingSource>-Objekt gebunden, das wiederum an das Datasetobjekt gebunden ist.

## <a name="add-the-dataset-to-the-data-cache"></a>Hinzufügen des Datasets zum Daten Cache
 Um Code außerhalb des Excel-Arbeitsmappenprojekts für den Zugriff auf das Dataset in der Arbeitsmappe zu aktivieren, müssen Sie das DataSet dem Daten Cache hinzufügen. Weitere Informationen zum Daten Cache finden Sie unter [zwischengespeicherte Daten in Anpassungen auf Dokument Ebene](../vsto/cached-data-in-document-level-customizations.md) und [Cache Daten](../vsto/caching-data.md).

1. Klicken Sie im Designer auf **AdventureWorksLTDataSet**.

2. Legen Sie im Fenster **Eigenschaften** die **modifizierereigenschaft** auf **Public** fest.

3. Legen Sie die **CacheInDocument** -Eigenschaft auf **true** fest.

## <a name="initialize-the-dataset-in-the-workbook"></a>Initialisieren des Datasets in der Arbeitsmappe
 Bevor Sie die Daten aus dem zwischengespeicherten Dataset mithilfe der Konsolenanwendung abrufen können, müssen Sie zuerst das zwischengespeicherte Dataset mit Daten auffüllen.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf die Datei *Sheet1.cs* oder *Sheet1. vb* , und klicken Sie dann auf **Code anzeigen**.

2. Ersetzen Sie den `Sheet1_Startup` -Ereignishandler durch den folgenden Code. In diesem Code wird eine Instanz der-Klasse verwendet, die `ProductTableAdapter` im Projekt **AdventureWorksDataSet** definiert ist, um das zwischengespeicherte Dataset mit Daten auszufüllen, wenn es derzeit leer ist.

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>Prüfpunkt
 Erstellen und führen Sie das Excel-Arbeitsmappenprojekt aus, um sicherzustellen, dass es ohne Fehler kompiliert und ausgeführt wird. Dieser Vorgang füllt auch das zwischengespeicherte Dataset und speichert die Daten in der Arbeitsmappe.

### <a name="build-and-run-the-project"></a>Erstellen und Ausführen des Projekts

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **AdventureWorksReport** , wählen Sie **Debuggen** aus, und klicken Sie dann auf **neue Instanz starten**.

     Das Projekt wird erstellt, und die Arbeitsmappe wird in Excel geöffnet. Überprüfen Sie Folgendes:

    - <xref:Microsoft.Office.Tools.Excel.ListObject>Füllt mit Daten.

    - Der Wert in der **ListPrice** -Spalte für die erste Zeile von <xref:Microsoft.Office.Tools.Excel.ListObject> ist 1431,5. Später in dieser exemplarischen Vorgehensweise verwenden Sie eine Konsolenanwendung, um die Werte in der **ListPrice** -Spalte zu ändern.

2. Speichern Sie die Arbeitsmappe. Ändern Sie den Dateinamen oder den Speicherort der Arbeitsmappe nicht.

3. Schließen Sie Excel.

## <a name="create-a-console-application-project"></a>Erstellen eines Konsolen Anwendungs Projekts
 Erstellen Sie ein Konsolen Anwendungsprojekt, das zum Ändern von Daten im zwischengespeicherten Dataset in der Arbeitsmappe verwendet werden soll.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf die Projekt **Mappe AdventureWorksDataSet** , zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt**.

2. Erweitern Sie im Bereich **Projekttypen** den Eintrag **Visual c#** , oder **Visual Basic**, und klicken Sie dann auf **Windows**.

3. Wählen Sie im Bereich **Vorlagen** die Option **Konsolenanwendung** aus.

4. Geben Sie im Feld **Name den Namen** **DataReader** ein. Ändern Sie den Speicherort nicht.

5. Klicken Sie auf **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]fügt **Projektmappen-Explorer** das **DataReader** -Projekt hinzu und öffnet die Codedatei *Program.cs* oder *Module1. vb* .

## <a name="retrieve-data-from-the-cached-dataset-by-using-the-console-application"></a>Abrufen von Daten aus dem zwischengespeicherten Dataset mithilfe der Konsolenanwendung
 Verwenden Sie die- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse in der Konsolenanwendung, um die Daten in einem lokalen Objekt zu lesen `AdventureWorksLTDataSet` . Um zu bestätigen, dass das lokale Dataset mit Daten aus dem zwischengespeicherten Dataset initialisiert wurde, zeigt die Anwendung die Anzahl der Zeilen im lokalen Dataset an.

### <a name="retrieve-data-from-the-cached-dataset"></a>Abrufen von Daten aus dem zwischengespeicherten Dataset

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **DataReader** , und klicken Sie auf **Verweis hinzufügen**.

2. Wählen Sie auf der Registerkarte **.net** die Option **Microsoft. VisualStudio. Tools. Applications. ServerDocument** aus.

3. Klicken Sie auf **OK**.

4. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **DataReader** , und klicken Sie auf **Verweis hinzufügen**.

5. Wählen Sie auf der Registerkarte **Projekte** die Option **AdventureWorksDataSet** aus, und klicken Sie auf **OK**.

6. Öffnen Sie im Code-Editor die Datei *Program.cs* oder *Module1. vb* .

7. Fügen Sie am Anfang der Codedatei die folgenden **using** -(for c#)-oder **Imports** -Anweisung (für Visual Basic) hinzu.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. Fügen Sie der `Main` -Methode den folgenden Code hinzu. Dieser Code deklariert die folgenden Objekte:

   - Eine Instanz des `AdventureWorksLTDataSet` Typs, der im **AdventureWorksDataSet** -Projekt definiert ist.

   - Der Pfad zur Arbeitsmappe "AdventureWorksReport" im Ordner "Build" des Projekts " **AdventureWorksReport** ".

   - Ein- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Objekt, das für den Zugriff auf den Daten Cache in der Arbeitsmappe verwendet werden soll.

     > [!NOTE]
     > Der folgende Code setzt voraus, dass die Arbeitsmappe mit der Erweiterung *. xlsx* gespeichert wird. Wenn die Arbeitsmappe in Ihrem Projekt eine andere Erweiterung hat, ändern Sie den Pfad nach Bedarf.

     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]

9. Fügen Sie der-Methode den folgenden Code `Main` nach dem Code hinzu, den Sie im vorherigen Schritt hinzugefügt haben. Mit diesem Code werden die folgenden Aufgaben durchgeführt:

   - Die- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Eigenschaft der-Klasse wird verwendet <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> , um auf das zwischengespeicherte Dataset in der Arbeitsmappe zuzugreifen.

   - Sie liest die Daten aus dem zwischengespeicherten Dataset in das lokale Dataset.

   - Er zeigt die Anzahl der Zeilen im lokalen Dataset an, um zu bestätigen, dass er Daten enthält.

     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]

10. Klicken Sie im Menü **Erstellen** auf **DataReader erstellen**.

## <a name="test-the-project"></a>Testen des Projekts
 Wenn Sie die Konsolenanwendung ausführen, wird die Anzahl der Zeilen im lokalen Dataset angezeigt.

### <a name="test-the-workbook"></a>Testen der Arbeitsmappe

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **DataReader** , zeigen Sie auf **Debuggen**, und klicken Sie dann auf **neue Instanz starten**.

     Vergewissern Sie sich, dass die Anwendung meldet, dass das lokale Dataset 295 Zeilen enthält.

2. Drücken Sie die **Eingabetaste** , um die Anwendung zu schließen.

## <a name="next-steps"></a>Nächste Schritte
 Weitere Informationen zum Arbeiten mit zwischengespeicherten Daten finden Sie in den folgenden Themen:

- Ändern der Daten in einem zwischengespeicherten Dataset, ohne Excel zu starten. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Ändern von zwischengespeicherten Daten in einer Arbeitsmappe auf einem Server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).

## <a name="see-also"></a>Weitere Informationen

- [Exemplarische Vorgehensweise: Einfügen von Daten in eine Arbeitsmappe auf einem Server](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
- [Exemplarische Vorgehensweise: Ändern von zwischengespeicherten Daten in einer Arbeitsmappe auf einem Server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
