---
title: Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen
description: Erfahren Sie mehr über die grundlegenden Unterschiede zwischen dem Verhalten von Host Elementen und Host Steuerelementen und systemeigenen Office-Objekten zur Laufzeit.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fbc3258f3ea7e0b3cc93a2887dfff5a3bfefb19d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891890"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen
  Jedes Hostelement und Hoststeuerelement ist so konzipiert, dass es sich wie ein entsprechendes systemeigenes Microsoft Office Word- oder Microsoft Office Excel-Objekt mit zusätzlichen Funktionen verhält. Es gibt jedoch einige grundlegende Unterschiede zwischen dem Verhalten von Hostelementen und Hoststeuerelementen und systemeigenen Office-Objekten zur Laufzeit.

 Allgemeine Informationen zu Host Elementen und Host Steuerelementen finden Sie unter [Übersicht über Host Elemente und Host](../vsto/host-items-and-host-controls-overview.md)Steuerelemente.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="programmatically-create-host-items"></a>Programm gesteuertes Erstellen von Host Elementen
 Wenn Sie ein Dokument, eine Arbeitsmappe oder ein Arbeitsblatt mithilfe des Word- oder Excel-Objektmodells zur Laufzeit programmgesteuert erstellen, ist das Element kein Hostelement. Stattdessen ist das neue Objekt ein systemeigenes Office-Objekt. Wenn Sie z. B. die <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> -Methode zum Erstellen eines neuen Word-Dokuments zur Laufzeit verwenden, handelt es sich dabei um ein systemeigenes <xref:Microsoft.Office.Interop.Word.Document> -Objekt, anstatt um ein <xref:Microsoft.Office.Tools.Word.Document> -Hostelement. Beim Erstellen eines neuen Arbeitsblatts zur Laufzeit mithilfe der <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> -Methode erhalten Sie entsprechend ein systemeigenes <xref:Microsoft.Office.Interop.Excel.Worksheet> -Objekt, anstatt ein <xref:Microsoft.Office.Tools.Excel.Worksheet> -Hostelement.

 In Projekten auf Dokumentebene können Sie zur Laufzeit keine Hostelemente erstellen. Hostelemente können in Projekten auf Dokumentebene nur zur Entwurfszeit erstellt werden. Weitere Informationen finden Sie unter [Dokument Host Element](../vsto/document-host-item.md), [Arbeitsmappenhostelement](../vsto/workbook-host-item.md)und [Arbeitsblatt-Host Element](../vsto/worksheet-host-item.md).

 In VSTO-Add-In-Projekten können Sie <xref:Microsoft.Office.Tools.Word.Document>-, <xref:Microsoft.Office.Tools.Excel.Workbook>- oder <xref:Microsoft.Office.Tools.Excel.Worksheet> -Hostelemente zur Laufzeit erstellen. Weitere Informationen finden [Sie unter Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="programmatically-create-host-controls"></a>Programm gesteuertes Erstellen von Host Steuerelementen
 Sie können Hoststeuerelemente zur Laufzeit programmgesteuert zu einem <xref:Microsoft.Office.Tools.Word.Document> - oder <xref:Microsoft.Office.Tools.Excel.Worksheet> -Hostelement hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Sie können Hoststeuerelemente nicht zu einem systemeigenen <xref:Microsoft.Office.Interop.Word.Document> oder <xref:Microsoft.Office.Interop.Excel.Worksheet>hinzufügen.

> [!NOTE]
> Die folgenden Hoststeuerelemente können nicht programmgesteuert zu Arbeitsblättern oder Dokumenten hinzugefügt werden: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>und <xref:Microsoft.Office.Tools.Word.XMLNodes>.

## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Grundlegendes zu Typunterschieden zwischen Host Elementen, Host Steuerelementen und systemeigenen Office-Objekten
 Für jedes Hostelement und Hoststeuerelement gibt es ein zugrunde liegendes systemeigenes Microsoft Office Word- oder Microsoft Office Excel-Objekt. Sie können auf das zugrunde liegende Objekt zugreifen, indem Sie die InnerObject-Eigenschaft des Host Elements oder des Host Steuer Elements verwenden. Allerdings besteht keine Möglichkeit, ein systemeigenes Office-Objekt in ein entsprechendes Hostelement oder Hoststeuerelement umzuwandeln. Wenn Sie versuchen, ein systemeigenes Office-Objekt in ein Hostelement oder Hoststeuerelement umzuwandeln, wird ein <xref:System.InvalidCastException> ausgelöst.

 Es gibt verschiedene Szenarien, in denen sich die Unterschiede zwischen den Typen von Hostelementen und Hoststeuerelementen sowie den zugrunde liegenden systemeigenen Office-Objekte auf den Code auswirken können.

### <a name="pass-host-controls-to-methods-and-properties"></a>Übergeben von Host Steuerelementen an Methoden und Eigenschaften
 In Word können Sie ein Hoststeuerelement nicht an eine Methode oder Eigenschaft übergeben, die ein systemeigenes Word-Objekt als Parameter erfordert. Sie müssen die InnerObject-Eigenschaft des-Host Steuer Elements verwenden, um das zugrunde liegende systemeigene Word-Objekt zurückzugeben. Sie können z. B. ein <xref:Microsoft.Office.Interop.Word.Bookmark> -Objekt an eine Methode übergeben, indem Sie die <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> -Eigenschaft des <xref:Microsoft.Office.Tools.Word.Bookmark> -Hoststeuerelements an die Methode übergeben.

 In Excel müssen Sie die InnerObject-Eigenschaft des Host Steuer Elements verwenden, um das Host Steuerelement an eine Methode oder Eigenschaft zu übergeben, wenn die Methode oder Eigenschaft das zugrunde liegende Excel-Objekt erwartet.

 Im folgenden Beispiel wird ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement erstellt und an die <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> -Methode übergeben. Der Code verwendet die <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> -Eigenschaft des benannten Bereichs, um das zugrunde liegende Office- <xref:Microsoft.Office.Interop.Excel.Range> zurückzugeben, das von der <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> -Methode benötigt wird.

 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]

