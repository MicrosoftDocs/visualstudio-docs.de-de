---
title: Erstellen eines Windows Forms Benutzer Steuer Elements, das die einfache Datenbindung unterstützt | Microsoft-Dokumentation
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
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf30a38384863c9ba5a8af35af3326a51058d831
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668769"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Erstellen eines Windows Forms-Benutzersteuerelements, das die einfache Datenbindung unterstützt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zum Anzeigen von Daten in Formularen in Windows-Anwendungen können Sie die in der **Toolbox** vorhandenen Steuerelemente verwenden oder, falls die gewünschte Funktionalität in den Standardsteuerelementen nicht verfügbar ist, benutzerdefinierte Steuerelemente erstellen. Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.DefaultBindingPropertyAttribute> implementiert. Steuerelemente, die <xref:System.ComponentModel.DefaultBindingPropertyAttribute> implementieren, können eine Eigenschaft enthalten, die an Daten gebunden werden kann. Solche Steuerelemente sind vergleichbar mit <xref:System.Windows.Forms.TextBox> oder <xref:System.Windows.Forms.CheckBox>.

 Weitere Informationen zum Erstellen von Steuerelementen finden Sie [unter Entwickeln von Windows Forms-Steuerelementen zur Entwurfszeit](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).

 Beim Erstellen von Steuerelementen für die Verwendung in Daten Bindungs Szenarien sollten Sie eines der folgenden Daten Bindungs Attribute implementieren:

|Verwendung des Daten Bindungs Attributs|
|-----------------------------------|
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte (oder Eigenschaft) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>-Steuerelement. (Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.)|
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms Benutzer Steuer Elements, das eine komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementieren Sie die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> auf Steuerelementen wie einem <xref:System.Windows.Forms.ComboBox>,das Listen (oder Tabellen) von Daten anzeigt, aber auch in einer einzelnen Spalte oder Eigenschaft vorhanden sein muss. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms Benutzer Steuer Elements, das die Datenbindung für die Suche unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 In dieser exemplarischen Vorgehensweise wird ein einfaches Steuerelement erstellt, das Daten aus einer einzelnen Spalte in einer Tabelle anzeigt. In diesem Beispiel wird die Spalte `Phone` der Tabelle `Customers` aus der Beispieldatenbank Northwind verwendet. Das einfache Benutzer Steuerelement zeigt die Telefonnummern der Kunden in einem Standardformat für die Telefonnummer an, unter Verwendung eines <xref:System.Windows.Forms.MaskedTextBox> und Festlegen der Maske auf eine Telefonnummer.

 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

- Erstellen Sie eine neue **Windows-Anwendung**.

- Ihrem Projekt ein neues **Benutzersteuerelement** hinzufügen.

- Entwerfen des Benutzersteuerelements im visuellen Designer.

- Implementieren des `DefaultBindingProperty`-Attributs.

- Erstellen Sie mit dem Assistenten zum **Konfigurieren von Datenquellen** ein DataSet.

- Legen Sie für die Spalte **Phone** im **Datenquellenfenster** fest, dass das neue Steuerelement verwendet wird.

- Erstellen eines Formulars, um Daten in dem neuen Steuerelement anzuzeigen.

## <a name="prerequisites"></a>Voraussetzungen
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Zugriff auf die Beispieldatenbank Northwind.

## <a name="create-a-windows-application"></a>Erstellen einer Windows-Anwendung
 Der erste Schritt besteht darin, eine **Windows-Anwendung**zu erstellen.

#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt

1. Erstellen Sie in Visual Studio im Menü **Datei** ein neues **Projekt**.

2. Nennen Sie das Projekt **SimpleControlWalkthrough**.

3. Wählen Sie **Windows-Anwendung** , und klicken Sie auf **OK**. Weitere Informationen finden Sie unter [Client Anwendungen](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Das Projekt **SimpleControlWalkthrough** wird erstellt und dem **Projektmappen-Explorer** hinzugefügt.

## <a name="add-a-user-control-to-the-project"></a>Hinzufügen eines Benutzersteuerelements zum Projekt
 In dieser exemplarischen Vorgehensweise wird ein einfaches Daten Bindungs Steuerelement aus einem **Benutzer Steuer**Element erstellt. Fügen Sie daher dem Projekt **SimpleControlWalkthrough** ein **Benutzer Steuer** Element hinzu.

#### <a name="to-add-a-user-control-to-the-project"></a>So fügen Sie dem Projekt ein Benutzersteuerelement hinzu

1. Klicken Sie im Menü **Projekt** auf **Benutzersteuerelement hinzufügen**.

2. Geben `PhoneNumberBox` Sie in den Bereich Name ein, und klicken Sie auf **Hinzufügen**.

     Das **PhoneNumberBox**-Steuerelement wird dem **Projektmappen-Explorer** hinzugefügt und im Designer geöffnet.

## <a name="design-the-phonenumberbox-control"></a>Entwerfen des PhoneNumberBox-Steuer Elements
 Diese exemplarische Vorgehensweise erweitert das vorhandene <xref:System.Windows.Forms.MaskedTextBox>, sodass das `PhoneNumberBox`-Steuerelement erstellt wird.

#### <a name="to-design-the-phonenumberbox-control"></a>Entwerfen des PhoneNumberBox-Steuerelements

1. Ziehen Sie ein <xref:System.Windows.Forms.MaskedTextBox> aus der **Toolbox** auf die Entwurfsoberfläche des Benutzersteuerelements.

2. Klicken Sie auf das Smarttag auf das soeben gezogene <xref:System.Windows.Forms.MaskedTextBox>-Objekt, und klicken Sie dann auf **Maske festlegen**.

3. Wählen Sie **Telefonnummer** im Dialogfeld **Eingabeformat** aus, und klicken Sie auf **OK**, um die Maske festzulegen.

## <a name="add-the-required-data-binding-attribute"></a>Hinzufügen des erforderlichen Daten Bindungs Attributs
 Implementieren Sie für einfache Steuerelemente, die Datenbindung unterstützen, das <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.

#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>So implementieren Sie das Attribut DefaultBindingProperty

1. Wechseln Sie für das `PhoneNumberBox`-Steuerelement zur Codeansicht. (Wählen Sie im Menü **Ansicht** den Befehl **Code** aus.)

2. Ersetzen Sie den Code in `PhoneNumberBox` durch folgenden Code:

     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]

3. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus.

## <a name="create-a-data-source-from-your-database"></a>Erstellen einer Datenquelle aus der Datenbank
 In diesem Schritt wird der Assistent zum **Konfigurieren von Datenquellen** verwendet, um eine Datenquelle basierend auf der `Customers` Tabelle in der Northwind-Beispieldatenbank zu erstellen. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können.

#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle

1. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

2. Wählen Sie im **Datenquellen** Fenster die Option **neue Datenquelle hinzufügen** aus, um den Assistenten zum **Konfigurieren von Datenquellen** zu starten.

3. Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie dann auf **Weiter**.

4. Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** aus einen der folgenden Schritte aus:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

    - Klicken Sie auf **Neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu öffnen.

5. Falls die Datenbank ein Kennwort erfordern sollte, aktivieren Sie die Option für die Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.

6. Klicken Sie auf der Seite **Save connection string to the Application Configuration file** (Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern) auf **Weiter**.

7. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.

8. Wählen Sie die `Customers`-Tabelle aus, und klicken Sie anschließend auf **Fertig stellen**.

     Das **NorthwindDataSet** wird dem Projekt hinzugefügt, und die `Customers` Tabelle wird im **Datenquellen** Fenster angezeigt.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Festlegen der telefonspalte für die Verwendung des PhoneNumberBox-Steuer Elements
 Im **Datenquellenfenster** können Sie vor dem Ziehen von Elementen auf das Formular festlegen, welches Steuerelement erstellt werden soll.

#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>So legen Sie die Bindung der Spalte "Telefon" an das PhoneNumberBox-Steuerelement fest

1. Öffnen Sie **Form1** im Designer.

2. Erweitern Sie im **Datenquellenfenster** den Knoten **Customers**.

3. Klicken Sie auf den Dropdownpfeil auf dem Knoten **Customers**, und wählen Sie **Details** aus der Steuerelementliste aus.

4. Klicken Sie auf den Dropdownpfeil auf der Spalte **Phone**, und wählen Sie **Anpassen** aus.

5. Wählen Sie im Dialogfeld **Data UI Customization Options** (Optionen für die Anpassung der Datenbenutzeroberfläche) in der Liste **Zugeordnete Steuerelemente** den Eintrag **PhoneNumberBox** aus.

6. Klicken Sie auf den Dropdownpfeil auf der Spalte **Phone**, und wählen Sie **PhoneNumberBox** aus.

## <a name="addcontrols-to-the-form"></a>Addcontrols zum Formular
 Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellenfenster** auf das Formular ziehen.

#### <a name="to-create-data-bound-controls-on-the-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Formular

- Ziehen Sie den Haupt Knoten **Customers** aus dem **Datenquellen** Fenster auf das Formular, und überprüfen Sie, ob das- `PhoneNumberBox` Steuerelement zum Anzeigen der Daten in der Spalte verwendet wird `Phone` .

     Auf dem Formular werden datengebundene Steuerelemente mit beschreibenden Bezeichnungen sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.

## <a name="run-the-application"></a>Ausführen der Anwendung

#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus

- Drücken Sie F5, um die Anwendung auszuführen.

## <a name="next-steps"></a>Nächste Schritte
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines Steuerelements, das Datenbindung unterstützt, noch weitere Schritte ausführen. Zu den typischen nächsten Schritten gehören Folgende:

- Platzieren der benutzerdefinierten Steuerelemente in eine Steuerelementbibliothek, sodass Sie sie in anderen Anwendungen wiederverwenden können.

- Erstellen von Steuerelementen, die komplexere Datenbindungsszenarien unterstützen. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms Benutzer Steuer Elements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) , und [Erstellen eines Windows Forms Benutzer Steuer Elements, das die Datenbindung für die Suche unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Weitere Informationen
 [Binden von Windows Forms Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [legen Sie das Steuerelement fest, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md) .
