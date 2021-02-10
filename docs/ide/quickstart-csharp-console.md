---
title: Erstellen Ihrer ersten C#-Konsolenanwendung mit Visual Studio
titleSuffix: ''
description: Hier finden Sie eine ausführliche Anleitung zum Erstellen einer einfachen „Hallo Welt“-Konsolenanwendung mit C# in Visual Studio.
ms.custom: seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: e3c6646fca0f0b20f7fb5d5d018c297d1ece920d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945551"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Schnellstart: Erstellen der ersten C#-Konsolenanwendung mit Visual Studio

Mithilfe dieser fünf- bis zehnminütigen Einführung in die integrierte Entwicklungsumgebung (IDE) von Visual Studio, können Sie eine einfache C#-Anwendung erstellen, die in der Konsole ausgeführt werden kann.

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range="vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

::: moniker-end

## <a name="create-a-project"></a>Erstellen eines Projekts

Zunächst müssen Sie ein Projekt für die C#-Anwendung erstellen. Der Projekttyp enthält, schon bevor Sie mit der Bearbeitung beginnen, alle Vorlagendateien, die Sie benötigen.

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio 2017.

2. Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. Erweitern Sie im linken Dialogfeld **Neues Projekt** den Eintrag **C#** , und klicken Sie auf **.NET Core**. Wählen Sie im mittleren Bereich die Option **Konsolenanwendung (.NET Core)** aus. Nennen Sie dann das Projekt *HalloWelt*.

   ![Projektvorlage „Console App (.NET Core)“ im Dialogfeld „Neues Projekt“ in der Visual Studio-IDE](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Falls Sie die Projektvorlage **Konsolenanwendung (.NET Core)** nicht finden, klicken Sie auf den Link **Visual Studio-Installer öffnen** auf der linken Seite des Dialogfelds **Neues Projekt**.

   ![Auswählen des Links „Visual Studio-Installer öffnen“ im Dialogfeld „Neues Projekt“](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Anpassen**.

     ![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

1. Öffnen Sie Visual Studio 2019.

1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   ![Fenster „Neues Projekt erstellen“](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Geben Sie im Fenster **Neues Projekt erstellen** im Suchfeld *Konsole* ein. Wählen Sie anschließend in der Liste der Sprachen **C#** und dann aus der Liste der Plattformen **Windows** aus. 

   Nachdem Sie die Sprach- und Plattformfilter angewendet haben, wählen Sie die Vorlage **Konsolen-App (.NET Core)** und dann **Weiter** aus.

   ![Auswählen der C#-Vorlage für die Konsolen-App (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Wenn Sie die **Konsolen-App (.NET Core)** nicht sehen, können Sie sie aus dem Fenster **Neues Projekt erstellen** installieren. Wählen Sie in der Meldung **Sie finden nicht, wonach Sie suchen?** den Link **Weitere Tools und Features installieren** aus.
   >
   > ![Link „Weitere Tools und Features installieren“ aus der Meldung „Sie finden nicht, wonach Sie suchen“ im Fenster „Neues Projekt erstellen“](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Wählen Sie anschließend im Visual Studio-Installer die Workload **Plattformübergreifende .NET Core-Entwicklung** aus.
   >
   > ![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Wählen Sie anschließend die Schaltfläche **Ändern** im Visual Studio-Installer aus. Möglicherweise werden Sie aufgefordert, Ihre Arbeit zu speichern; wenn dies der Fall ist, führen Sie das aus. Wählen Sie als Nächstes **Weiter** aus, um die Workload zu installieren. Kehren Sie dann zu Schritt 2 in dieser Vorgehensweise „[Projekt erstellen](#create-a-project)“ zurück.

1. Geben Sie im Fenster **Neues Projekt konfigurieren** im Feld **Projektname***HalloWelt* ein. Wählen Sie anschließend **Erstellen** aus.

   ![Benennen Sie Ihr Projekt im Fenster „Neues Projekt konfigurieren“ „HalloWelt“](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio öffnet Ihr neues Projekt.
   
::: moniker-end

## <a name="create-the-application"></a>Erstellen der Anwendung

::: moniker range="vs-2017"

Nachdem Sie Ihre C#-Projektvorlage ausgewählt und Ihr Projekt benannt haben, erstellt Visual Studio eine einfache „Hallo Welt“-Anwendung.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio schließt den „Hallo Welt“-Standardcode in Ihr Projekt ein.

::: moniker-end

(Zu diesem Zweck ruft es die Methode <xref:System.Console.WriteLine%2A> auf, um die literale Zeichenfolge „Hallo Welt“ anzuzeigen. im Konsolenfenster anzuzeigen.)

   ![Sehen Sie sich den Standardcode für „Hallo Welt“ in der Vorlage an](../ide/media/csharp-console-helloworld-template.png)

Wenn Sie **F5** drücken, wird das Programm im Debugmodus ausgeführt. Das Konsolenfenster öffnet sich nur für einen kurzen Moment, bevor es wieder geschlossen wird.

(Der Grund für dieses Verhalten ist, dass die Methode `Main` beendet wird, nachdem ihre einzige Anweisung ausgeführt wurde. Also wird die Anwendung geschlossen.)

### <a name="add-some-code"></a>Hinzufügen von Code

Fügen Sie Code hinzu, um die Anwendung anzuhalten, damit das Konsolenfenster nicht geschlossen wird, bis Sie die **EINGABETASTE** gedrückt haben.

1. Fügen Sie direkt nach dem Aufruf der <xref:System.Console.WriteLine%2A>-Methode folgenden Code ein:

   ```csharp
   Console.ReadLine();
   ```

1. Überprüfen Sie, ob der Code im Code-Editor wie folgt aussieht:

   ![Hinzufügen von Code zum Anhalten der Hallo Welt-App](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Ausführen der Anwendung

1. Wählen Sie auf der Symbolleiste die Schaltfläche **HelloWorld** aus, um die Anwendung im Debugmodus auszuführen. Alternativ können Sie **F5** drücken.

   ![Wählen Sie die Schaltfläche „Hello World“ aus, um die App von der Symbolleiste aus auszuführen](../ide/media/csharp-console-hello-world-button.png)

1. Zeigen Sie Ihre App im Konsolenfenster an.

   ![Konsolenfenster mit „Hello World!“](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Schließen der Anwendung

1. Drücken Sie die **EINGABETASTE**, um das Konsolenfenster zu schließen.

1. Schließen Sie den Bereich **Output** (Ausgabe) in Visual Studio.

   ![Schließen des Ausgabebereichs in Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Schließen Sie Visual Studio.

## <a name="next-steps"></a>Nächste Schritte

Damit haben Sie den Schnellstart erfolgreich abgeschlossen. Wir hoffen, dass Sie mehr über C# und die Visual Studio-IDE erfahren konnten. Wenn Sie noch mehr lernen möchten, fahren Sie mit den folgenden Tutorials fort.

> [!div class="nextstepaction"]
> [Erste Schritte mit einer C#-Konsolen-App in Visual Studio](../get-started/csharp/tutorial-console.md)
