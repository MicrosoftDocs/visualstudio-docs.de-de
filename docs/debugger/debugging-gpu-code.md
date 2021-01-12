---
title: Debuggen von GPU-Code | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie C++-Code in Visual Studio debuggen, der auf der GPU (Graphics Processing Unit, Grafikprozessor) ausgeführt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36359f8d5f2044c97e3479981290aff07d3f2e31
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727033"
---
# <a name="debugging-gpu-code"></a>Debuggen von GPU-Code
Sie können C++-Code debuggen, der im Grafikprozessor (Graphics Processing Unit, GPU) ausgeführt wird. Die GPU-Debugunterstützung in Visual Studio umfasst die Raceerkennung, das Starten von Prozessen bzw. Anfügen an Prozesse sowie die Integration in die Debugfenster.

## <a name="supported-platforms"></a>Unterstützte Plattformen
 Debuggen wird unter [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[win8](../debugger/includes/win8_md.md)], Windows 10, [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)], [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] und Windows Server 2016 unterstützt. Für Debuggen im Softwareemulator, in [!INCLUDE[win8](../debugger/includes/win8_md.md)], Windows 10 oder [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] ist Windows Server 2016 erforderlich. Für das Debuggen auf der Hardware müssen Sie die Treiber für Ihre Grafikkarte installieren. Nicht alle Hardwarehersteller implementieren sämtliche Debuggerfunktionen. Weitere Informationen zu Einschränkungen finden Sie in der Dokumentation des Herstellers.

> [!NOTE]
> Unabhängige Hardwareanbieter, die GPU-Debugging in Visual Studio unterstützen möchten, müssen eine DLL erstellen, mit der die VSD3DDebug-Schnittstelle implementiert wird und die auf ihre eigenen Treiber ausgerichtet ist.

## <a name="configuring-gpu-debugging"></a>Konfigurieren von GPU-Debugging
 Der Debugger kann nicht beim CPU- und GPU-Code in der gleichen App-Ausführung unterbrechen. Standardmäßig unterbricht der Debugger beim CPU-Code. Um den GPU-Code zu debuggen, verwenden Sie einen dieser beiden Schritte:

- Wählen Sie in der Liste **Debugtyp** auf der Symbolleiste **Standard** die Option **Nur GPU** aus.

- Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das Projekt, und wählen Sie **Eigenschaften** aus. Wählen Sie im Dialogfeld **Eigenschaftenseiten** die Option **Debuggen** und dann in der Liste **Debuggertyp** die Option **Nur GPU** aus.

