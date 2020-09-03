---
title: Verwalten mehrerer Threads in verwaltetem Code | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 296ef23bc512a86917920b3c3d5fbb5ec203a21e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387017"
---
# <a name="managing-multiple-threads-in-managed-code"></a>Verwalten von mehreren Threads in verwaltetem Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie über eine verwaltete VSPackage-Erweiterung verfügen, die asynchrone Methoden aufruft oder Vorgänge ausführt, die auf anderen Threads als dem UI-Thread von Visual Studio ausgeführt werden, sollten Sie die unten aufgeführten Richtlinien befolgen. Sie können verhindern, dass der UI-Thread reaktionsfähig ist, weil er nicht auf den Abschluss der Arbeit in einem anderen Thread warten muss. Sie können Ihren Code effizienter gestalten, da Sie nicht über zusätzliche Threads verfügen, die Stapel Speicher beanspruchen, und Sie können die Zuverlässigkeit und das Debuggen vereinfachen, da Sie Deadlocks und nicht Reaktionsfähigkeit vermeiden.  
  
 Im Allgemeinen können Sie vom UI-Thread zu einem anderen Thread wechseln oder umgekehrt. Wenn die Methode zurückgibt, ist der aktuelle Thread der Thread, von dem er ursprünglich aufgerufen wurde.  
  
> [!IMPORTANT]
> In den folgenden Richtlinien werden die APIs im- <xref:Microsoft.VisualStudio.Threading> Namespace verwendet, insbesondere die- <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> Klasse. Die APIs in diesem Namespace sind neu in [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] . Sie können eine Instanz eines- <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> Objekts aus der- <xref:Microsoft.VisualStudio.Shell.ThreadHelper> Eigenschaft erhalten `ThreadHelper.JoinableTaskFactory` .  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Wechseln vom UI-Thread zu einem Hintergrund Thread  
  
1. Wenn Sie sich im UI-Thread befinden und asynchrone Arbeit an einem Hintergrund Thread ausführen möchten, verwenden Sie "Task. Run ()":  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2. Wenn Sie sich im UI-Thread befinden und beim Ausführen von Arbeit an einem Hintergrund Thread synchron blockieren möchten, verwenden Sie die- <xref:System.Threading.Tasks.TaskScheduler> Eigenschaft `TaskScheduler.Default` in <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> :  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Wechseln von einem Hintergrund Thread zum UI-Thread  
  
1. Wenn Sie sich in einem Hintergrund Thread befinden und etwas im UI-Thread ausführen möchten, verwenden Sie Folgendes <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> :  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Sie können die- <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> Methode verwenden, um zum UI-Thread zu wechseln. Diese Methode sendet eine Meldung an den UI-Thread, wobei die aktuelle asynchrone Methode fortgesetzt wird. Außerdem kommuniziert Sie mit dem Rest des Threading Frameworks, um die korrekte Priorität festzulegen und Deadlocks zu vermeiden.  
  
     Wenn die Hintergrund Thread Methode nicht asynchron ist und Sie Sie nicht asynchron machen können, können Sie die-Syntax weiterhin verwenden, um `await` zum UI-Thread zu wechseln, indem Sie die Arbeit mit umschließen <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> , wie im folgenden Beispiel gezeigt:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
