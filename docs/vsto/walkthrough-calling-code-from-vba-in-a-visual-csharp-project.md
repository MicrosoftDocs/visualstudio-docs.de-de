---
title: 'Exemplarische Vorgehensweise: Abrufen von Code aus VBA in einem Visual c#-Projekt'
description: Erfahren Sie, wie Sie eine Methode in einer Anpassung auf Dokument Ebene für Microsoft Excel aus Visual Basic for Applications (VBA)-Code in der Arbeitsmappe abrufen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], calling code from VBA
- Word [Office development in Visual Studio], calling code from VBA
- Visual C# [Office development in Visual Studio], calling code from VBA
- workbooks [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: daf25a1e2e80d2c5918d0d11c4b31c75a2e40c87
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527295"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-c-project"></a>Exemplarische Vorgehensweise: Abrufen von Code aus VBA in einem Visual c#-Projekt
  Diese exemplarische Vorgehensweise veranschaulicht, wie eine Methode in einer Anpassung auf Dokumentebene für Microsoft Office Excel aus VBA-Code (Visual Basic for Applications) in der Arbeitsmappe aufgerufen wird. Das Verfahren umfasst drei grundlegende Schritte: Hinzufügen einer Methode zur `Sheet1` -Hostelementklasse, Verfügbarmachen der Methode für VBA-Code und Aufrufen der Methode aus VBA-Code in der Arbeitsmappe.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Obwohl in dieser exemplarischen Vorgehensweise speziell Excel verwendet wird, gelten die Konzepte in dieser exemplarischen Vorgehensweise auch für Word-Projekte auf Dokumentebene.

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen einer Arbeitsmappe, die VBA-Code enthält

- Festlegen des Arbeitsmappenspeicherorts als vertrauenswürdig im Trust Center in Excel

- Hinzufügen einer Methode, zur `Sheet1` -Hostelementklasse

- Extrahieren einer Schnittstelle für die `Sheet1` -Hostelementklasse

- Verfügbarmachen der Methode für VBA-Code

- Aufrufen der Methode aus VBA-Code

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-a-workbook-that-contains-vba-code"></a>Erstellen einer Arbeitsmappe, die VBA-Code enthält
 Im ersten Schritt wird eine Arbeitsmappe mit Makros erstellt, die ein einfaches VBA-Makro enthält. Bevor Sie Code in einer Anpassung für VBA verfügbar machen können, muss die Arbeitsmappe bereits VBA-Code enthalten. Andernfalls kann Visual Studio das VBA-Projekt nicht ändern, um dem VBA-Code das Aufrufen der Anpassungsassembly zu ermöglichen.

 Wenn Sie bereits über eine Arbeitsmappe mit VBA-Code verfügen, den Sie verwenden möchten, können Sie diesen Schritt überspringen.

### <a name="to-create-a-workbook-that-contains-vba-code"></a>So erstellen Sie eine Arbeitsmappe, die VBA-Code enthält

1. Starten Sie Excel.

2. Speichern Sie das aktive Dokument als **Excel-Macro-Enabled Arbeitsmappe ( \* . xlsm)** mit dem Namen **WorkbookWithVBA**. Speichern Sie es an einem geeigneten Speicherort, z. B. auf dem Desktop.

3. Klicken Sie im Menüband auf die Registerkarte **Entwickler** .

    > [!NOTE]
    > Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter Gewusst [wie: Anzeigen der Registerkarte "Entwickler" im Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Klicken Sie in der Gruppe **Code** auf **Visual Basic**.

     Der Visual Basic-Editor wird geöffnet.

5. Doppelklicken Sie im **Projektfenster** auf **DieseArbeitsmappe**.

     Die Codedatei für das `ThisWorkbook` -Objekt wird geöffnet.

6. Fügen Sie der Codedatei den folgenden VBA-Code hinzu. Dieser Code definiert eine einfache Funktion, die keine Aktion ausführt. Diese Funktion soll lediglich sicherstellen, dass ein VBA-Projekt in der Arbeitsmappe vorhanden ist. Dies ist für spätere Schritte in dieser exemplarischen Vorgehensweise erforderlich.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. Speichern Sie das Dokument, und beenden Sie Excel.

## <a name="create-the-project"></a>Erstellen des Projekts
 Jetzt können Sie ein Projekt auf Dokumentebene für Excel erstellen, das die zuvor erstellte Arbeitsmappe mit Makros verwendet.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

3. Erweitern Sie im Vorlagenbereich **Visual C#** und dann **Office/SharePoint**.

4. Wählen Sie den Knoten **Office-Add-Ins** aus.

5. Wählen Sie in der Liste der Projektvorlagen das Projekt **Excel 2010-Arbeitsmappe** oder **Excel 2013-Arbeitsmappe** aus.

6. Geben Sie im Feld **Name** die Zeichenfolge **CallingCodeFromVBA** ein.

7. Klicken Sie auf **OK**.

     Der **Projekt-Assistent aus Visual Studio Tools for Office** wird geöffnet.

8. Wählen Sie **Vorhandenes Dokument kopieren** aus, und geben Sie im Feld **Vollständiger Pfad zum vorhandenen Dokument** den Speicherort der zuvor erstellten Arbeitsmappe **WorkbookWithVBA** an. Wenn Sie Ihre eigene Arbeitsmappe mit Makros verwenden, geben Sie stattdessen den Speicherort dieser Arbeitsmappe an.

9. Klicken Sie auf **Fertig stellen**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Öffnet die Arbeitsmappe **WorkbookWithVBA** im Designer und fügt **Projektmappen-Explorer** das Projekt **CallingCodeFromVBA** hinzu.

## <a name="trust-the-location-of-the-workbook"></a>Vertrauensstellung des Speicher Orts der Arbeitsmappe
 Bevor Sie Code in der Projektmappe für VBA-Code in der Arbeitsmappe verfügbar machen können, müssen Sie VBA in der Arbeitsmappe als vertrauenswürdig festlegen, damit es ausgeführt werden kann. Hierzu stehen mehrere Vorgehensweisen zur Verfügung. In dieser exemplarischen Vorgehensweise führen Sie diese Aufgabe aus, indem Sie den Speicherort der Arbeitsmappe im **Trust Center** in Excel als vertrauenswürdig festlegen.

### <a name="to-trust-the-location-of-the-workbook"></a>So legen Sie den Arbeitsmappenspeicherort als vertrauenswürdig fest

1. Starten Sie Excel.

2. Klicken Sie auf die Registerkarte **Datei** .

3. Klicken Sie auf die Schaltfläche **Excel-Optionen** .

4. Klicken Sie im Bereich "Kategorien" auf **Trust Center**.

5. Klicken Sie im Detailbereich auf **Einstellungen für das Trust Center**.

6. Klicken Sie im Bereich "Kategorien" auf **Vertrauenswürdige Speicherorte**.

7. Klicken Sie im Detailbereich auf **Neuen Speicherort hinzufügen**.

8. Navigieren Sie im Dialogfeld **Vertrauenswürdiger Microsoft Office-Speicherort** zu dem Ordner mit dem Projekt **CallingCodeFromVBA** .

9. Wählen Sie **Unterordner dieses Speicherorts sind ebenfalls vertrauenswürdig** aus.

10. Klicken Sie im Dialogfeld **Vertrauenswürdiger Microsoft Office-Speicherort** auf **OK**.

11. Klicken Sie im Dialogfeld **Trust Center** auf **OK**.

12. Klicken Sie im Dialogfeld **Excel-Optionen** auf **OK**.

13. Beenden Sie **Excel**.

## <a name="add-a-method-to-the-sheet1-class"></a>Hinzufügen einer Methode zur Sheet1-Klasse
 Nun, da das VBA-Projekt eingerichtet ist, fügen Sie der `Sheet1` -Hostelementklasse eine öffentliche Methode hinzu, die Sie aus VBA-Code aufrufen können.

### <a name="to-add-a-method-to-the-sheet1-class"></a>So fügen Sie der Sheet1-Klasse eine Methode hinzu

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Sheet1.cs**, und klicken Sie dann auf **Code anzeigen**.

     Die Datei **Sheet1.cs** wird im Code-Editor geöffnet.

2. Fügen Sie der `Sheet1` -Klasse den folgenden Code hinzu. Die `CreateVstoNamedRange` -Methode erstellt ein neues <xref:Microsoft.Office.Tools.Excel.NamedRange> -Objekt im angegebenen Bereich. Durch diese Methode wird auch ein Ereignishandler für das <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> -Ereignis von <xref:Microsoft.Office.Tools.Excel.NamedRange>erstellt. Weiter unten in dieser exemplarischen Vorgehensweise rufen Sie die `CreateVstoNamedRange` -Methode aus VBA-Code im Dokument auf.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#2](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#2)]

3. Füge der `Sheet1`-Klasse die folgende Methode hinzu. Mit dieser Methode wird die <xref:Microsoft.Office.Tools.Excel.WorksheetBase.GetAutomationObject%2A> -Methode überschrieben, um die aktuelle Instanz der `Sheet1` -Klasse zurückzugeben.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#3](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#3)]

4. Wenden Sie die folgenden Attribute vor der ersten Zeile der `Sheet1` -Klassendeklaration an. Diese Attribute machen die Klasse für COM sichtbar, generieren aber keine Klassenschnittstelle.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#1](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#1)]

## <a name="extract-an-interface-for-the-sheet1-class"></a>Extrahieren einer Schnittstelle für die Sheet1-Klasse
 Bevor Sie die `CreateVstoNamedRange` -Methode für VBA-Code verfügbar machen können, müssen Sie eine öffentliche Schnittstelle erstellen, die diese Methode definiert, und diese Schnittstelle für COM verfügbar machen.

### <a name="to-extract-an-interface-for-the-sheet1-class"></a>So extrahieren Sie eine Schnittstelle für die Sheet1-Klasse

1. Klicken Sie in der Codedatei **Sheet1.cs** in der `Sheet1` -Klasse auf eine beliebige Stelle.

2. Klicken Sie im Menü **Umgestalten** auf **Schnittstelle extrahieren**.

3. Klicken Sie im Dialogfeld **Schnittstelle extrahieren** im Feld **Öffentliche Member zum Bilden einer Schnittstelle auswählen** auf den Eintrag für die `CreateVstoNamedRange` -Methode.

4. Klicken Sie auf **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] generiert die neue Schnittstelle `ISheet1`und ändert die Definition der `Sheet1` -Klasse, damit die `ISheet1` -Schnittstelle implementiert wird. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] öffnet außerdem die Datei **ISheet1.cs** im Code-Editor.

