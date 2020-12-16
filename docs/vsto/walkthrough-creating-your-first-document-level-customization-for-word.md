---
title: Erstellen Sie Ihre erste Anpassung auf Dokument Ebene für Word
description: Erstellen Sie eine Anpassung auf Dokument Ebene für Microsoft Word. Die Features, die Sie in dieser Art von Lösung erstellen, sind nur verfügbar, wenn ein bestimmtes Dokument geöffnet ist.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c1f827346c30720cefd781dade3039416504b9c0
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527076"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-word"></a>Exemplarische Vorgehensweise: Erstellen der ersten Anpassung auf Dokument Ebene für Word

  Diese exemplarische Vorgehensweise bietet eine Einführung zum Erstellen einer Anpassung auf Dokumentebene für Microsoft Office Word. Die Features, die Sie in dieser Art von Lösung erstellen, sind nur verfügbar, wenn ein bestimmtes Dokument geöffnet ist. Sie können eine Anpassung auf Dokumentebene nicht verwenden, um anwendungsweite Änderungen (z. B. eine neue Registerkarte des Menübands anzuzeigen, wenn ein Dokument geöffnet ist) vorzunehmen.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines Word-Dokumentprojekts.

- Hinzufügen von Text zu dem Dokument, das in Visual Studio-Designer gehostet wird.

- Schreiben von Code, der das Word-Objektmodell zum Hinzufügen von Text zum angepassten Dokument verwendet, wenn dieses geöffnet wird.

- Erstellen Sie das Projekt, und führen Sie es aus, um es zu testen.

- Bereinigen des Projekts zum Entfernen nicht benötigter Builddateien und Sicherheitseinstellungen vom Entwicklungscomputer.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Voraussetzungen

 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Erstellen des Projekts

### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>So erstellen Sie ein neues Word-Dokumentprojekt in Visual Studio

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.
::: moniker range="vs-2017"
3. Erweitern Sie im Vorlagenbereich **Visual C#** oder **Visual Basic** und dann **Office/SharePoint**.

4. Wählen Sie unter dem erweiterten Knoten **Office/SharePoint** den Knoten **VSTO-Add-ins** aus.

5. Wählen Sie in der Liste der Projektvorlagen ein Word-VSTO-Dokument Projekt aus.

6. Geben Sie im Feld **Name den Namen** **firstdocumentcustomiein**.

7. Klicken Sie auf **OK**.

8. Wählen Sie im **Assistenten für Visual Studio-Tools für Office-Projekte** die Option **Neues Dokument erstellen** aus, und klicken Sie auf **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
3. Wählen Sie im Dialogfeld **Neues Projekt erstellen** das **Word-VSTO-Dokument** Projekt aus.

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. Klicken Sie auf **Weiter**.

5. Geben Sie im Dialogfeld **Neues Projekt konfigurieren** im Feld **Name** den Text **firstworkbookcustomia** ein, und klicken Sie auf **Erstellen**.

6. Wählen Sie im **Assistenten für Visual Studio-Tools für Office-Projekte** die Option **Neues Dokument erstellen** aus, und klicken Sie auf **OK**.
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das Projekt **firstdocumentanpassung** und fügt dem Projekt das **firstdocumentanpassung** -Dokument und die ThisDocument-Codedatei hinzu. Das **firstdocumentcustomizdokument** wird automatisch im Designer geöffnet.

## <a name="close-and-reopen-the-document-in-the-designer"></a>Das Dokument im Designer schließen und erneut öffnen

 Wenn Sie das Dokument absichtlich oder versehentlich im Designer schließen, während Sie das Projekt entwickeln, können Sie es erneut öffnen.

### <a name="to-close-and-reopen-the-document-in-the-designer"></a>So schließen Sie das Dokument im Designer und öffnen es erneut

1. Schließen Sie das Dokument, indem Sie auf die Schaltfläche **Schließen** (X) für das Fenster "Designer" klicken.

2. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf die Codedatei **ThisDocument** , und klicken Sie dann auf **Designer anzeigen**.

     \- oder -

     Doppelklicken Sie in **Projektmappen-Explorer** auf die Codedatei **ThisDocument** .

## <a name="add-text-to-the-document-in-the-designer"></a>Hinzufügen von Text zum Dokument im Designer

 Sie können die Benutzeroberfläche (User Interface, UI) Ihrer Anpassung gestalten, indem Sie das im Designer geöffnete Dokument ändern. Sie können z. B. Text, Tabellen oder Word-Steuerelemente hinzufügen. Weitere Informationen zur Verwendung des Designers finden Sie unter Office- [Projekte in der Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).

### <a name="to-add-text-to-your-document-by-using-the-designer"></a>So fügen Sie Ihrem Dokument mithilfe des Designers Text hinzu

1. Geben Sie den folgenden Text in das Dokument ein, das im Designer geöffnet ist.

     **Dieser Text wurde mithilfe des Designers hinzugefügt.**

## <a name="add-text-to-the-document-programmatically"></a>Programm gesteuertes Hinzufügen von Text zum Dokument

 Fügen Sie der Codedatei "ThisDocument " nun Code hinzu. Der neue Code verwendet das Word-Objektmodell, um dem Dokument einen zweiten Textabsatz hinzuzufügen. Standardmäßig enthält die Codedatei "ThisDocument " den folgenden generierten Code:

