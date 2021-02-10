---
title: 'Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formular Bereichs'
description: Erfahren Sie, wie Sie einen Formular Bereich in Microsoft Outlook entwerfen und dann den Formular Bereich mithilfe des Assistenten für neue Formular Bereiche in ein Outlook VSTO-Add-in-Projekt importieren.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- importing form regions
- form regions [Office development in Visual Studio], importing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4b60060f8db2bf2bb1abf42803a8c80333ee5fc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969151"
---
# <a name="walkthrough-import-a-form-region-that-is-designed-in-outlook"></a>Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formular Bereichs
  Diese exemplarische Vorgehensweise veranschaulicht, wie ein Formularbereich in Microsoft Office Outlook entworfen und anschließend mithilfe des Assistenten **Neuer Formularbereich** in ein Outlook VSTO-Add-In-Projekt importiert wird. Durch das Entwerfen des Formularbereichs in Outlook ist es möglich, dass systemeigene Outlook-Steuerelemente zum Formularbereich hinzugefügt werden können, die Outlook-Daten binden. Nachdem Sie den Formularbereich importiert haben, können Sie die Ereignisse der einzelnen Steuerelemente behandeln.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Entwerfen eines Formularbereichs mithilfe des Formularbereich-Designers in Outlook

- Importieren eines Formularbereichs in ein Outlook VSTO-Add-In-Projekt

- Behandeln der Ereignisse von Steuerelementen im Formularbereich

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] oder [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Entwerfen eines Formular Bereichs mithilfe des Formular Bereich-Designers in Outlook
 In diesem Schritt entwerfen Sie einen Formularbereich in Outlook. Anschließend speichern Sie den Formularbereich an einem leicht zugänglichen Speicherort, damit dieser in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]importiert werden kann.

 Dieser Beispielformularbereich ersetzt das übliche Aufgabenformular. Es bietet eine Möglichkeit, den Fortschritt aller Aufgaben zu verfolgen, die abgeschlossen werden müssen, bevor die Hauptaufgabe ausgeführt werden kann (erforderliche Aufgaben). Der Formularbereich zeigt eine Liste der erforderlichen Aufgaben sowie den Abschlussstatus für jede Aufgabe in der Liste an. Benutzer können Aufgaben zur Liste hinzufügen und aus ihr entfernen. Sie können auch den Abschlussstatus der einzelnen Aufgaben aktualisieren.

### <a name="to-design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>So entwerfen Sie einen Formularbereich mithilfe des Formularbereich-Designers in Outlook

1. Starten Sie Microsoft Office Outlook.

