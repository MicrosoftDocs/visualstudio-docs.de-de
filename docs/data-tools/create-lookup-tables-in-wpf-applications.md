---
title: Erstellen von Nachschlagetabellen in WPF-Anwendungen
description: Erstellen von Nachschlage Tabellen in WPF-apps Eine Nachschlage Tabelle ist ein Steuerelement, das Informationen aus einer Datentabelle anhand eines Fremdschlüssel-Feldwerts in einer anderen Tabelle anzeigt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 293f04ca111fe88c905a288885f7e4763ec1cdc3
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436692"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Erstellen von Nachschlagetabellen in WPF-Anwendungen

Der Begriff Nachschlage *Tabelle* (manchmal als *Such Bindung* bezeichnet) beschreibt ein Steuerelement, das Informationen aus einer Datentabelle basierend auf dem Wert eines Fremdschlüssel Felds in einer anderen Tabelle anzeigt. Sie können eine Nachschlage Tabelle erstellen, indem Sie den Haupt Knoten einer übergeordneten Tabelle oder eines Objekts im **Datenquellen** Fenster auf ein Steuerelement ziehen, das bereits an eine Spalte oder Eigenschaft in einer verknüpften untergeordneten Tabelle gebunden ist.

Als Beispiel kann eine Tabelle mit dem Namen `Orders` dienen, die Teil einer Verkaufsdatenbank ist und Aufträge enthält. Jeder Datensatz in der `Orders` Tabelle enthält einen `CustomerID` , der angibt, welcher Kunde den Auftrag aufgegeben hat. Der `CustomerID` ist ein Fremdschlüssel, der auf einen Kundendaten Satz in der- `Customers` Tabelle verweist. Wenn Sie eine Liste der Bestellungen aus der `Orders` Tabelle anzeigen, möchten Sie möglicherweise den tatsächlichen Kundennamen anstelle von anzeigen `CustomerID` . Da der Kunden Name in der Tabelle enthalten ist `Customers` , müssen Sie eine Nachschlage Tabelle erstellen, um den Kundennamen anzuzeigen. In der Nachschlage Tabelle wird der `CustomerID` Wert im `Orders` Datensatz verwendet, um in der Beziehung zu navigieren und den Kundennamen zurückzugeben.

## <a name="to-create-a-lookup-table"></a>So erstellen Sie eine Suchtabelle

1. Fügen Sie einem Projekt einen der folgenden Typen von Datenquellen mit verknüpften Daten hinzu:

    - DataSet oder Entity Data Model.

    - WCF-Datendienst, WCF-Dienst oder Webdienst. Weitere Informationen finden Sie unter Gewusst [wie: Herstellen einer Verbindung mit Daten in einem Dienst](../data-tools/how-to-connect-to-data-in-a-service.md).

    - Objekte. Weitere Informationen finden Sie unter [binden an Objekte in Visual Studio](bind-objects-in-visual-studio.md).

    > [!NOTE]
    > Bevor Sie eine Nachschlage Tabelle erstellen können, müssen zwei verknüpfte Tabellen oder Objekte als Datenquelle für das Projekt vorhanden sein.

