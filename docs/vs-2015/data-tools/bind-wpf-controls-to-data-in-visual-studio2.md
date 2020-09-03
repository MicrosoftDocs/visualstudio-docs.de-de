---
title: Binden von WPF-Steuerelementen an Daten (Teil 2) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06428a633aec41489a8a77655d6ea9442ffffaa0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540087"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Binden von WPF-Steuerelementen an Daten in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Daten gebundene Steuerelemente erstellen, [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] indem Sie das Fenster **Datenquellen** verwenden. Fügen Sie zunächst dem **Datenquellen** Fenster eine Datenquelle hinzu. Ziehen Sie dann Elemente aus dem **Datenquellen** Fenster in den**WPF-Designer**.

## <a name="add-a-data-source-to-the-data-sources-window"></a><a name="adding"></a> Hinzufügen einer Datenquelle zum Datenquellen Fenster
 Bevor Sie Daten gebundene Steuerelemente erstellen können, müssen Sie zunächst dem **Datenquellen** Fenster eine Datenquelle hinzufügen.

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>So fügen Sie dem Datenquellenfenster eine Datenquelle hinzu

1. Zeigen Sie im Menü **Ansicht** auf **Weitere Fenster**, und klicken Sie dann auf **Datenquellen**.

2. Klicken Sie auf **Neue Datenquelle hinzufügen**, und führen Sie den **Assistenten zum Konfigurieren von Datenquellen** aus.

