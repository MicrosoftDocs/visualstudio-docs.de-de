---
title: 'Schritt 9: Überprüfen, Kommentieren und Testen des Codes | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 090aeb83f6d0480c511acd808498953ae6c01940
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851101"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Schritt 9: Überprüfen, Kommentieren und Testen des Codes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Als Nächstes fügen Sie dem Code einen Kommentar hinzu. Ein Kommentar ist ein Hinweis, der sich nicht auf das Programmverhalten auswirkt. Kommentare machen den Code für andere verständlicher. Es sollte zur guten Gewohnheit werden, Kommentare zum Code hinzuzufügen. In Visual C# kennzeichnen zwei Schrägstriche (//) eine Zeile als Kommentar. In Visual Basic wird ein einfaches Anführungszeichen (') verwendet, um eine Zeile als Kommentar zu kennzeichnen. Testen Sie das Programm, nachdem Sie einen Kommentar hinzugefügt haben. Es empfiehlt sich, den Code während der Arbeit am Projekt häufig auszuführen und zu testen, damit alle Probleme frühzeitig abgefangen und korrigiert werden können, bevor der Code komplexer wird. Dies wird *iteratives Testen* genannt.

 Sie haben soeben ein funktionierendes Programm erstellt, und obwohl es noch nicht fertig ist, kann es bereits ein Bild laden. Bevor Sie dem Code einen Kommentar hinzufügen und den Code testen, sollten Sie sich die Zeit nehmen, die Codekonzepte zu prüfen, da Sie diese Konzepte häufig verwenden:

- Wenn Sie auf die Schaltfläche **Bild anzeigen** in Windows Forms-Designer Doppel geklickt haben, hat die IDE dem Code des Programms automatisch eine *Methode* hinzugefügt.

- Mit Methoden wird Ihr Code organisiert: Es geht darum, auf welche Weise Ihr Code gruppiert wird.

- Die meiste Zeit führt eine Methode eine kleine Anzahl von Schritten in einer bestimmten Reihenfolge aus, so wie die `showButton_Click()`-Methode beispielsweise ein Dialogfeld anzeigt und dann ein Bild lädt.

- Eine Methode besteht aus *Codeanweisungen* oder Codezeilen. Stellen Sie sich eine Methode als eine Möglichkeit zum Bündeln von Codeanweisungen vor.

