---
title: 'Schritt 7: Hinzufügen von Dialogfeldkomponenten zum Formular | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40b90096f768a7dd836507c83dff935261a99a25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851140"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Schritt 7: Hinzufügen von Dialogfeldkomponenten zum Formular
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Schritt fügen Sie dem Formular eine **OpenFileDialog**- und eine **ColorDialog**-Komponente hinzu, damit das Programm Bilddateien öffnen und eine Hintergrundfarbe auswählen kann.

 Eine Komponente ist in gewisser Hinsicht mit einem Steuerelement vergleichbar. Sie fügen dem Formular mithilfe der Toolbox eine Komponente hinzu, und legen die Eigenschaften im **Eigenschaftenfenster** fest. Aber im Gegensatz zu einem Steuerelement wird dem Formular beim Hinzufügen einer Komponente kein für den Benutzer sichtbares Element hinzugefügt. Stattdessen stellt die Komponente bestimmte Verhalten bereit, die Sie mit Code auslösen können. Es handelt sich dabei um eine Komponente, die das Dialogfeld **Datei öffnen** anzeigt.

 ![Link zu Video](../data-tools/media/playvideo.gif "Wiedergeben") Eine videoversion dieses Themas finden Sie im Video 3 zum [Tutorial 1: Erstellen eines Bild Anzeige Programms in Visual Basic-Video 3](https://msdn.microsoft.com/vbasic/gg315354.aspx) oder [Tutorial 1: Erstellen eines Bild Anzeige Programms in c#](https://msdn.microsoft.com/vcsharp/gg278411.aspx). Diese Videos verwenden eine frühere Version von Visual Studio, sodass Menübefehle und andere Benutzeroberflächenelemente geringfügig abweichen können. Allerdings funktionieren die Konzepte und Prozeduren in der aktuellen Version von Visual Studio auf ähnliche Weise.

### <a name="to-add-dialog-components-to-your-form"></a>So fügen Sie dem Formular Dialogfeldkomponenten hinzu

1. Wählen Sie den Windows Forms-Designer (Form1.cs [Entwurf] oder Form1.vb [Entwurf]) aus, und öffnen Sie dann die Gruppe **Dialogfelder** in der Toolbox.

    > [!NOTE]
    > Die Gruppe **Dialogfelder** in der Toolbox verfügt über Komponenten zum Öffnen vieler nützlicher Dialogfelder, die z.B. zum Öffnen und Speichern von Dateien, Durchsuchen von Ordnern und Auswählen von Schriftarten und Farben verwendet werden können. Sie verwenden in diesem Projekt zwei Dialogfeldkomponenten: **OpenFileDialog** und **ColorDialog**.

2. Doppelklicken Sie auf **OpenFileDialog**, um dem Formular eine Komponente mit dem Namen **openFileDialog1** hinzuzufügen. Doppelklicken Sie in der Toolbox auf **ColorDialog**, um dem Formular eine Komponente mit dem Namen **colorDialog1** hinzuzufügen. (Sie verwenden diese im nächsten Schritt des Tutorials.) Unten in Windows Forms-Designer sollte ein Bereich angezeigt werden (unterhalb des Bild Anzeige Formulars), das ein Symbol für jede der beiden hinzugefügten Dialogfeld Komponenten enthält, wie in der folgenden Abbildung dargestellt.

     ![Dialog Feld Komponenten](../ide/media/express-dialogsadded.png "Express_DialogsAdded") Dialog Feld Komponenten

3. Wählen Sie das Symbol **openFileDialog1** im unteren Bereich des Windows Forms-Designer aus. Legen Sie zwei Eigenschaften fest:

    - Legen Sie die Eigenschaft **Filter** auf Folgendes fest (Sie können den Code kopieren und einfügen):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Legen Sie die **Title**-Eigenschaft auf Folgendes fest: **Select a picture file** („Bilddatei auswählen“).

         Die Eigenschafteneinstellungen für **Filter** geben die Arten von Dateitypen an, die im Dateidialogfeld **Select a picture** („Bilddatei auswählen“) angezeigt werden.

    > [!NOTE]
    > Öffnen Sie Editor oder Paint, und wählen Sie in der Menüleiste **Datei** > **Öffnen** aus, um ein Beispiel für das Dialogfeld **Datei öffnen** in einer anderen Anwendung zu sehen. Im unteren Bereich befindet sich die Dropdownliste **Dateityp**. Sie haben soeben die **Filter**-Eigenschaft in der **OpenFileDialog**-Komponente verwendet, um diese Dropdownliste einzurichten. Beachten Sie auch, dass die Eigenschaften **Title** und **Filter** im **Eigenschaftenfenster** fett sind. Hierdurch kennzeichnet die IDE alle Eigenschaften, deren Standardwerte geändert wurden.

### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Klicken Sie auf [Schritt 8: Schreiben von Code für den Ereignishandler der Schaltfläche „Build anzeigen“](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md), um zum nächsten Tutorialschritt zu gelangen.

- Klicken Sie auf [Schritt 6: Benennen der Schaltflächen-Steuerelemente](../ide/step-6-name-your-button-controls.md), um zum vorherigen Schritt des Tutorials zurückzugehen.