2. Öffnen Sie den **WPF-Designer** , und stellen Sie sicher, dass der Designer einen Container enthält, bei dem es sich um ein gültiges Ablage Ziel für Elemente im **Datenquellen** Fenster handelt.

     Weitere Informationen zu gültigen Drop-Zielen finden [Sie unterbinden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

3. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen** , um das Fenster **Datenquellen** zu öffnen.

4. Erweitern Sie die Knoten im **Datenquellen** Fenster, bis die übergeordnete Tabelle oder das übergeordnete Objekt und die zugehörige untergeordnete Tabelle oder das zugehörige Objekt angezeigt werden.

    > [!NOTE]
    > Die zugehörige untergeordnete Tabelle oder das verbundene Objekt ist der Knoten, der als erweiterbarer untergeordneter Knoten unter der übergeordneten Tabelle oder dem übergeordneten Objekt angezeigt wird

5. Klicken Sie auf das Dropdown Menü für den untergeordneten Knoten, und wählen Sie **Details** aus.

6. Erweitern Sie den untergeordneten Knoten.

7. Klicken Sie unter dem untergeordneten Knoten auf das Dropdown Menü für das Element, das die untergeordneten und übergeordneten Daten verknüpft. (Im vorherigen Beispiel ist dies der **CustomerID-** Knoten.) Wählen Sie einen der folgenden Typen von Steuerelementen aus, die die Such Bindung unterstützen:

    - **ComboBox**

    - **ListBox**

    - **ListView**

        > [!NOTE]
        > Wenn das **ListBox** -Steuerelement oder das **ListView** -Steuerelement nicht in der Liste angezeigt wird, können Sie diese Steuerelemente der Liste hinzufügen. Weitere Informationen finden [Sie unter Festlegen des Steuer Elements, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    - Alle benutzerdefinierten Steuerelemente, die von abgeleitet werden <xref:System.Windows.Controls.Primitives.Selector> .

        > [!NOTE]
        > Weitere Informationen zum Hinzufügen von benutzerdefinierten Steuerelementen zur Liste der Steuerelemente, die Sie für Elemente im **Datenquellen** Fenster auswählen können, finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellen Fenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8. Ziehen Sie den untergeordneten Knoten aus dem **Datenquellen** Fenster auf einen Container im WPF-Designer. (Im vorherigen Beispiel ist der untergeordnete Knoten der Knoten **Orders** .)

     Visual Studio generiert XAML, das neue Daten gebundene Steuerelemente für jedes der Elemente erstellt, die Sie ziehen. Die XAML fügt <xref:System.Windows.Data.CollectionViewSource> den Ressourcen des Ablage Ziels auch ein neues für die untergeordnete Tabelle oder das untergeordnete Objekt hinzu. Für einige Datenquellen generiert Visual Studio auch Code zum Laden von Daten in die Tabelle oder das Objekt. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

9. Ziehen Sie den übergeordneten Knoten aus dem **Datenquellen** Fenster auf das Nachschlage Steuerelement für die Suche, das Sie zuvor erstellt haben. (Im vorherigen Beispiel ist der übergeordnete Knoten der Knoten **Customers** ).

     Visual Studio legt einige Eigenschaften für das Steuerelement fest, um die Such Bindung zu konfigurieren. In der folgenden Tabelle werden die Eigenschaften aufgelistet, die von Visual Studio geändert werden. Bei Bedarf können Sie diese Eigenschaften im XAML-oder im **Eigenschaften** Fenster ändern.

    |Eigenschaft|Erklärung der Einstellung|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Diese Eigenschaft gibt die Auflistung oder Bindung an, die verwendet wird, um die im Steuerelement angezeigten Daten zu erhalten. Visual Studio legt diese Eigenschaft <xref:System.Windows.Data.CollectionViewSource> für die übergeordneten Daten, die Sie in das Steuerelement gezogen haben, auf fest.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Diese Eigenschaft gibt den Pfad des Datenelements an, das im-Steuerelement angezeigt wird. Visual Studio legt diese Eigenschaft auf die erste Spalte oder Eigenschaft in den übergeordneten Daten fest, und zwar nach dem Primärschlüssel, der einen Zeichen folgen-Datentyp aufweist.<br /><br /> Wenn Sie eine andere Spalte oder Eigenschaft in den übergeordneten Daten anzeigen möchten, ändern Sie diese Eigenschaft in den Pfad einer anderen Eigenschaft.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio bindet diese Eigenschaft an die Spalte oder Eigenschaft der untergeordneten Daten, die Sie in den Designer gezogen haben. Dies ist der Fremdschlüssel für die übergeordneten Daten.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Diese Eigenschaft wird von Visual Studio auf den Pfad der Spalte oder Eigenschaft der untergeordneten Daten festgelegt, die den Fremdschlüssel zu den übergeordneten Daten ist.|

## <a name="see-also"></a>Siehe auch

- [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Anzeigen zugehöriger Daten in WPF-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md)
- [Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einer WPF-Anwendung](../data-tools/display-related-data-in-wpf-applications.md)