5. Ersetzen Sie in der Datei **ISheet1.cs** die `ISheet1` -Schnittstellendeklaration durch den folgenden Code. Dieser Code macht `ISheet1` zu einer öffentlichen Schnittstelle und wendet das <xref:System.Runtime.InteropServices.ComVisibleAttribute> -Attribut an, um die Schnittstelle für COM sichtbar zu machen.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#4](../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs#4)]

6. Erstellen Sie das Projekt.

## <a name="expose-the-method-to-vba-code"></a>Verfügbar machen der Methode für VBA-Code
 Zum Verfügbarmachen der `CreateVstoNamedRange` -Methode für VBA-Code in der Arbeitsmappe legen Sie die **ReferenceAssemblyFromVbaProject** -Eigenschaft für das `Sheet1` -Hostelement auf **True** fest.

### <a name="to-expose-the-method-to-vba-code"></a>So machen Sie die Methode für VBA-Code verfügbar

1. Doppelklicken Sie im **Projektmappen-Explorer** auf **Sheet1.cs**.

     Die Datei **WorkbookWithVBA** wird im Designer mit "Sheet1" geöffnet.

2. Wählen Sie im Fenster **Eigenschaften** die **ReferenceAssemblyFromVbaProject** -Eigenschaft aus, und ändern Sie den Wert in **True**.

