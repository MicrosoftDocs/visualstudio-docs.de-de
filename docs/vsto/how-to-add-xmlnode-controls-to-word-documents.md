---
title: 'Gewusst wie: Hinzufügen von XMLNode-Steuerelementen zu Word-Dokumenten'
description: Wenn Sie einem Microsoft Office Word-Dokument ein nicht wiederholtes XML-Schema Element zuordnen, fügt Visual Studio dem Dokument automatisch ein XMLNode-Steuerelement hinzu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8b9deb6732552a827cb89465f6521bc566e8c46f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846739"
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Gewusst wie: Hinzufügen von XMLNode-Steuerelementen zu Word-Dokumenten
  **Wichtig** Die Informationen, die in diesem Thema in Bezug auf Microsoft Word beschrieben werden, werden exklusiv für den Vorteil und die Verwendung von Einzelpersonen und Organisationen präsentiert, die sich außerhalb der USA und ihrer Gebiete befinden oder Programme verwenden, die unter, Microsoft Word-Produkte, die von Microsoft vor Januar 2010 lizenziert wurden Diese Informationen zu Microsoft Word werden möglicherweise nicht von Einzelpersonen oder Organisationen in den USA oder deren Territorien gelesen oder verwendet, die von Microsoft Word-Produkten verwendet werden, die nach dem 10. Januar 2010 von Microsoft lizenziert wurden. Diese Produkte Verhalten sich nicht identisch mit Produkten, die vor diesem Datum lizenziert sind, oder für die Verwendung außerhalb der USA lizenziert und lizenziert wurden.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Wenn Sie einem Microsoft Office Word-Dokument ein nicht wiederholtes XML-Schema Element zuordnen, fügt Visual Studio dem Dokument automatisch ein-Steuerelement hinzu <xref:Microsoft.Office.Tools.Word.XMLNode> . Weitere Informationen zum Mapping wiederholter XML-Schema Elemente finden Sie unter Gewusst [wie: Hinzufügen von XMLNodes](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)-Steuerelementen zu Word-Dokumenten.

> [!NOTE]
> Das <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement ist nicht in der **Toolbox** oder im **Datenquellen** Fenster verfügbar und kann nicht Programm gesteuert erstellt werden.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnode-control-to-a-document"></a>So fügen Sie einem Dokument ein XMLNode-Steuerelement hinzu

1. Klicken Sie im Dokument im Visual Studio-Designer auf dem Menüband auf die Registerkarte **Entwickler** .

    > [!NOTE]
    > Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter Gewusst [wie: Anzeigen der Registerkarte "Entwickler" im Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

2. Klicken Sie in der Gruppe **XML** auf **Schema**.

     Das Dialogfeld **Vorlagen und Add-ins** wird geöffnet.

3. Klicken Sie auf die Registerkarte **XML-Schema** .

4. Klicken Sie auf **Schema hinzufügen**.

     Das Dialogfeld **Schema hinzufügen** wird geöffnet.

5. Wählen Sie im Dialogfeld **Schema hinzufügen** ein XML-Schema aus, das sich nicht wiederholende Schema Elemente enthält, und klicken Sie auf **Öffnen**.

     Das Dialogfeld **Schema Einstellungen** wird angezeigt.

6. Weisen Sie einen Alias zu, oder klicken Sie auf **OK** , um das Schema ohne Alias hinzuzufügen.

     Das Schema wird dem Dialogfeld **Schema hinzufügen** hinzugefügt.

7. Klicken Sie im Dialogfeld **Schema hinzufügen** auf **OK**.

8. Der Aufgabenbereich **XML-Struktur** wird geöffnet.

9. Klicken Sie im Aufgabenbereich der **XML-Struktur** auf das nicht wiederholende Schema Element, um es dem Dokument hinzuzufügen.

     Ein <xref:Microsoft.Office.Tools.Word.XMLNode> -Steuerelement wird erstellt und dem Projekt hinzugefügt.

## <a name="see-also"></a>Siehe auch
- [XMLNode-Steuerelement](../vsto/xmlnode-control.md)
- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
