---
title: Zugreifen auf das Menüband zur Laufzeit
description: Sie können Code zum Einblenden, Ausblenden und Ändern des Menübands schreiben und Benutzern das Ausführen des Codes von Steuerelementen in einem benutzerdefinierten Aufgabenbereich, Aktionsbereich oder Outlook-Formularbereich ermöglichen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d8facf847e484824b636324d1f84427a08172035
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847597"
---
# <a name="access-the-ribbon-at-run-time"></a>Zugreifen auf das Menüband zur Laufzeit
  Sie können Code zum Einblenden, Ausblenden und Ändern des Menübands schreiben und Benutzern das Ausführen des Codes von Steuerelementen in einem benutzerdefinierten Aufgabenbereich, Aktionsbereich oder Outlook-Formularbereich ermöglichen.

 Sie können mit der `Globals`-Klasse auf das Menüband zugreifen. Bei Outlook-Projekten können Sie auf die Menübänder zugreifen, die in einem bestimmten Outlook-Inspektor- oder Outlook-Explorer-Fenster angezeigt werden.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Zugreifen auf das Menüband mithilfe der Globals-Klasse
 Sie können die `Globals`-Klasse verwenden, um von einer beliebigen Stelle im Projekt auf das Menüband in einem Projekt auf Dokumentebene oder in einem VSTO-Add-In-Projekt zuzugreifen.

 Weitere Informationen zur- `Globals` Klasse finden Sie unter [globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).

 Im folgenden Beispiel wird die`Globals`-Klasse für den Zugriff auf ein benutzerdefiniertes Menüband mit der Bezeichnung `Ribbon1` und zum Festlegen des Texts verwendet, der in einem Kombinationsfeld im Menüband für `Hello World` angezeigt wird.

 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Zugreifen auf eine Auflistung von Menü Bändern, die in einem bestimmten Outlook-Inspektor-Fenster angezeigt werden
 Sie können auf eine Auflistung von Menü Bändern zugreifen, die in Outlook- *Inspektoren* angezeigt werden. Ein Inspektor ist ein Fenster, das in Outlook geöffnet wird, wenn Benutzer bestimmte Aufgaben ausführen, z. B. E-Mails verfassen. Um auf das Menüband eines Inspektor-Fensters zuzugreifen, rufen Sie die `Ribbons`-Eigenschaft der `Globals`-Klasse auf und übergeben ein <xref:Microsoft.Office.Interop.Outlook.Inspector>-Objekt, das den Inspektor darstellt.

 Im folgenden Beispiel wird die Menübandauflistung des Inspektors abgerufen, der gerade den Fokus besitzt. In diesem Beispiel wird dann auf ein Menüband mit der Bezeichnung `Ribbon1` zugegriffen und der Text festgelegt, der in einem Kombinationsfeld im Menüband für `Hello World` angezeigt wird.

 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Zugreifen auf eine Auflistung von Menü Bändern, die für einen bestimmten Outlook-Explorer angezeigt werden
 Sie können auf eine Auflistung von Menü Bändern zugreifen, die in einem Outlook- *Explorer* angezeigt werden. Ein Explorer ist die Haupt-Benutzeroberfläche (UI) der Anwendung für eine Instanz von Outlook. Um auf das Menüband eines Explorer-Fensters zuzugreifen, rufen Sie die `Ribbons`-Eigenschaft der `Globals`-Klasse auf und übergeben ein <xref:Microsoft.Office.Interop.Outlook.Explorer>-Objekt, das den Explorer darstellt.

 Im folgenden Beispiel wird die Menübandauflistung des Explorers abgerufen, der gerade den Fokus besitzt. In diesem Beispiel wird dann auf ein Menüband mit der Bezeichnung `Ribbon1` zugegriffen und der Text festgelegt, der in einem Kombinationsfeld im Menüband für `Hello World` angezeigt wird.

 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]

## <a name="see-also"></a>Siehe auch
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Übersicht über das Ribbon-Objektmodell](../vsto/ribbon-object-model-overview.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente auf einem Menüband zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Zugreifen auf einen Formular Bereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)