2. Klicken Sie in Outlook auf der Registerkarte **Entwickler** auf **Ein Formular entwerfen**. Weitere Informationen finden Sie unter Gewusst [wie: Anzeigen der Registerkarte "Entwickler" im Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. Klicken Sie im Feld **Formular entwerfen** auf **Aufgabe**, und klicken Sie dann auf **Öffnen**.

4. Klicken Sie in Outlook auf der Registerkarte **Entwickler** in der Gruppe **Entwurf** auf **Neuer Formularbereich**.

     Es wird ein neuer Formularbereich geöffnet. Wenn die **Feldauswahl** nicht angezeigt wird, klicken Sie in der Gruppe **Extras** auf **Feldauswahl** .

5. Ziehen Sie das Feld **Betreff** und das Feld **% abgeschlossen** aus der **Feldauswahl** in den Formularbereich.

6. Klicken Sie in der Gruppe **Extras** auf **Steuerelement-Toolbox** , um die **Toolbox** zu öffnen.

7. Ziehen Sie eine Bezeichnung aus der **Toolbox** in den Formularbereich. Ordnen Sie die Bezeichnung unter den Feldern **Betreff** und **% abgeschlossen** an.

8. Klicken Sie mit der rechten Maustaste auf die Bezeichnung, und klicken Sie dann auf **Erweiterte Eigenschaften**.

9. Legen Sie im Fenster **Eigenschaften** die **Beschriftung** -Eigenschaft auf **Diese Aufgabe ist von den folgenden Aufgaben abhängig** fest, legen Sie dann die **Breite** -Eigenschaft auf **200** fest, und klicken Sie anschließend auf **Übernehmen**.

10. Ziehen Sie ein ListBox-Steuerelement aus der **Toolbox** in den Formularbereich. Positionieren Sie das Listenfeld unterhalb der Bezeichnung **Diese Aufgabe ist von den folgenden Aufgaben abhängig** .

11. Wählen Sie das soeben hinzugefügte Listenfeld aus.

12. Legen Sie im Fenster **Eigenschaften** für **Breite** den Wert **300** fest, und klicken Sie dann auf **Übernehmen**.

13. Ziehen Sie eine Bezeichnung aus der **Toolbox** in den Formularbereich. Positionieren Sie die Bezeichnung unter dem Listenfeld.

14. Wählen Sie die soeben hinzugefügte Bezeichnung aus.

15. Legen Sie im Fenster **Eigenschaften** die **Beschriftung** -Eigenschaft auf **Aufgabe auswählen, die zur Liste der abhängigen Aufgaben hinzugefügt wird** fest, legen Sie dann die **Breite** -Eigenschaft auf **200** fest, und klicken Sie anschließend auf **Übernehmen**.

16. Ziehen Sie ein ComboBox-Steuerelement aus der **Toolbox** in den Formularbereich. Positionieren Sie das Kombinationsfeld unter die Bezeichnung **Aufgabe auswählen, die zur Liste der abhängigen Aufgaben hinzugefügt wird** .

17. Wählen Sie das soeben hinzugefügte Kombinationsfeld aus.

18. Legen Sie im Fenster **Eigenschaften** für die **Breite** -Eigenschaft den Wert **300** fest, und klicken Sie dann auf **Übernehmen**.

19. Ziehen Sie ein CommandButton-Steuerelement aus der **Toolbox** in den Formularbereich. Positionieren Sie die Befehlsschaltfläche neben dem Kombinationsfeld.

20. Wählen Sie die soeben hinzugefügte Befehlsschaltfläche aus.

21. Legen Sie Fenster **Eigenschaften** für **Name** die Option **AddDependentTask** fest. Legen Sie dann für **Beschriftung** die Option **Abhängige Aufgabe hinzufügen** und für **Breite** den Wert **100** fest, und klicken Sie anschließend auf **Übernehmen**.

22. Klicken Sie in der **Feldauswahl** auf **Neu**.

23. Geben Sie im Dialogfeld **Neues Feld** die Zeichenfolge **hiddenField** in das Feld **Name** ein, und klicken Sie dann auf **OK**.

24. Ziehen Sie das Feld **hiddenField** aus der **Feldauswahl** in den Formularbereich.

25. Legen Sie im Fenster **Eigenschaften** für **Sichtbar** den Wert **0 – False** fest, und klicken Sie dann auf **Übernehmen**.

26. Klicken Sie in Outlook auf der Registerkarte **Entwickler** in der Gruppe **Entwurf** auf die Schaltfläche **Speichern** , und klicken Sie dann auf **Formularbereich speichern unter**.

     Weisen Sie der Formularregion die Bezeichnung **TaskFormRegion** zu, und speichern Sie sie in einem lokalen Verzeichnis auf Ihrem Computer.

     Outlook speichert den Formular Bereich als *OFS*-Datei (Outlook Form Storage). Der Formular Bereich wird mit dem Namen " *TaskFormRegion. OFS*" gespeichert.

27. Beenden Sie Outlook.

## <a name="create-a-new-outlook-add-in-project"></a>Erstellen eines neuen Outlook-Add-in-Projekts
 In diesem Abschnitt erstellen Sie ein Outlook VSTO-Add-In-Projekt. Zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise werden Sie den Formularbereich in das Projekt importieren.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>So erstellen Sie ein neues Outlook VSTO-Add-In-Projekt

1. Erstellen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ein Outlook VSTO-Add-In-Projekt namens **TaskAddIn**.

2. Wählen Sie im Dialogfeld **Neues Projekt** die Option **Projektmappenverzeichnis erstellen** aus.

3. Speichern Sie das Projekt im Standardprojektverzeichnis.

     Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="import-the-form-region"></a>Importieren des Formular Bereichs
 Sie können den in Outlook entworfenen Formularbereich mithilfe des Assistenten **Neuer Outlook-Formularbereich** in das Outlook VSTO-Add-In-Projekt importieren.

### <a name="to-import-the-form-region-into-the-outlook-vsto-add-in-project"></a>So importieren Sie den Formularbereich in das Outlook VSTO-Add-In-Projekt

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **TaskAddIn** , zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.

2. Wählen Sie im Bereich **Vorlagen** die Option **Outlook-Formularbereich** aus, weisen Sie der Datei die Bezeichnung **TaskFormRegion** zu, und klicken Sie dann auf **Hinzufügen**.

     Der Assistent für den **NewOutlook-Formular Bereich** wird gestartet.

3. Klicken Sie auf der Seite **Legen Sie fest, wie der Formularbereich erstellt werden soll** auf die Option **OFS-Datei (Outlook Form Storage) importieren**, und klicken Sie dann auf **Durchsuchen**.

4. Navigieren Sie im Dialogfeld **Speicherort für vorhandene Outlook-Formularbereichsdateien** zum Speicherort der Datei *TaskFormRegion.ofs*, wählen Sie **TaskFormRegion.ofs** aus, klicken Sie dann auf **Öffnen** und anschließend auf **Weiter**.

5. Klicken Sie auf der Seite **Wählen Sie den Typ des zu erstellenden Formularbereichs aus** auf **Alle ersetzen**, und klicken Sie dann auf **Weiter**.

     Der Formularbereich *Alle ersetzen* ersetzt das gesamte Outlook-Formular. Weitere Informationen zu Formular Bereichs Typen finden Sie unter [Erstellen von Outlook-Formular](../vsto/creating-outlook-form-regions.md)Bereichen.

6. Klicken Sie auf der Seite **Geben Sie eine Beschreibung ein, und wählen Sie die Anzeigeeinstellungen aus** auf **Weiter**.

7. Gehen Sie auf der Seite **Geben Sie die Meldungsklassen an, von denen dieser Formularbereich angezeigt wird** in das Feld **Welche benutzerdefinierten Meldungsklassen sollen in diesem Formularbereich angezeigt werden?** die Zeichenfolge **IPM.Task.TaskFormRegion** ein, und klicken Sie dann auf **Fertig stellen**.

     Eine *TaskFormRegion.cs* -oder *TaskFormRegion. vb* -Datei wird dem Projekt hinzugefügt.

## <a name="handle-the-events-of-controls-on-the-form-region"></a>Behandeln der Ereignisse von Steuerelementen im Formular Bereich
 Nachdem sich der Formularbereich im Projekt befindet, können Sie Code hinzufügen, der das `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click`-Ereignis der Schaltfläche verarbeitet, die Sie in Outlook zum Formularbereich hinzugefügt haben.

 Darüber hinaus fügen Sie Code zum <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> -Ereignis hinzu, das Steuerelemente für den Formularbereich aktualisiert, wenn der Formularbereich angezeigt wird.

### <a name="to-handle-the-events-of-controls-on-the-form-region"></a>So behandeln Sie die Ereignisse von Steuerelementen im Formularbereich

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf *TaskFormRegion.cs* oder *TaskFormRegion. vb*, und klicken Sie dann auf **Code anzeigen**.

    *TaskFormRegion.cs* oder *TaskFormRegion. vb* wird im Code-Editor geöffnet.

2. Fügen Sie der `TaskFormRegion` -Klasse den folgenden Code hinzu. Dieser Code füllt das Kombinationsfeld des Formularbereichs mit der Betreffzeile der einzelnen Aufgaben aus dem Ordner für Outlook-Aufgaben.

    [!code-csharp[Trin_Outlook_FR_Import#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#1)]
    [!code-vb[Trin_Outlook_FR_Import#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#1)]

3. Fügen Sie der `TaskFormRegion` -Klasse den folgenden Code hinzu. Mit diesem Code werden die folgenden Aufgaben durchgeführt:

   - Sucht `Microsoft.Office.Interop.Outlook.TaskItem` im Ordner „Aufgaben“, indem die Hilfsmethode `FindTaskBySubjectName` aufgerufen und der Betreff der gewünschten Aufgabe übergeben wird. Sie werden die Hilfsmethode `FindTaskBySubjectName` im nächsten Schritt hinzufügen.

   - Fügt die Werte `Microsoft.Office.Interop.Outlook.TaskItem.Subject` und `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` dem Listenfeld für abhängige Aufgaben hinzu.

   - Fügt den Betreff der Aufgabe dem ausgeblendeten Feld des Formularbereichs hinzu. Das ausgeblendete Feld speichert diese Werte als Teil des Outlook-Elements.

     [!code-csharp[Trin_Outlook_FR_Import#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#2)]
     [!code-vb[Trin_Outlook_FR_Import#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#2)]

4. Fügen Sie der `TaskFormRegion` -Klasse den folgenden Code hinzu. Dieser Code stellt die Hilfsmethode `FindTaskBySubjectName` bereit, die im vorherigen Schritt beschrieben wurde.

    [!code-csharp[Trin_Outlook_FR_Import#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#3)]
    [!code-vb[Trin_Outlook_FR_Import#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#3)]

5. Fügen Sie der `TaskFormRegion` -Klasse den folgenden Code hinzu. Mit diesem Code werden die folgenden Aufgaben durchgeführt:

   - Aktualisiert das Listenfeld im Formularbereich mit dem aktuellen Abschlussstatus der einzelnen abhängigen Aufgabe.

   - Analysiert das ausgeblendete Textfeld, um den Betreff der einzelnen abhängigen Aufgaben zu erhalten. Anschließend wird jede Datei `Microsoft.Office.Interop.Outlook.TaskItem` im Ordner *Tasks* durch Aufrufen der `FindTaskBySubjectName` -Hilfsmethode und durch Übergeben des Subjekts jeder Aufgabe gesucht.

   - Fügt die Werte `Microsoft.Office.Interop.Outlook.TaskItem.Subject` und `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` dem Listenfeld für abhängige Aufgaben hinzu.

     [!code-csharp[Trin_Outlook_FR_Import#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#4)]
     [!code-vb[Trin_Outlook_FR_Import#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#4)]

6. Ersetzen Sie den `TaskFormRegion_FormRegionShowing` -Ereignishandler durch den folgenden Code. Mit diesem Code werden die folgenden Aufgaben durchgeführt:

   - Füllt das Kombinationsfeld des Formularbereichs mit den Betreffs von Aufgaben, wenn der Formularbereich angezeigt wird.

   - Ruft die Hilfsmethode `RefreshTaskListBox` auf, wenn der Formularbereich angezeigt wird. Dadurch werden alle abhängigen Aufgaben angezeigt, die beim vorherigen Öffnen des Elements zum Listenfeld hinzugefügt wurden.

     [!code-csharp[Trin_Outlook_FR_Import#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#5)]
     [!code-vb[Trin_Outlook_FR_Import#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#5)]

## <a name="test-the-outlook-form-region"></a>Testen des Outlook-Formular Bereichs
 Fügen Sie zum Testen des Formularbereichs die Aufgaben zur Liste der erforderlichen Aufgaben zum Formularbereich hinzu. Aktualisieren Sie den Abschlussstatus einer erforderlichen Aufgabe, und anschließend zeigen Sie den aktualisierten Abschlussstatus der Aufgabe in der Liste der erforderlichen Aufgaben an.

### <a name="to-test-the-form-region"></a>So testen Sie den Formularbereich

1. Drücken Sie **F5** , um das Projekt auszuführen.

     Outlook wird gestartet.

2. Klicken Sie in Outlook auf der Registerkarte **Start** auf **Neue Elemente**, und klicken Sie dann auf **Aufgabe**.

3. Geben Sie im Aufgabenformular die Zeichenfolge **Abhängige Aufgabe** in das Feld **Betreff** ein.

4. Klicken Sie auf der Registerkarte **Aufgabe** des Menübands in der Gruppe **Aktionen** auf **speichern & schließen**.

5. Klicken Sie in Outlook auf der Registerkarte **Start** auf **Neue Elemente**, dann auf **Weitere Elemente** und anschließend auf **Formular auswählen**.

6. Klicken Sie im Dialogfeld **Formular ausfüllen** auf **TaskFormRegion**, und klicken Sie dann auf **Öffnen**.

     Der Formularbereich **TaskFormRegion** wird angezeigt. Dieses Formular ersetzt das gesamte Aufgabenformular. Das Kombinationsfeld **Aufgabe auswählen, die zur Liste der abhängigen Aufgaben hinzugefügt wird** wird mit anderen Aufgaben im Ordner „Aufgaben“ aufgefüllt.

7. Geben Sie auf dem Aufgabenformular im Feld **Betreff** die Zeichenfolge **Primäre Aufgabe** ein.

8. Wählen Sie im Kombinationsfeld **Aufgabe auswählen, die zur Liste der abhängigen Aufgaben hinzugefügt wird** die Option **Abhängige Aufgabe** aus, und klicken Sie dann auf **Abhängige Aufgabe hinzufügen**.

     **0 % abgeschlossen – Abhängige Aufgabe** wird im Listenfeld **Diese Aufgabe ist von den folgenden Aufgaben abhängig** angezeigt. Dadurch wird gezeigt, dass Sie das `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click`-Ereignis der Schaltfläche erfolgreich behandelt haben.

9. Speichern und schließen Sie das Element **Primäre Aufgabe** .

10. Öffnen Sie das Element „Abhängige Aufgaben“ erneut in Outlook.

11. Ändern Sie im Formular „Abhängige Aufgabe“ das Feld **% abgeschlossen** zu **50 %**.

12. Klicken Sie auf der Registerkarte **Aufgabe** des Menübands abhängige Aufgabe in der Gruppe **Aktionen** auf **speichern & schließen**.

13. Öffnen Sie das Element **Abhängige Aufgabe** erneut in Outlook.

     Jetzt wird **50 % abgeschlossen – Abhängige Aufgabe** im Listenfeld **Diese Aufgabe ist von den folgenden Aufgaben abhängig** angezeigt.

## <a name="next-steps"></a>Nächste Schritte
 Weitere Informationen zum Anpassen der Benutzeroberfläche einer Outlook-Anwendung finden Sie in diesen Themen:

- Weitere Informationen zum Entwerfen der Darstellung eines Formular Bereichs durchziehen verwalteter Steuerelemente auf einen visuellen Designer finden Sie unter Exemplarische Vorgehensweise [: Entwerfen eines Outlook-Formular Bereichs](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Informationen zum Anpassen des Menübands eines Outlook-Elements finden Sie unter [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

- Weitere Informationen zum Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu Outlook finden Sie unter [benutzerdefinierte Aufgaben](../vsto/custom-task-panes.md)Bereiche.

## <a name="see-also"></a>Weitere Informationen
- [Zugreifen auf einen Formular Bereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)
- [Erstellen von Outlook-Formular Bereichen](../vsto/creating-outlook-form-regions.md)
- [Richtlinien zum Erstellen von Outlook-Formular Bereichen](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formular Bereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Gewusst wie: Hinzufügen eines Formular Bereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Zuordnen eines Formular Bereichs zu einer Outlook-Nachrichten Klasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Benutzerdefinierte Aktionen in Outlook-Formular Bereichen](../vsto/custom-actions-in-outlook-form-regions.md)
- [Gewusst wie: verhindern der Anzeige eines Formular Bereichs in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
