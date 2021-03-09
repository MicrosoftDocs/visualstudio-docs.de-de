---
title: Erstellen einer ersten Konsolen-App mit Visual Basic
description: Hier finden Sie eine ausführliche Anleitung zum Erstellen einer einfachen „Hallo Welt“-Konsolenanwendung mit Visual Basic in Visual Studio.
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
- vb
ms.workload:
- multiple
ms.openlocfilehash: 34b412d254d0775b57f2c9befaae71ce25c6ae75
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683864"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Schnellstart: Erstellen einer ersten Konsolenanwendung in Visual Studio mit Visual Basic

Mithilfe dieser Einführung in die integrierte Entwicklungsumgebung (IDE) von Visual Studio, die fünf bis zehn Minuten Ihrer Zeit in Anspruch nehmen wird, können Sie eine einfache Visual Basic-Anwendung erstellen, die in der Konsole ausgeführt werden kann.

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range="vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

::: moniker-end

## <a name="create-a-project"></a>Erstellen eines Projekts

Erstellen Sie zunächst ein Visual Basic-Anwendungsprojekt. Der Projekttyp enthält, schon bevor Sie mit der Bearbeitung beginnen, alle Vorlagendateien, die Sie benötigen.

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio 2017.

2. Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual Basic**, und klicken Sie auf **.NET Core**. Wählen Sie im mittleren Bereich die Option **Konsolenanwendung (.NET Core)** aus. Nennen Sie dann das Projekt *HalloWelt*.

   ![Projektvorlage „Console App (.NET Core)“ im Dialogfeld „Neues Projekt“ in der Visual Studio-IDE](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Falls Sie die Projektvorlage **Konsolenanwendung (.NET Core)** nicht finden, klicken Sie auf den Link **Visual Studio-Installer öffnen** auf der linken Seite des Dialogfelds **Neues Projekt**.

   ![Klicken Sie auf den Link „Visual Studio-Installer öffnen“ im Dialogfeld „Neues Projekt“](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Anpassen**.

     ![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Einige der Screenshots in diesem Schnellstart verwenden das dunkle Design. Wenn Sie ebenfalls das dunkle Design verwenden möchten, finden Sie auf der Seite [Personalisieren der Visual Studio-IDE und des Editors](quickstart-personalize-the-ide.md) entsprechende Anweisungen.

1. Öffnen Sie Visual Studio 2019.

1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   ![Anzeigen des Fensters „Neues Projekt erstellen“](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Wählen Sie im Fenster **Neues Projekt erstellen** in der Liste der Sprachen **Visual Basic** aus. Wählen Sie anschließend in der Liste der Plattformen **Windows** und in der Liste der Projekttypen **Konsole** aus.

   Nachdem Sie die Sprach-, Plattform- und Projekttypfilter angewendet haben, wählen Sie die Vorlage **Konsolenanwendung** und dann **Weiter** aus.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Auswählen der Visual Basic-Vorlage für die Konsolenanwendung":::

   > [!NOTE]
   > Wenn die Vorlage **Konsolenanwendung** nicht angezeigt wird, können Sie sie im Fenster **Neues Projekt erstellen** installieren. Wählen Sie in der Meldung **Sie finden nicht, wonach Sie suchen?** den Link **Weitere Tools und Features installieren** aus.
   >
   > ![Link „Weitere Tools und Features installieren“ aus der Meldung „Sie finden nicht, wonach Sie suchen“ im Fenster „Neues Projekt erstellen“](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Wählen Sie anschließend im Visual Studio-Installer die Workload **Plattformübergreifende .NET Core-Entwicklung** aus.
   >
   > ![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Wählen Sie anschließend die Schaltfläche **Ändern** im Visual Studio-Installer aus. Möglicherweise werden Sie aufgefordert, Ihre Arbeit zu speichern; wenn dies der Fall ist, führen Sie das aus. Wählen Sie als Nächstes **Weiter** aus, um die Workload zu installieren. Kehren Sie dann zu Schritt 2 in dieser Vorgehensweise "[Projekt erstellen](#create-a-project)" zurück.

1. Geben Sie im Fenster **Neues Projekt konfigurieren** im Feld **Projektname***WhatIsYourName* ein. Klicken Sie dann auf **Weiter**.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png" alt-text="Benennen Sie Ihr Projekt im Fenster „Neues Projekt konfigurieren“ „WhatIsYourName“":::

1. Im Fenster **Zusätzliche Informationen** sollte **.NET Core 3.1** bereits als Zielframework ausgewählt sein. Falls nicht, wählen Sie **.NET Core 3.1** aus. Wählen Sie anschließend **Erstellen** aus.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-target-framework.png" alt-text="Sicherstellen, dass im Fenster „Zusätzliche Informationen“ .NET Core 3.1 ausgewählt ist":::

   Visual Studio öffnet Ihr neues Projekt.

::: moniker-end

## <a name="create-the-application"></a>Erstellen der Anwendung

Nachdem Sie Ihre Visual Basic-Projektvorlage ausgewählt haben und Ihr Projekt benannt haben, erstellt Visual Studio eine einfache „Hallo Welt“-Anwendung für Sie. Sie ruft die <xref:System.Console.WriteLine%2A>-Methode auf, um die literale Zeichenfolge „Hello World!“ im Konsolenfenster anzuzeigen.

![Sehen Sie sich den Standardcode für „Hallo Welt“ in der Vorlage an](../ide/media/vb-console-helloworld-template.png)

Sie können das Programm im Debugmodus ausführen, indem Sie in der IDE auf die Schaltfläche **Hallo Welt** klicken.

  ![Klicken Sie auf die Schaltfläche „Hallo Welt“, um das Programm im Debugmodus auszuführen](../ide/media/vb-console-hello-world-button.png)

Wenn Sie dies tun, öffnet sich das Konsolenfenster nur für einen kurzen Moment, bevor es wieder geschlossen wird. Der Grund dafür ist, dass die Methode `Main` beendet wird, nachdem ihre einzige Anweisung ausgeführt wird, also wird die Anwendung geschlossen.

### <a name="add-some-code"></a>Hinzufügen von Code

Fügen Sie Code hinzu, um die Anwendung zu pausieren und den Benutzer zur Eingabe aufzufordern.

1. Fügen Sie direkt nach dem Aufruf der <xref:System.Console.WriteLine%2A>-Methode folgenden Code ein:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

    Durch diesen Code wird das Programm pausiert, bis eine Taste gedrückt wird.

2. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

   Dies kompiliert Ihr Programm in eine Zwischensprache (IL), die dann von einem JIT-Compiler (Just in Time) in Binärcode konvertiert wird.

## <a name="run-the-application"></a>Ausführen der Anwendung

1. Klicken Sie auf der Symbolleiste auf die Schaltfläche **HalloWelt**.

   ![Klicken Sie die Schaltfläche „HalloWelt“, um das Programm von der Symbolleiste aus auszuführen](../ide/media/vb-console-hello-world-button.png)

2. Drücken Sie eine beliebige Taste, um das Konsolenfenster zu schließen.

   ![Konsolenfenster mit „Hallo Welt“ und „Drücken Sie eine beliebige Taste um fortzufahren“](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Nächste Schritte

Damit haben Sie den Schnellstart erfolgreich abgeschlossen. Wir hoffen, dass Sie etwas über Visual Basic und die Visual Studio-IDE gelernt haben. Fahren Sie für weitere Informationen mit dem Tutorial fort.

> [!div class="nextstepaction"]
> [Erste Schritte mit Visual Basic in Visual Studio](../get-started/visual-basic/tutorial-console.md)
