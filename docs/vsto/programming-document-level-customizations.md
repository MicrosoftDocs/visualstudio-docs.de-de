---
title: Program mieren von Anpassungen auf Dokument Ebene
description: Erfahren Sie, wie Sie Microsoft Word oder Excel mit einer Anpassung auf Dokument Ebene erweitern, um verschiedene Aufgaben ausführen zu können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Sheet3
- thisWorkbook
- thisDocument
- Sheet1
- Sheet2
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument class
- Sheet3 class
- ThisWorkbook class
- writing code for Office solutions
- programming [Office development in Visual Studio], document-level customizations
- Sheet1 class
- Office applications [Office development in Visual Studio], document-level customizations
- Sheet2 class
- document-level customizations [Office development in Visual Studio], programming
- application development [Office development in Visual Studio], document-level customizations
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 58dd8e1803fc0bd06f5c2295b29e9586e1f8eb68
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527518"
---
# <a name="program-document-level-customizations"></a>Program mieren von Anpassungen auf Dokument Ebene
  Wenn Sie Microsoft Office Word oder Microsoft Office Excel mit einer Anpassung auf Dokumentebene erweitern, können Sie die folgenden Aufgaben ausführen:

- Automatisieren der Anwendung über deren Objektmodell

- Hinzufügen von Steuerelementen zur Oberfläche eines Dokuments

- Aufrufen von VBA-Code (Visual Basic for Applications) im Dokument aus der Anpassungsassembly

- Aufrufen von Code in der Anpassungsassembly aus VBA

- Verwalten bestimmter Aspekte des Dokuments, obwohl es sich auf einem Server befindet, auf dem Microsoft Office nicht installiert ist

- Anpassen der Benutzeroberfläche der Anwendung

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  Einige Aspekte beim Schreiben von Code in Projekten auf Dokumentebene unterscheiden sich von anderen Projekttypen in Visual Studio. Viele dieser Unterschiede haben mit der Art zu tun, wie die Office-Objektmodelle im verwalteten Code verfügbar gemacht werden. Weitere Informationen finden Sie unter [Schreiben von Code in Office](../vsto/writing-code-in-office-solutions.md)-Projektmappen.

  Allgemeine Informationen zu Anpassungen auf Dokument Ebene und anderen Lösungs Typen, die Sie mithilfe der Office-Entwicklungs Tools in Visual Studio erstellen können, finden Sie unter Übersicht über die Entwicklung von Office-Projektmappen [&#40;VSTO-&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-generated-classes-in-document-level-projects"></a>Verwenden der generierten Klassen in Projekten auf Dokument Ebene
 Wenn Sie ein Projekt auf Dokumentebene erstellen, generiert Visual Studio automatisch eine Klasse im Projekt, die Sie zum Schreiben von Code verwenden können. Visual Studio generiert unterschiedliche Klassen für Word und Excel:

- In Projekten auf Dokumentebene für Word erhält die Klasse standardmäßig den Namen `ThisDocument` .

- Projekte auf Dokumentebene für Excel haben mehrere generierte Klassen: eine für die Arbeitsmappe und eine für jedes Arbeitsblatt. Standardmäßig lauten die Namen dieser Klassen folgendermaßen:

  - `ThisWorkbook`

  - `Sheet1`

  - `Sheet2`

  - `Sheet3`

  Die generierte Klasse beinhaltet Ereignishandler, die aufgerufen werden, wenn das Dokument geöffnet oder geschlossen wird. Um Code auszuführen, wenn das Dokument geöffnet wird, fügen Sie dem `Startup` -Ereignishandler Code hinzu. Um Code auszuführen, unmittelbar bevor das Dokument geschlossen wird, fügen Sie dem `Shutdown` -Ereignishandler Code hinzu. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

### <a name="understand-the-design-of-the-generated-classes"></a>Grundlegendes zum Entwurf der generierten Klassen
 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]abzielen, sind die Hostelementtypen in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Schnittstellen, weshalb die generierten Klassen ihre Implementierung nicht aus ihnen ableiten können. Stattdessen werden für die generierten Klassen die meisten ihrer Member aus den folgenden Basisklassen abgeleitet:

