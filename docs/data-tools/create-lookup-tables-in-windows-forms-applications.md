---
title: Erstellen von Nachschlagetabellen in Windows Forms-Anwendungen
description: Weitere Informationen finden Sie unter Erstellen von Nachschlage Tabellen in Windows Forms Anwendungen. In einer Nachschlage Tabelle werden Steuerelemente beschrieben, die an zwei verknüpfte Datentabellen gebunden sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3d6ec8860d2c163d16e29d229203bb77abcdf65f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435194"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Erstellen von Nachschlagetabellen in Windows Forms-Anwendungen

Die Begriff *Nachschlagetabelle* bezeichnet Steuerelemente, die an zwei zusammengehörige Datentabellen gebunden werden. Diese Nachschlagesteuerelemente zeigen Daten aus der ersten Tabelle in Abhängigkeit von den in der zweiten Tabelle ausgewählten Werten an.

Sie können Nachschlage Tabellen erstellen, indem Sie den Haupt Knoten einer übergeordneten Tabelle (aus dem [Datenquellen Fenster](add-new-data-sources.md#data-sources-window)) auf ein Steuerelement auf dem Formular ziehen, das bereits an die Spalte in der zugehörigen untergeordneten Tabelle gebunden ist.

Als Beispiel kann eine Tabelle mit dem Namen `Orders` dienen, die Teil einer Verkaufsdatenbank ist und Aufträge enthält. Jeder Datensatz in der Tabelle `Orders` enthält eine `CustomerID`, die angibt, welcher Kunde den Auftrag erteilt hat. Die `CustomerID` ist ein Fremdschlüssel, der auf einen Kundendatensatz in der Tabelle `Customers` zeigt. In diesem Szenario erweitern Sie die `Orders` Tabelle im **Datenquellen** Fenster und legen den Haupt Knoten auf **Details** fest. Legen `CustomerID` Sie dann für die Spalte die Verwendung eines <xref:System.Windows.Forms.ComboBox> (oder eines beliebigen anderen Steuer Elements, das die Such Bindung unterstützt) fest, und ziehen `Orders` Sie den Knoten auf das Formular. Ziehen Sie schließlich den `Customers` Knoten auf das Steuerelement, das an die zugehörige Spalte gebunden ist – in diesem Fall die <xref:System.Windows.Forms.ComboBox> an die `CustomerID` Spalte gebundene.

## <a name="to-databind-a-lookup-control"></a>So stellen Sie die Datenbindung für ein Nachschlagesteuerelement her

1. Öffnen Sie das Fenster **Datenquellen** , während das Projekt geöffnet ist **View** , indem Sie  >  **andere Windows** -  >  **Datenquellen** anzeigen auswählen.

    > [!NOTE]
    > Für Nachschlagetabellen ist es erforderlich, dass zwei zusammengehörige Tabellen oder Objekte im **Datenquellenfenster** verfügbar sind. Weitere Informationen finden Sie unter [Beziehungen in Datasets](relationships-in-datasets.md).

2. Erweitern Sie im **Datenquellenfenster** die Knoten, bis die übergeordnete Tabelle und die zugehörige untergeordnete Tabelle jeweils mit allen Spalten angezeigt werden.

    > [!NOTE]
    > Der Knoten der untergeordneten Tabelle ist der Knoten, der in der übergeordneten Tabelle als ein erweiterbarer untergeordneter Knoten angezeigt wird.

3. Ändern Sie den Ablagetyp auf **Details** , indem Sie am Knoten der untergeordneten Tabelle in der Steuerelementliste die Option **Details** auswählen. Weitere Informationen finden Sie unter [Festlegen des Steuer Elements, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Suchen Sie den Knoten, der die beiden Tabellen verknüpft (der `CustomerID` Knoten im vorherigen Beispiel). Ändern Sie den Ablagetyp in ein, indem Sie in <xref:System.Windows.Forms.ComboBox> der Steuerelement Liste die Option **ComboBox** auswählen.

5. Ziehen Sie den Hauptknoten der untergeordneten Tabelle aus dem **Datenquellenfenster** auf das Formular.

     Auf dem Formular werden datengebundene Steuerelemente (mit beschreibenden Bezeichnungen) sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) angezeigt. Die Komponenten [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt.

6. Ziehen Sie den Hauptknoten der übergeordneten Tabelle aus dem **Datenquellenfenster** direkt auf das Nachschlagesteuerelement (<xref:System.Windows.Forms.ComboBox>).

     Die Nachschlagebindungen werden jetzt festgelegt. In der folgenden Tabelle finden Sie die spezifischen Eigenschaften, die für das-Steuerelement festgelegt wurden.

    |Eigenschaft|Erklärung der Einstellung|
    |--------------| - |
    |**DataSource**|Visual Studio legt diese Eigenschaft auf die <xref:System.Windows.Forms.BindingSource> fest, die für die auf das Steuerelement gezogene Tabelle erstellt wurde (also nicht auf die <xref:System.Windows.Forms.BindingSource>, die bei der Erstellung des Steuerelements erstellt wurde).<br /><br /> Wenn Sie eine Anpassung vornehmen müssen, legen Sie diese auf die <xref:System.Windows.Forms.BindingSource> der Tabelle mit der Spalte fest, die Sie anzeigen möchten.|
    |**DisplayMember**|Visual Studio legt diese Eigenschaft auf die erste Spalte nach dem Primärschlüssel fest, der einen Zeichenfolgendatentyp für die auf das Steuerelement gezogene Tabelle besitzt.<br /><br /> Wenn Sie eine Anpassung vornehmen müssen, legen Sie diese auf den Spaltennamen fest, den Sie anzeigen möchten.|
    |**ValueMember**|Visual Studio legt diese Eigenschaft auf die erste Spalte im Primärschlüssel bzw. – wenn kein Schlüssel definiert ist – auf die erste Spalte in der Tabelle fest.<br /><br /> Wenn Sie eine Anpassung vornehmen müssen, legen Sie diese auf den Primärschlüssel in der Tabelle mit der Spalte fest, die Sie anzeigen möchten.|
    |**SelectedValue**|Visual Studio legt diese Eigenschaft auf die ursprüngliche, aus dem **Datenquellenfenster** gezogene und abgelegte Spalte fest.<br /><br /> Wenn Sie eine Anpassung vornehmen müssen, legen Sie diese auf die Fremdschlüssel Spalte in der zugehörigen Tabelle fest.|

## <a name="see-also"></a>Siehe auch

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
