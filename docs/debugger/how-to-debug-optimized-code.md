---
title: Debuggen von optimiertem Code | Microsoft-Dokumentation
description: Erstellen Sie nach Möglichkeit kein Win32-Releaseziel, bis das Programm debuggt wird, da die Optimierung das Debuggen erschweren kann. Ausführlichere Informationen finden Sie in diesem Artikel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 971ceb59a17788076a1188e42d834f7b4bd704cc
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903180"
---
# <a name="how-to-debug-optimized-code"></a>Vorgehensweise: Debuggen von optimiertem Code

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

> [!NOTE]
> Die Compileroption [/Zo (erweitertes optimiertes Debugging)](/cpp/build/reference/zo-enhance-optimized-debugging) (eingeführt in Visual Studio Update 3) generiert umfassendere Debuginformationen für optimierten Code (Projekte, die nicht mit der Compileroption **/Od** erstellt wurden. Siehe [/O-Optionen (Code optimieren)](/cpp/build/reference/o-options-optimize-code)). Dazu gehört verbesserte Unterstützung zum Debuggen von lokalen Variablen und Inlinefunktionen.
>
> [Bearbeiten und Fortfahren](../debugger/edit-and-continue-visual-csharp.md) ist deaktiviert, wenn die **/Zo**-Compileroption verwendet wird.

 Wenn der Compiler Code optimiert, werden die Anweisungen neu positioniert und organisiert. Hierdurch wird die Effizienz des kompilierten Codes erhöht. Aufgrund dieser Neuanordnung ist der Debugger nicht immer in der Lage, den Quellcode, der einer bestimmten Gruppe von Anweisungen entspricht, zu erkennen.

 Durch die Optimierung können folgende Bereiche beeinflusst werden:

- Lokale Variablen, die durch den Optimierer entfernt oder an Speicherorte verschoben werden können, die vom Debugger nicht erkannt werden.

- Positionen in einer Funktion, die geändert werden, wenn Codeblöcke durch den Optimierer zusammenführt werden.

- Funktionsnamen für Rahmen der Aufrufliste, die möglicherweise falsch sind, wenn der Optimierer zwei Funktionen zusammenführt.

  Die in der Aufrufliste angezeigten Rahmen sind fast immer korrekt, vorausgesetzt, es sind für alle Rahmen Symbole vorhanden. Die Rahmen der Aufrufliste sind falsch, wenn die Aufrufliste beschädigt ist, wenn Funktionen in der Assemblysprache geschrieben wurden oder wenn es sich um Betriebssystemrahmen ohne entsprechende Symbole in der Aufrufliste handelt.

  Globale und statische Variablen werden immer richtig angezeigt. Dies trifft auch auf das Strukturlayout zu. Wenn ein Zeiger auf eine Struktur vorhanden und der Wert des Zeigers richtig ist, zeigt jede Membervariable der Struktur den richtigen Wert an.

  Aufgrund dieser Einschränkungen müssen Debugoperationen, wenn überhaupt möglich, unter Verwendung einer nicht optimierten Version des Programms erfolgen. In der Debugkonfiguration eines C++-Programms ist die Optimierung standardmäßig deaktiviert, während sie in der Releasekonfiguration aktiviert ist.

  Ein Fehler ist jedoch nur in einer optimierten Programmversion erkennbar. In diesem Fall muss der optimierte Code gedebuggt werden.

## <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>So aktivieren Sie die Optimierung in einer Debugbuildkonfiguration

1. Wählen Sie beim Erstellen eines neuen Projekts `Win32 Debug` als Ziel aus. Verwenden Sie das `Win32 Debug`-Ziel, bis das Programm vollständig debuggt und für die Erstellung eines `Win32 Release`-Ziels bereit ist. Das `Win32 Debug`-Ziel wird nicht vom Compiler optimiert.

2. Wählen Sie das Projekt im Projektmappen-Explorer aus.

3. Klicken Sie im Menü **Ansicht** auf die Option **Eigenschaftenseiten**.

4. Stellen Sie im Dialogfeld **Eigenschaftenseiten** sicher, dass die Option `Debug` in der Dropdownliste **Konfiguration** ausgewählt ist.

5. Wählen Sie in der Ordneransicht auf der linken Seite den Ordner **C/C++** aus.

6. Wählen Sie `Optimization` im Ordner **C++** aus.

7. Suchen Sie die Option `Optimization` in der Eigenschaftenliste auf der rechten Seite. Die Einstellung daneben lautet vermutlich `Disabled (`[/Od](/cpp/build/reference/od-disable-debug)`)`. Wählen Sie eine der anderen Optionen aus (`Minimum Size``(`[/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Maximum Speed``(`[/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Full Optimization``(`[/Ox](/cpp/build/reference/ox-full-optimization)`)` oder `Custom`).

8. Wenn Sie für die `Custom` die Option `Optimization` auswählen, können Sie Optionen für alle weiteren Eigenschaften in der Eigenschaftenliste festlegen.

9. Wählen Sie den C/C++-Befehlszeilenknoten „Konfigurationseigenschaften“ der Eigenschaftenseite des Projekts aus, und fügen Sie `(`[/Zo](/cpp/build/reference/zo-enhance-optimized-debugging)`)` dem Textfeld **Weitere Optionen** hinzu.

    > [!WARNING]
    > Für `/Zo` ist Visual Studio 2013 Update 3 oder höher erforderlich.
    >
    >  Das Hinzufügen von `/Zo` deaktiviert [Bearbeiten und Fortfahren](../debugger/edit-and-continue-visual-csharp.md).

   Ermitteln Sie beim Debuggen von optimiertem Code im Fenster **Disassemblierung**, welche Anweisungen tatsächlich generiert und ausgeführt werden. Beim Festlegen von Haltepunkten sollten Sie beachten, dass der Haltepunkt zusammen mit einer Anweisung verschoben werden kann. Beachten Sie z. B. folgenden Code:

```cpp
for (x=0; x<10; x++)
```

 Angenommen, Sie haben in dieser Zeile einen Haltepunkt festgelegt. Sie gehen möglicherweise davon aus, dass der Haltepunkt 10 Mal getroffen wird. Wenn der Code optimiert ist, wird er jedoch nur einmal getroffen. Dies liegt daran, dass die erste Anweisung den Wert von `x` auf 0 festlegt. Der Compiler erkennt, dass dies nur einmal durchgeführt werden muss und verschiebt es aus der Schleife. Gleichzeitig wird auch der Haltepunkt verschoben. Die Anweisungen zum Vergleichen und Heraufsetzen von `x` verbleiben innerhalb der Schleife. Wenn Sie das Fenster **Disassemblierung** anzeigen, wird die [Schritteinheit](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)) zur besseren Steuerung automatisch auf „Befehl“ festgelegt. Dies ist bei der schrittweisen Ausführung von optimiertem Code von Vorteil.

## <a name="see-also"></a>Siehe auch

- [Debuggersicherheit](../debugger/debugger-security.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)