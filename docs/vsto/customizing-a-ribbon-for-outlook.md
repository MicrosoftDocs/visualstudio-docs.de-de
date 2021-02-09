---
title: Anpassen eines Menübands für Outlook
description: Wenn Sie das Menüband in Microsoft Office Outlook anpassen, müssen Sie in Erwägung ziehen, wo das benutzerdefinierte Menüband in der Anwendung angezeigt wird.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c12e92ef77130ca2d9b55ccec737f37c73396c2b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99849878"
---
# <a name="customize-a-ribbon-for-outlook"></a>Anpassen eines Menübands für Outlook
  Beim Anpassen des Menübands in Microsoft Office Outlook müssen Sie berücksichtigen, wo das benutzerdefinierte Menüband in der Anwendung angezeigt wird. Outlook zeigt das Menüband in der Benutzeroberfläche der Hauptanwendung und in Fenstern an, die geöffnet werden, wenn Benutzer bestimmte Aufgaben ausführen, z. B. eine E-Mail erstellen. Diese Anwendungsfenster werden als Inspektoren bezeichnet.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Hinzufügen eines benutzerdefinierten Menübands zur Hauptbenutzer Oberfläche der Anwendung
 Die Benutzeroberfläche der Hauptanwendung in Outlook ist der Explorer. Wenn Sie das Element " **Menüband (visueller Designer)** " verwenden, können Sie dem Explorer eine Multifunktionsleiste hinzufügen, indem Sie im **Eigenschaften** Fenster auf die **RibbonType** -Eigenschaft des Menübands klicken und dann " **Microsoft. Outlook. Explorer**" auswählen.

## <a name="assign-a-ribbon-to-an-inspector"></a>Zuweisen eines Menübands zu einem Inspektor
 Sie identifizieren den anzupassenden Inspektor durch Angabe des Menübandtyps, der der Nachrichtenklasse des Inspektors entspricht.

 Wenn Sie das Element **Menüband (visueller Designer)** verwenden, klicken Sie auf die **RibbonType** -Eigenschaft des Menübands im Fenster **Eigenschaften** , und wählen Sie dann eine oder mehrere Menüband-IDs aus der Liste der Werte aus.

 Sie können einem Projekt mehrere Menübänder hinzufügen. Wenn sich mehrere Menübänder eine Menüband-ID teilen, überschreiben Sie die `CreateRibbonExtensibilityObject`-Methode in der `ThisAddin`-Klasse des Projekts, um anzugeben, welches Menüband zur Laufzeit angezeigt werden soll. Weitere Informationen finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md). Weitere Informationen zu den einzelnen Menü Band Typen finden Sie im technischen Artikel [Anpassen des Menübands in Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Angeben des Menü Band Typs mithilfe von Menüband-XML
 Wenn Sie das Element **Menüband (XML)** verwenden, überprüfen Sie den Wert des *ribbonID* -Parameters in der <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> -Methode, und geben Sie das entsprechende Menüband zurück.

 Die <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>-Methode wird automatisch von Visual Studio in der Menüband-Codedatei generiert. Der *ribbonID* -Parameter ist eine Zeichenfolge, die den Explorer oder einen bestimmten Inspektortyp identifiziert. Eine umfassende Liste der möglichen Werte für den *ribbonID* -Parameter finden Sie im technischen Artikel [Anpassen des Menübands in Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).

 Im folgenden Codebeispiel wird veranschaulicht, wie ein benutzerdefiniertes Menüband nur im `Microsoft.Outlook.Mail.Compose`-Inspektor angezeigt wird. Dies ist der Inspektor, der geöffnet wird, wenn ein Benutzer eine neue E-Mail erstellt. Das anzuzeigende Menüband wird in der- `GetResourceText()` Methode angegeben, die in der **Ribbon** -Klasse generiert wird. Weitere Informationen zur Menü **Band** Klasse finden Sie unter [Menüband-XML](../vsto/ribbon-xml.md).

 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]

## <a name="see-also"></a>Weitere Informationen
- [Zugreifen auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Menüband-Designer](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
