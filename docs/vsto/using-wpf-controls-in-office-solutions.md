---
title: Verwenden von WPF-Steuerelementen in Office-Lösungen
description: Erfahren Sie, wie Sie Windows Presentation Foundation (WPF)-Steuerelemente für das Entwerfen von Benutzeroberflächen in Visual Studio verwenden können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e041cda914cbf8aced4b19adfc80c601984c30e0
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526446"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Verwenden von WPF-Steuerelementen in Office-Lösungen

Mit den Office-Entwicklungstools in Visual Studio erstellte Projektmappen sind zwar für das direkte Arbeiten mit Windows Forms-Steuerelementen ausgelegt, Sie können jedoch auch WPF-Steuerelemente in den Projektmappen verwenden. Windows Presentation Foundation (WPF) bietet eine Alternative zu Windows Forms für das Entwerfen von Benutzeroberflächen. WPF bietet mithilfe einer Markupsprache namens XAML (Extensible Application Markup Language) neue Techniken zum Integrieren von Benutzeroberflächen, Medien und Dokumenten. Weitere Informationen finden Sie unter [Übersicht über WPF](/dotnet/framework/wpf/introduction-to-wpf).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Jedes Benutzeroberflächenelement, das Windows Forms-Steuerelemente in einer Office-Projektmappe hosten kann, kann auch WPF-Steuerelemente hosten. Dazu zählen folgende Elemente:

- Dokumente und Arbeitsblätter in Anpassungen auf Dokumentebene

- Aktionsbereiche in Anpassungen auf Dokumentebene

- Benutzerdefinierte Aufgabenbereiche in VSTO-Add-Ins.

- Formularbereiche in VSTO-Add-Ins für Outlook.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Hinzufügen von WPF-Steuerelementen zu Office-Projekten zur Entwurfszeit

Sie können Benutzeroberflächenelementen in Office-Projektmappen WPF-Steuerelemente nicht direkt hinzufügen. Fügen Sie dem Projekt stattdessen ein **Benutzer Steuerelement (WPF)** -Element hinzu, und verwenden Sie es als Entwurfs Oberfläche für WPF-Steuerelemente. Fügen Sie dann das WPF-Benutzersteuerelement einem Benutzeroberflächenelement im Projekt hinzu.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>So fügen Sie einem Aktionsbereich, einem benutzerdefinierten Aufgabenbereich oder einem Formularbereich WPF-Steuerelemente hinzu

1. Öffnen Sie ein Projekt, dem Sie einen benutzerdefinierten Aufgabenbereich, einen Aktionsbereich oder einen Formularbereich hinzufügen möchten.

2. Fügen Sie dem Projekt ein **Benutzer Steuerelement (WPF)** -Element hinzu.

3. Fügen Sie der Entwurfs Oberfläche der WPF-Benutzer Steuerelemente aus der **Toolbox** WPF-Steuerelemente hinzu.

     Wenn der WPF-Benutzer Steuerelement-Designer geöffnet ist, enthält die **Toolbox** standardmäßig nur WPF-Steuerelemente.

4. Erstellen Sie das Projekt.

5. Fügen Sie dem Projekt einen Aktionsbereich, einen Formularbereich oder einen benutzerdefinierten Aufgabenbereich hinzu:

    - Fügen Sie für Formular Bereiche dem Projekt ein **Outlook-Formular Bereichs** Element hinzu. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Formular Bereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

    - Fügen Sie dem Projekt für Aktionsbereiche ein Aktionsbereich- **Steuer** Element oder ein **Benutzer Steuer** Element hinzu. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeits](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)Mappen.

    - Fügen Sie für benutzerdefinierte Aufgabenbereiche dem Projekt ein **Benutzer Steuer** Element-Element hinzu. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

6. Ziehen Sie aus der Registerkarte *ProjectName* **WPF-Benutzer Steuerelemente** der **Toolbox** das WPF-Benutzer Steuerelement in den Designer für den Aktionsbereich, den Formular Bereich oder den benutzerdefinierten Aufgabenbereich.

     Visual Studio erstellt automatisch ein <xref:System.Windows.Forms.Integration.ElementHost>-Objekt, das das WPF-Benutzersteuerelement im Benutzeroberflächenelement hostet.

