---
title: Erweitern der Ausgabefenster | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie das Ausgabefenster im Visual Studio SDK erweitern und eigene benutzerdefinierte Bereiche erstellen und verwalten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91c59737d269af4eb91df402f38346cf41e3146e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961767"
---
# <a name="extend-the-output-window"></a>Erweitern des Ausgabe Fensters
Das Fenster **Ausgabe** ist ein Satz von Textbereichen mit Lese-/Schreibzugriff. Visual Studio verfügt über die folgenden integrierten Bereiche: **Build**, in denen Projekte Nachrichten über Builds und **Allgemeine** Informationen kommunizieren, in denen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nachrichten über die IDE kommuniziert. Projekte erhalten automatisch einen Verweis auf den Bereich **Build** über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> Schnittstellen Methoden, und Visual Studio bietet direkten Zugriff auf den **allgemeinen** Bereich über den <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> Dienst. Zusätzlich zu den integrierten Bereichen können Sie eigene benutzerdefinierte Bereiche erstellen und verwalten.

 Sie können das **Ausgabe** Fenster direkt über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> -Schnittstelle und die-Schnittstelle steuern <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> . Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Schnittstelle, die vom Dienst angeboten wird <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> , definiert Methoden zum Erstellen, abrufen und zerstören von **Ausgabe** Fensterbereichen. Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> Schnittstelle definiert Methoden, um Bereiche anzuzeigen, Bereiche zu verbergen und Ihren Text zu bearbeiten. Eine alternative Möglichkeit, das **Ausgabe** Fenster zu steuern, ist die über das <xref:EnvDTE.OutputWindow> -Objekt und das- <xref:EnvDTE.OutputWindowPane> Objekt im Visual Studio-Automatisierungs Objektmodell. Diese Objekte Kapseln fast alle Funktionen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> -Schnittstelle und der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> Schnittstelle. Außerdem werden mit dem <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> -Objekt und dem-Objekt einige Funktionen höherer Ebene hinzugefügt, um die Enumeration der Fensterbereiche des **Ausgabe** Fensters und das Abrufen von Text aus den Bereichen zu vereinfachen.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Erstellen einer Erweiterung, die den Ausgabebereich verwendet
 Sie können eine Erweiterung erstellen, mit der verschiedene Aspekte des Ausgabe Bereichs trainiert werden.

1. Erstellen Sie ein VSIX-Projekt namens `TestOutput` mit einem Menübefehl mit dem Namen " **testoutput**". Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Fügen Sie die folgenden Verweise hinzu:

    1. EnvDTE

    2. EnvDTE80

