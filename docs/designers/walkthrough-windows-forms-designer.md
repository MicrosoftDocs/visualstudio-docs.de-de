---
title: Übersicht über Windows Forms-Designer – Tutorial
description: Hier erfahren Sie, wie Sie eine App mithilfe der verschiedenen Tools erstellen, die vom Windows Forms-Designer bereitgestellt werden. Die App ist ein benutzerdefiniertes Steuerelement, das viele verfügbare Layoutfeatures nutzt.
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: tutorial
helpviewer_keywords:
- Windows Forms Designer, get started
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: d4d3c0965d638c9e048cef29d7f1b535a54e54a5
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493477"
---
# <a name="tutorial-get-started-with-windows-forms-designer"></a>Tutorial: Erste Schritte mit dem Windows Forms-Designer

Der Windows Forms-Designer stellt viele Tools zum Entwickeln von Windows Forms-Anwendungen bereit. In diesem Artikel wird veranschaulicht, wie Sie eine App mit den verschiedenen vom Designer bereitgestellten Tools erstellen, einschließlich der folgenden Aufgaben:

- Anordnen von Steuerelementen mithilfe von Ausrichtungslinien.
- Ausführen von Sie Designeraufgaben mit Smarttags.
- Festlegen von Rändern und Abständen für Steuerelemente.
- Anordnen von Steuerelementen mithilfe eines <xref:System.Windows.Forms.TableLayoutPanel>-Steuerelements.
- Partitionieren des Layouts Ihrer Steuerelemente mithilfe eines <xref:System.Windows.Forms.SplitContainer>-Steuerelements.
- Navigieren im Layout mit dem Fenster „Dokumentgliederung“.
- Positionieren von Steuerelementen mit angezeigten Informationen zu Größe und Speicherort.
- Festlegen von Eigenschaftswerten im Eigenschaftenfenster.

Nach Fertigstellung erhalten Sie ein benutzerdefiniertes Steuerelement, das mit vielen der im Windows Forms-Designer verfügbaren Layoutfunktionen zusammengestellt wurde. Dieses Steuerelement implementiert die Benutzeroberfläche (UI) für einen einfachen Rechner. In der folgenden Abbildung ist das allgemeine Layout des Steuerelements für den Rechner dargestellt:

![Oberfläche zur Rechner-Einführung](media/calculator-ui.gif)

## <a name="create-the-custom-control-project"></a>Erstellen des Projekts für das benutzerdefinierte Steuerelement

Der erste Schritt besteht darin, das DemoCalculator-Steuerelementprojekt zu erstellen.

1. Öffnen Sie Visual Studio, und erstellen ein neues Projekt **Windows Forms-Steuerelementbibliothek**. Nennen Sie das Projekt **DemoCalculatorLib**.

   ::: moniker range=">=vs-2019"

   ![Vorlage „Windows Forms-Steuerelementbibliothek“ in Visual Studio 2019](media/windows-forms-control-library-template.png)

   ::: moniker-end

2. Um die Datei umzubenennen, klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **UserControl1.vb** oder **UserControl1.cs**, wählen Sie **Umbenennen** aus, und ändern Sie den Dateinamen in „DemoCalculator.vb“ oder „DemoCalculator.cs“. Wählen Sie **Ja** aus, wenn Sie gefragt werden, ob alle Verweise auf das Codeelement „UserControl1“ umbenannt werden sollen.

Der Windows Forms-Designer zeigt die Designeroberfläche für das DemoCalculator-Steuerelement an. In dieser Ansicht können Sie das Aussehen des Steuerelements grafisch gestalten, indem Sie Steuerelemente und Komponenten aus der Toolbox auswählen und auf der Designeroberfläche platzieren. Weitere Informationen zu benutzerdefinierten Steuerelementen finden Sie unter [Varianten von benutzerdefinierten Steuerelementen](/dotnet/framework/winforms/controls/varieties-of-custom-controls).

## <a name="design-the-control-layout"></a>Entwerfen des Steuerelementlayouts

