---
title: Hinzufügen von Symbolen zu Menübefehlen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Befehlen Befehle hinzufügen, die in den Menüs und Symbolleisten in der integrierten Entwicklungsumgebung (IDE) von Visual Studio angezeigt werden können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eaf0a089c10c850c14b9ba2f807a69eada5d04b9
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597651"
---
# <a name="add-icons-to-menu-commands"></a>Hinzufügen von Symbolen zu Menübefehlen
Befehle können in Menüs und Symbolleisten angezeigt werden. Auf Symbolleisten ist es üblich, dass ein Befehl nur mit einem Symbol angezeigt wird (um Platz zu sparen). in Menüs wird ein Befehl in der Regel mit einem Symbol und einem Text angezeigt.

 Symbole sind 16 Pixel breit und 16 Pixel hoch und können entweder eine 8-Bit-Farbtiefe (256 Farben) oder eine 32-Bit-Farbtiefe (echte Farbe) sein. 32-Bit-Farbsymbole werden bevorzugt. Symbole werden in der Regel in einer einzelnen horizontalen Zeile in einer einzelnen Bitmap angeordnet, obwohl mehrere Bitmaps zulässig sind. Diese Bitmap wird in der *vsct* -Datei zusammen mit den einzelnen Symbolen, die in der Bitmap verfügbar sind, deklariert. Weitere Informationen finden Sie in der Referenz für das [Bitmaps-Element](../extensibility/bitmaps-element.md) .

## <a name="add-an-icon-to-a-command"></a>Hinzufügen eines Symbols zu einem Befehl
 Bei der folgenden Prozedur wird davon ausgegangen, dass Sie über ein vorhandenes VSPackage-Projekt mit einem Menübefehl verfügen. Weitere Informationen hierzu finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

1. Erstellen Sie eine Bitmap mit einer Farbtiefe von 32 Bits. Ein Symbol ist immer 16 x 16, sodass diese Bitmap 16 Pixel hoch und ein Vielfaches von 16 Pixel breit sein muss.

     Jedes Symbol wird in einer einzelnen Zeile in der Bitmap nebeneinander platziert. Verwenden Sie den Alphakanal, um Transparenz Orte in jedem Symbol anzugeben.

     Wenn Sie eine 8-Bit-Farbtiefe verwenden, verwenden Sie Magenta, `RGB(255,0,255)` , als Transparenz. Es werden jedoch 32-Bit-Farbsymbole bevorzugt.

2. Kopieren Sie die Symbol Datei in das Verzeichnis *Ressourcen* in Ihrem VSPackage-Projekt. Fügen Sie dem Projekt im **Projektmappen-Explorer** das Symbol hinzu. (Wählen Sie **Ressourcen** aus, und klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Vorhandenes Element**, und wählen Sie die Symbol Datei aus.)

3. Öffnen Sie die *vsct* -Datei im Editor.

4. Fügen Sie ein- `GuidSymbol` Element mit dem Namen **testicon** hinzu. Erstellen Sie eine GUID **(Extras**  >  **Create GUID**, wählen Sie **Registrierungs Format** aus, und klicken Sie auf **Kopieren**), und fügen Sie Sie in das- `value` Attribut ein. Das Ergebnis sollte wie folgt aussehen:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Fügen Sie ein- `<IDSymbol>` Symbol für das Symbol hinzu. Das `name` -Attribut ist die ID des Symbols, und das-Attribut `value` gibt seine Position auf dem Strip an (sofern vorhanden). Wenn nur ein Symbol vorhanden ist, fügen Sie 1 hinzu. Das Ergebnis sollte wie folgt aussehen:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Erstellen `<Bitmap>` Sie ein im- `<Bitmaps>` Abschnitt der *vsct* -Datei, um die Bitmap darzustellen, die die Symbole enthält.

    - Legen `guid` Sie den Wert auf den Namen des Elements fest, das `<GuidSymbol>` Sie im vorherigen Schritt erstellt haben.

    - Legen `href` Sie den Wert auf den relativen Pfad der Bitmapdatei (in diesem Fall **Ressourcen \\<Symbol Dateiname \>** fest.

    - Legen `usedList` Sie den Wert auf das idsymbol fest, das Sie zuvor erstellt haben. Dieses Attribut gibt eine durch Trennzeichen getrennte Liste der im VSPackage zu verwendenden Symbole an. Symbole, die nicht in der Liste aufgeführt sind, sind die ausgeschlossene Formular

         Der Bitmap-Block sollte wie folgt aussehen:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. Legen Sie im vorhandenen- `<Button>` Element das `Icon` -Element auf die guidsymbol-und idsymbol-Werte fest, die Sie zuvor erstellt haben. Im folgenden finden Sie ein Beispiel für ein Button-Element mit den folgenden Werten:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Testen Sie das Symbol. Erstellen Sie das Projekt, und starten Sie das Debugging. Suchen Sie in der experimentellen Instanz den Befehl. Das Symbol sollte angezeigt werden, das Sie hinzugefügt haben.

## <a name="see-also"></a>Siehe auch
- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md)
- [Vsct-XML-Schema Referenz](../extensibility/vsct-xml-schema-reference.md)
