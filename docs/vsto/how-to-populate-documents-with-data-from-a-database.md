---
title: 'Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank'
description: Erfahren Sie, wie Sie die Daten aus einer Datenbank in Ihrer Lösung verwenden können und wie Sie Windows Forms Steuerelemente verwenden können, um die Daten in einem Dokument anzuzeigen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0915d0ef57da5cba7fe73b6b374babe95b1a09c7
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848078"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank

Sie können in Microsoft Office-Projekten auf Dokumentebene auf die gleiche Weise auf Daten zugreifen wie in Windows Forms-Projekten. Sie verwenden dieselben Tools und denselben Code, um die Daten aus einer Datenbank in die Projektmappe einzufügen, und können Windows Forms-Steuerelemente zum Anzeigen der Daten verwenden.

Darüber hinaus können Sie Daten mithilfe von Hoststeuerelementen anzeigen. Hoststeuerelemente sind systemeigene Objekte in Microsoft Office Word, die mit Ereignissen und Datenbindungsfunktion erweitert wurden. Weitere Informationen finden Sie unter [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

Das folgende Beispiel zeigt, wie Sie datengebundene Steuerelemente in Projekten auf Dokumentebene mithilfe eines Designers hinzufügen. Ein Beispiel für das Hinzufügen von Daten gebundenen Steuerelementen in VSTO-Add-in-Projekten zur Laufzeit finden Sie unter Exemplarische Vorgehensweise [: einfache Datenbindung in einem VSTO-Add-in-Projekt](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") Eine entsprechende videodemo finden Sie unter [Binden von Daten an Word 2007-Inhalts Steuerelemente mithilfe von Visual Studio-Tools für das Office-System (3,0)](/previous-versions/office/developer/office-2007/bb967663(v=office.12)).

## <a name="add-a-control-to-a-document-at-design-time"></a>Hinzufügen eines Steuer Elements zu einem Dokument zur Entwurfszeit

### <a name="to-populate-a-document-with-data-from-a-database"></a>So füllen Sie ein Dokument mit Daten aus einer Datenbank auf

1. Öffnen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein Word-Projekt auf Dokumentebene, während das Dokument im Designer geöffnet ist.

2. Öffnen Sie das Fenster **Datenquellen** , und erstellen Sie eine Datenquelle aus einer Datenbank. Weitere Informationen finden Sie unter [Hinzufügen neuer Verbindungen](../data-tools/add-new-connections.md).

3. Ziehen Sie das gewünschte Feld aus dem Fenster **Datenquellen** in Ihr Dokument.

Ein Inhaltssteuerelement wird dem Dokument hinzugefügt. Der Typ des Inhaltssteuerelements hängt vom Datentyp des ausgewählten Felds ab. Weitere Informationen finden Sie unter [Inhalts Steuerelemente](../vsto/content-controls.md).

Sie können ein anderes Steuerelement hinzufügen, indem Sie im Fenster **Datenquellen** das Datenfeld auswählen und dann in der Dropdown Liste ein anderes Steuerelement auswählen.

## <a name="objects-in-the-project"></a>Objekte im Projekt

Neben dem Steuerelement werden die folgenden datenbezogenen Objekte dem Projekt automatisch hinzugefügt:

- Ein typisiertes Dataset, das die Datentabellen kapselt, mit denen Sie in der Datenbank eine Verbindung hergestellt haben. Weitere Informationen finden Sie unter [DataSet-Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Eine <xref:System.Windows.Forms.BindingSource>, durch die das Steuerelement mit dem typisierten Dataset verbunden wird. Weitere Informationen finden Sie unter [Übersicht über die BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- Ein TableAdapter, der das typisierte DataSet mit der Datenbank verbindet. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von TableAdapters](../data-tools/create-and-configure-tableadapters.md).

- Ein TableAdapterManager, der zum Koordinieren von Tabellen Adaptern im DataSet verwendet wird, um hierarchische Updates zu ermöglichen. Weitere Informationen finden Sie unter [hierarchische Update](../data-tools/hierarchical-update.md) -und [TableAdapterManager-Referenz](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Beim Ausführen des Projekts zeigt das Steuerelement den ersten Datensatz in der Datenquelle an. Sie können die <xref:System.Windows.Forms.BindingSource> verwenden, um Benutzern einen Bildlauf in den Datensätzen zu ermöglichen.

### <a name="to-scroll-through-the-records"></a>So führen Sie einen Bildlauf durch die Datensätze durch

- Verwenden Sie <xref:System.Windows.Forms.BindingSource>-Methoden wie <xref:System.Windows.Forms.BindingSource.MoveNext%2A> und <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Informationen zum Senden von Updates an das typisierte DataSet und die Datenbank finden Sie unter Gewusst [wie: Aktualisieren einer Datenquelle mit Daten aus einem Host Steuer](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)Element.

## <a name="see-also"></a>Siehe auch

- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Hinzufügen neuer Datenquellen](../data-tools/add-new-data-sources.md)
- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Host Steuer Elements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Verwenden lokaler Datenbankdateien in der Übersicht über Office-Lösungen](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Übersicht über die BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component-overview)