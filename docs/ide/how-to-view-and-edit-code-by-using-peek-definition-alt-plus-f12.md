---
title: Verwenden von „Definition einsehen“
description: Erfahren Sie, wie Sie Ihren Code mit dem Befehl „Definition einsehen“ anzeigen und bearbeiten können, ohne aus dem Code, den Sie gerade schreiben, den Kontext wechseln zu müssen.
ms.custom: SEO-VS-2020
ms.date: 01/10/2018
ms.topic: how-to
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b706e730767c7c79fbeebc11291ecd11f4635b6
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596923"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Vorgehensweise: Anzeigen und Bearbeiten von Code mithilfe von „Definition einsehen“ (Alt+F12)

Mit dem Befehl **Definition einsehen** können Sie Code anzeigen und bearbeiten, ohne den Code zu verlassen, den Sie gerade schreiben. Mit **Definition einsehen** und **Gehe zu Definition** werden dieselben Informationen angezeigt, wobei mit **Definition einsehen** ein Popupfenster geöffnet wird, und mit **Gehe zu Definition** der Code in einem separaten Codefenster angezeigt wird. **Gehe zu Definition** verursacht einen Wechsel des Kontexts (also des aktiven Codefensters, der aktuellen Zeile und der Cursorposition) zum Codedefinitionsfenster. Mithilfe von **Definition einsehen** können Sie die Definition anzeigen und bearbeiten sowie innerhalb der Definitionsdatei navigieren, ohne Ihre Position in der ursprünglichen Codedatei zu verlassen.

Sie können **Definition einsehen** mit C#-, Visual Basic- und C++-Code verwenden. In Visual Basic enthält **Definition einsehen** einen Link zum **Objektkatalog** für Symbole ohne Definitionsmetadaten (z.B. integrierte .NET-Typen).

## <a name="use-peek-definition"></a>Verwenden von „Definition einsehen“

### <a name="open-a-peek-definition-window"></a>Öffnen eines Fensters „Definition einsehen“

1. Klicken Sie im Kontextmenü eines Typs oder Members auf **Definition einsehen**, um eine Definition einzusehen. Wenn die Option aktiviert ist,können Sie eine Definition auch mithilfe der Maus einsehen, indem Sie **STRG** (oder eine andere Zusatztaste) gedrückt halten und auf den Namen des Members klicken. Alternativ drücken Sie auf der Tastatur die Tasten **ALT**+**F12**.

     Diese Abbildung zeigt das Fenster **Definition einsehen** für eine Methode mit dem Namen `Print()`:

     ![Peek-Fenster](../ide/media/peekwindow.png)

     Das Definitionsfenster wird unter der `printer.Print("Hello World!")`-Zeile in der ursprünglichen Datei angezeigt. Das Fenster blendet keinen Code in der ursprünglichen Datei aus. Die Zeilen, die auf den Aufruf `printer.Print("Hello World!")` folgen, werden unter dem Definitionsfenster angezeigt.

1. Sie können den Cursor im Fenster „Code einsehen“ an unterschiedliche Positionen bewegen. Zudem können Sie weiterhin im ursprünglichen Codefenster navigieren.

1. Sie können eine Zeichenfolge aus dem Definitionsfenster kopieren und in den ursprünglichen Code einfügen. Sie können die Zeichenfolge auch per Drag & Drop aus dem Definitionsfenster in den ursprünglichen Code verschieben. Sie wird allerdings nicht im Definitionsfenster gelöscht.

1. Sie können das Definitionsfenster schließen, indem Sie die **ESC-TASTE** drücken oder auf die Schaltfläche **Schließen** auf der Registerkarte „Definitionsfenster“ klicken.

### <a name="open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Öffnen eines Fensters „Definition einsehen“ in einem Fenster „Definition einsehen“

