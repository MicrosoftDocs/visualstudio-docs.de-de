---
title: Abonnieren eines Ereignisses | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein Tool Fenster erstellen, das auf Ereignisse in einer laufenden Dokument Tabelle im Visual Studio SDK antwortet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c739dad7be8d2a000662eca478bc117699694c8a
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715872"
---
# <a name="subscribing-to-an-event"></a>Abonnieren eines Ereignisses
In dieser exemplarischen Vorgehensweise wird erläutert, wie ein Tool Fenster erstellt wird, das auf Ereignisse in einer laufenden dokumententabelle (RDT) antwortet. Ein Tool Fenster hostet ein Benutzer Steuerelement, das implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> . Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Methode verbindet die-Schnittstelle mit den Ereignissen.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Abonnieren von RDT-Ereignissen

#### <a name="to-create-an-extension-with-a-tool-window"></a>So erstellen Sie eine Erweiterung mit einem Tool Fenster

1. Erstellen Sie ein Projekt mit dem Namen **rdtexplorer** mithilfe der VSIX-Vorlage, und fügen Sie eine benutzerdefinierte Tool Fenster-Element Vorlage mit dem Namen **rdtexplorerwindow** hinzu.

     Weitere Informationen zum Erstellen einer Erweiterung mit einem Tool Fenster finden Sie unter [Erstellen einer Erweiterung mit einem Tool Fenster](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>So abonnieren Sie RDT-Ereignisse

1. Öffnen Sie die Datei "rdtexplorerwindowcontrol. XAML", und löschen Sie die Schaltfläche mit dem Namen `button1` . Fügen Sie ein Steuerelement hinzu, <xref:System.Windows.Forms.ListBox> und akzeptieren Sie den Standardnamen. Das Raster Element sollte wie folgt aussehen:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Öffnen Sie die Datei RDTExplorerWindow.cs in der Code Ansicht. Fügen Sie am Anfang der Datei die folgenden using-Direktiven hinzu.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Ändern Sie die- `RDTExplorerWindow` Klasse so, dass Sie zusätzlich zur Ableitung von der- <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Klasse die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> Schnittstelle implementiert.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implementieren Sie die-Schnittstelle. Platzieren Sie den Cursor auf dem IVsRunningDocTableEvents-Namen. Am linken Rand sollte eine Glühbirne angezeigt werden. Klicken Sie rechts neben der Glühbirne auf den Pfeil nach unten, und wählen Sie **Schnittstelle implementieren** aus.

5. Ersetzen Sie in jeder Methode in der Schnittstelle die Zeile `throw new NotImplementedException();` durch Folgendes:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Fügen Sie ein Cookie-Feld zur rdtexplorerwindow-Klasse hinzu.

    ```csharp
    private uint rdtCookie;
    ```

     Dies enthält das Cookie, das von der-Methode zurückgegeben wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> .

7. Überschreiben Sie die Initialize ()-Methode von rdtexplorerwindow, um für RDT-Ereignisse zu registrieren. Sie sollten Dienste immer in der Initialize ()-Methode des ToolWindowPane erhalten, nicht im Konstruktor.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Der <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> Dienst wird aufgerufen, um eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> Schnittstelle zu erhalten. Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> Methode verbindet RDT-Ereignisse mit einem Objekt, das <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> in diesem Fall ein rdtexplorer-Objekt implementiert.

8. Aktualisieren Sie die Methode "verwerfen ()" von rdtexplorerwindow.

    ```csharp
    protected override void Dispose(bool disposing)
    {
        // Release the RDT cookie.
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));
        rdt.UnadviseRunningDocTableEvents(rdtCookie);

        base.Dispose(disposing);
    }
    ```

     Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> -Methode löscht die Verbindung zwischen `RDTExplorer` und RDT-Ereignis Benachrichtigung.

9. Fügen Sie die folgende Zeile in den Text des <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> Handlers ein, direkt vor der- `return` Anweisung.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Fügen Sie dem Text des <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> Handlers und anderen Ereignissen, die im Listenfeld angezeigt werden sollen, eine ähnliche Zeile hinzu.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.

12. Öffnen Sie **rdtexplorerwindow** (**View/other Windows/rdtexplorerwindow**).

     Das Fenster **rdtexplorerwindow** wird mit einer leeren Ereignisliste geöffnet.

13. Öffnen oder erstellen Sie eine Projekt Mappe.

     Wenn `OnBeforeLastDocument` -und- `OnAfterFirstDocument` Ereignisse ausgelöst werden, wird die Benachrichtigung jedes Ereignisses in der Ereignisliste angezeigt.
