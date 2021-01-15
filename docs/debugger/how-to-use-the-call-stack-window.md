---
title: Anzeigen der Aufrufliste im Debugger | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie das Fender „Aufrufliste“ verwenden, um die Funktions- oder Prozeduraufrufe anzuzeigen, die sich derzeit auf dem Stapel in Visual Studio befinden.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/29/2018
ms.topic: how-to
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 206c79a47ec59e02206332d80d1afe935fb72bdc
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150625"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>In diesem Artikel erhalten Sie Informationen zum Anzeigen der Aufrufliste und Verwenden des Fensters „Aufrufliste“ im Debugger.

Mithilfe des Fensters **Aufrufliste** können Sie die Funktions- und Prozeduraufrufe anzeigen, die sich derzeit im Stapel befinden. Im Fenster **Aufrufliste** wird die Reihenfolge angezeigt, in der Methoden und Funktionen aufgerufen werden. Die Aufrufliste bietet eine nützliche Möglichkeit zum Untersuchen und Verstehen des Ausführungsablaufs einer App.

Wenn für einen Teil der Aufrufliste keine [Debugsymbole](#bkmk_symbols) verfügbar sind, können im Fenster **Aufrufliste** für diesen Teil der Aufrufliste möglicherweise keine korrekten Informationen angezeigt werden. Stattdessen wird Folgendes angezeigt:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> Das Fenster **Aufrufliste** ist mit der Debugperspektive in einigen IDEs wie Eclipse vergleichbar.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den hier beschriebenen. Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Zurücksetzen von Einstellungen](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Anzeigen der Aufrufliste während des Debuggens

- Während des Debuggens können Sie im Menü **Debuggen** auf **Windows > Aufrufliste** klicken.

  ![Fenster „Aufrufliste“](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Ein gelber Pfeil bezeichnet den Stapelrahmen, in dem sich der Ausführungszeiger derzeit befindet. Standardmäßig werden die Informationen dieses Stapelrahmens in der Quelle und in den Fenstern **Lokale Variablen**, **Auto**, **Überwachung** und **Disassemblierung** angezeigt. [Wechseln Sie zu einem anderen Stapelrahmen](#bkmk_switch), um den Debuggerkontext in einen anderen Rahmen auf dem Stapel zu ändern.

## <a name="display-non-user-code-in-the-call-stack-window"></a>Anzeigen von IDE-generiertem Code im Fenster „Aufrufliste“

- Klicken Sie mit der rechten Maustaste auf das Fenster **Aufrufliste**, und wählen Sie **Externen Code anzeigen** aus.

IDE-generierter Code ist sämtlicher Code, der nicht angezeigt wird, wenn [Nur eigenen Code](../debugger/just-my-code.md) aktiviert ist. Bei verwaltetem Code werden Rahmen mit IDE-generiertem Code standardmäßig ausgeblendet. Anstelle der Rahmen mit IDE-generiertem Code wird die folgende Notation angezeigt:

`[<External Code>]`

## <a name="switch-to-another-stack-frame-change-the-debugger-context"></a><a name="bkmk_switch"></a> Wechseln zu einem anderen Stapelrahmen (Ändern des Debuggerkontexts)

1. Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf den Stapelrahmen, dessen Code und Daten angezeigt werden sollen.

    Alternativ können Sie auf einen Rahmen im Fenster **Aufrufliste** doppelklicken, um zu diesem Rahmen zu wechseln.

2. Wählen Sie **Switch to Frame** (Zu Frame wechseln) aus.

     Neben dem ausgewählten Stapelrahmen wird ein grüner Pfeil in Form einer Welle angezeigt. Der Ausführungszeiger verbleibt im ursprünglichen Rahmen, der noch immer durch einen gelben Pfeil gekennzeichnet ist. Wenn Sie im Menü **Debuggen** den Befehl **Schritt** oder **Weiter** auswählen, wird die Ausführung nicht im neu ausgewählten, sondern im ursprünglichen Frame fortgesetzt.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Anzeigen des Quellcodes für eine Funktion in der Aufrufliste

- Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf die Funktion, deren Quellcode Sie anzeigen möchten, und wählen Sie **Gehe zu Quellcode** aus.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Ausführung bis zu einer angegebenen Funktion im Fenster „Aufrufliste“

- Wählen Sie im Fenster **Aufrufliste** die Funktion aus, klicken Sie mit der rechten Maustaste darauf, und wählen Sie dann die Option **Ausführen bis Cursor** aus.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Festlegen eines Haltepunkts am Punkt der Beendigung eines Funktionsaufrufs

- Weitere Informationen finden Sie unter [Festlegen von Breakpoints in Debuggerfenstern](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="display-calls-to-or-from-another-thread"></a>Anzeigen von Aufrufen für oder von anderen Threads

- Klicken Sie mit der rechten Maustaste auf das Fenster **Aufrufliste**, und wählen Sie **Aufrufe zu/von anderen Threads einschließen** aus.

## <a name="visually-trace-the-call-stack"></a>Visuelle Überwachung der Aufrufliste

(Nur) in Visual Studio Enterprise können Sie Code Maps für die Aufrufliste während des Debuggens anzeigen.

- Öffnen Sie das Kontextmenü im Fenster **Aufrufliste**. Klicken Sie auf **Aufrufliste auf Code Map anzeigen** (**STRG** + **UMSCHALT** +  **`** ).

    Weitere Informationen finden Sie unter [Erstellen einer visuellen Map der Aufrufliste während des Debuggens (C#, Visual Basic, C++, JavaScript)](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Aufrufliste auf Code Map anzeigen](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Anzeigen des Disassemblierungscodes für eine Funktion in der Aufrufliste (C#, C++, Visual Basic, F#)

- Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf die Funktion, deren Disassemblycode Sie anzeigen möchten, und wählen Sie **Gehe zu Disassembly** aus.

## <a name="change-the-optional-information-displayed"></a>Ändern der Anzeige optionaler Informationen

- Klicken Sie mit der rechten Maustaste auf das Fenster **Aufrufliste**, und aktivieren oder deaktivieren Sie **\<**_the information that you want_**> anzeigen**.

## <a name="load-symbols-for-a-module-c-c-visual-basic-f"></a><a name="bkmk_symbols"></a> Laden von Symbolen für ein Modul (C#, C++, Visual Basic, F#)

Im Fenster **Aufrufliste** können Sie Debugsymbole für Code laden, für den derzeit keine Symbole geladen sind. Bei diesen Symbolen kann es sich um .NET-Symbole oder Systemsymbole handeln, die von den öffentlichen Microsoft-Symbolservern heruntergeladen wurden, oder um Symbole in einem Symbolpfad auf dem Computer, den Sie debuggen.

Weitere Informationen finden Sie unter [Angeben von Symbol- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-load-symbols"></a>So laden Sie Symbole

1. Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf einen Stapelrahmen, für den keine Symbole geladen werden. Der Rahmen wird abgeblendet.

2. Zeigen Sie auf **Symbole laden**, und klicken Sie dann auf **Microsoft-Symbolserver** (wenn verfügbar). Folgen Sie andernfalls dem Symbolpfad.

### <a name="to-set-the-symbol-path"></a>So legen Sie den Symbolpfad fest

1. Wählen Sie im Fenster **Aufrufliste** im Kontextmenü die Option **Symboleinstellungen** aus.

     Das Dialogfeld **Optionen** wird geöffnet, und die Seite **Symbole** wird angezeigt.

2. Klicken Sie auf **Symboleinstellungen**.

3. Klicken Sie im Dialogfeld **Optionen** auf das Ordnersymbol.

     Im Feld **Speicherorte für Symboldateien (.pdb)** wird ein Cursor angezeigt.

4. Geben Sie einen Verzeichnispfadnamen zum Symbolspeicherort auf dem Computer ein, den Sie debuggen. Beim lokalen und Remotedebuggen ist dies ein Pfad auf Ihrem lokalen Computer.

5. Klicken Sie auf **OK**, um das Dialogfeld **Optionen** zu schließen.

## <a name="see-also"></a>Siehe auch

- [Gemischter Code und fehlende Daten im Fenster "Aufrufliste"](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Viewing data in the debugger (Anzeigen von Daten im Debugger)](../debugger/viewing-data-in-the-debugger.md)
- [Specify symbol (.pdb) and source files (Angeben von Symboldateien (PDB) und Quelldateien)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)