Das DemoCalculator-Steuerelement enthält mehrere Windows Forms-Steuerelemente. In dieser Prozedur ordnen Sie die Steuerelemente mithilfe des Windows Forms-Designers an.

1. Vergrößern Sie das DemoCalculator-Steuerelement im Windows Forms-Designer, indem Sie den Größenziehpunkt in der unteren rechten Ecke auswählen und ihn nach unten und rechts ziehen. In der rechten unteren Ecke von Visual Studio sehen Sie Informationen zur Größe und den Speicherort für Steuerelemente. Stellen Sie die Größe des Steuerelements auf Breite 500 und Höhe 400 ein, indem Sie beim Ändern der Größe des Steuerelements die Größeninformationen beobachten.

2. Wählen Sie in der **Toolbox** den Knoten **Container** aus, um ihn zu öffnen. Wählen Sie das **SplitContainer**-Steuerelement aus, und ziehen Sie es auf die Designeroberfläche.

   `SplitContainer` wird auf der Designeroberfläche des DemoCalculator-Steuerelements platziert.

    > [!TIP]
    > Das `SplitContainer`-Steuerelement passt sich selbst der Größe des DemoCalculator-Steuerelements an. Im **Eigenschaftenfenster** finden Sie die Eigenschaftseinstellungen für das `SplitContainer`-Steuerelement. Suchen Sie die <xref:System.Windows.Forms.SplitContainer.Dock%2A>-Eigenschaft. Der Wert ist [DockStyle.Fill](xref:System.Windows.Forms.DockStyle.Fill). Das bedeutet, dass sich das `SplitContainer`-Steuerelement immer an die Begrenzungen des DemoCalculator-Steuerelements anpassen wird. Ändern Sie die Größe des DemoCalculator-Steuerelements, um dieses Verhalten zu überprüfen.

3. Ändern Sie den Wert der <xref:System.Windows.Forms.SplitContainer.Dock%2A>-Eigenschaft im **Eigenschaftenfenster** in `None`.

    Das `SplitContainer`-Steuerelement wird auf die Standardgröße verkleinert und folgt nicht mehr der Größe des DemoCalculator-Steuerelements.

4. Wählen Sie die Smarttag-Glyphe (![Smarttag-Glyphe](media/smart-tag-glyph.gif)) in der oberen rechten Ecke des `SplitContainer`-Steuerelements aus. Wählen Sie **In übergeordnetem Container andocken**, um die `Dock`-Eigenschaft auf `Fill` festzulegen.

    Das `SplitContainer`-Steuerelement wird an die Begrenzungen des DemoCalculator-Steuerelements angedockt.

    > [!NOTE]
    > Mehrere Steuerelemente bieten Smarttags zum Vereinfachen des Entwurfs. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Ausführen von häufigen Aufgaben mit Smarttags für Windows Forms-Steuerelemente](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls).

5. Klicken Sie auf die vertikale Begrenzung zwischen den Panels, und ziehen Sie diese nach rechts, sodass das linke Panel den größten Raum einnimmt.

    `SplitContainer` teilt das DemoCalculator-Steuerelement in zwei Panels mit einem verschiebbaren Rand dazwischen. Das linke Panel enthält die Rechnerschaltflächen und die Anzeige, und das rechte Panel zeigt einen Datensatz der vom Benutzer durchgeführten arithmetischen Operationen.

6. Ändern Sie den Wert der `BorderStyle`-Eigenschaft im **Eigenschaftenfenster** in `Fixed3D`.

7. Wählen Sie in der **Toolbox** den Knoten **Allgemeine Steuerelemente** aus, um ihn zu öffnen. Wählen Sie das `ListView`-Steuerelement aus, und ziehen Sie es in das rechte Panel des `SplitContainer`-Steuerelements.

8. Wählen Sie die Smarttag-Glyphe des `ListView`-Steuerelements aus. Ändern Sie die `View`-Einstellung im Smarttagpanel in `Details`.

9. Wählen Sie im Smarttagpanel **Spalten bearbeiten** aus.

   Das Dialogfeld **ColumnHeader-Auflistungs-Editor** wird geöffnet.

