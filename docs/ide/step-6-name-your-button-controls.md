---
title: 'Schritt 6: Benennen der Schaltflächen-Steuerelemente'
description: So benennen Sie die Schaltflächen-Steuerelemente
ms.custom: SEO-VS-2020
ms.date: 08/30/2016
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
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
ms.openlocfilehash: 0f6612806f8bf1453cf28f9d75c78588c2074bb0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868880"
---
# <a name="step-6-name-your-button-controls"></a>Schritt 6: Benennen der Schaltflächen-Steuerelemente

Es gibt nur ein <xref:System.Windows.Forms.PictureBox> im Formular. Als Sie es hinzugefügt haben, hat die IDE diesem Steuerelement automatisch den Namen **pictureBox1** gegeben. Es gibt nur ein <xref:System.Windows.Forms.CheckBox>, das den Namen **checkBox1** trägt. In diesem Tutorial schreiben Sie Code, der sich auf die Steuerelemente „CheckBox“ und „PictureBox“ bezieht. Da jedes Steuerelement nur einmal vorhanden ist, wissen Sie, was sich hinter den Namen **pictureBox1** oder **checkBox1** im Code verbirgt.

> [!TIP]
> In Visual Basic beginnen die Namen von Steuerelementen automatisch mit einem großen Anfangsbuchstaben. Daher lauten die Namen dort **PictureBox1**, **CheckBox1** usw.

Das Formular enthält vier Schaltflächen, und die IDE hat ihnen folgende Namen zugewiesen: **button1**, **button2**, **button3** und **button4**. Anhand der aktuellen Namen können Sie jedoch nicht erkennen, welches Steuerelement die Schaltfläche **Close** ist und welches Steuerelement die Schaltfläche **Show a picture** ist. Daher ist es hilfreich, den Schaltflächen-Steuerelementen aufschlussreichere Namen zu geben.

## <a name="to-name-your-button-controls"></a>So benennen Sie die Schaltflächen-Steuerelemente

1. Wählen Sie im Formular die Schaltfläche **Schließen** aus. (Wenn alle Schaltflächen noch ausgewählt sind, drücken Sie die **ESC-TASTE**, um die Auswahl aufzuheben.) Scrollen Sie im Fenster **Eigenschaften**, bis Sie die Eigenschaft **(Name)** sehen. (Die Eigenschaft **(Name)** befindet sich oben in der Liste, wenn die Eigenschaften alphabetisch sortiert sind.) Ändern Sie den Namen wie im folgenden Screenshot gezeigt in **closeButton**.

    ![Eigenschaftenfenster mit closeButton-Name](../ide/media/express_setnameproperty.png)<br>***Eigenschaftenfenster** __ mit* dem _Namen* ***closeButton**_

    > [!NOTE]
    > Versuchen Sie, den Namen der Schaltfläche in **close Button** (Schaltfläche schließen) zu ändern, sodass ein Leerzeichen zwischen den Wörtern „close“ und „Button“ steht. Daraufhin zeigt die IDE eine Fehlermeldung an: „Der Eigenschaftswert ist ungültig.“ Leerzeichen (und einige andere Zeichen) sind in Steuerelementnamen nicht zulässig.

1. Benennen Sie die anderen drei Schaltflächen in **backgroundButton**, **clearButton** und **showButton** um.
Sie können die Namen überprüfen, indem Sie im Fenster **Eigenschaften** die Steuerelementauswahl-Dropdownliste auswählen. Die neuen Schaltflächennamen werden angezeigt.

