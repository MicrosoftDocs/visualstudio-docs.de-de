---
title: 'Schritt 9: Überprüfen, Kommentieren und Testen des Codes'
description: Hier erfahren Sie, wie Sie Ihrem Code einen Kommentar hinzufügen und Ihre App testen.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
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
ms.openlocfilehash: 0bcf879d2bb6fa592f77d4c94cb2f784d2c53f2b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969619"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Schritt 9: Überprüfen, Kommentieren und Testen des Codes

Als Nächstes fügen Sie dem Code einen Kommentar hinzu. Ein Kommentar ist ein Hinweis, der sich nicht auf das Verhalten der App auswirkt. Kommentare machen den Code für andere verständlicher. Es sollte zur guten Gewohnheit werden, Kommentare zum Code hinzuzufügen.

In C# kennzeichnen zwei Schrägstriche (//) eine Zeile als Kommentar. In Visual Basic wird ein einfaches Anführungszeichen (') verwendet, um eine Zeile als Kommentar zu kennzeichnen. Testen Sie die Anwendung, nachdem Sie einen Kommentar hinzugefügt haben. Es empfiehlt sich, den Code während der Arbeit am Projekt häufig auszuführen und zu testen, damit alle Probleme frühzeitig abgefangen und korrigiert werden können, bevor der Code komplexer wird. Dies wird *iteratives Testen* genannt.

Sie haben soeben ein funktionierendes Programm erstellt, und obwohl es noch nicht fertig ist, kann es bereits ein Bild laden. Bevor Sie dem Code einen Kommentar hinzufügen und den Code testen, sollten Sie sich die Zeit nehmen, die Codekonzepte zu prüfen, da Sie diese Konzepte häufig verwenden:

- Durch Doppelklicken auf die Schaltfläche **Bild anzeigen** im **Windows Forms-Designer** hat die IDE dem Code des Programms automatisch eine *Methode* hinzugefügt.

- Mithilfe von Methoden wird der Code organisiert, denn Methoden stellen Gruppen von Code dar.

- Die meiste Zeit führt eine Methode eine kleine Anzahl von Schritten in einer bestimmten Reihenfolge aus, so wie die `showButton_Click()`- oder `ShowButton_Click()`-Methode beispielsweise ein Dialogfeld anzeigt und dann ein Bild lädt.

- Eine Methode besteht aus *Codeanweisungen* oder Codezeilen. Stellen Sie sich eine Methode als eine Möglichkeit zum Bündeln von Codeanweisungen vor.

