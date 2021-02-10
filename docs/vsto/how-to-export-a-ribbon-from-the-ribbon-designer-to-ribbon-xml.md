---
title: 'Gewusst wie: Exportieren eines Menübands aus dem Menüband-Designer in Menüband-XML'
description: Erfahren Sie, wie Sie das Menüband anpassen können, um das Menüband aus dem Designer in Menüband-XML zu exportieren und das XML direkt zu bearbeiten.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2a0511fd103345859f96b18f333465106505057a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953980"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Gewusst wie: Exportieren eines Menübands aus dem Menüband-Designer in Menüband-XML
  Das Element " **Menüband (visueller Designer)** " unterstützt nicht alle möglichen Typen der Menü Band Anpassung. Um das Menüband auf Erweiterte Weise anzupassen, können Sie das Menüband aus dem Designer in Menüband-XML exportieren und den XML-Code direkt bearbeiten.

> [!NOTE]
> Nicht alle Eigenschaftswerte werden in der Menüband-XML-Datei angezeigt. Weitere Informationen finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>So exportieren Sie ein Menüband aus dem Menüband-Designer in die Multifunktionsleiste

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf die Menüband-Codedatei, und klicken Sie dann auf **Designer anzeigen**

2. Klicken Sie mit der rechten Maustaste auf den Menüband-Designer, und klicken Sie dann auf **Menüband in XML**

     Visual Studio fügt dem Projekt eine Menüband-XML-Datei und eine Menüband-XML-Codedatei hinzu.

3. Suchen Sie in der Menüband-Code Klasse nach den Kommentaren, die mit beginnen `TODO:` .

4. Kopieren Sie den Codeblock in diesen Kommentaren abhängig vom Typ der Lösung, die Sie entwickeln, in die **ThisAddIn**-, **ThisWorkbook**-oder **ThisDocument** -Klasse.

     Dieser Code ermöglicht der Microsoft Office Anwendung das ermitteln und Laden Ihres benutzerdefinierten Menübands. Weitere Informationen finden Sie unter [Ribbon XML](../vsto/ribbon-xml.md).

5. Heben Sie die Auskommentierung des Codeblocks in der **ThisAddIn**-, **ThisWorkbook**-oder **ThisDocument** -Klasse auf.

     Nachdem Sie die Auskommentierung des Codes aufheben, sollte er dem folgenden Beispiel ähneln. In diesem Beispiel wird die Menü bandklasse aufgerufen `MyRibbon` .

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. Wechseln Sie zur Menüband-XML-Codedatei, und suchen Sie nach der `Ribbon Callbacks` Region.

     Hier schreiben Sie Rückruf Methoden, um Benutzeraktionen wie das Klicken auf eine Schaltfläche zu behandeln.

7. Erstellen Sie eine Rückruf Methode für jeden Ereignishandler, den Sie im Menüband-Designer-Code geschrieben haben.

8. Verschieben Sie den gesamten Ereignishandlercode aus den Ereignis Handlern in die Rückruf Methoden, und ändern Sie den Code so, dass er mit dem Programmiermodell der Multifunktionsleisten-Erweiterbarkeit (RibbonX) verwendet werden kann.

     Weitere Informationen zum Schreiben von Rückruf Methoden und zum Verwenden des RibbonX-Programmiermodells finden Sie unter [Menüband-XML](../vsto/ribbon-xml.md).

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
