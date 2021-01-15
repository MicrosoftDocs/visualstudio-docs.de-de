---
title: Debuggen eines Windows Form-Projekts | Microsoft-Dokumentation
description: In diesem Artikel finden Sie eine exemplarische Vorgehensweise zum Erstellen und Debuggen einer Windows Forms-Anwendung. Dabei handelt es sich um eine gängige verwaltete Anwendung. Hierzu können Sie C#, Visual Basic, C++ oder F# verwenden.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31c1bc9e65eb63877d8f8a42902d8ec47a61fd22
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148091"
---
# <a name="walkthrough-debugging-a-windows-form"></a>Exemplarische Vorgehensweise: Debuggen eines Windows Forms-Projekts
Ein Windows Form ist eine der am häufigsten vorkommenden verwalteten Anwendungen. Ein solches Formular erstellt eine Windows-Standardanwendung. Sie können diese exemplarische Vorgehensweise mit Visual Basic, C# oder C++ ausführen.

 Zuerst müssen Sie alle geöffneten Projektmappen schließen.

### <a name="to-prepare-for-this-walkthrough"></a>So bereiten Sie diese exemplarische Vorgehensweise vor

- Wenn Sie bereits eine Projektmappe geöffnet haben, schließen Sie diese. (Klicken Sie im Menü **Datei** auf **Projektmappe schließen**.)

## <a name="create-a-new-windows-form"></a>Erstellen eines neuen Windows Form
 Als Nächstes erstellen Sie ein neues Windows Form.

#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>So erstellen Sie das Windows Form für diese exemplarische Vorgehensweise

1. Klicken Sie im Menü **Datei** auf **Neu** und auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Öffnen Sie im Bereich „Projekttypen“ den Knoten **Visual Basic**, **Visual C#** oder **Visual C++** . Gehen Sie anschließend wie folgt vor:

    1. Klicken Sie bei Visual Basic oder Visual C# auf **Windows Desktop** > **Windows Form-App**.

    2. Bei Visual C++ klicken Sie auf **Windows-Desktopanwendung**.

3. Geben Sie im Feld **Name** einen eindeutigen Namen für das Projekt ein (z. B. „Walkthrough_SimpleDebug“).

4. Klicken Sie auf **OK**.

     Visual Studio erstellt ein neues Projekt und zeigt ein neues Formular im Windows Forms-Designer an. Weitere Informationen finden Sie unter [Windows Forms-Designer](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\)).

5. Wählen Sie im Menü **Ansicht** die Option **Toolbox** aus.

     Die Toolbox wird geöffnet. Weitere Informationen finden Sie unter [Toolbox](../ide/reference/toolbox.md).

6. Klicken Sie in der Toolbox auf das **Button**-Steuerelement, und ziehen Sie es auf die Formularentwurfsoberfläche. Legen Sie das Steuerelement im Formular ab.

7. Klicken Sie in der Toolbox auf das **TextBox**-Steuerelement, und ziehen Sie es auf die Formularentwurfsoberfläche. Legen Sie das **TextBox**-Steuerelement im Formular ab.

8. Doppelklicken Sie auf der Formularentwurfsoberfläche auf die Schaltfläche.

     Dadurch gelangen Sie auf die Codepage. Der Cursor sollte sich nun in der `button1_Click`-Funktion befinden.

10. Fügen Sie folgenden Code in die `button1_Click`-Funktion ein:

    ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

11. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

     Das Projekt wird fehlerfrei erstellt.

## <a name="debug-your-form"></a>Debuggen des Formulars
 Jetzt können Sie mit dem Debuggen beginnen.

#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>So debuggen Sie das Windows Form, das für diese exemplarische Vorgehensweise erstellt wurde

