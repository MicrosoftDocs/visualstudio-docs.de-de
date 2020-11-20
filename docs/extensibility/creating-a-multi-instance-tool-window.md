---
title: Erstellen eines Tool Fensters mit mehreren Instanzen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Tool Fenster so ändern, dass mehrere Instanzen von gleichzeitig geöffnet werden können. Standardmäßig kann für Tool Fenster nur eine Instanz geöffnet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10de60620bcd0b56f251955f478d4d06c984d021
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974006"
---
# <a name="create-a-multi-instance-tool-window"></a>Erstellen eines Tool Fensters mit mehreren Instanzen
Sie können ein Tool Fenster programmieren, sodass mehrere Instanzen von gleichzeitig geöffnet werden können. Standardmäßig kann für Tool Fenster nur eine Instanz geöffnet werden.

Wenn Sie ein Tool Fenster mit mehreren Instanzen verwenden, können Sie mehrere verwandte Quellen von Informationen gleichzeitig anzeigen. Sie könnten z. b. ein mehrzeilige- <xref:System.Windows.Forms.TextBox> Steuerelement in einem Tool Fenster mit mehreren Instanzen platzieren, damit mehrere Code Ausschnitte gleichzeitig während einer Programmier Sitzung verfügbar sind. Sie können z. b. ein <xref:System.Windows.Forms.DataGrid> -Steuerelement und ein Dropdown-Listenfeld in einem Tool Fenster mit mehreren Instanzen platzieren, damit mehrere Echtzeitdaten Quellen gleichzeitig nachverfolgt werden können.

## <a name="create-a-basic-single-instance-tool-window"></a>Erstellen eines einfachen Tool Fensters (Einzel Instanz)

1. Erstellen Sie ein Projekt mit dem Namen **multiinstancetoolwindow** mithilfe der VSIX-Vorlage, und fügen Sie eine benutzerdefinierte Tool Fenster-Element Vorlage mit dem Namen **mitoolwindow** hinzu.

    > [!NOTE]
    > Weitere Informationen zum Erstellen einer Erweiterung mit einem Tool Fenster finden Sie unter [Erstellen einer Erweiterung mit einem Tool Fenster](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="make-a-tool-window-multi-instance"></a>Erstellen eines Tool Fensters mit mehreren Instanzen

1. Öffnen Sie die Datei *MIToolWindowPackage.cs* , und suchen Sie nach dem- `ProvideToolWindow` Attribut. und den- `MultiInstances=true` Parameter, wie im folgenden Beispiel gezeigt:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. Suchen Sie in der Datei *MIToolWindowCommand.cs* die- `ShowToolWindos()` Methode. Bei dieser Methode wird die <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> -Methode aufgerufen und das-Flag auf festgelegt, `create` sodass die `false` vorhandenen Tool Fenster Instanzen durchlaufen werden, bis ein verfügbarer `id` gefunden wird.

3. Um eine Tool Fenster Instanz zu erstellen, rufen Sie die <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> -Methode auf, und legen `id` Sie auf einen verfügbaren Wert und dessen- `create` Flag auf fest `true` .

    Standardmäßig ist der Wert des- `id` Parameters der- <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> Methode `0` . Dieser Wert stellt ein Einzel Instanz-Tool Fenster dar. Für mehr als eine Instanz, die gehostet werden soll, muss jede Instanz über einen eigenen eindeutigen verfügen `id` .

4. Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> Methode für das- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Objekt auf, das von der- <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> Eigenschaft der Tool Fenster Instanz zurückgegeben wird.

5. Standardmäßig erstellt die- `ShowToolWindow` Methode, die von der Tool Fenster-Element Vorlage erstellt wird, ein Einzel Instanz-Tool Fenster. Im folgenden Beispiel wird gezeigt, wie Sie die- `ShowToolWindow` Methode ändern, um mehrere-Instanzen zu erstellen.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        for (int i = 0; i < 10; i++)
        {
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);
            if (window == null)
            {
                // Create the window with the first free ID.
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);
                if ((null == window) || (null == window.Frame))
                {
                    throw new NotSupportedException("Cannot create tool window");
                }

            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());
            break;
            }
        }
    }
    ```