- Wenn eine Methode ausgeführt oder *aufgerufen* wird, werden die Anweisungen in der Methode einzeln der Reihe nach ausgeführt, und zwar beginnend mit der ersten Anweisung.

   Im Folgenden sehen Sie ein Beispiel für eine Anweisung.

  ```csharp
  PictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Anweisungen sorgen dafür, dass Programme bestimmte Schritte ausführen. In C# enden Anweisungen immer mit einem Semikolon. In Visual Basic ist das Ende einer Zeile das Ende einer Anweisung. (In Visual Basic wird kein Semikolon benötigt.) Die vorangehende Anweisung teilt dem <xref:System.Windows.Forms.PictureBox>-Steuerelement mit, die Datei zu laden, die der Benutzer mit der **OpenFileDialog**-Komponente ausgewählt hat.

## <a name="to-add-comments"></a>So fügen Sie Kommentare hinzu

1. Fügen Sie dem Code folgenden Kommentar hinzu.

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     [!code-csharp[VbExpressTutorial1Step9_10#1](../ide/codesnippet/CSharp/step-9-review-comment-and-test-your-code_1.cs)]

     [!code-vb[VbExpressTutorial1Step9_10#1](../ide/codesnippet/VisualBasic/step-9-review-comment-and-test-your-code_1.vb)]

    Der <xref:System.Windows.Forms.Control.Click>-Ereignishandler der **showButton**-Schaltfläche ist jetzt funktionsfähig. Sie haben angefangen, Code zu schreiben, und mit einer `if`-Anweisung begonnen. Mit einer `if`-Anweisung teilen Sie der App Folgendes mit: „Prüfe diese Bedingung, und wenn sie zutrifft, führe diese Aktionen aus“. In diesem Fall wird die App aufgefordert, das Dialogfeld **Datei öffnen** zu öffnen. Wenn der Benutzer eine Datei auswählt und auf die Schaltfläche **OK** klickt, soll anschließend die entsprechende Datei im Steuerelement **PictureBox** geladen werden.

    > [!TIP]
    > Die IDE soll das Schreiben von Code vereinfachen, und *Codeausschnitte* sind eine Möglichkeit, dies zu erreichen. Ein Ausschnitt ist eine Kurzform, die in einen kleinen Codeblock erweitert wird.
    >
    >  Sie können alle verfügbaren Ausschnitte sehen. Klicken Sie in der Menüleiste auf **Extras** > **Codeausschnitt-Manager**. Bei C# befindet sich der `if`-Ausschnitt unter **Visual C#**. Bei Visual Basic befinden sich die `if`-Ausschnitte unter **Codemuster** > **Konditionelle Abschnitte und Schleifen**. Sie können diesen Manager verwenden, um vorhandene Ausschnitte zu durchsuchen oder eigene Ausschnitte hinzuzufügen.
    >
    >  Um einen Codeausschnitt bei der Eingabe von Code zu aktivieren, geben Sie ihn ein, und drücken Sie die **TAB-TASTE**. Im **IntelliSense**-Fenster werden viele Codeausschnitte angezeigt. Drücken Sie daher die **TAB-TASTE** zweimal: das erste Mal, um den Ausschnitt im **IntelliSense**-Fenster auszuwählen, und das zweite Mal, um der IDE mitzuteilen, dass dieser Ausschnitt verwendet werden soll. (IntelliSense unterstützt den `if`-Ausschnitt, aber nicht den `ifelse`-Ausschnitt.)

1. Speichern Sie Ihre App, indem Sie auf die Symbolleistenschaltfläche **Alle speichern** klicken (siehe Screenshot), bevor Sie Ihre Anwendung ausführen.

     Schaltfläche ![Alle speichern](../ide/media/express_iconsaveall.png) in der Symbolleiste<br>_Schaltfläche* 
***Alle speichern** _

     Alternativ können Sie zum Speichern der App in der Menüleiste auf **Datei** > **Alle speichern** klicken oder **STRG**+**UMSCHALT**+**S** drücken. Es ist empfehlenswert, früh und häufig zu speichern.

     Wenn die App ausgeführt wird, sollte sie wie im folgenden Bild aussehen.

     ![Bildanzeigeprogramm](../ide/media/express_pictureviewerdonerun.png)<br>***Bildanzeigeprogramm***

## <a name="to-test-your-app"></a>Testen der App

1. Drücken Sie die **F5-TASTE**, oder klicken Sie auf der Symbolleiste auf die Schaltfläche **Debuggen starten**.

1. Klicken Sie auf die Schaltfläche **Bild anzeigen**, um den Code auszuführen, den Sie soeben geschrieben haben. Zuerst öffnet die App das Dialogfeld **Datei öffnen**. Überprüfen Sie, ob Ihre Filter in der Dropdownliste **Dateityp** unten im Dialogfeld angezeigt werden. Navigieren Sie dann zu einem Bild, und öffnen Sie es. Normalerweise befinden sich Beispielbilder, die mit dem Betriebssystem Windows ausgeliefert werden, im Ordner *Eigene Bilder\Beispielbilder* unter dem Ordner *Eigene Dokumente*.

    > [!TIP]
    > Wenn im Dialogfeld **Bilddatei auswählen** keine Bilder angezeigt werden, stellen Sie sicher, dass der Filter **Alle Dateien (*.\*)** in der Dropdownliste auf der unteren rechten Seite des Dialogfelds aktiviert ist.

1. Laden Sie ein Bild, um es im PictureBox-Steuerelement anzuzeigen. Versuchen Sie dann, die Größe des Formulars zu ändern, indem Sie die Rahmen ziehen. Da Sie das PictureBox-Steuerelement in einem TableLayoutPanel angedockt haben, das wiederum im Formular angedockt ist, wird die Größe des Bildbereichs geändert, damit dieser so breit wie das Formular ist und die oberen 90 Prozent des Formulars einnimmt. Das ist der Grund für die Verwendung der <xref:System.Windows.Forms.TableLayoutPanel>- und <xref:System.Windows.Forms.FlowLayoutPanel>-Container: Diese Container sorgen dafür, dass das Formular die richtige Größe behält, wenn der Benutzer die Größe ändert.

     Zum jetzigen Zeitpunkt gehen größere Bilder über den Rahmen des Bildanzeigeprogramms hinaus. Im nächsten Schritt fügen Sie Code hinzu, um Bilder ins Fenster einzupassen.

## <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Den nächsten Schritt des Tutorials finden Sie unter **[Schritt 10: Schreiben von Code für zusätzliche Schaltflächen und ein Kontrollkästchen](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)** .

- Um zum vorherigen Tutorialschritt zurückzukehren, klicken Sie auf [Schritt 8: Schreiben von Code für den Ereignishandler der Schaltfläche „Bild anzeigen“](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

## <a name="see-also"></a>Weitere Informationen

* [Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Erstellen eines Vergleichsspiels](tutorial-3-create-a-matching-game.md)
