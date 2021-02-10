---
title: Projekteinstellungen für eine VB-Debugkonfiguration | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie die Projekteinstellungen für eine Visual Basic-Debugkonfiguration im Fenster „Eigenschaftenseiten“ von Visual Studio ändern.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7a1f0e7aa0e6ee7523f8ff7ae1f3c8e34745a3af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842707"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Projekteinstellungen für eine Visual Basic-Debugkonfiguration
Sie können die Projekteinstellungen für eine [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Debugkonfiguration im Fenster **Eigenschaftenseiten** entsprechend der Anleitung unter [Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md) ändern. Anhand der folgenden Tabellen erfahren Sie, wo die debuggerspezifischen Einstellungen im Fenster **Eigenschaftenseiten** zu finden sind.

> [!WARNING]
> Dieses Thema gilt nicht für UWP-Apps. Siehe [Starten einer Debugsitzung (VB, C#, C++ und XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

### <a name="debug-tab"></a>Registerkarte "Debuggen"

| Einstellung | Beschreibung |
|------------------------------| - |
| **Konfiguration** | Legt den Modus für das Kompilieren der Anwendung fest. Sie können **Aktiv (Debuggen)** , **Debuggen**, **Release** oder **Alle Konfigurationen** auswählen. |
| **Startaktion** | Anhand dieser Gruppe von Steuerungen wird festgelegt, welche Aktion bei Auswahl von Starten im Menü Debuggen erfolgt.<br /><br /> -   **Projekt starten** ist der Standardwert, durch den das Startprojekt zum Debuggen gestartet wird. <br />-   **Externes Programm starten** ermöglicht es, ein Programm zu starten, das nicht zu einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projekt gehört, und eine Verbindung zu diesem Programm herzustellen. Weitere Informationen finden Sie unter [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Browser mit folgender URL starten** ermöglicht das Debuggen einer Webanwendung. |
| **Befehlszeilenargumente** | Legt Befehlszeilenargumente für das Programm fest, das gedebuggt werden soll. Der Befehlsname entspricht dem unter Externes Programm starten angegebenen Programmnamen. Wenn die Option Start-URL für Startaktion ausgewählt ist, werden die Befehlszeilenargumente ignoriert. |
| **Arbeitsverzeichnis** | Gibt das Arbeitsverzeichnis des Programms an, das gerade gedebuggt wird. Das Arbeitsverzeichnis in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ist das Verzeichnis, über das die Anwendung gestartet wird. Das Standardarbeitsverzeichnis ist \bin\Debug oder \bin\Release. Dies hängt von der aktuellen Konfiguration ab. |
| **Remotecomputer verwenden** | Bei aktiviertem Kontrollkästchen ist das Remotedebuggen aktiviert. Im Textfeld können Sie den Namen eines Remotecomputers eingeben, auf dem die Anwendung zu Debugzwecken ausgeführt wird, oder einen [Msvsmon-Servernamen](../debugger/remote-debugging.md). Der Speicherort der EXE-Datei auf dem Remotecomputer wird in der Registerkarte „Erstellen“ unter der Eigenschaft „Ausgabepfad“ festgelegt. Bei diesem Speicherort muss es sich um ein freigegebenes Verzeichnis auf dem Remotecomputer handeln. |
| **Nicht verwalteten Code debuggen** | Bietet die Möglichkeit, Aufrufe von systemeigenem (nicht verwaltetem) Win32-Code von einer verwalteten Anwendung aus zu debuggen. Wenn Sie in einem [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-Projekt unter Debuggertyp die Option Gemischt auswählen, erzielen Sie denselben Effekt. |
| **SQL Server debuggen** | Ermöglicht das Debuggen von SQL Server-Datenbankobjekten. |

### <a name="compile-tab-press-advanced-compile-options-button"></a>Registerkarte "Kompilieren": Drücken der Schaltfläche "Erweiterte Kompilierungsoptionen"

| Einstellung | Beschreibung |
|---------------------------| - |
| **Optimierungen aktivieren** | Diese Option sollte deaktiviert sein. Eine Optimierung führt dazu, dass der tatsächlich ausgeführte Code sich von dem in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sichtbaren Quellcode unterscheidet. Dadurch wird das Debuggen erschwert. Bei einer Codeoptimierung werden Symbole nicht standardmäßig geladen, wenn Sie mit Nur mein Code debuggen. |
| **Generieren von Debuginformationen** | Standardmäßig in Debugversion und Releaseversion definiert, erstellt diese Einstellung (gleichwertig mit der Compileroption /debug) Debuginformationen zur Buildzeit. Der Debugger nutzt diese Informationen, um Variablennamen und andere Informationen während des Debuggens in einem sinnvollen Format anzuzeigen. Wenn Sie das Programm ohne diese Informationen kompilieren, sind die Funktionen des Debuggers eingeschränkt. Weitere Informationen finden Sie unter [/debug](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| **DEBUG-Konstante definieren** | Durch die Definition dieses Symbols können Ausgabefunktionen aus der [Debug-Klasse](/dotnet/api/system.diagnostics.debug) bedingt kompiliert werden. Wenn dieses Symbol definiert ist, generieren die Debug-Klassenmethoden im [Ausgabefenster](../ide/reference/output-window.md) eine Ausgabe. Ohne dieses Symbol werden Debug-Klassenmethoden nicht kompiliert und keine Ausgabe generiert. In der Debugversion sollte das Symbol definiert sein und in der Releaseversion nicht. Durch die Definition des Symbols in einer Releaseversion wird überflüssiger Code erstellt, der die Programmleistung beeinträchtigt. |
| **TRACE-Konstante definieren** | Durch die Definition dieses Symbols können Ausgabefunktionen aus der [Trace-Klasse](/dotnet/api/system.diagnostics.trace) bedingt kompiliert werden. Wenn dieses Symbol definiert ist, generieren die Trace-Klassenmethoden im [Ausgabefenster](../ide/reference/output-window.md) eine Ausgabe. Ohne dieses Symbol werden Trace-Klassenmethoden nicht kompiliert und keine Trace-Ausgabe generiert. Dieses Symbol wird standardmäßig sowohl für Debugversion als auch Releaseversion definiert. |

## <a name="see-also"></a>Siehe auch
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)