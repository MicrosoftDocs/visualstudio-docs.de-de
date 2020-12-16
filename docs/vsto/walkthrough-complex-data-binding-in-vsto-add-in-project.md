---
title: 'Exemplarische Vorgehensweise: komplexe Datenbindung in einem VSTO-Add-in-Projekt'
description: Erfahren Sie, wie Sie einem Microsoft Excel-Arbeitsblatt Steuerelemente hinzufügen und die Steuerelemente zur Laufzeit an Daten binden.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], Excel
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 573f15001dcbd678c576512349c36ae9594e10e8
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527086"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>Exemplarische Vorgehensweise: komplexe Datenbindung in einem VSTO-Add-in-Projekt
  Sie können in VSTO-Add-In-Projekten Daten an Hoststeuerelemente und Windows Forms-Steuerelemente binden. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie einem Microsoft Office Excel-Arbeitsblatt zur Laufzeit Steuerelemente hinzugefügt und diese Steuerelemente an Daten gebunden werden.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Hinzufügen eines <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements zu einem Arbeitsblatt zur Laufzeit

- Erstellen eines <xref:System.Windows.Forms.BindingSource> -Objekts, das das Steuerelement mit einer Instanz eines Datasets verbindet

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Zugriff auf eine aktive Instanz von SQL Server 2005 oder SQL Server 2005 Express, an die die `AdventureWorksLT` -Beispieldatenbank angefügt ist. Sie können die `AdventureWorksLT` Datenbank aus dem [GitHub-Repository SQL Server Beispiele](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)herunterladen. Weitere Informationen zum Anhängen von Datenbanken finden Sie in den folgenden Themen:

  - Informationen zum Anfügen einer Datenbank mithilfe von SQL Server Management Studio oder SQL Server Management Studio Express finden Sie unter Vorgehens [Weise: Anfügen einer Datenbank (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Informationen zum Anfügen einer Datenbank über die Befehlszeile finden Sie unter Gewusst [wie: Anfügen einer Datenbankdatei an SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Erstellen eines neuen Projekts
 Der erste Schritt besteht im Erstellen eines VSTO-Add-In-Projekts für Excel.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie mit Visual Basic oder C# ein Excel-VSTO-Add-In-Projekt, das den Namen **Füllen von Arbeitsblättern aus einer Datenbank** hat.

     Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet die Datei `ThisAddIn.vb` oder `ThisAddIn.cs` und fügt dem **Projektmappen-Explorer** das Projekt **Füllen von Arbeitsblättern aus einer Datenbank** hinzu.

## <a name="create-a-data-source"></a>Erstellen einer Datenquelle
 Verwenden das Fenster **Datenquellen** , um dem Projekt ein typisiertes Dataset hinzuzufügen.

### <a name="to-add-a-typed-dataset-to-the-project"></a>So fügen Sie dem Projekt ein typisiertes Dataset hinzu

1. Wenn das Fenster **Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie auf der Menüleiste **die Option**  >  **Weitere Windows**-  >  **Datenquellen** anzeigen auswählen.

2. Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

3. Klicken Sie auf **Datenbank**, und klicken Sie dann auf **Weiter**.

4. Wenn eine Verbindung mit der `AdventureWorksLT` -Datenbank vorhanden ist, wählen Sie diese Verbindung aus, und klicken Sie auf **Weiter**.

    Klicken Sie andernfalls auf **Neue Verbindung**, und erstellen Sie die neue Verbindung im Dialogfeld **Verbindung hinzufügen** . Weitere Informationen finden Sie unter [Hinzufügen neuer Verbindungen](../data-tools/add-new-connections.md).

5. Klicken Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** auf **Weiter**.

6. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen** , und wählen Sie **Address (SalesLT)** aus.

7. Klicken Sie auf **Fertig stellen**.

    Die Datei " *AdventureWorksLTDataSet. xsd* " wird **Projektmappen-Explorer** hinzugefügt. In dieser Datei sind die folgenden Elemente definiert:

   - Ein typisiertes Dataset namens `AdventureWorksLTDataSet`. Dieses Dataset entspricht dem Inhalt der **Address (SalesLT)** -Tabelle in der AdventureWorksLT-Datenbank.

   - Ein TableAdapter mit dem Namen `AddressTableAdapter` . Dieser TableAdapter kann verwendet werden, um Daten in zu lesen und zu schreiben `AdventureWorksLTDataSet` . Weitere Informationen finden Sie unter [Übersicht über TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise verwenden Sie beide Objekte.

## <a name="create-controls-and-bind-controls-to-data"></a>Erstellen von Steuerelementen und Binden von Steuerelementen an Daten
 In dieser exemplarischen Vorgehensweise zeigt das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement alle von Ihnen ausgewählten Daten in der Tabelle an, sobald der Benutzer die Arbeitsmappe öffnet. Das Listenobjekt stellt mit einer <xref:System.Windows.Forms.BindingSource> eine Verbindung zwischen Steuerelement und Datenbank her.

 Weitere Informationen zum Binden von Steuerelementen an Daten finden Sie unter [Binden von Daten an Steuerelemente in Office](../vsto/binding-data-to-controls-in-office-solutions.md)-Projektmappen.

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>So fügen Sie das Listenobjekt, das Dataset und den Tabellenadapter hinzu

1. Deklarieren Sie in der `ThisAddIn` -Klasse die folgenden Steuerelemente, um die `Address` -Tabelle des `AdventureWorksLTDataSet` -Datsets anzuzeigen.

     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]

2. Fügen Sie der `ThisAddIn_Startup` -Methode den folgenden Code hinzu, um das Dataset zu initialisieren und es mit Daten aus dem `AdventureWorksLTDataSet` -Dataset zu füllen.

     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]

3. Fügen Sie der `ThisAddIn_Startup` -Methode den folgenden Code hinzu. Dadurch wird ein Hostelement generiert, das das Arbeitsblatt erweitert. Weitere Informationen finden [Sie unter Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]

4. Erstellen Sie einen Bereich und fügen das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement hinzu.

     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]

5. Binden Sie das Listenobjekt mithilfe der `AdventureWorksLTDataSet` an das <xref:System.Windows.Forms.BindingSource>. Übergeben Sie die Namen der Spalten, die an das Listenobjekt gebunden werden sollen.

     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]