## <a name="launching-and-attaching-to-applications"></a>Starten von und Anfügen an Anwendungen
 Sie können die Visual Studio-Debuggingbefehle verwenden, um das GPU-Debugging zu starten und zu beenden. Weitere Informationen finden Sie unter [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md). Sie können den GPU-Debugger auch an einen laufenden Prozess anfügen, jedoch nur, wenn dieser Prozess GPU-Code ausführt. Weitere Informationen finden Sie unter [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="run-current-tile-to-cursor-and-run-to-cursor"></a>Befehle "Aktuelle Kachel bis zum Cursor ausführen" und "Ausführen bis Cursor"
 Wenn Sie im Grafikprozessor debuggen, stehen Ihnen zwei Möglichkeiten zum Ausführen bis zur Cursorposition zur Verfügung. Die Befehle für beide Optionen sind im Kontextmenü des Code-Editors verfügbar.

1. Mit dem Befehl **Ausführen bis Cursor** wird die App ausgeführt, bis sie die Cursorposition erreicht und dann angehalten wird. Dies bedeutet nicht, dass der aktuelle Thread bis zur Cursorposition ausgeführt wird, sondern vielmehr, dass der erste Thread, der die Cursorposition erreicht, die Unterbrechung auslöst. Weitere Informationen finden Sie unter [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md).

2. Mit dem Befehl **Aktuelle Kachel bis zum Cursor ausführen** wird die App ausgeführt, bis alle Threads in der aktuellen Kachel die Cursorposition erreichen und dann angehalten werden.

## <a name="debugging-windows"></a>Debugfenster
 Wenn Sie bestimmte Debugfenster verwenden, können Sie GPU-Threads überprüfen, kennzeichnen und einfrieren. Weitere Informationen finden Sie unter:

- [Verwenden des Fensters "Parallele Stapel"](../debugger/using-the-parallel-stacks-window.md)

- [Verwenden des Fensters „Aufgaben“](../debugger/using-the-tasks-window.md)

- [How to: Verwenden des Fensters „Parallele Überwachung“](../debugger/how-to-use-the-parallel-watch-window.md)

- [Debuggen von Threads und Prozessen](../debugger/debug-threads-and-processes.md) (Symbolleiste „Debugspeicherort“)

- [How to: Verwenden des Fensters „GPU-Threads“](../debugger/how-to-use-the-gpu-threads-window.md)

## <a name="data-synchronization-exceptions"></a>Ausnahmen bei Datensynchronisierung
 Der Debugger kann mehrere Datensynchronisierungsbedingungen während der Ausführung erkennen. Wenn eine Bedingung erkannt wird, wechselt der Debugger in den Unterbrechungszustand. Sie haben zwei Optionen: **Unterbrechen** oder **Weiter**. Im Dialogfeld **Ausnahmen** können Sie konfigurieren, ob der Debugger diese Bedingungen erkennen soll und bei welchen Bedingungen eine Unterbrechung ausgelöst werden soll. Weitere Informationen finden Sie unter [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md). Sie können im Dialogfeld **Optionen** auch angeben, ob der Debugger Ausnahmen ignorieren soll, wenn geschriebene Daten den Wert der Daten nicht ändern. Weitere Informationen finden Sie unter [General, Debugging, Options Dialog Box](../debugger/general-debugging-options-dialog-box.md).

## <a name="troubleshooting"></a>Problembehandlung

### <a name="specifying-an-accelerator"></a>Festlegen einer Zugriffstaste
 Haltepunkte im GPU-Code werden nur erreicht, wenn der Code auf der REF-Zugriffstaste [accelerator::direct3d_ref](/cpp/parallel/amp/reference/accelerator-class#direct3d_ref) ausgeführt wird. Wenn Sie keine Zugriffstaste im Code angeben, wird die REF-Zugriffstaste automatisch als **Debuggingbeschleunigungstyp** in den Projekteigenschaften ausgewählt. Wenn der Code explizit eine Zugriffstaste auswählt, wird die REF-Zugriffstaste nicht beim Debuggen verwendet und die Haltepunkte werden nicht erreicht, es sei denn, die GPU-Hardware verfügt über Debugunterstützung. Um dieses Problem zu beheben, schreiben Sie den Code so, dass die REF-Zugriffstaste beim Debuggen verwendet wird. Weitere Informationen finden Sie unter „Projekteigenschaften“ und [Verwenden von accelerator- und accelerator_view-Objekten](/cpp/parallel/amp/using-accelerator-and-accelerator-view-objects) sowie unter [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="conditional-breakpoints"></a>Bedingte Haltepunkte
 Bedingte Haltepunkte im GPU-Code werden unterstützt, jedoch kann nicht jeder Ausdruck auf dem Gerät ausgewertet werden. Wenn ein Ausdruck nicht auf dem Gerät ausgewertet werden kann, wird er im Debugger ausgewertet. Der Debugger wird wahrscheinlich langsamer ausgeführt als das Gerät.

### <a name="error-there-is-a-configuration-issue-with-the-selected-debugging-accelerator-type"></a>Fehler: Bei der Konfiguration des ausgewählten Debugbeschleunigungstyps ist ein Problem aufgetreten.
 Dieser Fehler tritt auf, wenn es zwischen den Projekteinstellungen und der Konfiguration des PCs, auf dem Sie debuggen, eine Inkonsistenz gibt. Weitere Informationen finden Sie unter [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="error-the-debug-driver-for-the-selected-debugging-accelerator-type-is-not-installed-on-the-target-machine"></a>Fehler: Der Debugtreiber für den ausgewählten Debugbeschleunigungstyp ist nicht auf dem Zielcomputer installiert.
 Dieser Fehler tritt auf, wenn Sie auf einem Remotecomputer debuggen. Der Debugger kann bis zur Laufzeit nicht bestimmen, ob die Treiber auf dem Remotecomputer installiert sind. Die Treiber sind vom Hersteller der Grafikkarte erhältlich.

### <a name="error-timeout-detection-and-recovery-tdr-must-be-disabled-at-the-remote-site"></a>Fehler: Auf der Remotesite muss TDR (Timeout Detection and Recovery) deaktiviert sein.
 Es ist möglich, dass die C++ AMP-Berechnungen das Standardzeitintervall überschreiten, das durch den Windows-TDR-Prozess (Timeout Detection and Recovery) festgelegt wird. Wenn dies geschieht, wird die Berechnung abgebrochen und die Daten gehen verloren. Weitere Informationen finden Sie unter [Behandlung von TDRs in C++ AMP](/archive/blogs/nativeconcurrency/handling-tdrs-in-c-amp).

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Debuggen einer C++ AMP-Anwendung](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)
- [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Start GPU Debugging in Visual Studio](/archive/blogs/nativeconcurrency/start-gpu-debugging-in-visual-studio-2012) (Starten von GPU-Debugging in Visual Studio)