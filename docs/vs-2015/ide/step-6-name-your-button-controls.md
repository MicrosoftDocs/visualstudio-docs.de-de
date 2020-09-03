---
title: 'Schritt 6: Benennen der Schaltflächen-Steuerelemente | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4d4d703dbe28776cd93c7a438fc457d9f50ac4f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851130"
---
# <a name="step-6-name-your-button-controls"></a>Schritt 6: Benennen der Schaltflächen-Steuerelemente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Es gibt nur ein PictureBox-Steuerelement im Formular. Als Sie es hinzugefügt haben, hat die IDE diesem Steuerelement automatisch den Namen **pictureBox1**gegeben. Es gibt nur ein Kontrollkästchen, das den Namen **checkBox1**trägt. Bald schreiben Sie einige Codezeilen, die auf das CheckBox- und das PictureBox-Steuerelement verweisen. Da jedes Steuerelement nur einmal vorhanden ist, wissen Sie, was sich hinter den Namen **pictureBox1** oder **checkBox1** im Code verbirgt.

> [!NOTE]
> In Visual Basic beginnen die Namen von Steuerelementen automatisch mit einem großen Anfangsbuchstaben. Daher lauten die Namen dort **PictureBox1**, **CheckBox1**usw.

 Das Formular enthält vier Schaltflächen, und die IDE hat ihnen folgende Namen zugewiesen: **button1**, **button2**, **button3**und **button4**. Anhand der aktuellen Namen können Sie jedoch nicht erkennen, welches Steuerelement die Schaltfläche **Close** ist und welches Steuerelement die Schaltfläche **Show a picture** ist. Daher ist es hilfreich, den Schaltflächen-Steuerelementen aufschlussreichere Namen zu geben.

 ![Link zu Video](../data-tools/media/playvideo.gif "Wiedergeben") Eine videoversion dieses Themas finden Sie im Video 3 zum [Tutorial 1: Erstellen eines Bild Anzeige Programms in Visual Basic-Video 3](https://msdn.microsoft.com/vbasic/gg315354.aspx) oder [Tutorial 1: Erstellen eines Bild Anzeige Programms in c#](https://msdn.microsoft.com/vcsharp/gg278411.aspx). Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können. Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise.

### <a name="to-name-your-button-controls"></a>So benennen Sie die Schaltflächen-Steuerelemente

1. Wählen Sie im Formular die Schaltfläche **Schließen** aus. (Wenn alle Schaltflächen noch ausgewählt sind, wählen Sie die ESC-Taste, um die Auswahl abzubrechen.) Scrollen Sie im Fenster **Eigenschaften** , bis Sie die Eigenschaft **(Name)** sehen. (Die Eigenschaft **(Name)** befindet sich in der Nähe des oberen Rands, wenn die Eigenschaften alphabetisch sind.) Ändern Sie den Namen in **CloseButton**, wie in der folgenden Abbildung dargestellt.

     ![Mit CloseButton-Namen Eigenschaftenfenster](../ide/media/express-setnameproperty.png "Express_SetNameProperty") Mit CloseButton-Namen Eigenschaftenfenster

    > [!NOTE]
    > Wenn Sie versuchen, den Namen der Schaltfläche in **closeButton** zu ändern, also mit einem Leerzeichen zwischen den beiden Wörtern, zeigt die IDE eine Fehlermeldung an: "Der Eigenschaftswert ist ungültig". Leerzeichen (und einige andere Zeichen) sind in Steuerelementnamen nicht zulässig.

2. Benennen Sie die anderen drei Schaltflächen in **backgroundButton**, **clearButton**und **showButton**um. Sie können die Namen überprüfen, indem Sie im Fenster **Eigenschaften** die Steuerelementauswahl-Dropdownliste auswählen. Die neuen Schaltflächennamen werden angezeigt.

3. Doppelklicken Sie im Formular auf die Schaltfläche **Bild anzeigen** . Wählen Sie alternativ die Schaltfläche **Bild anzeigen** im Formular aus, und drücken Sie dann die EINGABETASTE. Damit öffnet die IDE eine zusätzliche Registerkarte im Hauptfenster mit der Bezeichnung **Form1.cs** (**Form1.vb** bei Verwendung von Visual Basic). Auf dieser Registerkarte wird die Codedatei hinter dem Formular angezeigt, wie im folgenden Bild dargestellt.

     ![Registerkarte "Form1.cs" mit Visual C-&#35; Code](../ide/media/express-showbuttoncode.png "Express_ShowButtonCode") Registerkarte "Form1.cs" mit Visual c#-Code

4. Konzentrieren Sie sich auf diesen Teil des Codes. (Wählen Sie bei Verwendung von Visual Basic die Registerkarte **VB** unten aus, um die Visual Basic-Version des Codes anzuzeigen.)

     [!code-csharp[VbExpressTutorial1Step6#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial1Step6#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb#1)]

     Sie betrachten Code mit dem Namen `showButton_Click()`. Die IDE hat ihn dem Code des Formulars hinzugefügt, als Sie die Codedatei für die Schaltfläche **showButton** geöffnet haben. Wenn Sie zur Entwurfszeit die Codedatei für ein Steuerelement in einem Formular öffnen, wird Code für das Steuerelement generiert, wenn er nicht bereits vorhanden ist. Dieser Code, als *Methode*bezeichnet, wird ausgeführt, wenn Sie das Programm ausführen und das Steuerelement auswählen, in diesem Fall die Schaltfläche **Bild anzeigen** .

    > [!NOTE]
    > In diesem Lernprogramm wurde der automatisch generierte Visual Basic-Code vereinfacht, indem der zwischen Klammern, (), gesetzte Text entfernt wurde. In diesen Fällen können Sie den gleichen Code entfernen. Das Programm funktioniert so oder so. Für den Rest der Lernprogramme wird automatisch generierter Code vereinfacht, wann immer dies möglich ist.

5. Wählen Sie die Registerkarte Windows Forms-Designer erneut aus (**Form1.cs [Entwurf]** in Visual C#, **Form1.vb [Entwurf]** in Visual Basic), und öffnen Sie dann die Codedatei für die Schaltfläche **Bild löschen**, um eine Methode für sie im Code des Formulars zu erstellen. Wiederholen Sie diesen Vorgang für die verbleibenden beiden Schaltflächen. Die IDE fügt der Codedatei des Formulars jedes Mal eine neue Methode hinzu.

6. Um eine weitere Methode hinzuzufügen, öffnen Sie die Codedatei für das CheckBox-Steuerelement im Windows Forms-Designer, damit die IDE eine `checkBox1_CheckedChanged()` -Methode hinzufügt. Diese Methode wird immer dann aufgerufen, wenn der Benutzer das Kontrollkästchen aktiviert oder deaktiviert.

    > [!NOTE]
    > Wenn Sie an einem Programm arbeiten, wechseln Sie häufig zwischen dem Code-Editor und dem Windows Forms-Designer. Die IDE vereinfacht die Navigation im Projekt. Öffnen Sie den Windows Forms-Designer mit dem **Projektmappen-Explorer** , indem Sie in Visual C# auf **Form1.cs** oder in Visual Basic auf **Form1.vb** doppelklicken, oder wählen Sie in der Menüleiste **Ansicht**, **Designer**aus.

     Im Folgenden sehen Sie den neuen Code, der im Code-Editor angezeigt wird.

     [!code-csharp[VbExpressTutorial1Step6#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step6#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb#2)]

     Die fünf Methoden, die Sie hinzugefügt haben, werden als *Ereignishandler*bezeichnet, da das Programm sie immer dann aufruft, wenn ein Ereignis eintritt (wenn z. B. ein Benutzer eine Schaltfläche auswählt oder ein Kontrollkästchen aktiviert).

     Wenn Sie den Code für ein Steuerelement in der IDE zur Entwurfszeit anzeigen, fügt Visual Studio für dieses Steuerelement eine Ereignishandlermethode hinzu, wenn keine vorhanden ist. Wenn Sie z. B. auf eine Schaltfläche doppelklicken, fügt die IDE einen Ereignishandler für das Click-Ereignis hinzu (dieser wird jedes Mal aufgerufen, wenn der Benutzer die Schaltfläche auswählt). Wenn Sie auf ein Kontrollkästchen doppelklicken, fügt die IDE einen Ereignishandler für das CheckedChanged-Ereignis hinzu (dieser wird jedes Mal aufgerufen, wenn der Benutzer das Kontrollkästchen aktiviert oder deaktiviert).

     Nachdem Sie für ein Steuerelement einen Ereignishandler hinzugefügt haben, können Sie jederzeit vom Windows Forms-Designer aus zum Steuerelement zurückkehren, indem Sie auf das Steuerelement doppelklicken oder in der Menüleiste **Ansicht**, **Code**auswählen.

     Namen sind wichtig, wenn Sie Programme erstellen, und für Methoden (und Ereignishandler) können Sie beliebige Namen verwenden. Wenn Sie mit der IDE einen Ereignishandler hinzufügen, erstellt die IDE basierend auf dem Namen des Steuerelements und des behandelten Ereignisses einen Namen. Das Click-Ereignis für eine Schaltfläche mit dem Namen **showButton** wird z. B. als `showButton_Click()` -Ereignishandlermethode bezeichnet. Normalerweise werden nach dem Methodennamen auch eine öffnende und eine schließende runde Klammer () hinzugefügt, um anzuzeigen, dass es sich um Methoden handelt. Wenn Sie einen Codevariablennamen ändern möchten, klicken Sie mit der rechten Maustaste auf die Variable im Code, und wählen Sie dann **Umgestalten**, **Umbenennen**aus. Alle Instanzen dieser Variable im Code werden umbenannt. Weitere Informationen finden Sie unter [Rename Refactoring (c#)](../csharp-ide/rename-refactoring-csharp.md) oder [Refactoring und Umbenennen (Dialog Feld](https://msdn.microsoft.com/library/001d2d81-9bb6-4e8e-ae3a-20c0daaa3959) ).

### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Um zum nächsten Schritt des Tutorials zu wechseln, klicken Sie auf [Schritt 7: Hinzufügen von Dialog Feld Komponenten zu Ihrem Formular](../ide/step-7-add-dialog-components-to-your-form.md).

- Um zum vorherigen Tutorialschritt zurückzukehren, finden Sie unter [Schritt 5: Hinzufügen von Steuerelementen zum Formular](../ide/step-5-add-controls-to-your-form.md).
