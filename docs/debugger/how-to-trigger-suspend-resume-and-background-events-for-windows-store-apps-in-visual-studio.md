---
title: Auslösen von Anhalte-, Fortsetzungs- oder Hintergrundereignissen beim Debuggen von UWP-Apps
description: In diesem Artikel erfahren Sie, wie Sie Anhalte-, Fortsetzungs- und Hintergrundereignisse beim Debuggen von UWP-Apps (Universelle Windows-Plattform) in Visual Studio auslösen.
ms.custom: SEO-VS-2020
ms.date: 01/16/2018
ms.topic: how-to
f1_keywords:
- vs.debug.error.background_task_activate_failure
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 87b2718b6cd9db5b66635ca165253bd1e93f17d5
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150677"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-while-debugging-uwp-apps-in-visual-studio"></a>Auslösen von Anhalte-, Fortsetzungs- und Hintergrundereignissen beim Debuggen von UWP-Apps in Visual Studio

Wenn Sie nicht debuggen, steuert die Windows-PLM ( **Process Lifetime Management** , Prozessverwaltung für Lebensdauer) den Ausführungszustand der App, d. h. das Starten, Anhalten, Fortsetzen und Beenden der App als Reaktion auf Benutzeraktionen und den Gerätezustand. Wenn Sie debuggen, deaktiviert Windows diese Aktivierungsereignisse. In diesem Thema wird beschrieben, wie solche Ereignisse im Debugger ausgelöst werden.

Außerdem wird in diesem Thema das Debuggen von **Hintergrundaufgaben** beschrieben. Hintergrundaufgaben ermöglichen das Ausführen bestimmte Vorgänge in einem Hintergrundprozess, selbst wenn Ihre App nicht ausgeführt wird. Sie können den Debugger verwenden, um die App in den Debugmodus zu versetzen und die Hintergrundaufgabe anschließend zu debuggen, ohne die Benutzeroberfläche zu starten.

Weitere Informationen zur Verwaltung der Prozesslebensdauer und zu Hintergrundaufgaben finden Sie unter [Starten, Fortsetzen und Multitasking](/windows/uwp/launch-resume/index).

## <a name="trigger-process-lifetime-management-events"></a><a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Auslösen von Ereignissen der Prozesslebensdauer-Verwaltung
 Windows kann die App anhalten, wenn der Benutzer diese verlässt oder Windows in den Energiesparmodus wechselt. Sie können auf das `Suspending` -Ereignis reagieren, um relevante App- und Benutzerdaten im permanenten Speicher zu speichern und Ressourcen freizugeben. Wenn eine Anwendung nach dem Zustand **Angehalten** fortgesetzt wird, wechselt sie in den Zustand **Aktiv** und wird an der Position fortgesetzt, an der sie angehalten wurde. Sie können auf das `Resuming` -Ereignis reagieren, um den Anwendungszustand zu aktualisieren oder wiederherzustellen und Ressourcen zurückzufordern.

 Obwohl Windows versucht, so viele angehaltene Apps wie möglich im Arbeitsspeicher zu behalten, kann die App beendet werden, wenn die Ressourcen nicht ausreichen, um sie im Arbeitsspeicher zu behalten. Außerdem Ihre App auch durch einen Benutzer explizit geschlossen werden. Es gibt kein gesondertes Ereignis, um anzugeben, dass die App durch den Benutzer geschlossen wurde.

 Im Visual Studio-Debugger können Sie Ihre Apps manuell anhalten, fortsetzen und beenden, um Prozesslebenszyklusereignisse zu debuggen. So debuggen Sie ein Prozesslebenszyklusereignis:

1. Legen Sie einen Haltepunkt im Handler des Ereignisses fest, das Sie debuggen möchten.

2. Drücken Sie die Taste **F5** , um mit dem Debuggen zu beginnen.

3. Wählen Sie auf der Symbolleiste **Debugspeicherort** das Ereignis aus, das Sie auslösen möchten:

     ![Aufgaben für Unterbrechen, Wiederaufnehmen, Beenden und Hintergrund](../debugger/media/dbg_suspendresumebackground.png)

     Die Option **Anhalten und beenden** schließt die App und beendet die Debugsitzung.

## <a name="trigger-background-tasks"></a><a name="BKMK_Trigger_background_tasks"></a> Auslösen von Hintergrundaufgaben
 Jede App kann eine Hintergrundaufgabe registrieren, um auf bestimmte Systemereignisse zu reagieren, selbst wenn die App nicht ausgeführt wird. Hintergrundaufgaben können keinen Code ausführen, der die Benutzeroberfläche direkt aktualisiert. Stattdessen zeigen sie dem Benutzer Informationen mithilfe von mit Kachelupdates, Infoanzeigerupdates und Toastbenachrichtigungen an. Weitere Informationen finden Sie unter [App-Unterstützung durch Hintergrundaufgaben](/previous-versions/windows/apps/hh977046(v=win.10)).

 Sie können die Ereignisse, die Hintergrundaufgaben für die App starten, über den Debugger auslösen.

> [!NOTE]
> Der Debugger kann nur Ereignisse auslösen, die keine Daten enthalten, z. B. Ereignisse, die eine Zustandsänderung im Gerät angeben. Sie müssen Hintergrundaufgaben, die Benutzereingaben oder andere Daten benötigen, manuell auslösen.

 Bei der realistischsten Methode, um ein Hintergrundaufgabenereignis auszulösen, sollte Ihre App nicht ausgeführt werden. Das Auslösen des Ereignisses in einer Standarddebugsitzung wird jedoch ebenfalls unterstützt.

