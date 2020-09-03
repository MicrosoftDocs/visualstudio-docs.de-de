---
title: 'Tutorial 3: Erstellen eines Memory-Spiels | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 30ee029fe231202c821c8448d3594192b5ebfdf8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299852"
---
# <a name="tutorial-3-create-a-matching-game"></a>Tutorial 3: Erstellen eines Memory-Spiels
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Lernprogramm erstellen Sie ein Vergleichsspiel, bei dem Spieler ausgeblendete Symbolpaare finden müssen. Sie lernen Folgendes:

- Speichern von Objekten (beispielsweise Symbole) in einem `List`-Objekt

- Verwenden einer `foreach`-Schleife in Visual C# und einer `For Each`-Schleife in Visual Basic, um die Elemente einer Liste zu durchlaufen

- Speichern des Formularzustands mithilfe von Verweisvariablen

- Erstellen eines Ereignishandlers für mehrere Objekte zum Reagieren auf Ereignisse

- Erstellen eines Zeitgebers, der nach dem Start und Ablauf einer bestimmten Zeit genau ein Ereignis auslöst

  Am Ende dieses Lernprogramms sieht Ihr Code so aus wie in der folgenden Abbildung.

  ![Spiel, das Sie in diesem Tutorial erstellen](../ide/media/express-finishedgame.png "Express_FinishedGame") Spiel, das Sie in diesem Tutorial erstellen

> [!NOTE]
> In diesem Lernprogramm wird sowohl Visual C# als auch Visual Basic behandelt. Achten Sie also auf die entsprechenden Informationen zu der Programmiersprache, die Sie verwenden.

 Wenn Sie sich festfahren oder Probleme mit der Programmierung haben, versuchen Sie, Ihre Fragen in einem der MSDN-Foren zu stellen. Weitere Informationen finden Sie im Forum zu [Visual Basic](https://social.msdn.microsoft.com/Forums/en-US/home) und [Visual C#-Forum](https://social.msdn.microsoft.com/Forums/en-US/home). Es stehen auch umfangreiche kostenlose Videoschulungen zur Verfügung. Weitere Informationen zum Programmieren in Visual Basic finden Sie unter [Visual Basic Grundlagen: Entwicklung für Anfänger](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Weitere Informationen zum Programmieren in Visual Basic C# finden Sie unter [C#-Grundlagen: Entwicklung für Anfänger](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Schritt 1: Erstellen eines Projekts und Hinzufügen einer Tabelle zum Formular](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Erstellen Sie zuerst das Projekt, und fügen Sie ein `TableLayoutPanel`-Steuerelement hinzu, um die Steuerelemente richtig auszurichten.|
|[Schritt 2: Hinzufügen eines zufälligen Objekts und einer Liste von Symbolen](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Fügen Sie ein `Random`-Objekt und ein `List`-Objekt hinzu, um eine Liste mit Symbolen zu erstellen.|
|[Schritt 3: Zuweisen eines zufälligen Symbols zu jeder Bezeichnung](../ide/step-3-assign-a-random-icon-to-each-label.md)|Weisen Sie die Symbole willkürlich den `Label`-Steuerelementen zu, sodass sie in jedem Spiel anders angeordnet sind.|
|[Schritt 4: Hinzufügen eines Click-Ereignis Handlers zu jeder Bezeichnung](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Fügen Sie einen Click-Ereignishandler hinzu, der die Farbe der Bezeichnung ändert, auf die geklickt wird.|
|[Schritt 5: Hinzufügen von Bezeichnungs verweisen](../ide/step-5-add-label-references.md)|Fügen Sie Verweisvariablen hinzu, um nachzuverfolgen, auf welche Bezeichnungen geklickt wird.|
|[Schritt 6: Hinzufügen eines Timers](../ide/step-6-add-a-timer.md)|Fügen Sie dem Formular einen Zeitgeber hinzu, um die Zeit zu speichern, die im Spiel bisher vergangen ist.|
|[Schritt 7: beibehalten der Sichtbarkeit von Paaren](../ide/step-7-keep-pairs-visible.md)|Behalten Sie die Sichtbarkeit von Symbolpaaren bei, falls ein übereinstimmendes Paar ausgewählt wird.|
|[Schritt 8: Hinzufügen einer Methode, um zu überprüfen, ob der Spieler gewonnen hat](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Fügen Sie eine `CheckForWinner()`-Methode hinzu, um zu überprüfen, ob ein Spieler gewonnen hat.|
|[Schritt 9: ausprobieren weiterer Features](../ide/step-9-try-other-features.md)|Probieren Sie andere Funktionen aus, z. B. das Ändern von Symbolen und Farben, das Hinzufügen eines Rasters und das Hinzufügen von Sounds. Versuchen Sie, die Spielfläche zu vergrößern und den Timer anzupassen.|
