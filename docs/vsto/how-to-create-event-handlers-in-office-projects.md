---
title: 'Gewusst wie: Erstellen von Ereignis Handlern in Office-Projekten'
description: Erfahren Sie mehr über die verschiedenen Möglichkeiten, wie Sie Standard Ereignishandler für Steuerelemente in Visual Basic und c# erstellen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b2aed6102b6aed5938ecfab826363e62dcfac48a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889420"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Gewusst wie: Erstellen von Ereignis Handlern in Office-Projekten
  Es gibt mehrere Möglichkeiten zum Erstellen von Ereignis Handlern in Visual Basic und c#. In der Entwurfs Ansicht können Sie die Standard Ereignishandler für Steuerelemente erstellen, indem Sie auf das Steuerelement doppelklicken oder im Fenster "Ereignisse" im Fenster " **Eigenschaften** " Handler für ein beliebiges Ereignis im Steuerelement erstellen. Wenn Sie jedoch in der Code Ansicht sind, möchten Sie möglicherweise nicht zu Designansicht wechseln, um einen Ereignishandler zu erstellen.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-an-event-handler-in-visual-basic"></a>So erstellen Sie einen Ereignishandler in Visual Basic

1. Wählen Sie in der Dropdown Liste **Klassen Name** am oberen Rand des Code-Editors das Objekt aus, für das Sie einen Ereignishandler erstellen möchten.

    > [!NOTE]
    > Wenn Sie Ereignishandler für oder erstellen möchten `ThisDocument` `ThisWorkbook` , müssen Sie **(ThisDocument-Ereignisse)** oder **(ThisWorkbook-Ereignisse)** in der Dropdown Liste **Klassen Name** auswählen.

2. Wählen Sie in der Dropdown Liste **Methoden Name** am oberen Rand des Code-Editors das Ereignis aus.

     Visual Studio erstellt den Ereignishandler und verschiebt die Einfügemarke in den neu erstellten Ereignishandler. Wenn der Ereignishandler bereits vorhanden ist, wechselt die Einfügemarke in den vorhandenen Ereignishandler.

### <a name="to-create-an-event-handler-in-c"></a>So erstellen Sie einen Ereignishandler in C\#

1. Erstellen Sie den Ereignis Delegaten im **Startup** -Ereignis der-Klasse, indem Sie den qualifizierten Ereignis Namen, gefolgt von einem Leerzeichen, eingeben und **+=** anschließend ohne Leerzeichen eingeben. Beispiel:

     `this.<object name>.<event name> +=`

2. Drücken Sie am Ende der Codezeile zweimal die Tab-Taste.

     Visual Studio schließt die Codezeile automatisch ab, erstellt den Ereignishandler und verschiebt die Einfügemarke in den neu erstellten Ereignishandler.

## <a name="see-also"></a>Weitere Informationen
- [Schreiben von Code in Office-Lösungen](../vsto/writing-code-in-office-solutions.md)
- [Exemplarische Vorgehensweise: Program mieren gegen Ereignisse eines NamedRange-Steuer Elements](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Erstellen von Office-Lösungen](../vsto/building-office-solutions.md)