7. Erstellen Sie das Projekt neu.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>So fügen Sie einem Dokument oder einem Arbeitsblatt in einem Projekt auf Dokumentebene WPF-Steuerelemente hinzu

1. Öffnen Sie ein Projekt auf Dokumentebene für Word oder Excel.

2. Fügen Sie dem Projekt ein **Benutzer Steuerelement (WPF)** -Element hinzu.

3. Fügen Sie der Entwurfs Oberfläche der WPF-Benutzer Steuerelemente aus der **Toolbox** WPF-Steuerelemente hinzu.

4. Erstellen Sie das Projekt.

5. Fügen Sie dem Projekt ein **Benutzer Steuer** Element (d. h. ein Windows Forms Benutzer Steuerelement) hinzu.

6. Öffnen Sie den Designer für das Windows Forms-Benutzersteuerelement.

7. Ziehen Sie das WPF-Benutzer Steuerelement auf der Registerkarte *ProjectName* **WPF-Benutzer Steuerelemente** der **Toolbox** auf den Designer.

     Visual Studio erstellt automatisch ein <xref:System.Windows.Forms.Integration.ElementHost>-Objekt, das das WPF-Benutzersteuerelement im Windows Forms-Benutzersteuerelement hostet.

8. Schreiben Sie Code, der dem Dokument bzw. der Arbeitsmappe das Windows Forms-Benutzersteuerelement programmgesteuert hinzufügt. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

    > [!NOTE]
    > Sie können das Windows Forms-Benutzersteuerelement im Designer nicht auf das Dokument bzw. das Arbeitsblatt ziehen.

9. Erstellen Sie das Projekt neu.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>Hosten von WPF-Steuerelementen mithilfe der elemterthost-Klasse

Visual Studio bietet Funktionen, die Sie beim Verwenden von Windows Forms-Steuerelementen in Office-Projektmappen unterstützen, aber es fehlen vergleichbare Funktionen für WPF-Steuerelemente. Beispielsweise können Sie Dokumenten und Arbeitsblättern Windows Forms Steuerelemente zur Entwurfszeit hinzufügen, indem Sie Steuerelemente aus der **Toolbox** ziehen, oder zur Laufzeit mithilfe von Hilfsmethoden. Diese Tools sind jedoch für WPF-Steuerelemente nicht verfügbar.

WPF-Steuerelemente verwenden die <xref:System.Windows.Forms.Integration.ElementHost>-Klasse als Integrationsebene zwischen einem Windows Forms-Steuerelement bzw. -Formular und den WPF-Steuerelementen. Wenn Sie der Projektmappe zur Entwurfszeit WPF-Steuerelemente hinzufügen, generiert Visual Studio automatisch ein <xref:System.Windows.Forms.Integration.ElementHost>-Objekt.

## <a name="wpf-resources"></a>WPF-Ressourcen

Weitere Informationen zu Fragen über Architektur und Entwurf beim Hosten von WPF-Steuerelementen in Windows Forms-Steuerelementen und -Formularen finden Sie in den folgenden Themen:

- [Windows Forms-und WPF-Interoperabilitäts Eingabe Architektur](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

- [Windows Forms-und WPF-Eigenschaften Zuordnung](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

- [WPF-und Windows Forms Interoperation](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

- [Windows Forms-Steuerelemente und entsprechende WPF-Steuerelemente](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Weitere Informationen über das Hinzufügen von WPF-Steuerelementen zu Windows Forms-Steuerelementen und -Formularen in Visual Studio zur Entwurfszeit finden Sie in den folgenden Themen:

- [Exemplarische Vorgehensweise: Erstellen eines neuen WPF-Inhalts auf Windows Forms zur Entwurfszeit](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

- [Exemplarische Vorgehensweise: Anordnen von WPF-Inhalt auf Windows Forms zur Entwurfszeit](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

- [Exemplarische Vorgehensweise: Formatieren von WPF-Inhalten](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>Weitere Informationen

- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
- [Übersicht über Windows Forms Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)
- [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)
- [Erstellen von Outlook-Formular Bereichen](../vsto/creating-outlook-form-regions.md)
- [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Gewusst wie: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Gewusst wie: Hinzufügen eines Formular Bereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
