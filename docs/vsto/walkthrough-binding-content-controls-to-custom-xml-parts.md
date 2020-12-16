---
title: 'Exemplarische Vorgehensweise: Binden von Steuerelementen an benutzerdefinierte XML-Elemente'
description: Erfahren Sie, wie Sie Inhalts Steuerelemente in einer Anpassung auf Dokument Ebene für Word an XML-Daten binden, die im Dokument gespeichert sind.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PlainTextContentControl, binding to a custom XML part
- custom XML parts, binding to content controls
- content controls [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], content controls
- DropDownListContentControl, binding items to a custom XML part
- DatePickerContentControl, binding to a custom XML part
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a82a8fd98bbf1a735661f3e1cf01e2452eb7ee58
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527968"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>Exemplarische Vorgehensweise: Binden von Steuerelementen an benutzerdefinierte XML-Elemente
  Diese exemplarische Vorgehensweise veranschaulicht, wie Sie Inhaltssteuerelemente in einer Anpassung auf Dokumentebene für Word an XML-Daten binden, die in dem Dokument gespeichert sind.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Mit Word können Sie XML-Daten mit dem Namen *benutzerdefinierte XML-Teile* in einem Dokument speichern. Sie können die Anzeige dieser Daten steuern, indem Sie Inhaltssteuerelemente an Elemente in einem benutzerdefinierten XML-Abschnitt binden. Im Beispieldokument dieser exemplarischen Vorgehensweise werden Mitarbeiterinformationen angezeigt, die in einem benutzerdefinierten XML-Abschnitt gespeichert werden. Wenn Sie das Dokument öffnen, zeigen die Inhaltssteuerelemente die Werte der XML-Elemente an. Am Text in den Inhaltssteuerelementen vorgenommene Änderungen werden im benutzerdefinierten XML-Abschnitt gespeichert.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Hinzufügen von Inhaltssteuerelementen zum Word-Dokument in einem Projekt auf Dokumentebene zur Entwurfszeit.

- Erstellen einer XML-Datendatei und eines XML-Schemas, das die Elemente definiert, die an die Inhaltssteuerelemente gebunden werden sollen.

- Anfügen des XML-Schemas an das Dokument zur Entwurfszeit.

- Hinzufügen des Inhalts der XML-Datei zu einem benutzerdefinierten XML-Abschnitt im Dokument zur Laufzeit.

- Binden der Inhaltssteuerelemente an Elemente im benutzerdefinierten XML-Abschnitt.

- Binden eines <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> an eine Gruppe von Werten, die im XML-Schema definiert sind.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-document-project"></a>Erstellen eines neuen Word-Dokument Projekts
 Erstellen Sie ein Word-Dokument, das Sie in der exemplarischen Vorgehensweise verwenden.

### <a name="to-create-a-new-word-document-project"></a>So erstellen Sie ein neues Word-Dokumentprojekt

1. Erstellen Sie ein Word-Dokument Projekt mit dem Namen Mitarbeiter- **EControls**. Erstellen Sie ein neues Dokument für die Projektmappe. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Öffnet das neue Word-Dokument im Designer und fügt **Projektmappen-Explorer** das Projekt "Mitarbeiter- **EControls** " hinzu.

## <a name="add-content-controls-to-the-document"></a>Hinzufügen von Inhalts Steuerelementen zum Dokument
 Erstellen Sie eine Tabelle, die drei verschiedene Typen von Inhaltssteuerelementen enthält, in der der Benutzer Informationen über einen Mitarbeiter anzeigen bzw. bearbeiten kann.

### <a name="to-add-content-controls-to-the-document"></a>So fügen Sie dem Dokument Inhaltssteuerelemente hinzu