- `ThisDocument`wird aus <xref:Microsoft.Office.Tools.Word.DocumentBase>abgeleitet.

- `ThisWorkbook`wird aus <xref:Microsoft.Office.Tools.Excel.WorkbookBase>abgeleitet.

- `Sheet`*n*: wird von abgeleitet <xref:Microsoft.Office.Tools.Excel.WorksheetBase> .

  Diese Basisklassen leiten alle Aufrufe an ihre Member zu internen Implementierungen der entsprechenden Hostelementschnittstellen in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]um. Wenn Sie beispielsweise die <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> -Methode der `ThisDocument` -Klasse aufrufen, leitet die <xref:Microsoft.Office.Tools.Word.DocumentBase> -Klasse diesen Aufruf an die interne Implementierung der <xref:Microsoft.Office.Tools.Word.Document> -Schnittstelle in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]um.

## <a name="access-the-object-model-of-the-host-application"></a>Zugreifen auf das Objektmodell der Host Anwendung
 Wenn Sie auf das Objektmodell der Hostanwendung zugreifen möchten, verwenden Sie Member der generierten Klasse in Ihrem Projekt. Jede dieser Klassen entspricht einem Objekt im Objektmodell von Excel oder Word, und sie enthalten einen Großteil derselben Eigenschaften, Methoden und Ereignisse. Beispielsweise stellt die `ThisDocument` -Klasse in einem Projekt auf Dokumentebene für Word stellt einen Großteil derselben Member wie das <xref:Microsoft.Office.Interop.Word.Document> -Objekt im Word-Objektmodell bereit.

 Im folgenden Codebeispiel wird gezeigt, wie Sie mithilfe des Word-Objektmodells das Dokument speichern, das Teil der Anpassung auf Dokumentebene für Word ist. Dieses Beispiel ist für die Ausführung über die `ThisDocument` -Klasse bestimmt.

```vb
Me.Save()
```

```csharp
this.Save();
```

 Verwenden Sie für die Ausführung außerhalb der `ThisDocument` -Klasse das `Globals` -Objekt, um auf die `ThisDocument` -Klasse zuzugreifen. Beispielsweise können Sie diesen Code zu einer Codedatei eines Aktionsbereichs hinzufügen, wenn Sie eine **Speichern** -Schaltfläche in die Benutzeroberfläche des Aktionsbereichs einschließen möchten.

```vb
Globals.ThisDocument.Save()
```

```csharp
Globals.ThisDocument.Save();
```

 Da die `ThisDocument` -Klasse die meisten ihrer Member aus dem <xref:Microsoft.Office.Tools.Word.Document> -Hostelement übernimmt, handelt es sich bei der in diesem Code aufgerufenen `Save` -Methode tatsächlich um die <xref:Microsoft.Office.Tools.Word.Document.Save%2A> -Methode des <xref:Microsoft.Office.Tools.Word.Document> -Hostelements. Diese Methode entspricht der <xref:Microsoft.Office.Interop.Word._Document.Save%2A> -Methode des <xref:Microsoft.Office.Interop.Word.Document> -Objekts im Word-Objektmodell.

 Weitere Informationen zum Verwenden der Objekt Modelle von Word und Excel finden Sie unter Übersicht über das [Word-Objektmodell](../vsto/word-object-model-overview.md) und Übersicht über das [Excel-Objektmodell](../vsto/excel-object-model-overview.md).

 Weitere Informationen zum- `Globals` Objekt finden Sie unter [globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).

