---
title: Übersicht über Menüband
description: Erfahren Sie, wie Sie mit dem Menüband verwandte Befehle organisieren können, damit Sie leichter zu finden sind und wie Befehle als Steuerelemente auf dem Menüband angezeigt werden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, multiple Ribbons
- Ribbon [Office development in Visual Studio], about Ribbon
- toolbars [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], multiple Ribbons
- toolbars [Office development in Visual Studio]
- custom Ribbon, multiple Ribbons
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2eff346425dca31cb88342e69701a229de2b80ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940864"
---
# <a name="ribbon-overview"></a>Übersicht über Menüband
  Das Menüband ist eine Möglichkeit, verwandte Befehle so zu organisieren, dass Sie leichter zu finden sind. Befehle werden als Steuerelemente auf dem Menüband angezeigt. Steuerelemente sind in *Gruppen* entlang eines horizontalen Streifens am oberen Rand eines Anwendungsfensters angeordnet. Verwandte Gruppen sind auf Registerkarten organisiert.

 Auf die meisten Funktionen, auf die in früheren Versionen des Microsoft Office Systems mithilfe von Menüs und Symbolleisten zugegriffen wurde, kann jetzt über das Menüband zugegriffen werden. Weitere Informationen finden Sie im technischen Artikel [Developer Overview of the User Interface for the 2007 Microsoft Office System](/previous-versions/office/developer/office-2007/aa338198(v=office.12)).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="customize-the-microsoft-office-ribbon"></a>Anpassen des Microsoft Office Menübands
 Fügen Sie dem Office-Projekt eines der folgenden Menü Band Elemente hinzu, um das Menüband anzupassen:

- **Menüband (Visueller Designer)**

- **Menüband (XML)**

  Zum Anpassen des Excel-Menübands fügen Sie dem Excel-VSTO-Add-In-Projekt beispielsweise ein Menübandelement hinzu.

### <a name="ribbon-visual-designer-item"></a>Menüband (visueller Designer) Element
 Das Element " **Menüband (visueller Designer)** " bietet erweiterte Tools, die Ihnen das Entwerfen und entwickeln eines benutzerdefinierten Menübands erleichtern. Verwenden Sie das Element **Menüband (visueller Designer)** , um das Menüband auf folgende Weisen anzupassen:

- Hinzufügen benutzerdefinierter oder integrierter Registerkarten zu einem Menüband.

- Fügen Sie einer benutzerdefinierten oder integrierten Registerkarte benutzerdefinierte Gruppen hinzu.

  > [!NOTE]
  > Eine integrierte Registerkarte oder Gruppe ist eine, die bereits auf dem Menüband einer Microsoft Office Anwendung vorhanden ist. Beispielsweise ist die Registerkarte " **Daten** " eine integrierte Registerkarte in Excel. Die Gruppe **Verbindungen** ist eine integrierte Gruppe auf der Registerkarte **Daten** .

- Fügen Sie einer benutzerdefinierten Gruppe benutzerdefinierte Steuerelemente hinzu.

- Fügen Sie der Backstage-Ansicht benutzerdefinierte Steuerelemente hinzu.

  Weitere Informationen zum Anpassen eines Menübands mithilfe des Elements **Menüband (visueller Designer)** finden Sie unter [Menüband-Designer](../vsto/ribbon-designer.md).

### <a name="ribbon-xml-item"></a>Menüband (XML)-Element
 Verwenden Sie das Element **Menüband (XML)** , wenn Sie das Menüband auf eine Weise anpassen möchten, die vom Element **Menüband (visueller Designer)** nicht unterstützt wird. Verwenden Sie das Element **Menüband (XML)** , um das Menüband auf folgende Weisen anzupassen:

- Fügen Sie *integrierte* Gruppen zu einer benutzerdefinierten Registerkarte oder integrierten Registerkarte hinzu.

- Fügen Sie einer benutzerdefinierten Gruppe integrierte Steuerelemente hinzu.

- Fügen Sie benutzerdefinierten Code hinzu, um die Ereignishandler integrierter Steuerelemente zu überschreiben.

- Passen Sie die Symbolleiste für den Schnellzugriff an.