- Eine partielle Definition der Klasse `ThisDocument`, die das Programmiermodell des Dokuments darstellt und den Zugriff auf das Word-Objektmodell bereitstellt. Weitere Informationen finden Sie unter [Dokument Host Element](../vsto/document-host-item.md) und [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md). Der Rest der `ThisDocument` -Klasse ist in einer ausgeblendeten Codedatei definiert, die nicht geändert werden darf.

- Die Ereignishandler `ThisDocument_Startup` und `ThisDocument_Shutdown` . Diese Ereignishandler werden aufgerufen, wenn das Dokument geöffnet und geschlossen wird. Verwenden Sie diese Ereignishandler, um Ihre Anpassung zu initialisieren, wenn das Dokument geöffnet wird, sowie zum Bereinigen von Ressourcen, die von Ihrer Anpassung verwendet werden, wenn das Dokument geschlossen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>So fügen Sie dem Dokument mithilfe von Code einen zweiten Textabsatz hinzu

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf **ThisDocument**, und klicken Sie dann auf **Code anzeigen**.

     Die Codedatei wird in Visual Studio geöffnet.

2. Ersetzen Sie den `ThisDocument_Startup` -Ereignishandler durch den folgenden Code. Beim Öffnen des Dokuments fügt dieser Code dem Dokument einen zweiten Textabsatz hinzu.

     [!code-vb[Trin_WordDocumentTutorial#1](../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb#1)]
     [!code-csharp[Trin_WordDocumentTutorial#1](../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs#1)]

    > [!NOTE]
    > Dieser Code verwendet den Indexwert 1 in der Eigenschaft <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A>, um auf den ersten Absatz zuzugreifen. Obwohl Visual Basic und Visual C# auf Null basierende Arrays verwenden, ist die untere Arraygrenze der meisten Auflistungen im Word-Objektmodell 1. Weitere Informationen finden Sie unter [Schreiben von Code in Office](../vsto/writing-code-in-office-solutions.md)-Projektmappen.

## <a name="test-the-project"></a>Testen des Projekts

### <a name="to-test-your-document"></a>So testen Sie das Dokument

1. Drücken Sie **F5** , um das Projekt zu erstellen und auszuführen.

     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die dem Dokument zugeordnet ist. Visual Studio legt eine Kopie des Dokuments und der Assembly im Buildausgabeordner für das Projekt ab und konfiguriert die Sicherheitseinstellungen auf dem Entwicklungscomputer, damit die Anpassung ausgeführt werden kann. Weitere Informationen finden Sie unter [Erstellen von Office](../vsto/building-office-solutions.md)-Projektmappen.

2. Vergewissern Sie sich im Dokument, dass der folgende Text angezeigt wird.

     **Dieser Text wurde mithilfe des Designers hinzugefügt.**

     **Dieser Text wurde per Code hinzugefügt.**

3. Schließen Sie das Dokument.

## <a name="clean-up-the-project"></a>Bereinigen des Projekts

 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, sollten Sie die Dateien im Buildausgabeordner und die Sicherheitseinstellungen entfernen, die durch den Buildvorgang erstellt wurden.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>So bereinigen Sie das abgeschlossene Projekt auf dem Entwicklungscomputer

1. Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.

## <a name="next-steps"></a>Nächste Schritte

 Da Sie nun eine grundlegende Anpassung auf Dokumentebene für Word erstellt haben, können Sie mehr über die Entwicklung von Anpassungen in den folgenden Themen erfahren:

- Allgemeine Programmieraufgaben, die Sie in Anpassungen auf Dokument Ebene durchführen können: [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md).

- Programmieren von Aufgaben, die für Anpassungen auf Dokument Ebene für Word: [Word](../vsto/word-solutions.md)-Projektmappen spezifisch sind.

- Verwenden des Word-Objektmodells: [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md).

- Anpassen der Benutzeroberfläche von Word, z. b. durch Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband oder Erstellen eines eigenen Aktionsbereichs: [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

- Verwenden von erweiterten Word-Objekten, die von Office-Projektmappen in Visual Studio bereitgestellt werden, um Aufgaben auszuführen, die mithilfe des Word-Objektmodells nicht möglich sind (z. b. das Hosting von verwalteten Steuerelementen in Dokumenten und das Binden von Word-Steuerelementen an Daten mithilfe des Windows Forms Daten Bindungs Modells): [Automatisieren von Wörtern](../vsto/automating-word-by-using-extended-objects.md)

- Erstellen und Debuggen von Anpassungen auf Dokument Ebene für Word: [Erstellen von Office](../vsto/building-office-solutions.md)-Projektmappen.

- Bereitstellen von Anpassungen auf Dokument Ebene für Word: bereitstellen [einer Office](../vsto/deploying-an-office-solution.md)-Projekt Mappe.

## <a name="see-also"></a>Weitere Informationen

- [Übersicht über die Entwicklung von Office-Lösungen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Word-Lösungen](../vsto/word-solutions.md)
- [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md)
- [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)
- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
- [Erstellen von Office-Lösungen](../vsto/building-office-solutions.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
- [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)
