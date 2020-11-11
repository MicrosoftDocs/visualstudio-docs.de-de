---
title: Binden von Steuerelementen an Daten
description: Binden von Steuerelementen an Daten in Visual Studio Erstellen Sie Daten gebundene Steuerelemente durchziehen von Elementen aus dem Datenquellen Fenster.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1b48c2e8b557a47c1ed795b6f9d3c3ced6247a43
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518621"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Binden von Steuerelementen an Daten in Visual Studio

Sie können Daten für Benutzer der Anwendung anzeigen, indem Sie Daten an Steuerelemente binden. Sie können diese Daten gebundenen Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellen** Fenster auf eine Entwurfs Oberfläche oder Steuerelemente auf einer Oberfläche in Visual Studio ziehen.

In diesem Thema werden die Datenquellen, mit denen Sie datengebundene Steuerelemente erstellen können, beschrieben. Es werden auch einige der allgemeinen Aufgaben beschrieben, die mit der Datenbindung zusammenhängen. Spezifischere Informationen zum Erstellen Daten gebundener Steuerelemente finden Sie unterbinden von Windows Forms-Steuer [Elementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) und [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

## <a name="data-sources"></a>Datenquellen

Im Kontext der Datenbindung stellt eine Datenquelle die Daten im Arbeitsspeicher dar, die an Ihre Benutzeroberfläche gebunden werden können. Praktisch ausgedrückt kann eine Datenquelle eine Entity Framework Klasse, ein DataSet, ein Dienst Endpunkt, der in einem .NET-Proxy Objekt, eine LINQ to SQL Klasse oder ein beliebiges .NET-Objekt oder eine beliebige Auflistung gekapselt ist. Einige Datenquellen ermöglichen es Ihnen, datengebundene Steuerelemente durch Ziehen von Elementen aus dem Fenster **Datenquellen** zu erstellen. Bei anderen Datenquellen ist dies hingegen nicht der Fall. Die folgende Tabelle zeigt, welche Datenquellen unterstützt werden.

| Datenquelle | Drag & Drop-Unterstützung im **Windows Forms-Designer** | Drag & Drop-Unterstützung im **WPF-Designer** | Drag & Drop-Unterstützung im **Silverlight-Designer** |
| - | - | - | - |
| Dataset | Ja | Ja | Nein  |
| Entity Data Model | Ja<sup>1</sup> | Ja | Ja |
| LINQ to SQL-Klassen | Nein<sup>2</sup> | Nein<sup>2</sup> | Nein<sup>2</sup> |
| Dienste (einschließlich [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], WCF-Dienste und Webdienste) | Ja | Ja | Ja |
| Object | Ja | Ja | Ja |
| SharePoint | Ja | Ja | Ja |

1. Generieren Sie das Modell mithilfe des **Entity Data Model** -Assistenten, und ziehen Sie dann diese Objekte in den Designer.

2. LINQ to SQL-Klassen werden nicht im Fenster **Datenquellen** angezeigt. Sie können jedoch eine neue Objektdatenquelle hinzufügen, die auf LINQ to SQL-Klassen basiert und anschließend diese Objekte in den Designer ziehen, um datengebundene Steuerelemente zu erstellen. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen von LINQ to SQL Klassen (O-R-Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="data-sources-window"></a>Datenquellenfenster

Datenquellen stehen dem Projekt als Elemente im Fenster **Datenquellen** zur Verfügung. Dieses Fenster ist sichtbar, wenn eine Formular Entwurfs Oberfläche das aktive Fenster in Ihrem Projekt ist, oder Sie können es öffnen (wenn ein Projekt geöffnet ist), **View** indem Sie  >  **andere Windows** -  >  **Datenquellen** anzeigen auswählen. Sie können Elemente aus diesem Fenster ziehen, um Steuerelemente zu erstellen, die an die zugrunde liegenden Daten gebunden sind. Außerdem können Sie die Datenquellen konfigurieren, indem Sie mit der rechten Maustaste klicken.

![Datenquellenfenster](../data-tools/media/raddata-data-sources-window.png)

Für jeden Datentyp, der im Fenster **Datenquellen** angezeigt wird, wird ein standardmäßiges Steuerelement erstellt, wenn das Element in den Designer gezogen wird. Bevor Sie ein Element aus dem **Datenquellen** Fenster ziehen, können Sie das Steuerelement ändern, das erstellt wird. Weitere Informationen finden Sie unter [Festlegen des Steuer Elements, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Aufgaben beim Binden von Steuerelementen an Daten

In der folgenden Tabelle sind einige der gängigsten Aufgaben aufgeführt, die Sie zum Binden von Steuerelementen an Daten ausführen.

|Aufgabe|Weitere Informationen|
|----------| - |
|Öffnen Sie das Fenster **Datenquellen**.|Öffnen Sie im Editor eine Entwurfs Oberfläche, und **View** wählen Sie  >  **Datenquellen** anzeigen aus.|
|Fügen Sie dem Projekt eine Datenquelle hinzu.|[Hinzufügen neuer Datenquellen](../data-tools/add-new-data-sources.md)|
|Legen Sie das Steuerelement fest, das erstellt wird, wenn Sie ein Element vom Fenster **Datenquellen** in den Designer ziehen.|[Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Ändern Sie die Liste der Steuerelemente, die Elementen im Fenster **Datenquellen** zugeordnet sind.|[Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Erstellen Sie datengebundene Steuerelemente.|[Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|
|Binden an ein Objekt oder eine Auflistung.|[Binden von Objekten in Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtern von Daten, die in der Benutzeroberfläche angezeigt werden.|[Filtern und Sortieren von Daten in einer Windows Forms-Anwendung](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Anpassen von Untertiteln für Steuerelemente.|[Anpassen der Erstellung von Beschriftungen für datengebundene Steuerelemente durch Visual Studio](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Datenbindung Windows Forms](/dotnet/framework/winforms/windows-forms-data-binding)