1. Wählen Sie im Word-Dokument, das im-Designer gehostet wird [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , auf dem Menüband die Registerkarte **Einfügen** aus.

2. Wählen Sie in der Gruppe **Tabellen** die Option **Tabelle** aus, und fügen Sie eine Tabelle mit 2 Spalten und 3 Zeilen ein.

3. Geben Sie in der ersten Spalte Text ein, sodass sie der folgenden Spalte ähnelt:

   ||
   |-|
   |**Employee Name**|
   |**Hire Date**|
   |**Titel**|

4. Wählen Sie in der zweiten Spalte der Tabelle die erste Zeile (neben **Employee Name**) aus.

5. Wählen Sie im Menüband die Registerkarte **Entwickler** aus.

   > [!NOTE]
   > Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter Gewusst [wie: Anzeigen der Registerkarte "Entwickler" im Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. Wählen Sie in der Gruppe Steuer **Elemente** die **Text** Schaltfläche ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") aus, um <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> der ersten Zelle ein hinzuzufügen.

7. Wählen Sie in der zweiten Spalte der Tabelle die zweite Zeile aus (neben Einstellungs **Datum**).

8. Wählen Sie in der Gruppe Steuer **Elemente** die Schaltfläche **Datums** Auswahl, ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") aus, um <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> der zweiten Zelle ein hinzuzufügen.

9. Wählen Sie in der zweiten Spalte der Tabelle die dritte Zeile (neben **Titel**) aus.

10. Wählen Sie in der Gruppe Steuer **Elemente** die **Dropdown Listen Schaltfläche** ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") aus, um <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> der letzten Zelle ein hinzuzufügen.

    Das ist die vollständige Benutzeroberfläche für dieses Projekt. Wenn Sie das Projekt jetzt ausführen, können Sie in der ersten Zeile Text eingeben und in der zweiten Zeile ein Datum auswählen. Im nächsten Schritt fügen Sie die anzuzeigenden Daten in einer XML-Datei an das Dokument an.

## <a name="create-the-xml-data-file"></a>Erstellen der XML-Datendatei
 Sie erhalten XML-Daten zum Speichern in einem benutzerdefinierten XML-Abschnitt üblicherweise von einer externen Quelle, wie etwa einer Datei oder Datenbank. In dieser exemplarischen Vorgehensweise erstellen Sie eine XML-Datei mit Mitarbeiterdaten, die durch Elemente gekennzeichnet sind, die Sie an die Inhaltssteuerelemente im Dokument binden. Um die Daten zur Laufzeit verfügbar zu machen, Betten Sie die XML-Datei als Ressource in die Anpassungsassembly ein.

#### <a name="to-create-the-data-file"></a>So erstellen Sie die Datendatei

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

2. Wählen Sie im Bereich **Vorlagen** die Option **XML-Datei** aus.

3. Benennen Sie die Datei **employees.xml**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

     Die **employees.xml** Datei wird im Code-Editor geöffnet.

4. Ersetzen Sie den Inhalt der **employees.xml** Datei durch den folgenden Text.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">
      <employee>
        <name>Karina Leal</name>
        <hireDate>1999-04-01</hireDate>
        <title>Manager</title>
      </employee>
    </employees>
    ```

5. Wählen Sie in **Projektmappen-Explorer** die **employees.xml** Datei aus.

6. Wählen Sie im Fenster **Eigenschaften** die Eigenschaft Buildvorgang aus, und ändern Sie **dann den Wert** in **eingebettete Ressource**.

     Dieser Schritt bettet die XML-Datei als Ressource in die Assembly ein, wenn Sie das Projekt erstellen. Dadurch können Sie auf den Inhalt der XML-Datei zur Laufzeit zugreifen.

## <a name="create-an-xml-schema"></a>Erstellen eines XML-Schemas
 Wenn Sie ein Inhaltssteuerelement an ein einzelnes Element in einem benutzerdefinierten XML-Abschnitt binden möchten, müssen Sie kein XML-Schema verwenden. Um jedoch das <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> an einen Satz von Werten zu binden, müssen Sie ein XML-Schema erstellen, das die zuvor erstellte XML-Datendatei überprüft. Das XML-Schema definiert die möglichen Werte für das `title`-Element. Im weiteren Verlauf dieser exemplarischen Vorgehensweise binden Sie das <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> an dieses Element.

#### <a name="to-create-an-xml-schema"></a>So erstellen Sie ein XML-Schema

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

2. Wählen Sie im Bereich **Vorlagen** die Option **XML-Schema** aus.

3. Benennen Sie das Schema **Employees. xsd** , und klicken Sie auf die Schaltfläche **Hinzufügen** .

     Der Schema-Designer wird geöffnet.

4. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für  **Employees. xsd**, und wählen Sie dann  **Code anzeigen** aus.

5. Ersetzen Sie den Inhalt der Datei **Employees. xsd** durch das folgende Schema.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"
        targetNamespace="http://schemas.microsoft.com/vsto/samples"
        xmlns:xs="http://www.w3.org/2001/XMLSchema"
        elementFormDefault="qualified">
      <xs:element name="employees" type="EmployeesType"></xs:element>
      <xs:complexType name="EmployeesType">
        <xs:all>
          <xs:element name="employee" type="EmployeeType"/>
        </xs:all>
      </xs:complexType>
      <xs:complexType name="EmployeeType">
        <xs:sequence>
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>
        </xs:sequence>
      </xs:complexType>
      <xs:simpleType name="TitleType">
        <xs:restriction base="xs:string">
          <xs:enumeration value ="Engineer"/>
          <xs:enumeration value ="Designer"/>
          <xs:enumeration value ="Manager"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:schema>
    ```

6. Klicken Sie im Menü **Datei** auf **Alle speichern** , um die Änderungen am **employees.xml** und den Dateien **Employees. xsd** zu speichern.

## <a name="attach-the-xml-schema-to-the-document"></a>Anfügen des XML-Schemas an das Dokument
 Sie müssen das XML-Schema an das Dokument anfügen, um das <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> an die gültigen Werte des `title`-Elements zu binden.

### <a name="to-attach-the-xml-schema-to-the-document--word_15_short"></a>So fügen Sie das XML-Schema an das Dokument an ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] )

1. Aktivieren Sie **EmployeeControls.docx** im Designer.

2. Wählen Sie im Menüband die Registerkarte **Entwickler** aus, und klicken Sie dann auf die Schaltfläche **Add-ins** .

3. Wählen Sie im Dialogfeld **Vorlagen und Add-ins** die Registerkarte **XML-Schema** aus, und wählen Sie dann die Schaltfläche **Schema hinzufügen** aus.

4. Navigieren Sie zum zuvor erstellten Schema **Employees. xsd** , das sich im Projektverzeichnis befindet, und wählen Sie dann die Schaltfläche **Öffnen** aus.

5. Klicken Sie im Dialogfeld **Schema Einstellungen** auf die Schaltfläche **OK** .

6. Wählen Sie die Schaltfläche **OK** aus, um das Dialogfeld **Vorlagen und Add-ins** zu schließen.

### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>So fügen Sie das XML-Schema an das Dokument an (Word 2010)

1. Aktivieren Sie **EmployeeControls.docx** im Designer.

2. Wählen Sie im Menüband die Registerkarte **Entwickler** aus.

3. Wählen Sie in der Gruppe **XML** die Schaltfläche **Schema** aus.

4. Wählen Sie im Dialogfeld **Vorlagen und Add-ins** die Registerkarte **XML-Schema** aus, und wählen Sie dann die Schaltfläche **Schema hinzufügen** aus.

5. Navigieren Sie zum zuvor erstellten Schema **Employees. xsd** , das sich im Projektverzeichnis befindet, und klicken Sie auf die Schaltfläche **Öffnen** .

6. Klicken Sie im Dialogfeld **Schema Einstellungen** auf die Schaltfläche **OK** .

7. Wählen Sie die Schaltfläche **OK** aus, um das Dialogfeld **Vorlagen und Add-ins** zu schließen.

     Der Aufgabenbereich **XML-Struktur** wird geöffnet.

8. Schließen Sie den Aufgabenbereich **XML-Struktur** .

## <a name="add-a-custom-xml-part-to-the-document"></a>Hinzufügen eines benutzerdefinierten XML-Teils zum Dokument
 Bevor Sie die Inhaltssteuerelemente an die Elemente in der XML-Datei binden können, müssen Sie einem neuen benutzerdefiniertem XML-Abschnitt im Dokument den Inhalt der XML-Datei hinzufügen.

### <a name="to-add-a-custom-xml-part-to-the-document"></a>So fügen Sie dem Dokument einen benutzerdefinierten XML-Abschnitt hinzu

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für  **ThisDocument.cs** oder **ThisDocument. vb**, und wählen Sie dann **Code anzeigen** aus.

2. Fügen Sie der `ThisDocument`-Klasse die folgenden Deklarationen hinzu. In diesem Code werden mehrere Objekte deklariert, mit denen Sie dem Dokument einen benutzerdefinierten XML-Abschnitt hinzufügen.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]

3. Füge der `ThisDocument`-Klasse die folgende Methode hinzu. Diese Methode ruft den Inhalt der XML-Datendatei ab, die als Ressource in der Assembly eingebettet ist, und gibt den Inhalt als XML-Zeichenfolge zurück.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]