## <a name="test-the-add-in"></a>Testen des Add-ins
 Beim Öffnen von Excel zeigt das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement die Daten aus der `Address` -Tabelle des `AdventureWorksLTDataSet` -Datasets .

### <a name="to-test-the-vsto-add-in"></a>So testen Sie das VSTO-Add-In

- Drücken Sie **F5**.

     Im Arbeitsblatt wird ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement namens `addressListObject` erstellt. Gleichzeitig werden dem Projekt ein Datasetobjekt namens `adventureWorksLTDataSet` und ein <xref:System.Windows.Forms.BindingSource> -Objekt namens `addressBindingSource` hinzugefügt. Das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement ist an das <xref:System.Windows.Forms.BindingSource>-Objekt gebunden, das wiederum an das Datasetobjekt gebunden ist.

## <a name="see-also"></a>Weitere Informationen

- [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Gewusst wie: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Gewusst wie: Scrollen durch Datenbankdaten Sätze in einem Arbeitsblatt](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Host Steuer Elements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Exemplarische Vorgehensweise: einfache Datenbindung in einem Projekt auf Dokument Ebene](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Exemplarische Vorgehensweise: komplexe Datenbindung in einem Projekt auf Dokument Ebene](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Verwenden lokaler Datenbankdateien in der Übersicht über Office-Lösungen](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Hinzufügen neuer Datenquellen](../data-tools/add-new-data-sources.md)
- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Verwenden lokaler Datenbankdateien in der Übersicht über Office-Lösungen](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Übersicht über die BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component-overview)