10. Wählen Sie im Dialogfeld **ColumnHeader-Auflistungs-Editor** **Hinzufügen** aus,um dem `ListView`-Steuerelement eine Spalte hinzuzufügen. Ändern Sie den Wert der `Text`-Eigenschaft der Spalte in **Verlauf**. Klicken Sie auf **OK**, um die Spalte zu erstellen.

11. Wählen Sie im Smarttagpanel die Option **In übergeordnetem Container andocken** und dann die Smarttag-Glyphe aus, um das Smarttagpanel zu schließen.

12. Ziehen Sie ein `TableLayoutPanel`-Steuerelement aus der **Toolbox** im Knoten **Container** in das linke Panel des `SplitContainer`-Steuerelements.

    Das `TableLayoutPanel`-Steuerelement wird auf der Designeroberfläche mit geöffnetem Smarttagpanel angezeigt. Das `TableLayoutPanel`-Steuerelement ordnet seine untergeordneten Steuerelemente in einem Rasterlayout an. Das `TableLayoutPanel`-Steuerelement enthält die Anzeige und die Schaltflächen des DemoCalculator-Steuerelements. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anordnen von Steuerelementen mithilfe von TableLayoutPanel](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel).

13. Wählen Sie im Smarttagpanel **Zeilen und Spalten bearbeiten** aus.

    Das Dialogfeld **Spalten- und Zeilenstile** wird geöffnet.

14. Wählen Sie die Schaltfläche **Hinzufügen**, bis fünf Spalten angezeigt werden. Wählen Sie alle fünf Spalten aus, und wählen Sie dann im Feld **Größentyp** die Option **Prozent** aus. Legen Sie den **Prozentwert** auf **20** fest. Damit wird für jede Spalte die gleiche Breite festgelegt.

15. Wählen Sie unter **Anzeigen** die Option **Zeilen** aus.

16. Wählen Sie **Hinzufügen**, bis fünf Zeilen angezeigt werden. Wählen Sie alle fünf Zeilen aus, und wählen Sie dann im Feld **Größentyp** die Option **Prozent** aus. Legen Sie den **Prozentwert** auf **20** fest. Damit wird für Zeile dieselbe Höhe festgelegt.

17. Wählen Sie **OK** aus, um Ihre Änderungen zu übernehmen, und dann die Smarttag-Glyphe, um das Smarttagpanel zu schließen.

18. Ändern Sie den Wert der `Dock`-Eigenschaft im **Eigenschaftenfenster** in `Fill`.

## <a name="populate-the-control"></a>Ausfüllen des Steuerelements

Nachdem das Layout des Steuerelements eingerichtet ist, können Sie das Steuerelement des DemoCalculators mit Schaltflächen und einer Anzeige füllen.

1. Wählen Sie in der **Toolbox** das `TextBox`-Steuerelementsymbol aus.

   Ein `TextBox`-Steuerelement wird in der ersten Zelle des `TableLayoutPanel`-Steuerelements platziert.

2. Ändern Sie den Wert der ColumnSpan-Eigenschaft des `TextBox`-Steuerelements im **Eigenschaftenfenster** in **5**.

   Das `TextBox`-Steuerelement wechselt zu einer Position, die in seiner Zeile zentriert ist.

3. Ändern Sie den Wert der `Anchor`-Eigenschaft des `TextBox`-Steuerelements in `Left`, `Right`.

   Das `TextBox`-Steuerelement wird horizontal erweitert und umfasst anschließend alle fünf Spalten.

4. Ändern Sie den Wert der `TextBox` -Eigenschaft des `TextAlign` -Steuerelements in `Right`.

5. Erweitern Sie im **Eigenschaftenfenster** den `Font`-Eigenschaftsknoten. Legen Sie für das `TextBox`-Steuerelement `Size` auf **14** und `Bold` auf **True** fest.

6. Wählen Sie das `TableLayoutPanel`-Steuerelement.

7. Wählen Sie in der **Toolbox** das `Button`-Symbol aus.

   Ein `Button`-Steuerelement wird in der nächsten offenen Zelle des `TableLayoutPanel`-Steuerelements platziert.

