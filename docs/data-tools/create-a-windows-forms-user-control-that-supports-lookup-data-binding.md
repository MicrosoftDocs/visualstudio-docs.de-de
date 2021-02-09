---
title: Verwenden von Nachschlage Tabellen in Datenbindung-Windows Forms
description: Erfahren Sie, wie Sie mithilfe der LookupBindingPropertiesAttribute-Klasse in Visual Studio ein Windows Forms Benutzer Steuerelement erstellen, das die Datenbindung für die Suche unterstützt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 0eeb3e768370066bf93afc766d4d7f67d8d39a1d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859072"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Erstellen eines Windows Forms-Benutzersteuerelements, das Nachschlagedatenbindung unterstützt

Zum Anzeigen von Daten in Windows Forms können Sie die in der **Toolbox** vorhandenen Steuerelemente verwenden oder, falls die gewünschte Funktionalität in den Standardsteuerelementen nicht verfügbar ist, benutzerdefinierte Steuerelemente erstellen. Diese exemplarische Vorgehensweise erläutert, wie Sie ein Steuerelement erstellen, das <xref:System.ComponentModel.LookupBindingPropertiesAttribute> implementiert. Steuerelemente, die <xref:System.ComponentModel.LookupBindingPropertiesAttribute> implementieren, können drei Eigenschaften enthalten, die an Daten gebunden werden können. Solche Steuerelemente ähneln einem <xref:System.Windows.Forms.ComboBox>-Steuerelement.

