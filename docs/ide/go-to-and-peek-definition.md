---
title: Anzeigen von Typdefinitionen
description: Erfahren Sie mehr über die Features „Gehe zu Definition“ und „Definition einsehen“, mit denen Sie mühelos die Definition eines Typs oder Members anzeigen können.
ms.custom: SEO-VS-2020
ms.date: 01/10/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, view definition
- go to definition
- peek definition
- type definition [Visual Studio]
- member definition [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 804c49c079f619a774cb1f99d54b2b2af5a3929d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869361"
---
# <a name="view-type-and-member-definitions"></a>Anzeigen von Typ- und Memberdefinitionen

Entwickler müssen häufig die Quellcodedefinitionen für Typen oder Klassenmember anzeigen, die sie in ihrem Code verwenden. In Visual Studio können Sie die Definition eines Typs oder Members ganz einfach mithilfe der Features **Gehe zu Definition** und **Definition einsehen** anzeigen. Wenn der Quellcode nicht verfügbar ist, werden stattdessen Metadaten angezeigt.

## <a name="go-to-definition"></a>Gehe zu Definition

Das Feature **Gehe zu Definition** navigiert zur Quelle eines Typs oder Members und öffnet die Ergebnisse in einer neuen Registerkarte. Wenn Sie die Tastatur verwenden, platzieren Sie den Textcursor an einer beliebigen Stelle innerhalb des Symbols, und drücken Sie **F12**. Wenn Sie die Maus verwenden, klicken Sie entweder im Kontextmenü auf **Gehe zu Definition**, oder verwenden Sie die im folgenden Abschnitt beschriebene Funktionalität **STRG+Klick**.

### <a name="ctrl-click-go-to-definition"></a>„Gehe zu Definition“ mit STRG+Klick

Mit der Kombination **STRG**+**Klick** können Mausbenutzer schnell auf **Gehe zu Definition** zugreifen. Symbole werden anklickbar, wenn Sie **STRG** drücken und auf den Typ oder Member zeigen. Drücken Sie die Taste **STRG**, und klicken Sie auf ein Symbol, um schnell zu dessen Definition zu navigieren. So einfach ist das!

![Animation: „Gehe zu Definition“ per Mausklick](../ide/media/click_gotodef.gif)

Die Zusatztaste für **Gehe zu Definition** per Mausklick können Sie ändern, indem Sie zu **Tools** > **Optionen** > **Text-Editor** > **Allgemein** navigieren und aus der Dropdownliste **Use modifier key** (Zusatztaste verwenden) entweder **ALT** oder **STRG**+**ALT** auswählen. Sie können **Gehe zu Definition** per Mausklick auch deaktivieren, indem Sie das Kontrollkästchen **Mausklick zum Wechseln zur Definition aktivieren** deaktivieren.

![Aktivieren des Mausklicks zum Wechsel zur Definition](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Peek-Definition

Das Feature **Definition einsehen** ermöglicht eine Vorschau der Definition eines Typs, ohne Ihre Position im Editor verlassen zu müssen. Wenn Sie die Tastatur verwenden, platzieren Sie den Textcursor an einer beliebigen Stelle innerhalb des Typs oder Members, und drücken Sie **ALT+F12**. Wenn Sie die Maus verwenden, können Sie im Kontextmenü auf **Definition einsehen** klicken.

Wenn Sie die Funktion **STRG**+**Klick** aktivieren möchten, navigieren Sie zu **Tools** > **Optionen** > **Text-Editor** > **Allgemein**. Wählen Sie die Option **Definition in der Vorschauansicht öffnen** aus, klicken Sie auf **OK**, und schließen Sie das Dialogfeld **Optionen**.

![Festlegen der Option, Definitionen per Mausklick einzusehen](../ide/media/editor_options_peek_view.png)

Drücken Sie dann **STRG** (bzw. die Zusatztaste, die in **Optionen** ausgewählt ist), und klicken Sie auf den Typ oder Member.

![Animation: „Definition einsehen“](../ide/media/peek_definition.gif)

Wenn Sie im Popupfenster eine andere Definition einsehen, starten Sie einen Breadcrumbpfad, in dem Sie mithilfe der Kreise und Pfeile navigieren können, die oberhalb des Popups angezeigt werden.

Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen und Bearbeiten von Code mithilfe von „Definition einsehen“ (ALT+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Anzeigen von Metadaten als Quellcode (C#)

Wenn Sie die Definition von C#-Typen oder -Membern anzeigen, deren Quellcode nicht verfügbar ist, werden stattdessen die entsprechenden Metadaten angezeigt. Sie können die Deklarationen der Typen und Member sehen, nicht aber ihre Implementierungen.

Wenn Sie den Befehl **Gehe zu Definition** oder **Definition einsehen** für ein Element ausführen, dessen Quellcode nicht verfügbar ist, wird im Code-Editor ein Dokument mit Registerkarten angezeigt, das eine Ansicht der Metadaten des betreffenden Elements in der Darstellung als Quellcode enthält. Der Name des Typs wird auf der Registerkarte des Dokuments angezeigt, gefolgt von **[aus Metadaten]**.

Wenn Sie beispielsweise den Befehl **Gehe zu Definition** für <xref:System.Console>ausführen, werden Metadaten für <xref:System.Console> im Code-Editor als C#-Quellcode angezeigt. Der Code entspricht seiner Deklaration, zeigt jedoch keine Implementierung an.

![Metadaten als Quelle](../ide/media/metadatasource.png)

> [!NOTE]
> Wenn Sie versuchen, den Befehl **Gehe zu Definition** oder **Code einsehen** für Typen oder Member auszuführen, die als intern gekennzeichnet sind, zeigt die Visual Studio ihre Metadaten nicht als Quellcode an, unabhängig davon, ob die referenzierende Assembly ein Friend ist oder nicht.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Anzeigen von dekompilierten Quelldefinitionen anstelle von Metadaten (C#)

Sie können jetzt eine Option festlegen, mit der dekompilierter Quellcode angezeigt wird, wenn Sie die Definition eines C#-Typs oder -Members anzeigen, dessen Quellcode nicht verfügbar ist. Um dieses Feature zu aktivieren, wählen Sie in der Menüleiste **Extras** > **Optionen**. Erweitern Sie dann **Text-Editor** > **C#**  > **Erweitert**, und wählen Sie **Navigation zu dekompilierten Quellen aktivieren**.

![Anzeigen einer dekompilierten Definition](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio rekonstruiert Methodentexte mithilfe der ILSpy-Dekompilierung. Wenn Sie zum ersten Mal auf dieses Feature zugreifen, müssen Sie einem Haftungsausschluss bezüglich Softwarelizenzierung sowie Urheber- und Markenrecht zustimmen.

## <a name="see-also"></a>Siehe auch

- [Navigieren durch den Code](../ide/navigating-code.md)
- [Vorgehensweise: Anzeigen und Bearbeiten von Code mithilfe von „Definition einsehen“ (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)
