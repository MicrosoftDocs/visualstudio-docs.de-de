---
title: Starten eines Programms | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Reihe von Ereignissen, die stattfinden, wenn Sie ein Programm mit F5 Debuggen, um den Debugger aus der IDE auszuführen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de29b012914ac9997a78674fd3215f2c15d43c6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945915"
---
# <a name="launch-a-program"></a>Programm starten
Benutzer, die ein Programm debuggen möchten, können **F5** drücken, um den Debugger aus der IDE auszuführen. Dadurch beginnt eine Reihe von Ereignissen, die letztendlich dazu führen, dass die IDE eine Verbindung mit einer Debug-Engine (de) herstellt, die wiederum wie folgt mit dem Programm verbunden oder angefügt wird:

1. Die IDE ruft zunächst das Projektpaket auf, um die aktiven Debugeinstellungen der Projekt Mappe zu erhalten. Zu den Einstellungen gehören das Start Verzeichnis, die Umgebungsvariablen, der Port, in dem das Programm ausgeführt wird, und der de, der zum Erstellen des Programms verwendet werden soll (sofern angegeben). Diese Einstellungen werden an das Debugpaket übermittelt.

2. Wenn ein de-Wert angegeben wird, ruft der de das Betriebssystem auf, um das Programm zu starten. Aufgrund des Starts des Programms lädt die Laufzeitumgebung des Programms. Wenn ein Programm z. b. in MSIL geschrieben ist, wird die Common Language Runtime aufgerufen, um das Programm auszuführen.

    - oder -

    Wenn ein "de" nicht angegeben wird, ruft der Port das Betriebssystem auf, um das Programm zu starten, was dazu führt, dass die Laufzeitumgebung des Programms geladen wird.

   > [!NOTE]
   > Wenn eine de zum Starten eines Programms verwendet wird, ist es wahrscheinlich, dass dieselbe de an das Programm angefügt wird.

3. Abhängig davon, ob der oder der Port das Programm gestartet hat, erstellt der de oder die Laufzeitumgebung eine Programmbeschreibung bzw. einen Knoten und benachrichtigt den Port, dass das Programm ausgeführt wird.

   > [!NOTE]
   > Es wird empfohlen, dass in der Laufzeitumgebung der Programmknoten erstellt wird, da es sich bei dem Programmknoten um eine vereinfachte Darstellung eines Programms handelt, das deaktiviertem Programm ausgeführt werden kann. Es ist nicht erforderlich, eine gesamte de zu laden, um einen Programmknoten zu erstellen und zu registrieren. Wenn die de für die Ausführung im Prozess der IDE konzipiert ist, aber keine IDE tatsächlich ausgeführt wird, muss eine Komponente vorhanden sein, die dem Port einen Programmknoten hinzufügen kann.

   Das neu erstellte Programm zusammen mit allen anderen Programmen, verknüpften oder nicht verknüpften, von der gleichen IDE gestarteten oder angefügten Programmen, verfassen Sie eine Debugsitzung.

   Programm gesteuert, wenn der Benutzer zuerst **F5** drückt, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ruft das Debugpaket das Projektpaket (das mit dem Typ des gestarteten Programms verknüpft ist) über die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> Methode auf, die wiederum eine <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> Struktur mit den aktiven Debugeinstellungen der Projekt Mappe ausfüllt. Diese Struktur wird mithilfe eines Aufrufens der-Methode an das Debugpaket zurückgegeben <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> . Das Debugpaket instanziiert dann den Sitzungs-Debug-Manager (SDM), der das zu debuggende Programm und alle zugehörigen Debug-engines startet.

   Eines der Argumente, das an SDM übermittelt wird, ist die GUID der de, die zum Starten des Programms verwendet wird.

   Wenn die de-GUID nicht ist `GUID_NULL` , erstellt der SDM die de und ruft dann seine [launchangeh](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) -Methode auf, um das Programm zu starten. Wenn ein Programm z. b. in nativem Code geschrieben ist, `IDebugEngineLaunch2::LaunchSuspended` Ruft wahrscheinlich `CreateProcess` und `ResumeThread` (Win32-Funktionen) auf, um das Programm auszuführen.

   Die Laufzeitumgebung des Programms wird daher geladen, wenn das Programm gestartet wird. Von der de oder der Laufzeitumgebung wird dann eine [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) -Schnittstelle erstellt, um das Programm zu beschreiben, und diese Schnittstelle wird an [addprogram Node](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) weitergeleitet, um den Port zu benachrichtigen, an dem das Programm ausgeführt wird.

   Wenn erfolgreich `GUID_NULL` ist, wird das Programm vom Port gestartet. Sobald das Programm ausgeführt wird, erstellt die Laufzeitumgebung eine `IDebugProgramNode2` Schnittstelle, um das Programm zu beschreiben, und übergibt es an `IDebugPortNotify2::AddProgramNode` . Dadurch wird der Port benachrichtigt, dass das Programm ausgeführt wird. Anschließend fügt die SDM die Debug-Engine an das laufende Programm an.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Benachrichtigen des Ports](../../extensibility/debugger/notifying-the-port.md) Erläutert, was geschieht, nachdem ein Programm gestartet wurde und der Port benachrichtigt wird.

 Anfügen [nach einem Start](../../extensibility/debugger/attaching-after-a-launch.md) Dokumentiert, wann die Debugsitzung bereit ist, die de an das Programm anzufügen.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debugtasks](../../extensibility/debugger/debugging-tasks.md) Enthält Links zu verschiedenen Debuggingaufgaben, z. b. das Starten eines Programms und Auswerten von Ausdrücken.