Wenn bereits ein Fenster **Definition einsehen** geöffnet ist, können Sie **Definition ansehen** für den Code in diesem Fenster erneut aufrufen. Ein weiteres Definitionsfenster wird geöffnet. Ein Satz von Breadcrumbpunkten wird neben der Definitionsfensterregisterkarte, die Sie zum Navigieren zwischen Definitionsfenstern verwenden können, angezeigt. Die QuickInfo für die einzelnen Punkte zeigt jeweils den Namen und den Pfad der von den Punkten dargestellten Definitionsdatei an.

   ![Peek-Fenster innerhalb eines Peek-Fensters](../ide/media/peekwithinpeek.png)

### <a name="peek-definition-with-multiple-results"></a>„Definition einsehen“ mit mehreren Ergebnissen

Wenn Sie **Definition einsehen** für Code verwenden, für den mehrere Definitionen vorliegen, (z.B. bei einer partiellen Klasse), wird rechts neben der Codedefinitionsansicht eine Ergebnisliste angezeigt. Sie können jedes Ergebnis in der Liste auswählen, um dessen Definition anzuzeigen.

   ![Peek-Fenster aus verschiedenen Ergebnissen](../ide/media/peekmultiple.png)

### <a name="edit-inside-the-peek-definition-window"></a>Bearbeitung im Fenster „Definition einsehen“

Wenn Sie die Bearbeitung innerhalb eines **Definition einsehen**-Fensters beginnen, wird die Datei, die Sie ändern, automatisch als separate Registerkarte im Code-Editor geöffnet. Die Datei spiegelt dann die von Ihnen vorgenommenen Änderungen wider. Sie können weiterhin Änderungen im **Definition einsehen**-Fenster vornehmen, rückgängig machen und speichern, und die Registerkarte spiegelt weiterhin diese Änderungen wider. Auch wenn Sie das Fenster **Definition einsehen** schließen, ohne die Änderungen zu speichern, können Sie weitere Änderungen auf der Registerkarte vornehmen, rückgängig machen und speichern, indem Sie genau da weitermachen, wo Sie im Fenster **Definition einsehen** aufgehört hatten.

   ![Bearbeiten innerhalb eines Peek-Fensters](../ide/media/peekedit.png)

### <a name="to-change-options-for-peek-definition"></a>So ändern Sie die Optionen für „Definition einsehen“

1. Wechseln Sie zu **Extras** > **Optionen** > **Text-Editor** > **Allgemein**.

1. Klicken Sie auf die Option **Definition in der Vorschauansicht öffnen**.

1. Klicken Sie auf **OK**, um das Dialogfeld **Optionen** zu schließen.

   ![Festlegen der Option, Definitionen per Mausklick einzusehen](../ide/media/editor_options_peek_view.png)

### <a name="keyboard-shortcuts-for-peek-definition"></a>Tastenkombinationen für „Definition einsehen“

Im Fenster **Definition einsehen** können Sie diese Tastenkombinationen verwenden:

|Funktionalität|Tastenkombination|
|-------------------|:-----------------------:|
|Öffnen des Definitionsfensters|**ALT**+**F12**|
|Schließen des Definitionsfensters|**ESC**|
|Höherstufen des Definitionsfensters auf eine reguläre Dokumentregisterkarte|**STRG**+**Alt**+**Pos1**|
|Wechseln zwischen Definitionsfenstern|**STRG**+**ALT**+ **-** und **STRG**+**ALT**+ **=**|
|Zwischen mehreren Ergebnissen navigieren|**F8** und **UMSCHALT**+**F8**|
|Umschalten zwischen den Fenstern "Code-Editor" und "Definition"|**UMSCHALT**+**ESC**|

> [!NOTE]
> Sie können die gleichen Tastenkombinationen zum Bearbeiten in einem **Definition einsehen**-Fenster verwenden, die Sie an anderer Stelle in Visual Studio nutzen.

## <a name="see-also"></a>Siehe auch

- [Navigieren durch den Code](../ide/navigating-code.md)
- [Go To Definition and Peek Definition („Gehe zu Definition“ und „Definition einsehen“)](../ide/go-to-and-peek-definition.md)
- [Produktivitätsfeatures in Visual Studio](../ide/productivity-features.md)
