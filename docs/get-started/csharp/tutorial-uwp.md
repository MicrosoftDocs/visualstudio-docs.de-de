---
title: Erstellen einer UWP-App mit Visual Studio und C#
description: Erstellen einer UWP-App in Visual Studio mit XAML und C#
titleSuffix: ''
ms.custom: seodec18, get-started, SEO-VS-2020
ms.date: 09/20/2019
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 342fb2ba0d094299b41707b93b52f3b28a3afdce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909251"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Tutorial: Erstellen Ihrer ersten Anwendung für die Universelle Windows-Plattform in Visual Studio mit XAML und C&#35;

Mithilfe dieser Einführung in die integrierte Entwicklungsumgebung (IDE) von Visual Studio erstellen Sie die App „Hallo Welt“, die auf jedem beliebigen Windows 10-Gerät ausgeführt werden kann. Zu diesem Zweck verwenden Sie eine UWP-Projektvorlage (Universelle Windows-Plattform), XAML (Extensible Application Markup Language) und die C#-Programmiersprache.

::: moniker range="vs-2017"
Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.
::: moniker-end
::: moniker range="vs-2019"
Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.
::: moniker-end

## <a name="create-a-project"></a>Erstellen eines Projekts

Erstellen Sie zuerst ein UWP-Projekt (Universelle Windows-Plattform). Der Projekttyp enthält alle nötigen Vorlagendateien, schon bevor Sie mit der Bearbeitung beginnen.

::: moniker range="vs-2017"
1. Öffnen Sie Visual Studio.

1. Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

