---
title: XML-Schemas und-Daten in Anpassungen auf Dokument Ebene
description: Microsoft Excel und Word bieten die Möglichkeit, Ihren Dokumenten Schemas zuzuordnen und das Importieren und Exportieren von XML-Daten in und aus dem Dokument zu vereinfachen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 57fad7982f762c4837399e12552cd109c9a9086c
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527864"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>XML-Schemas und-Daten in Anpassungen auf Dokument Ebene
  **Wichtig** Die Informationen, die in diesem Thema in Bezug auf Microsoft Word beschrieben werden, werden exklusiv für den Vorteil und die Verwendung von Einzelpersonen und Organisationen präsentiert, die sich außerhalb der USA und ihrer Gebiete befinden oder Programme verwenden, die unter, Microsoft Word-Produkte, die von Microsoft vor Januar 2010 lizenziert wurden Diese Informationen zu Microsoft Word werden möglicherweise nicht von Einzelpersonen oder Organisationen in den USA oder deren Territorien gelesen oder verwendet, die von Microsoft Word-Produkten verwendet werden, die nach dem 10. Januar 2010 von Microsoft lizenziert wurden. Diese Produkte Verhalten sich nicht identisch mit Produkten, die vor diesem Datum lizenziert sind, oder für die Verwendung außerhalb der USA lizenziert und lizenziert wurden.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Mit Microsoft Office Excel und Microsoft Office Word können Sie Ihren Dokumenten Schemas zuordnen. Diese Funktion kann das Importieren und Exportieren von XML-Daten in und aus dem Dokument vereinfachen.

 Visual Studio macht zugeordnete Schema Elemente in Anpassungen auf Dokument Ebene als Steuerelemente im Programmiermodell verfügbar. Für Excel bietet Visual Studio Unterstützung für das Binden von Steuerelementen an Daten in Datenbanken, Webdiensten und Objekten. Für Word und Excel bietet Visual Studio Unterstützung für Aktionsbereiche, die mit einem Schema zugeordneten Dokument verwendet werden können, um für ihre Lösungen eine verbesserte Endbenutzer Funktion zu erstellen. Weitere Informationen finden Sie unter [Übersicht über den Aktions](../vsto/actions-pane-overview.md)Bereich.

> [!NOTE]
> Sie können keine mehrteiligen XML-Schemas in Excel-Lösungen verwenden.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Beim Anfügen von Schemas an Excel-Arbeitsmappen erstellte Objekte
 Wenn Sie ein Schema an eine-Arbeitsmappe anfügen, erstellt Visual Studio automatisch mehrere-Objekte und fügt Sie dem Projekt hinzu. Diese Objekte sollten nicht mithilfe von Visual Studio-Tools gelöscht werden, da Sie von Excel verwaltet werden. Entfernen Sie die zugeordneten Elemente aus dem Arbeitsblatt, oder trennen Sie das Schema mithilfe der Excel-Tools, um Sie zu löschen.

 Es gibt zwei Hauptobjekte:

- XML-Schema (XSD-Datei). Für jedes Schema in der Arbeitsmappe fügt Visual Studio dem Projekt ein Schema hinzu. Dies wird als Projekt Element mit einer XSD-Erweiterung in **Projektmappen-Explorer** angezeigt.

- Eine typisierte <xref:System.Data.DataSet>-Klasse. Diese Klasse wird basierend auf dem Schema erstellt. Diese DataSet-Klasse ist in **Klassenansicht** sichtbar.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Objekte, die erstellt werden, wenn Schema Elemente Excel-Arbeitsblättern zugeordnet werden
 Wenn Sie ein Schema Element aus dem **XML-Quell** Aufgabenbereich einem Arbeitsblatt zuordnen, erstellt Visual Studio automatisch mehrere Objekte und fügt Sie dem Projekt hinzu:

- Steuerelemente Für jedes zugeordnete Objekt in der Arbeitsmappe wird ein- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelement (für nicht wiederholende Schema Elemente) oder ein- <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement (für sich wiederholende Schema Elemente) im-Programmiermodell erstellt. Das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement kann nur gelöscht werden, indem die Zuordnungen und die zugeordneten Objekte aus der Arbeitsmappe gelöscht werden. Weitere Informationen zu-Steuerelementen finden Sie unter [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md).

