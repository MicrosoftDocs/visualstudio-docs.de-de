---
title: Projekteinstellungen für eine C#-Debugkonfiguration | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie die Projekteinstellungen für eine C#-Debugkonfiguration in Visual Studio über die Registerkarten „Debuggen“ und „Erstellen“ der Projekteigenschaftenseiten ändern.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/21/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 262e46436f1391ae21df0ccdd3ca308eecb347da
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205566"
---
# <a name="project-settings-for--c-debug-configurations"></a>Projekteinstellungen für C#-Debugkonfigurationen

Debugeinstellungen für ein C#-Projekt können über die [Registerkarte „Debuggen“](#debug-tab) und die [Registerkarte „Erstellen“](#build-tab) der Projekteigenschaftenseiten geändert werden.

Wählen Sie zum Öffnen der Eigenschaftenseiten das Projekt im **Projektmappen-Explorer** aus, und wählen Sie dann das Symbol **Eigenschaften** aus, oder klicken Sie mit der rechten Maustaste auf das Projekt und wählen dann **Eigenschaften** aus.

Weitere Informationen finden Sie unter [Debug and release configurations (Debug- und Releasekonfigurationen)](how-to-set-debug-and-release-configurations.md).

>[!IMPORTANT]
>Diese Einstellungen gelten nicht für .NET Core-, ASP.NET- oder UWP-Apps. Informationen zum Konfigurieren der Debugeinstellungen für UWP-Apps finden Sie unter [Starten einer Debugsitzung für eine UWP-App](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

## <a name="debug-tab"></a>Registerkarte "Debuggen"

|Einstellung|Beschreibung|
|-------------------------------------| - |
| **Konfiguration** | Legt den Modus zum Erstellen der App fest. Wählen Sie in der Dropdownliste **Aktiv (Debuggen)** , **Debuggen**, **Freigeben** oder **Alle Konfigurationen** aus. |
| **Startaktion** | Gibt die Aktion an, wenn Sie in einer Debugkonfiguration **Starten** auswählen.<br />- Durch den Standardwert **Projekt starten**, wird das Startprojekt zum Debuggen gestartet. Weitere Informationen finden Sie unter [Auswählen des Startprojekts](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />-  Mit **Externes Programm starten** wird eine App gestartet und angefügt, die nicht Teil eines [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projekts ist. Weitere Informationen finden Sie unter [Anfügen an laufende Prozesse mit dem Visual Studio Debugger](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- Mithilfe von **Browser mit URL starten** können Sie eine Web-App debuggen. |
| **Startoptionen** > **Befehlszeilenargumente** | Gibt Befehlszeilenargumente für die App an, die gerade gedebuggt wird. Der Befehlsname entspricht dem unter **Externes Programm starten** angegebenen App-Namen. |
| **Startoptionen** > **Arbeitsverzeichnis** | Gibt das Arbeitsverzeichnis der App an, die gerade gedebuggt wird. In C# lautet das Arbeitsverzeichnis standardmäßig *\bin\debug*.
| **Startoptionen** > **Remotecomputer verwenden**|Wählen Sie zum Remotedebuggen diese Option aus, und geben Sie den Namen des Remotedebugziels oder einen [Msvsmon-Servernamen](../debugger/remote-debugging.md) ein. <br />Der Speicherort der App auf dem Remotecomputer wird auf der Registerkarte **Erstellen** mit der Eigenschaft **Ausgabepfad** festgelegt. Bei diesem Speicherort muss es sich um ein freigegebenes Verzeichnis auf dem Remotecomputer handeln.
| **Debugger-Engine** > **Nicht verwaltetes Codedebuggen aktivieren** | Dient zum Debuggen von Aufrufen von nativem (nicht verwaltetem) Win32-Code über die verwaltete App. |
| **Debugger-Engine** > **SQL Server-Debuggen aktivieren** | Dient zum Debuggen von SQL Server-Datenbankobjekten. |

## <a name="build-tab"></a>Registerkarte "Erstellen"

|Einstellung|Beschreibung|
|-------------|-----------------|
|**Allgemein** > **Symbole für bedingte Kompilierung**|Ist diese Option ausgewählt, werden die Konstanten DEBUG und TRACE definiert.<br /><br /> Diese Konstanten ermöglichen das Kompilieren der [Debug-](/dotnet/api/system.diagnostics.debug) und [Trace-Klassen](/dotnet/api/system.diagnostics.trace). Wenn diese Konstanten definiert sind, generieren die Klassenmethoden „Debug“ und „Trace“ eine Ausgabe im [Ausgabefenster](../ide/reference/output-window.md). Ohne diese Konstanten werden die Klassenmethoden Debug und Trace nicht kompiliert und keine Ausgabe erzeugt.<br /><br />DEBUG wird in der Regel in der Debugversion eines Builds definiert. Die Definition wird in der Releaseversion wieder aufgehoben. TRACE wird normalerweise sowohl in Debugversionen als auch in Releaseversionen definiert.|
|**Allgemein** > **Code optimieren**|Aktivieren Sie diese Einstellung für Debugbuilds nur, wenn ein Fehler ausschließlich in optimiertem Code auftritt. Optimierter Code ist aufwendiger zu debuggen, da die Anweisungen nicht direkt mit den Anweisungen im Quellcode übereinstimmen.|
|**Ausgabe** > **Ausgabepfad**|Wird zum Debuggen normalerweise auf *bin\Debug* festgelegt.|
|Schaltfläche **Erweitert**|Weitere Informationen zu erweiterten Debugoptionen finden Sie unter [Dialogfeld „Erweiterte Buildeinstellungen“ (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Das portierbare Format für Symboldateien ( *.pdb*) ist ein aktuelles plattformübergreifendes Format für .NET Core-Apps.

## <a name="see-also"></a>Siehe auch
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)