4. Füge der `ThisDocument`-Klasse die folgende Methode hinzu. Die `AddCustomXmlPart`-Methode erstellt einen neuen benutzerdefinierten XML-Abschnitt, der eine XML-Zeichenfolge enthält, die an die Methode übergeben wird.

     Um sicherzustellen, dass der benutzerdefinierte XML-Abschnitt nur einmal erstellt wird, erstellt die Methode den benutzerdefinierten XML-Abschnitt nur dann, wenn noch kein benutzerdefinierter XML-Abschnitt mit einer übereinstimmenden GUID im Dokument vorhanden ist. Beim ersten Aufruf dieser Methode wird der Wert der <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A>-Eigenschaft in der Zeichenfolge `employeeXMLPartID` gespeichert. Der Wert der `employeeXMLPartID`-Zeichenfolge wird im Dokument beibehalten, da er mit dem <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>-Attribut deklariert wurde.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]

## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Binden der Inhalts Steuerelemente an Elemente im benutzerdefinierten XML-Abschnitt
 Binden Sie jedes Inhalts Steuerelement an ein Element im benutzerdefinierten XML-Abschnitt, indem Sie die **XmlMapping** -Eigenschaft der einzelnen Inhalts Steuerelemente verwenden.

### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>So binden Sie die Inhaltssteuerelemente an Elemente im benutzerdefinierten XML-Abschnitt

