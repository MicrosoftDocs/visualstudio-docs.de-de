---
title: 'Gewusst wie: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank'
description: Erfahren Sie, wie Sie die Daten aus einem Objekt in der Projekt Mappe verwenden können und wie Sie Windows Forms Steuerelemente zum Anzeigen der Daten in einem Arbeitsblatt verwenden können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 66f37a1639cb6a86f107d9372704d5c8364c6a18
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918567"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Gewusst wie: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank

Sie können auf Daten in Office-Projekten auf Dokument Ebene auf die gleiche Weise zugreifen, wie Sie auf Daten in Windows Forms Projekten zugreifen. Sie verwenden dieselben Tools und denselben Code, um die Daten in die Projektmappe einzufügen, und können außerdem Windows Forms-Steuerelemente zum Anzeigen der Daten verwenden. Außerdem können Sie die Steuerelemente, die als Host Steuerelemente bezeichnet werden, als systemeigene Objekte in Microsoft Office Excel nutzen, die mit Ereignissen und Daten Bindungsfunktionen erweitert wurden. Weitere Informationen finden Sie unter [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

Das folgende Beispiel zeigt, wie Sie datengebundene Steuerelemente in Projekten auf Dokumentebene mithilfe eines Designers hinzufügen. Ein Beispiel zum Hinzufügen von Daten gebundenen Steuerelementen in Projekten auf Anwendungsebene zur Laufzeit finden Sie unter Exemplarische Vorgehensweise [: komplexe Datenbindung in einem VSTO-Add-in-Projekt](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Hinzufügen eines Daten gebundenen Steuer Elements zu einem Arbeitsblatt zur Entwurfszeit

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>So füllen Sie ein Arbeitsblatt mit Daten aus einer Datenbank auf

1. Öffnen Sie ein Excel-Projekt auf Dokument Ebene in Visual Studio, auf dem das Arbeitsblatt im Designer geöffnet ist.

2. Öffnen Sie das Fenster **Datenquellen** , und erstellen Sie für Ihr Projekt eine Datenquelle. Weitere Informationen finden Sie unter [Hinzufügen neuer Verbindungen](../data-tools/add-new-connections.md).

3. Ziehen Sie das gewünschte Feld oder die gewünschte Tabelle aus dem Fenster **Datenquellen** in das Arbeitsblatt.

Eines der folgenden Steuerelemente wird auf dem Arbeitsblatt erstellt:

- Wenn Sie ein Feld ziehen, wird ein- <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement auf dem Arbeitsblatt erstellt. Weitere Informationen finden Sie unter [Name Drange Control](../vsto/namedrange-control.md).

- Wenn Sie eine Tabelle ziehen, wird ein- <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement auf dem Arbeitsblatt erstellt. Weitere Informationen finden Sie unter [ListObject Control](../vsto/listobject-control.md).

Sie können ein anderes Steuerelement hinzufügen, indem Sie die Tabelle oder das Feld im **Datenquellen** Fenster auswählen und dann in der Dropdown Liste ein anderes Steuerelement auswählen.

## <a name="objects-in-the-project"></a>Objekte im Projekt

Neben dem Steuerelement werden die folgenden datenbezogenen Objekte dem Projekt automatisch hinzugefügt:

- Ein typisiertes Dataset, das die Datentabellen kapselt, mit denen Sie in der Datenbank eine Verbindung hergestellt haben. Weitere Informationen finden Sie unter [DataSet-Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Eine <xref:System.Windows.Forms.BindingSource>, durch die das Steuerelement mit dem typisierten Dataset verbunden wird. Weitere Informationen finden Sie unter [Übersicht über die BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- Ein TableAdapter, der das typisierte DataSet mit der Datenbank verbindet. Weitere Informationen finden Sie unter [Übersicht über TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

- Ein TableAdapterManager, der zum Koordinieren von Tabellen Adaptern im DataSet verwendet wird, um hierarchische Updates zu ermöglichen. Weitere Informationen finden Sie unter [hierarchische Update](../data-tools/hierarchical-update.md) -und [TableAdapterManager-Referenz](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Beim Ausführen des Projekts zeigt das Steuerelement den ersten Datensatz in der Datenquelle an. Sie können die <xref:System.Windows.Forms.BindingSource> verwenden, um Benutzern einen Bildlauf in den Datensätzen zu ermöglichen.

### <a name="to-scroll-through-the-records"></a>So führen Sie einen Bildlauf durch die Datensätze durch

- Verwenden Sie <xref:System.Windows.Forms.BindingSource>-Methoden wie <xref:System.Windows.Forms.BindingSource.MoveNext%2A> und <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Informationen zum Senden von Updates an das typisierte DataSet und die Datenbank finden Sie unter Gewusst [wie: Aktualisieren einer Datenquelle mit Daten aus einem Host Steuer](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)Element.

## <a name="see-also"></a>Weitere Informationen

- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Hinzufügen neuer Datenquellen](../data-tools/add-new-data-sources.md)
- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Host Steuer Elements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)