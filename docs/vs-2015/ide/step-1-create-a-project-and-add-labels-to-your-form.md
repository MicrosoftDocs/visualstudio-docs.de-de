---
title: 'Schritt 1: Erstellen eines Projekts und Hinzufügen von Bezeichnungen zum Formular | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2a13d96d8932a3a9e4628f2d0e67a28869252c95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667359"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>Schritt 1: Erstellen eines Projekts und Hinzufügen von Bezeichnungen zum Formular
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wie in den ersten Schritten zur Entwicklung dieses Quiz erstellen Sie das Projekt und fügen einem Formular Bezeichnungen, eine Schaltfläche und weitere Steuerelemente hinzu. Außerdem legen Sie Eigenschaften für jedes Steuerelement fest, das Sie hinzufügen. Das Projekt enthält das Formular, die Steuerelemente und (später im Lernprogramm) den Code. Das Quiz wird mit der Schaltfläche gestartet, die Bezeichnungen stellen die Quizaufgaben dar und die anderen Steuerelemente zeigen die Quizantworten und die Zeit an, die bis zum Abschluss des Quiz verbleibt.

> [!NOTE]
> Dieses Thema ist Teil einer Reihe von Lernprogrammen zu grundlegenden Konzepte der Codierung. Eine Übersicht über das Tutorial finden Sie unter [Tutorial 2: Erstellen eines mathematischen Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md)mit Zeitüberschreitung.

### <a name="to-create-a-project-and-set-properties-for-a-form"></a>So erstellen Sie ein Projekt und legen Eigenschaften für ein Formular fest

1. Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.

2. Wählen Sie in der Liste **Installierte Vorlagen** entweder **C#** oder **Visual Basic** aus.

3. Wählen Sie in der Liste der Vorlagen die Vorlage **Windows Forms-Anwendung** aus, benennen Sie sie mit **Mathequiz**, und wählen Sie anschließend die Schaltfläche **OK** aus.

     Je nach der gewählten Programmiersprache wird ein Formular mit dem Namen **Form1.cs** oder **Form1.vb** angezeigt.

4. Wählen Sie das Formular aus, und ändern Sie dann die Eigenschaft **Text** in **Mathequiz**.

     Das Fenster **Eigenschaften** enthält Eigenschaften für das Formular.

5. Ändern Sie die Größe des Formulars in eine Breite von 500 Pixeln und eine Höhe von 400 Pixeln.

     Sie können die Größe des Formulars ändern, indem Sie die Ränder ziehen, bis die richtige Größe in der unteren linken Ecke der integrierten Entwicklungsumgebung (IDE) angezeigt wird. Alternativ können Sie die Werte der Eigenschaft **Größe** ändern.

6. Ändern Sie den Wert der Eigenschaft **FormBorderStyle** in **Fixed3D**, und legen Sie die Eigenschaft **MaximizeBox** auf **False** fest.

     Mit diesen Werte wird verhindert, dass Quizteilnehmer die Größe des Formulars ändern.

### <a name="to-create-the-time-remaining-box"></a>So erstellen Sie Feld "Verbleibende Zeit"

1. Fügen Sie ein **Label**-Steuerelement aus der Toolbox hinzu, und legen Sie dann den Wert der Eigenschaft **(Name)** auf `timeLabel` fest.

     Diese Bezeichnung wird zu einem Feld in der rechten oberen Ecke, in dem die Anzahl von Sekunden angezeigt, die im Quiz verbleiben.

2. Ändern Sie die **AutoSize**-Eigenschaft in **False**, damit Sie die Größe des Felds selbst anpassen können.

3. Ändern Sie die **BorderStyle**-Eigenschaft in **FixedSingle**, um eine Linie um das Feld zu zeichnen.

4. Legen Sie die Eigenschaft **Größe** auf **200, 30** fest.

5. Verschieben Sie die Bezeichnung in die rechte obere Ecke des Formulars, wo die blauen Abstandshalterlinien erscheinen.

     Anhand dieser Zeilen können Sie die Steuerelemente im Formular ausrichten.

6. Wählen Sie im Fenster **Eigenschaften** die Eigenschaft **Text** aus, und löschen Sie den Wert mit der RÜCKTASTE.

