---
title: Binden von Windows Forms-Steuerelementen an Daten
description: Binden von Windows Forms-Steuerelementen an Daten in Visual Studio, sodass Sie Daten für Benutzer Ihrer Anwendung anzeigen können.
ms.custom: SEO-VS-2020
ms.date: 11/03/2017
ms.topic: how-to
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ee50a01093ff83faba17ec6fd59f4ddc1101012a
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518647"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Binden von Windows Forms-Steuerelementen an Daten in Visual Studio

Sie können Daten für Benutzer der Anwendung anzeigen, indem Sie Daten an Windows Forms binden. Um diese Daten gebundenen Steuerelemente zu erstellen, ziehen Sie Elemente aus dem Fenster **Datenquellen** auf die Windows Forms-Designer in Visual Studio.

![Datenquellen-Zieh Vorgang](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Wenn das Fenster **Datenquellen** nicht sichtbar ist, können Sie es öffnen, indem **View** Sie  >  **andere Windows**  >  - **Datenquellen** anzeigen auswählen oder **UMSCHALT** + **alt** + **D** drücken. Sie müssen ein Projekt in Visual Studio geöffnet haben, um das Fenster **Datenquellen** anzuzeigen.

Vor dem Ziehen von Elementen können Sie den Steuer Elementtyp festlegen, an den die Bindung erfolgen soll. Abhängig davon, ob Sie die Tabelle selbst oder eine einzelne Spalte auswählen, werden unterschiedliche Werte angezeigt.  Sie können auch benutzerdefinierte Werte festlegen. Für eine **Tabelle bedeutet das** , dass jede Spalte an ein separates Steuerelement gebunden ist.

![Datenquelle an DataGridView binden](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource-und BindingNavigator-Steuerelemente

Die <xref:System.Windows.Forms.BindingSource>-Komponente dient zwei Zwecken. Zuerst wird eine Abstraktions Ebene bereitstellt, wenn die Steuerelemente an Daten gebunden werden. Steuerelemente im Formular sind an die Komponente gebunden, <xref:System.Windows.Forms.BindingSource> anstatt direkt an eine Datenquelle. Zweitens kann so eine Auflistung von Objekten verwaltet werden. Wenn Sie zur <xref:System.Windows.Forms.BindingSource>-Komponente einen Typ hinzuzufügen, wird eine Liste dieses Typs erstellt.

Weitere Informationen über die <xref:System.Windows.Forms.BindingSource>-Komponente finden Sie unter:

- [BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component)

- [Übersicht über die BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [Architektur der BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

Das [BindingNavigator-Steuer](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) Element bietet eine Benutzeroberfläche zum Navigieren durch Daten, die von einer Windows-Anwendung angezeigt werden.

## <a name="bind-to-data-in-a-datagridview-control"></a>Binden an Daten in einem DataGridView-Steuerelement

Bei einem [DataGridView-Steuer](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms)Element ist die gesamte Tabelle an dieses einzelne Steuerelement gebunden. Wenn Sie ein **DataGridView** -Steuerelemente auf das Formular ziehen, wird auch eine Tool Leiste zum Navigieren in Datensätzen ( <xref:System.Windows.Forms.BindingNavigator> ) angezeigt. Die Komponenten [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt. In der folgenden Abbildung wird auch ein [TableAdapterManager](/previous-versions/bb384426(v=vs.140)) hinzugefügt, da die Customers-Tabelle eine Beziehung zur Orders-Tabelle aufweist. Diese Variablen werden alle im automatisch generierten Code als private Member in der Formular Klasse deklariert. Der automatisch generierte Code zum Auffüllen der **DataGridView** befindet sich im- `Form_Load` Ereignishandler. Der Code zum Speichern der Daten zum Aktualisieren der Datenbank befindet sich im- `Save` Ereignishandler für **BindingNavigator**. Sie können diesen Code nach Bedarf verschieben oder ändern.

![GridView mit BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Sie können das Verhalten von **DataGridView** und **BindingNavigator** anpassen, indem Sie in der oberen rechten Ecke auf das smarttagtag klicken:

![Smarttags DataGridView und Binding Navigator](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Wenn die von der Anwendung benötigten Steuerelemente im **Datenquellen** Fenster nicht verfügbar sind, können Sie Steuerelemente hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellen Fenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Sie können auch Elemente aus dem **Datenquellen** Fenster auf Steuerelemente ziehen, die sich bereits in einem Formular befinden, um das Steuerelement an Daten zu binden. Ein Steuerelement, das bereits an Daten gebunden ist, setzt die Daten Bindungen auf das Element zurück, das zuletzt auf das Element gezogen wurde. Um gültige Drop-Ziele zu sein, müssen Steuerelemente in der Lage sein, den zugrunde liegenden Datentyp des Elements anzuzeigen, das aus dem **Datenquellen** Fenster auf das Element gezogen wird. Beispielsweise ist es nicht zulässig, ein Element mit dem-Datentyp <xref:System.DateTime> auf einen zu ziehen <xref:System.Windows.Forms.CheckBox> , da das <xref:System.Windows.Forms.CheckBox> ein Datum nicht anzeigen kann.

## <a name="bind-to-data-in-individual-controls"></a>Binden an Daten in einzelnen Steuerelementen

Wenn Sie eine Datenquelle an **Details** binden, wird jede Spalte im DataSet an ein separates Steuerelement gebunden.

![Datenquelle an Details binden](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Beachten Sie, dass Sie in der vorherigen Abbildung aus der Orders-Eigenschaft der Customers-Tabelle und nicht aus der Orders-Tabelle ziehen. Durch Binden an die- `Customer.Orders` Eigenschaft werden die in der **DataGridView** vorgenommenen Navigations Befehle sofort in den Details-Steuerelementen angezeigt. Wenn Sie die Tabelle "Orders" aus der Tabelle "Orders" gezogen haben, sind die Steuerelemente weiterhin an das DataSet gebunden, aber nicht mit der **DataGridView** synchronisiert.

Die folgende Abbildung zeigt die standardmäßigen Daten gebundenen Steuerelemente, die dem Formular hinzugefügt werden, nachdem die Orders-Eigenschaft in der Customers-Tabelle an **Details** im **Datenquellen** Fenster gebunden ist.

![An Details gebundene Tabelle "Orders"](../data-tools/media/raddata-orders-table-bound-to-details.png)

Beachten Sie auch, dass jedes Steuerelement über ein Smarttag verfügt. Dieses Tag ermöglicht Anpassungen, die nur für dieses Steuerelement gelten.

## <a name="see-also"></a>Siehe auch

- [Binding controls to data in Visual Studio (Binden von Steuerelementen an Daten in Visual Studio)](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Datenbindung in Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)