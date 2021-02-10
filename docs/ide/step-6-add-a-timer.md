---
title: 'Schritt 6: Hinzufügen von Timern'
description: Hier erfahren Sie, wie Sie dem Spiel ein <xref:System.Windows.Forms.Timer>-Steuerelement hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 77daa47cdd6336849903202233392d3eecc33c1a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868893"
---
# <a name="step-6-add-a-timer"></a>Schritt 6: Hinzufügen von Timern
Als Nächstes fügen Sie dem Spiel ein <xref:System.Windows.Forms.Timer>-Steuerelement hinzu. Ein solcher Timer wartet eine angegebene Anzahl von Millisekunden und löst anschließend ein Ereignis aus, das als *Tick* bezeichnet wird. Dies ist nützlich für den Start einer Aktion oder die regelmäßige Wiederholung eine Aktion. In diesem Fall verwenden Sie einen Zeitgeber, um dem Spieler zu ermöglichen, zwei Symbole auszuwählen, und um die beiden Symbole nach einer kurzen Zeit wieder auszublenden, sofern sie nicht übereinstimmen.

## <a name="to-add-a-timer"></a>So fügen Sie einen Timer hinzu

1. Wählen Sie **Timer** in der Toolbox des **Windows Forms-Designers** (in der Kategorie **Komponenten**) aus, und drücken Sie anschließend die **EINGABETASTE**, oder doppelklicken Sie auf den Timer, um dem Formular ein Timer-Steuerelement hinzuzufügen. Das Symbol des Timers mit dem Namen **Timer1** wird in einem Bereich unterhalb des Formulars angezeigt, wie in der folgenden Abbildung dargestellt.

     ![Zeitgeber](../ide/media/express_timer.png)<br/>
***Zeitgeber***

    > [!NOTE]
    > Wenn die Toolbox leer ist, haben Sie zuvor möglicherweise nicht den Formular-Designer aktiviert, sondern den Code für das Formular.

2. Wählen Sie das Symbol **Timer1**, um den Timer auszuwählen. Im Fenster **Eigenschaften** wechseln Sie von der Anzeige der Ereignisse zur Anzeige der Eigenschaften. Legen Sie die **Interval**-Eigenschaft des Timers auf **750** fest, ohne den Wert **FALSE** der **Enabled**-Eigenschaft zu ändern. Die Eigenschaft **Interval** gibt an, wie lange der Timer zwischen *Ticks* wartet bzw. wann das <xref:System.Windows.Forms.Timer.Tick>-Ereignis auslöst werden soll. Mit dem Wert „750“ wartet der Timer eine Dreiviertelsekunde (750 Millisekunden), bevor er das Tick-Ereignis auslöst. Sie rufen die <xref:System.Windows.Forms.Timer.Start>-Methode für den Start des Zeitgeber nur auf, nachdem der Spieler das zweite Bezeichnungsfeld auswählt hat.