7. Wählen Sie das Pluszeichen (+) neben der Eigenschaft **Schriftart** aus, und ändern Sie dann den Wert der Eigenschaft **Größe** in **15,75**.

     Sie können einige Schriftarteigenschaften ändern, wie im folgenden Bild gezeigt.

     ![Eigenschaftenfenster mit Schriftart Größe](../ide/media/express-setfontsize.png "Express_setFontSize") Eigenschaftenfenster mit Schriftart Größe

8. Fügen Sie ein weiteres **Label** -Steuerelement aus der Toolbox hinzu, und legen Sie dessen Schriftgröße auf **15,75**fest.

9. Legen Sie die **Text**-Eigenschaft auf **Time Left** fest.

10. Verschieben Sie die Bezeichnung, sodass sie direkt links von der Bezeichnung **timeLabel** angeordnet ist.

### <a name="to-add-controls-for-the-addition-problems"></a>So fügen Sie Steuerelemente für die Additionsaufgabe hinzu

1. Fügen Sie ein **Label** -Steuerelement aus der Toolbox hinzu, und legen Sie dessen **Text** -Eigenschaft auf **?** fest. (Fragezeichen).

2. Legen Sie die **AutoSize**-Eigenschaft auf **False** fest.

3. Legen Sie die Eigenschaft **Größe** auf **60, 50** fest.

4. Legen Sie den Schriftgrad auf **18** fest.

5. Legen Sie die Eigenschaft **TextAlign** auf **MiddleCenter** fest.

6. Legen Sie die **Location**-Eigenschaft auf **50, 75** fest, um das Steuerelement auf dem Formular zu positionieren.

7. Legen Sie die Eigenschaft **(Name)** auf **plusLeftLabel** fest.

8. Wählen Sie die Bezeichnung **PlusLeftLabel** aus, und wählen Sie dann entweder die Tasten STRG + C oder **Kopieren** im Menü **Bearbeiten** aus.

9. Fügen Sie die Bezeichnung dreimal ein, indem Sie entweder die Tastenkombination STRG + V oder **Einfügen** im Menü **Bearbeiten** auswählen.

10. Ordnen Sie die drei neuen Bezeichnungen so an, dass sie in einer Zeile auf der rechten Seite der Bezeichnung **plusLeftLabel** stehen.

     Mithilfe der Abstandshalterlinie können Sie die Steuerelemente verteilen und ausrichten.

11. Legen Sie den Wert der **Text**-Eigenschaft der zweiten Bezeichnung auf **+** (Pluszeichen) fest.

12. Legen Sie den Wert der **(Name)**-Eigenschaft der dritten Bezeichnung auf **plusRightLabel** fest.

13. Legen Sie den Wert der **Text**-Eigenschaft der vierten Bezeichnung auf **=** (Gleichheitszeichen) fest.

14. Fügen Sie ein **NumericUpDown**-Steuerelement aus der Toolbox hinzu, legen Sie den Schriftgrad auf **18** fest, und legen Sie seine Breite auf **100** fest.

     Später erfahren Sie mehr über diese Art Steuerelement.

15. Richten Sie das **NumericUpDown** -Steuerelement mit den Label-Steuerelementen für die Additions Aufgabe aus.

16. Ändern Sie den Wert der **(Name)** -Eigenschaft für das **NumericUpDown** -Steuerelement in **Sum**.

     Sie haben die erste Zeile erstellt, wie im folgenden Bild dargestellt.

     ![Erste Zeile des Mathetests](../ide/media/express-firstrow.png "Express_firstRow") Erste Zeile des Mathetests

### <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>So fügen Sie weitere Steuerelemente für die Subtraktion-, Multiplikations- und Divisionsaufgaben hinzu

1. Kopieren Sie alle fünf Steuerelemente für die Additionsaufgabe (die vier Label-Steuerelemente und das NumericUpDown-Steuerelement), und fügen Sie sie ein.

     Das Formular enthält fünf neue Steuerelemente, die immer noch ausgewählt sind.

2. Verschieben Sie alle Steuerelemente an die vorgesehene Position, sodass sie unter den Steuerelementen für die Addition ausgerichtet sind.

     Mithilfe der Abstandshalterlinien können Sie ausreichend Platz zwischen den beiden Zeilen lassen.