1. Klicken Sie im Quellcodefenster auf den linken Rand der Zeile, in der sich der hinzugefügte Text befindet:

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

     Ein roter Punkt wird angezeigt, und der Text der Zeile wird rot hervorgehoben. Der rote Punkt steht für einen Haltepunkt. Weitere Informationen finden Sie unter [Breakpoints (Haltepunkte)](/previous-versions/ktf38f66(v=vs.100)). Wenn Sie die Anwendung unter dem Debugger ausführen, hält dieser die Ausführung an der Stelle mit dem Haltepunkt an. Dadurch erhalten Sie die Möglichkeit, den Status der Anwendung zu überprüfen und diese zu debuggen.

    > [!NOTE]
    > Sie können auch mit der rechten Maustaste auf jede Codezeile klicken, auf **Haltepunkt** zeigen und anschließend auf **Haltepunkt einfügen** klicken, um einen Breakpoint in dieser Zeile hinzuzufügen.

2. Wählen Sie im Menü **Debuggen** den Befehl **Starten** aus.

     Das Windows Form wird ausgeführt.

3. Klicken Sie im Formular auf die hinzugefügte Schaltfläche.

     In Visual Studio gelangen Sie damit in die Zeile, in der Sie auf der Codepage den Haltepunkt festgelegt haben. Diese Zeile sollte gelb markiert sein. Jetzt können Sie die Variablen der Anwendung anzeigen und die Ausführung der Anwendung steuern. Die Ausführung der Anwendung wird angehalten, und der Debugger wartet auf eine Aktion Ihrerseits.

4. Klicken Sie im Menü **Debuggen** auf **Fenster**, dann auf **Überwachen** und anschließend auf **Überwachen 1**.

5. Klicken Sie im Fenster **Überwachen 1** auf eine leere Zeile. Geben Sie `textBox1.Text` in der Spalte **Name** ein, wenn Sie Visual Basic oder Visual C# verwenden, oder `textBox1->Text`, wenn Sie C++ verwenden, und drücken Sie dann die EINGABETASTE.

     Das Fenster **Überwachen 1** zeigt den Wert dieser Variablen in Anführungszeichen an:

    `""`

6. Wählen Sie im Menü **Debuggen** die Option **Einzelschritt** aus.

     Im Fenster **Überwachen1** ändert sich der Wert von „textBox1.Text“ in:

    `Button was clicked!`

7. Klicken Sie im Menü **Debuggen** auf **Weiter**, um das Debuggen des Programms fortzusetzen.

8. Klicken Sie im Formular erneut auf die Schaltfläche.

     Visual Studio unterbricht die Ausführung erneut.

9. Klicken Sie auf den roten Punkt, der den Haltepunkt darstellt.

     Dadurch wird der Haltpunkt aus dem Code entfernt.

10. Wählen Sie im Menü **Debuggen** die Option **Debuggen beenden** aus.

## <a name="attach-to-your-windows-form-application-for-debugging"></a>Anfügen an die Windows Form-Anwendung zum Debuggen
 In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] können Sie den Debugger an einen laufenden Prozess anfügen. Wenn Sie eine Express Edition verwenden, wird dieses Feature nicht unterstützt.

#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>So fügen Sie die Windows Form-Anwendung zum Debuggen an

1. Klicken Sie im soeben erstellen Projekt in den linken Rand der hinzugefügten Zeile, um erneut einen Haltepunkt festzulegen:

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

2. Klicken Sie im Menü **Debuggen** auf die Option **Starten ohne Debuggen**.

     Das Windows Form wird unter Windows ausgeführt, genau wie bei einem Doppelklick auf die ausführbare Datei. Der Debugger wird nicht angehängt.

3. Klicken Sie im Menü **Debuggen** auf die Option **An den Prozess anhängen**. (Dieser Befehl ist auch im Menü **Extras** verfügbar.)

     Das Dialogfeld **An den Prozess anhängen** wird angezeigt.

4. Suchen Sie im Bereich **Verfügbare Prozesse** in der Spalte **Prozess** den Prozessnamen (Walkthrough_SimpleDebug.exe), und klicken Sie darauf.

5. Klicken Sie auf die Schaltfläche **Anfügen**.

6. Klicken Sie im Formular auf die einzige vorhandene Schaltfläche.

     Der Debugger unterbricht die Ausführung des Formulars am Haltepunkt.

## <a name="see-also"></a>Siehe auch
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [Debuggersicherheit](../debugger/debugger-security.md)