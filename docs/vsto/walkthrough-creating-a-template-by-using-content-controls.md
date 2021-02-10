---
title: 'Exemplarische Vorgehensweise: Erstellen einer Vorlage mithilfe von Inhalts Steuerelementen'
description: Erfahren Sie, wie Sie eine Anpassung auf Dokument Ebene erstellen, die Inhalts Steuerelemente verwendet, um strukturierte und wiederverwendbare Inhalte in einer Microsoft Word-Vorlage zu erstellen.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4bd636070a8375b6761cb2d3ab62d08be4302db4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937497"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>Exemplarische Vorgehensweise: Erstellen einer Vorlage mithilfe von Inhalts Steuerelementen
  Diese exemplarische Vorgehensweise veranschaulicht, wie eine Anpassung auf Dokumentebene erstellt wird, die Inhaltssteuerelemente zum Erstellen strukturierter und wiederverwendbarer Inhalte in einer Microsoft Office Word-Vorlage verwendet.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Mit Word können Sie eine Auflistung wiederverwendbarer Dokument Teile erstellen, die als *Bausteine* bezeichnet werden. Diese exemplarische Vorgehensweise veranschaulicht, wie zwei Tabellen als Bausteine erstellt werden. Jede Tabelle enthält mehrere Inhaltssteuerelemente, die unterschiedliche Inhaltstypen aufweisen können, z. B. reinen Text oder Datumsangaben. Eine der Tabellen enthält Informationen über einen Mitarbeiter und die andere Kundenfeedback.

 Nachdem Sie ein Dokument von der Vorlage erstellt haben, können Sie ihm mithilfe mehrerer <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>-Objekte, die die verfügbaren Bausteine in der Vorlage anzeigen, eine der beiden Tabellen hinzufügen.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen von Tabellen, die Inhaltssteuerelemente in einer Word-Vorlage enthalten, zur Entwurfszeit

- Programmgesteuertes Auffüllen eines Kombinationsfeld-Inhaltssteuerelements und eines Dropdownlisten-Inhaltssteuerelements

- Verhindern, dass Benutzer eine bestimmte Tabelle bearbeiten

- Hinzufügen von Tabellen zur Bausteinauflistung einer Vorlage

- Erstellen eines Inhaltssteuerelements, das die verfügbaren Bausteine in der Vorlage anzeigt

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-template-project"></a>Erstellen eines neuen Word-Vorlagen Projekts
 Erstellen Sie eine Word-Vorlage, damit Benutzer leicht eigene Kopien erstellen können.

### <a name="to-create-a-new-word-template-project"></a>So erstellen Sie ein neues Word-Vorlagenprojekt

1. Erstellen Sie ein Word-Vorlagen Projekt mit dem Namen **MyBuildingBlockTemplate**. Erstellen Sie im Assistenten ein neues Dokument in der Projektmappe. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Öffnet die neue Word-Vorlage im Designer und fügt **Projektmappen-Explorer** das Projekt **MyBuildingBlockTemplate** hinzu.

## <a name="create-the-employee-table"></a>Erstellen der Employee-Tabelle
 Erstellen Sie eine Tabelle, die vier verschiedene Typen von Inhaltssteuerelementen enthält, in denen der Benutzer Informationen zu einem Mitarbeiter eingeben kann.

### <a name="to-create-the-employee-table"></a>So erstellen Sie die Mitarbeitertabelle

1. Klicken Sie in der im Designer gehosteten Word-Vorlage [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] auf dem Menüband auf die Registerkarte **Einfügen** .

2. Klicken Sie in der Gruppe **Tabellen** auf **Tabelle**, und fügen Sie eine Tabelle mit zwei Spalten und vier Zeilen ein.

3. Geben Sie in der ersten Spalte Text ein, sodass sie der folgenden Spalte ähnelt:

   ||
   |-|
   |**Employee Name**|
   |**Hire Date**|
   |**Titel**|
   |**Picture**|

4. Klicken Sie in die erste Zelle in der zweiten Spalte (neben **Employee Name**).

