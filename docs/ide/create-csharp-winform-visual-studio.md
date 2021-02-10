---
title: Erstellen einer Windows Forms-App mit C#
description: Erfahren Sie in dieser Schrittanleitung, wie Sie eine Windows Forms-App in Visual Studio mit C# erstellen.
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 0fcc42b999039abe5d682394e378cb95f12b9283
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956931"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Erstellen einer Windows Forms-App in Visual Studio mit C\#

In dieser kurzen Einführung in die integrierte Entwicklungsumgebung (IDE) von Visual Studio erstellen Sie eine einfache C#-Anwendung, die über eine Windows-basierte Benutzeroberfläche verfügt.

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range="vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

> [!NOTE]
> Einige der Screenshots in diesem Tutorial verwenden das dunkle Design. Wenn Sie ebenfalls das dunkle Design verwenden möchten, finden Sie auf der Seite [Personalisieren der Visual Studio-IDE und des Editors](../ide/quickstart-personalize-the-ide.md) entsprechende Anweisungen.

::: moniker-end

## <a name="create-a-project"></a>Erstellen eines Projekts

Zunächst müssen Sie ein Projekt für die C#-Anwendung erstellen. Der Projekttyp enthält schon bevor Sie mit der Bearbeitung beginnen alle Vorlagendateien, die Sie benötigen.

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio 2017.

1. Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

1. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual C#** , und klicken Sie dann auf **Windows-Desktop**. Klicken Sie im mittleren Bereich auf **Windows Forms-App (.NET Framework)** . Nennen Sie die Datei `HelloWorld`.

     Wenn Ihnen die Projektvorlage **Windows Forms-App (.NET Framework)** nicht angezeigt wird, schließen Sie das Dialogfeld **Neues Projekt**, und klicken Sie in der oberen Menüleiste auf **Extras** > **Get Tools and Features** (Tools und Features abrufen). Der Visual Studio-Installer wird gestartet. Wählen Sie beispielsweise die Workload **.NET-Desktopentwicklung** aus, und klicken Sie anschließend auf **Ändern**.

     ![Die Workload „.NET Core“ im Visual Studio-Installer](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Öffnen Sie Visual Studio 2019.

1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   ![Fenster „Neues Projekt erstellen“ anzeigen](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Wählen Sie im Fenster **Neues Projekt erstellen** die Vorlage **Windows Forms-App (.NET Framework)** für C# aus.

   (Sie können die Suche auch verfeinern, um schnell zu der gewünschten Vorlage zu gelangen. Sie können z. B. *Windows Forms-App* im Suchfeld eingeben. Wählen Sie anschließend in der Liste der Sprachen **C#** und dann in der Liste der Plattformen **Windows** aus.)  

   ![Auswählen der C#-Vorlage für die Windows Forms-App (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > Wenn Sie die **Windows Forms-App (.NET Framework)** nicht sehen, können Sie sie aus dem Fenster **Neues Projekt erstellen** installieren. Wählen Sie in der Meldung **Sie finden nicht, wonach Sie suchen?** den Link **Weitere Tools und Features installieren** aus.
   >
   > ![Link „Weitere Tools und Features installieren“ aus der Meldung „Sie finden nicht, wonach Sie suchen“ im Fenster „Neues Projekt erstellen“](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Wählen Sie anschließend im Visual Studio-Installer die Workload **.NET Desktopentwicklung** aus.
   >
   > ![Die Workload „.NET Core“ im Visual Studio-Installer](../ide/media/install-dot-net-desktop-env.png)
   >
   > Wählen Sie anschließend die Schaltfläche **Ändern** im Visual Studio-Installer aus. Möglicherweise werden Sie aufgefordert, Ihre Arbeit zu speichern; wenn dies der Fall ist, führen Sie das aus. Wählen Sie als Nächstes **Weiter** aus, um die Workload zu installieren. Kehren Sie dann zu Schritt 2 in dieser Vorgehensweise "[Projekt erstellen](#create-a-project)" zurück.

1. Geben Sie im Fenster **Neues Projekt konfigurieren** im Feld **Projektname***HalloWelt* ein. Wählen Sie anschließend **Erstellen** aus.

   ![Benennen Sie Ihr Projekt im Fenster „Neues Projekt konfigurieren“ „HalloWelt“](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio öffnet Ihr neues Projekt.

::: moniker-end

## <a name="create-the-application"></a>Erstellen der Anwendung

Nachdem Sie eine C#-Projektvorlage ausgewählt und die Datei benannt haben, öffnet Visual Studio ein Formular für Sie. Ein Formular ist eine Windows-Benutzeroberfläche. Wir erstellen eine „Hallo Welt“-Anwendung, indem wir dem Formular Steuerelemente hinzufügen und die App dann ausführen.

### <a name="add-a-button-to-the-form"></a>Hinzufügen einer Schaltfläche zum Formular

1. Klicken Sie auf **Toolbox**, um das Toolbox-Flyoutfenster zu öffnen.

     ![Auswählen von „Toolbox“ zum Öffnen des Toolbox-Fensters](../ide/media/csharp-toolbox-toolwindow.png)

     (Wenn Ihnen die Option **Toolbox** nicht angezeigt wird, können Sie sie über die Menüleiste öffnen. Klicken Sie zu diesem Zweck auf **Ansicht** > **Toolbox**. Drücken Sie alternativ auf **STRG**+**ALT**+**X**.)

1. Klicken Sie auf das **Stecknadelsymbol**, um das **Toolbox**-Fenster anzudocken.

     ![Auswählen des Stecknadelsymbols zum Anheften des Toolbox-Fensters an die IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. Klicken Sie auf das **Schaltflächen**-Steuerelement, und ziehen Sie es auf das Formular.

     ![Hinzufügen einer Schaltfläche zum Formular](../ide/media/csharp-add-button-form1.png)

1. Suchen Sie im Fenster **Eigenschaften** nach **Text**, ändern Sie den Namen von **Button1** in `Click this`, und drücken Sie dann die **EINGABETASTE**.

     ![Hinzufügen von Text zur Schaltfläche auf dem Formular](../ide/media/vb-button-control-text.png)

     (Wenn Ihnen das **Eigenschaftenfenster** nicht angezeigt wird, können Sie es über die Menüleiste öffnen. Klicken Sie zu diesem Zweck auf **Ansicht** > **Eigenschaftenfenster**. Oder drücken Sie **F4**.)

1. Ändern Sie im Fenster **Eigenschaften** im Abschnitt **Entwurf** den Namen von **Button1** in `btnClickThis`, und drücken Sie dann die **EINGABETASTE**.

     ![Hinzufügen einer Funktion zur Schaltfläche auf dem Formular](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Wenn Sie die Liste im Fenster **Eigenschaften** alphabetisch sortiert haben, wird **Button1** stattdessen im Abschnitt **(DataBindings)** angezeigt.

### <a name="add-a-label-to-the-form"></a>Hinzufügen einer Bezeichnung zum Formular

Da nun ein Schaltflächen-Steuerelement hinzugefügt wurde, kann jetzt auch ein Bezeichnungs-Steuerelement hinzugefügt werden, an das Text gesendet werden kann, um eine Aktion zu erstellen.

1. Wählen Sie im **Toolbox**-Fenster das Steuerelement **Bezeichnung** aus, und ziehen Sie es dann unter die Schaltfläche **Click this** („Hier klicken“).

1. Ändern Sie im Fenster **Eigenschaften** entweder im Abschnitt **Entwurf** oder im Abschnitt **(DataBindings)** den Namen von **Label1** in `lblHelloWorld`, und drücken Sie dann die **EINGABETASTE**.

### <a name="add-code-to-the-form"></a>Hinzufügen von Code zum Formular

1. Doppelklicken Sie im Fenster **Form1.cs &#91;Entwurf&#93;** auf die Schaltfläche **Hier klicken**, um das Fenster **Form1.cs** zu öffnen.

      (Stattdessen können Sie auch **Form1.cs** im **Projektmappen-Explorer** erweitern und dann auf **Form1** klicken.)

1. Geben Sie im Fenster **Form1.cs** nach der Zeile **private void** die Zeichenfolge `lblHelloWorld.Text = "Hello World!";` ein, wie im folgenden Screenshot gezeigt:

     ![Hinzufügen von Code zum Formular](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Ausführen der Anwendung

1. Klicken Sie auf die Schaltfläche **Start**, um die Anwendung auszuführen.

     ![Auswählen von „Start“ zum Debuggen und Ausführen der App](../ide/media/vb-click-start-hello-world.png)

   Daraufhin werden einige Vorgänge gleichzeitig ausgeführt. In der Visual Studio-IDE öffnen sich das Fenster **Diagnosetools** und ein **Ausgabefenster**. Außerhalb der IDE wird das **Form1**-Dialogfeld angezeigt. Darin ist die Schaltfläche **Click this** („Hier klicken“) und Text mit dem Inhalt **Label1** enthalten.

1. Klicken Sie im Dialogfeld **Form1** auf die Schaltfläche **Hier klicken**. Beachten Sie, dass der Text **Label1** sich in **Hallo Welt!** ändert.

    ![Ein „Form1“-Dialogfeld, das den Text „Label1“ beinhaltet. ](../ide/media/vb-form1-dialog-hello-world.png)

1. Schließen Sie das Dialogfeld **Form1**, um die Ausführung der App zu beenden.

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie für weitere Informationen mit dem folgenden Tutorial fort:

> [!div class="nextstepaction"]
> [Tutorial: Erstellen eines Bildanzeigeprogramms](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Siehe auch

* [Weitere C#-Tutorials](../get-started/csharp/index.yml)
* [Visual Basic-Tutorials](../get-started/visual-basic/index.yml)
* [C++-Tutorials](/cpp/get-started/tutorial-console-cpp)