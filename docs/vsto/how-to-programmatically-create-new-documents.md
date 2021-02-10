---
title: 'Gewusst wie: Programm gesteuertes Erstellen neuer Dokumente'
description: Erfahren Sie, wie Sie Programm gesteuert neue Dokumente in Microsoft Word mithilfe von Visual Studio erstellen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e9ff98654da8d7125ecf788fadc9cbf7ff4bdfc7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964068"
---
# <a name="how-to-programmatically-create-new-documents"></a>Gewusst wie: Programm gesteuertes Erstellen neuer Dokumente
  Wenn Sie ein Dokument programmgesteuert erstellen, ist das neue Dokument ein systemeigenes <xref:Microsoft.Office.Interop.Word.Document>-Objekt. Dieses Objekt verfügt nicht über die zusätzlichen Ereignisse und Datenbindungsfunktionen eines <xref:Microsoft.Office.Tools.Word.Document>-Hostelements. Weitere Informationen finden Sie Unterprogramm gesteuerte [Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Wenn Sie ein Projekt auf Dokumentebene entwickeln, können Sie Ihrem Projekt nicht programmgesteuert <xref:Microsoft.Office.Tools.Word.Document>-Hostelemente hinzufügen. In einem VSTO-Add-In-Projekt können Sie beliebige <xref:Microsoft.Office.Interop.Word.Document>-Objekte zur Laufzeit in <xref:Microsoft.Office.Tools.Word.Document>-Hostelements konvertieren. Weitere Informationen finden [Sie unter Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-document-based-on-the-normal-template"></a>So erstellen Sie ein neues Dokument basierend auf der Vorlage "NORMAL.DOT"

- Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> der Auflistung <xref:Microsoft.Office.Interop.Word.Documents> zum Erstellen eines neuen Dokuments auf der Grundlage der Vorlage "NORMAL.DOT". Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#1)]
     [!code-csharp[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#1)]

## <a name="use-custom-templates"></a>Verwenden von benutzerdefinierten Vorlagen
 Die- <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> Methode verfügt über ein optionales *Vorlagen* Argument zum Erstellen eines neuen Dokuments, das auf einer anderen Vorlage als der normalen Vorlage basiert. Sie müssen den Dateinamen und den vollqualifizierten Pfad der Vorlage angeben.

### <a name="to-create-a-new-document-based-on-a-custom-template"></a>So erstellen Sie ein neues Dokument basierend auf einer benutzerdefinierten Vorlage

- Rufen Sie die Methode <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> der Auflistung <xref:Microsoft.Office.Interop.Word.Documents> auf, und geben Sie den Pfad zur Vorlage an. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#2)]
     [!code-csharp[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#2)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
