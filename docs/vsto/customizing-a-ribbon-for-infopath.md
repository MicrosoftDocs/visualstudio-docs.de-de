---
title: Anpassen eines Menübands für InfoPath
description: Wenn Sie das Menüband in Microsoft Office InfoPath anpassen, müssen Sie in Erwägung ziehen, wo das benutzerdefinierte Menüband in der Anwendung angezeigt wird.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0bc66a9266baf865e2efb87497361bc0c525e55a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99849891"
---
# <a name="customize-a-ribbon-for-infopath"></a>Anpassen eines Menübands für InfoPath
  Beim Anpassen des Menübands in Microsoft Office InfoPath müssen Sie berücksichtigen, wo das benutzerdefinierte Menüband in der Anwendung angezeigt wird. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] kann das Menüband in den folgenden drei Typen von InfoPath-Anwendungsfenstern anzeigen:

- Fenster, in denen eine Formularvorlage angezeigt wird, die im Entwurfsmodus geöffnet ist.

- Fenster, in denen ein Formular angezeigt wird, das auf einer Formatvorlage basiert.

- Im Seitenansichtsfenster.

  **Betrifft:** Die Informationen in diesem Thema betreffen VSTO-Add-In-Projekte für InfoPath 2010. Weitere Informationen finden Sie unter [verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).

  Benutzer und Designer öffnen eine Formularvorlage im Entwurfsmodus, um die Darstellung und das Layout der Vorlage zu ändern. Benutzer öffnen Formulare, die auf einer Formularvorlage basieren, um Inhalte hinzuzufügen.

  Im Seitenansichtsfenster können Designer und Benutzer, die Seiten eines Formulars oder einer Formularvorlage vor dem Drucken in der Vorschau anzeigen.

> [!NOTE]
> Die Registerkarte **Add-Ins** wird im Seitenansichtsfenster nicht angezeigt. Wenn eine benutzerdefinierte Registerkarte im Seitenansichtsfenster angezeigt werden soll, stellen Sie sicher, dass die **OfficeId** -Eigenschaft der Registerkarte nicht auf **TabAddIns** festgelegt ist.

 Sie müssen den Menübandtyp jedes Fensters angeben, in denen das Menüband angezeigt werden soll.

## <a name="specify-the-ribbon-type-in-the-ribbon-designer"></a>Angeben des Menü Band Typs im Menüband-Designer
 Wenn Sie das Element **Menüband (visueller Designer)** verwenden, klicken Sie auf die **RibbonType** -Eigenschaft des Menübands im Fenster **Eigenschaften** , und wählen Sie dann eine der in der folgenden Tabelle beschriebenen Menüband-IDs aus.

|Menüband-ID|Fenster, in dem das Menüband angezeigt wird, wenn Sie das Projekt ausführen|
|---------------|---------------------------------------------------------------------|
|**Microsoft.InfoPath.Designer**|Fenster, in denen eine Formularvorlage angezeigt wird, die im Entwurfsmodus geöffnet ist.|
|**Microsoft.InfoPath.Editor**|Fenster, in denen ein Formular angezeigt wird, das auf einer Formatvorlage basiert.|
|**Microsoft.InfoPath.PrintPreview**|Im Seitenansichtsfenster.|

 Sie können einem Projekt mehrere Menübänder hinzufügen. Wenn sich mehrere Menübänder eine Menüband-ID teilen, überschreiben Sie die `CreateRibbonExtensibilityObject` -Methode in der `ThisAddin` -Klasse des Projekts, um anzugeben, welches Menüband zur Laufzeit ausgeführt werden soll. Weitere Informationen finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Angeben des Menü Band Typs mithilfe von Menüband-XML
 Bei Verwendung des Elements **Menüband (XML)** überprüfen Sie den Wert des *ribbonID* -Parameters in der <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> -Methode, und geben Sie das entsprechende Menüband zurück.

 Die <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> -Methode wird automatisch von Visual Studio in der Menüband-Codedatei generiert. Der *ribbonID* -Parameter ist eine Zeichenfolge, die den Typ des InfoPath-Fensters identifiziert, das geöffnet wird, angibt.

 Im folgenden Codebeispiel wird veranschaulicht, wie ein benutzerdefiniertes Menüband nur in einem Fenster angezeigt wird, in dem eine Formularvorlage im Entwurfsmodus angezeigt wird. Das anzuzeigende Menüband wird in der `GetResourceText()` -Methode angegeben, die in der Menübandklasse generiert wird. Weitere Informationen zur Menübandklasse finden Sie unter [Ribbon XML](../vsto/ribbon-xml.md).

 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]

## <a name="see-also"></a>Weitere Informationen
- [Zugreifen auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Menüband-Designer](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
