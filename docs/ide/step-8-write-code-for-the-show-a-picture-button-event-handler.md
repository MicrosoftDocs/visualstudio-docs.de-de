---
title: Schreiben von Code für den Ereignishandler der Schaltfläche „Bild anzeigen“
description: Schreiben Sie Code für den Ereignishandler der Schaltfläche „Bild anzeigen“ im Tutorial zum Erstellen eines Bildanzeigeprogramms.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9ed9e315bc4373fc2de9e31f0cbdd98ea274b404
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969671"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Schritt 8: Schreiben von Code für den Ereignishandler der Schaltfläche „Bild anzeigen“

In diesem Schritt schreiben Sie die Funktionsweise der Schaltfläche **Bild anzeigen** wie folgt:

- Wenn ein Benutzer auf die Schaltfläche klickt, öffnet die App ein <xref:System.Windows.Forms.OpenFileDialog>-Dialogfeld.

- Wenn ein Benutzer eine Bilddatei öffnet, zeigt die App dieses Bild in <xref:System.Windows.Forms.PictureBox> an.

Die IDE stellt ein leistungsstarkes Tool namens IntelliSense bereit, das Sie beim Schreiben von Code unterstützt. Wenn Sie Code eingeben, öffnet die IDE ein Feld mit Vervollständigungsvorschlägen für teilweise eingegebene Wörter.

IntelliSense versucht zu ermitteln, was Sie als Nächstes machen möchten, und springt automatisch zum zuletzt in der Liste auswählten Element. Sie können mithilfe der NACH-OBEN- oder NACH-UNTEN-TASTE in der Liste navigieren oder die Eingabe von Buchstaben fortsetzen, um die Optionen einzugrenzen. Wenn Sie die gewünschte Auswahl sehen, verwenden Sie die **Tab**-Taste, um sie auszuwählen. Sie können die Vorschläge aber auch ignorieren, wenn sie nicht benötigt werden.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>So schreiben Sie Code für den Ereignishandler der Schaltfläche „Bild anzeigen“

1. Wechseln Sie zum **Windows Forms-Designer**, und doppelklicken Sie auf die Schaltfläche **Bild anzeigen**. Die IDE wechselt sofort zum Code-Designer und positioniert den Cursor in der `showButton_Click()`-Methode (oder `ShowButton_Click()`-Methode), die Sie zuvor hinzugefügt haben.

