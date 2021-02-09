---
title: Ereignisse in Office-Projekten
description: Erfahren Sie, wie jede Office-Projektvorlage mehrere Ereignishandler generiert und wie sich diese Ereignishandler geringfügig von Ereignis Handlern für VSTO-Add-ins unterscheiden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Sheet1_Startup
- ThisDocument_Shutdown
- ThisDocument_Startup
- application-level add-ins [Office development in Visual Studio], events
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- Sheet2_Startup
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio], events
- Sheet2_Shutdown
- Startup event
- Sheet3_Shutdown
- add-ins [Office development in Visual Studio], events
- Shutdown event
- ThisAddIn_Startup
- Sheet3_Startup
- Startup method [Office development in Visual Studio]
- Shutdown method [Office development in Visual Studio]
- Sheet1_Shutdown
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7bf4da3f0b2dd9cbab960a779690aa752744cdae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910324"
---
# <a name="events-in-office-projects"></a>Ereignisse in Office-Projekten
  Jede Office-Projektvorlage generiert automatisch mehrere Ereignishandler. Die Ereignishandler für Anpassungen auf Dokumentebene unterscheiden sich geringfügig von Ereignishandlern für VSTO-Add-Ins.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="document-level-projects"></a>Projekte auf Dokument Ebene
 Visual Studio stellt generierten Code hinter neuen oder vorhandenen Dokumenten oder Arbeitsblättern in Anpassungen auf Dokumentebene bereit. Mit diesem Code werden zwei unterschiedliche Ereignisse ausgelöst: **Startup** und **Shutdown**.

### <a name="startup-event"></a>Startup-Ereignis
 Das **Startup** -Ereignis wird für jedes Hostelement ausgelöst (Dokument, Arbeitsmappe oder Arbeitsblatt), nachdem das Dokument und der gesamte Initialisierungscode in der Assembly ausgeführt wurde. Dies ist das letzte ausgeführte Element im Konstruktor der Klasse, in dem Ihr Code ausgeführt wird. Weitere Informationen zu Host Elementen finden Sie unter [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md).

 Wenn Sie ein Projekt auf Dokumentebene erstellen, erstellt Visual Studio Ereignishandler für das **Startup** -Ereignis in den generierten Codedateien:

- Für Microsoft Office Word-Projekte hat der Ereignishandler den Namen `ThisDocument_Startup`.

- Für Microsoft Office Excel-Projekte haben die Ereignishandler die folgenden Namen:

  - `Sheet1_Startup`

  - `Sheet2_Startup`

  - `Sheet3_Startup`

  - `ThisWorkbook_Startup`

### <a name="shutdown-event"></a>Shutdown-Ereignis
 Das **Shutdown** -Ereignis wird für jedes Hostelement (Dokument oder Arbeitsblatt) ausgelöst, wenn die Anwendungsdomäne, in der Ihr Code geladen wurde, entladen werden soll. Dies ist das letzte Element, das beim Entladen in der Klasse aufgerufen wird.

 Wenn Sie ein Projekt auf Dokumentebene erstellen, erstellt Visual Studio Ereignishandler für das **Shutdown** -Ereignis in den generierten Codedateien:

- Für Microsoft Office Word-Projekte hat der Ereignishandler den Namen `ThisDocument_Shutdown`.

- Für Microsoft Office Excel-Projekte haben die Ereignishandler die folgenden Namen:

  - `Sheet1_Shutdown`

  - `Sheet2_Shutdown`

  - `Sheet3_Shutdown`

  - `ThisWorkbook_Shutdown`

> [!NOTE]
> Vermeiden Sie es, Steuerelemente während des **Shutdown** -Ereignishandlerzeitraums des Dokuments programmgesteuert zu entfernen. Die Benutzeroberflächenelemente des Dokuments sind nicht mehr verfügbar, wenn das **Shutdown** -Ereignis eintritt. Wenn Sie Steuerelemente vor dem Schließen der Anwendung entfernen möchten, können Sie Ihren Code einem anderen Ereignishandler hinzufügen, z. B. **BeforeClose** oder **BeforeSave**.

