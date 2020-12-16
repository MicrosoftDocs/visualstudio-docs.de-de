---
title: XMLNode-Steuerelement
description: Erfahren Sie, dass das XMLNode-Steuerelement ein zugeordnetes XML-Knoten Objekt ist, das Ereignisse verfügbar macht und an Daten gebunden werden kann.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 58f9c5db883f55c00236bc202797dcf2ec3003f6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528343"
---
# <a name="xmlnode-control"></a>XMLNode-Steuerelement
  **Wichtig** Die Informationen, die in diesem Thema in Bezug auf Microsoft Word beschrieben werden, werden exklusiv für den Vorteil und die Verwendung von Einzelpersonen und Organisationen präsentiert, die sich außerhalb der USA und ihrer Gebiete befinden oder Programme verwenden, die unter, Microsoft Word-Produkte, die von Microsoft vor Januar 2010 lizenziert wurden Diese Informationen zu Microsoft Word werden möglicherweise nicht von Einzelpersonen oder Organisationen in den USA oder deren Territorien gelesen oder verwendet, die von Microsoft Word-Produkten verwendet werden, die nach dem 10. Januar 2010 von Microsoft lizenziert wurden. Diese Produkte Verhalten sich nicht identisch mit Produkten, die vor diesem Datum lizenziert sind, oder für die Verwendung außerhalb der USA lizenziert und lizenziert wurden.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Das <xref:Microsoft.Office.Tools.Word.XMLNode> -Steuerelement ist ein zugeordnetes XML-Knoten Objekt, das Ereignisse verfügbar macht und an Daten gebunden werden kann. Das- <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement wird nur erstellt, wenn ein nicht wiederholtes Schema Element einem Microsoft Office Word-Dokument zugeordnet ist. Nachdem Visual Studio den XML-Knoten erstellt hat, können Sie ihn direkt programmieren, ohne das Word-Objektmodell durchlaufen zu müssen.

 Das- <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement kann nur gelöscht werden, indem die Element Zuordnung in Word entfernt wird.

## <a name="bind-data-to-the-control"></a>Binden von Daten an das Steuerelement
 Ein- <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement unterstützt die einfache Datenbindung. Der XML-Knoten sollte mithilfe der-Eigenschaft an eine Datenquelle gebunden werden <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> . Wenn die Daten im gebundenen DataSet aktualisiert werden, spiegelt das <xref:Microsoft.Office.Tools.Word.XMLNode> -Steuerelement die Änderungen wider.

## <a name="formatting"></a>Formatierung
 Die Formatierung, die auf ein-Objekt angewendet werden kann, <xref:Microsoft.Office.Interop.Word.XMLNode> kann auf ein-Steuerelement angewendet werden <xref:Microsoft.Office.Tools.Word.XMLNode> . Dies schließt Schriftarten, unterstrich Stile und Zeichenstile ein.

## <a name="events"></a>Ereignisse
 Die folgenden Ereignisse sind für das <xref:Microsoft.Office.Tools.Word.XMLNode> -Steuerelement verfügbar:

- <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>

## <a name="compare-events"></a>Vergleichen von Ereignissen
 Sie können ein Ereignis erfassen, wenn der Benutzer den Cursor innerhalb des Kontexts eines bestimmten Steuer Elements verschiebt <xref:Microsoft.Office.Tools.Word.XMLNode> . Angenommen, Sie verfügen über ein-Steuerelement mit dem Namen, <xref:Microsoft.Office.Tools.Word.XMLNode> `Customer` das über ein untergeordnetes Steuerelement mit dem <xref:Microsoft.Office.Tools.Word.XMLNode> Namen verfügt `Company` und über zwei untergeordnete Steuerelemente mit dem `Company` <xref:Microsoft.Office.Tools.Word.XMLNode> Namen `CompanyName` und `CompanyRegion`

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Wenn Sie ein Steuerelement im Aktionsbereich anzeigen möchten, wenn der Cursor in den Knoten verschoben wird `Company` , sollte es keine Rolle spielen, ob der Cursor in oder eingefügt wird, `CompanyName` `CompanyRegion` da beide im Kontext von liegen `Company` . In diesem Fall können Sie den Code im- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> Ereignis von schreiben `Company` .

 In den meisten Fällen <xref:Microsoft.Office.Tools.Word.XMLNode> <xref:Microsoft.Office.Tools.Word.XMLNode.Select> werden das-Ereignis und das-Ereignis ausgelöst, wenn der Cursor in ein-Steuerelement eintritt <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> . In der folgenden Tabelle werden die Unterschiede zwischen diesen Ereignissen angezeigt.

|Ereignis auswählen|ContextEnter-Ereignis|
|------------------|------------------------|
|Tritt ein, wenn sich der Cursor in einem befindet <xref:Microsoft.Office.Tools.Word.XMLNode> .|Wird ausgelöst, wenn der Cursor ausgehend von einem Bereich außerhalb des Knotenkontexts in einen <xref:Microsoft.Office.Tools.Word.XMLNode> oder von ihm abgeleiteten Knoten platziert wird. Das heißt, es wird nur ausgelöst, wenn der Kontext geändert wird.|

 Wenn Sie z. b. den Cursor von außerhalb von `Customer` in bewegen `CompanyName` , <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> wird das `Customer` -Ereignis für, `Company` und `CompanyName` ausgelöst. Wenn Sie den Cursor dann von `CompanyName` in bewegen `CompanyRegion` , wird nur das- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> Ereignis für `CompanyRegion` ausgelöst, da Sie sich immer noch im Kontext von `Company` und befinden `Customer` .

 Die gleichen Unterschiede bestehen zwischen dem <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> Ereignis und dem <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> Ereignis.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNodes-Steuerelement](../vsto/xmlnodes-control.md)
- [Gewusst wie: Hinzufügen von XMLNode-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Gewusst wie: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