3. Ändern Sie den Wert der Eigenschaft **Text** für die zweite Bezeichnung in **-** (Minuszeichen).

4. Benennen Sie die erste Bezeichnung mit dem Fragezeichen **minusLeftLabel**.

5. Benennen Sie die zweite Bezeichnung mit dem Fragezeichen **minusRightLabel**.

6. Benennen **Sie den NumericUpDown** -Steuerelement **Unterschied**.

7. Fügen Sie die fünf Steuerelemente zwei weitere Male ein.

8. Führen Sie für die dritte Zeile folgende Schritte aus: Benennen Sie die erste Bezeichnung **timesLeftLabel**, ändern Sie die **Text**-Eigenschaft der zweiten Bezeichnung in **×** (Multiplikationszeichen), benennen Sie die dritte Bezeichnung **timesRightLabel**, und benennen Sie das NumericUpDown-Steuerelement **Produkt**.

9. Führen Sie für die vierte Zeile folgende Schritte aus: Nennen Sie die erste Bezeichnung **dividedLeftLabel**, ändern Sie die **Text**-Eigenschaft der zweiten Eigenschaft in **÷** (Divisionszeichen), nennen Sie die dritte Bezeichnung **dividedRightLabel**, und nennen Sie das NumericUpDown-Steuerelement **Quotient**.

    > [!NOTE]
    > Sie können das Multiplikationszeichen × und das Divisionszeichen ÷ aus diesem Lernprogramm kopieren und in das Formular einfügen.

### <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>So fügen Sie einen Startknopf hinzu und legen die Aktivierreihenfolge fest

1. Fügen Sie aus der Toolbox ein **Schaltfläche**-Steuerelement hinzu, und legen Sie dessen Eigenschaft **(Name)** auf **startButton** fest.

2. Legen Sie die **Text**-Eigenschaft auf **Quiz starten** fest.

3. Legen Sie den Schriftgrad auf **14** fest.

4. Legen Sie die Eigenschaft **AutoSize** auf **True** fest. Dies bewirkt, dass die Größe der Schaltfläche automatisch an die Textlänge angepasst wird.

5. Zentrieren Sie die Schaltfläche am unteren Rand des Formulars.

6. Legen Sie den Wert der **TabIndex**-Eigenschaft für das **startButton**-Steuerelement auf **1** fest.

    > [!NOTE]
    > Mit der Eigenschaft **TabIndex** wird die Reihenfolge der Steuerelemente festgelegt, wenn der Quizteilnehmer die TAB-TASTE drückt. Um zu sehen, wie dies funktioniert, öffnen Sie ein beliebiges Dialogfeld (wählen Sie z. B. in der Menüleiste **Datei**, **Öffnen** aus), und drücken Sie dann mehrmals die TAB-TASTE. Beobachten Sie, wie der Cursor jedes Mal, wenn Sie die TAB-TASTE auswählen, von Steuerelement zu Steuerelement springt. Ein Programmierer hat diese Reihenfolge beim Erstellen des Formulars festgelegt.

7. Legen Sie den Wert der Eigenschaft **TabIndex** für das NumericUpDown-Steuerelement „Summe“ auf **2**, für das Differenzsteuerelement auf **3**, für das Produktsteuerelement auf **4** und für das Quotientsteuerelement auf **5** fest.

     Das fertige Formular sollte der folgenden Abbildung ähneln.

     ![Anfängliches Formular für den Mathetest](../ide/media/express-formlaidout.png "Express_FormLaidOut") Anfängliches Formular für den Mathetest

8. Um sicherzustellen, dass die Eigenschaft **TabIndex** wie erwartet funktioniert, speichern das Programm, und führen Sie es durch Auswählen der F5-TASTE oder der Optionen **Debuggen**, **Debuggen starten** in der Menüleiste aus, und wählen Sie dann die TAB-TASTE einige Male aus.

### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Um zum nächsten Schritt des Tutorials zu wechseln, klicken Sie auf [Schritt 2: Erstellen einer zufälligen Additions Aufgabe](../ide/step-2-create-a-random-addition-problem.md).

- Weitere Informationen zum Übersichts Thema finden Sie unter [Tutorial 2: Erstellen eines mathematischen Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md)mit Zeitüberschreitung.