### <a name="event-handler-method-declarations"></a>Methoden Deklarationen der Ereignis Handlers
 An jede Ereignishandler-Methodendeklaration werden die gleichen Argumente übergeben: *sender* und *e*. In Excel bezieht sich das *sender* -Argument auf das Arbeitsblatt, z. B. `Sheet1` oder `Sheet2`. In Word bezieht sich das *sender* -Argument auf das Dokument. Das *e* -Argument bezieht sich auf die Standardargumente für ein Ereignis, die in diesem Fall nicht verwendet werden.

 Im folgenden Codebeispiel werden die Standardereignishandler in Projekten auf Dokumentebene für Word veranschaulicht.

 [!code-vb[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#121)]
 [!code-csharp[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#121)]

 Im folgenden Codebeispiel werden die Standardereignishandler in Projekten auf Dokumentebene für Excel veranschaulicht.

> [!NOTE]
> Im folgenden Codebeispiel werden die Ereignishandler in der `Sheet1` -Klasse veranschaulicht. Die Namen der Ereignishandler in anderen Hostelementklassen entsprechen dem Klassennamen. In der `Sheet2` -Klasse hat der **Startup** -Ereignishandler beispielsweise den Namen `Sheet2_Startup`. In der `ThisWorkbook` -Klasse hat der **Startup** -Ereignishandler beispielsweise den Namen `ThisWorkbook_Startup`.

 [!code-csharp[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#83)]

### <a name="order-of-events-in-document-level-excel-projects"></a>Reihenfolge der Ereignisse in Excel-Projekten auf Dokument Ebene
 Die **Startup** -Ereignishandler in Excel-Projekten werden in dieser Reihenfolge aufgerufen:

1. `ThisWorkbook_Startup`.

2. `Sheet1_Startup`.

3. `Sheet2_Startup`.

4. `Sheet3_Startup`.

5. Andere Blätter laut Reihenfolge.

   Die **Shutdown** -Ereignishandler in einer Arbeitsmappen-Projektmappe werden in dieser Reihenfolge aufgerufen:

6. `ThisWorkbook_Shutdown`.

7. `Sheet1_Shutdown`.

8. `Sheet2_Shutdown`.

9. `Sheet3_Shutdown`.

10. Andere Blätter laut Reihenfolge.

    Die Reihenfolge wird festgelegt, wenn das Projekt kompiliert wird. Wenn der Benutzer die Blätter zur Laufzeit anders anordnet, ändert sich dadurch nicht die Reihenfolge, in der die Ereignisse beim nächsten Öffnen oder Schließen der Arbeitsmappe ausgelöst werden.

## <a name="vsto-add-in-projects"></a>VSTO-Add-In-Projekte
 Visual Studio stellt generierten Code in VSTO-Add-Ins bereit. Mit diesem Code werden zwei unterschiedliche Ereignisse ausgelöst: <xref:Microsoft.Office.Tools.AddInBase.Startup> und <xref:Microsoft.Office.Tools.AddInBase.Shutdown> .

### <a name="startup-event"></a>Startup-Ereignis
 Das <xref:Microsoft.Office.Tools.AddIn.Startup> -Ereignis wird ausgelöst, nachdem das VSTO-Add-In geladen und der gesamte Initialisierungscode in der Assembly ausgeführt wurde. Dieses Ereignis wird mit der `ThisAddIn_Startup` -Methode in der generierten Codedatei behandelt.

 Code im `ThisAddIn_Startup` -Ereignishandler ist der erste Benutzercode, der ausgeführt wird, es sei denn, Ihr VSTO-Add-In setzt die <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> -Methode außer Kraft. In diesem Fall wird der `ThisAddIn_Startup` -Ereignishandler nach <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>aufgerufen.

 Fügen Sie im-Ereignishandler keinen Code hinzu `ThisAdd-In_Startup` , wenn der Code erfordert, dass ein Dokument geöffnet ist. Fügen Sie stattdessen diesen Code einem Ereignis hinzu, welches durch die Office-Anwendung ausgelöst wird, wenn vom Benutzer ein Dokument erstellt oder geöffnet wird. Weitere Informationen finden Sie unter [zugreifen auf ein Dokument beim Starten der Office-Anwendung](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 Weitere Informationen zur Startsequenz von VSTO-Add-Ins finden Sie unter [Architektur von VSTO-Add-ins](../vsto/architecture-of-vsto-add-ins.md).

### <a name="shutdown-event"></a>Shutdown-Ereignis
 Das <xref:Microsoft.Office.Tools.AddInBase.Shutdown> -Ereignis wird ausgelöst, wenn die Anwendungsdomäne, in der Ihr Code geladen wird, entladen werden soll. Dieses Ereignis wird mit der `ThisAddIn_Shutdown` -Methode in der generierten Codedatei behandelt. Dieser Ereignishandler ist der letzte Benutzercode, der beim Entladen des VSTO-Add-Ins ausgeführt wird.

#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Shutdown-Ereignis in Outlook-VSTO-Add-ins
 Das <xref:Microsoft.Office.Tools.AddInBase.Shutdown> -Ereignis wird nur ausgelöst, wenn der Benutzer das VSTO-Add-In in Outlook über das Dialogfeld "COM-Add-Ins" deaktiviert. Es wird nicht ausgelöst, wenn Outlook beendet wird. Wenn Sie über Code verfügen, der beim Beenden von Outlook ausgeführt werden muss, sollten Sie eines der folgenden Ereignisse behandeln:

- Das <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> -Ereignis des <xref:Microsoft.Office.Interop.Outlook.Application> -Objekts.

- Das <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> -Ereignis des <xref:Microsoft.Office.Interop.Outlook.Explorer> -Objekts.

> [!NOTE]
> Sie können für Outlook erzwingen, dass das <xref:Microsoft.Office.Tools.AddInBase.Shutdown> -Ereignis beim Beenden ausgelöst wird, indem Sie dies in der Registrierung ändern. Aber wenn ein Administrator diese Einstellung zurücksetzt, wird der Code, den Sie der `ThisAddIn_Shutdown` -Methode hinzufügen, beim Beenden von Outlook nicht mehr ausgeführt. Weitere Informationen finden Sie unter [Shutdown-Änderungen für Outlook 2010](/previous-versions/office/developer/office-2010/ee720183(v=office.14)).

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln von Office-Lösungen](../vsto/developing-office-solutions.md)
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program mieren von Anpassungen auf Dokument Ebene](../vsto/programming-document-level-customizations.md)
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)
