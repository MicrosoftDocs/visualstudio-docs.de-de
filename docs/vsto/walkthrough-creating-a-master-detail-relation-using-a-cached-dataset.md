---
title: Erstellen einer Master Detail Beziehung mithilfe eines zwischengespeicherten Datasets
description: Erfahren Sie mehr über das Erstellen einer Master/Detail-Beziehung auf einem Arbeitsblatt und das Zwischenspeichern der Daten, damit die Projekt Mappe offline verwendet werden kann.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: de7bf3ba34a2a7dd3e7db9ff549e4a839800d524
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524865"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>Exemplarische Vorgehensweise: Erstellen einer Master Detail Beziehung mithilfe eines zwischengespeicherten Datasets
  Diese exemplarische Vorgehensweise veranschaulicht das Erstellen einer Master/Detail-Beziehung auf einem Arbeitsblatt und das Zwischenspeichern der Daten, damit die Projekt Mappe offline verwendet werden kann.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

- Fügen Sie einem Arbeitsblatt Steuerelemente hinzu.

- Richten Sie ein Dataset ein, das in einem Arbeitsblatt zwischengespeichert werden soll.

- Fügen Sie Code hinzu, um das Scrollen durch die Datensätze zu ermöglichen

- Testen Sie das Projekt.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Zugriff auf die Beispieldatenbank Northwind SQL Server. Die-Datenbank kann sich auf dem Entwicklungs Computer oder auf einem-Server befinden.

- Lese-und Schreibberechtigungen für die SQL Server Datenbank.

## <a name="create-a-new-project"></a>Erstellen eines neuen Projekts
 In diesem Schritt erstellen Sie ein Excel-Arbeitsmappenprojekt.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen " **My Master-Detail**", indem Sie entweder Visual Basic oder c# verwenden. Stellen Sie sicher, dass **ein neues Dokument erstellen** ausgewählt ist. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt das **eigene Master/Detail-** Projekt **Projektmappen-Explorer** hinzu.

## <a name="create-the-data-source"></a>Erstellen der Datenquelle
 Verwenden das Fenster **Datenquellen** , um dem Projekt ein typisiertes Dataset hinzuzufügen.

### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle

1. Wenn das Fenster **Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie auf der Menüleiste **die Option**  >  **Weitere Windows**-  >  **Datenquellen** anzeigen auswählen.

2. Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

3. Wählen Sie **Datenbank** aus, und klicken Sie dann auf **weiter**.

4. Wählen Sie eine Datenverbindung mit der Beispieldatenbank Northwind SQL Server aus, oder fügen Sie mithilfe der Schaltfläche **neue Verbindung** eine neue Verbindung hinzu.

5. Nachdem Sie eine Verbindung ausgewählt oder erstellt haben, klicken Sie auf **weiter**.

6. Deaktivieren Sie die Option zum Speichern der Verbindung, wenn Sie ausgewählt ist, und klicken Sie dann auf **weiter**.

7. Erweitern Sie den Knoten **Tabellen** im Fenster **Datenbankobjekte** .

8. Wählen Sie die Tabelle **Orders** und die Tabelle **Order Details** aus.

9. Klicken Sie auf **Fertig stellen**.

   Der Assistent fügt die beiden Tabellen zum Fenster **Datenquellen** hinzu. Außerdem wird ein typisiertes DataSet zu Ihrem Projekt hinzugefügt, das in **Projektmappen-Explorer** sichtbar ist.

## <a name="add-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt
 In diesem Schritt fügen Sie dem ersten Arbeitsblatt einen benannten Bereich, ein Listen Objekt und zwei Schaltflächen hinzu. Fügen Sie zunächst den benannten Bereich und das Listen Objekt aus dem Fenster **Datenquellen** hinzu, damit Sie automatisch an die Datenquelle gebunden werden. Fügen Sie als nächstes die Schaltflächen aus der **Toolbox** hinzu.

### <a name="to-add-a-named-range-and-a-list-object"></a>So fügen Sie einen benannten Bereich und ein Listen Objekt hinzu

1. Vergewissern Sie sich, dass die Arbeitsmappe **meine Master-Detail.xlsx** im Visual Studio-Designer geöffnet ist, wobei **Sheet1** angezeigt wird.

2. Öffnen Sie das Fenster **Datenquellen** , und erweitern Sie den Knoten **Orders** .

3. Wählen Sie die Spalte **OrderID** aus, und klicken Sie dann auf den angezeigten Dropdown Pfeil.

4. Klicken Sie in der Dropdown Liste auf **NamedRange** , und ziehen Sie dann die Spalte **OrderID** in Zelle **a2**.

     <xref:Microsoft.Office.Tools.Excel.NamedRange> `OrderIDNamedRange` In Zelle **a2** wird ein Steuerelement mit dem Namen erstellt. Gleichzeitig <xref:System.Windows.Forms.BindingSource> werden dem Projekt ein benannter `OrdersBindingSource` , ein Tabellen Adapter und eine- <xref:System.Data.DataSet> Instanz hinzugefügt. Das-Steuerelement ist an das-Steuerelement gebunden <xref:System.Windows.Forms.BindingSource> , das wiederum an die-Instanz gebunden ist <xref:System.Data.DataSet> .

5. Scrollen Sie nach unten zu den Spalten, die sich in der Tabelle **Orders** befinden. Am unteren Rand der Liste befindet sich die Tabelle **Order Details** . Dies liegt daran, dass es sich um ein untergeordnetes Element der **Orders** -Tabelle handelt. Wählen Sie diese **Order Details** -Tabelle aus, nicht die, die sich auf derselben Ebene wie die **Orders** -Tabelle befindet, und klicken Sie dann auf den angezeigten Dropdown Pfeil.

