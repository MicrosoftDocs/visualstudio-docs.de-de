---
title: XMLNodes-Steuerelement
description: Erfahren Sie, dass das XMLNodes-Steuerelement nur erstellt wird, wenn ein sich wiederholendes Schema Element einem Microsoft Word-Dokument zugeordnet ist.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d920df609c8172b6329cac537d10868e5795be12
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894386"
---
# <a name="xmlnodes-control"></a>XMLNodes-Steuerelement
  **Wichtig** Die Informationen, die in diesem Thema in Bezug auf Microsoft Word beschrieben werden, werden exklusiv für den Vorteil und die Verwendung von Einzelpersonen und Organisationen präsentiert, die sich außerhalb der USA und ihrer Gebiete befinden oder Programme verwenden, die unter, Microsoft Word-Produkte, die von Microsoft vor Januar 2010 lizenziert wurden Diese Informationen zu Microsoft Word werden möglicherweise nicht von Einzelpersonen oder Organisationen in den USA oder deren Territorien gelesen oder verwendet, die von Microsoft Word-Produkten verwendet werden, die nach dem 10. Januar 2010 von Microsoft lizenziert wurden. Diese Produkte Verhalten sich nicht identisch mit Produkten, die vor diesem Datum lizenziert sind, oder für die Verwendung außerhalb der USA lizenziert und lizenziert wurden.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Das- <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement ist eine Sammlung von zugeordneten XML-Knoten Objekten, die Ereignisse verfügbar macht. Das- <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement wird nur erstellt, wenn ein sich wiederholendes Schema Element einem Microsoft Office Word-Dokument zugeordnet ist. Wenn das sich wiederholende Element untergeordnete Elemente enthält, wird jedes der untergeordneten Elemente ebenfalls als-Steuerelement erstellt <xref:Microsoft.Office.Tools.Word.XMLNodes> .

 Nachdem Visual Studio die Auflistung von XML-Knoten erstellt hat, können Sie das Steuerelement direkt programmieren, ohne das Word-Objektmodell durchlaufen zu müssen. Das- <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement kann nur gelöscht werden, indem die Element Zuordnung aus dem Dokument entfernt wird.

> [!NOTE]
> Wenn Sie über die-Eigenschaft auf ein untergeordnetes Element des-Steuer Elements zugreifen <xref:Microsoft.Office.Tools.Word.XMLNodes> <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> , wird ein- <xref:Microsoft.Office.Interop.Word.XMLNode> Objekt anstelle eines-Steuer Elements zurückgegeben <xref:Microsoft.Office.Tools.Word.XMLNode> . Weitere Informationen finden Sie Unterprogramm gesteuerte [Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="bind-data-to-the-control"></a>Binden von Daten an das Steuerelement
 Ein- <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement unterstützt keine Datenbindung. Dies liegt daran, dass das <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement keine komplexen Daten Bindungsfunktionen hat und die einfache Datenbindung keine sich wiederholenden Daten darstellen kann.

## <a name="formatting"></a>Formatierung
 Jede Formatierung, die auf Text im Dokument angewendet werden kann, kann auf ein-Steuerelement angewendet werden <xref:Microsoft.Office.Tools.Word.XMLNodes> .

## <a name="events"></a>Ereignisse
 Folgende Ereignisse sind für das-Steuerelement verfügbar <xref:Microsoft.Office.Tools.Word.XMLNodes> :

- <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>Vergleichen von Ereignissen
 Sie können ein Ereignis erfassen, wenn der Benutzer den Cursor innerhalb des Kontexts eines bestimmten Steuer Elements verschiebt <xref:Microsoft.Office.Tools.Word.XMLNodes> . Angenommen, Sie verfügen über ein-Steuerelement mit dem Namen, <xref:Microsoft.Office.Tools.Word.XMLNodes> `Customer` das über ein untergeordnetes Steuerelement mit dem <xref:Microsoft.Office.Tools.Word.XMLNodes> Namen verfügt `Company` und über zwei untergeordnete Steuerelemente mit dem `Company` <xref:Microsoft.Office.Tools.Word.XMLNodes> Namen `CompanyName` und `CompanyRegion`

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Wenn Sie ein Steuerelement im Aktionsbereich anzeigen möchten, wenn der Cursor in den Knoten verschoben wird `Company` , sollte es keine Rolle spielen, ob der Cursor in oder eingefügt wird, `CompanyName` `CompanyRegion` da beide im Kontext von liegen `Company` . In diesem Fall können Sie den Code im- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> Ereignis von schreiben `Company` .

 In den meisten Fällen <xref:Microsoft.Office.Tools.Word.XMLNodes> <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> werden das-Ereignis und das-Ereignis ausgelöst, wenn der Cursor in ein-Steuerelement eintritt <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> . In der folgenden Tabelle werden die Unterschiede zwischen diesen Ereignissen angezeigt.

|Ereignis auswählen|ContextEnter-Ereignis|
|------------------|------------------------|
|Tritt auf, wenn der Cursor auf einem der Knoten der <xref:Microsoft.Office.Tools.Word.XMLNodes>-Auflistung platziert wird.|Tritt auf, wenn der Cursor außerhalb eines Bereichs des Knotenkontexts, in einem der Knoten oder der nachfolgenden Knoten der <xref:Microsoft.Office.Tools.Word.XMLNodes>-Auflistung platziert wird. Das heißt, es wird nur ausgelöst, wenn der Kontext geändert wird, und kann für mehrere geschdingte Steuerelemente ausgelöst werden <xref:Microsoft.Office.Tools.Word.XMLNodes> .|

 Wenn Sie den Cursor z. b. von außerhalb von `Customer` in bewegen `CompanyName` , <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> werden die `Customer` -Ereignisse für, `Company` und `CompanyName` ausgelöst. Wenn Sie den Cursor dann von `CompanyName` in bewegen `CompanyRegion` , <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> wird das Ereignis nur für `CompanyRegion` ausgelöst, da der Kontext für und identisch ist `Company` `Customer` . Es können mehrere `Company` Knoten in Ihrem Dokument vorhanden sein. Wenn Sie den Cursor vom `CompanyName` Knoten von einem `Company` auf den `CompanyName` Knoten eines anderen verschieben `Company` , ist der Kontext identisch, sodass nur das <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> Ereignis ausgelöst wird.

 Die gleichen Unterschiede bestehen zwischen dem <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> Ereignis und dem <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> Ereignis.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNode-Steuerelement](../vsto/xmlnode-control.md)
- [Gewusst wie: Hinzufügen von XMLNodes-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Gewusst wie: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