3. Klicken Sie in der Meldung, die angezeigt wird, auf **OK** .

4. Erstellen Sie das Projekt.

## <a name="call-the-method-from-vba-code"></a>Abrufen der Methode aus VBA-Code
 Jetzt können Sie die `CreateVstoNamedRange` -Methode aus dem VBA-Code in der Arbeitsmappe aufrufen.

> [!NOTE]
> In dieser exemplarischen Vorgehensweise fügen Sie der Arbeitsmappe VBA-Code beim Debuggen des Projekts hinzu. Der VBA-Code, den Sie diesem Dokument hinzufügen, wird beim nächsten Erstellen des Projekts überschrieben. Visual Studio ersetzt das Dokument im Buildausgabeordner durch eine Kopie des Dokuments aus dem Hauptordner des Projekts. Wenn Sie den VBA-Code speichern möchten, können Sie ihn in das Dokument im Projektordner kopieren. Weitere Informationen finden Sie unter [Kombinieren von VBA und Anpassungen auf Dokument Ebene](../vsto/combining-vba-and-document-level-customizations.md).

### <a name="to-call-the-method-from-vba-code"></a>So rufen Sie die Methode aus VBA-Code auf

1. Drücken Sie **F5** , um das Projekt auszuführen.

2. Klicken Sie auf der Registerkarte **Entwickler** in der Gruppe **Code** auf **Visual Basic**.

     Der Visual Basic-Editor wird geöffnet.

