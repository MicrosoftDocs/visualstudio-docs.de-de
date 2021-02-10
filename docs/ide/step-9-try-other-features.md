---
title: 'Schritt 9: Ausprobieren weiterer Features'
description: Hier erfahren Sie, wie Sie Symbole und Farben ändern, einen Spieltimer und Sounds hinzufügen und das Spiel vergrößern können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e405cef9360083a8f0169ac338e2c23cffc71218
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969554"
---
# <a name="step-9-try-other-features"></a>Schritt 9: Ausprobieren weiterer Features
Um den Lerneffekt zu erhöhen, können Sie das Ändern von Symbolen und Farben, das Hinzufügen eines Spieltimers und das Hinzufügen von Sounds ausprobieren. Versuchen Sie, die Spielfläche zu vergrößern und den Timer anzupassen, um das Spiel anspruchsvoller zu machen.

Eine vollständige Version des Beispiels können Sie unter [Complete Matching Game tutorial sample (Durchführen des Abgleichspiels)](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba) herunterladen.

## <a name="to-try-other-features"></a>So probieren Sie weitere Funktionen aus

- Ersetzen Sie die Symbole und Farben durch selbst gewählte Symbole und Farben.

    > [!TIP]
    > Beschäftigen Sie sich mit der [Forecolor](<xref:System.Windows.Forms.Control.ForeColor%2A>)-Eigenschaft des Bezeichnungsfelds.

- Fügen Sie einen Spieltimer hinzu und ermitteln Sie, wie lange es dauert, bis der Spieler gewinnt.

    > [!TIP]
    > Dazu können Sie ein Bezeichnungsfeld über dem <xref:System.Windows.Forms.TableLayoutPanel>-Steuerelement hinzufügen, um die bisher abgelaufene Zeit anzuzeigen, und dem Formular ein weiteres Zeitgeber-Steuerelement hinzufügen, das die Zeit misst. Verwenden Sie Code, um den Zeitgeber zu starten, wenn der Spieler das Spiel startet, und beenden Sie den Zeitgeber, nachdem die letzten zwei Symbole übereinstimmen.

- Fügen Sie einen Sound hinzu, der wiedergegeben wird, wenn der Spieler eine Übereinstimmung findet. Fügen Sie einen anderen Sound hinzu, der wiedergegeben wird, wenn der Spieler zwei nicht übereinstimmende Symbole aufdeckt, und einen dritten Sound für das Ausblenden der Symbole durch das Programm.

    > [!TIP]
    > Um Sounds wiederzugeben, können Sie den <xref:System.Media>-Namespace verwenden. Weitere Informationen finden Sie in den Videos [Play sounds in Windows Forms app (C#) (Wiedergeben von Sound in der Windows Forms-App (C#))](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) oder [How to play audio in Visual Basic (Audiowiedergabe in Visual Basic)](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be).

- Machen Sie das Spiel schwieriger, indem Sie die Spielfläche vergrößern.

    > [!TIP]
    > Es genügt nicht, einfach nur Zeilen und Spalten im TableLayoutPanel-Steuerelement hinzuzufügen – Sie müssen außerdem die Anzahl von Symbolen beachten, die Sie erstellen.

- Gestalten Sie das Spiel anspruchsvoller, indem Sie das erste Symbol ausblenden, wenn der Spieler zu langsam ist und nach Ablauf einer bestimmten Zeit nicht das zweite Symbol gewählt hat.

## <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Es stehen umfangreiche kostenlose Videoschulungen zur Verfügung. Weitere Informationen zum Programmieren in Visual Basic finden Sie unter [Visual Basic fundamentals: Development for absolute beginners (Visual Basic-Grundlagen: Entwicklung für Anfänger)](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Weitere Informationen zum Programmieren in C# finden Sie unter [C#-Grundlagen: Development for absolute beginners (C#-Grundlagen: Entwicklung für Anfänger)](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Wie Sie zum vorherigen Tutorialschritt zurückkehren, erfahren Sie unter [Schritt 8: Hinzufügen einer Methode zum Überprüfen, ob der Spieler gewonnen hat](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