3. Wählen Sie das Symbol des Timer-Steuerelements im **Windows Forms-Designer** aus, und drücken Sie dann die **EINGABETASTE**, oder doppelklicken Sie auf den Timer, um einen leeren Tick-Ereignishandler hinzuzufügen. Ersetzen Sie entweder den Code durch den folgenden Code, oder geben Sie den folgenden Code manuell in den Ereignishandler ein.

     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]

      > [!IMPORTANT]
      > Verwenden Sie das Programmiersprachensteuerelement oben rechts auf dieser Seite, um entweder den C#-Codeausschnitt oder den Visual Basic-Codeausschnitt anzuzeigen.<br><br>![Programmiersprachensteuerelement auf docs.microsoft.com](../ide/media/docs-programming-language-control.png)

     Der Tick-Ereignishandler bewirkt drei Dinge: Zuerst beendet er den Zeitgeber, indem er die <xref:System.Windows.Forms.Timer.Stop>-Methode aufruft. Anschließend verwendet er die beiden Verweisvariablen `firstClicked` und `secondClicked`, um die Symbole für die zwei Bezeichnungsfelder, die der Spieler gewählt hat, wieder unsichtbar zu machen. Zuletzt setzt er die Verweisvariablen `firstClicked` und `secondClicked` in C# auf `null` und in Visual Basic auf `Nothing` zurück. Dieser Schritt ist wichtig, weil sich das Programm auf diese Weise selbst zurücksetzt. In diesem Zustand werden keine <xref:System.Windows.Forms.Label>-Steuerelemente überwacht, und das Programm ist wieder für eine Auswahl des Spielers bereit.

    > [!NOTE]
    > Ein Timer-Objekt verfügt über eine `Start()`-Methode, die den Timer startet, und eine `Stop()`-Methode, die den Timer stoppt. Wenn Sie die **Enabled**-Eigenschaft des Timers im **Eigenschaftenfenster** auf **TRUE** festlegen,fängt dieser an zu laufen, sobald das Programm beginnt. Wenn Sie die Eigenschaft jedoch auf **FALSE** festgelegt lassen, fängt dieser erst an zu laufen, wenn seine `Start()`-Methode aufgerufen wird. Normalerweise löst ein Timer sein Tick-Ereignis immer wieder aus, wobei in der **Interval**-Eigenschaft festgelegt ist, wie viele Millisekunden zwischen Ticks gewartet wird. Sie haben möglicherweise bemerkt, dass im Tick-Ereignis die `Stop()`-Methode des Zeitgebers aufgerufen wird. Damit wird der Timer in den *Einmalmodus* versetzt, was bedeutet, dass er nach dem Aufruf der `Start()`-Methode das festgelegte Zeitintervall wartet, dann ein Tick-Ereignis auslöst und anschließend stoppt.

4. Um den neuen Zeitgeber in Aktion zu sehen, wechseln Sie zum Code-Editor und fügen am Anfang und Ende der `label_Click()`-Ereignishandlermethode den folgenden Code hinzu. (Sie fügen am Anfang zwei `if`-Anweisungen und am Ende drei Anweisungen hinzu. Der Rest der Methode bleibt unverändert.)

     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]

     Der Code am Anfang der Methode ermittelt durch Überprüfung des Werts der **Enabled**-Eigenschaft, ob der Timer gestartet wurde. Wenn der Spieler also das erste und zweite Label-Steuerelement wählt und der Timer gestartet wird, hat die Auswahl eines dritten Steuerelements keinerlei Auswirkungen. Außerdem wird verhindert, dass der Spieler schnell ein drittes Mal klickt, bevor das Spiel für einen weiteren ersten Klick bereit ist. 

     Mit dem Code am Ende der Methode wird die Verweisvariable `secondClicked` festgelegt, um das zweite Label-Steuerelement zu ermitteln, das der Spieler gewählt hat. Anschließend wird die Farbe des Symbols in der Bezeichnung auf Schwarz festgelegt, um es sichtbar zu machen. Dann startet der Code den Timer im Einmalmodus, sodass dieser 750 Millisekunden lang wartet und dann ein einzelnes Tick-Ereignis auslöst. Der Tick-Ereignishandler des Timers blendet dann die beiden Symbole aus und setzt die Verweisvariablen `firstClicked` und `secondClicked` zurück, damit das Formular dafür bereit ist, dass der Spieler ein anderes Symbol wählt.

5. Speichern Sie das Programm, und führen Sie es aus. Wenn Sie ein Symbol wählen, wird es sichtbar.

6. Wählen Sie ein anderes Symbol. Es wird kurz angezeigt, und dann werden beide Symbole wieder ausgeblendet. Wiederholen Sie dies mehrere Male. Das Formular überwacht jetzt das erste und zweite gewählte Symbol und verwendet den Zeitgeber, um bis zum Ausblenden der Symbole zu warten.

## <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Den nächsten Schritt des Tutorials finden Sie unter **[Schritt 7: Beibehalten der Sichtbarkeit von Paaren](../ide/step-7-keep-pairs-visible.md)** .

- Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 5: Hinzufügen von Bezeichnungsverweisen](../ide/step-5-add-label-references.md).