8. Wählen Sie in der **Toolbox** vier weitere Male das `Button`-Symbol aus, um die zweite Zeile des `TableLayoutPanel`-Steuerelements aufzufüllen.

9. Markieren Sie alle fünf `Button`-Steuerelemente, indem Sie sie auswählen, während Sie die **UMSCHALTTASTE** gedrückt halten. Drücken Sie **STRG**+**C**, um die `Button`-Steuerelemente in die Zwischenablage zu kopieren.

10. Drücken Sie drei Mal **STRG**+**V**, um Kopien der `Button`-Steuerelemente in die verbleibenden Zeilen des `TableLayoutPanel`-Steuerelements einzufügen.

11. Markieren Sie alle 20 `Button`-Steuerelemente, indem Sie sie auswählen, während Sie die **UMSCHALTTASTE** gedrückt halten.

12. Ändern Sie den Wert der `Dock`-Eigenschaft im **Eigenschaftenfenster** in `Fill`.

    Alle `Button`-Steuerelemente docken an, um ihre enthaltenen Zellen zu füllen.

13. Erweitern Sie im **Eigenschaftenfenster** den `Margin`-Eigenschaftsknoten. Legen Sie den Wert von `All` auf **5** fest.

    Alle `Button`-Steuerelemente sind kleiner ausgelegt, um einen breiteren Rand zwischen ihnen zu schaffen.

14. Wählen Sie **button10** und **button20**, und drücken Sie dann auf **Löschen**, um sie aus dem Layout zu entfernen.

15. Wählen Sie **button5** und **button15**, und ändern Sie dann den Wert der `RowSpan`-Eigenschaft in **2**. Dies sind die Schaltflächen **Löschen** und **=** für die DemoCalculator-Schaltfläche.

## <a name="use-the-document-outline-window"></a>Verwenden des Fensters „Dokumentgliederung“

Wenn Ihr Steuerelement oder Formular mit mehreren Steuerelementen gefüllt ist, ist es möglicherweise einfacher, mit dem Fenster „Dokumentgliederung“ durch Ihr Layout zu navigieren.

1. Wählen Sie in der Menüleiste **Ansicht** > **Weitere Fenster** > **Dokumentgliederung**.

   Das Fenster „Dokumentgliederung“ zeigt eine Strukturansicht des DemoCalculator-Steuerelements und der zugehörigen Steuerelemente an. Containersteuerelemente wie `SplitContainer` zeigen ihre untergeordneten Steuerelemente als Unterknoten in der Struktur an. Über das Fenster „Dokumentgliederung“ können Sie vorhandene Steuerelemente auch umbenennen.

2. Klicken Sie im Fenster **Dokumentgliederung** mit der rechten Maustaste auf **button1**, und wählen Sie dann **Umbenennen** aus. Ändern Sie den Namen in „sevenButton“.

3. Benutzen Sie das Fenster **Dokumentgliederung**, um die `Button`-Steuerelemente vom vom Designer generierten Namen gemäß der folgenden Liste in den Produktionsnamen umzubenennen:

   - button1 in **sevenButton**

   - button2 in **eightButton**

   - button3 in **nineButton**

   - button4 in **divisionButton**

   - button5 in **clearButton**

   - button6 in **fourButton**

   - button7 in **fiveButton**

   - button8 in **sixButton**

   - button9 in **multiplicationButton**

   - button11 in **oneButton**

   - button12 in **twoButton**

   - button13 in **threeButton**

   - button14 in **subtractionButton**

   - button15 in **equalsButton**

   - button16 in **zeroButton**

   - button17 in **changeSignButton**

   - button18 in **decimalButton**

   - button19 in **additionButton**

