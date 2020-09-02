---
title: Erstellen und Verwalten von modalen Dialog Feldern | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29b0066f201fbb791d471d5cfb433d9a335aa775
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431575"
---
# <a name="creating-and-managing-modal-dialog-boxes"></a>Erstellen und Verwalten von modalen Dialogfeldern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie ein modales Dialogfeld in Visual Studio erstellen, müssen Sie sicherstellen, dass das übergeordnete Fenster des Dialog Felds deaktiviert ist, während das Dialogfeld angezeigt wird, und dann das übergeordnete Fenster erneut aktivieren, nachdem das Dialogfeld geschlossen wurde. Wenn Sie dies nicht tun, erhalten Sie möglicherweise die folgende Fehlermeldung: "Microsoft Visual Studio kann nicht heruntergefahren werden, da ein modales Dialogfeld aktiv ist. Schließen Sie das aktive Dialogfeld, und versuchen Sie es erneut. "  
  
 Hierfür gibt es zwei Möglichkeiten. Die empfohlene Vorgehensweise ist, wenn Sie über ein WPF-Dialogfeld verfügen, dieses von abzuleiten <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> und dann aufzurufen, <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> um das Dialogfeld anzuzeigen. Wenn Sie dies tun, müssen Sie den modalen Zustand des übergeordneten Fensters nicht verwalten.  
  
 Wenn das Dialogfeld nicht WPF ist, oder aus einem anderen Grund die Dialogfeld Klasse nicht von abgeleitet werden kann <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> , müssen Sie das übergeordnete Element des Dialog Felds abrufen, indem Sie aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> und den modalen Zustand selbst verwalten, indem Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> Methode mit dem-Parameter 0 (false) aufrufen, bevor Sie das Dialogfeld anzeigen und die Methode erneut mit dem Parameter 1 (true) aufrufen  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>Erstellen eines Dialog Felds, das von dialogwindow abgeleitet wird  
  
1. Erstellen Sie ein VSIX-Projekt namens **opendialogtest** , und fügen Sie einen Menübefehl mit dem Namen **OpenDialog**hinzu. Weitere Informationen hierzu finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Um die- <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> Klasse zu verwenden, müssen Sie Verweise auf die folgenden Assemblys hinzufügen (auf der Registerkarte Framework im Dialogfeld **Verweis hinzufügen** ):  
  
    - PresentationCore  
  
    - PresentationFramework  
  
    - WindowsBase  
  
    - System.Xaml  
  
3. Fügen Sie in OpenDialog.cs die folgende- `using` Anweisung hinzu:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4. Deklarieren Sie eine Klasse mit dem Namen **testdialogwindow** , die von abgeleitet ist <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> :  
  
    ```csharp  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5. Um das Dialogfeld zu minimieren und zu maximieren, legen Sie <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> und <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> auf true fest:  
  
    ```csharp  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6. Ersetzen Sie in der **OpenDialog. ShowMessageBox** -Methode den vorhandenen Code durch Folgendes:  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7. Erstellen Sie die Anwendung, und führen Sie sie aus. Die experimentelle Instanz von Visual Studio sollte angezeigt werden. **Im Menü Extras** der experimentellen Instanz sollte ein Befehl mit dem Namen **OpenDialog aufrufen**angezeigt werden. Wenn Sie auf diesen Befehl klicken, sollte das Dialogfenster angezeigt werden. Sie sollten das Fenster minimieren und maximieren können.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>Erstellen und Verwalten eines Dialog Felds, das nicht von dialogwindow abgeleitet ist  
  
1. Für dieses Verfahren können Sie die **opendialogtest** -Projekt Mappe verwenden, die Sie im vorherigen Verfahren erstellt haben, mit denselben Assemblyverweisen.  
  
2. Fügen Sie die folgenden `using` Deklarationen hinzu:  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3. Erstellen Sie eine Klasse mit dem Namen **TestDialogWindow2** , die von abgeleitet wird <xref:System.Windows.Window> :  
  
    ```csharp  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4. Fügen Sie einen privaten Verweis hinzu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5. Fügen Sie einen Konstruktor hinzu, der den Verweis auf festlegt <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :  
  
    ```csharp  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6. Ersetzen Sie in der **OpenDialog. ShowMessageBox** -Methode den vorhandenen Code durch Folgendes:  
  
    ```csharp  
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));  
  
    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);  
    //get the owner of this dialog  
    IntPtr hwnd;  
    uiShell.GetDialogOwnerHwnd(out hwnd);  
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;  
    uiShell.EnableModeless(0);  
    try  
    {  
        WindowHelper.ShowModal(testDialog2, hwnd);  
    }  
    finally  
    {  
        // This will take place after the window is closed.  
        uiShell.EnableModeless(1);  
    }  
    ```  
  
7. Erstellen Sie die Anwendung, und führen Sie sie aus. **Im Menü Extras** sollte ein Befehl mit dem Namen **OpenDialog aufrufen**angezeigt werden. Wenn Sie auf diesen Befehl klicken, sollte das Dialogfenster angezeigt werden.
