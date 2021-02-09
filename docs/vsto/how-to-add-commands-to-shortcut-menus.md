---
title: 'Gewusst wie: Hinzufügen von Befehlen zu Kontextmenüs'
description: Erfahren Sie, wie Sie mithilfe eines VSTO-Add-ins einem Kontextmenü in einer Office-Anwendung Befehle hinzufügen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2f5c244d78ab5a6b5d98550b11c280159f285db7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913456"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Gewusst wie: Hinzufügen von Befehlen zu Kontextmenüs
  In diesem Thema wird veranschaulicht, wie Sie mithilfe eines VSTO-Add-ins einem Kontextmenü in einer Office-Anwendung Befehle hinzufügen.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

### <a name="to-add-commands-to-shortcut-menus-in-office"></a>So fügen Sie in Office einem Kontextmenü Befehle hinzu

1. Fügen Sie ein **Menüband-XML** -Element einem Projekt auf Dokumentebene oder einem VSTO-Add-In-Projekt hinzu. Weitere Informationen finden Sie unter Gewusst [wie: Starten der Anpassung des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md). In

2. **Projektmappen-Explorer** wählen Sie **ThisAddIn.cs** oder **ThisAddIn.vb** aus.

3. Wählen Sie in der Menüleiste **Ansicht** > **Code** aus.

     Die **ThisAddin** -Klassendatei wird im Code-Editor geöffnet.

4. Fügen Sie der Klasse **ThisAddin** den folgenden Code hinzu. Mit diesem Code wird die `CreateRibbonExtensibilityObject`-Methode überschrieben und der Office-Anwendung die Menüband-XML-Klasse zurückgegeben.

     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]

5. Wählen Sie die Menüband-XML-Datei im **Projektmappen-Explorer** aus. Standardmäßig wird die Menüband-XML-Datei *Ribbon1.xml* benannt.

6. Wählen Sie in der Menüleiste **Ansicht** > **Code** aus.

     Die Menüband-XML-Datei wird im Code-Editor geöffnet.

7. Fügen Sie im Code-Editor den XML-Code hinzu, der das Kontextmenü und das Steuerelement beschreibt, das Sie dem Kontextmenü hinzufügen möchten.

     Im folgenden Beispiel werden dem Kontextmenü für ein Word-Dokument ein Schaltflächen-, ein Menü- und ein Katalog-Steuerelement hinzugefügt. Die Steuerelement-ID dieses Kontextmenüs lautet „ContextMenuText“. Eine komplette Liste der Verknüpfungs Steuerelement-IDs von Office 2010 finden Sie unter [Office 2010-Hilfedateien:](https://www.microsoft.com/download/details.aspx?id=6627)Bezeichner von Office-Benutzeroberflächen-Steuerelementen.

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />
          <menu id="MySubMenu" label="My Submenu" >
            <button id="MyButton2" label="Button on submenu" />
          </menu>
          <gallery id="galleryOne" label="My Gallery">
            <item id="item1" imageMso="HappyFace" />
            <item id="item2" imageMso="HappyFace" />
            <item id="item3" imageMso="HappyFace" />
            <item id="item4" imageMso="HappyFace" />
          </gallery>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

8. Wählen Sie im **Projektmappen-Explorer** die Datei **MyRibbon.cs** oder **MyRibbon.vb** aus.

9. Fügen Sie der-Klasse eine Rückruf Methode `Ribbon1` für jedes Steuerelement hinzu, das Sie verarbeiten möchten.

     Die folgende Rückrufmethode verarbeitet die Schaltfläche **My Button** . In diesem Code wird dem aktiven Dokument an der aktuellen Position des Cursors eine Zeichenfolge hinzugefügt.

     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]

## <a name="see-also"></a>Weitere Informationen
- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
- [Exemplarische Vorgehensweise: Erstellen von Kontextmenüs für Lesezeichen](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
- [Anpassen von Kontextmenüs in Office 2010](/previous-versions/office/developer/office-2010/ee691832(v=office.14))
