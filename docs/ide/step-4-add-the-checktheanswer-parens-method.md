---
title: 'Schritt 4: Hinzufügen der CheckTheAnswer()-Methode'
description: Hier erfahren Sie, wie Sie eine CheckTheAnswer()-Methode schreiben, um die Antworten auf Mathematikaufgaben auf Korrektheit zu überprüfen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f6e52d415b4278a04e559c64cdcfac86cdf22261
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950704"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Schritt 4: Hinzufügen der CheckTheAnswer()-Methode

Im vierten Teil dieses Lernprogramms schreiben Sie eine Methode, `CheckTheAnswer()`, die bestimmt, ob die Antworten auf die Mathematikaufgaben korrekt sind. Dieses Thema ist Teil einer Reihe von Lernprogrammen zu grundlegenden Konzepte der Codierung. Eine Übersicht über das Tutorial finden Sie unter [Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Dieses Thema ist Teil einer Reihe von Lernprogrammen zu grundlegenden Konzepte der Codierung. Eine Übersicht über das Tutorial finden Sie unter [Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-whether-the-answers-are-correct"></a>So überprüfen Sie, ob die Antworten richtig sind

> [!NOTE]
> Wenn Sie weiterhin in Visual Basic arbeiten, verwenden Sie das Schlüsselwort `Function` anstelle des üblichen Schlüsselworts `Sub`, da diese Methode einen Wert zurückgibt. Es ist wirklich ganz einfach: Ein Sub-Schlüsselwort gibt keinen Wert zurück, aber ein Function-Schlüsselwort gibt einen Wert zurück.

1. Fügen Sie die `CheckTheAnswer()`-Methode hinzu. Diese Methode sollte den anderen Methoden entsprechen, die Sie erstellt haben, z. B. `StartTheQuiz()`.

     Wenn diese Methode aufgerufen wird, werden die Werte von „addend1“ und „addend2“ hinzugefügt und das Ergebnis mit dem Wert im <xref:System.Windows.Forms.NumericUpDown>-Summensteuerelement verglichen. Wenn die Werte gleich sind, gibt die Methode den Wert `true` zurück. Anderenfalls gibt die Methode den Wert `false` zurück. Der Code sollte wie folgt aussehen.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Nun überprüfen Sie die Antwort, indem Sie die Code in der Methode aktualisieren, damit der <xref:System.Windows.Forms.Timer.Tick>-Ereignishandler des Zeitgebers die neue `CheckTheAnswer()`-Methode aufruft.

2. Fügen Sie den folgenden Code zur `if else`-Anweisung in der `Timer1_Tick()`-Methode hinzu, damit der Timer angehalten wird, wenn der Benutzer die richtige Antwort auswählt.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Wenn die Antwort richtig ist, gibt `CheckTheAnswer()``true` zurück. Der Ereignishandler beendet den Timer, zeigt eine Glückwunschmeldung an, und macht anschließend die Schaltfläche **Start** erneut verfügbar. Anderenfalls wird das Quiz fortgesetzt.

3. Speichern Sie das Programm, führen Sie es aus, starten Sie ein Quiz, und geben Sie eine richtige Antwort für die Additionsaufgabe an.

    > [!NOTE]
    > Bevor Sie die Antwort eingeben, müssen Sie entweder den Standardwert auswählen, oder Sie müssen die Null manuell löschen. Später in diesem Lernprogramm wird dieses Verhalten korrigiert.

     Wenn Sie eine richtige Antwort angeben, wird ein Meldungsfeld geöffnet, die Schaltfläche **Start** wird verfügbar, und der Timer wird angehalten.

## <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Den nächsten Schritt des Tutorials finden Sie unter **[Schritt 5: Hinzufügen von Enter-Ereignishandlern für die NumericUpDown-Steuerelemente](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)** .

- Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 3: Hinzufügen eines Countdowntimers](../ide/step-3-add-a-countdown-timer.md).
