---
title: 'Exemplarische Vorgehensweise: Abrufen von Code aus VBA in einem Visual Basic Projekt'
description: Erfahren Sie, wie Sie eine Methode in einer Anpassung auf Dokument Ebene für Microsoft Word aus Visual Basic for Applications (VBA)-Code im Dokument aufzurufen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- ThisDocument class
- Word [Office development in Visual Studio], calling code from VBA
- Visual Basic [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bcb13ec0e26b1668a397d56982d049bf9ebcceb0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906543"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-basic-project"></a>Exemplarische Vorgehensweise: Abrufen von Code aus VBA in einem Visual Basic Projekt
  Diese exemplarische Vorgehensweise veranschaulicht, wie eine Methode in einer Anpassung auf Dokumentebene für Microsoft Office Word aus VBA-Code (Visual Basic for Applications) im Dokument aufgerufen wird. Das Verfahren umfasst drei grundlegende Schritte: Hinzufügen einer Methode zur `ThisDocument` -Hostelementklasse, Verfügbarmachen der Methode für VBA-Code und Aufrufen der Methode aus VBA-Code im Dokument.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Obwohl in dieser exemplarischen Vorgehensweise speziell Word verwendet wird, gelten die Konzepte in dieser exemplarischen Vorgehensweise auch für Excel-Projekte auf Dokumentebene.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines Dokuments, das VBA-Code enthält

- Festlegen des Dokumentspeicherorts als vertrauenswürdig im Trust Center in Word

- Hinzufügen einer Methode, zur `ThisDocument` -Hostelementklasse

- Verfügbarmachen der Methode für VBA-Code

- Aufrufen der Methode aus VBA-Code

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-a-document-that-contains-vba-code"></a>Erstellen eines Dokuments, das VBA-Code enthält
 Im ersten Schritt wird ein Dokument mit Makros erstellt, das ein einfaches VBA-Makro enthält. Das Dokument muss ein VBA-Projekt enthalten, bevor Sie ein Visual Studio-Projekt erstellen, das auf dem Dokument basiert. Andernfalls kann Visual Studio das VBA-Projekt nicht ändern, um dem VBA-Code das Aufrufen der Anpassungsassembly zu ermöglichen.

 Wenn Sie bereits über ein Dokument mit VBA-Code verfügen, den Sie verwenden möchten, können Sie diesen Schritt überspringen.

### <a name="to-create-a-document-that-contains-vba-code"></a>So erstellen Sie ein Dokument, das VBA-Code enthält

1. Starten Sie Word.

2. Speichern Sie das aktive Dokument als Word **-Dokument mit Makros ( \* . docm)** mit dem Namen **DocumentWithVBA**. Speichern Sie sie an einem geeigneten Speicherort, z. B. auf dem Desktop.

3. Klicken Sie im Menüband auf die Registerkarte **Entwickler** .

    > [!NOTE]
    > Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter Gewusst [wie: Anzeigen der Registerkarte "Entwickler" im Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Klicken Sie in der Gruppe **Code** auf **Visual Basic**.

     Der Visual Basic-Editor wird geöffnet.

5. Doppelklicken Sie im Fenster **Projekt** auf **ThisDocument**.

     Die Codedatei für das `ThisDocument` -Objekt wird geöffnet.

6. Fügen Sie der Codedatei den folgenden VBA-Code hinzu. Dieser Code definiert eine einfache Funktion, die keine Aktion ausführt. Diese Funktion soll lediglich sicherstellen, dass ein VBA-Projekt im Dokument vorhanden ist. Dies ist für spätere Schritte in dieser exemplarischen Vorgehensweise erforderlich.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. Speichern Sie das Dokument, und beenden Sie Word.

## <a name="create-the-project"></a>Erstellen des Projekts
 Jetzt können Sie ein Projekt auf Dokumentebene für Word erstellen, das das zuvor erstellte Dokument mit Makros verwendet.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**. Wenn die IDE auf die Verwendung von Visual Basic-Entwicklungseinstellungen festgelegt ist, klicken Sie im Menü **Datei** auf **Neues Projekt**.

3. Erweitern Sie im Vorlagenbereich **Visual Basic** und dann **Office/SharePoint**.

4. Wählen Sie den Knoten **Office-Add-Ins** aus.

5. Wählen Sie in der Liste der Projektvorlagen das Projekt **Word 2010-Dokument** oder **Word 2013-Dokument** aus.

6. Geben Sie im Feld **Name** die Zeichenfolge **CallingCodeFromVBA** ein.

7. Klicken Sie auf **OK**.

     Der **Projekt-Assistent aus Visual Studio Tools for Office** wird geöffnet.

8. Wählen Sie **Vorhandenes Dokument kopieren** aus, und geben Sie im Feld **Vollständiger Pfad zum vorhandenen Dokument** den Speicherort des zuvor erstellten Dokuments **DocumentWithVBA** an. Wenn Sie Ihr eigenes Dokument mit Makros verwenden, geben Sie stattdessen den Speicherort dieses Dokuments an.

9. Klicken Sie auf **Fertig stellen**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Öffnet das Dokument **DocumentWithVBA** im Designer und fügt **Projektmappen-Explorer** das Projekt **CallingCodeFromVBA** hinzu.

## <a name="trust-the-location-of-the-document"></a>Dem Speicherort des Dokuments Vertrauen
 Bevor Sie Code in der Projektmappe für VBA-Code im Dokument verfügbar machen können, müssen Sie VBA im Dokument als vertrauenswürdig festlegen, damit es ausgeführt werden kann. Hierzu stehen mehrere Vorgehensweisen zur Verfügung. In dieser exemplarischen Vorgehensweise legen Sie den Speicherort des Dokuments im **Trust Center** in Word als vertrauenswürdig fest.

### <a name="to-trust-the-location-of-the-document"></a>So legen Sie den Dokumentspeicherort als vertrauenswürdig fest

1. Starten Sie Word.

2. Klicken Sie auf die Registerkarte **Datei** .

3. Klicken Sie auf die Schaltfläche **Word-Optionen** .

4. Klicken Sie im Bereich "Kategorien" auf **Trust Center**.

5. Klicken Sie im Detailbereich auf **Einstellungen für das Trust Center**.

6. Klicken Sie im Bereich "Kategorien" auf **Vertrauenswürdige Speicherorte**.

7. Klicken Sie im Detailbereich auf **Neuen Speicherort hinzufügen**.

8. Navigieren Sie im Dialogfeld **Vertrauenswürdiger Microsoft Office-Speicherort** zu dem Ordner mit dem Projekt **CallingCodeFromVBA** .

9. Wählen Sie **Unterordner dieses Speicherorts sind ebenfalls vertrauenswürdig** aus.

10. Klicken Sie im Dialogfeld **Vertrauenswürdiger Microsoft Office-Speicherort** auf **OK**.

11. Klicken Sie im Dialogfeld **Trust Center** auf **OK**.

12. Klicken Sie im Dialogfeld **Word-Optionen** auf **OK**.

13. Beenden Sie Word.

## <a name="add-a-method-to-the-thisdocument-class"></a>Hinzufügen einer Methode zur ThisDocument-Klasse
 Nun, da das VBA-Projekt eingerichtet ist, fügen Sie der `ThisDocument` -Hostelementklasse eine Methode hinzu, die Sie aus VBA-Code aufrufen können.

### <a name="to-add-a-method-to-the-thisdocument-class"></a>So fügen Sie der ThisDocument-Klasse eine Methode hinzu

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **ThisDocument.vb**, und klicken Sie dann auf **Code anzeigen**.

     Die Datei **ThisDocument.vb** wird im Code-Editor geöffnet.

2. Füge der `ThisDocument`-Klasse die folgende Methode hinzu. Durch diese Methode wird eine Tabelle mit zwei Zeilen und zwei Spalten am Anfang des Dokuments erstellt. Die Parameter geben den Text an, der in der ersten Zeile angezeigt wird. Weiter unten in dieser exemplarischen Vorgehensweise rufen Sie diese Methode aus VBA-Code im Dokument auf.

     [!code-vb[Trin_CallingVBCustomizationFromVBA#1](../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb#1)]

3. Erstellen Sie das Projekt.

## <a name="expose-the-method-to-vba-code"></a>Verfügbar machen der Methode für VBA-Code
 Um die `CreateTable` -Methode für VBA-Code im Dokument verfügbar zu machen, legen Sie die **EnableVbaCallers** -Eigenschaft für das `ThisDocument` -Hostelement auf **True** fest.

### <a name="to-expose-the-method-to-vba-code"></a>So machen Sie die Methode für VBA-Code verfügbar

1. Doppelklicken Sie im **Projektmappen-Explorer** auf **ThisDocument.vb**.

     Die Datei **DocumentWithVBA** wird im Designer geöffnet.

2. Wählen Sie im Fenster **Eigenschaften** die **EnableVbaCallers** -Eigenschaft aus, und ändern Sie den Wert in **True**.

3. Klicken Sie in der Meldung, die angezeigt wird, auf **OK** .

4. Erstellen Sie das Projekt.

## <a name="call-the-method-from-vba-code"></a>Abrufen der Methode aus VBA-Code
 Jetzt können Sie die `CreateTable` -Methode aus VBA-Code im Dokument aufrufen.

> [!NOTE]
> In dieser exemplarischen Vorgehensweise fügen Sie dem Dokument VBA-Code beim Debuggen des Projekts hinzu. Der VBA-Code, den Sie diesem Dokument hinzufügen, wird beim nächsten Erstellen des Projekts überschrieben. Visual Studio ersetzt das Dokument im Buildausgabeordner durch eine Kopie des Dokuments aus dem Hauptordner des Projekts. Wenn Sie den VBA-Code speichern möchten, können Sie ihn in das Dokument im Projektordner kopieren. Weitere Informationen finden Sie unter [Kombinieren von VBA und Anpassungen auf Dokument Ebene](../vsto/combining-vba-and-document-level-customizations.md).

### <a name="to-call-the-method-from-vba-code"></a>So rufen Sie die Methode aus VBA-Code auf

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Klicken Sie auf der Registerkarte **Entwickler** in der Gruppe **Code** auf **Visual Basic**.

     Der Visual Basic-Editor wird geöffnet.

3. Klicken Sie im Menü **Einfügen** auf **Modul**.

4. Fügen Sie dem neuen Modul den folgenden Code hinzu.

     Dieser Code Ruft die `CreateTable` -Methode in der Anpassungsassembly auf. Das Makro greift mithilfe der `CallVSTOAssembly` -Eigenschaft des `ThisDocument` -Objekts auf diese Methode zu. Diese Eigenschaft wurde beim Festlegen der **EnableVbaCallers** -Eigenschaft weiter oben in dieser exemplarischen Vorgehensweise automatisch generiert.

    ```vb
    Sub CreateTable()
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")
    End Sub
    ```

5. Drücken Sie **F5**.

6. Überprüfen Sie, ob dem Dokument eine neue Tabelle hinzugefügt wurde.

7. Beenden Sie Word, ohne Ihre Änderungen zu speichern.

## <a name="next-steps"></a>Nächste Schritte
 In den folgenden Themen erfahren Sie mehr über das Aufrufen von Code in Office-Projektmappen aus VBA:

- Aufrufen von Code in einer Visual C#-Anpassung aus VBA Dieses Verfahren unterscheidet sich vom Visual Basic-Verfahren. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Abrufen von Code aus VBA in einem Visual C-&#35; Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).

- Aufrufen von Code in einem VSTO-Add-In aus VBA Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Abrufen von Code in einem VSTO-Add-in aus VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

## <a name="see-also"></a>Weitere Informationen
- [Kombinieren von VBA und Anpassungen auf Dokument Ebene](../vsto/combining-vba-and-document-level-customizations.md)
- [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md)
- [Gewusst wie: verfügbar machen von Code für VBA in einem Visual Basic Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Gewusst wie: verfügbar machen von Code für VBA in einem Visual C-&#35; Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Exemplarische Vorgehensweise: Abrufen von Code aus VBA in einem Visual C-&#35; Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
