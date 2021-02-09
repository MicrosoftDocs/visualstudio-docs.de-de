---
title: 'Gewusst wie: Auffüllen von Dokumenten mit Daten aus Objekten'
description: Erfahren Sie, wie Sie die Daten aus einem Objekt in der Projekt Mappe verwenden können, und Sie können Windows Forms Steuerelemente verwenden, um die Daten in einem Dokument anzuzeigen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5bebc21fb02f6b5441c597fcfd25364991829e71
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918581"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Gewusst wie: Auffüllen von Dokumenten mit Daten aus Objekten

Der Zugriff auf Daten in einem Datenobjekt funktioniert in Microsoft Office Word-Projekten auf Dokumentebene auf die gleiche Weise wie in Windows Forms-Projekten. Sie verwenden dieselben Tools und denselben Code, um die Daten aus einem Objekt in die Projektmappe einzufügen, und können Windows Forms-Steuerelemente zum Anzeigen der Daten verwenden. Darüber hinaus können Sie Daten mithilfe von Hoststeuerelementen anzeigen. Hoststeuerelemente sind systemeigene Objekte in Microsoft Office Word, die mit Ereignissen und Datenbindungsfunktion erweitert wurden. Weitere Informationen finden Sie unter [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

Sie müssen drei grundlegende Schritte ausführen, um das Dokument mit Daten aus einem Objekt aufzufüllen:

- Fügen Sie ein Steuerelement zum Dokument hinzu, das an Daten gebunden werden kann.

- Fügen Sie ein Datenobjekt zum Dokument hinzu.

- Verbinden Sie das Datenobjekt mit der BindingSource-Komponente.

## <a name="to-add-a-data-object"></a>So fügen Sie ein Datenobjekt hinzu

Öffnen Sie zum Hinzufügen eines Datenobjekts das Fenster **Datenquellen** , und erstellen Sie eine Datenquelle aus einem-Objekt. Weitere Informationen finden Sie unter [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md).

## <a name="connect-the-data-object-to-the-bindingsource"></a>Verbinden des Datenobjekts mit der BindingSource

In Projekten auf Dokumentebene fügen Sie Ihrem Dokument Steuerelemente hinzu und binden diese zur Entwurfszeit an Daten.

In VSTO-Add-In-Projekten erstellen Sie Steuerelemente und binden diese zur Laufzeit.

### <a name="document-level-projects"></a>Projekte auf Dokument Ebene

So verbinden Sie das Datenobjekt mit der BindingSource:

1. Ziehen Sie das gewünschte Datenfeld vom Fenster **Datenquellen** in Ihr Dokument. Dadurch wird automatisch ein Steuerelement erstellt.

2. Erstellen Sie im Code eine Instanz des Typs des Objekts, das Sie für die Datenquelle ausgewählt haben.

3. Weisen Sie die Instanz der <xref:System.Windows.Forms.BindingSource.DataSource%2A> -Eigenschaft der <xref:System.Windows.Forms.BindingSource>-Komponente zu.

### <a name="application-level-projects"></a>Projekte auf Anwendungsebene

So verbinden Sie das Datenobjekt mit der BindingSource:

1. Erstellen Sie im Code eine Instanz des Typs des Objekts, das der Datenquelle zugewiesen wird.

2. Erstellen Sie eine Instanz von <xref:System.Windows.Forms.BindingSource>.

3. Weisen Sie die Datenquelleninstanz der <xref:System.Windows.Forms.BindingSource.DataSource%2A> -Eigenschaft der <xref:System.Windows.Forms.BindingSource>-Komponente zu.

4. Fügen Sie die Datenquelle als eine Datenbindung zum Steuerelement hinzu.

## <a name="see-also"></a>Weitere Informationen

- [Hinzufügen neuer Datenquellen](../data-tools/add-new-data-sources.md)
- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Host Steuer Elements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Übersicht über die BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component-overview)