1. Füge der `ThisDocument`-Klasse die folgende Methode hinzu. Mit dieser Methode wird jedes Inhaltssteuerelement an ein Element im benutzerdefinierten XML-Abschnitt gebunden und die Anzeige des Datumsformats für das <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> festgelegt.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]

## <a name="run-your-code-when-the-document-is-opened"></a>Ausführen des Codes beim Öffnen des Dokuments
 Erstellen Sie den benutzerdefinierten XML-Abschnitt, und binden Sie die benutzerdefinierten Steuerelemente an die Daten, wenn das Dokument geöffnet wird.

### <a name="to-run-your-code-when-the-document-is-opened"></a>So führen Sie den Code beim Öffnen des Dokuments aus

1. Fügen Sie der `ThisDocument_Startup`-Methode der `ThisDocument`-Klasse den folgenden Code hinzu. Mit diesem Code wird die XML-Zeichenfolge aus der **employees.xml** Datei abgerufen, die XML-Zeichenfolge einem neuen benutzerdefinierten XML-Abschnitt im Dokument hinzugefügt und die Inhalts Steuerelemente an Elemente im benutzerdefinierten XML-Abschnitt gebunden.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]

## <a name="test-the-project"></a>Testen des Projekts
 Wenn Sie das Dokument öffnen, zeigen die Inhaltssteuerelemente Daten der Elemente im benutzerdefinierten XML-Abschnitt an. Sie können auf das klicken, <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> um einen von drei gültigen Werten für das- `title` Element auszuwählen, die in der Datei **Employees. xsd** definiert sind. Wenn Sie die Daten in einem Inhaltssteuerelement bearbeiten, werden die neuen Werte im benutzerdefinierten XML-Abschnitt im Dokument gespeichert.

