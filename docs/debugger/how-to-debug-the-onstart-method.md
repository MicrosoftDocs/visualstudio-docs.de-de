---
title: Debuggen der OnStart-Methode | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die OnStart-Methode eines Windows-Diensts in Visual Studio debuggen, indem Sie den Debugger aus der Methode heraus starten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 488fe471552256e8fad62bb6f831448811ca343f
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903141"
---
# <a name="how-to-debug-the-onstart-method"></a>Vorgehensweise: Debuggen der OnStart-Methode
Sie können einen Windows-Dienst debuggen, indem Sie den Dienst starten und den Debugger an den Dienstprozess anfügen. Weitere Informationen finden Sie unter [Vorgehensweise: Debuggen von Windows-Dienstanwendungen](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Zum Debuggen der <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> -Methode eines Windows-Diensts müssen Sie den Debugger allerdings aus der Methode starten.

1. Fügen Sie am Anfang der <xref:System.Diagnostics.Debugger.Launch%2A> -Methode einen Aufruf von `OnStart()`hinzu.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Starten Sie den Dienst (dazu können Sie `net start`oder das Fenster **Dienste** verwenden).

    Ein Dialogfeld ähnlich dem folgenden sollte angezeigt werden:

    ![Screenshot eines Dialogfelds „Just-in-Time-Debugger“ in Visual Studio, in dem eine nicht behandelte .NET Framework-Ausnahme in WindowsService-Asis.exe gezeigt wird.](../debugger/media/onstartdebug.png)

3. Wählen Sie **Ja\<service name> aus.**

4. Wählen Sie im Fenster des Just-In-Time-Debuggers die Version von Visual Studio aus, die Sie zum Debuggen verwenden möchten.

    ![Screenshot eines Visual Studio-Fensters „Just-In-Time-Debugger“, wobei in der Liste „Mögliche Debugger“ die Option „Neue Instanz von Microsoft Visual Studio 2015“ ausgewählt ist.](../debugger/media/justintimedebugger.png)

5. Eine neue Instanz von Visual Studio wird gestartet, und die Ausführung wird beim Erreichen der `Debugger.Launch()` -Methode beendet.

## <a name="see-also"></a>Siehe auch
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
