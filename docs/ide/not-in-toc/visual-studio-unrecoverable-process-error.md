---
title: Bei einem Prozess ist ein nicht behebbarer Fehler aufgetreten
ms.date: 09/10/2020
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1c9dc5053e2168482f4463f805bdc5e724ef6b0
ms.sourcegitcommit: d9dd86c421532cfca6c0c5761d160f35829419c6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90025564"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Nicht behebbare Prozessfehler in Visual Studio

Visual Studio verwendet mehrere Out-of-Proc-Prozesse, um die erforderlichen Hintergrundaufgaben, wie z.B. Live-Komponententests, Code-Analysetools und mehr auszuführen. Diese Prozesse werden Out-of-Proc ausgeführt, um Leistungsvorteile von Visual Studio zu nutzen, z.B. dass Visual Studio schneller reagieren kann, wenn ressourcenintensive, langfristige Aufträge ausgeführt werden. Da Visual Studio ein 32-Bit-Prozess ist, bietet die Out-of-Proc-Ausführung von Prozessen anspruchsvollen speicherintensiven Arbeiten einen größeren Speicherplatz, in dem ausgeführt werden soll.

Wenn der Prozess *ServiceHub.RoslynCodeAnalysisService.exe* oder *ServiceHub.RoslynCodeAnalysisService32.exe* aus irgendeinem Grund beendet wird, wird eine Popup-Informationsleiste mit folgender Meldung angezeigt:

**„Unfortunately, a process used by Visual Studio has encountered an unrecoverable error. We recommend saving your work, and then closing and restarting Visual Studio.“ (Leider ist bei einem von Visual Studio verwendeten Prozess ein nicht behebbarer Fehler aufgetreten. Es wird empfohlen, die Arbeit abzuspeichern und Visual Studio anschließend neu zu starten.)**

Wenn diese Meldung angezeigt wird, müssen Sie Ihre Arbeit speichern und Visual Studio anschließend schließen und neu starten.

## <a name="list-of-processes"></a>Liste der Prozesse

Im Folgenden finden Sie eine Liste der Out-of-Proc-Prozesse, die von Visual Studio verwendet werden. Diese Liste enthält Prozesse, die in bestimmten Workflows oder Szenarios gestartet werden. In den meisten Fällen werden diese also nicht alle gleichzeitig ausgeführt.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- MSBuild.exe
- PerfWatson2.exe
- ScriptedSandbox64.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- „ServiceHub.RoslynCodeAnalysisService.exe“
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.VSDetouredHost.exe
- VBCSCompiler.exe
- VsHub.exe
- vstest.discoveryengine.x86.exe
- WaAppAgent.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe

Wenn einer dieser Prozesse unerwartet beendet wird, funktionieren einige Funktionalitäten in Visual Studio nicht mehr. Bei einigen Prozesse kann der Ausfall dieser Funktionalitäten unbedeutend sein. Bei anderen wird die Stabilität von Visual Studio beeinträchtigt, und eine Fehlermeldung wird angezeigt.

> [!NOTE]
> Wenn ein Problem auftritt, das auf dieser Seite nicht berücksichtigt wird, informieren Sie uns bitte über das Tool [Problem melden](../../ide/how-to-report-a-problem-with-visual-studio.md), das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
