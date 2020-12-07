---
title: 'Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung'
description: Hier lernen Sie, ein Quiz zu erstellen, bei dem der Quizteilnehmer vier zufällige Mathematikaufgaben innerhalb einer vorgegebenen Zeit lösen muss.
ms.custom: SEO-VS-2020
ms.date: 10/16/2019
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0044e5d3a08e46318a325443e9f05742e141127
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479107"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung

In diesem Lernprogramm erstellen Sie ein Quiz, bei dem der Quizteilnehmer vier zufällige Mathematikaufgaben innerhalb einer angegebenen Zeit lösen muss.

> [!NOTE]
> In diesem Tutorial werden sowohl C# als auch Visual Basic behandelt. Achten Sie also auf die entsprechenden Informationen zu der Programmiersprache, die Sie verwenden.

In diesem Tutorial werden Sie durch die folgenden Aufgaben geführt:

- Generieren von Zufallszahlen mithilfe der <xref:System.Random>-Klasse.

- Auslösen von Ereignissen, die zu einem bestimmten Zeitpunkt ausgeführt werden, mithilfe eines <xref:System.Windows.Forms.Timer>-Steuerelements.

- Steuern des Programmablaufs mit `if else`-Anweisungen.

- Ausführen grundlegender arithmetischer Operationen im Code.

Nach Abschluss der Übung sieht das Quiz in etwa wie im folgenden Screenshot aus, enthält jedoch andere Zahlen:

![Mathetest mit vier Aufgaben](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Tutoriallinks

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Schritt 1: Erstellen eines Projekts und Hinzufügen von Bezeichnungen zum Formular](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Beginnen Sie, indem Sie das Projekt erstellen, Eigenschaften ändern und `Label`-Steuerelemente hinzufügen.|
|[Schritt 2: Erstellen einer zufälligen Additionsaufgabe](../ide/step-2-create-a-random-addition-problem.md)|Erstellen Sie eine Additionsaufgabe, und erstellen Sie Zufallszahlen mithilfe der `Random`-Klasse.|
|[Schritt 3: Hinzufügen eines Countdowntimers](../ide/step-3-add-a-countdown-timer.md)|Fügen Sie einen Countdowntimer hinzu, damit beim Quiz die Zeit gestoppt werden kann.|
|[Schritt 4: Hinzufügen der CheckTheAnswer()-Methode](../ide/step-4-add-the-checktheanswer-parens-method.md)|Fügen Sie eine Methode hinzu, mit der überprüft wird, ob der Quizteilnehmer eine richtige Antwort für die Aufgabe eingegeben hat.|
|[Schritt 5: Hinzufügen von Enter-Ereignishandlern für die NumericUpDown-Steuerelemente](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Fügen Sie Ereignishandler hinzu, mit denen das Quiz einfacher durchzuführen ist.|
|[Schritt 6: Hinzufügen einer Subtraktionsaufgabe](../ide/step-6-add-a-subtraction-problem.md)|Fügen Sie eine Subtraktionsaufgabe hinzu, in der Zufallszahlen generiert werden, der Timer verwendet wird, sowie überprüft wird, ob richtige Antworten eingegeben wurden.|
|[Schritt 7: Hinzufügen von Multiplikations- und Divisionsaufgaben](../ide/step-7-add-multiplication-and-division-problems.md)|Fügen Sie Multiplikations- und Divisionsaufgaben hinzu, die Zufallszahlen generieren, den Timer verwenden und in Hinsicht auf richtige Antworten überprüfen.|
|[Schritt 8: Anpassen des Quiz](../ide/step-8-customize-the-quiz.md)|Probieren Sie andere Funktionen aus. Ändern Sie z. B. Farben, und fügen Sie einen Hinweis hinzu.|

Es stehen auch umfangreiche kostenlose Videoschulungen zur Verfügung. Weitere Informationen zum Programmieren in C# finden Sie unter [C#-Grundlagen: Development for absolute beginners (C#-Grundlagen: Entwicklung für Anfänger)](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Weitere Informationen zum Programmieren in Visual Basic finden Sie unter [Visual Basic fundamentals: Development for absolute beginners (Visual Basic-Grundlagen: Entwicklung für Anfänger)](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Nächste Schritte

Beginnen Sie das Tutorial mit **[Schritt 1: Erstellen eines Projekts und Hinzufügen von Bezeichnungen zum Formular](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)** .

## <a name="see-also"></a>Siehe auch

* [Weitere C#-Tutorials](../get-started/csharp/index.yml)
* [Visual Basic-Tutorials](../get-started/visual-basic/index.yml)
* [C++-Tutorials](/cpp/get-started/tutorial-console-cpp)