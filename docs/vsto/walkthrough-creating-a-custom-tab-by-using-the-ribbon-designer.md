---
title: 'Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer'
description: Erfahren Sie, wie Sie eine benutzerdefinierte Registerkarte erstellen und dann mit dem Menüband-Designer Steuerelemente hinzufügen und positionieren können.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b87113b47ee0dc4d296bb5e206d6d277394160c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962274"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer
  Mit dem Menüband-Designer können Steuerelemente auf der benutzerdefinierten Registerkarte hinzugefügt und positioniert werden.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- [Erstellen von Aktions](#BKMK_CreateActionsPanes)Bereichen.

- [Erstellen Sie eine benutzerdefinierte Registerkarte](#BKMK_CreateCustomTab).

- [Anzeigen und Anzeigen von Aktionsbereichen mithilfe von Schaltflächen auf der Registerkarte "Benutzer](#BKMK_HideShowActionsPane)definiert".

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-an-excel-workbook-project"></a>Erstellen eines Excel-Arbeitsmappenprojekts
 Die Schritte für die Verwendung des Menüband-Designers sind für alle Office-Anwendungen nahezu identisch. In diesem Beispiel wird eine Excel-Arbeitsmappe verwendet.

### <a name="to-create-an-excel-workbook-project"></a>So erstellen Sie ein Excel-Arbeitsmappenprojekt

- Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **MyExcelRibbon**. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet die neue Arbeitsmappe im Designer und fügt das Projekt **MyExcelRibbon** **Projektmappen-Explorer** hinzu.

## <a name="create-actions-panes"></a><a name="BKMK_CreateActionsPanes"></a> Aktionsbereiche erstellen
 Fügen Sie dem Projekt zwei benutzerdefinierte Aktionsbereiche hinzu. Später werden der benutzerdefinierten Registerkarte Schaltflächen hinzugefügt, mit denen diese Aktionsbereiche angezeigt und ausgeblendet werden.

### <a name="to-create-actions-panes"></a>So erstellen Sie Aktionsbereiche

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **aktionspanecontrol** aus, und wählen Sie dann **Hinzufügen** aus.

     Die Datei **ActionsPaneControl1.cs** oder **ActionsPaneControl1. vb** wird im Designer geöffnet.

3. Fügen Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** der Designer Oberfläche eine Bezeichnung hinzu.

4. Legen Sie im **Eigenschaften** Fenster die **Text** -Eigenschaft von Label1 auf **Actions Pane 1** fest.

5. Wiederholen Sie die Schritte 1 bis 5, um einen zweiten Aktionsbereich und eine Bezeichnung zu erstellen. Legen Sie die **Text** -Eigenschaft der zweiten Bezeichnung auf **Actions Pane 2** fest.

## <a name="create-a-custom-tab"></a><a name="BKMK_CreateCustomTab"></a> Erstellen einer benutzerdefinierten Registerkarte
 Eine der Entwurfsrichtlinien für Office-Anwendungen besagt, dass Benutzer immer die Möglichkeit haben sollen, die Benutzeroberfläche von Office-Anwendungen zu steuern. Um diese Funktion für die Aktionsbereiche hinzuzufügen, können Schaltflächen hinzugefügt werden, mit denen jeder Aktionsbereich von einer benutzerdefinierten Registerkarte auf dem Menüband angezeigt und ausgeblendet werden kann. Fügen Sie zum Erstellen einer benutzerdefinierten Registerkarte dem Projekt ein Element vom Typ **Menüband (visueller Designer)** hinzu. Der Designer unterstützt Sie beim Hinzufügen und Anordnen von Steuerelementen, Festlegen von Steuerelementeigenschaften und Behandeln von Ereignissen von Steuerelementen.

### <a name="to-create-a-custom-tab"></a>So erstellen Sie eine benutzerdefinierte Registerkarte

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Menüband (Visueller Designer)** aus.

3. Ändern Sie den Namen des neuen Menübands in **MyRibbon**, und wählen Sie **Hinzufügen** aus.

     Die Datei **MyRibbon.cs** oder **MyRibbon.vb** wird im Menüband-Designer geöffnet. Sie beinhaltet eine standardmäßige Registerkarte und eine Gruppe.

4. Wählen Sie im Menüband-Designer die Standardregisterkarte aus.

5. Erweitern Sie im Fenster **Eigenschaften** die Eigenschaft **ControlID** , und legen Sie dann die **ControlIdType** -Eigenschaft auf **Custom** fest.

6. Legen Sie die **Label** -Eigenschaft auf **meine benutzerdefinierte Registerkarte** fest.

7. Wählen Sie im Menüband-Designer die Option **group1** aus.

8. Legen Sie im Fenster **Eigenschaften** die **Bezeichnung** auf **Aktions** Bereich-Manager fest.

9. Ziehen Sie von der Registerkarte Steuer **Elemente für Office** -Menü Bänder der **Toolbox** eine Schaltfläche auf **group1**.

10. Wählen Sie **Button1** aus.

11. Legen Sie im Fenster **Eigenschaften** die **Bezeichnung Bezeichnung** auf **Show Actions Pane 1** fest.

12. Fügen Sie **group1** eine zweite Schaltfläche hinzu, und legen Sie die **Label** -Eigenschaft auf **Show Actions Pane 2** fest.

13. Ziehen Sie von der Register **Karte Steuer** **Elemente für Office** -Menü Bänder der **Toolbox** ein-Steuerelement auf **group1**.

14. Legen Sie die Eigenschaft **Bezeichnung** auf den Bereich **Aktionen ausblenden** fest.

## <a name="hide-and-show-actions-panes-by-using-buttons-on-the-custom-tab"></a><a name="BKMK_HideShowActionsPane"></a> Ausblenden und Anzeigen von Aktionsbereichen mithilfe von Schaltflächen auf der Registerkarte "Benutzer definiert"
 Im letzten Schritt wird Code hinzugefügt, der auf den Benutzer reagiert. Fügen Sie Ereignishandler für die <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click>-Ereignisse der zwei Schaltflächen und das <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>-Ereignis der Umschaltfläche hinzu. Fügen Sie diesen Ereignishandlern Code hinzu, um das Aus- und Einblenden der Aktionsbereiche zu aktivieren.

### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>So werden Aktionsbereiche mithilfe von Schaltflächen auf der benutzerdefinierten Registerkarte ausgeblendet und angezeigt

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für *MyRibbon.cs* oder *MyRibbon. vb*, und wählen Sie dann **Code anzeigen** aus.

2. Fügen Sie oben in der `MyRibbon`-Klasse den folgenden Code hinzu: Mit diesem Code werden zwei Aktionsbereichobjekte erstellt.

     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]

3. Ersetzen Sie die `MyRibbon_Load`-Methode durch den folgenden Code. Mit diesem Code werden die Aktionsbereichsobjekte der <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>-Auflistung hinzugefügt und die Objekte ausgeblendet. Durch den Visual C#-Code werden außerdem Delegate an mehrere Menüband-Steuerelementereignisse angefügt.

     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]

4. Fügen Sie der `MyRibbon`-Klasse die folgenden drei Ereignishandlermethoden hinzu. Diese Methoden dienen zur Behandlung der <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click>-Ereignisse der zwei Schaltflächen und des <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>-Ereignisses der Umschaltfläche. Die Ereignishandler für button1 und button2 zeigen andere Aktionsbereiche an. Der Ereignishandler für toggleButton1 zeigt den aktiven Aktionsbereich an und blendet diesen aus.

     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]

