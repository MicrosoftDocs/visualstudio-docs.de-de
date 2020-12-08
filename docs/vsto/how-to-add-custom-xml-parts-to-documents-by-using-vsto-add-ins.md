---
title: Hinzufügen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-ins
description: Erfahren Sie, wie Sie XML-Daten in den folgenden Dokumenttypen speichern können, indem Sie ein benutzerdefiniertes XML-Element in einem VSTO-Add-in erstellen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1b153fe3e7c68ed6a8288ff69a30e16dd32c448a
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847714"
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Gewusst wie: Hinzufügen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-ins
  Sie können XML-Daten in folgenden Dokumenttypen speichern, indem Sie ein benutzerdefiniertes XML-Element in einem VSTO-Add-In erstellen:

- Microsoft Office Excel-Arbeitsmappe

- Microsoft Office Word-Dokument

- Microsoft Office PowerPoint-Präsentation

  Weitere Informationen finden Sie unter [Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md).

  **Betrifft:** Die Informationen in diesem Thema betreffen Projekte auf Anwendungsebene für Excel, PowerPoint und Word. Weitere Informationen finden Sie unter [verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).

## <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>So fügen Sie einer Excel-Arbeitsmappe ein benutzerdefiniertes XML-Element hinzu

1. Fügen Sie der <xref:Microsoft.Office.Core.CustomXMLPart> -Auflistung in der Arbeitsmappe ein neues <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> -Objekt hinzu. Die XML-Zeichenfolge, die Sie in der Arbeitsmappe speichern möchten, ist in <xref:Microsoft.Office.Core.CustomXMLPart> enthalten.

     Im folgenden Codebeispiel wird einer angegebenen Arbeitsmappe ein benutzerdefiniertes XML-Element hinzugefügt.

     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]

2. Fügen Sie der- `AddCustomXmlPartToWorkbook` `ThisAddIn` Klasse in einem VSTO-Add-in-Projekt für Excel die-Methode hinzu.

3. Rufen Sie die Methode aus anderem Code in Ihrem Projekt auf. Um das benutzerdefinierte XML-Element beispielsweise zu erstellen, wenn der Benutzer eine Arbeitsmappe öffnet, rufen Sie die Methode von einem Ereignishandler für das <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> -Ereignis auf.

## <a name="to-add-a-custom-xml-part-to-a-word-document"></a>So fügen Sie einem Word-Dokument ein benutzerdefiniertes XML-Element hinzu

1. Fügen Sie der <xref:Microsoft.Office.Core.CustomXMLPart> -Auflistung im Dokument ein neues <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> -Objekt hinzu. Die XML-Zeichenfolge, die Sie im Dokument speichern möchten, ist in <xref:Microsoft.Office.Core.CustomXMLPart> enthalten.

     Im folgenden Codebeispiel wird einem angegebenen Dokument ein benutzerdefiniertes XML-Element hinzugefügt.

     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]

2. Fügen Sie die-Methode der- `AddCustomXmlPartToDocument` `ThisAddIn` Klasse in einem VSTO-Add-in-Projekt für Word hinzu.

3. Rufen Sie die Methode aus anderem Code in Ihrem Projekt auf. Um das benutzerdefinierte XML-Element beispielsweise zu erstellen, wenn der Benutzer ein Dokument öffnet, rufen Sie die Methode von einem Ereignishandler für das <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> -Ereignis auf.

## <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>So fügen Sie einer PowerPoint-Präsentation ein benutzerdefiniertes XML-Element hinzu

1. Fügen Sie <xref:Microsoft.Office.Core.CustomXMLPart> der [Microsoft.Office.Interop.PowerPoint._Presentation. CustomXMLParts](/previous-versions/office/developer/office-2010/ff760806%28v%3doffice.14%29) -Auflistung in der Präsentation ein neues-Objekt hinzu. Die XML-Zeichenfolge, die Sie in der Präsentation speichern möchten, ist in <xref:Microsoft.Office.Core.CustomXMLPart> enthalten.

     Im folgenden Codebeispiel wird einer angegebenen Präsentation ein benutzerdefiniertes XML-Element hinzugefügt.

     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]

2. Fügen Sie die-Methode der- `AddCustomXmlPartToPresentation` `ThisAddIn` Klasse in einem VSTO-Add-in-Projekt für PowerPoint hinzu.

3. Rufen Sie die Methode aus anderem Code in Ihrem Projekt auf. Um z. b. das benutzerdefinierte XML-Element zu erstellen, wenn der Benutzer eine Präsentation öffnet, rufen Sie die-Methode von einem Ereignishandler für das [Microsoft.Office.Interop.PowerPoint.EApplication_Event. AfterPresentationOpen](/previous-versions/office/developer/office-2010/ff762843(v=office.14)) -Ereignis auf.

## <a name="robust-programming"></a>Stabile Programmierung
 Zur Vereinfachung verwendet dieses Beispiel eine XML-Zeichenfolge, die als lokale Variable in der Methode definiert ist. In der Regel sollten Sie den XML-Code aus einer externen Quelle, z. B. einer Datei oder Datenbank, abrufen.

## <a name="see-also"></a>Siehe auch
- [Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md)
- [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Abschnitten zu Anpassungen auf Dokument Ebene](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
