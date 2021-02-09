---
title: Dokument Host Element
description: Erfahren Sie, dass das Dokument Host Element ein Typ ist, der den Dokumenttyp aus der primären Interopassembly für Word erweitert.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b7eb29a9cae9e43bd0372088298d2bd6b122c7a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910584"
---
# <a name="document-host-item"></a>Dokument Host Element
  Das <xref:Microsoft.Office.Tools.Word.Document> Hostelement ist ein Typ, der den <xref:Microsoft.Office.Interop.Word.Document> -Typ aus der primären Interopassembly für Word erweitert. Das <xref:Microsoft.Office.Tools.Word.Document> -Hostelement stellt die gleichen Eigenschaften, Methoden und Ereignisse wie ein <xref:Microsoft.Office.Interop.Word.Document> -Objekt bereit, es macht jedoch auch zusätzliche Ereignisse verfügbar und fungiert als Container für Hoststeuerelemente und Windows Forms-Steuerelemente.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 In Projekten auf Dokumentebene gibt es ein <xref:Microsoft.Office.Tools.Word.Document> -Standardhostelement, das das Dokument im Projekt darstellt. In VSTO-Add-In-Projekten können Sie <xref:Microsoft.Office.Tools.Word.Document> -Hostelemente zur Laufzeit generieren.

## <a name="understand-the-document-host-item-in-document-level-projects"></a>Grundlegendes zum Dokument Host Element in Projekten auf Dokument Ebene
 Verwenden Sie die `ThisDocument` -Klasse, um auf das Dokument im Projekt zuzugreifen. Wenn Sie ein Projekt auf Dokumentebene erstellen, generiert Visual Studio die `ThisDocument` -Klasse, die als Kommunikationsverbindung zwischen Word und dem Anpassungscode dient. Über die `ThisDocument` -Klasse erhalten Sie Zugriff auf Member des <xref:Microsoft.Office.Tools.Word.Document> -Hostelements, um grundlegende Aufgaben in der Anpassung auszuführen, z. B. das Ausführen von Code, wenn das Dokument geöffnet bzw. geschlossen wird. Sie können die Klasse auch verwenden, um dem Dokument Steuerelemente hinzuzufügen. Sie können Steuerelemente an Daten binden, Benutzerinformationen abfragen und auf Benutzeraktionen reagieren, indem Sie verschiedene Gruppen von Steuerelementen kombinieren und Code schreiben. Weitere Informationen finden Sie unter [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md).

 Die `ThisDocument` -Klasse stellt einen Ausgangspunkt bereit, an dem Sie mit dem Schreiben von Code im Projekt beginnen können. Da die Klasse die gleichen Eigenschaften, Methoden und Ereignisse wie das <xref:Microsoft.Office.Interop.Word.Document> -Objekt in der primären Interop_Assembly für Word bereitstellt, können Sie auch mit `ThisDocument` auf das Word-Objektmodell zugreifen. Weitere Informationen finden Sie unter [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md).

### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Einschränkungen des Dokument Host Elements in Projekten auf Dokument Ebene
 Ein Projekt auf Dokumentebene kann nur ein <xref:Microsoft.Office.Tools.Word.Document> -Hostelement (die `ThisDocument` -Klasse) enthalten. Sie können dem Projekt zur Entwurfszeit keine neuen <xref:Microsoft.Office.Tools.Word.Document> -Hostelemente hinzufügen, und Sie können zur Laufzeit von einer Anpassung auf Dokumentebene keine neuen <xref:Microsoft.Office.Tools.Word.Document> -Hostelemente erstellen.

 Wenn Sie zur Laufzeit ein neues Word-Dokument erstellen, ist es vom Typ <xref:Microsoft.Office.Interop.Word.Document>. Da es kein Hostelement ist, kann es keine Hoststeuerelemente bzw. Windows Forms-Steuerelemente enthalten. Weitere Informationen zum Erstellen von Dokumenten zur Laufzeit finden Sie unter Gewusst [wie: Programm gesteuertes Erstellen neuer Dokumente](../vsto/how-to-programmatically-create-new-documents.md).

## <a name="understand-document-host-items-in-application-level-projects"></a>Grundlegendes zu Dokument Host Elementen in Projekten auf Anwendungsebene
 In VSTO-Add-In-Projekten können Sie für jedes Dokument, das in Word geöffnet ist, zur Laufzeit ein <xref:Microsoft.Office.Tools.Word.Document> -Hostelement erstellen. Sie können das <xref:Microsoft.Office.Tools.Word.Document> -Hostelement verwenden, um dem zugeordneten Dokument Steuerelemente hinzuzufügen, oder um Ereignisse zu behandeln, die für <xref:Microsoft.Office.Interop.Word.Document> -Objekte nicht verfügbar sind.

 Verwenden Sie zum Generieren eines <xref:Microsoft.Office.Tools.Word.Document>-Hostelements die `GetVstoObject`-Methode. Weitere Informationen finden [Sie unter Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