Weitere Informationen zum Erstellen von Steuerelementen finden Sie [unter Entwickeln von Windows Forms-Steuerelementen zur Entwurfszeit](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Beim Erstellen von Steuerelementen, die in Datenbindungsszenarios verwendet werden sollen, müssen Sie eines der folgenden Datenbindungsattribute implementieren:

|Verwendung des Daten Bindungs Attributs|
| - |
|Implementieren Sie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> für einfache Steuerelemente, die eine einzige Spalte (oder Eigenschaft) von Daten anzeigen, wie das <xref:System.Windows.Forms.TextBox>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms Benutzer Steuer Elements, das die einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementieren Sie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, wie das <xref:System.Windows.Forms.DataGridView>-Steuerelement. Weitere Informationen finden Sie unter [Erstellen eines Windows Forms Benutzer Steuer Elements, das eine komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementieren Sie <xref:System.ComponentModel.LookupBindingPropertiesAttribute> für Steuerelemente, die Listen (oder Tabellen) von Daten anzeigen, aber auch eine einzelne Spalte oder Eigenschaft darstellen müssen, wie das <xref:System.Windows.Forms.ComboBox>-Steuerelement. (Dieser Prozess wird in dieser exemplarischen Vorgehensweise beschrieben.)|

In dieser exemplarischen Vorgehensweise wird ein Nachschlagesteuerelement erstellt, das an Daten aus zwei Tabellen gebunden ist. In diesem Beispiel werden die Tabellen `Customers` und `Orders` aus der Beispieldatenbank Northwind verwendet. Das Nachschlage Steuerelement wird an das `CustomerID` Feld aus der `Orders` Tabelle gebunden. Dieser Wert wird verwendet, um die `CompanyName` Tabelle aus der `Customers` Tabelle zu suchen.

In dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

- Erstellen Sie eine neue **Windows Forms Anwendung**.

- Ihrem Projekt ein neues **Benutzersteuerelement** hinzufügen.

- Entwerfen des Benutzersteuerelements im visuellen Designer.

- Implementieren des `LookupBindingProperty`-Attributs.

- Erstellen Sie mit dem Assistenten zum **Konfigurieren von Datenquellen** ein DataSet.

- Die Spalte **CustomerID** in der Tabelle **Orders** im **Datenquellenfenster** festlegen, um das neue Steuerelement zu verwenden.

- Erstellen eines Formulars, um Daten in dem neuen Steuerelement anzuzeigen.

## <a name="prerequisites"></a>Voraussetzungen

In dieser exemplarischen Vorgehensweise werden SQL Server Express localdb-und Northwind-Beispieldatenbank verwendet.

1. Wenn Sie nicht über SQL Server Express localdb verfügen, installieren Sie es entweder über die [SQL Server Express Downloadseite](https://www.microsoft.com/sql-server/sql-server-editions-express)oder über das **Visual Studio-Installer**. Im **Visual Studio-Installer** können Sie SQL Server Express localdb als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** oder als einzelne Komponente installieren.

2. Installieren Sie die Beispieldatenbank Northwind, indem Sie die folgenden Schritte ausführen:

    1. Öffnen Sie in Visual Studio das Fenster **SQL Server-Objekt-Explorer** . (SQL Server-Objekt-Explorer wird als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** im Visual Studio-Installer installiert.) Erweitern Sie den Knoten **SQL Server** . Klicken Sie mit der rechten Maustaste auf die localdb-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren Sie das [Northwind-Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Mit diesem T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript in den Abfrage-Editor ein, und klicken Sie dann auf die Schaltfläche **Ausführen** .

       Nach kurzer Zeit wird die Ausführung der Abfrage abgeschlossen und die Datenbank Northwind erstellt.

## <a name="create-a-windows-forms-app-project"></a>Erstellen eines Windows Forms-App-Projekts

Der erste Schritt besteht darin, ein **Windows Forms Anwendungs** Projekt zu erstellen.

1. Wählen Sie in Visual Studio im Menü **Datei** die Optionen **Neu** > **Projekt** aus.

2. Erweitern Sie entweder **Visual c#** oder **Visual Basic** im linken Bereich, und wählen Sie dann **Windows-Desktop** aus.

3. Wählen Sie im mittleren Bereich den **Windows Forms App** -Projekttyp aus.

4. Nennen Sie das Projekt **LookupControlWalkthrough**, und wählen Sie dann **OK** aus.

     Das Projekt **LookupControlWalkthrough** wird erstellt und dem **Projektmappen-Explorer** hinzugefügt.

## <a name="add-a-user-control-to-the-project"></a>Hinzufügen eines Benutzersteuerelements zum Projekt

In dieser exemplarischen Vorgehensweise wird aus einem **Benutzersteuerelement** ein Nachschlagesteuerelement erstellt. Fügen Sie dem Projekt **LookupControlWalkthrough** zunächst also ein **Benutzersteuerelement** hinzu.

1. Klicken Sie im Menü **Projekt** auf **Benutzersteuerelement hinzufügen**.

2. Geben `LookupBox` Sie in den Bereich **Name** ein, und klicken Sie dann auf **Hinzufügen**.

     Das **LookupBox**-Steuerelement wird dem **Projektmappen-Explorer** hinzugefügt und im Designer geöffnet.

## <a name="design-the-lookupbox-control"></a>Entwerfen des LookupBox-Steuer Elements

Um das LookupBox-Steuerelement zu entwerfen, ziehen Sie ein <xref:System.Windows.Forms.ComboBox> aus der **Toolbox** auf die Entwurfs Oberfläche des Benutzer Steuer Elements.

## <a name="add-the-required-data-binding-attribute"></a>Hinzufügen des erforderlichen Daten Bindungs Attributs

Implementieren Sie für Nachschlagesteuerelemente, die Datenbindung unterstützen, das <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

1. Wechseln Sie für das **LookupBox**-Steuerelement zur Codeansicht. (Wählen Sie im Menü **Ansicht** den Befehl **Code** aus.)

2. Ersetzen Sie den Code in `LookupBox` durch folgenden Code:

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen** aus.

## <a name="create-a-data-source-from-your-database"></a>Erstellen einer Datenquelle aus der Datenbank

In diesem Schritt wird mit dem **Assistenten zum Konfigurieren von Datenquellen** eine Datenquelle erstellt, die auf den Tabellen `Customers` und `Orders` der Beispieldatenbank Northwind basiert.

1. Um das Fenster **Datenquellen** zu öffnen, klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

2. Wählen Sie im **Datenquellen** Fenster die Option **neue Datenquelle hinzufügen** aus, um den Assistenten zum **Konfigurieren von Datenquellen** zu starten.

3. Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.

4. Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** einen der folgenden Schritte aus:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

    - Klicken Sie auf **Neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu öffnen.

5. Falls die Datenbank ein Kennwort erfordern sollte, aktivieren Sie die Option für die Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.

6. Klicken Sie auf der Seite **Save connection string to the Application Configuration file** (Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern) auf **Weiter**.

7. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.

8. Wählen Sie die Tabellen `Customers` und `Orders` aus, und klicken Sie dann auf **Fertig stellen**.

     Das **NorthwindDataSet** wird dem Projekt hinzugefügt, und die `Customers` Tabellen und werden `Orders` im Fenster **Datenquellen** angezeigt.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Festlegen der Spalte "CustomerID" der Tabelle "Orders" auf die Verwendung des LookupBox-Steuer Elements

Im **Datenquellenfenster** können Sie vor dem Ziehen von Elementen auf das Formular festlegen, welches Steuerelement erstellt werden soll.

1. Öffnen Sie **Form1** im Designer.

2. Erweitern Sie im **Datenquellenfenster** den Knoten **Customers**.

3. Erweitern Sie den Knoten **Orders** (denjenigen, der sich im Knoten **Customers** unterhalb der Spalte **Fax** befindet).

4. Klicken Sie im Knoten **Orders** auf den Dropdownpfeil, und wählen Sie in der Steuerelementliste die Option **Details** aus.

5. Klicken Sie in der Spalte **CustomerID** (im Knoten **Orders**) auf den Dropdownpfeil, und wählen Sie **Anpassen** aus.

6. Wählen Sie im Dialogfeld **Data UI Customization Options** (Optionen für die Anpassung der Datenbenutzeroberfläche) in der Liste **Zugeordnete Steuerelemente** den Eintrag **LookupBox** aus.

7. Klicken Sie auf **OK**.

8. Klicken Sie in der Spalte **CustomerID** auf den Dropdownpfeil, und wählen Sie **LookupBox** aus.

## <a name="add-controls-to-the-form"></a>Hinzufügen von Steuerelementen zu dem Formular

Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellenfenster** auf **Form1** ziehen.

Wenn Sie Daten gebundene Steuerelemente auf dem Windows Form erstellen möchten, ziehen Sie den Knoten **Orders** aus dem **Datenquellen** Fenster auf das Windows Form, und überprüfen Sie, ob das **LookupBox** -Steuerelement zum Anzeigen der Daten in der Spalte verwendet wird `CustomerID` .

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Binden Sie das Steuerelement, um CompanyName aus der Tabelle Customers zu suchen.

Wenn Sie die Such Bindungen einrichten möchten, wählen Sie im Fenster **Datenquellen** den Haupt Knoten **Customers** aus, und ziehen Sie ihn in das Kombinations Feld in **CustomerIDLookupBox** auf **Form1**.

Damit wird die Datenbindung so eingerichtet, dass der Wert für `CompanyName` aus der Tabelle `Customers` angezeigt und gleichzeitig der Wert für `CustomerID` aus der Tabelle `Orders` beibehalten wird.

## <a name="run-the-application"></a>Ausführen der Anwendung

- Drücken Sie **F5**, um die Anwendung auszuführen.

- Navigieren Sie durch einige Datensätze, und prüfen Sie, ob im `LookupBox`-Steuerelement der Wert von `CompanyName` angezeigt wird.

## <a name="see-also"></a>Weitere Informationen

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