- BindingSource. Wenn Sie ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> -Element erstellen, indem Sie dem Arbeitsblatt ein nicht wiederholtes Schema Element hinzu ordnen, <xref:System.Windows.Forms.BindingSource> wird ein erstellt, und das-Steuerelement <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> wird an das-Steuerelement gebunden <xref:System.Windows.Forms.BindingSource> . Sie müssen das <xref:System.Windows.Forms.BindingSource> an eine Instanz der Datenquelle binden, die dem Schema entspricht, das dem Dokument zugeordnet ist, z. b. eine Instanz der erstellten typisierten <xref:System.Data.DataSet> Klasse. Erstellen Sie die Bindung, indem Sie die-Eigenschaft und die-Eigenschaft festlegen <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> , die im **Eigenschaften** Fenster verfügbar gemacht werden.

    > [!NOTE]
    > Der <xref:System.Windows.Forms.BindingSource> wird nicht für- <xref:Microsoft.Office.Tools.Excel.ListObject> Objekte erstellt. Sie müssen das manuell <xref:Microsoft.Office.Tools.Excel.ListObject> an die Datenquelle binden, indem Sie die <xref:System.Windows.Forms.BindingSource.DataSource%2A> -Eigenschaft und die-Eigenschaft <xref:System.Windows.Forms.BindingSource.DataMember%2A> im **Eigenschaften** Fenster festlegen.

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Mit dem Office verknüpftes Schema und das Visual Studio-Datenquellen Fenster
 Sowohl die zugeordnete Schema Funktionalität von Office als auch das Visual Studio- **Datenquellen** Fenster können Sie bei der Darstellung von Daten in einem Excel-Arbeitsblatt zur Berichterstellung oder Bearbeitung unterstützen. In beiden Fällen können Sie Datenelemente auf das Excel-Arbeitsblatt ziehen. Beide Methoden erstellen Steuerelemente, bei denen Daten durch einen <xref:System.Windows.Forms.BindingSource> an eine Datenquelle, z <xref:System.Data.DataSet> . b. oder einen Webdienst, gebunden werden.

> [!NOTE]
> Wenn Sie einem Arbeitsblatt ein sich wiederholendes Schema Element zuordnen, erstellt Visual Studio ein <xref:Microsoft.Office.Tools.Excel.ListObject> . Der <xref:Microsoft.Office.Tools.Excel.ListObject> wird nicht automatisch über das an Daten gebunden <xref:System.Windows.Forms.BindingSource> . Sie müssen das manuell <xref:Microsoft.Office.Tools.Excel.ListObject> an die Datenquelle binden, indem Sie die <xref:System.Windows.Forms.BindingSource.DataSource%2A> -Eigenschaft und die-Eigenschaft <xref:System.Windows.Forms.BindingSource.DataMember%2A> im **Eigenschaften** Fenster festlegen.

 In der folgenden Tabelle sind einige der Unterschiede zwischen den beiden Methoden aufgeführt.

|XML-Schema|Datenquellenfenster|
|----------------|-------------------------|
|Verwendet die Office-Schnittstelle.|Verwendet das Fenster " **Datenquellen** " in Visual Studio.|
|Aktiviert die integrierten Office-Funktionen zum Importieren und Exportieren von Daten aus XML-Dateien.|Sie müssen Import-und Exportfunktionen Programm gesteuert bereitstellen.|
|Sie müssen Code schreiben, um die generierten Steuerelemente mit Daten zu füllen.|Steuerelemente, die aus dem Fenster **Datenquellen** hinzugefügt wurden, werden automatisch generiert, um Sie zusammen mit den erforderlichen Verbindungs Zeichenfolgen zu füllen, wenn Sie Datenbankserver verwenden|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Verhalten beim Anfügen von Schemas an Word-Dokumente
 Datenobjekte werden nicht erstellt, wenn Sie ein Schema an ein Word-Dokument anfügen, das in einem Office-Projekt auf Dokument Ebene verwendet wird. Wenn Sie dem Dokument jedoch ein Schema Element zuordnen, werden Steuerelemente erstellt. Der Typ des Steuer Elements hängt vom Typ des Elements ab, das Sie zuordnen. sich wiederholende Elemente generieren Steuerelemente <xref:Microsoft.Office.Tools.Word.XMLNodes> , und nicht wiederholende Elemente generieren Steuerelemente <xref:Microsoft.Office.Tools.Word.XMLNode> . Weitere Informationen finden Sie unter [XMLNodes-Steuer](../vsto/xmlnodes-control.md) Element und [XmlNode-Steuer](../vsto/xmlnode-control.md)Element.

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Bereitstellung von Lösungen, die XML-Schemas einschließen
 Sie sollten ein Installationsprogramm erstellen, um eine Lösung bereitzustellen, die ein XML-Schema verwendet, das einem Dokument zugeordnet ist. Das Installationsprogramm sollte das Schema in der Schema Bibliothek auf dem Computer des Benutzers registrieren. Wenn Sie das Schema nicht registrieren, funktioniert die Lösung weiterhin, da Word ein temporäres Schema basierend auf den Elementen generiert, die im Dokument enthalten sind, wenn der Benutzer es öffnet. Der Benutzer kann jedoch keine Validierung für das Schema ausführen, das zum Erstellen des Projekts verwendet wurde. Weitere Informationen zu Installationsprogrammen finden Sie unter bereit [Stellen von Anwendungen, Diensten und Komponenten](../deployment/deploying-applications-services-and-components.md).

 Sie können dem Projekt auch Code hinzufügen, um zu überprüfen, ob das Schema in der Bibliothek und registriert ist. Wenn dies nicht der Fall ist, können Sie den Benutzer warnen.

 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]

## <a name="see-also"></a>Weitere Informationen

- [Gewusst wie: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Gewusst wie: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