3. Führen Sie eine der folgenden Aufgaben aus, um datengebundene Steuerelemente zu erstellen:

    - [Erstellen eines Steuer Elements, das an ein einzelnes Datenfeld gebunden ist](#simple).

    - [Erstellen eines Steuer Elements, das an mehrere Datenfelder gebunden ist](#complex).

    - [Erstellen eines Satzes von Steuerelementen, die an mehrere Datenfelder gebunden sind](#details).

    - [Binden von Daten an vorhandene Steuerelemente im Designer](#existing).

## <a name="create-a-control-that-is-bound-to-a-single-field-of-data"></a><a name="simple"></a> Erstellen eines Steuer Elements, das an ein einzelnes Datenfeld gebunden ist
 Nachdem Sie dem **Datenquellen** Fenster eine Datenquelle hinzugefügt haben, können Sie ein neues Daten gebundenes Steuerelement erstellen, das ein einzelnes Datenfeld anzeigt, z <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.TextBox> . b. oder.

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>So erstellen Sie ein Steuerelement, das an ein einzelnes Datenfeld gebunden ist

1. Erweitern Sie im **Datenquellen** Fenster ein Element, das eine Tabelle oder ein Objekt darstellt. Suchen Sie das untergeordnete Element, das die Spalte oder die Eigenschaft darstellt, an die das Steuerelement gebunden werden soll. Ein visuelles Beispiel finden Sie unter [Datenquellen Fenster](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Optional können Sie das zu erstellende Steuerelement auswählen. Jedes Element im **Datenquellen** Fenster verfügt über ein Standard Steuerelement, das erstellt wird, wenn Sie das Element in den Designer ziehen. Das Standardsteuerelement hängt vom zugrunde liegenden Datentyp des Elements ab.

     Um ein anderes Steuerelement auszuwählen, klicken Sie auf den Dropdownpfeil neben dem Element, und wählen Sie ein Steuerelement aus. Weitere Informationen finden Sie unter [Festlegen des Steuer Elements, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

3. Ziehen Sie das Element in einen gültigen Container im Designer. Weitere Informationen zu gültigen Containern finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellt das neue Daten gebundene Steuerelement und einen entsprechend <xref:System.Windows.Controls.Label> der Bezeichnung im Container. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert außerdem [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] und Code zum Binden des Steuer Elements an die Daten. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="create-a-control-that-is-bound-to-multiple-fields-of-data"></a><a name="complex"></a> Erstellen eines Steuer Elements, das an mehrere Datenfelder gebunden ist
 Nachdem Sie dem **Datenquellen** Fenster eine Datenquelle hinzugefügt haben, können Sie ein neues Daten gebundenes Steuerelement erstellen, das mehrere Datenfelder anzeigt, z <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.ListView> . b. oder.

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>So erstellen Sie ein Steuerelement, das an mehrere Datenfelder gebunden ist

1. Wählen Sie im Fenster **Datenquellen** ein Element aus, das eine Tabelle oder ein Objekt darstellt. Ein visuelles Beispiel finden Sie unter [Datenquellen Fenster](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Optional können Sie das zu erstellende Steuerelement auswählen. Standardmäßig wird jedes Element im **Datenquellen** Fenster, das eine Datentabelle oder ein Datenobjekt darstellt, so festgelegt, dass ein <xref:System.Windows.Controls.DataGrid> (wenn das Projekt auf .NET Framework 4 festgelegt ist) oder <xref:System.Windows.Controls.ListView> (für frühere Versionen des .NET Framework) erstellt wird.

     Um ein anderes Steuerelement auszuwählen, klicken Sie auf den Dropdownpfeil neben dem Element, und wählen Sie ein Steuerelement aus. Weitere Informationen finden Sie unter [Festlegen des Steuer Elements, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    > [!NOTE]
    > Wenn eine bestimmte Spalte oder Eigenschaft nicht angezeigt werden soll, erweitern Sie das Element, um seine untergeordneten Elemente anzuzeigen. Klicken Sie auf den Dropdown Pfeil neben der Spalte oder Eigenschaft, die Sie nicht anzeigen möchten, und klicken Sie dann auf **keine**.

3. Ziehen Sie das Element auf einen gültigen Container im Designer, z. B. ein <xref:System.Windows.Controls.Grid>. Weitere Informationen zu gültigen Containern finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellt das neue Daten gebundene Steuerelement im Container. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert außerdem [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] und Code zum Binden des Steuer Elements an die Daten. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a><a name="details"></a> Erstellen eines Satzes von Steuerelementen, die an mehrere Datenfelder gebunden sind
 Nachdem Sie dem **Datenquellen** Fenster eine Datenquelle hinzugefügt haben, können Sie eine Datentabelle oder ein Objekt an einen Satz von Steuerelementen binden. Für jede Spalte oder jede Eigenschaft in der Tabelle oder dem Objekt wird ein anderes Steuerelement erstellt.

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>So erstellen Sie einen Satz von Steuerelementen, die an mehrere Datenfelder gebunden sind

1. Wählen Sie im Fenster **Datenquellen** ein Element aus, das eine Tabelle oder ein Objekt darstellt. Ein visuelles Beispiel finden Sie unter [Datenquellen Fenster](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Klicken Sie auf den Dropdown Pfeil neben dem Element, und wählen Sie **Details**aus.

    > [!NOTE]
    > Wenn eine bestimmte Spalte oder Eigenschaft nicht angezeigt werden soll, erweitern Sie das Element, um seine untergeordneten Elemente anzuzeigen. Klicken Sie auf den Dropdown Pfeil neben der Spalte oder Eigenschaft, die Sie nicht anzeigen möchten, und klicken Sie dann auf **keine**.

3. Ziehen Sie das Element auf einen gültigen Container im Designer, z. B. ein <xref:System.Windows.Controls.Grid>. Weitere Informationen zu gültigen Containern finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellt die neuen datengebundenen Steuerelemente im Container. Jedes Steuerelement wird an eine andere Spalte oder Eigenschaft gebunden, und jedes Steuerelement wird von einem entsprechend benannten <xref:System.Windows.Controls.Label>-Steuerelement begleitet. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert außerdem [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] und Code, um die Steuerelemente an die Daten zu binden. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="binddata-to-existing-controls-in-the-designer"></a><a name="existing"></a> BindData an vorhandene Steuerelemente im Designer
 Nachdem Sie dem **Datenquellen** Fenster eine Datenquelle hinzugefügt haben, können Sie eine Datenbindung zu einem vorhandenen Steuerelement im Designer hinzufügen.

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>So binden Sie Daten an ein vorhandenes Steuerelement im Designer

1. Verwenden Sie im Fenster **Datenquellen** eines der folgenden Prozeduren:

    - Um einem vorhandenen Steuerelement, das mehrere Datenfelder anzeigt, z. B. ein <xref:System.Windows.Controls.DataGrid> oder eine <xref:System.Windows.Controls.ListView>, eine Datenbindung hinzuzufügen, wählen Sie das Element aus, das die Tabelle oder das Objekt darstellt, die bzw. das Sie an das Steuerelement binden möchten.

    - Um einem vorhandenen Steuerelement, das ein einzelnes Datenfeld anzeigt, z. B. eine <xref:System.Windows.Controls.ComboBox> oder eine <xref:System.Windows.Controls.TextBox>, eine Datenbindung hinzuzufügen, erweitern Sie das Element, das die Tabelle oder das Objekt mit den Daten darstellt, und wählen Sie dann das Element aus, das die an das Steuerelement zu bindenden Daten darstellt.

2. Ziehen Sie das ausgewählte Element aus dem **Datenquellen** Fenster auf ein vorhandenes Steuerelement im Designer. Das Steuerelement muss ein gültiges Ablageziel sein. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generiert [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] und Code zum Binden des Steuer Elements an die Daten. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

    > [!NOTE]
    > Wenn das Steuerelement bereits an Daten gebunden ist, wird die Datenbindung für das Steuerelement auf das Element zurückgesetzt, das zuletzt auf das Steuerelement gezogen wurde.

## <a name="see-also"></a>Weitere Informationen
 [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [Erstellen von Nachschlage Tabellen in WPF-Anwendungen](../data-tools/create-lookup-tables-in-wpf-applications.md) [Anzeigen verwandter Daten in WPF-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md) Binden von WPF-Steuerelementen an ein [DataSet](../data-tools/bind-wpf-controls-to-a-dataset.md) [Binden von WPF-Steuerelementen an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) Exemplarische Vorgehensweise [: Anzeigen verwandter Daten in einer WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