### <a name="return-types-of-native-office-methods-and-properties"></a>Rückgabe Typen von systemeigenen Office-Methoden und-Eigenschaften
 Die meisten Methoden und Eigenschaften von Hostelementen geben das zugrunde liegende systemeigene Office-Objekt zurück, auf dem das Hostelement basiert. Die <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> -Eigenschaft des <xref:Microsoft.Office.Tools.Excel.NamedRange> -Hoststeuerelements in Excel gibt z. B. ein <xref:Microsoft.Office.Interop.Excel.Worksheet> -Objekt anstelle eines <xref:Microsoft.Office.Tools.Excel.Worksheet> -Hostelements zurück. Die <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> -Eigenschaft eines <xref:Microsoft.Office.Tools.Word.RichTextContentControl> -Hoststeuerelements in Word gibt entsprechend ein <xref:Microsoft.Office.Interop.Word.Document> -Objekt anstelle eines <xref:Microsoft.Office.Tools.Word.Document> -Hostelements zurück.

### <a name="access-collections-of-host-controls"></a>Zugreifen auf Sammlungen von Host Steuerelementen
 Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bietet für die einzelnen Hoststeuerelementtypen keine individuellen Auflistungen. Verwenden Sie stattdessen die Control-Eigenschaft eines-Host Elements, um alle verwalteten Steuerelemente (sowohl Host Steuerelemente als auch Windows Forms Steuerelemente) im Dokument oder Arbeitsblatt zu durchlaufen und dann nach Elementen zu suchen, die dem Typ des gewünschten Host Steuer Elements entsprechen. Im folgenden Codebeispiel wird jedes Steuerelement in einem Word-Dokument untersucht und dann bestimmt, ob das Steuerelement ein <xref:Microsoft.Office.Tools.Word.Bookmark>ist.

 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]

 Weitere Informationen zur Eigenschaft Steuerelemente von Host Elementen finden [Sie unter Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Die Objektmodelle von Word und Excel enthalten Eigenschaften, die Auflistungen von systemeigenen Steuerelementen für Dokumente und Arbeitsblätter bereitstellen. Sie können mithilfe dieser Eigenschaften nicht auf verwaltete Steuerelemente zugreifen. Es ist z. B. nicht möglich, jedes <xref:Microsoft.Office.Tools.Word.Bookmark> -Hoststeuerelement in einem Dokument mithilfe der <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> -Eigenschaft einer <xref:Microsoft.Office.Interop.Word.Document> - oder <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> -Eigenschaft eines <xref:Microsoft.Office.Tools.Word.Document>aufzuzählen. Diese Eigenschaften beziehen nur die <xref:Microsoft.Office.Interop.Word.Bookmark> -Steuerelemente im Dokument ein. Sie enthalten nicht die <xref:Microsoft.Office.Tools.Word.Bookmark> -Hoststeuerelemente im Dokument.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Arbeitsblatt-Host Element](../vsto/worksheet-host-item.md)
- [Arbeitsmappenhostelement](../vsto/workbook-host-item.md)
- [Dokument Host Element](../vsto/document-host-item.md)
