---
title: 'Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente auf einem Menüband zur Laufzeit'
description: Erfahren Sie, wie Sie das Menüband-Objektmodell zum Aktualisieren der Steuerelemente auf einem Menüband verwenden können, nachdem das Menüband in die Office-Anwendung geladen wurde.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- updating Ribbon controls
- Ribbon [Office development in Visual Studio], dynamic menu
- dynamic menus [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 181fafeb55720b5a97a635a4c2322cf7343643d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937185"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-run-time"></a>Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente auf einem Menüband zur Laufzeit

Diese exemplarische Vorgehensweise veranschaulicht die Verwendung des Menüband-Objektmodells zum Aktualisieren der Steuerelemente auf einem Menüband, nachdem das Menüband in die Office-Anwendung geladen wurde.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

Das Beispiel ruft Daten aus der Beispieldatenbank "Northwind" ab, um ein Kombinationsfeld und ein Menü in Microsoft Office Outlook mit Daten aufzufüllen. Elemente, die Sie in diesen Steuerelementen auswählen, füllen automatisch Felder wie z. b. und **Betreff** in einer e-Mail-Nachricht **auf** .

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen Sie ein neues Outlook VSTO-Add-in-Projekt.

- Entwerfen einer benutzerdefinierten Menü Bandgruppe.

- Fügen Sie die benutzerdefinierte Gruppe einer integrierten Registerkarte hinzu.

- Aktualisieren Sie die Steuerelemente auf dem Menüband zur Laufzeit.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen

Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Erstellen eines neuen Outlook VSTO-Add-in-Projekts

Erstellen Sie zunächst ein neues Outlook VSTO-Add-In-Projekt.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>So erstellen Sie ein neues Outlook VSTO-Add-In-Projekt

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Erstellen Sie in ein Outlook VSTO-Add-in-Projekt mit dem Namen **Ribbon_Update_At_Runtime**.

2. Wählen Sie im Dialogfeld **Neues Projekt** die Option **Projektmappenverzeichnis erstellen** aus.

3. Speichern Sie das Projekt im Standardprojektverzeichnis.

     Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Entwerfen einer benutzerdefinierten Menü Bandgruppe

Das Menüband für dieses Beispiel wird angezeigt, wenn ein Benutzer eine neue e-Mail-Nachricht verfasst. Um eine benutzerdefinierte Gruppe für das Menüband zu erstellen, fügen Sie dem Projekt zunächst ein Menü Band Element hinzu, und entwerfen Sie dann die Gruppe im Menüband-Designer. Diese benutzerdefinierte Gruppe unterstützt Sie beim Generieren von e-Mail-Nachrichten an Kunden durch das Abrufen von Namen und Bestell Verläufen aus einer Datenbank.

### <a name="to-design-a-custom-group"></a>So entwerfen Sie eine benutzerdefinierte Gruppe

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Menüband (Visueller Designer)** aus.

3. Ändern Sie den Namen des neuen Menübands in **CustomerRibbon**, und klicken Sie dann auf **Hinzufügen**.

     Die Datei *CustomerRibbon.cs* oder *CustomerRibbon. vb* wird im Menüband-Designer geöffnet und zeigt eine Standard Registerkarte und-Gruppe an.

4. Klicken Sie auf den Menüband-Designer, um diese auszuwählen.

5. Klicken Sie im Fenster **Eigenschaften** auf den Dropdown Pfeil neben der **RibbonType** -Eigenschaft, und klicken Sie dann auf **Microsoft. Outlook. Mail. Compose**.

     Dadurch kann das Menüband angezeigt werden, wenn der Benutzer eine neue e-Mail-Nachricht in Outlook verfasst.

6. Klicken Sie im Menüband-Designer auf **group1** , um es auszuwählen.

7. Legen Sie im Fenster **Eigenschaften** die **Bezeichnung** auf **Kunden Käufe** fest.

8. Ziehen Sie von der Registerkarte Steuer **Elemente für Office** -Menü Bänder der **Toolbox** ein Kombinations **Feld** auf die Gruppe **Kunden Käufe** .

9. Klicken Sie auf **ComboBox1** , um es auszuwählen.

10. Legen Sie im Fenster **Eigenschaften** die **Bezeichnung** auf **Kunden** fest.

11. Ziehen Sie von der Registerkarte Steuer **Elemente für Office** -Menü Bänder der **Toolbox** ein **Menü** auf die Gruppe **Kunden Käufe** .

12. Legen Sie im Fenster **Eigenschaften** die **Bezeichnung** auf **Produkt gekauft** fest.

13. Legen Sie **Dynamic** auf **true** fest.

     Dies ermöglicht Ihnen das Hinzufügen und Entfernen von Steuerelementen im Menü zur Laufzeit, nachdem das Menüband in die Office-Anwendung geladen wurde.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Hinzufügen der benutzerdefinierten Gruppe zu einer integrierten Registerkarte

Eine integrierte Registerkarte ist eine Registerkarte, die sich bereits auf dem Menüband eines Outlook-Explorers oder Inspektors befindet. In diesem Verfahren fügen Sie die benutzerdefinierte Gruppe einer integrierten Registerkarte hinzu und geben dann die Position der benutzerdefinierten Gruppe auf der Registerkarte an.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>So fügen Sie die benutzerdefinierte Gruppe einer integrierten Registerkarte hinzu

1. Klicken Sie auf die Registerkarte **TabAddins (integriert)** , um Sie auszuwählen.

2. Erweitern Sie im Fenster **Eigenschaften** die Eigenschaft **ControlID** , und legen Sie **OfficeId** auf **TabNewMailMessage** fest.

     Dadurch wird die Gruppe " **Kunden Käufe** " der Registerkarte **Nachrichten** des Menübands hinzugefügt, das in einer neuen e-Mail angezeigt wird.

3. Klicken Sie auf die Gruppe **Kunden Käufe** , um Sie auszuwählen.

4. Erweitern Sie im Fenster **Eigenschaften** die Eigenschaft **Position** , klicken Sie auf den Dropdown Pfeil neben der Eigenschaft **PositionType** , und klicken Sie dann auf **BeforeOfficeId**.

5. Legen Sie die **OfficeId-** Eigenschaft auf **GroupClipBoard** fest.

     Dadurch wird die Gruppe **Kunden Käufe** vor der Gruppe **Zwischenablage** auf der Registerkarte **Nachrichten** positioniert.

## <a name="create-the-data-source"></a>Erstellen der Datenquelle

Verwenden das Fenster **Datenquellen** , um dem Projekt ein typisiertes Dataset hinzuzufügen.

### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle

1. Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.

     Dadurch wird der **Assistent zum Konfigurieren von Datenquellen** gestartet.

2. Wählen Sie **Datenbank** aus, und klicken Sie dann auf **weiter**.

3. Wählen Sie **DataSet** aus, und klicken Sie dann auf **weiter**.

4. Wählen Sie eine Datenverbindung mit der Beispieldatenbank Northwind Microsoft SQL Server Compact 4,0 aus, oder fügen Sie mithilfe der Schaltfläche **neue Verbindung** eine neue Verbindung hinzu.

5. Nachdem eine Verbindung ausgewählt oder erstellt wurde, klicken Sie auf **weiter**.

6. Klicken Sie zum Speichern der Verbindungs Zeichenfolge auf **weiter** .

7. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.

8. Aktivieren Sie das Kontrollkästchen neben jeder der folgenden Tabellen:

    1. **Folgend**

    2. **Auftragsdetails**

    3. **Orders**

    4. **Produkte**

9. Klicken Sie auf **Fertig stellen**.

## <a name="update-controls-in-the-custom-group-at-run-time"></a>Aktualisieren von Steuerelementen in der benutzerdefinierten Gruppe zur Laufzeit

Verwenden Sie Menüband-Objektmodell, um die folgenden Aufgaben auszuführen:

- Fügen Sie Kundennamen zum Kombinations Feld **Customers** hinzu.

- Fügen Sie dem Menü **erworbene Produkte** Menü-und Schaltflächen-Steuerelemente hinzu, die Verkaufsaufträge und verkaufte Produkte darstellen.

- Füllen Sie die Felder "an", "Betreff" und "Text" für neue e-Mail-Nachrichten mit Daten aus dem Kombinations Feld " **Customers** " und dem **erworbenen Produkt**

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>So aktualisieren Sie Steuerelemente in der benutzerdefinierten Gruppe mithilfe des Menüband-Objektmodells

1. Klicken Sie im Menü **Projekt** auf **Verweis hinzufügen**.

2. Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **.net** , wählen Sie die Assembly **System. Data. Linq** aus, und klicken Sie dann auf **OK**.

    Diese Assembly enthält Klassen für die Verwendung von LINQ (Language-Integrated Queries). Sie verwenden LINQ zum Auffüllen der Steuerelemente in der benutzerdefinierten Gruppe mit Daten aus der Datenbank "Northwind".

3. Klicken Sie in **Projektmappen-Explorer** auf **CustomerRibbon.cs** oder **CustomerRibbon. vb** , um es auszuwählen.

4. Klicken Sie im Menü **Ansicht** auf **Code**.

    Die Menüband-Codedatei wird im Code-Editor geöffnet.

5. Fügen Sie am Anfang der Menüband-Codedatei die folgenden Anweisungen hinzu. Diese Anweisungen ermöglichen den einfachen Zugriff auf LINQ-Namespaces und den Namespace der primären Interopassembly (PIA) von Outlook.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. Fügen Sie in der-Klasse den folgenden Code hinzu `CustomerRibbon` . Dieser Code deklariert die Datentabelle und die Tabellenadapter, die Sie zum Speichern von Informationen aus den Kunden-, Bestellungen-, Bestelldetails- und Produkttabellen der Datenbank "Northwind" verwenden.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. Fügen Sie der Klasse `CustomerRibbon` den folgenden Codeblock hinzu. Mit diesem Code werden drei Hilfsmethoden hinzugefügt, die zur Laufzeit Steuerelemente für das Menüband erstellen.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. Ersetzen Sie die `CustomerRibbon_Load`-Ereignishandlermethode durch den folgenden Code. Dieser Code verwendet eine LINQ-Abfrage, um die folgenden Aufgaben auszuführen:

   - Füllen Sie das Kombinations Feld **Customers** mit der ID und dem Namen von 20 Kunden in der Northwind-Datenbank.

   - Aufrufen der Hilfsmethode `PopulateSalesOrderInfo`. Diese Methode aktualisiert das **productspurgejagt** -Menü mit Bestellnummern, die sich auf den aktuell ausgewählten Kunden beziehen.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. Fügen Sie der `CustomerRibbon` -Klasse den folgenden Code hinzu. Dieser Code verwendet LINQ-Abfragen, um die folgenden Aufgaben auszuführen:

   - Fügt dem Menü **productspurgejagt** für jeden Verkaufsauftrag, der sich auf den ausgewählten Kunden bezieht, ein Untermenü hinzu.

   - Hinzufügen von Schaltflächen zu jedem Untermenü für die Produkte, die sich auf die Bestellung beziehen.

   - Hinzufügen von Ereignishandlern zu jeder Schaltfläche.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. Doppelklicken Sie in **Projektmappen-Explorer** auf die Menüband-Codedatei.

     Der Menüband-Designer wird geöffnet.

11. Doppelklicken Sie im Menüband-Designer auf das Kombinations Feld **Kunden** .

     Die Menüband-Codedatei wird im Code-Editor geöffnet, und der `ComboBox1_TextChanged`-Ereignishandler wird angezeigt.

12. Ersetzen Sie den `ComboBox1_TextChanged` -Ereignishandler durch den folgenden Code. Mit diesem Code werden die folgenden Aufgaben durchgeführt:

    - Aufrufen der Hilfsmethode `PopulateSalesOrderInfo`. Diese Methode aktualisiert das Menü " **Produkte gekauft** " mit Verkaufsaufträgen, die sich auf den ausgewählten Kunden beziehen.

    - Aufrufen der Hilfsmethode `PopulateMailItem` und Übergeben des aktuellen Texts, der den Namen des ausgewählten Kunden darstellt. Diese Methode füllt die Felder "an", "Betreff" und "Text" neuer e-Mail-Nachrichten.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. Fügen Sie der `Click` -Klasse den folgenden `CustomerRibbon` -Ereignishandler hinzu. Mit diesem Code wird der Name ausgewählter Produkte dem Feld Text der neuen e-Mail-Nachrichten hinzugefügt.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. Fügen Sie der `CustomerRibbon` -Klasse den folgenden Code hinzu. Mit diesem Code werden die folgenden Aufgaben durchgeführt:

    - Füllt die Zeile neuer e-Mail-Nachrichten mithilfe der e-Mail-Adresse des aktuell ausgewählten Kunden auf.

    - Fügt Text zu den Feldern Betreff und Text der neuen e-Mail-Nachrichten hinzu.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>Testen der Steuerelemente in der benutzerdefinierten Gruppe

Wenn Sie ein neues e-Mail-Formular in Outlook öffnen, wird eine benutzerdefinierte Gruppe mit dem Namen **Kunden Käufe** auf der Registerkarte **Nachrichten** des Menübands angezeigt.

Wählen Sie zum Erstellen einer e-Mail-nach Verfolgungs Nachricht einen Kunden aus, und wählen Sie dann die vom Kunden erworbenen Produkte aus. Die Steuerelemente in der Gruppe **Kunden Käufe** werden zur Laufzeit mit Daten aus der Northwind-Datenbank aktualisiert.

### <a name="to-test-the-controls-in-the-custom-group"></a>So testen Sie die Steuerelemente in der benutzerdefinierten Gruppe

1. Drücken Sie **F5** , um das Projekt auszuführen.

     Outlook wird gestartet.

2. Zeigen Sie in Outlook im Menü **Datei** auf **neu**, und klicken Sie dann auf e- **Mail-Nachricht**.

     Die folgenden Aktionen werden ausgeführt:

    - Eine neues Inspektor-Fenster für E-Mail-Nachrichten wird angezeigt.

    - Auf der Registerkarte **Nachricht** des Menübands wird die Gruppe **Kunden Käufe** vor der Gruppe **Zwischenablage** angezeigt.

    - Das Kombinations Feld **Customers** in der Gruppe wird mit den Namen der Kunden in der Northwind-Datenbank aktualisiert.

3. Wählen Sie auf der Registerkarte **Nachricht** des Menübands in der Gruppe **Kunden Käufe** einen Kunden aus dem Kombinations Feld **Kunden** aus.

     Die folgenden Aktionen werden ausgeführt:

    - Das Menü " **erworbene Produkte** " wird aktualisiert und zeigt jeden Verkaufsauftrag für den ausgewählten Kunden an.

    - Jedes Bestellungsuntermenü wird so aktualisiert, dass die in der betreffenden Bestellung gekauften Produkte angezeigt werden.

    - Die e-Mail-Adresse des ausgewählten Kunden wird der Zeile **an** der e-Mail-Nachricht hinzugefügt, und der Betreff und der Textkörper der e-Mail-Nachricht werden mit Text aufgefüllt.

4. Klicken Sie auf das Menü **Produkte Einkäufe** , zeigen Sie auf einen beliebigen Verkaufsauftrag, und klicken Sie dann auf ein Produkt aus der Bestellung.

     Der Produktname wird dem Nachrichtentext der E-Mail-Nachricht hinzugefügt.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Anpassen der Office-Benutzeroberfläche finden Sie in diesen Themen:

- Fügen Sie jeder Anpassung auf Dokumentebene kontextbasierte Benutzeroberfläche hinzu. Weitere Informationen finden Sie unter [Übersicht über den Aktions](../vsto/actions-pane-overview.md)Bereich.

- Erweitern Sie ein standardmäßiges oder benutzerdefiniertes Microsoft Office Outlook-Formular. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Entwerfen eines Outlook-Formular Bereichs](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu Outlook. Weitere Informationen finden Sie unter [benutzerdefinierte Aufgaben](../vsto/custom-task-panes.md)Bereiche.

## <a name="see-also"></a>Weitere Informationen

- [Zugreifen auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Language-Integrated Query (LINQ)](/dotnet/csharp/linq/index)
- [Gewusst wie: Starten der Anpassung des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Übersicht über das Ribbon-Objektmodell](../vsto/ribbon-object-model-overview.md)
- [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Vorgehensweise: Ändern der Position einer Registerkarte im Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)
- [Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Gewusst wie: Exportieren eines Menübands aus dem Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Gewusst wie: Anzeigen von Add-in-Benutzeroberflächen Fehlern](../vsto/how-to-show-add-in-user-interface-errors.md)