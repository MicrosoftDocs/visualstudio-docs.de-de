---
title: 'Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formular Bereichs'
description: Erfahren Sie, wie Sie einen benutzerdefinierten Microsoft Outlook-Formular Bereich entwerfen können, der als neue Seite im Inspektor-Fenster eines Kontakt Elements angezeigt wird.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e306814512c6cab2d331a26128f22bb94d7dbbf4
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524204"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formular Bereichs
  Benutzerdefinierte Formularbereiche erweitern Standard- oder benutzerdefinierte Microsoft Office Outlook-Formulare. In dieser exemplarischen Vorgehensweise entwerfen Sie einen benutzerdefinierten Formularbereich, der als neue Seite im Inspektor-Fenster eines Kontaktelements angezeigt wird. Dieser Formularbereich zeigt eine Zuordnung jeder Adresse an, die für den Kontakt aufgeführt ist, indem die Adressinformationen an die Windows Live Local Search-Website gesendet werden. Weitere Informationen zu Formular Bereichen finden Sie unter [Erstellen von Outlook-Formular](../vsto/creating-outlook-form-regions.md)Bereichen.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines neuen Outlook VSTO-Add-In-Projekts.

- Hinzufügen eines Formularbereichs zum VSTO-Add-In-Projekt.

- Entwerfen des Layouts des Formularbereichs.

- Anpassen des Verhaltens des Formularbereichs.

- Testen des Outlook-Formularbereichs.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] oder neuer.

  ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") Eine videoversion dieses Themas finden [Sie unter Video Gewusst wie: Entwerfen eines Outlook-Formular Bereichs](/previous-versions/visualstudio/visual-studio-2008/cc837160(v=vs.90)).

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Erstellen eines neuen Outlook VSTO-Add-in-Projekts
 Erstellen Sie zunächst ein Outlook VSTO-Add-In-Basisprojekt.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>So erstellen Sie ein neues Outlook VSTO-Add-In-Projekt

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Erstellen Sie in ein Outlook VSTO-Add-in-Projekt mit dem Namen " **MapItAddIn**".

2. Wählen Sie im Dialogfeld **Neues Projekt** die Option **Projektmappenverzeichnis erstellen** aus.

3. Speichern Sie das Projekt in einem beliebigen Verzeichnis.

     Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Hinzufügen eines Formular Bereichs zum Outlook-VSTO-Add-in-Projekt
 Eine Outlook-VSTO-Add-In-Projektmappe enthält mindestens ein Outlook-Formularbereichelement. Fügen Sie dem Projekt ein Formular Bereichs Element hinzu, indem Sie den Assistenten für **neue Outlook-Formular** Bereiche verwenden.

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>So fügen Sie dem VSTO-Add-In-Projekt einen Formularbereich hinzu

1. Wählen Sie in **Projektmappen-Explorer** das Projekt **MapItAddIn** aus.

2. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

3. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Outlook-Formular Bereich** aus, benennen Sie die Datei **MapIt**, und klicken Sie dann auf **Hinzufügen**.

     Der Assistent für den **NewOutlook-Formular Bereich** wird gestartet.

4. Klicken Sie auf der Seite Wählen Sie aus, **wie der Formular Bereich erstellt** werden soll auf **neuen Formular Bereich entwerfen**, und klicken Sie dann auf **weiter**.

5. Klicken Sie auf der Seite **Wählen Sie den Typ des zu erstellenden Formular Bereichs aus** auf **getrennt** aus, und klicken Sie dann auf **weiter**.

     Ein *separater* Formular Bereich fügt einem Outlook-Formular eine neue Seite hinzu. Weitere Informationen zu Formular Bereichs Typen finden Sie unter [Erstellen von Outlook-Formular](../vsto/creating-outlook-form-regions.md)Bereichen.

6. Geben Sie auf der Seite geben Sie einen beschreibenden Text ein, **und wählen Sie die Anzeigeeinstellungen** aus im Feld **Name** den Text **map** aus.

     Dieser Name wird auf dem Menüband im Inspektor-Fenster angezeigt, wenn das Kontaktelement geöffnet ist.

7. Wählen Sie **Inspektoren im Compose-Modus** und **Inspektoren im Lesemodus** aus, und klicken Sie dann auf **weiter**.

8. Löschen Sie auf der Seite **Nachrichten Klassen, die diesen Formular Bereich anzeigen werden** die Option **e-Mail**, wählen Sie **Kontakt** aus, und klicken Sie dann auf **Fertig** stellen.

     Eine *MapIt.cs* -oder *MapIt. vb* -Datei wird dem Projekt hinzugefügt.

## <a name="design-the-layout-of-the-form-region"></a>Entwerfen des Layouts des Formular Bereichs
 Entwickeln Sie Formular Bereiche visuell mithilfe des *Formular Bereich-Designers*. Sie können verwaltete Steuerelemente auf die Oberfläche des Formularbereich-Designers ziehen. Verwenden Sie den Designer und das **Eigenschaften** Fenster, um das Layout und die Darstellung des Steuer Elements anzupassen.

### <a name="to-design-the-layout-of-the-form-region"></a>So entwerfen Sie das Layout des Formularbereichs

1. Erweitern Sie in **Projektmappen-Explorer** das Projekt **MapItAddIn** , und doppelklicken Sie dann auf *MapIt.cs* oder *MapIt. vb* , um den Formular Bereich-Designer zu öffnen.

2. Klicken Sie mit der rechten Maustaste auf den Designer, und klicken Sie auf **Eigenschaften**.

3. Legen Sie im Fenster **Eigenschaften** die **Größe** auf **664, 469** fest.

     Auf diese Weise wird sichergestellt, dass der Formularbereich groß genug ist, um eine Zuordnung anzuzeigen.

