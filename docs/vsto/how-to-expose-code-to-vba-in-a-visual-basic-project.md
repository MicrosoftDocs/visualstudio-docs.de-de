---
title: 'Gewusst wie: verfügbar machen von Code für VBA in einem Visual Basic Projekt'
description: Erfahren Sie, wie Sie Code in einem Visual Basic Projekt zum Visual Basic for Applications (VBA)-Code verfügbar machen können, wenn Sie möchten, dass die beiden Code Typen miteinander interagieren.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 69ef8b47ac4038b466d0ebf859832bd4363403cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913489"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Gewusst wie: verfügbar machen von Code für VBA in einem Visual Basic Projekt
  Sie können Code in einem [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Projekt zum Visual Basic for Applications (VBA-Code) verfügbar machen, wenn Sie möchten, dass die beiden Code Typen miteinander interagieren.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Der Visual Basic Prozess unterscheidet sich vom Visual c#-Prozess. Weitere Informationen finden Sie unter Gewusst wie: verfügbar machen von [Code für VBA in einem Visual C-&#35; Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).

 Der Prozess unterscheidet sich für Code in einer Host Element Klasse, als er für Code in anderen Klassen gilt:

- [Verfügbar machen von Code in einer Host Element Klasse](#HostItemCode)

- [Verfügbar machen von Code, der nicht in einer Host Element Klasse ist](#NonHostItem)

## <a name="expose-code-in-a-host-item-class"></a><a name="HostItemCode"></a> Verfügbar machen von Code in einer Host Element Klasse
 Um VBA-Code zum Aufrufen von Visual Basic Code in einer Host Element Klasse zu aktivieren, legen Sie die **enablevbacallzer** -Eigenschaft des Host Elements auf **true** fest.

 Eine exemplarische Vorgehensweise, in der veranschaulicht wird, wie eine Methode einer Host Element Klasse verfügbar gemacht wird, und Sie dann über VBA aufgerufen wird, finden Sie unter Exemplarische Vorgehensweise [: Abrufen von Code aus VBA in einem Visual Basic Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Weitere Informationen zu Host Elementen finden Sie unter [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md).

#### <a name="to-expose-code-in-a-host-item-to-vba"></a>So machen Sie Code in einem Host Element für VBA verfügbar

1. Öffnen oder erstellen Sie ein Projekt auf Dokument Ebene, [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] das auf einem Word-Dokument, einer Excel-Arbeitsmappe oder einer Excel-Vorlage basiert, die Makros unterstützt und bereits VBA-Code enthält.

     Weitere Informationen zu den Dokument Dateiformaten, die Makros unterstützen, finden Sie unter [Kombinieren von VBA und Anpassungen auf Dokument Ebene](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Diese Funktion kann in Word-Vorlagenprojekten nicht verwendet werden.

2. Stellen Sie sicher, dass VBA-Code im Dokument ausgeführt werden darf, ohne dass der Benutzer aufgefordert wird, Makros zu aktivieren. Sie können die Vertrauenswürdigkeit für die Ausführung des VBA-Codes angeben, indem Sie den Speicherort des Office-Projekts der Liste der vertrauenswürdigen Speicherorte in den Trust Center-Einstellungen für Word oder Excel hinzufügen.

3. Fügen Sie die Eigenschaft, die Methode oder das Ereignis, die Sie für VBA verfügbar machen möchten, einer der Host Element Klassen im Projekt hinzu, und deklarieren Sie den neuen Member als **öffentlich**. Der Name der Klasse hängt von der Anwendung ab:

    - In einem Word-Projekt wird die Host Element Klasse `ThisDocument` standardmäßig benannt.

    - In einem Excel-Projekt werden die Host Element Klassen `ThisWorkbook` `Sheet1` `Sheet2` standardmäßig,, und genannt `Sheet3` .

4. Legen Sie die **enablevbacallzer** -Eigenschaft für das-Host Element auf **true** fest. Diese Eigenschaft ist im Fenster **Eigenschaften** verfügbar, wenn das Host Element im Designer geöffnet ist.

     Nachdem Sie diese Eigenschaft festgelegt haben, legt Visual Studio automatisch die **ReferenceAssemblyFromVbaProject** -Eigenschaft auf **true** fest.

    > [!NOTE]
    > Wenn die Arbeitsmappe oder das Dokument nicht bereits VBA-Code enthält oder VBA-Code im Dokument nicht als vertrauenswürdig eingestuft wird, erhalten Sie eine Fehlermeldung, wenn Sie die **enablevbacallzer** -Eigenschaft auf " **true**" festlegen. Dies liegt daran, dass Visual Studio das VBA-Projekt im Dokument in dieser Situation nicht ändern kann.

5. Klicken Sie in der Meldung, die angezeigt wird, auf **OK** . Diese Meldung weist darauf hin, dass beim [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nächsten Erstellen des Projekts der VBA-Code beim nächsten Erstellen des Projekts verloren geht, wenn Sie der Arbeitsmappe oder dem Dokument VBA-Code hinzufügen. Dies liegt daran, dass das Dokument im Buildausgabeordner jedes Mal überschrieben wird, wenn Sie das Projekt erstellen.

     An diesem Punkt konfiguriert Visual Studio das Projekt so, dass das VBA-Projekt in der Assembly aufgerufen werden kann. Visual Studio fügt `CallVSTOAssembly` dem `ThisDocument` `ThisWorkbook` Modul,, `Sheet1` , `Sheet2` oder `Sheet3` im VBA-Projekt auch eine Eigenschaft mit dem Namen hinzu. Sie können diese Eigenschaft verwenden, um auf öffentliche Member der Klasse zuzugreifen, die Sie für VBA verfügbar gemacht haben.

6. Erstellen Sie das Projekt.

## <a name="expose-code-that-is-not-in-a-host-item-class"></a><a name="NonHostItem"></a> Verfügbar machen von Code, der nicht in einer Host Element Klasse ist
 Damit VBA-Code Visual Basic Code aufruft, der sich nicht in einer Host Element Klasse befindet, ändern Sie den Code so, dass er für VBA sichtbar ist.

### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>So machen Sie Code, der nicht in einer Host Element Klasse für VBA verfügbar ist

1. Öffnen oder erstellen Sie ein Projekt auf Dokument Ebene, [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] das auf einem Word-Dokument, einer Excel-Arbeitsmappe oder einer Excel-Vorlage basiert, die Makros unterstützt und bereits VBA-Code enthält.

     Weitere Informationen zu den Dokument Dateiformaten, die Makros unterstützen, finden Sie unter [Kombinieren von VBA und Anpassungen auf Dokument Ebene](../vsto/combining-vba-and-document-level-customizations.md).

    > [!NOTE]
    > Diese Funktion kann in Word-Vorlagenprojekten nicht verwendet werden.

2. Stellen Sie sicher, dass VBA-Code im Dokument ausgeführt werden darf, ohne dass der Benutzer aufgefordert wird, Makros zu aktivieren. Sie können die Vertrauenswürdigkeit für die Ausführung des VBA-Codes angeben, indem Sie den Speicherort des Office-Projekts der Liste der vertrauenswürdigen Speicherorte in den Trust Center-Einstellungen für Word oder Excel hinzufügen.

3. Fügen Sie den Member, den Sie für VBA verfügbar machen möchten, einer öffentlichen Klasse in Ihrem Projekt hinzu, und deklarieren Sie den neuen Member als **öffentlich**.

4. Wenden Sie die folgenden <xref:System.Runtime.InteropServices.ComVisibleAttribute> -und- <xref:Microsoft.VisualBasic.ComClassAttribute> Attribute auf die-Klasse an, die Sie für VBA verfügbar machen. Diese Attribute machen die Klasse für VBA sichtbar.

    ```vb
    <Microsoft.VisualBasic.ComClass()> _
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _
    ```

5. Überschreiben Sie die **GetAutomationObject** -Methode einer Hostelementklasse in Ihrem Projekt, um eine Instanz der Klasse zurückzugeben, die Sie für VBA verfügbar machen. Im folgenden Codebeispiel wird davon ausgegangen, dass Sie eine Klasse `DocumentUtilities` mit dem Namen VBA verfügbar machen.

    ```vb
    Protected Overrides Function GetAutomationObject() As Object
        Return New DocumentUtilities()
    End Function
    ```

6. Öffnen Sie das Dokument (für Word) oder den Arbeitsblatt-Designer (für Excel) in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

7. Wählen Sie im Fenster **Eigenschaften** die **ReferenceAssemblyFromVbaProject** -Eigenschaft aus, und ändern Sie den Wert in **True**.

    > [!NOTE]
    > Wenn die Arbeitsmappe oder das Dokument nicht bereits VBA-Code enthält oder VBA-Code im Dokument nicht als vertrauenswürdig eingestuft wird, erhalten Sie eine Fehlermeldung, wenn Sie die **ReferenceAssemblyFromVbaProject** -Eigenschaft auf " **true**" festlegen. Dies liegt daran, dass Visual Studio das VBA-Projekt im Dokument in dieser Situation nicht ändern kann.

8. Klicken Sie in der Meldung, die angezeigt wird, auf **OK** . Diese Meldung weist darauf hin, dass beim [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nächsten Erstellen des Projekts der VBA-Code beim nächsten Erstellen des Projekts verloren geht, wenn Sie der Arbeitsmappe oder dem Dokument VBA-Code hinzufügen. Dies liegt daran, dass das Dokument im Buildausgabeordner jedes Mal überschrieben wird, wenn Sie das Projekt erstellen.

     An diesem Punkt konfiguriert Visual Studio das Projekt so, dass das VBA-Projekt in der Assembly aufgerufen werden kann. Visual Studio fügt `GetManagedClass` dem VBA-Projekt außerdem eine Methode mit dem Namen hinzu. Sie können diese Methode von jeder beliebigen Stelle im VBA-Projekt aus aufrufen, um auf die Klasse zuzugreifen, die Sie für VBA verfügbar gemacht haben.

9. Erstellen Sie das Projekt.

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
- [Kombinieren von VBA und Anpassungen auf Dokument Ebene](../vsto/combining-vba-and-document-level-customizations.md)
- [Exemplarische Vorgehensweise: Abrufen von Code aus VBA in einem Visual Basic Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Gewusst wie: verfügbar machen von Code für VBA in einem Visual C-&#35; Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