6. Klicken Sie in der Dropdown Liste auf **ListObject** , und ziehen Sie dann die Tabelle **Order Details** in die Zelle **a6**.

7. Ein <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement mit dem Namen **Order_DetailsListObject** wird in der Zelle **a6** erstellt und an gebunden <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-two-buttons"></a>So fügen Sie zwei Schaltflächen hinzu

1. Fügen Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** ein- <xref:System.Windows.Forms.Button> Steuerelement zu Zelle **a3** des Arbeitsblatts hinzu.

    Diese Schaltfläche hat den Namen `Button1` .

2. Fügen Sie der <xref:System.Windows.Forms.Button> Zelle **B3** des Arbeitsblatts ein weiteres Steuerelement hinzu.

    Diese Schaltfläche hat den Namen `Button2` .

   Markieren Sie als nächstes das DataSet, das im Dokument zwischengespeichert werden soll.

## <a name="cache-the-dataset"></a>Zwischenspeichern des Datasets
 Markieren Sie das DataSet, das im Dokument zwischengespeichert werden soll, indem Sie das DataSet öffentlich gestalten und die **CacheInDocument** -Eigenschaft festlegen.

### <a name="to-cache-the-dataset"></a>So speichern Sie das Dataset zwischen

1. Wählen Sie in der Komponenten Leiste **NorthwindDataSet** aus.

2. Ändern Sie im Fenster **Eigenschaften** die **modifizierereigenschaft** in **Public**.

    Datasets müssen öffentlich sein, bevor das Caching aktiviert wird.

3. Ändern Sie die **CacheInDocument** -Eigenschaft in **true**.

   Der nächste Schritt besteht darin, den Schaltflächen Text hinzuzufügen und in c# Code hinzufügen, um die Ereignishandler zu verbinden.

## <a name="initialize-the-controls"></a>Initialisieren der Steuerelemente
 Legen Sie den Schaltflächen Text fest, und fügen Sie während des Ereignisses Ereignishandler hinzu <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> .

### <a name="to-initialize-the-data-and-the-controls"></a>So initialisieren Sie die Daten und Steuerelemente

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **Sheet1. vb** oder **Sheet1.cs**, und klicken Sie dann im Kontextmenü auf **Code anzeigen** .

2. Fügen Sie der-Methode den folgenden Code hinzu `Sheet1_Startup` , um den Text für die Schaltflächen festzulegen.

     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]

3. Fügen Sie der-Methode nur für c# Ereignishandler für die Click-Ereignisse der Schaltfläche hinzu `Sheet1_Startup` .

     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Fügen Sie Code hinzu, um das Scrollen durch die Datensätze
 Fügen Sie dem- <xref:System.Windows.Forms.Control.Click> Ereignishandler für jede Schaltfläche Code hinzu, um durch die Datensätze zu navigieren.

### <a name="to-scroll-through-the-records"></a>So führen Sie einen Bildlauf durch die Datensätze durch

1. Fügen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click> -Ereignis von hinzu `Button1` , und fügen Sie den folgenden Code hinzu, um durch die Datensätze rückwärts zu wechseln:

     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]

2. Fügen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click> -Ereignis von hinzu `Button2` , und fügen Sie den folgenden Code hinzu, um die Datensätze zu durchlaufen:

     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]

## <a name="test-the-application"></a>Testen der Anwendung
 Nun können Sie die Arbeitsmappe testen, um sicherzustellen, dass die Daten erwartungsgemäß angezeigt werden, und dass Sie die Lösung offline verwenden können.

### <a name="to-test-the-data-caching"></a>So testen Sie das Zwischenspeichern von Daten

1. Drücken Sie **F5**.

2. Überprüfen Sie, ob der benannte Bereich und das List-Objekt mit Daten aus der Datenquelle gefüllt sind.

3. Scrollen Sie durch einige der Datensätze, indem Sie auf die Schaltflächen klicken.

4. Speichern Sie die Arbeitsmappe, und schließen Sie dann die Arbeitsmappe und Visual Studio.

5. Deaktivieren Sie die Verbindung mit der Datenbank. Entfernen Sie das Netzwerkkabel von Ihrem Computer, wenn sich die Datenbank auf einem Server befindet, oder schließen Sie den SQL Server-Dienst, wenn sich die Datenbank auf dem Entwicklungs Computer befindet.

6. Öffnen Sie Excel, und öffnen Sie dann **meine Master-Detail.xlsx** aus dem Verzeichnis " *\bin* " ("*\My Master-Detail\bin* " in Visual Basic oder " *\My Master-Detail\bin\debug* in c#").

7. Scrollen Sie durch einige der Datensätze, um zu sehen, dass das Arbeitsblatt bei der Trennung normal funktioniert.

8. Stellen Sie erneut eine Verbindung mit der Datenbank her. Verbinden Sie den Computer erneut mit dem Netzwerk, wenn sich die Datenbank auf einem Server befindet, oder starten Sie den SQL Server-Dienst, wenn sich die Datenbank auf dem Entwicklungs Computer befindet.

## <a name="next-steps"></a>Nächste Schritte
 Diese exemplarische Vorgehensweise zeigt die Grundlagen der Erstellung einer Master/Detail-Daten Beziehung auf einem Arbeitsblatt und Zwischenspeichern eines Datasets. Die folgenden Aufgaben könnten sich daran anschließen:

- Bereitstellen der Projektmappe Weitere Informationen finden Sie unter Bereitstellen [einer Office](../vsto/deploying-an-office-solution.md) -Projekt Mappe.

## <a name="see-also"></a>Weitere Informationen
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)
- [Daten zwischenspeichern](../vsto/caching-data.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