3. Klicken Sie im Menü **Einfügen** auf **Modul**.

4. Fügen Sie dem neuen Modul den folgenden Code hinzu.

     Dieser Code Ruft die `CreateTable` -Methode in der Anpassungsassembly auf. Das Makro greift auf diese Methode zu, indem es die globale `GetManagedClass` -Methode für den Zugriff auf die `Sheet1` -Hostelementklasse verwendet, die Sie für VBA-Code verfügbar gemacht haben. Die `GetManagedClass` -Methode wurde beim Festlegen der **ReferenceAssemblyFromVbaProject** -Eigenschaft weiter oben in dieser exemplarischen Vorgehensweise automatisch generiert.

    ```vb
    Sub CallVSTOMethod()
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1
        Set VSTOSheet1 = GetManagedClass(Sheet1)
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")
    End Sub
    ```

5. Drücken Sie **F5**.

6. Klicken Sie in der geöffneten Arbeitsmappe in **Sheet1** auf die Zelle **A1**. Vergewissern Sie sich, dass das Meldungsfeld angezeigt wird.

7. Beenden Sie Excel, ohne Ihre Änderungen zu speichern.

## <a name="next-steps"></a>Nächste Schritte
 In den folgenden Themen erfahren Sie mehr über das Aufrufen von Code in Office-Projektmappen aus VBA:

- Aufrufen von Code in einem Hostelement in einer Visual Basic-Anpassung aus VBA Dieses Verfahren unterscheidet sich vom Visual C#-Verfahren. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Abrufen von Code aus VBA in einem Visual Basic Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).

- Aufrufen von Code in einem VSTO-Add-In aus VBA Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Abrufen von Code in einem VSTO-Add-in aus VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

## <a name="see-also"></a>Weitere Informationen
- [Kombinieren von VBA und Anpassungen auf Dokument Ebene](../vsto/combining-vba-and-document-level-customizations.md)
- [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md)
- [Gewusst wie: verfügbar machen von Code für VBA in einem Visual Basic Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Gewusst wie: verfügbar machen von Code für VBA in einem Visual C-&#35; Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Exemplarische Vorgehensweise: Abrufen von Code aus VBA in einem Visual Basic Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
