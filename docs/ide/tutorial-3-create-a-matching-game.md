---
title: 'Tutorial 3: Erstellen eines Vergleichsspiels'
description: Hier erfahren Sie, wie Sie ein Vergleichsspiel erstellen, bei dem der Spieler ausgeblendete Symbolpaare finden müssen.
ms.custom: SEO-VS-2020
ms.date: 10/16/2019
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62859c86ff3b4057eceb1f6e00ebfd46867f9927
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479029"
---
# <a name="tutorial-3-create-a-matching-game"></a>Tutorial 3: Erstellen eines Memory-Spiels

In diesem Lernprogramm erstellen Sie ein Vergleichsspiel, bei dem Spieler ausgeblendete Symbolpaare finden müssen.

> [!NOTE]
> In diesem Tutorial werden sowohl C# als auch Visual Basic behandelt. Achten Sie also auf die entsprechenden Informationen zu der Programmiersprache, die Sie verwenden.

In diesem Tutorial werden Sie durch die folgenden Aufgaben geführt:

- Speichern von Objekten (beispielsweise Symbole) in einem <xref:System.Collections.Generic.List%601>-Objekt

- Verwenden einer `foreach`-Schleife in C# und einer `For Each`-Schleife in Visual Basic, um die Elemente einer Liste zu durchlaufen

- Speichern des Formularzustands mithilfe von Verweisvariablen

- Erstellen eines Ereignishandlers für mehrere Objekte zum Reagieren auf Ereignisse

- Erstellen eines Zeitgebers, der nach dem Start und Ablauf einer bestimmten Zeit genau ein Ereignis auslöst

Anschließend sollte Ihre App in etwa wie in der folgenden Abbildung aussehen:

![Spiel, das Sie in diesem Lernprogramm erstellen](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Tutoriallinks

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Schritt 1: Erstellen eines Projekts und Hinzufügen einer Tabelle zum Formular](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Erstellen Sie zuerst das Projekt, und fügen Sie ein `TableLayoutPanel`-Steuerelement hinzu, um die Steuerelemente richtig auszurichten.|
|[Schritt 2: Hinzufügen eines zufällig ausgewählten Objekts und einer Liste von Symbolen](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Fügen Sie ein `Random`-Objekt und ein `List`-Objekt hinzu, um eine Liste mit Symbolen zu erstellen.|
|[Schritt 3: Zuweisen eines zufälligen Symbols zu jeder Bezeichnung](../ide/step-3-assign-a-random-icon-to-each-label.md)|Weisen Sie die Symbole willkürlich den `Label`-Steuerelementen zu, sodass sie in jedem Spiel anders angeordnet sind.|
|[Schritt 4: Hinzufügen eines Click-Ereignishandlers zu jeder Bezeichnung](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Fügen Sie einen `Click`-Ereignishandler hinzu, der die Farbe der Bezeichnung ändert, auf die geklickt wird.|
|[Schritt 5: Hinzufügen von Bezeichnungsverweisen](../ide/step-5-add-label-references.md)|Fügen Sie Verweisvariablen hinzu, um nachzuverfolgen, auf welche Bezeichnungen geklickt wird.|
|[Schritt 6: Hinzufügen von Timern](../ide/step-6-add-a-timer.md)|Fügen Sie dem Formular einen Zeitgeber hinzu, um die Zeit zu speichern, die im Spiel bisher vergangen ist.|
|[Schritt 7: Beibehalten der Sichtbarkeit von Paaren](../ide/step-7-keep-pairs-visible.md)|Behalten Sie die Sichtbarkeit von Symbolpaaren bei, falls ein übereinstimmendes Paar ausgewählt wird.|
|[Schritt 8: Hinzufügen einer Methode, um zu überprüfen, ob ein Spieler gewonnen hat](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Fügen Sie eine `CheckForWinner()`-Methode hinzu, um zu überprüfen, ob ein Spieler gewonnen hat.|
|[Schritt 9: Ausprobieren weiterer Features](../ide/step-9-try-other-features.md)|Probieren Sie andere Funktionen aus, z. B. das Ändern von Symbolen und Farben, das Hinzufügen eines Rasters und das Hinzufügen von Sounds. Versuchen Sie, die Spielfläche zu vergrößern und den Timer anzupassen.|

Es stehen auch umfangreiche kostenlose Videoschulungen zur Verfügung. Weitere Informationen zum Programmieren in C# finden Sie unter [C#-Grundlagen: Development for absolute beginners (C#-Grundlagen: Entwicklung für Anfänger)](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Weitere Informationen zum Programmieren in Visual Basic finden Sie unter [Visual Basic fundamentals: Development for absolute beginners (Visual Basic-Grundlagen: Entwicklung für Anfänger)](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Nächste Schritte

Beginnen Sie das Tutorial mit **[Schritt 1: Erstellen eines Projekts und Hinzufügen einer Tabelle zum Formular](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)** .

## <a name="see-also"></a>Siehe auch

* [Weitere C#-Tutorials](../get-started/csharp/index.yml)
* [Visual Basic-Tutorials](../get-started/visual-basic/index.yml)
* [C++-Tutorials](/cpp/get-started/tutorial-console-cpp)