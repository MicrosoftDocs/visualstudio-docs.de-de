---
title: Erstellen eines Webparts für SharePoint mithilfe des Designers
description: In dieser exemplarischen Vorgehensweise erstellen Sie ein Webpart mit der SharePoint-Projektvorlage für visuelle Webparts in Visual Studio visuell.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 02a0eb7c9279aef1fd2821d44a6f3cc4a0008356
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847751"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint mithilfe eines Designers

Wenn Sie Webparts für eine SharePoint-Website erstellen, können Benutzer Inhalt, Darstellung und Verhalten der Seiten auf dieser Website direkt mithilfe eines Browsers ändern. In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie ein Webpart mit der SharePoint-Projektvorlage für **visuelle Webparts** in Visual Studio visuell erstellen.

Das erstellte Webpart zeigt eine monatliche Kalenderansicht und ein Kontrollkästchen für jede Kalenderliste auf der Website an. Die Benutzer können angeben, welche Kalenderlisten in die monatliche Kalenderansicht eingeschlossen werden, indem sie die Kontrollkästchen aktivieren.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines Webparts mithilfe der Projektvorlage für ein **visuelles Webpart** .
- Entwerfen des Webparts mit dem Visual Web Developer-Designer in Visual Studio
- Hinzufügen von Code, um die Ereignisse der Steuerelemente des Webparts zu behandeln
- Testen des Webparts in SharePoint

    > [!NOTE]
    > Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt, als in den folgenden Anweisungen aufgeführt werden. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren der Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Voraussetzungen

Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Unterstützte Editionen von Windows und SharePoint.

## <a name="create-a-web-part-project"></a>Erstellen eines Webpartprojekts

Erstellen Sie zunächst ein Webpartprojekt mithilfe der Projektvorlage für das **visuelle Webpart** .

