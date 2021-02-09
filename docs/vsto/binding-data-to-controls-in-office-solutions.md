---
title: Binden von Daten an Steuerelemente in Office-Projektmappen
description: Erfahren Sie, wie Sie Windows Forms Steuerelemente und Host Steuerelemente in einem Microsoft Office Word-Dokument oder Excel-Arbeitsblatt an eine Datenquelle binden können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio], connecting to data
- data, data binding
- data binding
- data binding, Office solutions
- data binding, controls
- Office applications [Office development in Visual Studio], data binding
- controls, data binding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 459c50b5f8135756f85de852a62de44b3878148d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882478"
---
# <a name="bind-data-to-controls-in-office-solutions"></a>Binden von Daten an Steuerelemente in Office-Projektmappen
  Sie können Windows Forms-Steuerelemente und *Hoststeuerelemente* auf einem Microsoft Office Word-Dokument oder einem Microsoft Office Excel-Arbeitsblatt an eine Datenquelle binden, sodass die Steuerelemente die Daten automatisch anzeigen. Sie können Daten sowohl in Projekten auf Anwendungsebene als auch in Projekten auf Dokumentebene an Steuerelemente binden.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Hoststeuerelemente erweitern Objekte in den Word- und Excel-Objektmodellen, beispielsweise Inhaltssteuerelemente in Word und benannte Bereiche in Excel. Weitere Informationen finden Sie unter [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md).

 Sowohl in Windows Forms- als auch in Hoststeuerelementen wird das Windows Forms-Datenbindungsmodell verwendet, das sowohl *einfache Datenbindung* als auch *komplexe Datenbindung* an Datenquellen wie Datasets und Datentabellen unterstützt. Ausführliche Informationen zum Daten Bindungs Modell in Windows Forms finden Sie unter [Datenbindung und Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="simple-data-binding"></a>Einfache Datenbindung
 Eine einfache Datenbindung besteht dann, wenn eine Steuerelementeigenschaft an ein einzelnes Datenelement (z. B. einen Wert in einer Datentabelle) gebunden ist. Zum Beispiel hat das <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement die <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> -Eigenschaft, die an ein Feld in einem Dataset gebunden werden kann. Wenn sich das Feld im Dataset ändert, ändert sich auch der Wert im benannten Bereich. Alle Hoststeuerelemente, mit Ausnahme des <xref:Microsoft.Office.Tools.Word.XMLNodes> -Steuerelements, unterstützen einfache Datenbindung. Das <xref:Microsoft.Office.Tools.Word.XMLNodes> -Steuerelement ist eine Auflistung und unterstützt daher keine Datenbindung.

 Um eine einfache Datenbindung an ein Hoststeuerelement auszuführen, fügen Sie der `DataBindings`-Eigenschaft des Steuerelements ein <xref:System.Windows.Forms.Binding>-Objekt hinzu. Ein <xref:System.Windows.Forms.Binding> -Objekt stellt die einfache Bindung zwischen einem Eigenschaftswert des Steuerelements und dem Wert eines Datenelements dar.

 Im folgenden Beispiel wird veranschaulicht, wie die <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> -Eigenschaft in einem Projekt auf Dokumentebene an ein Datenelement gebunden wird.

 [!code-vb[Trin_BindableComponent#4](../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb#4)]
 [!code-csharp[Trin_BindableComponent#4](../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs#4)]

 Exemplarische Vorgehensweisen, die die einfache Datenbindung veranschaulichen, finden Sie unter Exemplarische Vorgehensweise [: einfache Datenbindung in einem Projekt](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) auf Dokument Ebene für ein Projekt auf Dokument Ebene und Exemplarische Vorgehensweise [: einfache Datenbindung im VSTO-Add-in-Projekt](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) für ein VSTO-Add-in-Projekt.

## <a name="complex-data-binding"></a>Komplexe Datenbindung
 Eine komplexe Datenbindung besteht dann, wenn eine Steuerelementeigenschaft an mindestens zwei Datenelemente (z. B. mehrere Spalten einer Datentabelle) gebunden ist. Das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement für Excel ist das einzige Hoststeuerelement, das komplexe Datenbindung unterstützt. Zudem unterstützen viele Windows Forms-Steuerelemente komplexe Datenbindung, etwa das <xref:System.Windows.Forms.DataGridView> -Steuerelement.

 Um eine komplexe Datenbindung auszuführen, legen Sie die `DataSource`-Eigenschaft des Steuerelements auf ein Datenquellenobjekt fest, das von komplexer Datenbindung unterstützt wird. Beispielsweise kann die <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> -Eigenschaft des <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements an mehrere Spalten einer Datentabelle gebunden werden. Alle Daten in der Datentabelle werden im <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement angezeigt, und wenn sich die Daten in der Datentabelle ändern, ändert sich auch aus <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement. Eine Liste der Datenquellen, die Sie für die komplexe Datenbindung verwenden können, finden Sie [unter von Windows Forms unterstützte Datenquellen](/dotnet/framework/winforms/data-sources-supported-by-windows-forms).

 Im folgenden Codebeispiel wird ein <xref:System.Data.DataSet> mit zwei <xref:System.Data.DataTable> -Objekten erstellt, und eine der Tabellen wird mit Daten aufgefüllt. Im Code wird dann das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement an die Tabelle gebunden, die Daten enthält. Dieses Beispiel gilt für ein Excel-Projekt auf Dokumentebene.

 [!code-csharp[Trin_ExcelListObject#18](../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb#18)]

 Exemplarische Vorgehensweisen für die komplexe Datenbindung finden Sie unter Exemplarische Vorgehensweise [: komplexe Datenbindung in einem Projekt](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) auf Dokument Ebene für ein Projekt auf Dokument Ebene und Exemplarische Vorgehensweise [: komplexe Datenbindung im VSTO-Add-in-Projekt](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) für ein VSTO-Add-in-Projekt.

## <a name="display-data-in-documents-and-workbooks"></a>Anzeigen von Daten in Dokumenten und Arbeitsmappen
 In Projekten auf Dokumentebene können Sie mithilfe des Fensters **Datenquellen** Dokumenten oder Arbeitsmappen datengebundene Steuerelemente auf die gleiche einfache Weise wie für Windows Forms hinzufügen. Weitere Informationen zum Verwenden des **Datenquellen** Fensters finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) und [Hinzufügen neuer Datenquellen](../data-tools/add-new-data-sources.md).

### <a name="drag-controls-from-the-data-sources-window"></a>Ziehen von Steuerelementen aus dem Fenster "Datenquellen"
 Auf einem Dokument wird ein Steuerelement erstellt, wenn Sie aus dem Fenster **Datenquellen** ein Objekt auf das Dokument ziehen. Der Typ des erstellten Steuerelements ist davon abhängig, ob Sie an eine einzelne Datenspalte oder an mehrere Datenspalten binden.

 In Excel werden auf dem Arbeitsblatt ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement für jedes einzelne Feld und für jeden Datenbereich, der mehrere Zeilen und Spalten enthält, ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement erstellt. Sie können diese Standardeinstellung ändern, indem Sie im Fenster **Datenquellen** das Feld oder die Tabelle auswählen und dann in der Dropdownliste ein anderes Steuerelement auswählen.

 Ein <xref:Microsoft.Office.Tools.Word.ContentControl> -Steuerelement wird den Dokumenten hinzugefügt. Der Typ des Inhaltssteuerelements hängt vom Datentyp des von Ihnen ausgewählten Felds ab.

### <a name="bind-data-in-document-level-projects-at-design-time"></a>Binden von Daten in Projekten auf Dokument Ebene zur Entwurfszeit
 In den folgenden Themen werden Beispiele für das Binden von Daten zur Entwurfszeit erläutert:

- [Gewusst wie: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)

- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)

- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)

- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)

- [Gewusst wie: Scrollen durch Datenbankdaten Sätze in einem Arbeitsblatt](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)

### <a name="bind-data-in-vsto-add-in-projects"></a>Binden von Daten in VSTO-Add-in-Projekten
 In VSTO-Add-in-Projekten können Sie Steuerelemente nur zur Laufzeit hinzufügen. In den folgenden Themen werden Beispiele für das Binden von Daten zur Laufzeit erläutert:

- [Exemplarische Vorgehensweise: einfache Datenbindung in einem VSTO-Add-in-Projekt](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)

- [Exemplarische Vorgehensweise: komplexe Datenbindung in einem VSTO-Add-in-Projekt](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)

## <a name="update-data-that-is-bound-to-host-controls"></a>Aktualisieren von Daten, die an Host Steuerelemente gebunden sind
 Eine Datenbindung zwischen einer Datenquelle und einem Hoststeuerelement bedingt eine bidirektionale Datenaktualisierung. Bei einer einfachen Datenbindung werden Änderungen in der Datenquelle automatisch für das Hoststeuerelement übernommen, aber Änderungen im Hoststeuerelement erfordern einen expliziten Aufruf, damit die Datenquelle aktualisiert wird. Dies ist darauf zurückzuführen, dass in einigen Fällen Änderungen in einem datengebundenen Feld nur dann akzeptiert werden, wenn gleichzeitig auch Änderungen in einem anderen datengebundenen Feld vorgenommen werden. Es könnten z. B. zwei Felder vorhanden sein: eines für das Alter und eines für die Jahre an Berufserfahrung. Die Berufserfahrung kann das Alter nicht übersteigen Ein Benutzer kann nur dann das Alter von 50 in 25 und die Berufserfahrung von 30 in 10 ändern, wenn er die Änderungen gleichzeitig vornimmt. Um dieses Problem zu beheben, werden Felder mit einfacher Datenbindung erst aktualisiert, wenn die Aktualisierungen explizit durch Code gesendet wurden.

 Um eine Datenquelle aus Hoststeuerelementen zu aktualisieren, die einfache Datenbindung ermöglichen, müssen Sie Aktualisierungen an die In-Memory-Datenquelle (etwa ein <xref:System.Data.DataSet> oder eine <xref:System.Data.DataTable>) und an die Back-End-Datenbank senden, wenn in Ihrer Projektmappe eine solche verwendet wird.

 Sie müssen die In-Memory-Datenquelle nicht explizit aktualisieren, wenn Sie eine komplexe Datenbindung mit dem <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement ausführen. In diesem Fall werden Änderungen automatisch ohne zusätzlichen Code an die In-Memory-Datenquelle gesendet.

 Weitere Informationen finden Sie unter Gewusst [wie: Aktualisieren einer Datenquelle mit Daten eines Host Steuer](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)Elements.

## <a name="see-also"></a>Weitere Informationen
- [Datenbindung und Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)
- [Gewusst wie: Erstellen eines einfach gebundenen Steuer Elements in einem Windows Form](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)
- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
- [Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Daten zwischenspeichern](../vsto/caching-data.md)
- [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)
