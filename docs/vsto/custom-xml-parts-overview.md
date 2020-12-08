---
title: Übersicht über benutzerdefinierte XML-Abschnitte
description: Erfahren Sie, wie Sie XML-Daten für einige Microsoft Office Anwendungen in Dokumente einbetten können. Wenn Sie XML-Daten in ein Dokument einbetten, werden die Daten als ein benutzerdefiniertes XML-Element bezeichnet.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d7998f2a47edd85a65b1e81dd45a046de80d0cdb
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844126"
---
# <a name="custom-xml-parts-overview"></a>Übersicht über benutzerdefinierte XML-Abschnitte
  Sie können XML-Daten für einige Microsoft Office-Anwendungen in Dokumente einbetten. Wenn Sie XML-Daten in ein Dokument einbetten, werden die Daten als *benutzerdefiniertes XML*-Element bezeichnet.

 Sie können benutzerdefinierte XML-Elemente in einem Dokument mithilfe eines VSTO-Add-Ins oder einer Projektmappe auf Dokumentebene in Visual Studio erstellen und ändern. Sie müssen nicht die Microsoft Office-Anwendung starten, um benutzerdefinierte XML-Elemente zu erstellen und zu ändern.

 **Gilt für:** Die Informationen in diesem Thema gelten für Projekte auf Dokument Ebene und VSTO-Add-in-Projekte für Excel, PowerPoint und Word. Weitere Informationen finden Sie unter [verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Visual Studio ermöglicht es Ihnen außerdem, Datenobjekte in Anpassungen auf Dokumentebene zwischenzuspeichern. Diese Funktion unterscheidet sich von benutzerdefinierten XML-Elementen, obwohl es einige Ähnlichkeiten gibt. Weitere Informationen finden Sie unter [zwischengespeicherte Daten in Anpassungen auf Dokument Ebene](../vsto/cached-data-in-document-level-customizations.md).

## <a name="understand-custom-xml-parts"></a>Verstehen benutzerdefinierter XML-Elemente
 Benutzerdefinierte XML-Elemente wurden in Microsoft Office System 2007 zusammen mit den Open XML-Formaten eingeführt. Diese Formate enthalten neue XML-basierte Dateiformate für Excel, PowerPoint und Word (z *. b.. xlsx*, *. pptx* und *. docx*). Dokumente in diesen Formaten bestehen aus XML-Dateien (auch als *XML-Teile* bezeichnet), die in Ordnern in einem ZIP-Archiv angeordnet sind. Die meisten der XML-Elemente sind integrierte Elemente, mit deren Hilfe die Struktur und der Status des Dokuments definiert werden. Allerdings können Dokumente auch benutzerdefinierte XML-Elemente enthalten, die Sie verwenden können, um beliebige XML-Daten in den Dokumenten zu speichern.

 Die XML-Dateiformate ermöglichen es Anwendungen, mit Dokumenten auf eine Weise zu arbeiten, die mit den älteren Binärdatei Formaten (z *. b.. xls*, *. ppt* und *. doc*) nicht möglich ist. Jede Anwendung, die ZIP-Archive lesen kann, kann den Inhalt der Dokumente untersuchen und ändern, auch wenn Microsoft Office nicht installiert ist.

 Weitere Informationen zur Struktur von Open XML und benutzerdefinierten XML-Elementen finden Sie in den folgenden Artikeln:

- [Einführung in das Office (2007) Open XML-Dateiformat](/previous-versions/office/developer/office-2007/aa338205(v=office.12))

- [Gewusst wie: Bearbeiten von Dokumenten im Open XML-Format](/previous-versions/office/developer/office-2007/aa982683(v=office.12))

- [Exemplarische Vorgehensweise: Word 2007 XML-Format](/previous-versions/office/developer/office-2007/bb266220(v=office.12))

- [Erstellen von Word 2007-Dokumenten mit Open XML-Formaten](/previous-versions/office/developer/office-2007/bb264572(v=office.12))

> [!NOTE]
> Excel, Word und PowerPoint ermöglichen auch die Verwendung benutzerdefinierter XML-Elemente in Dokumenten, die in den binären Dateiformaten gespeichert werden. Wenn ein Dokument in einem binären Format gespeichert wird, können Sie benutzerdefinierte XML-Elemente jedoch nicht hinzufügen oder ändern, ohne die jeweilige Microsoft Office-Anwendung zu starten.

## <a name="create-and-modify-custom-xml-parts"></a>Erstellen und Ändern von benutzerdefinierten XML-Elementen
 Sie können benutzerdefinierte XML-Elemente erstellen oder ändern, wenn das Dokument in der Office-Anwendung geöffnet ist oder wenn das Dokument geschlossen ist – selbst dann, wenn Microsoft Office nicht installiert ist.

### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Ändern von XML-Teilen während der Ausführung der Office-Anwendung
 Sie können mit benutzerdefinierten XML-Elementen arbeiten, indem Sie eine Anpassung auf Dokument Ebene oder ein VSTO-Add-in verwenden. Wenn Sie eine Anpassung auf Dokumentebene verwenden, arbeiten Sie in der Regel mit benutzerdefinierten XML-Elementen, die sich im angepassten Dokument befinden. Wenn Sie ein VSTO-Add-in verwenden, können Sie benutzerdefinierte XML-Elemente in jedem Dokument erstellen oder ändern, das in der Anwendung geöffnet ist.

 Wenn Sie ein benutzerdefiniertes XML-Element mit Visual Studio erstellen möchten, fügen Sie der Auflistung  <xref:Microsoft.Office.Core.CustomXMLParts> im Dokument ein neues <xref:Microsoft.Office.Core.CustomXMLPart>-Objekt hinzu. Weitere Informationen finden Sie unter den folgenden Themen:

- [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Abschnitten zu Anpassungen auf Dokument Ebene](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)

- [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)

### <a name="modify-xml-parts-without-starting-the-office-application"></a>Ändern von XML-Teilen ohne Starten der Office-Anwendung
 Sie können ein benutzerdefiniertes XML-Element hinzufügen oder ändern, ohne Excel, PowerPoint oder Word zu starten. Dies ist hilfreich, wenn Sie mit XML-Daten in einem Dokument auf einem Computer arbeiten möchten, auf dem keine Microsoft Office-Anwendungen installiert sind (z. B. auf einem Server).

 Wenn Sie ein benutzerdefiniertes XML-Element hinzufügen möchten, ohne Microsoft Office zu starten, verwenden Sie Klassen im Open XML SDK. Diese Klassen bieten Zugriff auf Open XML-Inhalt, der für Office-Dokumente spezifisch ist. Wenn Sie z. b. einer Excel-Arbeitsmappe ein benutzerdefiniertes XML-Element hinzufügen möchten, verwenden Sie die- <xref:DocumentFormat.OpenXml.Packaging.OpenXmlPartContainer.AddNewPart%2A> Methode eines- <xref:DocumentFormat.OpenXml.Packaging.WorkbookPart> Objekts. Weitere Informationen finden Sie unter [Open XML SDK](/office/open-xml/open-xml-sdk).

## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Binden benutzerdefinierter XML-Elemente an Word-Inhalts Steuerelemente
 Sie können Inhaltssteuerelemente in einer Word-Projektmappe an Elemente in einem benutzerdefinierten XML-Element binden. Wenn ein Inhaltssteuerelement an ein benutzerdefiniertes XML-Element gebunden ist, werden die Daten im benutzerdefinierten XML-Element in der Benutzeroberfläche (User Interface, UI) des Inhaltssteuerelements angezeigt. Wenn ein Benutzer Text im Steuerelement bearbeitet, werden die entsprechenden XML-Elemente automatisch aktualisiert. Wenn Elementwerte in den benutzerdefinierten XML-Elementen geändert werden, zeigen die Inhaltssteuerelemente, die an die XML-Elemente gebunden sind, auf ähnliche Weise die neuen Daten an. Weitere Informationen finden Sie unter [Inhalts Steuerelemente](../vsto/content-controls.md).

## <a name="see-also"></a>Siehe auch
- [XML-Schemas und-Daten in Anpassungen auf Dokument Ebene](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
- [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Abschnitten zu Anpassungen auf Dokument Ebene](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)
- [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)
- [Inhalts Steuerelemente](../vsto/content-controls.md)
- [Exemplarische Vorgehensweise: Binden von Steuerelementen an benutzerdefinierte XML-Elemente](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)
