---
title: 'Exemplarische Vorgehensweise: Debuggen eines Windows Forms | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
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
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a553f77e352b16ba1a0709e13e8893cf0f57a43d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704899"
---
# <a name="walkthrough-debugging-a-windows-form"></a>Exemplarische Vorgehensweise: Debuggen eines Windows Forms-Projekts
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
    1. Wählen Sie für Visual Basic oder Visual c# den Knoten **Windows** aus, und wählen Sie dann im Bereich **Vorlagen** die Option **Windows Form-Anwendung** aus.  
  
    2. Wählen Sie für Visual C++ den Knoten **CLR** aus, und wählen Sie dann im Bereich **Vorlagen** die Option **Windows Form-Anwendung** aus.  
  
3. Wählen Sie im Bereich **Vorlagen** die Option **Windows-Anwendung** aus.  
  
4. Geben Sie im Feld **Name** einen eindeutigen Namen für das Projekt ein (z. B. „Walkthrough_SimpleDebug“).  
  
5. Klicken Sie auf **OK**.  
  
     Visual Studio erstellt ein neues Projekt und zeigt ein neues Formular im Windows Forms-Designer an. Weitere Informationen finden Sie unter [Windows Forms-Designer](https://msdn.microsoft.com/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
6. Wählen Sie im Menü **Ansicht** die Option **Toolbox** aus.  
  
     Die Toolbox wird geöffnet. Weitere Informationen finden Sie unter [Toolbox](../ide/reference/toolbox.md).  
  
7. Klicken Sie in der Toolbox auf das **Button**-Steuerelement, und ziehen Sie es auf die Formularentwurfsoberfläche. Legen Sie das Steuerelement im Formular ab.  
  
8. Klicken Sie in der Toolbox auf das **TextBox**-Steuerelement, und ziehen Sie es auf die Formularentwurfsoberfläche. Legen Sie das **TextBox**-Steuerelement im Formular ab.  
  
9. Doppelklicken Sie auf der Formularentwurfsoberfläche auf die Schaltfläche.  
  
     Dadurch gelangen Sie auf die Codepage. Der Cursor sollte sich nun in der `button1_Click`-Funktion befinden.  
  
10. Fügen Sie folgenden Code in die `button1_Click`-Funktion ein:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
     Das Projekt wird fehlerfrei erstellt.  
  
## <a name="debug-your-form"></a>Debuggen des Formulars  
 Jetzt können Sie mit dem Debuggen beginnen.  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>So debuggen Sie das Windows Form, das für diese exemplarische Vorgehensweise erstellt wurde  
  
1. Klicken Sie im Quellcodefenster auf den linken Rand der Zeile, in der sich der hinzugefügte Text befindet:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
     Ein roter Punkt wird angezeigt, und der Text der Zeile wird rot hervorgehoben. Der rote Punkt steht für einen Haltepunkt. Weitere Informationen finden Sie unter [Breakpoints (Haltepunkte)](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583). Wenn Sie die Anwendung unter dem Debugger ausführen, hält dieser die Ausführung an der Stelle mit dem Haltepunkt an. Dadurch erhalten Sie die Möglichkeit, den Status der Anwendung zu überprüfen und diese zu debuggen.  
  
    > [!NOTE]
    > Sie können auch mit der rechten Maustaste auf jede Codezeile klicken, auf **Haltepunkt** zeigen und anschließend auf **Haltepunkt einfügen** klicken, um einen Breakpoint in dieser Zeile hinzuzufügen.  
  
2. Wählen Sie im Menü **Debuggen** den Befehl **Starten** aus.  
  
     Das Windows Form wird ausgeführt.  
  
3. Klicken Sie im Formular auf die hinzugefügte Schaltfläche.  
  
     In Visual Studio gelangen Sie damit in die Zeile, in der Sie auf der Codepage den Haltepunkt festgelegt haben. Diese Zeile sollte gelb markiert sein. Jetzt können Sie die Variablen der Anwendung anzeigen und die Ausführung der Anwendung steuern. Die Ausführung der Anwendung wird angehalten, und der Debugger wartet auf eine Aktion Ihrerseits.  
  
4. Klicken Sie im Menü **Debuggen** auf **Fenster**, dann auf **Überwachen** und anschließend auf **Überwachen 1**.  
  
5. Klicken Sie im Fenster **Überwachen 1** auf eine leere Zeile. Geben Sie **Name** in der Spalte Name `textBox1.Text` (bei Verwendung von Visual Basic, Visual c# oder j#) oder `textBox1->Text` (wenn Sie C++ verwenden) ein, und drücken Sie dann die EINGABETASTE.  
  
     Das Fenster **Überwachen 1** zeigt den Wert dieser Variablen in Anführungszeichen an:  
  
    ```  
    ""  
    ```  
  
6. Wählen Sie im Menü **Debuggen** die Option **Einzelschritt** aus.  
  
     Im Fenster **Überwachen1** ändert sich der Wert von „textBox1.Text“ in:  
  
    ```  
    Button was clicked!  
    ```  
  
7. Klicken Sie im Menü **Debuggen** auf **Weiter**, um das Debuggen des Programms fortzusetzen.  
  
8. Klicken Sie im Formular erneut auf die Schaltfläche.  
  
     Visual Studio unterbricht die Ausführung erneut.  
  
9. Klicken Sie auf den roten Punkt, der den Haltepunkt darstellt.  
  
     Dadurch wird der Haltpunkt aus dem Code entfernt.  
  
10. Wählen Sie im Menü **Debuggen** die Option **Debuggen beenden** aus.  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>Anfügen an die Windows Form-Anwendung zum Debuggen  
 In [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] können Sie den Debugger an einen laufenden Prozess anfügen. Wenn Sie eine Express Edition verwenden, wird dieses Feature nicht unterstützt.  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>So fügen Sie die Windows Form-Anwendung zum Debuggen an  
  
1. Klicken Sie im soeben erstellen Projekt in den linken Rand der hinzugefügten Zeile, um erneut einen Haltepunkt festzulegen:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!"  
  
    // C++  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugging von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)
