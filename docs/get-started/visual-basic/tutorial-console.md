---
title: 'Tutorial: Erste Schritte mit Visual Basic'
description: Erfahren Sie anhand einer exemplarischen Vorgehensweise, wie Sie Visual Basic-Konsolenanwendungen in Visual Studio erstellen.
ms.custom: seodec18, get-started
ms.date: 02/10/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jmartens
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 70782687b6220adf1c61c5b2bb6487d68fde70f4
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101682611"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Tutorial: Erste Schritte mit Visual Basic in Visual Studio

In diesem Tutorial für Visual Basic (VB) lernen Sie die Entwicklung mit Visual Studio kennen und erstellen und führen verschiedene Konsolen-Apps aus. Außerdem machen Sie sich währenddessen mit einigen Features der [integrierten Entwicklungsumgebung (Integrated Development Environment, IDE)](visual-studio-ide.md) von Visual Studio vertraut.

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range="vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

::: moniker-end

## <a name="create-a-project"></a>Erstellen eines Projekts

Erstellen wir zunächst ein Visual Basic-Anwendungsprojekt. Der Projekttyp enthält, schon bevor Sie mit der Bearbeitung beginnen, alle Vorlagendateien, die Sie benötigen.

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio 2017.

2. Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual Basic**, und klicken Sie auf **.NET Core**. Wählen Sie im mittleren Bereich die Option **Konsolenanwendung (.NET Core)** aus. Nennen Sie das Projekt dann *WhatIsYourName*.

   ![Projektvorlage „Console App (.NET Core)“ im Dialogfeld „Neues Projekt“ in der Visual Studio-IDE](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>Hinzufügen einer Workload (optional)

Wenn Ihnen die Projektvorlage **Console App (.NET Core)** (Konsolen-App (.NET Core)) fehlt, fügen Sie einfach die Workload **Plattformübergreifende .NET Core-Entwicklung** hinzu. Sie haben folgende Möglichkeiten für das Hinzufügen der Workload, je nachdem, welche Visual Studio 2017-Updates auf dem Computer installiert sind.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1: Verwenden des Dialogfelds „Neues Projekt“

1. Klicken Sie im Dialogfeld **Neues Projekt** im linken Bereich auf den Link **Visual Studio-Installer öffnen**.

   ![Klicken Sie auf den Link „Visual Studio-Installer öffnen“ im Dialogfeld „Neues Projekt“](../media/vs-open-visual-studio-installer-generic.png)

1. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Anpassen**.

   ![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Option 2: Verwenden der Menüleiste „Extras“

1. Schließen Sie das Dialogfeld **Neues Projekt**, und klicken Sie in der oberen Menüleiste auf **Tools** > **Tools und Features abrufen**.

1. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Anpassen**.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Einige der Screenshots in diesem Tutorial verwenden das dunkle Design. Wenn Sie ebenfalls das dunkle Design verwenden möchten, finden Sie auf der Seite [Personalisieren der Visual Studio-IDE und des Editors](../../ide/quickstart-personalize-the-ide.md) entsprechende Anweisungen.

1. Öffnen Sie Visual Studio 2019.

1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   ![Anzeigen des Fensters „Neues Projekt erstellen“](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Wählen Sie im Fenster **Neues Projekt erstellen** in der Liste der Sprachen **Visual Basic** aus. Wählen Sie anschließend in der Liste der Plattformen **Windows** und in der Liste der Projekttypen **Konsole** aus.

   Nachdem Sie die Sprach-, Plattform- und Projekttypfilter angewendet haben, wählen Sie die Vorlage **Konsolenanwendung** und dann **Weiter** aus.

   :::image type="content" source="./media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Auswählen der Visual Basic-Vorlage für die Konsolenanwendung":::

   > [!NOTE]
   > Wenn die Vorlage **Konsolenanwendung** nicht angezeigt wird, können Sie sie im Fenster **Neues Projekt erstellen** installieren. Wählen Sie in der Meldung **Sie finden nicht, wonach Sie suchen?** den Link **Weitere Tools und Features installieren** aus.
   >
   > ![Link „Weitere Tools und Features installieren“ aus der Meldung „Sie finden nicht, wonach Sie suchen“ im Fenster „Neues Projekt erstellen“](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Wählen Sie anschließend im Visual Studio-Installer die Workload **Plattformübergreifende .NET Core-Entwicklung** aus.
   >
   > ![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Wählen Sie anschließend die Schaltfläche **Ändern** im Visual Studio-Installer aus. Möglicherweise werden Sie aufgefordert, Ihre Arbeit zu speichern; wenn dies der Fall ist, führen Sie das aus. Wählen Sie als Nächstes **Weiter** aus, um die Workload zu installieren. Kehren Sie dann zu Schritt 2 in dieser Vorgehensweise "[Projekt erstellen](#create-a-project)" zurück.

1. Geben Sie im Fenster **Neues Projekt konfigurieren** im Feld **Projektname***WhatIsYourName* ein. Klicken Sie dann auf **Weiter**.

   :::image type="content" source="./media/vs-2019/vb-name-your-project-whatname.png" alt-text="Benennen Sie Ihr Projekt im Fenster „Neues Projekt konfigurieren“ „WhatIsYourName“":::

1. Im Fenster **Zusätzliche Informationen** sollte **.NET Core 3.1** bereits als Zielframework ausgewählt sein. Falls nicht, wählen Sie **.NET Core 3.1** aus. Wählen Sie anschließend **Erstellen** aus.

   :::image type="content" source="./media/vs-2019/vb-target-framework.png" alt-text="Sicherstellen, dass im Fenster „Zusätzliche Informationen“ .NET Core 3.1 ausgewählt ist":::

   Visual Studio öffnet Ihr neues Projekt.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>Erstellen einer „What is your name“-Anwendung

Erstellen wir eine App, die Sie nach Ihrem Namen fragt und ihn anschließend zusammen mit dem Datum und der Uhrzeit anzeigt. Gehen Sie dazu wie folgt vor:

 ::: moniker range="vs-2017"

1. Wenn es nicht bereits geöffnet ist, öffnen Sie das Projekt *WhatIsYourName*.

1. Geben Sie unmittelbar nach der öffnenden Klammer, die auf die Zeile `Sub Main(args As String())` folgt, und vor der Zeile `End Sub` den folgenden Visual Basic-Code ein:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Dieser Code ersetzt die bestehenden Anweisungen <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> und <xref:System.Console.ReadKey%2A>.

   ![Codefenster mit „What is your name“-Code](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Wählen Sie die grüne Schaltfläche **Starten** aus, oder drücken Sie **F5**, um Ihre erste App zu erstellen und auszuführen.

1. Wenn sich das Konsolenfenster öffnet, geben Sie Ihren Namen ein. Das Konsolenfenster sollte so wie der folgende Screenshot aussehen:

   ![Konsolenfenster mit „What is your name“, der Uhrzeit und dem Datum sowie der Nachricht „Drücken Sie eine beliebige Taste, um fortzufahren“](media/vb-console-what-name.png)

1. Drücken Sie eine beliebige Taste, um das Konsolenfenster zu schließen.

::: moniker-end

::: moniker range="vs-2019"

1. Geben Sie im Projekt *WhatIsYourName* unmittelbar nach der öffnenden Klammer, die auf die Zeile `Sub Main(args As String())` folgt, und vor der Zeile `End Sub` den folgenden Visual Basic-Code ein:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Dieser Code ersetzt die bestehenden Anweisungen <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> und <xref:System.Console.ReadKey%2A>.

   ![Codefenster mit „What is your name“-Code](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Wählen Sie die grüne Schaltfläche **Starten** aus, oder drücken Sie **F5**, um Ihre erste App zu erstellen und auszuführen.

1. Wenn sich das Konsolenfenster öffnet, geben Sie Ihren Namen ein. Das Konsolenfenster sollte so wie der folgende Screenshot aussehen:

   ![Konsolenfenster mit „What is your name“, der Uhrzeit und dem Datum sowie der Nachricht „Drücken Sie eine beliebige Taste, um fortzufahren“](media/vb-console-what-name.png)

1. Drücken Sie eine beliebige Taste, um das Konsolenfenster zu schließen.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>Erstellen einer Rechenanwendung

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio 2017, und klicken Sie in der Menüleiste oben auf **Datei** > **Neu** > **Projekt**.

1. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual Basic**, und klicken Sie auf **.NET Core**. Wählen Sie im mittleren Bereich die Option **Konsolenanwendung (.NET Core)** aus. Nennen Sie die Datei *CalculateThis*.

1. Geben Sie zwischen den Zeilen `Module Program` und `End Module` den folgenden Code ein:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   Das Codefenster sollte wie der folgende Screenshot aussehen:

   ![Codefenster mit „CalulateThis“-Code](media/vb-codewindow-calculate-this.png)

1. Klicken Sie auf **CalculateThis**, um das Programm auszuführen. Das Konsolenfenster sollte so wie der folgende Screenshot aussehen:

    ![Konsolenfenster mit CalculateThis-App und Aufforderungen zu den erwarteten Benutzeraktionen.](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range="vs-2019"

1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus. 

1. Wählen Sie im Fenster **Neues Projekt erstellen** in der Liste der Sprachen **Visual Basic** aus. Wählen Sie anschließend in der Liste der Plattformen **Windows** und in der Liste der Projekttypen **Konsole** aus.

1. Nachdem Sie die Sprach-, Plattform- und Projekttypfilter angewendet haben, wählen Sie die Vorlage **Konsolenanwendung** und dann **Weiter** aus.

   Geben Sie anschließend *CalculateThis* im Feld **Projektname** im Fenster **Neues Projekt konfigurieren** ein. Klicken Sie dann auf **Weiter**.

1. Im Fenster **Zusätzliche Informationen** sollte **.NET Core 3.1** bereits als Zielframework ausgewählt sein. Falls nicht, wählen Sie **.NET Core 3.1** aus. Wählen Sie anschließend **Erstellen** aus.

1. Geben Sie zwischen den Zeilen `Module Program` und `End Module` den folgenden Code ein:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   Das Codefenster sollte wie der folgende Screenshot aussehen:

   ![Codefenster mit „CalulateThis“-Code](media/vb-codewindow-calculate-this.png)

1. Klicken Sie auf **CalculateThis**, um das Programm auszuführen. Das Konsolenfenster sollte so wie der folgende Screenshot aussehen:

    ![Konsolenfenster mit CalculateThis-App und Aufforderungen zu den erwarteten Benutzeraktionen.](media/vb-console-calculate-this.png)

::: moniker-end

## <a name="quick-answers-faq"></a>Schnelle Antworten zu häufig gestellten Fragen

In den folgenden häufig gestellten Fragen werden einige wichtige Konzepte besprochen.

### <a name="what-is-visual-basic"></a>Was ist Visual Basic?

Visual Basic ist eine typsichere Programmiersprache, die einfach zu erlernen ist. Sie wurde von BASIC abgeleitet, was für „Beginner's All-purpose Symbolic Instruction Code“ (nicht zweckgebundener, symbolischer Anweisungscode für Anfänger) steht.

### <a name="what-is-visual-studio"></a>Was ist Visual Studio?

Visual Studio ist eine integrierte Zusammenstellung von Entwicklertools, die die Produktivität fördern. Es ist also ein Programm zum Erstellen von Programmen und Anwendungen.

### <a name="what-is-a-console-app"></a>Was ist eine Konsolen-App?

Eine Konsolenanwendung akzeptiert eine Eingabe und zeigt eine Ausgabe in einem Befehlszeilenfenster, das auch als Konsole bezeichnet wird.

### <a name="what-is-net-core"></a>Was ist .NET Core?

.NET Core ist die Weiterentwicklung von .NET Framework. In .NET Framework war es nur möglich, Code programmiersprachenübergreifend zu verwenden. Mit .NET Core kann er auch plattformübergreifend genutzt werden. Und die Technologie ist sogar Open Source. (Sowohl .NET Framework als auch .NET Core enthalten Bibliotheken mit vorgefertigter Funktionalität und eine Common Language Runtime (CLR), die als virtueller Computer fungiert, auf dem der Code ausgeführt wird.)

## <a name="next-steps"></a>Nächste Schritte

Damit haben Sie das Tutorial erfolgreich abgeschlossen. Weitere Informationen finden Sie im folgenden Tutorial.

> [!div class="nextstepaction"]
> [Erstellen einer .NET Standard-Bibliothek mit Visual Basic und .NET Core SDK in Visual Studio](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Weitere Informationen

* [Exemplarische Vorgehensweisen für Visual Basic](/dotnet/visual-basic/walkthroughs)
* [Sprachreferenz zu Visual Basic](/dotnet/visual-basic/language-reference/index)
* [IntelliSense für Visual Basic-Codedateien](../../ide/visual-basic-specific-intellisense.md)