- Geben Sie eine Menübandanpassung zwischen VSTO-Add-Ins mithilfe einer qualifizierten ID frei.

  Weitere Informationen zum Anpassen des Menübands mithilfe des Elements **Menüband (XML)** finden Sie unter [Menüband-XML](../vsto/ribbon-xml.md).

## <a name="export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Exportieren eines Menübands aus dem Menüband-Designer in Menüband-XML
 Wenn Sie ein Menüband mithilfe des Menüband-Designers erstellen und dann festlegen, dass Sie das Menüband auf eine Weise anpassen möchten, die vom Element " **Menüband (visueller Designer)** " nicht unterstützt wird, können Sie das Menüband nach XML exportieren.

 Visual Studio erstellt automatisch ein **Menüband (XML)** -Element und füllt die Menüband-XML-Datei mit Elementen und Attributen für jedes Steuerelement auf dem Menüband auf.

 Nicht alle Eigenschaften im Fenster **Eigenschaften** des Menüband-Designers werden in die Menüband-XML-Datei übertragen.  Beispielsweise wird der Wert der **Image** -oder **Text** -Eigenschaft von Visual Studio nicht exportiert. Hierfür müssen Sie eine Rückrufmethode in der Menüband-Codedatei des exportierten Projekts erstellen, um ein Bild zuzuweisen oder den Text eines Steuerelements festzulegen. Visual Studio generiert im Rahmen des Exportvorgangs keine automatischen Rückrufmethoden.

 Darüber hinaus werden alle nicht geänderten Standardeigenschaftswerte nicht in der resultierenden Menüband-XML-Datei angezeigt.

 Weitere Informationen zum Exportieren des Menübands in XML finden Sie unter Gewusst [wie: Exportieren eines Menübands aus dem Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="update-the-code"></a>Aktualisieren des Codes
 **Projektmappen-Explorer** wird eine neue Menüband-Codedatei hinzugefügt. Diese Datei enthält die Menüband-XML-Klasse. Sie müssen Rückrufmethoden im `Ribbon Callbacks`-Bereich dieser Klasse erstellen, um Benutzeraktionen wie das Klicken auf eine Schaltfläche zu behandeln. Verschieben Sie den Code aus den Ereignishandlern in die Rückrufmethoden, und ändern Sie den Code, damit er mit dem Programmmodell für die Menübanderweiterung (RibbonX) verwendet werden kann. Weitere Informationen finden Sie unter [Ribbon XML](../vsto/ribbon-xml.md).

 Sie müssen den Code auch den Klassen `ThisAddIn`, `ThisWorkbook` oder `ThisDocument` hinzufügen, durch die die `CreateRibbonExtensibilityObject`-Methode überschrieben und die Menüband-XML-Klasse an die Office-Anwendung zurückgegeben wird.

 Weitere Informationen finden Sie unter [Ribbon XML](../vsto/ribbon-xml.md).

## <a name="add-multiple-ribbon-items-to-a-project"></a>Hinzufügen mehrerer Menü Band Elemente zu einem Projekt
 Sie können einem einzelnen Projekt mehrere Menübandelemente hinzufügen. Dies ist hilfreich, wenn Sie eine der folgenden Aufgaben ausführen möchten:

- Erstellen von Multifunktionsleisten für Outlook- *Inspektoren*. Weitere Informationen finden Sie unter [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

    > [!NOTE]
    > Ein Inspektor ist ein Fenster, das geöffnet wird, wenn der Benutzer bestimmte Aufgaben ausführt, z. B. eine E-Mail verfasst.

- Wählen Sie aus, welches Menüband zur Laufzeit angezeigt werden soll.

### <a name="select-which-ribbons-to-display-at-run-time"></a>Wählen Sie aus, welche Menü Bänder zur Laufzeit angezeigt werden.
 Da ein Projekt mehr als eine Multifunktionsleiste enthalten kann, können Sie auswählen, welches Menüband zur Laufzeit angezeigt werden soll.

 Wenn Sie ein Menüband zur Laufzeit auswählen möchten, überschreiben Sie die `CreateRibbonExtensibilityObject` -Methode in der `ThisAddin` -,- `ThisWorkbook` oder `ThisDocument` -Klasse Ihres Projekts, und geben Sie das Menüband zurück, das Sie anzeigen möchten. Im folgenden Beispiel wird der Wert eines Felds mit dem Namen überprüft `myCondition` und das entsprechende Menüband zurückgegeben.

> [!NOTE]
> Die in diesem Beispiel verwendete Syntax gibt eine Multifunktionsleiste zurück, die mit dem Element **Menüband (visueller Designer)** erstellt wurde. Die Syntax zum Zurückgeben eines Menübands, das mit einem **Menüband (XML)** -Element erstellt wird, unterscheidet sich geringfügig. Weitere Informationen zum Zurückgeben eines Elements im **Menüband (XML)** finden Sie unter [Menüband-XML](../vsto/ribbon-xml.md).

 Fügen Sie den folgenden Code hinzu:

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_Ribbon_choose_Ribbon_4/ThisWorkbook.cs#1)]

### <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Gewusst wie: Starten der Anpassung des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)|Zeigt, wie Sie das Menüband einer Microsoft Office-Anwendung anpassen und einem Office-Projekt ein **Menüband (visueller Designer)** oder ein **Menüband (XML)** -Element hinzufügen.|
|[Menüband-Designer](../vsto/ribbon-designer.md)|Beschreibt, wie Sie mit dem Menüband-Designer dem Menüband einer Microsoft Office Anwendung benutzerdefinierte Registerkarten, Gruppen und Steuerelemente hinzufügen können.|
|[Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Veranschaulicht die Erstellung einer benutzerdefinierten Menüband-Registerkarte mithilfe des Menüband-Designers. Sie können den Menüband-Designer verwenden, um der benutzerdefinierten Registerkarte Steuerelemente hinzuzufügen und diese zu positionieren.|
|[Übersicht über das Ribbon-Objektmodell](../vsto/ribbon-object-model-overview.md)|Bietet eine Übersicht des Objektmodells mit starker Typisierung, das Sie zum Abrufen und Festlegen der Eigenschaften von Menübandsteuerelementen zur Laufzeit verwenden können.|
|[Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente auf einem Menüband zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Veranschaulicht die Verwendung des Menüband-Objektmodells zum Aktualisieren der Steuerelemente auf einem Menüband, nachdem das Menüband in die Office-Anwendung geladen wurde.|
|[Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Enthält Anleitungen zur Anpassung des Menübands in Microsoft Office Outlook.|
|[Anpassen eines Menübands für InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Enthält Anleitungen zur Anpassung des Menübands in Microsoft Office InfoPath.|
|[Zugreifen auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)|Veranschaulicht das anzeigen, ausblenden und Ändern des Menübands und das Ausführen des Codes von Steuerelementen in einem benutzerdefinierten Aufgabenbereich, Aktionsbereich oder Outlook-Formular Bereich.|
|[Vorgehensweise: Ändern der Position einer Registerkarte im Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Zeigt, wie die Reihenfolge von Registerkarten auf einem Menüband geändert wird.|
|[Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)|Veranschaulicht das Hinzufügen von Gruppen und Steuerelementen zu einer integrierten Registerkarte.|
|[Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)|Veranschaulicht das Hinzufügen von Steuerelementen zum Menü, das geöffnet wird, wenn Sie auf die **Datei** klicken.|
|[Gewusst wie: Hinzufügen eines Dialogfeld-Start Programms zu einer Menü Bandgruppe](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Zeigt, wie einem Dialogfeld-Start Programm eine beliebige Gruppe auf einem Menüband hinzugefügt wird.|
|[Gewusst wie: Exportieren eines Menübands aus dem Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Zeigt, wie Sie das Menüband auf Erweiterte Weise anpassen, indem Sie das Menüband aus dem Designer in Menüband-XML exportieren.|
|[Ribbon XML](../vsto/ribbon-xml.md)|Erläutert, wie Sie ein Menüband mithilfe von Menüband-XML anpassen können.|
|[Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Veranschaulicht, wie eine benutzerdefinierte Registerkarte des Menübands mithilfe des Elements **Menüband (XML)** erstellt wird.|