### <a name="trigger-a-background-task-event-from-a-standard-debug-session"></a><a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Auslösen eines Hintergrundaufgabenereignisses aus einer Standarddebugsitzung

1. Legen Sie einen Haltepunkt im Code der Hintergrundaufgabe fest, den Sie debuggen möchten.

2. Drücken Sie die Taste **F5** , um mit dem Debuggen zu beginnen.

3. Wählen Sie die Hintergrundaufgabe, die Sie starten möchten, aus der Ereignisliste auf der Symbolleiste **Debugspeicherort** aus.

     ![Aufgaben für Unterbrechen, Wiederaufnehmen, Beenden und Hintergrund](../debugger/media/dbg_suspendresumebackground.png)

### <a name="trigger-a-background-task-when-the-app-is-not-running"></a><a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a> Auslösen einer Hintergrundaufgabe, wenn die App nicht ausgeführt wird

1. Legen Sie einen Haltepunkt im Code der Hintergrundaufgabe fest, den Sie debuggen möchten.

2. Öffnen Sie die Debugeigenschaftenseite für das Startprojekt. Wählen Sie im Projektmappen-Explorer das Projekt aus. Klicken Sie im Menü **Debuggen** auf **Eigenschaften**.

     Für C++-Projekte müssen Sie die **Konfigurationseigenschaften** erweitern und anschließend **Debugging** auswählen.

3. Führen Sie einen der folgenden Schritte aus:

    - Wählen Sie für Visual C#- und Visual Basic-Projekte **Eigenen Code zunächst nicht starten sondern debuggen** aus.

         ![Eigenschaft zum Starten der Anwendung beim Debuggen in C#/VB](../debugger/media/dbg_csvb_dontlaunchapp.png "DBG_CsVb_DontLaunchApp")

    - Wählen Sie für C++-Projekte **Nein** aus der Liste **Anwendung starten** aus.

         ![Eigenschaft zum Starten des Anwendungsdebuggens in C++/VB](../debugger/media/dbg_cppjs_dontlaunchapp.png "DBG_CppJs_DontLaunchApp")

4. Drücken Sie **F5** , um die App in den Debugmodus zu versetzen. Beachten Sie, dass die Liste **Prozess** auf der Symbolleiste **Debugspeicherort** den Namen des Apppakets anzeigt, um zu signalisieren, dass der Debugmodus aktiv ist.

     ![Prozessliste für Hintergrundaufgaben](../debugger/media/dbg_backgroundtask_processlist.png "DBG_BackgroundTask_ProcessList")

5. Wählen Sie die Hintergrundaufgabe, die Sie starten möchten, aus der Ereignisliste auf der Symbolleiste **Debugspeicherort** aus.

     ![Anhalte-, Fortsetzungs-, Beendigungs- und Hintergrundaufgaben](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")

## <a name="trigger-process-lifetime-management-events-and-background-tasks-from-an-installed-app"></a><a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Ereignisse zur Verwaltung der Prozesslebensdauer sowie Hintergrundaufgaben der installierten App auslösen bzw. aktivieren.
 Verwenden Sie das Dialogfeld **Installiertes App-Paket debuggen**, um eine App zu starten, die bereits im Debugger installiert ist. Sie können beispielsweise eine App debuggen, die über den Microsoft Store installiert wurde, oder eine App, deren Quelldateien Sie zwar besitzen, für die Sie jedoch noch kein Visual Studio-Projekt erstellt haben. Über das Dialogfeld **Installiertes App-Paket debuggen** können Sie eine App auf einem Visual Studio-Computer oder einem Remotegerät im Debugmodus starten oder den Debugmodus für die App festlegen, ohne sie zu starten. Weitere Informationen finden Sie unter [Debuggen eines installierten App-Pakets](../debugger/debug-installed-app-package.md).

 Sobald die App in den Debugger geladen ist, können Sie die oben beschriebenen Prozeduren anwenden.

## <a name="diagnosing-background-task-activation-errors"></a><a name="BKMK_Diagnosing_background_task_activation_errors"></a> Diagnostizieren von Hintergrundaufgaben-Aktivierungsfehlern
 Die Diagnoseprotokolle in der Windows-Ereignisanzeige für die Hintergrundinfrastruktur enthalten ausführliche Informationen, die Sie zur Diagnose und Behebung von Fehlern bei Hintergrundaufgaben verwenden können. So zeigen Sie das Protokoll an:

1. Öffnen Sie die Ereignisanzeige.

2. Wählen Sie im Bereich **Aktionen** die Option **Ansicht** aus, und stellen Sie sicher, dass **Show Analytic and Debug Logs** (Analytische Protokolle und Debugprotokolle einblenden) aktiviert ist.

3. Wählen Sie auf der Symbolleiste **Ereignisanzeige (Lokal)** die Knoten **Anwendungs- und Dienstprotokolle** > **Microsoft** > **Windows** > **BackgroundTasksInfrastructure** beschrieben.

4. Wählen Sie das **Diagnose** -Protokoll aus.

## <a name="see-also"></a>Siehe auch
- [Testen von UWP-Apps mit Visual Studio](../test/unit-test-your-code.md)
- [Debuggen von Apps in Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
- [Application lifecycle (Anwendungslebenszyklus)](/windows/uwp/launch-resume/app-lifecycle)
- [Launching, resuming, and multitasking](/windows/uwp/launch-resume/index)
