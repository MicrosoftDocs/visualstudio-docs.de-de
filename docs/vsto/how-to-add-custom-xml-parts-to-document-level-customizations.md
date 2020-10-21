---
title: 'Gewusst wie: Hinzufügen von benutzerdefinierten XML-Abschnitten zu Anpassungen auf Dokument Ebene'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document-level customizations [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 74bceeeabdaa46e6c1a35b5ab76de6a180d16d53
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "92298453"
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Gewusst wie: Hinzufügen von benutzerdefinierten XML-Abschnitten zu Anpassungen auf Dokument Ebene
  Sie können XML-Daten in einer Microsoft Office Excel-Arbeitsmappe oder in einem Microsoft Office Word-Dokument speichern, indem Sie einen benutzerdefinierten XML-Abschnitt in einer Anpassung auf Dokumentebene erstellen. Weitere Informationen finden Sie unter [Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Visual Studio stellt keine Projekte auf Dokumentebene für Microsoft Office PowerPoint bereit. Weitere Informationen zum Hinzufügen eines benutzerdefinierten XML-Teils zu einer PowerPoint-Präsentation mithilfe eines VSTO-Add-Ins finden Sie unter Gewusst [wie: Hinzufügen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>So fügen Sie einer Excel-Arbeitsmappe ein benutzerdefiniertes XML-Element hinzu

1. Fügen Sie der <xref:Microsoft.Office.Core.CustomXMLPart> -Auflistung in der Arbeitsmappe ein neues <xref:Microsoft.Office.Core.CustomXMLParts> -Objekt hinzu. Die XML-Zeichenfolge, die Sie in der Arbeitsmappe speichern möchten, ist in <xref:Microsoft.Office.Core.CustomXMLPart> enthalten.

     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb#1)]

2. Fügen Sie die `AddCustomXmlPartToWorkbook` -Methode der `ThisWorkbook` -Klasse in einem Projekt auf Dokumentebene für Excel hinzu.

3. Rufen Sie die Methode aus anderem Code in Ihrem Projekt auf. Um z. B. das benutzerdefinierte XML-Element zu erstellen, wenn der Benutzer eine Arbeitsmappe öffnet, rufen Sie die Methode über den `ThisWorkbook_Startup` -Ereignishandler auf.

### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>So fügen Sie einem Word-Dokument ein benutzerdefiniertes XML-Element hinzu

1. Fügen Sie der <xref:Microsoft.Office.Core.CustomXMLPart> -Auflistung im Dokument ein neues <xref:Microsoft.Office.Core.CustomXMLParts> -Objekt hinzu. Die XML-Zeichenfolge, die Sie im Dokument speichern möchten, ist in <xref:Microsoft.Office.Core.CustomXMLPart> enthalten.

     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs#1)]

2. Fügen Sie die `AddCustomXmlPartToDocument` -Methode der `ThisDocument` -Klasse in einem Projekt auf Dokumentebene für Word hinzu.

3. Rufen Sie die Methode aus anderem Code in Ihrem Projekt auf. Um z. B. das benutzerdefinierte XML-Element zu erstellen, wenn der Benutzer ein Dokument öffnet, rufen Sie die Methode über den `ThisDocument_Startup` -Ereignishandler auf.

## <a name="robust-programming"></a>Stabile Programmierung
 Zur Vereinfachung verwendet dieses Beispiel eine XML-Zeichenfolge, die als lokale Variable in der Methode definiert ist. In der Regel sollten Sie den XML-Code aus einer externen Quelle, z. B. einer Datei oder Datenbank, abrufen.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md)
- [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