5. Klicken Sie im Menüband auf die Registerkarte **Entwickler** .

   > [!NOTE]
   > Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter Gewusst [wie: Anzeigen der Registerkarte "Entwickler" im Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. Klicken Sie in der Gruppe Steuer **Elemente** auf die **Text** Schaltfläche ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") , um <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> der ersten Zelle ein hinzuzufügen.

7. Klicken Sie auf die zweite Zelle in der zweiten Spalte (neben Einstellungs **Datum**).

8. Klicken Sie in der Gruppe Steuer **Elemente** auf die Schaltfläche **Datums** Auswahl, ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") , um <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> der zweiten Zelle ein hinzuzufügen.

9. Klicken Sie auf die dritte Zelle in der zweiten Spalte (neben **Title**).

10. Klicken Sie in der Gruppe Steuer **Elemente** auf die Kombinations **Feld** -Schaltfläche ![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") , um <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> der dritten Zelle ein hinzuzufügen.

11. Klicken Sie auf die letzte Zelle in der zweiten Spalte (neben **Bild**).

12. Klicken Sie in der Gruppe Steuer **Elemente** auf die Schaltfläche **Bildinhalts Steuerung** ![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl") , um <xref:Microsoft.Office.Tools.Word.PictureContentControl> der letzten Zelle ein hinzuzufügen.

## <a name="create-the-customer-feedback-table"></a>Erstellen der Kundenfeedback-Tabelle
 Erstellen Sie eine Tabelle, die drei verschiedene Typen von Inhaltssteuerelementen enthält, in der der Benutzer Informationen zu Kundenfeedback eingeben kann.

### <a name="to-create-the-customer-feedback-table"></a>So erstellen Sie die Kundenfeedback-Tabelle

1. Klicken Sie in der Word-Vorlage in die Zeile hinter der Tabelle Employee, die Sie zuvor hinzugefügt haben, und drücken **Sie die Eingabe** Taste, um einen neuen Absatz hinzuzufügen.

2. Klicken Sie im Menüband auf die Registerkarte **Einfügen** .

3. Klicken Sie in der Gruppe **Tabellen** auf **Tabelle**, und fügen Sie eine Tabelle mit zwei Spalten und drei Zeilen ein.

4. Geben Sie in der ersten Spalte Text ein, sodass sie der folgenden Spalte ähnelt:

   ||
   |-|
   |**Customer Name**|
   |**Satisfaction Rating**|
   |**Kommentare**|

5. Klicken Sie in die erste Zelle der zweiten Spalte (neben **Kunden Name**).

6. Klicken Sie im Menüband auf die Registerkarte **Entwickler** .

7. Klicken Sie in der Gruppe Steuer **Elemente** auf die **Text** Schaltfläche ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") , um <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> der ersten Zelle ein hinzuzufügen.

8. Klicken Sie in die zweite Zelle der zweiten Spalte (neben der **Zufriedenheitsbewertung**).

9. Klicken Sie in der Gruppe Steuer **Elemente** auf die **Dropdown Liste** ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") , um <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> der zweiten Zelle ein hinzuzufügen.

10. Klicken Sie in die letzte Zelle der zweiten Spalte (neben **Kommentare**).

11. Klicken Sie in der Gruppe Steuer **Elemente** auf die Schaltfläche **Rich-Text** -Schaltfläche ![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") , um <xref:Microsoft.Office.Tools.Word.RichTextContentControl> der letzten Zelle ein hinzuzufügen.

## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>Programm gesteuertes Auffüllen des Kombinations Felds und der Dropdown Liste
 Sie können Inhalts Steuerelemente zur Entwurfszeit mithilfe des Fensters **Eigenschaften** in initialisieren [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Sie können sie auch zur Laufzeit initialisieren, wodurch Sie deren Anfangszustände dynamisch festlegen können. Verwenden Sie für diese exemplarische Vorgehensweise Code, um die Einträge in der <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> und <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> zur Laufzeit aufzufüllen, damit Sie sehen können, wie diese Objekte funktionieren.

### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>So ändern Sie die Benutzeroberfläche der Inhaltssteuerelemente programmgesteuert

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **ThisDocument.cs** oder **ThisDocument. vb**, und klicken Sie dann auf **Code anzeigen**.

2. Fügen Sie der `ThisDocument` -Klasse den folgenden Code hinzu. Dieser Code deklariert mehrere Objekte, die Sie später in dieser exemplarischen Vorgehensweise verwenden.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]

3. Fügen Sie der `ThisDocument_Startup`-Methode der `ThisDocument`-Klasse den folgenden Code hinzu. Durch diesen Code werden <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> und <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> in den Tabellen Einträge hinzugefügt und der Platzhaltertext festgelegt, der in den einzelnen Steuerelementen angezeigt wird, bevor sie vom Benutzer bearbeitet werden.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]

## <a name="prevent-users-from-editing-the-employee-table"></a>Benutzer daran hindern, die Employee-Tabelle zu bearbeiten
 Verwenden Sie das zuvor deklarierte <xref:Microsoft.Office.Tools.Word.GroupContentControl>-Objekt, um die Mitarbeitertabelle zu schützen. Nachdem Sie die Tabelle geschützt haben, können Benutzer die Inhaltssteuerelemente in der Tabelle immer noch bearbeiten. Allerdings können sie in der ersten Spalte keinen Text bearbeiten oder die Tabelle auf andere Weise ändern, z. B. Zeilen und Spalten hinzufügen oder löschen. Weitere Informationen zum <xref:Microsoft.Office.Tools.Word.GroupContentControl> Schützen eines Teils eines Dokuments mithilfe von finden Sie unter [Inhalts Steuerelemente](../vsto/content-controls.md).

### <a name="to-prevent-users-from-editing-the-employee-table"></a>So verhindern Sie, dass Benutzer die Mitarbeitertabelle bearbeiten

1. Fügen Sie der `ThisDocument_Startup`-Methode der `ThisDocument`-Klasse nach dem im vorherigen Schritt hinzugefügten Code den folgenden Code hinzu. Dieser Code verhindert, dass Benutzer die Mitarbeitertabelle bearbeiten, indem die Tabelle in das zuvor deklarierte <xref:Microsoft.Office.Tools.Word.GroupContentControl>-Objekt eingefügt wird.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]

## <a name="add-the-tables-to-the-building-block-collection"></a>Hinzufügen der Tabellen zur Baustein Auflistung
 Fügen Sie die Tabellen einer Auflistung von Dokumentbausteinen in der Vorlage hinzu, sodass Benutzer die Tabellen, die Sie erstellt haben, in das Dokument einfügen können. Weitere Informationen zu Dokument Bausteinen finden Sie unter [Inhalts Steuerelemente](../vsto/content-controls.md).

### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>So fügen Sie die Tabellen den Bausteinen in der Vorlage hinzu

1. Fügen Sie der `ThisDocument_Startup`-Methode der `ThisDocument`-Klasse nach dem im vorherigen Schritt hinzugefügten Code den folgenden Code hinzu. Mit diesem Code werden neue Bausteine hinzugefügt, die die Tabellen der Microsoft. Office. Interop. Word. BuildingBlockEntries-Auflistung enthalten, die alle wiederverwendbaren Bausteine in der Vorlage enthält. Die neuen Bausteine werden in einer neuen Kategorie namens **Mitarbeiter-und Kundeninformationen** definiert, und Ihnen wird der baublocktyp zugewiesen `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]

2. Fügen Sie der `ThisDocument_Startup`-Methode der `ThisDocument`-Klasse nach dem im vorherigen Schritt hinzugefügten Code den folgenden Code hinzu. Dieser Code löscht die Tabellen aus der Vorlage. Die Tabellen sind nicht mehr erforderlich, da Sie sie dem Katalog wiederverwendbarer Bausteine in der Vorlage hinzugefügt haben. Durch den Code wird das Dokument zuerst in den Entwurfsmodus versetzt, sodass die geschützte Mitarbeitertabelle gelöscht werden kann.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]

## <a name="create-a-content-control-that-displays-the-building-blocks"></a>Erstellen eines Inhalts Steuer Elements, das die Bausteine anzeigt
 Erstellen Sie ein Inhaltssteuerelement, das den Zugriff auf die Bausteine (d. h. die Tabellen) ermöglicht, die Sie zuvor erstellt haben. Benutzer können auf dieses Steuerelement klicken, um die Tabellen dem Dokument hinzuzufügen.

### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>So erstellen Sie ein Inhaltssteuerelement, das die Bausteine anzeigt

1. Fügen Sie der `ThisDocument_Startup`-Methode der `ThisDocument`-Klasse nach dem im vorherigen Schritt hinzugefügten Code den folgenden Code hinzu. Dieser Code initialisiert das zuvor deklarierte <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>-Objekt. Das <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> zeigt alle Bausteine an, die in der Kategorie **Mitarbeiter-und Kundeninformationen** definiert sind und die den baublocktyp aufweisen `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]

## <a name="test-the-project"></a>Testen des Projekts
 Benutzer können auf die Steuerelemente im Bausteinkatalog im Dokument klicken, um die Mitarbeiter- oder Kundenfeedback-Tabelle einzufügen. Benutzer können in den Inhaltssteuerelementen in beiden Tabellen Antworten eingeben oder auswählen. Benutzer können andere Teile der Kundenfeedback-Tabelle ändern, sollten aber nicht in der Lage sein, andere Teile der Mitarbeitertabelle zu ändern.

### <a name="to-test-the-employee-table"></a>So testen Sie die Mitarbeitertabelle

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Klicken Sie auf Wählen Sie den **ersten Baustein** aus, um das erste Inhalts Steuerelement des Baustein Katalogs anzuzeigen.

3. Klicken Sie auf den Dropdown Pfeil neben der Überschrift **Benutzerdefinierter Katalog 1** im Steuerelement, und wählen Sie **Mitarbeitertabelle** aus.

4. Klicken Sie in die Zelle rechts neben der Zelle **Employee Name** , und geben Sie einen Namen ein.

     Stellen Sie sicher, dass Sie dieser Zelle nur Text hinzufügen können. <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> ermöglicht es Benutzern, nur Text und keine anderen Inhaltstypen wie Grafiken oder Tabellen hinzuzufügen.

5. Klicken Sie in die Zelle rechts neben der Zelle " **Hire Date** ", und wählen Sie ein Datum in der Datumsauswahl aus.

6. Klicken Sie in die Zelle rechts neben der Zelle " **Title** ", und wählen Sie einen der Auftrags Titel im Kombinations Feld aus.

     Geben Sie optional eine Berufsbezeichnung ein, die nicht in der Liste enthalten ist. Dies ist möglich, weil <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> Benutzern die Auswahl aus einer Liste von Einträgen oder die Eingabe eigener Einträge ermöglicht.

7. Klicken Sie in der Zelle rechts neben der **Bildzelle** auf das Symbol, und navigieren Sie zu einem Bild, um es anzuzeigen.

8. Versuchen Sie, der Tabelle Zeilen oder Spalten hinzuzufügen und Zeilen und Spalten aus der Tabelle zu löschen. Vergewissern Sie sich, dass Sie die Tabelle nicht ändern können. <xref:Microsoft.Office.Tools.Word.GroupContentControl> verhindert, dass Sie Änderungen vornehmen.

### <a name="to-test-the-customer-feedback-table"></a>So testen Sie die Kundenfeedback-Tabelle

1. Klicken Sie auf Wählen Sie den **zweiten Baustein** aus, um das zweite Inhalts Steuerelement des Baustein Katalogs anzuzeigen.

2. Klicken Sie auf den Dropdown Pfeil neben der Überschrift **Benutzerdefinierter Katalog 1** im Steuerelement, und wählen Sie **Kunden Tabelle** aus.

3. Klicken Sie in die Zelle rechts neben der Zelle **Customer Name** , und geben Sie einen Namen ein.

4. Klicken Sie in die Zelle rechts neben der Zelle für die **Zufriedenheitsbewertung** , und wählen Sie eine der verfügbaren Optionen aus.

     Stellen Sie sicher, dass Sie ihren eigenen Eintrag nicht eingeben können. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> ermöglicht Benutzern nur die Auswahl aus einer Liste von Einträgen.

5. Klicken Sie in die Zelle rechts neben der **Kommentar** Zelle, und geben Sie einige Kommentare ein.

     Fügen Sie optional andere Inhalte als Text hinzu, z. B. Grafiken oder eine eingebettete Tabelle. Dies ist möglich, weil <xref:Microsoft.Office.Tools.Word.RichTextContentControl> Benutzern das Hinzufügen anderer Inhalt als Text ermöglicht.

6. Vergewissern Sie sich, dass Sie der Tabelle Zeilen oder Spalten hinzufügen und Zeilen und Spalten aus der Tabelle löschen können. Dies ist möglich, da Sie die Tabelle nicht geschützt haben, indem Sie sie in <xref:Microsoft.Office.Tools.Word.GroupContentControl> eingefügt haben.

7. Schließen Sie die Vorlage.

## <a name="next-steps"></a>Nächste Schritte
 Weitere Informationen zur Verwendung von Inhaltssteuerelementen finden Sie in diesem Thema:

- Binden von Inhaltssteuerelementen an XML-Elemente (werden auch als benutzerdefinierte XML-Teile bezeichnet), die in ein Dokument eingebettet sind Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Binden von Inhalts Steuerelementen an benutzerdefinierte XML-Elemente](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).

## <a name="see-also"></a>Weitere Informationen
- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [Inhalts Steuerelemente](../vsto/content-controls.md)
- [Gewusst wie: Hinzufügen von Inhalts Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Gewusst wie: Schützen von Teilen von Dokumenten mithilfe von Inhalts Steuerelementen](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
