---
title: Barrierefreiheit in Office-Projekten
description: Erfahren Sie, wie Microsoft Office Projekte viele Barrierefreiheits Features enthalten, die es Ihnen ermöglichen, benutzerdefinierte Lösungen zu erstellen, die die Anforderungen an die Standard
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4021517aa296f3c1e6355b82260b00590181f4cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955150"
---
# <a name="accessibility-in-office-projects"></a>Barrierefreiheit in Office-Projekten

Microsoft Visual Studio und Microsoft Office enthalten viele Barrierefreiheits Features, die es Ihnen ermöglichen, benutzerdefinierte Lösungen zu erstellen, die die Standardanforderungen für Barrierefreiheit erfüllen. Microsoft veröffentlicht Richtlinien für Barrierefreiheit im Web. Weitere Informationen finden Sie auf der [Website zur Barrierefreiheit](https://www.microsoft.com/accessibility/).

In den meisten Fällen erfüllen Office-Projekte in Visual Studio Barrierefreiheits Standards oder machen Eigenschaften verfügbar, die Sie festlegen können, um Ihre Lösungen zugänglich zu machen. Allerdings gibt es einige Features mit eingeschränkter Barrierefreiheit.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>Barrierefreiheit zur Entwurfszeit

### <a name="use-shortcut-keys-in-document-level-projects"></a>Verwenden von Tastenkombinationen in Projekten auf Dokument Ebene
 Wenn ein Microsoft Office Word-Dokument oder eine Microsoft Office Excel-Arbeitsmappe in Visual Studio geöffnet ist, empfängt jeweils nur eine Anwendung die Tastenkombinationen. Standardmäßig empfängt Visual Studio alle Tastenkombinationen, Sie können Sie jedoch in Word oder Excel empfangen, wenn das Dokument den Fokus besitzt, indem Sie auf der Seite **Tastatur Einstellungen** des Dialog Felds **Optionen die Option** **dynamisches Tastatur Schema** auswählen. Weitere Informationen finden Sie unter [Microsoft Office Word-Tastatur, Microsoft Office Tastatur Einstellungen, Dialogfeld "Optionen](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) " und [Microsoft Office Excel-Tastatur, Microsoft Office Tastatur Einstellungen, Dialogfeld "Optionen](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)".

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Anzeigen von Tastenkombinationen für das Menüband in Projekten auf Dokument Ebene
 Wenn ein Word-Dokument oder eine Excel-Arbeitsmappe in Visual Studio geöffnet ist, können Sie die **alt** -Taste nicht drücken, um die Tastenkombinationen für die Registerkarten und Steuerelemente auf dem Menüband anzuzeigen. Um die Tastenkombinationen anzuzeigen, während das Dokument oder die Arbeitsmappe im Designer geöffnet ist, führen Sie die folgenden Schritte aus.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>So zeigen Sie Tastenkombinationen für Registerkarten und Steuerelemente des Menübands im Designer an

1. Klicken Sie in Visual Studio im **Menü Extras** auf **Optionen**.

2. Erweitern Sie den Knoten " **Office-Tools** ", und wählen Sie nach Bedarf **Microsoft Office Excel-Tastatur** oder **Microsoft Office Wort Tastatur** aus.

3. Wählen Sie **dynamisches Tastatur Schema** aus.

     Es wird eine Meldung angezeigt, die besagt, dass Sie Visual Studio neu starten müssen, damit die Änderung wirksam wird.

4. Klicken Sie auf **OK**.

5. Starten Sie Visual Studio neu, und öffnen Sie das Projekt erneut.

6. Öffnen Sie das Dokument oder den arbeitsmappendesigner für Ihr Projekt.

7. Drücken Sie **F6** , um die Tastenkombinationen für das Menüband anzuzeigen.

## <a name="accessibility-at-run-time"></a>Barrierefreiheit zur Laufzeit

### <a name="windows-forms-controls-on-office-documents"></a>Windows Forms Steuerelemente in Office-Dokumenten
 Windows Forms Steuerelemente machen Barrierefreiheits Eigenschaften verfügbar, die Informationen über das Steuerelement für Barrierefreiheits Hilfen bereitstellen, z. b. Sprachausgabe Sie können diese Barrierefreiheits Eigenschaften nutzen, wenn die Steuerelemente in einem Office-Dokument in einer Anpassung auf Dokument Ebene vorliegen. Weitere Informationen finden Sie unter [Bereitstellen von Barrierefreiheits Informationen für Steuerelemente in einem Windows Form](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).

 Zur Laufzeit gibt es jedoch einige Einschränkungen für die Barrierefreiheit, wenn Windows Forms-Steuerelemente in einer Excel-Arbeitsmappe oder einem Word-Dokument gehostet werden:

- Sie können nicht von einem Steuerelement zu einem anderen Tabulator.

- Steuerelemente in einem Dokument werden deaktiviert, wenn Sie die Zoomeinstellung des Dokuments in einen anderen Wert als 100% ändern.

  Informationen zu Einschränkungen bei Windows Forms Steuerelementen in Dokumenten finden Sie unter [Einschränkungen von Windows Forms Steuerelementen in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

### <a name="actions-panes-and-custom-task-panes"></a>Aktionsbereiche und benutzerdefinierte Aufgabenbereiche
 Wenn ein Aktionsbereich oder ein benutzerdefinierter Aufgabenbereich den Fokus besitzt, können Sie auf die Steuerelemente auf die gleiche Weise zugreifen wie auf Steuerelemente in einer Windows Forms Anwendung. Wenn Sie den Cursor zwischen dem Aktionsbereich und dem Dokument verschieben möchten, können Sie **F6** drücken.

 Weitere Informationen zu Aktionsbereichen und benutzerdefinierten Aufgabenbereichen finden Sie unter Übersicht über den [Aktions](../vsto/actions-pane-overview.md) Bereich und [benutzerdefinierte Aufgaben](../vsto/custom-task-panes.md)Bereiche.

### <a name="display-modes"></a>Anzeigemodi

Visual Studio weist die folgenden Einschränkungen im Zusammenhang mit den Anzeigemodi auf:

- Steuerelemente in einem Word-Dokument oder Excel-Arbeitsblatt werden deaktiviert, wenn Sie die Zoomeinstellung des Dokuments in etwas anderes als 100% ändern.

- Im Dialogfeld **Neues Projekt** werden Steuerelemente nicht ordnungsgemäß angezeigt, wenn ein Benutzer die Barrierefreiheits Optionen des Computers zur **Verwendung von hoher Kontrast** ändert.

Sie können die Bildschirmlupe verwenden, um diese Einschränkungen zu überwinden. Die Bildschirmlupe ist ein Anzeige Dienstprogramm in Windows, das ein separates Fenster erstellt, in dem ein vergrößerter Teil des Bildschirms angezeigt wird.

## <a name="see-also"></a>Weitere Informationen

- [Entwickeln von Office-Lösungen](../vsto/developing-office-solutions.md)
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Barrierefreiheit für Personen mit Behinderungen](../ide/reference/accessibility-features-of-visual-studio.md)
- [Barrierefreiheits Funktionen in Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)