### <a name="to-test-the-content-controls"></a>So testen Sie die Inhaltssteuerelemente

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Überprüfen Sie, ob die Tabelle im Dokument ähnlich aussieht wie die folgende Tabelle. Jede der Zeichenfolgen in der zweiten Spalte wird von einem Element im benutzerdefinierten XML-Abschnitt im Dokument abgerufen.

    |Column|Wert|
    |-|-|
    |**Employee Name**|**Karina Leal**|
    |**Hire Date**|**April 1, 1999**|
    |**Titel**|**Manager**|

3. Wählen Sie die Zelle rechts neben der Zelle **Employee Name** aus, und geben Sie einen anderen Namen ein.

4. Wählen Sie die Zelle rechts neben der Zelle " **Hire Date** " aus, und wählen Sie in der Datumsauswahl ein anderes Datum aus.

5. Wählen Sie die Zelle rechts neben der Zelle " **Title** " aus, und wählen Sie ein neues Element aus der Dropdown Liste aus.

6. Speichern und schließen Sie das Dokument.

7. Öffnen Sie im Datei-Explorer den Ordner *\bin\debug* unter dem Speicherort des Projekts.

8. Öffnen Sie das Kontextmenü für **EmployeeControls.docx** , und wählen Sie dann **Umbenennen** aus.

9. Benennen Sie die Datei **EmployeeControls.docx.zip**.

     Das **EmployeeControls.docx** Dokument wird im Open XML-Format gespeichert. Wenn Sie dieses Dokument mit der *ZIP* -Dateinamenerweiterung umbenennen, können Sie den Inhalt des Dokuments überprüfen. Weitere Informationen zu Open XML finden Sie im technischen Artikel [Einführung in die Open XML-Dateiformate von Office (2007)](/previous-versions/office/developer/office-2007/aa338205(v=office.12)).

10. Öffnen Sie die Datei **EmployeeControls.docx.zip** .

11. Öffnen Sie den Ordner **customXml** .

12. Öffnen Sie das Kontextmenü für **item2.xml** , und wählen Sie dann **Öffnen** aus.

     Diese Datei enthält den benutzerdefinierten XML-Abschnitt, den Sie dem Dokument hinzugefügt haben.

13. Überprüfen Sie, ob die Elemente `name`, `hireDate` und `title` die neuen Werte enthalten, die Sie in die Inhaltssteuerelemente im Dokument eingegeben haben.

14. Schließen Sie die **item2.xml** Datei.

## <a name="next-steps"></a>Nächste Schritte
 Weitere Informationen über die Verwendung von Inhaltssteuerelementen finden Sie in den folgenden Themen:

- Erstellen Sie eine Vorlage mithilfe aller verfügbaren Inhaltssteuerelemente. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer Vorlage mithilfe von Inhalts Steuerelementen](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).

- Ändern Sie die Daten in den benutzerdefinierten XML-Abschnitten bei geschlossenem Dokument. Wenn der Benutzer das Dokument das nächste Mal öffnet, zeigen die Inhaltssteuerelemente, die an die XML-Elemente gebunden sind, die neuen Daten an.

- Schützen Sie Teile eines Dokuments mithilfe von Inhaltssteuerelementen. Weitere Informationen finden Sie unter Gewusst [wie: Schützen von Teilen von Dokumenten mithilfe von Inhalts Steuerelementen](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="see-also"></a>Weitere Informationen
- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [Inhalts Steuerelemente](../vsto/content-controls.md)
- [Gewusst wie: Hinzufügen von Inhalts Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Gewusst wie: Schützen von Teilen von Dokumenten mithilfe von Inhalts Steuerelementen](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
