---
title: 'Schritt 7: Hinzufügen von Multiplikations- und Divisionsaufgaben'
description: So fügen Sie Multiplikations- und Divisionsaufgaben hinzu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84dc1df79392aeefe331746c52d2fbe8dbb91e8e
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479497"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Schritt 7: Hinzufügen von Multiplikations- und Divisionsaufgaben

Im siebenten Teil dieses Lernprogramms fügen Sie Multiplikations- und Divisionsaufgaben hinzu. Zunächst müssen Sie aber überlegen, wie diese Änderung vorgenommen wird. Überlegen Sie sich den ersten Schritt, der das Speichern von Werten einschließt.

> [!NOTE]
> Dieses Thema ist Teil einer Reihe von Lernprogrammen zu grundlegenden Konzepte der Codierung. Eine Übersicht über das Tutorial finden Sie unter [Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-multiplication-and-division-problems"></a>So fügen Sie Multiplikations- und Divisionsaufgaben hinzu

1. Fügen Sie dem Formular vier Ganzzahlvariablen hinzu.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Ändern Sie wie zuvor die `StartTheQuiz()`-Methode, damit die Multiplikations- und Divisionsaufgaben mit Zufallszahlen ausgefüllt werden.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. Ändern Sie die `CheckTheAnswer()`-Methode, damit auch die Multiplikations- und Divisionsaufgaben überprüft werden.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Da es keine einfache Möglichkeit gibt, das Multiplikationszeichen (×) und das Divisionszeichen (÷) mit der Tastatur einzugeben, wird in C# und Visual Basic ein Sternchen (*) für Multiplikation und ein Schrägstrich (/) für Division akzeptiert.

4. Ändern Sie den letzten Teil des <xref:System.Windows.Forms.Timer.Tick>-Ereignishandlers des Timers, damit die richtige Antwort ausgegeben wird, wenn die Zeit abgelaufen ist.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Speichern Sie das Programm, und führen Sie es aus.

     Die Quizteilnehmer müssen vier Aufgaben beantworten, um das Quiz abzuschließen. Dies ist in der folgenden Abbildung veranschaulicht.

     ![Mathequiz mit vier Aufgaben](../ide/media/express_finishedquiz.png)<br/>
***Mathetest** _ _ mit vier Aufgaben*

## <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Den nächsten Schritt des Tutorials finden Sie unter **[Schritt 8: Anpassen des Quiz](../ide/step-8-customize-the-quiz.md)** .

- Um zum vorherigen Tutorialschritt zurückzukehren, klicken Sie auf [Schritt 6: Hinzufügen einer Subtraktionsaufgabe](../ide/step-6-add-a-subtraction-problem.md).