## <a name="add-controls-to-documents"></a>Hinzufügen von Steuerelementen zu Dokumenten
 Wenn Sie die Benutzeroberfläche des Dokuments anpassen möchten, können Sie der Dokumentoberfläche Windows Forms-Steuerelemente oder *Hoststeuerelemente* hinzufügen. Sie können Steuerelemente an Daten binden, Benutzerinformationen abfragen und auf Benutzeraktionen reagieren, indem Sie verschiedene Gruppen von Steuerelementen kombinieren und Code schreiben.

 Hoststeuerelemente sind Klassen, die einige der Objekte im Word-Objektmodell und im Excel-Objektmodell erweitern. Zum Beispiel stellt das <xref:Microsoft.Office.Tools.Excel.ListObject> -Hoststeuerelement alle Funktionen des <xref:Microsoft.Office.Interop.Excel.ListObject> -Elements in Excel zur Verfügung. Allerdings hat das <xref:Microsoft.Office.Tools.Excel.ListObject> -Hoststeuerelement weitere Ereignisse und Datenbindungsfunktionen.

 Weitere Informationen finden Sie unter Übersicht über [Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md) und Übersicht [über Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="combine-vba-and-document-level-customizations"></a>Kombinieren von VBA und Anpassungen auf Dokument Ebene
 Sie können VBA-Code in einem Dokument verwenden, das Teil einer Anpassung auf Dokumentebene ist. Sie können VBA-Code im Dokument aus der Anpassungsassembly aufrufen, und Sie können für Ihr Projekt die Aktivierung des VBA-Codes im Dokument konfigurieren, um Code in der Anpassungsassembly aufzurufen.

 Weitere Informationen finden Sie unter [Kombinieren von VBA und Anpassungen auf Dokument Ebene](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="manage-documents-on-a-server"></a>Verwalten von Dokumenten auf einem Server
 Sie können verschiedene Aspekte von Anpassungen auf Dokumentebene auf einem Server verwalten, auf dem Microsoft Office Word oder Microsoft Office Excel nicht installiert ist. Beispielsweise können Sie auf Daten im Datencache des Dokuments zugreifen und diese Daten ändern. Sie können auch die Anpassungsassembly verwalten, die dem Dokument zugeordnet ist. Sie können beispielsweise die Assembly programmgesteuert aus dem Dokument entfernen, sodass das Dokument den Code nicht mehr ausführt, oder Sie können eine Assembly programmgesteuert an ein Dokument anfügen.

 Weitere Informationen finden Sie unter [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Anpassen der Benutzeroberfläche von Microsoft Office Anwendungen
 Sie können die Benutzeroberfläche von Word und Excel mithilfe einer Anpassung auf Dokumentebene folgendermaßen anpassen:

- Hinzufügen von Hoststeuerelementen oder Windows Forms-Steuerelementen zur Dokumentoberfläche

   Weitere Informationen finden Sie unter [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md), [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)und [Windows Forms Steuerelemente in der Übersicht über Office-Dokumente](../vsto/windows-forms-controls-on-office-documents-overview.md).

- Hinzufügen eines Aktionsbereichs zum Dokument

   Weitere Informationen finden Sie unter [Übersicht über den Aktions](../vsto/actions-pane-overview.md)Bereich.

- Hinzufügen von benutzerdefinierten Registerkarten zum Menüband

   Weitere Informationen finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).

- Hinzufügen benutzerdefinierter Gruppen zu einer integrierten Registerkarte auf dem Menüband

   Weitere Informationen finden Sie unter Gewusst [wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md).

  Weitere Informationen zum Anpassen der Benutzeroberfläche von Microsoft Office Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

## <a name="get-extended-objects-from-native-office-objects-in-document-level-customizations"></a>Erweiterte Objekte aus systemeigenen Office-Objekten in Anpassungen auf Dokument Ebene erhalten
 Viele Ereignishandler für Office-Ereignisse empfangen ein systemeigenes Office-Objekt, das die Arbeitsmappe, das Arbeitsblatt oder das Dokument darstellt, durch das das Ereignis ausgelöst wurde. In einigen Fällen möchten Sie eventuell Code nur dann ausführen, wenn das Ereignis durch die Arbeitsmappe oder das Dokument in Ihrer Anpassung auf Dokumentebene ausgelöst wurde. So könnte es sein, dass Sie in einer Anpassung auf Dokumentebene für Excel bestimmten Code nur ausführen möchten, wenn der Benutzer eines der Arbeitsblätter in der angepassten Arbeitsmappe aktiviert, diesen Code aber nicht ausführen möchten, wenn der Benutzer ein Arbeitsblatt in einer anderen Arbeitsmappe aktiviert, die zufällig zur gleichen Zeit geöffnet ist.

 Wenn Sie ein systemeigenes Office-Objekt haben, können Sie testen, ob das betreffende Objekt in einer Anpassung auf Dokumentebene zu einem *Hostelement* oder *Hoststeuerelement* erweitert wurde. Hostelemente und Hoststeuerelemente sind Typen, die von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bereitgestellt werden und Funktionalität zu Objekten hinzufügen, die als systemeigene Elemente im Word- oder Excel-Objektmodell vorhanden sind (sogenannte *systemeigene Office-Objekte*). Hostelemente und Hoststeuerelemente werden zusammen auch als *erweiterte Objekte* bezeichnet. Weitere Informationen zu Host Elementen und Host Steuerelementen finden Sie unter [Übersicht über Host Elemente und](../vsto/host-items-and-host-controls-overview.md)Host Steuerelemente.

## <a name="understand-the-getvstoobject-and-hasvstoobject-methods"></a>Grundlegendes zu den Methoden GetVstoObject und HasVstoObject
 Um ein systemeigenes Office-Objekt zu testen, verwenden Sie in Ihrem Projekt die `HasVstoObject`- und die `GetVstoObject`-Methode:

- Wenn Sie ermitteln möchten, ob das systemeigene Office-Objekt in Ihrer Anpassung ein erweitertes Objekt hat, verwenden Sie die `HasVstoObject`-Methode. Diese Methode gibt **true** zurück, wenn das systemeigene Office-Objekt ein erweitertes Objekt hat, andernfalls gibt sie **false** zurück.

- Wenn Sie das erweiterte Objekt für ein systemeigenes Office-Objekt abrufen möchten, verwenden Sie die `GetVstoObject`-Methode. Diese Methode gibt ein <xref:Microsoft.Office.Tools.Excel.ListObject>-, <xref:Microsoft.Office.Tools.Excel.Workbook>-, <xref:Microsoft.Office.Tools.Excel.Worksheet>- oder <xref:Microsoft.Office.Tools.Word.Document> -Objekt zurück, wenn das angegebene systemeigene Office-Objekt ein solches Objekt hat. Andernfalls wird `GetVstoObject` **null** zurückgegeben. Die `GetVstoObject`-Methode gibt z. B. ein <xref:Microsoft.Office.Tools.Word.Document> zurück, wenn das angegebene <xref:Microsoft.Office.Interop.Word.Document>-Objekt das zugrunde liegende Objekt für das Dokument in Ihrem Word-Dokumentprojekt ist.

  In Projekten auf Dokument Ebene können Sie die- `GetVstoObject` Methode nicht zum Erstellen eines neuen- <xref:Microsoft.Office.Tools.Excel.Workbook> ,-oder- <xref:Microsoft.Office.Tools.Excel.Worksheet> <xref:Microsoft.Office.Tools.Word.Document> Host Elements zur Laufzeit verwenden. Sie können diese Methode nur für den Zugriff auf vorhandene Hostelemente verwenden, die zur Entwurfszeit in Ihrem Projekt generiert werden. Wenn Sie neue Host Elemente zur Laufzeit erstellen möchten, müssen Sie ein VSTO-Add-in-Projekt entwickeln. Weitere Informationen finden Sie Unterprogramm gesteuerte [Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) und [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="use-the-getvstoobject-and-hasvstoobject-methods"></a>Verwenden der Methoden GetVstoObject und HasVstoObject
 Um die `HasVstoObject` -Methode und die-Methode aufzurufen `GetVstoObject` , verwenden Sie die- `Globals.Factory.GetVstoObject` Methode oder die `Globals.Factory.HasVstoObject` -Methode, und übergeben Sie das systemeigene Word-oder Excel-Objekt, <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Excel.Worksheet> das Sie testen möchten.

## <a name="see-also"></a>Weitere Informationen
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Kombinieren von VBA und Anpassungen auf Dokument Ebene](../vsto/combining-vba-and-document-level-customizations.md)
- [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Schreiben von Code in Office-Lösungen](../vsto/writing-code-in-office-solutions.md)