1. Geben Sie in der leeren Zeile zwischen den beiden geschweiften Klammern `{ }` ein `i` ein. (Machen Sie die Eingabe in Visual Basic in der leeren Zeile zwischen `Private Sub...` und `End Sub`.) Ein **IntelliSense**-Fenster wird wie im folgenden Bild gezeigt geöffnet.

    ![IntelliSense mit Visual C&#35;-Code](../ide/media/express_ifintellisense.png)

    > [!NOTE]
    > Der Code zeigt möglicherweise keine Ereignishandler in Binnenmajuskeln an.

1. Im **IntelliSense**-Fenster sollte das Wort `if` hervorgehoben werden. (Ist dies nicht der Fall, geben Sie den Kleinbuchstaben `f` ein, dann wird das Wort markiert.) Beachten Sie, dass ein *QuickInfo*-Feld neben dem **IntelliSense**-Fenster mit der Beschreibung **Codeausschnitt für if-Anweisung** angezeigt wird. (In Visual Basic zeigt die QuickInfo auch an, dass es sich um einen Codeausschnitt handelt, aber mit einem etwas anderen Wortlaut.) Wenn Sie diesen Ausschnitt verwenden möchten, drücken Sie die **Tab**-Taste, um `if` in den Code einzufügen. Drücken Sie dann erneut die **Tab**-Taste, um den Codeausschnitt für die `if`-Anweisung zu verwenden. (Wenn Sie eine andere Stelle ausgewählt haben und das **IntelliSense**-Fenster nicht mehr angezeigt wird, verwenden Sie die RÜCKTASTE, um das `i` zu löschen. Geben Sie den Buchstaben „i“ erneut ein, um das **IntelliSense-Fenster** wieder zu öffnen.)

    ![Visual C&#35;-Code](../ide/media/express_highlighttrue.png)

### <a name="use-intellisense-to-enter-more-code"></a>Verwenden von IntelliSense zum Eingeben von weiterem Code

Als Nächstes verwenden Sie IntelliSense, um weiteren Code einzugeben, mit dem das Dialogfeld **Datei öffnen** geöffnet wird. Wenn der Benutzer die Schaltfläche **OK** auswählt, lädt PictureBox die Datei, die der Benutzer ausgewählt hat. In den folgenden Schritten wird gezeigt, wie Sie Code eingeben. Obwohl dies zahlreiche Schritte umfasst, sind nur wenige Tastatureingaben nötig:

 1. Beginnen Sie mit dem markierten Text **true** im Ausschnitt. Geben Sie `op` ein, um ihn zu überschreiben. (In Visual Basic beginnen Sie den Text mit einem Großbuchstaben; geben Sie daher `Op` ein.)

 1. Das **IntelliSense**-Fenster wird geöffnet und zeigt **openFileDialog1** an. Wählen Sie die **Tab**-Taste, um sie auszuwählen. (In Visual Basic beginnt der Text mit einem Großbuchstaben, daher wird **OpenFileDialog1** angezeigt. Stellen Sie sicher, dass **OpenFileDialog1** ausgewählt ist.)

     Weitere Informationen über `OpenFileDialog` finden Sie unter [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>).

 1. Geben Sie einen Punkt (`.`) ein (viele Programmierer nennen dies einen „Dot“). Da Sie direkt nach **openFileDialog1** einen Punkt eingegeben haben, wird ein **IntelliSense**-Fenster geöffnet, das alle Eigenschaften und Methoden der **OpenFileDialog**-Komponente enthält. Dies sind die gleichen Eigenschaften, die im Fenster **Eigenschaften** angezeigt werden, wenn Sie sie im **Windows Forms-Designer** auswählen. Sie können auch Methoden auswählen, die Komponenten veranlassen, bestimmte Aufgaben auszuführen (z. B. Öffnen eines Dialogfelds).

    > [!NOTE]
    > Im **IntelliSense**-Fenster werden sowohl Eigenschaften als auch Methoden angezeigt. Um zu bestimmen, was angezeigt wird, betrachten Sie das Symbol auf der linken Seite jedes Elements im Fenster **IntelliSense**. Neben jeder Methode wird ein Block und neben jeder Eigenschaft ein Schraubenschlüssel abgebildet. Zudem wird neben jedem Ereignis ein Blitzsymbol angezeigt. <br><br>Die folgenden Symbole werden angezeigt:<br><br>![Methodensymbol](../ide/media/express_iconmethod.png)<br>![Eigenschaftssymbol](../ide/media/express_iconproperty.png)<br>![Ereignissymbol](../ide/media/express_iconevent.png)

 1. Beginnen Sie mit der Eingabe von `ShowDialog` (die Großschreibung ist in IntelliSense nicht relevant). Die `ShowDialog()`-Methode zeigt das Dialogfeld **Datei öffnen** an. Nachdem **ShowDialog** im Fenster hervorgehoben wurde, wählen Sie die **Tab**-Taste. Sie können „ShowDialog“ auch markieren und **F1** auswählen, um dazu Hilfe abzurufen.

    Weitere Informationen zur `ShowDialog()`-Methode finden Sie unter [ShowDialog-Methode](<xref:System.Windows.Forms.Form.ShowDialog%2A>).

 1. Wenn Sie für ein Steuerelement oder eine Komponente eine Methode verwenden (wird als *Aufrufen einer Methode* bezeichnet), müssen Sie Klammern hinzufügen. Geben Sie daher eine öffnende und schließende runde Klammer direkt nach dem „g“ in `ShowDialog` ein: `()`. Nun sollte es wie „openFileDialog1.ShowDialog()“ angezeigt werden.

    > [!NOTE]
    > Methoden sind ein wichtiger Bestandteil von Apps, und in diesem Tutorial wurden mehrere Möglichkeiten zum Verwenden von Methoden veranschaulicht. Sie können die Methode einer Komponente aufrufen, um sie zu veranlassen, eine bestimmte Aufgabe auszuführen, so wie Sie beispielsweise die `ShowDialog()`-Methode der **OpenFileDialog**-Komponente aufgerufen haben. Sie können eigene Methoden erstellen, um die App zum Ausführen bestimmter Schritte zu veranlassen. Hierzu gehört zum Beispiel die jetzt von Ihnen erstellten Methode, die als `showButton_Click()`-Methode bezeichnet wird und ein Dialogfeld sowie ein Bild öffnet, wenn ein Benutzer auf eine Schaltfläche klickt.

 1. Fügen Sie für C# ein Leerzeichen und dann zwei Gleichheitszeichen (`==`) hinzu. Fügen Sie für Visual Basic ein Leerzeichen hinzu, und verwenden Sie dann ein einzelnes Gleichheitszeichen (`=`). (C# und Visual Basic verwenden unterschiedliche Gleichheitsoperatoren.)

 1. Fügen Sie ein weiteres Leerzeichen hinzu. Sobald Sie das Leerzeichen eingeben, wird ein anderes **IntelliSense**-Fenster geöffnet. Geben Sie `DialogResult` ein, und drücken Sie die **Tab**-Taste zum Hinzufügen.

    > [!NOTE]
    > Wenn Sie Code schreiben, um eine Methode aufzurufen, wird gelegentlich ein Wert zurückgegeben. In diesem Fall gibt die <xref:System.Windows.Forms.CommonDialog.ShowDialog>-Methode der **OpenFileDialog**-Komponente einen <xref:System.Windows.Forms.DialogResult>-Wert zurück. DialogResult ist ein besonderer Wert, der anzeigt, was in einem Dialogfeld geschehen ist. Bei der **OpenFileDialog**-Komponente gibt es z.B. die Möglichkeit, dass der Benutzer entweder **OK** oder **Abbrechen** auswählt. Daher gibt die `ShowDialog()`-Methode der Komponente entweder `DialogResult.OK` oder `DialogResult.Cancel` zurück.

 1. Geben Sie einen Punkt ein, um das **IntelliSense**-Fenster für den DialogResult-Wert zu öffnen. Geben Sie den Buchstaben `O` ein, und drücken Sie die **Tab**-Taste, um **OK** einzufügen.

    Weitere Informationen zu DialogResult finden Sie unter [DialogResult](<xref:System.Windows.Forms.DialogResult>).

    > [!NOTE]
    > Die erste Codezeile sollte vollständig sein. Für C# sollte die Ausgabe in etwa wie folgt aussehen.
    >
    >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
    >
    >  Für Visual Basic sollte sie wie folgt aussehen.
    >
    >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

 1. Fügen Sie jetzt eine weitere Codezeile hinzu. Sie können die Codezeile eingeben (oder kopieren und einfügen), aber erwägen Sie, die Codezeile mithilfe von IntelliSense hinzuzufügen. Je vertrauter Sie mit IntelliSense sind, desto schneller können Sie einen eigenen Code schreiben. Die letzte `showButton_Click()`-Methode sollte folgendem Code ähneln.

    [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

    [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]

    [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="next-steps"></a>Nächste Schritte

* Den nächsten Schritt des Tutorials finden Sie unter **[Schritt 9: Überprüfen, Kommentieren und Testen des Codes](../ide/step-9-review-comment-and-test-your-code.md)** .

* Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 7: Hinzufügen von Dialogfeldkomponenten zum Formular](../ide/step-7-add-dialog-components-to-your-form.md).

## <a name="see-also"></a>Weitere Informationen

* [Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Erstellen eines Vergleichsspiels](tutorial-3-create-a-matching-game.md)
