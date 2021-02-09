---
title: Einfache Daten-App mit WPF und Entity Framework 6
description: In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie eine einfache Forms-over-Data-app in Visual Studio mit Windows Presentation Foundation (WPF) und Entity Framework 6 erstellen.
ms.custom: SEO-VS-2020
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 52c9d8ca4af6467c6db21be64083b5bf64af0b6a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859189"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Erstellen einer einfachen Datenanwendung mit WPF und Entity Framework 6

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie eine grundlegende "Forms over Data"-Anwendung in Visual Studio erstellen. Die APP verwendet SQL Server localdb, die Northwind-Datenbank, Entity Framework 6 (nicht Entity Framework Core) und Windows Presentation Foundation für .NET Framework (nicht .net Core). Es zeigt, wie Sie eine einfache Datenbindung mit einer Master/Detail-Ansicht durchführen können. Außerdem enthält Sie einen benutzerdefinierten Bindungs Navigator mit Schaltflächen für "weiter", "nach oben", " **an den Anfang** **", "** an den Anfang **", "**  **an den Ende**"

Der Schwerpunkt dieses Artikels liegt auf der Verwendung von Data Tools in Visual Studio. es wird nicht versucht, die zugrunde liegenden Technologien in beliebiger Tiefe zu erläutern. Dabei wird davon ausgegangen, dass Sie über eine grundlegende Vertrautheit mit XAML, Entity Framework und SQL verfügen. In diesem Beispiel wird auch die Architektur Model-View-ViewModel (MVVM) nicht veranschaulicht, die für WPF-Anwendungen standardmäßig verwendet wird. Sie können diesen Code jedoch mit wenigen Änderungen in Ihre eigene MVVM-Anwendung kopieren.

## <a name="install-and-connect-to-northwind"></a>Installieren von und Herstellen einer Verbindung mit Northwind

In diesem Beispiel werden SQL Server Express localdb-und Northwind-Beispieldatenbank verwendet. Wenn der ADO.NET-Datenanbieter für dieses Produkt Entity Framework unterstützt, sollte es auch mit anderen SQL-Datenbankprodukten funktionieren.

