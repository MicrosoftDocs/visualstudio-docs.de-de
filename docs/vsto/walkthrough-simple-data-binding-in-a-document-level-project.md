---
title: 'Exemplarische Vorgehensweise: einfache Datenbindung in einem Projekt auf Dokument Ebene'
description: Erlernen Sie die Grundlagen der Datenbindung in einem Projekt auf Dokument Ebene, und dass ein einzelnes Datenfeld in einer SQL Server-Datenbank an einen benannten Bereich in Microsoft Excel gebunden ist.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 868a120baa8207d922d3dee55e10c8e903381e19
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524095"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Exemplarische Vorgehensweise: einfache Datenbindung in einem Projekt auf Dokument Ebene
  In dieser exemplarischen Vorgehensweise werden die Grundlagen der Datenbindung in einem Projekt auf Dokument Ebene veranschaulicht. Ein einzelnes Datenfeld in einer SQL Server Datenbank wird in Microsoft Office Excel an einen benannten Bereich gebunden. Die exemplarische Vorgehensweise zeigt auch, wie Sie Steuerelemente hinzufügen, mit denen Sie durch alle Datensätze in der Tabelle scrollen können.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen einer Datenquelle für ein Excel-Projekt.

- Hinzufügen von Steuerelementen zu einem Arbeitsblatt

- Scrollen Sie durch Datenbankdaten Sätze.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Zugriff auf einen Server mit der Beispieldatenbank Northwind SQL Server.

- Lese-und Schreibberechtigungen für die SQL Server Datenbank.

## <a name="create-a-new-project"></a>Erstellen eines neuen Projekts
 In diesem Schritt erstellen Sie ein Excel-Arbeitsmappenprojekt.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **meine Simple-Datenbindung**, indem Sie entweder Visual Basic oder c# verwenden. Stellen Sie sicher, dass **ein neues Dokument erstellen** ausgewählt ist. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt das **eigene einfache Daten Bindungs** Projekt **Projektmappen-Explorer** hinzu.

## <a name="create-the-data-source"></a>Erstellen der Datenquelle
 Verwenden das Fenster **Datenquellen** , um dem Projekt ein typisiertes Dataset hinzuzufügen.

### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle

1. Wenn das Fenster **Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie auf der Menüleiste **die Option**  >  **Weitere Windows**-  >  **Datenquellen** anzeigen auswählen.

2. Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

3. Wählen Sie **Datenbank** aus, und klicken Sie dann auf **weiter**.

4. Wählen Sie eine Datenverbindung mit der Beispieldatenbank Northwind SQL Server aus, oder fügen Sie mithilfe der Schaltfläche **neue Verbindung** eine neue Verbindung hinzu.

5. Nachdem eine Verbindung ausgewählt oder erstellt wurde, klicken Sie auf **weiter**.

6. Deaktivieren Sie die Option zum Speichern der Verbindung, wenn Sie ausgewählt ist, und klicken Sie dann auf **weiter**.

7. Erweitern Sie den Knoten **Tabellen** im Fenster **Datenbankobjekte** .

8. Aktivieren Sie das Kontrollkästchen neben der Tabelle **Customers** .

9. Klicken Sie auf **Fertig stellen**.

   Der Assistent fügt dem **Datenquellen** Fenster die **Customers** -Tabelle hinzu. Außerdem wird ein typisiertes DataSet zu Ihrem Projekt hinzugefügt, das in **Projektmappen-Explorer** sichtbar ist.

## <a name="add-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt
 In dieser exemplarischen Vorgehensweise benötigen Sie zwei benannte Bereiche und vier Schaltflächen auf dem ersten Arbeitsblatt. Fügen Sie zunächst die beiden benannten Bereiche aus dem Fenster **Datenquellen** hinzu, damit Sie automatisch an die Datenquelle gebunden werden. Fügen Sie als nächstes die Schaltflächen aus der **Toolbox** hinzu.

### <a name="to-add-two-named-ranges"></a>So fügen Sie zwei benannte Bereiche hinzu

1. Vergewissern Sie sich, dass die Arbeitsmappe *meine Simple Data Binding.xlsx* -Arbeitsmappe im Visual Studio-Designer geöffnet ist, wobei **Sheet1** angezeigt wird.

2. Öffnen Sie das Fenster **Datenquellen** , und erweitern Sie den Knoten **Customers** .

3. Wählen Sie die Spalte **CompanyName** aus, und klicken Sie dann auf den angezeigten Dropdown Pfeil.

4. Wählen Sie in der Dropdown Liste **Name Drange** aus, und ziehen Sie dann die Spalte **CompanyName** in die Zelle **a1**.

     <xref:Microsoft.Office.Tools.Excel.NamedRange> `companyNameNamedRange` In Zelle **a1** wird ein-Steuerelement mit dem Namen erstellt. Gleichzeitig <xref:System.Windows.Forms.BindingSource> werden dem Projekt ein benannter `customersBindingSource` , ein Tabellen Adapter und eine- <xref:System.Data.DataSet> Instanz hinzugefügt. Das-Steuerelement ist an das-Steuerelement gebunden <xref:System.Windows.Forms.BindingSource> , das wiederum an die-Instanz gebunden ist <xref:System.Data.DataSet> .

5. Wählen Sie im Fenster **Datenquellen** die Spalte **CustomerID** aus, und klicken Sie dann auf den angezeigten Dropdown Pfeil.

