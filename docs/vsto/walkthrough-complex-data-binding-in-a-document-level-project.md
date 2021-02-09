---
title: 'Exemplarische Vorgehensweise: komplexe Datenbindung in einem Projekt auf Dokument Ebene'
description: Erfahren Sie, wie Sie mehrere Zellen in einem Microsoft Excel-Arbeitsblatt an Felder in der Northwind-SQL Server Datenbank binden können.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2dc5708da09074c7d973336958c9e89c16bf9da6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927664"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Exemplarische Vorgehensweise: komplexe Datenbindung in einem Projekt auf Dokument Ebene
  In dieser exemplarischen Vorgehensweise werden die Grundlagen der komplexen Datenbindung in einem Projekt auf Dokument Ebene veranschaulicht. Sie können mehrere Zellen in einem Microsoft Office Excel-Arbeitsblatt an Felder in der Northwind-SQL Server Datenbank binden.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Hinzufügen einer Datenquelle zum Arbeitsmappenprojekt.

- Hinzufügen von Daten gebundenen Steuerelementen zu einem Arbeitsblatt.

- Datenänderungen werden wieder in der Datenbank gespeichert.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Zugriff auf einen Server mit der Beispieldatenbank Northwind SQL Server.

- Lese-und Schreibberechtigungen für die SQL Server Datenbank.

## <a name="create-a-new-project"></a>Erstellen eines neuen Projekts
 Der erste Schritt besteht darin, ein Excel-Arbeitsmappenprojekt zu erstellen.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **meine komplexe Datenbindung**. Wählen Sie im Assistenten **Neues Dokument erstellen** aus.

     Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt **Projektmappen-Explorer** ein Projekt mit der **komplexen Datenbindung** hinzu.

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

8. Aktivieren Sie das Kontrollkästchen neben der Tabelle **Employees** .

9. Klicken Sie auf **Fertig stellen**.

   Der Assistent fügt dem **Datenquellen** Fenster die Tabelle **Employees** hinzu. Außerdem wird ein typisiertes DataSet zu Ihrem Projekt hinzugefügt, das in **Projektmappen-Explorer** sichtbar ist.

## <a name="add-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt
 Beim Öffnen der Arbeitsmappe wird in einem Arbeitsblatt die Tabelle **Employees** angezeigt. Benutzer können Änderungen an den Daten vornehmen und diese Änderungen dann wieder in der Datenbank speichern, indem Sie auf eine Schaltfläche klicken.

 Um das Arbeitsblatt automatisch an die Tabelle zu binden, können Sie dem <xref:Microsoft.Office.Tools.Excel.ListObject> Arbeitsblatt ein-Steuerelement aus dem Fenster **Datenquellen** hinzufügen. Um dem Benutzer die Möglichkeit zu geben, Änderungen zu speichern, fügen Sie ein- <xref:System.Windows.Forms.Button> Steuerelement aus der **Toolbox** hinzu.

#### <a name="to-add-a-list-object"></a>So fügen Sie ein Listen Objekt hinzu

1. Vergewissern Sie sich, dass die Arbeitsmappe **meine komplexen Daten Binding.xlsx** im Visual Studio-Designer geöffnet ist, wobei **Sheet1** angezeigt wird.

2. Öffnen Sie das Fenster **Datenquellen** , und wählen Sie den Knoten **Employees** aus.

3. Klicken Sie auf den angezeigten Dropdown Pfeil.

4. Wählen Sie in der Dropdown Liste **ListObject** aus.

5. Ziehen Sie die **Employees** -Tabelle in die Zelle **a6**.

     <xref:Microsoft.Office.Tools.Excel.ListObject> `EmployeesListObject` In der Zelle **a6** wird ein Steuerelement mit dem Namen erstellt. Gleichzeitig <xref:System.Windows.Forms.BindingSource> werden dem Projekt ein benannter `EmployeesBindingSource` , ein Tabellen Adapter und eine- <xref:System.Data.DataSet> Instanz hinzugefügt. Das-Steuerelement ist an das-Steuerelement gebunden <xref:System.Windows.Forms.BindingSource> , das wiederum an die-Instanz gebunden ist <xref:System.Data.DataSet> .

### <a name="to-add-a-button"></a>So fügen Sie eine Schaltfläche hinzu

1. Fügen Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** ein- <xref:System.Windows.Forms.Button> Steuerelement zur Zelle **a4** des Arbeitsblatts hinzu.

   Der nächste Schritt besteht darin, der Schaltfläche Text hinzuzufügen, wenn das Arbeitsblatt geöffnet wird.

## <a name="initialize-the-control"></a>Initialisieren des Steuer Elements
 Fügen Sie der Schaltfläche im- <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Ereignishandler Text hinzu.

### <a name="to-initialize-the-control"></a>So initialisieren Sie das Steuerelement

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **Sheet1. vb** oder **Sheet1.cs**, und klicken Sie dann im Kontextmenü auf **Code anzeigen** .

2. Fügen Sie der-Methode den folgenden Code hinzu `Sheet1_Startup` , um den Text für die b-Methode festzulegen `utton` .

    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]

3. Fügen Sie der-Methode für nur c# einen Ereignishandler für das- <xref:System.Windows.Forms.Control.Click> Ereignis hinzu `Sheet1_Startup` .

    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]

   Fügen Sie nun Code hinzu, um das- <xref:System.Windows.Forms.Control.Click> Ereignis der Schaltfläche zu behandeln.

## <a name="save-changes-to-the-database"></a>Änderungen an der Datenbank speichern
 Alle Änderungen, die an den Daten vorgenommen wurden, sind nur im lokalen DataSet vorhanden, bis Sie explizit wieder in der Datenbank gespeichert werden.