4. Klicken Sie im Menü **Ansicht** auf **Toolbox**.

5. Fügen Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** einen **Webbrowser** zum Formular Bereich hinzu.

     Im **Webbrowser** wird eine Zuordnung der einzelnen Adressen angezeigt, die für den Kontakt aufgeführt sind.

## <a name="customize-the-behavior-of-the-form-region"></a>Anpassen des Verhaltens des Formular Bereichs
 Fügen Sie den Formularbereich-Ereignishandlern Code hinzu, um das Verhalten eines Formularbereichs zur Laufzeit anzupassen. Für diesen Formularbereich untersucht der Code die Eigenschaften eines Outlook-Elements und bestimmt, ob der Map It-Formularbereich angezeigt wird. Wenn der Formularbereich angezeigt wird, navigiert der Code zu Windows Live Local Search und lädt eine Zuordnung jeder im Outlook-Kontaktelement aufgeführten Adresse.

### <a name="to-customize-the-behavior-of-the-form-region"></a>So passen Sie das Verhalten des Formularbereichs an

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf *MapIt.cs* oder *MapIt. vb*, und klicken Sie dann auf **Code anzeigen**.

    *MapIt.cs* oder *MapIt. vb* wird im Code-Editor geöffnet.

2. Erweitern Sie den Code Bereich der **Formular Bereich-Factory** .

    Die Formularbereichsfactory-Klasse namens `MapItFactory` wird bereitgestellt.

3. Fügen Sie dem `MapItFactory_FormRegionInitializing`-Ereignishandler den folgenden Code hinzu. Dieser Ereignishandler wird aufgerufen, wenn der Benutzer ein Kontaktelement öffnet. Der folgende Code ermittelt, ob das Kontaktelement eine Adresse enthält. Wenn das Kontakt Element keine Adresse enthält, legt dieser Code die <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> -Eigenschaft der <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> -Klasse auf " **true** " fest, und der Formular Bereich wird nicht angezeigt. Andernfalls löst das VSTO-Add-In das Ereignis <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> aus und zeigt den Formularbereich an.

    [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
    [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

4. Fügen Sie dem <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>-Ereignishandler den folgenden Code hinzu. Mit diesem Code werden die folgenden Aufgaben durchgeführt:

   - Verketten jeder Adresse im Kontaktelement und Erstellen  eine URL-Zeichenfolge.

   - Aufrufen der Methode <xref:System.Windows.Forms.WebBrowser.Navigate%2A> des <xref:System.Windows.Forms.WebBrowser>-Objekts und Übergeben der URL-Zeichenfolge als Parameter.

     Die Website für lokale Suche wird im Map It-Formularbereich angezeigt und zeigt jede Adresse im Testbereich an.

     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]

## <a name="test-the-outlook-form-region"></a>Testen des Outlook-Formular Bereichs
 Wenn Sie das Projekt ausführen, öffnet Visual Studio Outlook. Öffnen Sie ein Kontaktelement, um den Map It-Formularbereich anzuzeigen. Der Map It-Formularbereich wird als Seite in Form eines beliebigen Kontaktelements angezeigt, das eine Adresse enthält.

### <a name="to-test-the-map-it-form-region"></a>So testen Sie den Map It-Formularbereich

1. Drücken Sie **F5** , um das Projekt auszuführen.

     Outlook wird geöffnet.

2. Klicken Sie in Outlook auf der Registerkarte **Start** auf **neue Elemente**, und klicken Sie dann auf **Kontakt**.

3. Geben Sie im Kontaktformular **Ann Beebe** als Kontakt Name ein, und geben Sie dann die folgenden drei Adressen an.

    |Adresstyp|Adresse|
    |------------------|-------------|
    |**Geschäftlich**|**4567 Main St. Buffalo, NY**|
    |**Home**|**1234 North St. Buffalo, NY**|
    |**Andere**|**3456 Main St. Seattle, WA**|

4. Speichern und schließen Sie das Kontaktelement.

5. Öffnen Sie das **Ann Beebe** -Kontakt Element erneut.

    In Outlook kann dies in **der Gruppe suchen** erfolgen, indem Sie entweder das Adressbuch für Kontakte öffnen oder Ann Beebe in **Search People** eingeben.

6. Klicken Sie in der Gruppe **anzeigen** des Menübands des Elements **auf zuordnen** , um den Formular Bereich der Karte zu öffnen.

     Der Map It-Formularbereich wird geöffnet und zeigt die Website für lokale Suche an. Die **Geschäfts**-, **Start**-und **anderen** Adressen werden im Scratch-Pad angezeigt. Wählen Sie im Testbereich eine Adresse aus, die Sie zuordnen möchten.

## <a name="next-steps"></a>Nächste Schritte
 Weitere Informationen zum Anpassen der Benutzeroberfläche einer Outlook-Anwendung finden Sie in diesen Themen:

- Informationen zum Anpassen des Menübands eines Outlook-Elements finden Sie unter [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

## <a name="see-also"></a>Weitere Informationen
- [Zugreifen auf einen Formular Bereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)
- [Erstellen von Outlook-Formular Bereichen](../vsto/creating-outlook-form-regions.md)
- [Richtlinien zum Erstellen von Outlook-Formular Bereichen](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formular Bereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Gewusst wie: Hinzufügen eines Formular Bereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Zuordnen eines Formular Bereichs zu einer Outlook-Nachrichten Klasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Benutzerdefinierte Aktionen in Outlook-Formular Bereichen](../vsto/custom-actions-in-outlook-form-regions.md)
- [Gewusst wie: verhindern der Anzeige eines Formular Bereichs in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
