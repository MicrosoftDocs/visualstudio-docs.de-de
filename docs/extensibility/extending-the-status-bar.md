---
title: Erweitern der Status Leiste | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Visual Studio-Statusleiste am unteren Rand der IDE erweitern, in der Informationen angezeigt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7776c7fa35cd7ac06dec60ced3604cb67c96da4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903204"
---
# <a name="extend-the-status-bar"></a>Erweitern der Statusleiste
Sie können die Visual Studio-Statusleiste unten in der IDE verwenden, um Informationen anzuzeigen.

 Wenn Sie die Statusleiste erweitern, können Sie Informationen und die Benutzeroberfläche in vier Regionen anzeigen: den Feedback Bereich, die Statusanzeige, den Animations Bereich und den Designer Bereich. Der Feedback Bereich ermöglicht es Ihnen, Text anzuzeigen und den angezeigten Text hervorzuheben. Die Statusanzeige zeigt den inkrementellen Fortschritt für Vorgänge mit kurzer Laufzeit, z. b Der Animations Bereich zeigt eine fortlaufend Loopende Animation für Vorgänge mit langer Ausführungsdauer oder einen Vorgang mit unbestimmter Länge an, z. b. das entwickeln mehrerer Projekte in einer Projekt Mappe. Und der Designer Bereich zeigt die Zeilen-und Spaltennummer der Cursorposition an.

 Sie können die Statusleiste mithilfe der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> Schnittstelle (aus dem- <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> Dienst) erhalten. Darüber hinaus kann jedes Objekt, das auf einem Fensterrahmen positioniert ist, als Client Objekt der Statusleiste registriert werden, indem die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> Schnittstelle implementiert wird. Wenn ein Fenster aktiviert ist, fragt Visual Studio das Objekt ab, das in diesem Fenster für die `IVsStatusbarUser` Schnittstelle positioniert ist. Wenn Sie gefunden wird, wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> -Methode für die zurückgegebene Schnittstelle aufgerufen, und das-Objekt kann die Statusleiste innerhalb dieser Methode aktualisieren. Dokument Fenster können z. b. die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Methode verwenden, um Informationen im Designer Bereich zu aktualisieren, wenn Sie aktiv werden.

 In den folgenden Verfahren wird davon ausgegangen, dass Sie wissen, wie Sie ein VSIX-Projekt erstellen und einen benutzerdefinierten Menübefehl hinzufügen. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="modify-the-status-bar"></a>Ändern der Statusleiste
 In diesem Verfahren wird gezeigt, wie Sie Text festlegen und aufrufen, statischen Text anzeigen und den angezeigten Text im Feedback Bereich der Statusleiste hervorheben.

### <a name="read-and-write-to-the-status-bar"></a>Lese-und Schreibzugriff auf die Statusleiste

1. Erstellen Sie ein VSIX-Projekt mit dem Namen " **Teststatus-Erweiterung** ", und fügen Sie einen Menübefehl mit dem Namen **Teststatus**

2. Ersetzen Sie in *TestStatusBarCommand.cs* den Befehls handlermethodencode ( `MenuItemCallback` ) durch den folgenden Code:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Make sure the status bar is not frozen
        int frozen;

        statusBar.IsFrozen(out frozen);

        if (frozen != 0)
        {
            statusBar.FreezeOutput(0);
        }

        // Set the status bar text and make its display static.
        statusBar.SetText("We just wrote to the status bar.");

        // Freeze the status bar.
        statusBar.FreezeOutput(1);

        // Get the status bar text.
        string text;
        statusBar.GetText(out text);
        System.Windows.Forms.MessageBox.Show(text);

        // Clear the status bar text.
        statusBar.FreezeOutput(0);
        statusBar.Clear();
    }
    ```

3. Kompilieren Sie den Code, und starten Sie das Debugging.

4. Öffnen Sie **das Menü Extras in der experimentellen** Instanz von Visual Studio. Klicken Sie auf die Schaltfläche **Teststatus-barcommand aufrufen** .

     Sie sollten sehen, dass der Text in der Statusleiste nun **gerade in die Statusleiste geschrieben wird.** und das Meldungs Feld, das angezeigt wird, hat denselben Text.

### <a name="update-the-progress-bar"></a>Aktualisieren der Statusanzeige

1. In diesem Verfahren wird erläutert, wie Sie die Statusanzeige initialisieren und aktualisieren.

2. Öffnen Sie die Datei *TestStatusBarCommand.cs* , und ersetzen Sie die- `MenuItemCallback` Methode durch den folgenden Code:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));
        uint cookie = 0;
        string label = "Writing to the progress bar";

        // Initialize the progress bar.
        statusBar.Progress(ref cookie, 1, "", 0, 0);

        for (uint i = 0, total = 20; i <= total; i++)
        {
            // Display progress every second.
            statusBar.Progress(ref cookie, 1, label, i, total);
            System.Threading.Thread.Sleep(1000);
        }

        // Clear the progress bar.
        statusBar.Progress(ref cookie, 0, "", 0, 0);
    }
    ```

3. Kompilieren Sie den Code, und starten Sie das Debugging.

4. Öffnen Sie **das Menü Extras in der experimentellen** Instanz von Visual Studio. Klicken Sie auf die Schaltfläche **Teststatus-Befehlszeile aufrufen** .

     Sie sollten sehen, dass der Text in der Statusleiste jetzt in die Statusanzeige **schreibt.** Außerdem sollten Sie sehen, dass die Statusanzeige für 20 Sekunden jede Sekunde aktualisiert wird. Danach werden die Statusleiste und die Statusleiste gelöscht.

### <a name="display-an-animation"></a>Anzeigen einer Animation

1. Die Statusleiste zeigt eine Schleifen Animation an, die entweder einen Vorgang mit langer Ausführungszeit anzeigt (z. b. das entwickeln mehrerer Projekte in einer Projekt Mappe). Wenn diese Animation nicht angezeigt wird, stellen Sie sicher, dass Sie über die richtigen **Tools**-  >  **options** Einstellungen verfügen:

     Wechseln Sie zu Extras  >  **Optionen**  >  Registerkarte **Allgemein** , und deaktivieren Sie **visuelle Darstellung automatisch basierend auf der Client Leistung anpassen**. Aktivieren Sie dann die unter Option umfassende **visuelle Client Darstellung aktivieren**. Sie sollten jetzt in der Lage sein, die Animation anzuzeigen, wenn Sie das Projekt in ihrer experimentellen Instanz von Visual Studio erstellen.

     In diesem Verfahren wird die standardmäßige Visual Studio-Animation angezeigt, die das Projekt oder die Projekt Mappe bildet.

2. Öffnen Sie die Datei *TestStatusBarCommand.cs* , und ersetzen Sie die- `MenuItemCallback` Methode durch den folgenden Code:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));

        // Use the standard Visual Studio icon for building.
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;

        // Display the icon in the Animation region.
        statusBar.Animation(1, ref icon);

        // The message box pauses execution for you to look at the animation.
        System.Windows.Forms.MessageBox.Show("showing?");

        // Stop the animation.
        statusBar.Animation(0, ref icon);
    }
    ```

3. Kompilieren Sie den Code, und starten Sie das Debugging.

4. Öffnen Sie **das Menü Extras in der experimentellen** Instanz von Visual Studio, und klicken Sie auf **Teststatus-barcommand aufrufen**.

     Wenn das Meldungs Feld angezeigt wird, sollte die Animation in der Statusleiste ganz rechts angezeigt werden. Wenn Sie das Meldungs Feld schließen, wird die Animation nicht mehr angezeigt.