- Wenn eine Methode ausgeführt oder *aufgerufen* wird, werden die Anweisungen in der Methode einzeln der Reihe nach ausgeführt, und zwar beginnend mit der ersten Anweisung.

   Im Folgenden sehen Sie ein Beispiel für eine Anweisung.

  ```csharp
  pictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Anweisungen sorgen dafür, dass Programme bestimmte Schritte ausführen. In Visual C# endet eine Anweisung immer mit einem Semikolon. In Visual Basic ist das Ende einer Zeile das Ende einer Anweisung. (In Visual Basic wird kein Semikolon benötigt.) Die vorangehende Anweisung teilt dem `PictureBox`-Steuerelement mit, die Datei zu laden, die der Benutzer mit der **OpenFileDialog**-Komponente ausgewählt hat.

  ![Link zu Video](../data-tools/media/playvideo.gif "Wiedergeben") Eine videoversion dieses Themas finden Sie im Video 5 zum [Tutorial 1: Erstellen eines Bild Anzeige Programms in Visual Basic-Video 5](https://msdn.microsoft.com/vbasic/gg315356.aspx) oder im [Tutorial 1: Erstellen eines Bild Anzeige Programms in c#](https://msdn.microsoft.com/vcsharp/gg278413.aspx). Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können. Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise.

### <a name="to-add-comments"></a>So fügen Sie Kommentare hinzu

1. Fügen Sie dem Code folgenden Kommentar hinzu.

     [!code-csharp[VbExpressTutorial1Step9_10#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial1Step9_10#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#1)]

    > [!NOTE]
    > Der Click-Ereignishandler der **showButton**-Schaltfläche ist jetzt funktionsfähig. Sie haben angefangen, Code zu schreiben, und mit einer `if`-Anweisung begonnen. Mit einer `if`-Anweisung teilen Sie dem Programm Folgendes mit: "Prüfe diese Bedingung, und wenn sie zutrifft, führe diese Aktionen aus". In diesem Fall wird das Programm angewiesen, das Dialogfeld **Datei öffnen** zu öffnen. wenn der Benutzer eine Datei auswählt und die Schaltfläche **OK** auswählt, laden Sie die Datei in das PictureBox-Feld.

    > [!TIP]
    > Die IDE soll das Schreiben von Code vereinfachen, und *Codeausschnitte* sind eine Möglichkeit, dies zu erreichen. Ein Ausschnitt ist eine Kurzform, die in einen kleinen Codeblock erweitert wird.
    >
    >  Sie können alle verfügbaren Ausschnitte sehen. Klicken Sie in der Menüleiste auf **Extras** > **Codeausschnitt-Manager**. Bei Visual C# befindet sich der `if`-Ausschnitt unter **Visual C#**. Bei Visual Basic befinden sich die `if`-Ausschnitte unter **Konditionelle Abschnitte und Schleifen**, **Codemuster**. Sie können diesen Manager verwenden, um vorhandene Ausschnitte zu durchsuchen oder eigene Ausschnitte hinzuzufügen.
    >
    >  Um einen Ausschnitt bei der Eingabe von Code zu aktivieren, geben Sie ihn ein, und wählen Sie die TAB-TASTE aus. Im **IntelliSense** -Fenster werden viele Ausschnitte angezeigt. aus diesem Grund wählen Sie die Tab-Taste zweimal aus: zuerst wählen Sie den Ausschnitt aus dem **IntelliSense** -Fenster aus, und teilen Sie der IDE mit, dass der Ausschnitt verwendet werden soll. (IntelliSense unterstützt den `if`-Ausschnitt, aber nicht den `ifelse`-Ausschnitt.)

2. Speichern Sie das Programm, bevor Sie es ausführen, indem Sie die Symbolleistenschaltfläche **Alle speichern** auswählen, die wie folgt aussieht.

     ![Schaltfläche "Alle speichern](../ide/media/express-iconsaveall.png "Express_IconSaveAll") " Schaltfläche zum Speichern aller

     Wählen Sie alternativ in der Menüleiste **Datei**, **Alle speichern** aus, um das Programm zu speichern. Es ist empfehlenswert, früh und häufig zu speichern.

     Wenn das Programm ausgeführt wird, sollte es wie im folgenden Bild aussehen.

     ![Bild](../ide/media/express-pictureviewerdonerun.png "Express_PictureViewerDoneRun") Anzeige Bild Anzeige

### <a name="to-test-your-program"></a>So testen Sie das Programm

1. Drücken Sie die F5-TASTE, oder klicken Sie auf die Symbolleistenschaltfläche **Debuggen starten**.

2. Klicken Sie auf die Schaltfläche **Bild anzeigen**, um den Code auszuführen, den Sie soeben geschrieben haben. Zuerst öffnet das Programm das Dialogfeld **Datei öffnen**. Überprüfen Sie, ob Ihre Filter in der Dropdownliste **Dateityp** unten im Dialogfeld angezeigt werden. Navigieren Sie dann zu einem Bild, und öffnen Sie es. Normalerweise befinden sich Beispielbilder, die mit dem Betriebssystem Windows ausgeliefert werden, im Ordner **Eigene Bilder\Beispielbilder** unter dem Ordner **Eigene Dokumente**.

    > [!NOTE]
    > Wenn keine Bilder im Dialogfeld **Bilddatei auswählen** angezeigt werden, stellen Sie sicher, dass der Filter "alle Dateien (*. \* )" in der Dropdown Liste auf der unteren rechten Seite des Dialog Felds ausgewählt ist.

3. Laden Sie ein Bild, um es im PictureBox-Steuerelement anzuzeigen. Versuchen Sie dann, die Größe des Formulars zu ändern, indem Sie die Rahmen ziehen. Da Sie das PictureBox-Steuerelement in einem TableLayoutPanel angedockt haben, das wiederum im Formular angedockt ist, wird die Größe des Bildbereichs geändert, damit dieser so breit wie das Formular ist und die oberen 90 Prozent des Formulars einnimmt. Das ist der Grund, weshalb Sie den TableLayoutPanel- und FlowLayoutPanel-Container verwendet haben: Diese Container sorgen dafür, dass das Formular ordnungsgemäß dimensioniert wird, wenn der Benutzer die Größe ändert.

     Zum jetzigen Zeitpunkt gehen größere Bilder über den Rahmen des Bildanzeigeprogramms hinaus. Im nächsten Schritt fügen Sie Code hinzu, um Bilder ins Fenster einzupassen.

### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Um zum nächsten Schritt des Tutorials zu wechseln, [Klicken Sie auf Schritt 10: Schreiben von Code für zusätzliche Schaltflächen und ein Kontrollkästchen](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

- Um zum vorherigen Tutorialschritt zurückzukehren, klicken Sie auf [Schritt 8: Schreiben von Code für den Ereignis Handler der Schaltfläche "Bild anzeigen](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)".