3. Fügen Sie in *TestOutput.cs* die folgende using-Anweisung hinzu:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. Löschen Sie in *TestOutput.cs* die- `ShowMessageBox` Methode. Fügen Sie den folgenden Methodenstub hinzu:

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. Ändern Sie im testoutput-Konstruktor den Befehls Handler in outputcommandhandler. Hier ist der Teil, in dem die Befehle hinzugefügt werden:

    ```csharp
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    if (commandService != null)
    {
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
        EventHandler eventHandler = OutputCommandHandler;
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

6. In den folgenden Abschnitten finden Sie verschiedene Methoden, die verschiedene Möglichkeiten zum Umgang mit dem Ausgabebereich veranschaulichen. Sie können diese Methoden als Text der-Methode aufzurufen `OutputCommandHandler()` . Der folgende Code fügt z. b. die-Methode hinzu, die `CreatePane()` im nächsten Abschnitt angegeben wird.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Erstellen eines Ausgabe Fensters mit ivsoutputwindow
 Dieses Beispiel zeigt, wie ein neuer **Ausgabe** Fensterbereich mithilfe der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Schnittstelle erstellt wird.

```csharp
void CreatePane(Guid paneGuid, string title,
    bool visible, bool clearWithSolution)
{
    IVsOutputWindow output =
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));
    IVsOutputWindowPane pane;

    // Create a new pane.
    output.CreatePane(
        ref paneGuid,
        title,
        Convert.ToInt32(visible),
        Convert.ToInt32(clearWithSolution));

    // Retrieve the new pane.
    output.GetPane(ref paneGuid, out pane);

     pane.OutputString("This is the Created Pane \n");
}
```

 Wenn Sie diese Methode der Erweiterung hinzufügen, die im vorherigen Abschnitt angegeben wurde, sollten Sie beim Klicken auf den Befehl " **testoutput aufrufen** " das **Ausgabe** Fenster mit einem Header anzeigen, der besagt, dass **Ausgabe anzeigen aus: "kreatedpane" angezeigt** **wird. Dies ist der erstellte** Bereich im Bereich.

## <a name="create-an-output-window-with-outputwindow"></a>Erstellen eines Ausgabe Fensters mit OutputWindow
 In diesem Beispiel wird gezeigt, wie ein **Ausgabe** Fensterbereich mithilfe des-Objekts erstellt wird <xref:EnvDTE.OutputWindow> .

```csharp
void CreatePane(string title)
{
    DTE2 dte = (DTE2)GetService(typeof(DTE));
    OutputWindowPanes panes =
        dte.ToolWindows.OutputWindow.OutputWindowPanes;

    try
    {
        // If the pane exists already, write to it.
        panes.Item(title);
    }
    catch (ArgumentException)
    {
        // Create a new pane and write to it.
        panes.Add(title);
    }
}
```

 Obwohl die-Auflistung das <xref:EnvDTE.OutputWindowPanes> Abrufen eines **Ausgabe** Fenster Bereichs anhand seines Titels ermöglicht, ist es nicht gewährleistet, dass Pane-Titel eindeutig sind. Wenn Sie die Eindeutigkeit eines Titels zweifelhaft sind, verwenden Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> Methode, um den korrekten Bereich anhand seiner GUID abzurufen.

 Wenn Sie diese Methode der Erweiterung hinzufügen, die im vorherigen Abschnitt angegeben wurde, sollten Sie beim Klicken auf den Befehl " **testoutput aufrufen** " das Ausgabefenster mit einem Header anzeigen, der den Befehl **Ausgabe aus: dtepane anzeigen** und den Bereich für **hinzugefügte DTE** -Elemente im Bereich selbst.

## <a name="delete-an-output-window"></a>Löschen eines Ausgabe Fensters
 Dieses Beispiel zeigt, wie ein **Ausgabe** Fensterbereich gelöscht wird.

```csharp
void DeletePane(Guid paneGuid)
{
    IVsOutputWindow output =
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));

    IVsOutputWindowPane pane;
    output.GetPane(ref paneGuid, out pane);

    if (pane == null)
    {
        CreatePane(paneGuid, "New Pane\n", true, true);
    }
     else
    {
        output.DeletePane(ref paneGuid);
    }
}
```

 Wenn Sie diese Methode der Erweiterung hinzufügen, die im vorherigen Abschnitt angegeben wurde, sollten Sie beim Klicken auf den Befehl **testoutput aufrufen** das Fenster Ausgabe mit einem Header mit dem Text **Ausgabe anzeigen aus: neuer** Bereich und den Text **hinzugefügten** Bereich im Bereich Selbstanzeigen. Wenn Sie erneut auf den Befehl " **testoutput aufrufen** " klicken, wird der Bereich gelöscht.

## <a name="get-the-general-pane-of-the-output-window"></a>Bereich "Allgemein" des Ausgabe Fensters
 Dieses Beispiel zeigt, wie Sie den integrierten **allgemeinen** Bereich des **Ausgabe** Fensters erhalten.

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Wenn Sie diese Methode der Erweiterung hinzufügen, die im vorherigen Abschnitt angegeben wurde, sollten Sie beim Klicken auf den Befehl **testoutput aufrufen** sehen, dass im Fenster **Ausgabe** der Bereich **Allgemeine** Wörter angezeigt wird.

## <a name="get-the-build-pane-of-the-output-window"></a>Bereich "Build" des Ausgabe Fensters
 Dieses Beispiel zeigt, wie **Sie den** Buildbereich suchen und darin schreiben. Da der Bereich " **Build** " nicht standardmäßig aktiviert ist, wird er ebenfalls aktiviert.

```csharp
void OutputTaskItemStringExExample(string buildMessage)
{
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));

    EnvDTE.OutputWindowPanes panes =
        dte.ToolWindows.OutputWindow.OutputWindowPanes;
    foreach (EnvDTE.OutputWindowPane pane in panes)
        {
            if (pane.Name.Contains("Build"))
            {
                pane.OutputString(buildMessage + "\n");
                pane.Activate();
                return;
             }
        }
}
```