1. Doppelklicken Sie im Formular auf die Schaltfläche **Bild anzeigen** . Wählen Sie alternativ im Formular die Schaltfläche **Bild anzeigen** aus, und drücken Sie anschließend die **EINGABETASTE**. Daraufhin öffnet die IDE eine neue Registerkarte namens **Form1.cs** im Hauptfenster. (Wenn Sie Visual Basic verwenden, lautet der Name der Registerkarte **Form1.vb**).

   Auf dieser Registerkarte wird die Codedatei wie im folgenden Screenshot dargestellt hinter dem Formular angezeigt.

    ![Form1.cs-Registerkarte mit Visual C&#35;-Code](../ide/media/express_showbuttoncode.png)<br>
***Form1.cs** _ _Registerkarte mit C#-Code*

    > [!NOTE]
    > Möglicherweise zeigt die Registerkarte „Form1.cs“ oder „Form1.vb“ **showButton** als **ShowButton** an.

1. Konzentrieren Sie sich auf diesen Teil des Codes.

    ```csharp
        private void ShowButton_Click(object sender, EventArgs e)
    {
    }
    ```

    ```vb
        Private Sub showButton_Click() Handles showButton.Click

    End Sub
    ```

   [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

   Dieser Code wird `showButton_Click()` bzw. `ShowButton_Click()` genannt. Die IDE hat ihn dem Code des Formulars hinzugefügt, als Sie die Codedatei für die Schaltfläche **showButton** geöffnet haben. Wenn Sie zur Entwurfszeit die Codedatei für ein Steuerelement in einem Formular öffnen, wird Code für das Steuerelement generiert, wenn er nicht bereits vorhanden ist. Dieser Code, der als *Methode* bezeichnet wird, wird ausgeführt, wenn Sie die App ausführen und auf das Steuerelement klicken, in diesem Fall die Schaltfläche **Bild anzeigen**.

1. Wählen Sie noch mal die Registerkarte **Windows Forms-Designer** aus (**Form1.cs [Entwurf]**), und öffnen Sie dann die Codedatei für die Schaltfläche **Bild löschen**, um für diese eine Methode im Code des Formulars zu erstellen. Wiederholen Sie diesen Vorgang für die verbleibenden beiden Schaltflächen. Die IDE fügt der Codedatei des Formulars jedes Mal eine neue Methode hinzu.

1. Öffnen Sie zum Hinzufügen einer weiteren Methode im **Windows Forms-Designer** die Codedatei für das Steuerelement **CheckBox**, damit die IDE eine `checkBox1_CheckedChanged()`-Methode hinzufügt. Diese Methode wird immer dann aufgerufen, wenn der Benutzer das Kontrollkästchen aktiviert oder deaktiviert.

   > [!TIP]
   > Wenn Sie an einer App arbeiten, wechseln Sie häufig zwischen dem Code-Editor und dem **Windows Forms-Designer**. Die IDE vereinfacht die Navigation im Projekt. Öffnen Sie den **Windows Forms-Designer** mit dem **Projektmappen-Explorer**, indem Sie für C# auf *Form1.cs* oder für Visual Basic auf *Form1.vb* doppelklicken, oder klicken Sie in der Menüleiste auf **Ansicht** > **Designer**.

    Im Folgenden sehen Sie den neuen Code, der im Code-Editor angezeigt wird.

    [!code-csharp[VbExpressTutorial1Step6_#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]

    [!code-vb[VbExpressTutorial1Step6_#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]

    > [!NOTE]
    > Der Code zeigt möglicherweise keine Ereignishandler in Binnenmajuskeln an.

    Die fünf Methoden, die Sie hinzugefügt haben, werden als *Ereignishandler* bezeichnet, da die App sie immer dann aufruft, wenn ein Ereignis eintritt (z. B. wenn ein Benutzer auf eine Schaltfläche klickt oder ein Kontrollkästchen aktiviert).

    Wenn Sie den Code für ein Steuerelement in der IDE zur Entwurfszeit anzeigen, fügt Visual Studio für dieses Steuerelement eine Ereignishandlermethode hinzu, wenn keine vorhanden ist. Wenn Sie z.B. auf eine Schaltfläche doppelklicken, fügt die IDE einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click>-Ereignis hinzu (dieser wird jedes Mal aufgerufen, wenn der Benutzer auf die Schaltfläche klickt). Wenn Sie auf ein Kontrollkästchen doppelklicken, fügt die IDE einen Ereignishandler für das <xref:System.Windows.Forms.CheckBox.CheckedChanged>-Ereignis hinzu (dieser wird jedes Mal aufgerufen, wenn der Benutzer das Kontrollkästchen aktiviert oder deaktiviert).

    Nachdem Sie für ein Steuerelement einen Ereignishandler hinzugefügt haben, können Sie jederzeit vom **Windows Forms-Designer** dahin zurückkehren, indem Sie auf das Steuerelement doppelklicken oder in der Menüleiste **Ansicht** > **Code** auswählen.

    Namen sind wichtig, wenn Sie Programme erstellen, und für Methoden (und Ereignishandler) können Sie beliebige Namen verwenden. Wenn Sie mit der IDE einen Ereignishandler hinzufügen, erstellt die IDE basierend auf dem Namen des Steuerelements und des behandelten Ereignisses einen Namen.

    Das Click-Ereignis für eine Schaltfläche mit dem Namen **showButton** wird beispielsweise als `showButton_Click()`- oder `ShowButton_Click()`-Ereignishandlermethode bezeichnet. Normalerweise werden nach dem Methodennamen auch eine öffnende und eine schließende runde Klammer `()` hinzugefügt, um anzuzeigen, dass es sich um Methoden handelt.

    Wenn Sie den Namen einer Codevariable ändern möchten, klicken Sie mit der rechten Maustaste auf die Variable im Code, und wählen Sie dann **Umgestalten** > **Umbenennen** aus. Alle Instanzen dieser Variable im Code werden umbenannt. Weitere Informationen finden Sie unter [Refactoring: Umbenennen](../ide/reference/rename.md).

## <a name="next-steps"></a>Nächste Schritte

* Den nächsten Schritt des Tutorials finden Sie unter **[Schritt 7: Hinzufügen von Dialogfeldkomponenten zum Formular](../ide/step-7-add-dialog-components-to-your-form.md)** .

* Um zum vorherigen Tutorialschritt zurückzukehren, klicken Sie auf [Schritt 5: Hinzufügen von Steuerelementen zum Formular](../ide/step-5-add-controls-to-your-form.md).

## <a name="see-also"></a>Weitere Informationen

* [Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Erstellen eines Vergleichsspiels](tutorial-3-create-a-matching-game.md)
