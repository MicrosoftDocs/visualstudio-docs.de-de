---
title: 'Schritt 1: Erstellen eines Windows Forms-App-Projekts'
description: Hier erfahren Sie, wie Sie ein Windows Forms-App-Projekt für Ihre Bildanzeige erstellen.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76225685a9f68ca6f6cb05f902922f8fa208015d
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480394"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>Schritt 1: Erstellen eines Windows Forms-App-Projekts

Beim Erstellen einer Bildanzeige erstellen Sie im ersten Schritt ein Windows Forms-App-Projekt.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Öffnen Sie Visual Studio 2017.

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Das Dialogfeld sollte in etwa wie auf dem folgenden Screenshot dargestellt aussehen.

     ![Dialogfeld „Neues Projekt“](../ide/media/newprojectdialogcallouts.png)<br/>_Dialogfeld* **_Neues Projekt_* _

2. Wählen Sie im Dialogfeld **Neues Projekt** im linken Bereich **Visual C#** oder **Visual Basic** aus, und klicken Sie dann auf **Windows-Desktop**.

3. Wählen Sie in der Projektvorlagenliste **Windows Forms-App (.NET Framework)** aus. Geben Sie dem neuen Formular den Namen *PictureViewer*, und wählen Sie dann die Schaltfläche **OK** aus.

    >[!NOTE]
    >Wenn Ihnen die Vorlage **Windows Forms-App (.NET Framework)** nicht angezeigt wird, verwenden Sie den Visual Studio-Installer, um die Workload **.NET Desktop-Entwicklung** zu installieren.<br/><br/>![Die Workload „.NET Desktopentwicklung“ im Visual Studio-Installer](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Weitere Informationen finden Sie im Artikel [Installieren von Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Öffnen von Visual Studio 2019

1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   ![Anzeigen des Fensters „Neues Projekt erstellen“](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Geben Sie im Fenster **Neues Projekt erstellen** im Suchfeld den Begriff *Windows Forms* ein. Wählen Sie anschließend **Desktop** aus der Liste **Projekttyp** aus.

   Nachdem Sie den Filter **Projekttyp** angewendet haben, wählen Sie die Vorlage **Windows Forms-App (.NET Framework)** für C# oder Visual Basic aus, und klicken Sie dann auf **Weiter**.

   ![Screenshot: Auswählen der C#- oder Visual Basic-Vorlage für die Windows Forms-App (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Wenn die Vorlage **Windows Forms-App (.NET Framework)** nicht angezeigt wird, können Sie sie über das Fenster **Neues Projekt erstellen** installieren. Wählen Sie in der Meldung **Sie finden nicht, wonach Sie suchen?** den Link **Weitere Tools und Features installieren** aus.
   >
   > ![Link „Weitere Tools und Features installieren“ aus der Meldung „Sie finden nicht, wonach Sie suchen“ im Fenster „Neues Projekt erstellen“](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Wählen Sie anschließend im Visual Studio-Installer die Workload **.NET Desktopentwicklung** aus.
   >
   > ![Die Workload „.NET Core“ im Visual Studio-Installer](../ide/media/install-dot-net-desktop-env.png)
   >
   > Wählen Sie anschließend die Schaltfläche **Ändern** im Visual Studio-Installer aus. Möglicherweise werden Sie aufgefordert, Ihre Arbeit zu speichern; wenn dies der Fall ist, führen Sie das aus. Wählen Sie als Nächstes **Weiter** aus, um die Workload zu installieren.

1. Geben Sie im Fenster **Neues Projekt konfigurieren** im Feld **Projektname** den Begriff *PictureViewer* ein. Wählen Sie anschließend **Erstellen** aus.

::: moniker-end

Visual Studio erstellt eine Projektmappe für die App. Eine Projektmappe fungiert als Container für alle Projekte und Dateien, die Ihre App benötigt. Diese Begriffe werden später ausführlicher in diesem Tutorials erläutert.

## <a name="about-the-windows-forms-app-project"></a>Informationen zum Windows Forms-App-Projekt

1. Die Entwicklungsumgebung enthält drei Fenster: ein Hauptfenster, den **Projektmappen-Explorer** und das Fenster **Eigenschaften**.

     Wenn eines dieser Fenster fehlt, können Sie das Standardfensterlayout wiederherstellen. Klicken Sie in der Menüleiste auf **Fenster** > **Fensterlayout zurücksetzen**.

     Sie können Fenster auch mit den Menübefehlen anzeigen. Klicken Sie in der Menüleiste auf **Anzeigen** > **Eigenschaftenfenster** oder auf **Projektmappen-Explorer**.

     Wenn andere Fenster geöffnet sind, schließen Sie diese mit der Schaltfläche **Schließen** (x), die sich jeweils in der rechten oberen Ecke befindet.

    ::: moniker range="vs-2017"

    * **Hauptfenster** In diesem Fenster führen Sie die meisten Schritte aus, z. B. Arbeiten mit Formularen oder Bearbeiten von Code. Im Fenster wird ein Formular im **Formular-Editor** angezeigt. Oben im Fenster werden die Registerkarte **Startseite** und die Registerkarte **Form1.cs [Entwurf]** angezeigt. (In Visual Basic endet der Registerkartenname mit *.vb* und nicht mit *.cs*.)

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Hauptfenster** In diesem Fenster führen Sie die meisten Schritte aus, z. B. Arbeiten mit Formularen oder Bearbeiten von Code. Im Fenster wird ein Formular im **Formular-Editor** angezeigt.

    ::: moniker-end

    * Fenster **Projektmappen-Explorer**: In diesem Fenster können Sie alle Elemente in der Projektmappe anzeigen und dorthin navigieren.

    Wenn Sie eine Datei auswählen, ändert sich der Inhalt im Fenster **Eigenschaften**. Wenn Sie eine Codedatei (die in C# mit *.cs* und in Visual Basic mit *.vb* endet) öffnen, wird die Codedatei oder ein Designer für die Codedatei angezeigt. Ein Designer ist eine visuelle Oberfläche, der Sie Steuerelemente wie Schaltflächen und Listen hinzufügen können. Für Visual Studio-Formulare wird der Designer als **Windows Forms-Designer** bezeichnet.

    * **Eigenschaftenfenster:** In diesem Fenster können Sie die Eigenschaften von Elementen ändern, die Sie in den anderen Fenstern auswählen. Wenn Sie z. B. Form1 auswählen, können Sie den Titel ändern, indem Sie die Eigenschaft **Text** festlegen, und die Hintergrundfarbe ändern, indem Sie die Eigenschaft **Hintergrundfarbe** festlegen.

      > [!NOTE]
      > In der obersten Zeile im **Projektmappen-Explorer** wird **Projektmappe ‚PictureViewer‘ (1 Projekt)** angezeigt, was bedeutet, dass Visual Studio eine Projektmappe für Sie erstellt hat. Eine Projektmappe kann mehr als ein Projekt enthalten. Vorerst arbeiten Sie jedoch mit Projektmappen, die nur ein Projekt enthalten.

1. Klicken Sie in der Menüleiste auf **Datei** > **Alle speichern**.

     Klicken Sie alternativ in der Symbolleiste auf die im folgenden Bild gezeigte Schaltfläche **Alle speichern**.

     Schaltfläche ![Alle speichern](../ide/media/express_iconsaveall.png) in der Symbolleiste<br/>
     _Symbolleistenschaltfläche* **_Alle speichern_* _

     Visual Studio fügt automatisch den Ordnernamen und den Projektnamen ein und speichert das Projekt dann im Projektordner.

## <a name="next-steps"></a>Nächste Schritte

* Den nächsten Schritt des Tutorials finden Sie unter **[Schritt 2: Ausführen der App](../ide/step-2-run-your-program.md)** .

* Um zum Übersichtsthema zurückzukehren, beachten Sie [Tutorial 1: Create a picture viewer (Tutorial 1: Erstellen eines Bildanzeigeprogramms)](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Weitere Informationen

* [Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Erstellen eines Vergleichsspiels](tutorial-3-create-a-matching-game.md)