6. Klicken Sie in der Dropdown Liste auf **NamedRange** , und ziehen Sie dann die Spalte **CustomerID** in Zelle **B1**.

7. Ein weiteres <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement `customerIDNamedRange` mit dem Namen wird in Zelle **B1** erstellt und an gebunden <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-four-buttons"></a>So fügen Sie vier Schaltflächen hinzu

1. Fügen Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** ein- <xref:System.Windows.Forms.Button> Steuerelement zu Zelle **a3** des Arbeitsblatts hinzu.

    Diese Schaltfläche hat den Namen `Button1` .

2. Fügen Sie den folgenden Zellen in dieser Reihenfolge drei weitere Schaltflächen hinzu, sodass die Namen wie folgt angezeigt werden:

   |Cell (Zelle)|(Name)|
   |----------|--------------|
   |B3|Button2|
   |C3|Button3|
   |D3|Button4|

   Der nächste Schritt besteht im Hinzufügen von Text zu den Schaltflächen und in c# Hinzufügen von Ereignis Handlern.

## <a name="initialize-the-controls"></a>Initialisieren der Steuerelemente
 Legen Sie den Schaltflächen Text fest, und fügen Sie während des Ereignisses Ereignishandler hinzu <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> .

### <a name="to-initialize-the-controls"></a>So initialisieren Sie die Steuerelemente

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **Sheet1. vb** oder **Sheet1.cs**, und klicken Sie dann im Kontextmenü auf **Code anzeigen** .

2. Fügen Sie der-Methode den folgenden Code hinzu `Sheet1_Startup` , um den Text für jede Schaltfläche festzulegen.

    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]

3. Fügen Sie der-Methode nur für c# Ereignishandler für die Click-Ereignisse der Schaltfläche hinzu `Sheet1_Startup` .

    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]

   Fügen Sie nun Code hinzu, mit dem die <xref:System.Windows.Forms.Control.Click> Ereignisse der Schaltflächen behandelt werden, damit der Benutzer die Datensätze durchsuchen kann.

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Fügen Sie Code hinzu, um das Scrollen durch die Datensätze
 Fügen Sie dem- <xref:System.Windows.Forms.Control.Click> Ereignishandler für jede Schaltfläche Code hinzu, um durch die Datensätze zu navigieren.

### <a name="to-move-to-the-first-record"></a>So wechseln Sie zum ersten Datensatz

1. Fügen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click> -Ereignis der `Button1` Schaltfläche hinzu, und fügen Sie den folgenden Code hinzu, um zum ersten Datensatz zu wechseln:

     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]

### <a name="to-move-to-the-previous-record"></a>So wechseln Sie zum vorherigen Datensatz

1. Fügen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click> -Ereignis der `Button2` Schaltfläche hinzu, und fügen Sie den folgenden Code hinzu, um die Position wieder um eins zu verschieben:

     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]

### <a name="to-move-to-the-next-record"></a>So wechseln Sie zum nächsten Datensatz

1. Fügen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click> -Ereignis der `Button3` Schaltfläche hinzu, und fügen Sie den folgenden Code hinzu, um die Position um eins fortzusetzen:

     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]

### <a name="to-move-to-the-last-record"></a>So wechseln Sie zum letzten Datensatz

1. Fügen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click> -Ereignis der `Button4` Schaltfläche hinzu, und fügen Sie den folgenden Code hinzu, um zum letzten Datensatz zu wechseln:

     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]

## <a name="test-the-application"></a>Testen der Anwendung
 Nun können Sie die Arbeitsmappe testen, um sicherzustellen, dass Sie die Datensätze in der Datenbank durchsuchen können.

### <a name="to-test-your-workbook"></a>So testen Sie die Arbeitsmappe

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Vergewissern Sie sich, dass der erste Datensatz in den Zellen **a1** und **B1** angezeigt wird.

3. Klicken Sie auf die **>** `Button3` Schaltfläche (), und vergewissern Sie sich, dass der nächste Datensatz in Zelle **a1** und **B1** erscheint.

4. Klicken Sie auf die anderen Bild Lauf Schaltflächen, um zu bestätigen, dass der Datensatz erwartungsgemäß

## <a name="next-steps"></a>Nächste Schritte
 Diese exemplarische Vorgehensweise zeigt die Grundlagen der Bindung eines benannten Bereichs an ein Feld in einer Datenbank. Die folgenden Aufgaben könnten sich daran anschließen:

- Zwischenspeichern der Daten, sodass Sie offline verwendet werden können. Weitere Informationen finden Sie unter Gewusst [wie: Zwischenspeichern von Daten zur Offline Verwendung oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Binden Sie Zellen an mehrere Spalten in einer Tabelle statt an ein Feld. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: komplexe Datenbindung in einem Projekt auf Dokument Ebene](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).

- Mit einem-Steuerelement können <xref:System.Windows.Forms.BindingNavigator> Sie durch die Datensätze scrollen. Weitere Informationen finden Sie unter Gewusst [wie: Navigieren in Daten mit dem Windows Forms BindingNavigator-Steuer](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms)Element.

## <a name="see-also"></a>Weitere Informationen
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)
- [Exemplarische Vorgehensweise: komplexe Datenbindung in einem Projekt auf Dokument Ebene](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