### <a name="to-save-changes-to-the-database"></a>So speichern Sie Änderungen an der Datenbank

1. Fügen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click> -Ereignis von hinzu `button` , und fügen Sie den folgenden Code hinzu, um einen Commit für alle im DataSet vorgenommenen Änderungen an der Datenbank vorzunehmen.

     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]

## <a name="test-the-application"></a>Testen der Anwendung
 Nun können Sie die Arbeitsmappe testen, um zu überprüfen, ob die Daten erwartungsgemäß angezeigt werden, und Sie können die Daten im Listen Objekt bearbeiten.

### <a name="to-test-the-data-binding"></a>So testen Sie die Datenbindung

- Drücken Sie **F5**.

     Überprüfen Sie, ob das Listen Objekt beim Öffnen der Arbeitsmappe mit Daten aus der Tabelle **Employees** ausgefüllt ist.

### <a name="to-modify-data"></a>So ändern Sie Daten

1. Klicken Sie auf Zelle **B7**, die den Namen **Davolio** enthalten soll.

2. Geben Sie den Namen **Anderson** ein, und drücken Sie dann die **Eingabe** Taste.

### <a name="to-modify-a-column-header"></a>So ändern Sie einen Spaltenheader

1. Klicken Sie auf die Zelle, die den Spaltenheader **LastName** enthält.

2. Geben Sie **Nachname** ein, einschließlich eines leer Zeichens zwischen den beiden Wörtern, und drücken Sie dann die **Eingabe** Taste.

### <a name="to-save-data"></a>So speichern Sie Daten

1. Klicken Sie im Arbeitsblatt auf **Speichern** .

2. Beenden Sie Excel. Klicken Sie auf **Nein** , wenn Sie zum Speichern der vorgenommenen Änderungen aufgefordert werden.

3. Drücken Sie **F5** , um das Projekt erneut auszuführen.

     Das Listen Objekt wird mit Daten aus der **Employees** -Tabelle aufgefüllt.

4. Beachten Sie, dass der Name in Zelle **B7** immer noch **Anderson** ist, d. h. die Datenänderung, die Sie vorgenommen und wieder in der Datenbank gespeichert haben. Die Spaltenüberschrift " **LastName** " wurde wieder in die ursprüngliche Form ohne Leerzeichen geändert, da die Spaltenüberschrift nicht an die Datenbank gebunden ist und Sie die an dem Arbeitsblatt vorgenommenen Änderungen nicht gespeichert haben.

### <a name="to-add-new-rows"></a>So fügen Sie neue Zeilen hinzu

1. Wählen Sie eine Zelle innerhalb des Listen Objekts aus.

    Am Ende der Liste wird eine neue Zeile mit einem Sternchen ( **\*** ) in der ersten Zelle der neuen Zeile angezeigt.

2. Fügen Sie die folgenden Informationen in die leere Zeile ein.

   |EmployeeID|LastName|FirstName|Titel|
   |----------------|--------------|---------------|-----------|
   |10|Ito|Shu|Sales Manager|

### <a name="to-delete-rows"></a>Löschen von Zeilen

- Klicken Sie mit der rechten Maustaste auf die Zahl 16 (Zeile 16) auf der linken Seite des Arbeitsblatts, und klicken Sie dann auf **Löschen**.

### <a name="to-sort-the-rows-in-the-list"></a>So sortieren Sie die Zeilen in der Liste

1. Wählen Sie eine Zelle in der Liste aus.

     In jedem Spaltenheader werden Pfeil Schaltflächen angezeigt.

2. Klicken Sie in der Spaltenüberschrift **Last Name** auf die Pfeil Schaltfläche.

3. Klicken Sie auf **Aufsteigend sortieren**.

     Die Zeilen werden alphabetisch nach Nachnamen sortiert.

### <a name="to-filter-information"></a>So filtern Sie Informationen

1. Wählen Sie eine Zelle in der Liste aus.

2. Klicken Sie in der **Titel** Spalten Kopfzeile auf die Pfeil Schaltfläche.

3. Klicken Sie auf **Vertriebsmitarbeiter**.

     In der Liste werden nur die Zeilen angezeigt, die in der Spalte **Titel** über einen **Vertriebsmitarbeiter** verfügen.

4. Klicken Sie erneut auf die Pfeil Schaltfläche im **Titel** Spaltenheader.

5. Klicken Sie auf **(alle)**.

     Das Filtern wird entfernt, und alle Zeilen werden angezeigt.

## <a name="next-steps"></a>Nächste Schritte
 Diese exemplarische Vorgehensweise zeigt die Grundlagen der Bindung einer Tabelle in einer Datenbank an ein Listen Objekt. Die folgenden Aufgaben könnten sich daran anschließen:

- Zwischenspeichern der Daten, sodass Sie offline verwendet werden können. Weitere Informationen finden Sie unter Gewusst [wie: Zwischenspeichern von Daten zur Offline Verwendung oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Bereitstellen der Projektmappe Weitere Informationen finden Sie unter Bereitstellen [einer Office](../vsto/deploying-an-office-solution.md)-Projekt Mappe.

- Erstellen Sie eine Master/Detail-Beziehung zwischen einem Feld und einer Tabelle. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer Master Detail Beziehung mithilfe eines zwischengespeicherten Datasets](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).

## <a name="see-also"></a>Weitere Informationen
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)
- [Exemplarische Vorgehensweise: einfache Datenbindung in einem Projekt auf Dokument Ebene](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
