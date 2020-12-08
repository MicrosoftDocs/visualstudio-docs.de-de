---
title: 'Gewusst wie: verfügbar machen von Code für VBA in einem c#-Projekt'
description: Erfahren Sie, wie Sie Code in einem Visual c#-Projekt für Visual Basic for Applications (VBA)-Code verfügbar machen können, wenn Sie möchten, dass die beiden Code Typen miteinander interagieren.
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a830ec75e3997bee8d4bed9e275fc6229fec3405
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846596"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Gewusst wie: verfügbar machen von Code für VBA in einem Visual c#-Projekt
  Sie können Code in einem Visual c#-Projekt für den Visual Basic for Applications (VBA)-Code verfügbar machen, wenn Sie möchten, dass die beiden Code Typen miteinander interagieren.

 Der Visual c#-Prozess unterscheidet sich vom Visual Basic Prozess. Weitere Informationen finden Sie unter Gewusst wie: verfügbar machen von [Code für VBA in einem Visual Basic Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="expose-code-in-a-visual-c-project"></a>Verfügbar machen von Code in einem Visual c#-Projekt
 Um VBA-Code das Aufrufen von Code in einem Visual c#-Projekt zu ermöglichen, ändern Sie den Code so, dass er für com sichtbar ist, und legen Sie dann die **ReferenceAssemblyFromVbaProject** -Eigenschaft im Designer auf **true** fest.

 Eine exemplarische Vorgehensweise, in der veranschaulicht wird, wie eine Methode in einem Visual c#-Projekt aus VBA aufgerufen wird, finden Sie unter Exemplarische Vorgehensweise [: Abrufen von Code aus VBA in einem Visual C-&#35; Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).

### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>So machen Sie Code in einem Visual c#-Projekt für VBA verfügbar

1. Öffnen oder erstellen Sie ein Projekt auf Dokument Ebene, das auf einem Word-Dokument, einer Excel-Arbeitsmappe oder einer Excel-Vorlage basiert, die Makros unterstützt und bereits VBA-Code enthält.

    Weitere Informationen zu den Dokument Dateiformaten, die Makros unterstützen, finden Sie unter [Kombinieren von VBA und Anpassungen auf Dokument Ebene](../vsto/combining-vba-and-document-level-customizations.md).

   > [!NOTE]
   > Diese Funktion kann in Word-Vorlagenprojekten nicht verwendet werden.

2. Stellen Sie sicher, dass VBA-Code im Dokument ausgeführt werden darf, ohne dass der Benutzer aufgefordert wird, Makros zu aktivieren. Sie können die Vertrauenswürdigkeit für die Ausführung des VBA-Codes angeben, indem Sie den Speicherort des Office-Projekts der Liste der vertrauenswürdigen Speicherorte in den Trust Center-Einstellungen für Word oder Excel hinzufügen.

3. Fügen Sie den Member, den Sie für VBA verfügbar machen möchten, einer öffentlichen Klasse in Ihrem Projekt hinzu, und deklarieren Sie den neuen Member als **öffentlich**.

4. Wenden Sie die folgenden <xref:System.Runtime.InteropServices.ComVisibleAttribute> -und- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> Attribute auf die-Klasse an, die Sie für VBA verfügbar machen. Diese Attribute machen die Klasse für COM sichtbar, generieren aber keine Klassenschnittstelle.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   [System.Runtime.InteropServices.ClassInterface(
       System.Runtime.InteropServices.ClassInterfaceType.None)]
   ```

5. Überschreiben Sie die **GetAutomationObject** -Methode einer Host Element Klasse in Ihrem Projekt, um eine Instanz der-Klasse zurückzugeben, die Sie für VBA verfügbar machen:

   - Wenn Sie eine Host Element Klasse für VBA verfügbar machen, überschreiben Sie die **GetAutomationObject** -Methode, die zu dieser Klasse gehört, und geben Sie die aktuelle Instanz der-Klasse zurück.

     ```csharp
     protected override object GetAutomationObject()
     {
         return this;
     }
     ```

   - Wenn Sie eine Klasse verfügbar machen, bei der es sich nicht um ein Host Element für VBA handelt, überschreiben Sie die **GetAutomationObject** -Methode eines beliebigen Host Elements in Ihrem Projekt, und geben Sie eine Instanz der nicht-Host Element Klasse zurück. Im folgenden Code wird beispielsweise davon ausgegangen, dass Sie eine Klasse `DocumentUtilities` mit dem Namen VBA verfügbar machen.

     ```csharp
     protected override object GetAutomationObject()
     {
         return new DocumentUtilities();
     }
     ```

     Weitere Informationen zu Host Elementen finden Sie unter [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md).

6. Extrahieren Sie eine Schnittstelle aus der-Klasse, die Sie für VBA verfügbar machen. Wählen Sie im Dialogfeld **Schnittstelle extrahieren** die öffentlichen Member aus, die Sie in die Schnittstellen Deklaration einschließen möchten. Weitere Informationen finden Sie unter [Umgestaltung der Schnittstelle extrahieren](../ide/reference/extract-interface.md).

7. Fügen Sie der Schnittstellen Deklaration das **Public** -Schlüsselwort hinzu.

8. Machen Sie die Schnittstelle für com sichtbar, indem Sie der-Schnittstelle das folgende-Attribut hinzufügen <xref:System.Runtime.InteropServices.ComVisibleAttribute> .

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   ```

9. Öffnen Sie das Dokument (für Word) oder Arbeitsblatt (für Excel) im Designer in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

10. Wählen Sie im Fenster **Eigenschaften** die **ReferenceAssemblyFromVbaProject** -Eigenschaft aus, und ändern Sie den Wert in **True**.

    > [!NOTE]
    > Wenn die Arbeitsmappe oder das Dokument nicht bereits VBA-Code enthält oder VBA-Code im Dokument nicht als vertrauenswürdig eingestuft wird, erhalten Sie eine Fehlermeldung, wenn Sie die **ReferenceAssemblyFromVbaProject** -Eigenschaft auf " **true**" festlegen. Dies liegt daran, dass Visual Studio das VBA-Projekt im Dokument in dieser Situation nicht ändern kann.

11. Klicken Sie in der Meldung, die angezeigt wird, auf **OK** . Diese Meldung weist darauf hin, dass beim [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nächsten Erstellen des Projekts der VBA-Code beim nächsten Erstellen des Projekts verloren geht, wenn Sie der Arbeitsmappe oder dem Dokument VBA-Code hinzufügen. Dies liegt daran, dass das Dokument im Buildausgabeordner jedes Mal überschrieben wird, wenn Sie das Projekt erstellen.

     An diesem Punkt konfiguriert Visual Studio das Projekt so, dass das VBA-Projekt in der Assembly aufgerufen werden kann. Visual Studio fügt `GetManagedClass` dem VBA-Projekt außerdem eine Methode mit dem Namen hinzu. Sie können diese Methode von jeder beliebigen Stelle im VBA-Projekt aus aufrufen, um auf die Klasse zuzugreifen, die Sie für VBA verfügbar gemacht haben.

12. Erstellen Sie das Projekt.

## <a name="see-also"></a>Siehe auch
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
- [Kombinieren von VBA und Anpassungen auf Dokument Ebene](../vsto/combining-vba-and-document-level-customizations.md)
- [Exemplarische Vorgehensweise: Abrufen von Code aus VBA in einem Visual C-&#35; Projekt](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Gewusst wie: verfügbar machen von Code für VBA in einem Visual Basic Projekt](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