1. Klappen Sie im linken Bereich des Dialogfelds **Neues Projekt** den Eintrag **Visual C#** auf, und wählen Sie **Universelles Windows** aus. Wählen Sie im mittleren Bereich **Leere App (universelles Windows)** aus. Benennen Sie das Projekt mit *HalloWelt*, und wählen Sie **OK**.

   > [!NOTE]
   > Stellen Sie sicher, dass es sich beim Speicherort des Quellprojekts um ein Laufwerk mit **NTFS-Formatierung (New Technology File System)** handelt, z. B. bei Ihrem Betriebssystemlaufwerk. Andernfalls können beim Erstellen und Ausführen Ihres Projekts Probleme auftreten. 

   ![Die Projektvorlage für universelles Windows im Dialogfeld „Neues Projekt“ in der Visual Studio-IDE](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Falls Sie die Projektvorlage **Leere App (universelles Windows)** nicht finden, klicken Sie auf der linken Seite des Dialogfelds **Neues Projekt** auf den Link **Visual Studio-Installer öffnen**.<br><br>![Klicken Sie auf den Link „Visual Studio-Installer öffnen“ im Dialogfeld „Neues Projekt“.](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Entwicklung für die universelle Windows-Plattform** aus, und klicken Sie dann auf **Ändern**.<br><br>![Workload für die Entwicklung für die universelle Windows-Plattform im Visual Studio-Installer](media/uwp-dev-workload.png)

1. Übernehmen Sie im Dialogfeld **Neues UWP-Projekt (Universelle Windows-Plattform)** die Standardeinstellungen für **Zielversion** und **Mindestversion**.

   ![Übernehmen Sie die Standardeinstellungen für Zielversion und Mindestversion im Dialogfeld „Neues UWP-Projekt (Universelle Windows-Plattform)“.](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Öffnen Sie Visual Studio, und wählen Sie im Fenster Start die Option **Neues Projekt erstellen**.

1. Geben Sie auf dem Bildschirm **Neues Projekt erstellen** ins Suchfeld *Universelles Windows* ein, und wählen Sie die C#-Vorlage für **Leere App (Universelle Windows-App)** und anschließend **Weiter** aus.

   ![Screenshot des Bildschirms „Neues Projekt erstellen“](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > Wird die Projektvorlage **Leere App (Universelle Windows-App)** nicht angezeigt, klicken Sie auf den Link **Weitere Tools und Features installieren**.<br><br>![Klicken auf den Link „Weitere Tools und Features installieren“](media/vs-2019/uwp-not-finding.png)<br><br>Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Entwicklung für die universelle Windows-Plattform** aus, und klicken Sie dann auf **Ändern**.<br><br>![Workload für die Entwicklung für die universelle Windows-Plattform im Visual Studio-Installer](media/uwp-dev-workload.png)

1. Benennen Sie das Projekt mit _HelloWorld_, und klicken Sie auf **Erstellen**.

   ![Bildschirm „Konfigurieren des Projekts“](media/vs-2019/uwp-configure-your-project.png)

1. Übernehmen Sie im Dialogfeld **Neues UWP-Projekt (Universelle Windows-Plattform)** die Standardeinstellungen für **Zielversion** und **Mindestversion**.

   ![Übernehmen der Standardeinstellungen für Zielversion und Mindestversion im Dialogfeld „Neues UWP-Projekt (Universelle Windows-Plattform)“](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

   > [!NOTE]
   > Wenn Sie Visual Studio erstmals zum Erstellen einer UWP-App verwenden, wird möglicherweise ein Dialogfeld **Einstellungen** angezeigt. Wählen Sie **Entwicklermodus**, und wählen Sie dann **Ja**.<br><br>
   > ![Aktivieren Sie den Entwicklermodus im Dialogfeld mit UWP-Einstellungen.](media/enable-developer-mode.png)<br><br>Visual Studio installiert für Sie ein zusätzliches Entwicklermoduspaket. Wenn die Paketinstallation abgeschlossen ist, schließen Sie das Dialogfeld **Einstellungen**.

## <a name="create-the-application"></a>Erstellen der Anwendung

Beginnen wir jetzt mit der Entwicklung. Sie fügen ein Schaltflächensteuerelement hinzu, fügen der Schaltfläche eine Aktion hinzu und starten dann die App „Hallo Welt“, um sie sich anzusehen.

### <a name="add-a-button-to-the-design-canvas"></a>Hinzufügen einer Schaltfläche zur Entwurfs-Canvas

1. Doppelklicken Sie im **Projektmappen-Explorer** auf die Datei *MainPage.xaml*, um eine geteilte Ansicht zu öffnen.

   ::: moniker range="vs-2017"
   ![Öffnen Sie im Projektmappen-Explorer die Datei „MainPage.xaml“. ](media/uwp-solution-explorer-MainPage-xaml.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Öffnen Sie im Projektmappen-Explorer die Datei „MainPage.xaml“.](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)
   ::: moniker-end

   Es gibt zwei Bereiche: den **XAML-Designer** mit einer Entwurfs-Canvas und den **XAML-Editor** zum Hinzufügen oder Ändern von Code.

   ![Der XAML-Designer-Bereich im XAML-Editor](media/uwp-xaml-editor.png)

1. Klicken Sie auf **Toolbox**, um das Toolbox-Flyoutfenster zu öffnen.

   ![Klicken Sie auf „Toolbox“, um das Toolbox-Flyoutfenster zu öffnen.](media/uwp-toolbox.png)

   (Wenn Ihnen die Option **Toolbox** nicht angezeigt wird, können Sie sie über die Menüleiste öffnen. Hierzu wählen Sie **Ansicht** > **Symbolleiste**. Drücken Sie alternativ auf **STRG**+**ALT**+**X**.)

1. Klicken Sie auf das **Stecknadelsymbol**, um das Toolbox-Fenster anzudocken.

   ![Klicken Sie auf das Stecknadelsymbol, um das Toolbox-Fenster anzudocken.](media/uwp-toolbox-autohide.png)

1. Klicken Sie auf das Steuerelement **Schaltfläche**, und ziehen Sie es auf die Entwurfs-Canvas.

   ![Klicken Sie auf das Steuerelement „Schaltfläche“, und ziehen Sie es auf die Entwurfs-Canvas.](media/uwp-toolbox-add-button-control.png)

   Wenn Sie den Code im **XAML-Editor** betrachten, sehen Sie, dass die Schaltfläche auch dort hinzugefügt wurde:

   ![Anzeigen der Schaltfläche im XAML-Editor](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Hinzufügen einer Bezeichnung zur Schaltfläche

1. Ändern Sie im **XAML-Editor** den Wert für den Schaltflächeninhalt von „Schaltfläche“ in „Hallo Welt!“

   ![Ändern Sie den Wert für den Schaltflächeninhalt in „Hallo Welt“.](media/uwp-change-button-text-in-xaml-code-window.png)

1. Beachten Sie, dass die Schaltfläche auch im **XAML-Designer** geändert wird.

   ![Die Schaltfläche ändert sich auf der Entwurfs-Canvas in „Hallo Welt“.](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Hinzufügen eines Ereignishandlers

Ein „Ereignishandler“ klingt kompliziert, ist aber nur ein anderer Name für Code, der aufgerufen wird, wenn ein Ereignis eintritt. In diesem Fall fügt er der Schaltfläche „Hallo Welt!“ eine Aktion Schaltfläche.

1. Doppelklicken Sie auf der Entwurfs-Canvas auf das Steuerelement „Schaltfläche“.

1. Bearbeiten Sie den Ereignishandlercode in *MainPage.Xaml.cs*, der CodeBehind-Seite.

   An dieser Stelle wird es interessant. Der Standardereignishandler sieht folgendermaßen aus:

   ![Der Standardereignishandler für „Button_Click“ ](media/uwp-button-click-code.png)

   Wir ändern ihn folgendermaßen:

   ![Der neue asynchrone Ereignishandler für „Button_Click“ ](media/uwp-add-hello-world-async-code.png)

   Hier finden Sie den Code zum Kopieren und Einfügen:

   ```C#
   private async void Button_Click(object sender, RoutedEventArgs e)
         {
             MediaElement mediaElement = new MediaElement();
             var synth = new Windows.Media.SpeechSynthesis.SpeechSynthesizer();
             Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream = await synth.SynthesizeTextToStreamAsync("Hello, World!");
             mediaElement.SetSource(stream, stream.ContentType);
             mediaElement.Play();
         }
   ```

#### <a name="what-did-we-just-do"></a>Was haben wir gerade getan?

Der Code verwendet einige Windows-APIs, um eine Sprachsyntheseobjekt zu erstellen, und weist diesem dann Text für die Ausgabe zu. (Weitere Informationen zur Verwendung von `SpeechSynthesis` finden Sie unter <xref:System.Speech.Synthesis>.)

## <a name="run-the-application"></a>Ausführen der Anwendung

::: moniker range="vs-2017"
Jetzt können wir die UWP-App „Hallo Welt“ erstellen, bereitstellen und starten, um sie uns anzusehen. Gehen Sie folgendermaßen vor:

1. Verwenden Sie die Wiedergabeschaltfläche (mit dem Text **Lokaler Computer**), um die Anwendung auf dem lokalen Computer zu starten.

   ![Klicken Sie auf lokaler Computer, um Ihre UWP-App zu starten und zu debuggen.](media/uwp-start-or-debug.png)

   (Alternativ können Sie zum Starten Ihrer App in der Menüleiste auf **Debuggen** > **Debugging starten** klicken oder F5 drücken.)

1. Sehen Sie sich Ihre App an, die gleich nach der Anzeige eines Begrüßungsbildschirms angezeigt wird. Die App sollte ungefähr folgendermaßen aussehen:

   ![Eine UWP-App „Hallo Welt“](media/uwp-hello-world-app.png)

1. Klicken Sie auf die Schaltfläche **Hallo Welt**.

   Ihr Windows 10-Gerät sagt laut „Hallo Welt!“.

1. Klicken Sie in der Symbolleiste auf die Schaltfläche **Debuggen beenden**, um die App zu schließen. (Alternativ können Sie auf der Menüleiste auf **Debuggen** > **Debuggen beenden** auswählen oder UMSCHALT+F5 drücken.)

::: moniker-end
::: moniker range=">=vs-2019"
Jetzt können wir die UWP-App „Hallo Welt“ erstellen, bereitstellen und starten, um sie uns anzusehen. Gehen Sie folgendermaßen vor:

1. Verwenden Sie die Wiedergabeschaltfläche (mit dem Text **Lokaler Computer**), um die Anwendung auf dem lokalen Computer zu starten.

   ![Klicken Sie auf lokaler Computer, um Ihre UWP-App zu starten und zu debuggen.](media/uwp-start-or-debug.png)

   (Alternativ können Sie zum Starten Ihrer App in der Menüleiste auf **Debuggen** > **Debugging starten** klicken oder F5 drücken.)

1. Sehen Sie sich Ihre App an, die gleich nach der Anzeige eines Begrüßungsbildschirms angezeigt wird. Die App sollte ungefähr folgendermaßen aussehen:

   ![UWP-App „Hallo Welt“](media/vs-2019/uwp-hello-world-app.png)

1. Klicken Sie auf die Schaltfläche **Hallo Welt**.

   Ihr Windows 10-Gerät sagt laut „Hallo Welt!“.

1. Klicken Sie in der Symbolleiste auf die Schaltfläche **Debuggen beenden**, um die App zu schließen. (Alternativ können Sie auf der Menüleiste auf **Debuggen** > **Debuggen beenden** auswählen oder UMSCHALT+F5 drücken.)

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

Damit haben Sie das Tutorial erfolgreich abgeschlossen. Wir hoffen, Sie haben einige Grundlagen zu UWP und der Visual Studio-IDE erlernt. Fahren Sie für weitere Informationen mit dem folgenden Tutorial fort:

> [!div class="nextstepaction"]
> [Erstellen einer Benutzeroberfläche](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>Siehe auch

- [UWP-Übersicht](/windows/uwp/get-started/universal-application-platform-guide)
- [Beispiele für UWP-Apps](/windows/uwp/get-started/get-uwp-app-samples)