1. Starten [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sie mit der Option **als Administrator ausführen** .

2. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3. Erweitern Sie im Dialogfeld **Neues Projekt** unter **Visual c#** oder **Visual Basic** den Eintrag **Office/SharePoint**, und wählen Sie dann die Kategorie **SharePoint-Lösungen** aus.

4. Wählen Sie in der Liste der Vorlagen die Vorlage **SharePoint 2013-Visual Web Part** aus, und klicken Sie dann auf die Schaltfläche **OK** .

     Der Assistent zum Anpassen von **SharePoint** wird angezeigt. Mit diesem Assistenten können Sie die Website, die Sie zum Debuggen des Projekts verwenden, sowie die Vertrauensebene der Projektmappe angeben.

5. Wählen Sie im Abschnitt **Was ist die Vertrauens Ebene für diese SharePoint-Lösung?** das Optionsfeld **als Farm Lösung** bereitstellen aus.

6. Wählen Sie die Schaltfläche **Fertig** stellen, um die standardmäßige lokale SharePoint-Website zu akzeptieren

## <a name="designing-the-web-part"></a>Entwerfen des Webparts

Entwerfen Sie das Webpart, indem Sie Steuerelemente aus der **Toolbox** der Oberfläche des Visual Web Developer-Designers hinzufügen.

1. Wählen Sie im Visual Web Developer-Designer die Registerkarte **Entwurf** aus, um zu Designansicht zu wechseln.

2. Wählen Sie in der Menüleiste   >  **Toolbox** anzeigen aus.

3. Wählen Sie im Knoten **Standard** der **Toolbox** das Steuerelement **CheckBoxList** aus, und führen Sie dann einen der folgenden Schritte aus:

    - Öffnen Sie das Kontextmenü für das Steuerelement **CheckBoxList** , wählen Sie **Kopieren** aus, öffnen Sie das Kontextmenü für die erste Zeile im Designer, und wählen Sie dann **Einfügen** aus.

    - Ziehen Sie das **CheckBoxList** -Steuerelement aus der **Toolbox**, und verbinden Sie das Steuerelement mit der ersten Zeile im Designer.

4. Wiederholen Sie den vorherigen Schritt, aber verschieben Sie eine Schaltfläche in die nächste Zeile des Designers.

5. Wählen Sie im Designer die Schaltfläche **Button1** aus.

6. Wählen Sie in der Menüleiste **Ansicht**  >  **Eigenschaften Fenster** aus.

     Das Fenster **Eigenschaften** wird geöffnet.

7. Geben Sie in der **Text** -Eigenschaft der Schaltfläche **Update** ein.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Behandeln der Ereignisse von Steuerelementen des Webparts

Fügen Sie Code hinzu, der es dem Benutzer ermöglicht, der Masterkalenderansicht Kalender hinzuzufügen.

1. Führen Sie einen der folgenden Schritte aus:

   - Doppelklicken Sie im Designer auf die Schaltfläche **Aktualisieren** .

   - Wählen Sie im Fenster **Eigenschaften** für die Schaltfläche **Aktualisieren** die Schaltfläche **Ereignisse** aus. Geben Sie in der **Click** -Eigenschaft **Button1_Click** ein, und drücken Sie dann die EINGABETASTE.

     Die Benutzersteuerelement-Codedatei wird im Code-Editor geöffnet, und der `Button1_Click`-Ereignishandler wird angezeigt. Später fügen Sie diesem Ereignishandler Code hinzu.

2. Fügen Sie am Anfang der Benutzersteuerelement-Codedatei die folgenden Anweisungen hinzu.

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. Fügen Sie der `VisualWebPart1`-Klasse folgende Codezeile hinzu. In diesem Code wird ein monatliches Kalenderansichtssteuerelement deklariert.

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. Ersetzen Sie die `Page_Load`-Methode der `VisualWebPart1`-Klasse durch folgenden Code. Mit diesem Code werden die folgenden Aufgaben durchgeführt:

   - Fügt dem Benutzersteuerelement eine monatliche Kalenderansicht hinzu.

   - Fügt ein Kontrollkästchen für jede Kalenderliste der Website hinzu.

   - Gibt eine Vorlage für jeden Typ von Element an, das in der Kalenderansicht angezeigt wird.

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. Ersetzen Sie die `Button1_Click`-Methode der `VisualWebPart1`-Klasse durch folgenden Code. Mit diesem Code werden der Masterkalenderansicht Elemente aus jedem ausgewählten Kalender hinzugefügt.

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>Testen des Webparts

Wenn Sie das Projekt ausführen, wird die SharePoint-Website geöffnet. Das Webpart wird automatisch dem Webpartkatalog in SharePoint hinzugefügt. Um dieses Projekt zu testen, führen Sie die folgenden Aufgaben aus:

- Fügen Sie jeder von zwei separaten Kalenderlisten ein Ereignis hinzu.
- Fügen Sie das Webpart einer Webpartseite hinzu.
- Geben Sie die Listen an, die in die monatliche Kalenderansicht eingeschlossen werden sollen.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>So fügen Sie Kalenderlisten der Website Ereignisse hinzu

1. Wählen Sie in Visual Studio die Taste **F5** aus.

     Die SharePoint-Website wird geöffnet, und die [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] Schnellstartleiste wird auf der Seite angezeigt.

2. Wählen Sie auf der Schnellstartleiste unter **Listen** den Link **Kalender** aus.

     Die Seite **Kalender** wird angezeigt.

     Wenn in der Schnellstartleiste kein Kalender Link angezeigt wird, wählen Sie den Link **Website Inhalte** aus. Wenn auf der Seite Website Inhalt kein **Kalender** Element angezeigt wird, erstellen Sie eines.

3. Wählen Sie auf der Seite Kalender einen Tag aus, und wählen Sie dann den Link **Hinzufügen** am ausgewählten Tag aus, um ein Ereignis hinzuzufügen.

4. Geben Sie im Feld **Titel** **im Standardkalender Ereignis** ein, und klicken Sie dann auf die Schaltfläche **Speichern** .

5. Wählen Sie den Link **Website Inhalte** aus, und wählen Sie dann die Kachel **app hinzufügen** aus.

6. Wählen Sie auf der Seite **Erstellen** den **Kalendertyp** aus, benennen Sie den Kalender, und wählen Sie dann die Schaltfläche **Erstellen** aus.

7. Fügen Sie dem neuen Kalender ein Ereignis hinzu, benennen Sie das Ereignis Ereignis **im benutzerdefinierten Kalender**, und klicken Sie dann auf die Schaltfläche **Speichern** .

### <a name="to-add-the-web-part-to-a-web-part-page"></a>So fügen Sie das Webpart einer Webpartseite hinzu

1. Öffnen Sie auf der Seite **Website Inhalte** den Ordner **Website Seiten** .

2. Wählen Sie im Menüband die Registerkarte **Dateien** aus, öffnen Sie das Menü **Neues Dokument** , und wählen Sie dann den Befehl **Webpartseite** aus.

3. Benennen Sie auf der Seite **neue Webpartseite** die Seite **SampleWebPartPage. aspx**, und wählen Sie dann die Schaltfläche **Erstellen** aus.

     Die Webpartseite wird angezeigt.

4. Wählen Sie in der oberen Zone der Webpartseite die Registerkarte **Einfügen** aus, und klicken Sie dann auf die Schaltfläche **Webpart** .

5. Wählen Sie den **benutzerdefinierten** Ordner aus, wählen Sie das Webpart **VisualWebPart1** aus, und wählen Sie dann die Schaltfläche **Hinzufügen**

     Das Webpart wird auf der Seite angezeigt. Die folgenden Steuerelemente werden für das Webpart angezeigt:

    - Eine monatliche Kalenderansicht.

    - Eine **Aktualisierungs** Schaltfläche.

    - Ein **Kalender** -Kontrollkästchen.

    - Ein **benutzerdefiniertes Kalender** -Kontrollkästchen.

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>So geben Sie die Listen an, die in die monatliche Kalenderansicht eingeschlossen werden sollen

Geben Sie im Webpart Kalender an, die Sie in die monatliche Kalenderansicht einschließen möchten, und klicken Sie dann auf die Schaltfläche **Aktualisieren** .

Die Ereignisse aus allen angegebenen Kalendern werden in der monatlichen Kalenderansicht angezeigt.

## <a name="see-also"></a>Weitere Informationen

[Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 Vorgehens [Weise: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 Exemplarische Vorgehensweise [: Erstellen eines Webparts für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