## <a name="test-the-custom-tab"></a>Testen der benutzerdefinierten Registerkarte
 Wenn Sie das Projekt ausführen, wird Excel gestartet, und die Registerkarte **meine benutzerdefinierte Register** Karte wird auf dem Menüband angezeigt. Wählen Sie die Schaltflächen auf der **Registerkarte Benutzer** definiert aus, um die Aktionsbereiche anzuzeigen und auszublenden.

### <a name="to-test-the-custom-tab"></a>So testen Sie die benutzerdefinierte Registerkarte

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Wählen Sie die Registerkarte **meine benutzerdefinierte Registerkarte** aus.

3. Wählen Sie in der Gruppe **benutzerdefinierte Aktionen** Bereich-Manager die Option **Aktionen Bereich 1 anzeigen** aus.

     Der Aktionsbereich wird angezeigt und zeigt den **Aktionsbereich 1** der Bezeichnung an.

4. Wählen Sie **Aktionsbereich 2 anzeigen** aus.

     Der Aktionsbereich wird angezeigt und zeigt den **Aktionsbereich 2** der Bezeichnung an.

5. Wählen Sie den Bereich **Aktionen ausblenden** aus.

     Die Aktionsbereiche werden nicht mehr angezeigt.

## <a name="next-steps"></a>Nächste Schritte
 Weitere Informationen zum Anpassen der Office-Benutzeroberfläche finden Sie in diesen Themen:

- Fügen Sie jeder Anpassung auf Dokumentebene kontextbasierte Benutzeroberfläche hinzu. Weitere Informationen finden Sie unter [Übersicht über den Aktions](../vsto/actions-pane-overview.md)Bereich.

- Erweitern Sie ein standardmäßiges oder benutzerdefiniertes Microsoft Office Outlook-Formular. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Entwerfen eines Outlook-Formular Bereichs](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>Weitere Informationen
- [Zugreifen auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)
- [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Gewusst wie: Starten der Anpassung des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Vorgehensweise: Ändern der Position einer Registerkarte im Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)
- [Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Übersicht über das Ribbon-Objektmodell](../vsto/ribbon-object-model-overview.md)