4. Ändern Sie im Fenster **Dokumentengliederung** und im **Eigenschaftenfenster** den `Text`-Eigenschaftswert für jeden `Button`-Steuerelementnamen gemäß der folgenden Liste:

   - Ändern Sie die Texteigenschaft des sevenButton-Steuerelements in **7**.

   - Ändern Sie die Texteigenschaft des eightButton-Steuerelements in **8**.

   - Ändern Sie die Texteigenschaft des nineButton-Steuerelements in **9**.

   - Ändern Sie die Texteigenschaft des divisionButton-Steuerelements in **/** (Schrägstrich).

   - Ändern Sie die Texteigenschaft des clearButton-Steuerelements in **Löschen**.

   - Ändern Sie die Texteigenschaft des fourButton-Steuerelements in **4**.

   - Ändern Sie die Texteigenschaft des fiveButton-Steuerelements in **5**.

   - Ändern Sie die Texteigenschaft des sixButton-Steuerelements in **6**.

   - Ändern Sie die Texteigenschaft des multiplicationButton-Steuerelements in * *\** _ (Sternchen).

   - Ändern Sie die Texteigenschaft des oneButton-Steuerelements in _ *1**.

   - Ändern Sie die Texteigenschaft des twoButton-Steuerelements in **2**.

   - Ändern Sie die Texteigenschaft des threeButton-Steuerelements in **3**.

   - Ändern Sie die Texteigenschaft des subtractionButton-Steuerelements in **-** (Bindestrich).

   - Ändern Sie die Texteigenschaft des equalsButton-Steuerelements in **=** (Gleichheitszeichen).

   - Ändern Sie die Texteigenschaft des zeroButton-Steuerelements in **0**.

   - Ändern Sie die Texteigenschaft des changeSignButton-Steuerelements in **+/-** .

   - Ändern Sie die Texteigenschaft des decimalButton-Steuerelements in **.** (Punkt).

   - Ändern Sie die Texteigenschaft des additionButton-Steuerelements in **+** (Pluszeichen).

5. Wählen Sie in der Designeroberfläche alle `Button`-Steuerelemente, indem Sie sie auswählen, während Sie die **UMSCHALTTASTE** gedrückt halten.

6. Erweitern Sie im **Eigenschaftenfenster** den `Font`-Eigenschaftsknoten. Legen Sie für alle `Button`-Steuerelemente `Size` auf **14** und `Bold` auf **True** fest.

Damit ist der Entwurf des DemoCalculator-Steuerelements abgeschlossen. Es muss nur noch die Rechnerlogik bereitgestellt werden.

## <a name="implement-event-handlers"></a>Implementieren von Ereignishandlern

Die Schaltflächen im DemoCalculator-Steuerelement verfügen über Ereignishandler, die zum Implementieren eines Großteil der Rechnerlogik verwendet werden können. Mit dem Windows Forms-Designer können Sie die Stubs aller Ereignishandler für alle Schaltflächen mit einer einzigen Auswahl implementieren.

1. Wählen Sie in der Designeroberfläche alle `Button`-Steuerelemente, indem Sie sie auswählen, während Sie die **UMSCHALTTASTE** gedrückt halten.

2. Wählen Sie eines der `Button`-Steuerelemente aus.

   Der Code-Editor wird mit den vom Designer generierten Ereignishandlern geöffnet.

## <a name="test-the-control"></a>Testen des Steuerelements

Da das DemoCalculator-Steuerelement von der <xref:System.Windows.Forms.UserControl>-Klasse erbt, können Sie sein Verhalten mit dem **UserControl-Testcontainer** testen. Weitere Informationen finden Sie unter [Vorgehensweise: Testen des Laufzeitverhaltens eines UserControl](/dotnet/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol).

1. Drücken Sie **F5**, um das DemoCalculator-Steuerelement im **UserControl-Testcontainer** zu erstellen und auszuführen.

2. Wählen Sie die Begrenzung zwischen den `SplitContainer`-Panels aus, und ziehen Sie sie nach links und rechts. `TableLayoutPanel` und alle untergeordneten Steuerelemente werden an den verfügbaren Platz angepasst.

3. Wenn Sie mit dem Testen des Steuerelements fertig sind, wählen Sie **Schließen** aus.

## <a name="use-the-control-on-a-form"></a>Verwenden des Steuerelements in einem Formular

Das DemoCalculator-Steuerelement kann in anderen zusammengesetzten Steuerelementen oder auf einem Formular verwendet werden. Im Folgenden wird dies näher beschrieben.

### <a name="create-the-project"></a>Erstellen eines Projekts

Im ersten Schritt erstellen Sie das Anwendungsprojekt. Damit erstellen Sie die Anwendung, die Ihr benutzerdefiniertes Steuerelement anzeigt.

1. Erstellen Sie ein neues **Windows Forms-Anwendungsprojekt**, und nennen Sie es **DemoCalculatorTest**.

2. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt **DemoCalculatorTest**, und wählen Sie **Verweis hinzufügen** aus, um das Dialogfeld **Verweis hinzufügen** zu öffnen.

3. Gehen Sie zur Registerkarte **Projekte**, und wählen Sie dann das Projekt DemoCalculatorLib aus, um den Verweis dem Testprojekt hinzuzufügen.

4. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **DemoCalculatorTest**, und wählen Sie dann **Als Startprojekt festlegen** aus.

5. Vergrößern Sie im Windows Forms-Designer das Formular auf ungefähr **700 x 500**.

### <a name="use-the-control-in-the-forms-layout"></a>Verwenden des Steuerelements im Layout des Formulars

Um das DemoCalculator-Steuerelement in einer Anwendung zu verwenden, müssen Sie es in einem Formular platzieren.

1. Erweitern Sie in der **Toolbox** den Knoten **DemoCalculatorLib-Komponenten**.

2. Ziehen Sie das **DemoCalculator**-Steuerelement aus der **Toolbox** auf das Formular. Verschieben Sie das Steuerelement in die obere linke Ecke des Formulars. Wenn sich das Steuerelement in der Nähe der Formularbegrenzungen befindet, erscheinen *Ausrichtungslinien*. Ausrichtungslinien geben den Abstand zwischen der `Padding`-Eigenschaft des Formulars und der `Margin`-Eigenschaft des Steuerelements an. Positionieren Sie das Steuerelement an der Position, die durch die Ausrichtungslinien angegeben wird.

   Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anordnen von Steuerelementen mithilfe von Ausrichtungslinien](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines).

3. Ziehen Sie ein `Button`-Steuerelement aus der **Toolbox**, und legen Sie es auf dem Formular ab.

4. Verschieben Sie das `Button`-Steuerelement um das DemoCalculator-Steuerelement, und beobachten Sie, wo die Ausrichtungslinien angezeigt werden. Mit diesem Feature können Sie die Steuerelemente genau und einfach ausrichten. Löschen Sie das `Button`-Steuerelement, wenn Sie fertig sind.

5. Klicken Sie mit der rechten Maustaste auf das DemoCalculator-Steuerelement, und wählen Sie **Eigenschaften** aus.

6. Ändern Sie den Wert der `Dock`-Eigenschaft in `Fill`.

7. Wählen Sie das Formular aus, und erweitern Sie dann den `Padding`-Eigenschaftenknoten. Ändern Sie den Wert von **Alle** in **20**.

   Die Größe des DemoCalculator-Steuerelements wird reduziert, um den neuen Wert `Padding` des Formulars zu unterstützen.

8. Ändern Sie die Größe des Formulars, indem Sie die verschiedenen Größenziehpunkte an verschiedene Positionen ziehen. Beobachten Sie, wie die Größe des DemoCalculator-Steuerelements angepasst wird.

## <a name="next-steps"></a>Nächste Schritte

In diesem Artikel wurde gezeigt, wie Sie die Benutzeroberfläche für einen einfachen Rechner erstellen. Um fortzufahren, können Sie seine Funktionalität durch Implementieren der Rechnerlogik erweitern und die [App dann mithilfe von ClickOnce veröffentlichen](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md). Oder fahren Sie mit einem anderen Tutorial fort, [in dem Sie mit Windows Forms einen Bildviewer erstellen](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Siehe auch

- [Windows Forms-Steuerelemente](/dotnet/framework/winforms/controls/)
- [Barrierefreiheit für Windows Forms-Steuerelemente](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [Veröffentlichen mithilfe von ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