1. Wenn Sie nicht über SQL Server Express localdb verfügen, installieren Sie es entweder über die [SQL Server Express Downloadseite](https://www.microsoft.com/sql-server/sql-server-editions-express)oder über das **Visual Studio-Installer**. Im **Visual Studio-Installer** können Sie SQL Server Express LocalDB als Teil der Workload **.NET-Desktopentwicklung** oder als einzelne Komponente installieren.

2. Installieren Sie die Beispieldatenbank Northwind, indem Sie die folgenden Schritte ausführen:

    1. Öffnen Sie in Visual Studio das Fenster **SQL Server-Objekt-Explorer** . (**SQL Server-Objekt-Explorer** wird als Teil der Arbeitsauslastung für die **Datenspeicherung und-Verarbeitung** im **Visual Studio-Installer** installiert.) Erweitern Sie den Knoten **SQL Server** . Klicken Sie mit der rechten Maustaste auf die localdb-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren Sie das [Northwind-Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Mit diesem T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript in den Abfrage-Editor ein, und klicken Sie dann auf die Schaltfläche **Ausführen** .

       Nach kurzer Zeit wird die Ausführung der Abfrage abgeschlossen und die Datenbank Northwind erstellt.

3. [Fügen Sie neue Verbindungen](../data-tools/add-new-connections.md) für Northwind hinzu.

## <a name="configure-the-project"></a>Konfigurieren des Projekts

1. Erstellen Sie in Visual Studio ein neues c#- **WPF-App** -Projekt.

2. Fügen Sie das nuget-Paket für Entity Framework 6 hinzu. Wählen Sie in **Projektmappen-Explorer** den Projekt Knoten aus. Wählen Sie im Hauptmenü **Projekt**  >  **nuget-Pakete verwalten** aus.

     ![Menü Element "nuget-Pakete verwalten"](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3. Klicken Sie im **nuget-Paket-Manager** auf den Link zum **Durchsuchen** . Entity Framework ist wahrscheinlich das oberste Paket in der Liste. Klicken Sie im rechten Bereich auf **Installieren** , und befolgen Sie die Anweisungen. Das Ausgabefenster gibt Aufschluss darüber, wann die Installation abgeschlossen ist.

     ![Entity Framework nuget-Pakets](../data-tools/media/raddata_vs2015_nuget_ef.png)

4. Nun können Sie Visual Studio verwenden, um ein Modell zu erstellen, das auf der Northwind-Datenbank basiert.

## <a name="create-the-model"></a>Erstellen des Modells

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie   >  **Neues Element** hinzufügen aus. Wählen Sie im linken Bereich unter dem Knoten c# die Option **Daten** aus, und wählen Sie im mittleren Bereich die Option **ADO.NET Entity Data Model** aus.

   ![Neues Element Entity Framework Modell](../data-tools/media/raddata-ef-new-project-item.png)

2. Nennen Sie das Modell, `Northwind_model` und wählen Sie **OK** aus. Der **Entity Data Model-Assistent** wird geöffnet. Wählen Sie **EF Designer aus Datenbank aus** , und klicken Sie dann auf **weiter**.

   ![EF-Modell aus der Datenbank](../data-tools/media/raddata-ef-model-from-database.png)

3. Geben Sie auf dem nächsten Bildschirm Ihre localdb-Verbindung mit Northwind (z. b. (localdb) \mssqllocaldb) ein, oder wählen Sie Sie aus, und klicken Sie auf **weiter**.

4. Wählen Sie auf der nächsten Seite des Assistenten die Tabellen, gespeicherten Prozeduren und anderen Datenbankobjekte aus, die im Entity Framework Modell enthalten sein sollen. Erweitern Sie den Knoten dbo in der Strukturansicht, und wählen Sie **Kunden**, **Bestellungen** und **Bestell Details** aus. Belassen Sie die Standardeinstellungen, und klicken Sie auf **Fertig** stellen

    ![Datenbankobjekte für das Modell auswählen](../data-tools/media/raddata-choose-ef-objects.png)

5. Der Assistent generiert die c#-Klassen, die das Entity Framework Modell darstellen. Die Klassen sind einfache alte c#-Klassen, die wir an die WPF-Benutzeroberfläche übermitteln. Die *edmx* -Datei beschreibt die Beziehungen und anderen Metadaten, die die Klassen den Objekten in der Datenbank zuordnen. Die *TT* -Dateien sind T4-Vorlagen, die den Code generieren, der auf dem Modell basiert und Änderungen an der Datenbank speichert. Sie können alle diese Dateien in **Projektmappen-Explorer** unter dem Knoten Northwind_model sehen:

      ![Projektmappen-Explorer EF-Modelldateien](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    Die Designer Oberfläche für die *edmx* -Datei ermöglicht es Ihnen, einige Eigenschaften und Beziehungen im Modell zu ändern. Der Designer wird in dieser exemplarischen Vorgehensweise nicht verwendet.

6. Die *TT* -Dateien sind universell, und Sie müssen eine von Ihnen für die Arbeit mit WPF-Datenbindung optimieren, was observablecollections erfordert. Erweitern Sie in **Projektmappen-Explorer** den Knoten Northwind_model, bis Sie *Northwind_model. tt* gefunden haben. (Stellen Sie sicher, dass Sie nicht im sind *. Context.tt* -Datei, die sich direkt unterhalb der *edmx* -Datei befindet.)

   - Ersetzen Sie die beiden Vorkommen von <xref:System.Collections.ICollection> durch <xref:System.Collections.ObjectModel.ObservableCollection%601> .

   - Ersetzen Sie das erste Vorkommen von <xref:System.Collections.Generic.HashSet%601> durch <xref:System.Collections.ObjectModel.ObservableCollection%601> in Zeile 51. Ersetzen Sie das zweite Vorkommen des Hashsets nicht.

   - Ersetzen Sie das einzige Vorkommen von <xref:System.Collections.Generic> (um Zeile 431) durch <xref:System.Collections.ObjectModel> .

7. Drücken Sie **STRG** + **UMSCHALT** + **B** , um das Projekt zu erstellen. Wenn der Build abgeschlossen ist, sind die Modellklassen für den Datenquellen-Assistenten sichtbar.

Nun können Sie dieses Modell mit der XAML-Seite verbinden, sodass Sie die Daten anzeigen, navigieren und ändern können.

## <a name="databind-the-model-to-the-xaml-page"></a>DataBind des Modells an die XAML-Seite

Es ist möglich, ihren eigenen Datenbindung-Code zu schreiben, aber es ist viel einfacher, Visual Studio für Sie zu verwenden.

1. Wählen Sie im Hauptmenü **Projekt**  >  **neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu aktivieren. Wählen Sie **Objekt** aus, weil Sie an die Modellklassen und nicht an die Datenbank gebunden sind:

     ![Assistent zum Konfigurieren von Datenquellen mit Objekt Quelle](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2. Erweitern Sie den Knoten für das Projekt, und wählen Sie **Customer** aus. (Quellen für Aufträge werden automatisch aus der Orders-Navigations Eigenschaft in Customer generiert.)

     ![Entitäts Klassen als Datenquellen hinzufügen](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3. Klicken Sie auf **Fertig stellen**.

4. Navigieren Sie in der Code Ansicht zu " *MainWindow. XAML* ". Der XAML-Code wird für dieses Beispiel einfach gehalten. Ändern Sie den Titel von "MainWindow" in einen aussagekräftigeren Namen, und vergrößern Sie seine Höhe und Breite auf 600 x 800. Sie können Sie später jederzeit ändern. Fügen Sie nun die drei Zeilen Definitionen dem Haupt Raster hinzu, eine Zeile für die Navigations Schaltflächen, eine für die Details des Kunden und eine für das Raster, das Ihre Bestellungen anzeigt:

    ```xaml
        <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5. Öffnen Sie nun die Datei " *MainWindow. XAML* ", sodass Sie Sie im Designer anzeigen. Dies bewirkt, dass das Fenster **Datenquellen** als Option im Visual Studio-Fensterrand neben der **Toolbox** angezeigt wird. Klicken Sie auf die Registerkarte, um das Fenster zu öffnen, oder drücken Sie **UMSCHALT** + **alt** + **D** , oder wählen Sie   >  **andere Windows**-  >  **Datenquellen** anzeigen aus. Jede Eigenschaft in der Customers-Klasse wird in einem eigenen Textfeld angezeigt. Klicken Sie zuerst auf den Pfeil im Kombinations Feld **Customers** , und wählen Sie **Details** aus. Ziehen Sie dann den Knoten auf den mittleren Teil der Entwurfs Oberfläche, damit der Designer weiß, dass er in der mittleren Zeile angezeigt werden soll. Wenn Sie ihn falsch angeben, können Sie die Zeile später in der XAML manuell angeben. Standardmäßig werden die Steuerelemente vertikal in einem Raster Element platziert, aber an diesem Punkt können Sie Sie im Formular anordnen. Beispielsweise kann es sinnvoll sein, das Textfeld **Name** oberhalb der Adresse zu platzieren. Die Beispielanwendung für diesen Artikel ordnet die Felder neu an und ordnet Sie in zwei Spalten an.

     ![Kundendaten Quellen Bindung an einzelne Steuerelemente](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     In der Code Ansicht können Sie nun ein neues `Grid` Element in Zeile 1 (die mittlere Zeile) des übergeordneten Rasters sehen. Das übergeordnete Raster verfügt über ein- `DataContext` Attribut, das auf eine CollectionViewSource verweist, die dem-Element hinzugefügt wurde `Windows.Resources` . Wenn das erste Textfeld an die **Adresse** gebunden wird, wird dieser Name der- `Address` Eigenschaft im aktuellen- `Customer` Objekt in der CollectionViewSource zugeordnet.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Wenn ein Kunde in der oberen Hälfte des Fensters sichtbar ist, sollten Sie die Reihenfolge der Bestellungen in der unteren Hälfte des Fensters sehen. Sie zeigen die Aufträge in einem einzelnen Rasteransicht-Steuerelement an. Damit die Master-Detail-Datenbindung erwartungsgemäß funktioniert, ist es wichtig, dass Sie eine Bindung an die Orders-Eigenschaft in der Customers-Klasse und nicht an den separaten Knoten Orders herstellen. Ziehen Sie die Orders-Eigenschaft der Customers-Klasse in die untere Hälfte des Formulars, sodass der Designer Sie in Zeile 2 einfügt:

     ![Ziehen Sie Orders-Klassen als Raster.](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7. Visual Studio hat den gesamten Bindungs Code generiert, der die UI-Steuerelemente mit Ereignissen im Modell verbindet. Alles, was Sie tun müssen, um einige Daten anzuzeigen, ist das Schreiben von Code zum Auffüllen des Modells. Navigieren Sie zunächst zu *MainWindow.XAML.cs* , und fügen Sie der MainWindow-Klasse für den Datenkontext einen Datenmember hinzu. Dieses Objekt, das für Sie generiert wurde, verhält sich ähnlich wie ein Steuerelement, das Änderungen und Ereignisse im Modell nachverfolgt. Außerdem fügen Sie CollectionViewSource-Datenmember für Kunden und Bestellungen sowie die zugehörige Initialisierungs Logik für den Konstruktor hinzu. Der Anfang der Klasse sollte wie folgt aussehen:

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     Fügen Sie eine- `using` Direktive für System. Data. Entity hinzu, um die Load-Erweiterungsmethode in den Gültigkeitsbereich

     ```csharp
     using System.Data.Entity;
     ```

     Scrollen Sie nun nach unten, und suchen Sie nach dem `Window_Loaded` Ereignishandler. Beachten Sie, dass Visual Studio ein CollectionViewSource-Objekt hinzugefügt hat. Dies stellt das NorthwindEntities-Objekt dar, das Sie beim Erstellen des Modells ausgewählt haben. Sie haben das bereits hinzugefügt, sodass Sie es hier nicht benötigen. Ersetzen Sie den Code in `Window_Loaded` , sodass die-Methode jetzt wie folgt aussieht:

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8. Drücken Sie **F5**. Die Details für den ersten Kunden, der in der CollectionViewSource abgerufen wurde, sollten angezeigt werden. Außerdem sollten Ihre Bestellungen im Datenraster angezeigt werden. Die Formatierung ist nicht groß, also korrigieren wir dies. Sie können auch eine Möglichkeit erstellen, die anderen Datensätze anzuzeigen und grundlegende CRUD-Vorgänge durchzuführen.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Anpassen des Seiten Entwurfs und Hinzufügen von Rastern für neue Kunden und Bestellungen

Die von Visual Studio erstellte Standardanordnung ist für Ihre Anwendung nicht ideal. Deshalb stellen wir die endgültige XAML hier bereit, um Sie in Ihren Code zu kopieren. Sie benötigen auch einige "Formulare" (die tatsächlich Raster sind), damit der Benutzer einen neuen Kunden oder eine Bestellung hinzufügen kann. Um einen neuen Kunden und eine Bestellung hinzufügen zu können, benötigen Sie einen separaten Satz von Textfeldern, die nicht an die Daten gebunden sind `CollectionViewSource` . Sie steuern, welches Raster der Benutzer zu einem beliebigen Zeitpunkt sieht, indem Sie die Visible-Eigenschaft in den Handlermethoden festlegen. Schließlich fügen Sie jeder Zeile im Raster Orders eine Lösch Schaltfläche hinzu, um dem Benutzer zu ermöglichen, eine einzelne Bestellung zu löschen.

Fügen Sie zunächst diese Stile dem- `Windows.Resources` Element in " *MainWindow. XAML*" hinzu:

```xaml
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Left"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="23"/>
</Style>
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Right"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="26"/>
    <Setter Property="Width" Value="120"/>
</Style>
```

Ersetzen Sie als nächstes das gesamte äußere Raster durch dieses Markup:

```xaml
<Grid>
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="New Order Form" FontWeight="Bold"/>
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">
         <DataGrid.Columns>
             <DataGridTemplateColumn>
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <Button Content="Delete" Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>
         </DataGrid.Columns>
     </DataGrid>
 </Grid>
```

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Hinzufügen von Schaltflächen zum Navigieren, hinzufügen, aktualisieren und löschen

In Windows Forms-Anwendungen erhalten Sie ein BindingNavigator-Objekt mit Schaltflächen, mit denen Sie durch Zeilen in einer Datenbank navigieren und grundlegende CRUD-Vorgänge ausführen können. WPF bietet keinen BindingNavigator, aber es ist einfach genug, eine zu erstellen. Verwenden Sie dazu Schaltflächen in einem horizontalen StackPanel, und ordnen Sie den Schaltflächen Befehle zu, die an Methoden im Code Behind gebunden sind.

Die Befehls Logik besteht aus vier Teilen: (1) den Befehlen, (2) der Bindungen, (3) den Schaltflächen und (4) den Befehls Handlern im Code-Behind.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Hinzufügen von Befehlen, Bindungen und Schaltflächen in XAML

1. Fügen Sie zunächst die Befehle in der Datei " *MainWindow. XAML* " im- `Windows.Resources` Element hinzu:

    ```xaml
    <RoutedUICommand x:Key="FirstCommand" Text="First"/>
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>
    ```

2. Eine CommandBinding ordnet ein- `RoutedUICommand` Ereignis einer Methode im Code Behind zu. Fügen Sie dieses `CommandBindings` Element nach dem `Windows.Resources` schließenden Tag hinzu:

    ```xaml
    <Window.CommandBindings>
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>
    </Window.CommandBindings>
    ```

3. Fügen Sie nun `StackPanel` mit den Schaltflächen Navigation, hinzufügen, löschen und aktualisieren hinzu. Fügen Sie zunächst diesen Stil zu hinzu `Windows.Resources` :

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Fügen Sie den folgenden Code direkt nach dem `RowDefinitions` für das äußere `Grid` Element in den oberen Bereich der XAML-Seite ein:

    ```xaml
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

### <a name="add-command-handlers-to-the-mainwindow-class"></a>Hinzufügen von Befehls Handlern zur MainWindow-Klasse

Der Code Behind ist nur minimal, mit Ausnahme der Add-und Delete-Methoden. Die Navigation erfolgt durch Aufrufen von Methoden für die View-Eigenschaft der CollectionViewSource. Das `DeleteOrderCommandHandler` zeigt, wie eine Lösch Weitergabe in einer Reihenfolge durchgeführt wird. Wir müssen zunächst die Order_Details löschen, die ihr zugeordnet sind. Fügt der-Auflistung `UpdateCommandHandler` einen neuen Kunden oder eine Bestellung hinzu oder aktualisiert einen vorhandenen Kunden oder eine Bestellung mit den Änderungen, die der Benutzer in den Textfeldern vorgenommen hat.

Fügen Sie diese Handlermethoden der MainWindow-Klasse in *MainWindow.XAML.cs* hinzu. Wenn Ihre CollectionViewSource für die Customers-Tabelle einen anderen Namen aufweist, müssen Sie den Namen in jeder der folgenden Methoden anpassen:

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Ausführen der Anwendung

Drücken Sie **F5**, um mit dem Debuggen zu beginnen. Im Raster werden Kunden-und Bestelldaten angezeigt, und die Navigations Schaltflächen sollten erwartungsgemäß funktionieren. Klicken Sie auf **Commit** , um dem Modell einen neuen Kunden hinzuzufügen, nachdem Sie die Daten eingegeben haben. Klicken Sie auf " **Abbrechen** ", um ein neues Kunden-oder neues Bestellformular zu sichern, ohne die Daten zu speichern. Sie können Änderungen an vorhandenen Kunden und Aufträgen direkt in den Textfeldern vornehmen, und diese Änderungen werden automatisch in das Modell geschrieben.

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Entity Framework-Dokumentation](/ef/)
