---
title: JIT-Optimierung und -Debuggen | Microsoft-Dokumentation
description: Optimierter Code ist schwieriger zu debuggen als nicht optimierter Code. Hier erfahren Sie mehr über die JIT-Optimierung sowie darüber, wann und wie Sie sie unterdrücken sollten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66f63c7232b52ebe849722147e007ab70527c311
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903921"
---
# <a name="jit-optimization-and-debugging"></a>JIT-Optimierung und -Debuggen
Wenn Sie versuchen, Code zu debuggen, ist es einfacher, wenn der Code **NICHT** optimiert ist. Wenn der Code optimiert ist, nehmen der Compiler und die Runtime Änderungen am ausgegebenen CPU-Code vor, sodass er schneller ausgeführt wird, aber eine geringere direkte Zuordnung zum ursprünglichen Quellcode aufweist. Wenn die Zuordnung weniger direkt ist, können Debugger häufig nicht den Wert lokaler Variablen erkennen, und Codeschritte und Breakpoints funktionieren möglicherweise nicht wie erwartet.

> [!NOTE]
> Weitere Informationen zum JIT-Debuggen (Just-in-Time) finden Sie in [dieser Dokumentation](../debugger/debug-using-the-just-in-time-debugger.md).

## <a name="how-optimizations-work-in-net"></a>Funktionsweise von Optimierungen in .NET 
Im Gegensatz zur Buildkonfiguration „Debuggen“ erstellt die Buildkonfiguration „Release“ in der Regel optimierten Code. Die MSBuild-Eigenschaft `Optimize` steuert, ob der Compiler aufgefordert wird, Code zu optimieren.

Im .NET-Ökosystem wird Code in einem zweistufigen Prozess von der Quelle in CPU-Anweisungen umgewandelt: Zuerst konvertiert der C#-Compiler den eingegebenen Text in ein binäres Zwischenformat namens MSIL und schreibt dieses in DLL-Dateien. Später konvertiert die .NET-Runtime dieses MSIL-Format in CPU-Anweisungen. Beide Schritte sorgen in gewissem Maß für Optimierungen, aber der zweite Schritt, der von der .NET-Runtime ausgeführt wird, führt zu den signifikanteren Optimierungen.

## <a name="the-suppress-jit-optimization-on-module-load-managed-only-option"></a>Option „JIT-Optimierung beim Laden von Modulen unterdrücken (nur verwaltet)“
Der Debugger macht eine Option verfügbar, die steuert, was geschieht, wenn eine mit Optimierungen kompilierte DLL innerhalb des Zielprozesses geladen wird. Wenn diese Option deaktiviert ist (Standardzustand), werden die Optimierungen beim Kompilieren des MSIL-Codes in CPU-Code von der .NET-Runtime aktiviert. Wenn die Option aktiviert ist, wird vom Debugger angefordert, dass Optimierungen deaktiviert werden.

Klicken Sie auf **Extras** > **Optionen** und dann unter dem Knoten **Debuggen** auf die Seite **Allgemein**, um die Option **JIT-Optimierung beim Laden von Modulen unterdrücken (nur verwaltet)** zu finden.

![JIT-Optimierung unterdrücken](../debugger/media/suppress-jit-tool-options.png "JIT-Optimierung unterdrücken")

## <a name="when-should-you-check-the-suppress-jit-optimization-option"></a>Wann sollten Sie die Option „JIT-Optimierung unterdrücken“ aktivieren?
Aktivieren Sie diese Option, wenn Sie die DLLs aus einer anderen Quelle (z. B. einem NuGet-Paket) heruntergeladen haben und den Code in dieser DLL debuggen möchten. Damit die Unterdrückung funktioniert, müssen Sie auch die Symboldatei (PDB-Datei) für diese DLL finden.

Wenn Sie nur den Code debuggen möchten, den Sie lokal erstellen, empfiehlt es sich, diese Option nicht zu deaktivieren. In manchen Fällen wird das Debuggen durch Aktivieren dieser Option erheblich verlangsamt. Es gibt zwei Gründe für diese Verlangsamung:

* Optimierter Code wird schneller ausgeführt. Wenn Sie die Optimierungen für Code deaktivieren, kann sich dies auf die Leistung auswirken.
* Wenn die Option „Nur eigenen Code“ aktiviert ist, versucht der Debugger nicht einmal, Symbole für optimierte DLLs zu laden. Die Suche nach Symbolen kann viel Zeit in Anspruch nehmen.

## <a name="limitations-of-the-suppress-jit-optimization-option"></a>Einschränkungen der Option „JIT-Optimierung unterdrücken“ 
Es gibt zwei Situationen, in denen das Aktivieren dieser Option **NICHT** funktioniert:

1. In Situationen, in denen der Debugger an einen bereits laufenden Prozess angefügt wird, hat diese Option keine Auswirkungen auf Module, die zum Zeitpunkt der Anfügung des Debuggers bereits geladen wurden.
2. Diese Option hat keine Auswirkung auf DLLs, die in nativem Code vorkompiliert wurden (auch als „Ngen‘ed“ bezeichnet). Sie können jedoch die Verwendung von vorkompiliertem Code deaktivieren, indem Sie den Prozess mit der Umgebungsvariablen **COMPlus_ReadyToRun** auf **0** (null) festlegen. Dadurch wird der .NET Core-Runtime mitgeteilt, die Verwendung von vorkompilierten Images zu deaktivieren. Auf diese Weise wird die Runtime zur JIT-Kompilierung von Frameworkcode gezwungen. 

    > [!IMPORTANT]
    > Wenn Sie .NET Framework oder eine ältere Version von .NET Core (2.x oder niedriger) als Ziel festlegen, fügen Sie auch die Umgebungsvariable „COMPlus_ZapDisable“ hinzu, und legen Sie diese auf „1“ fest.

    **So legen Sie eine Umgebungsvariable für ein .NET Core-Projekt in Visual Studio fest:**
    1. Klicken Sie im **Projektmappen-Explorer** mit der **rechten Maustaste** auf die Projektdatei und anschließend auf **Eigenschaften**.
    2. Navigieren Sie unter **Umgebungsvariablen** zur Registerkarte **Debuggen**, und klicken Sie auf die Schaltfläche **Add** (Hinzufügen).
    3. Legen Sie „Name (Schlüssel)“ auf **COMPlus_ReadyToRun** und „Wert“ auf **0** (null) fest.

    ![Festlegen der Umgebungsvariablen „COMPlus_ReadyToRun“](../debugger/media/environment-variables-debug-menu.png "Festlegen der Umgebungsvariablen „COMPlus_ReadyToRun“")

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Debuggen einer .NET Framework-Quelle](../debugger/how-to-debug-dotnet-framework-source.md)
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md)
- [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Der verwaltete Ausführungsprozess](/dotnet/standard/managed-execution-process)
