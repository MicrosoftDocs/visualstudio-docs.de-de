---
title: Anzeigen von Disassemblierungscode im Debugger | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie das Disassemblierungsfenster in Visual Studio verwenden, um Assemblycode anzuzeigen, der den vom Compiler erstellten Anweisungen entspricht.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/30/2018
ms.topic: how-to
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 733eb439808d6cab2d290615751cf44ccd711022
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150612"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Anzeigen von Disassemblierungscode im Visual Studio-Debugger (C#, C++, Visual Basic, F#)

Im Fenster **Disassemblierung** wird der Assemblycode angezeigt, der den vom Compiler erstellten Anweisungen entspricht. Beim Debuggen von verwaltetem Code entsprechen diese Assemblierungsanweisungen nicht der durch den Visual Studio-Compiler generierten Microsoft Intermediate Language (MSIL), sondern dem durch den Just-In-Time-Compiler (JIT) erstellten nativen Code.

> [!NOTE]
> Um das Fenster **Disassemblierung** in vollem Umfang nutzen zu können, sollten Sie sich mit den Grundlagen der [Assemblersprache](https://wikipedia.org/wiki/Assembly_language) (Programmiersprache) vertraut machen.

Diese Funktion ist nur verfügbar, wenn das Debuggen auf Adressebene aktiviert ist. Sie ist nicht für das Skript- oder SQL-Debuggen verfügbar.

Neben den Assemblyanweisungen können folgende optionale Informationen im Fenster **Disassemblierung** angezeigt werden:

- Speicheradresse, an der sich die einzelnen Anweisungen befinden. Bei nativen Anwendungen ist dies die eigentliche Speicheradresse. Bei Visual Basic oder C# ist dies ein Offset vom Beginn der Funktion.

- Quellcode, aus dem der Assemblercode abgeleitet wird.

- Codebytes sind Bytedarstellungen der eigentlichen Maschinen- oder MSIL-Anweisungen.

- Symbolnamen für die Speicheradressen.

- Mit dem Quellcode übereinstimmende Zeilennummern.

Anweisungen in Assemblersprache bestehen aus *mnemonischem Code* (Abkürzungen für Anweisungsnamen) sowie *Symbolen* für Variablen, Register und Konstanten. Jede Anweisung in Maschinensprache wird durch einen mnemonischen Code in Assemblersprache dargestellt, dem optional eine oder mehrere Symbole folgen.

Assemblercode basiert in hohem Maß auf Prozessorregistern oder bei verwaltetem Code auf Common Language Runtime-Registern. Sie können das Fenster **Disassemblierung** zusammen mit dem Fenster **Register** verwenden, in dem Sie Registerinhalte überprüfen können.

Verwenden Sie zum Anzeigen von Anweisungen in Maschinencode in unformatierter numerischer Form (und nicht in Assemblersprache) das Fenster **Speicher**, oder wählen Sie **Codebytes** im Fenster **Disassemblierung** aus.

## <a name="use-the-disassembly-window"></a>Verwenden des Disassembierungsfensters

Klicken Sie unter **Extras** > **Optionen** > **Debuggen** auf **Debugging auf Adressebene aktivieren**, um das Fenster **Disassemblierung** zu aktivieren.

Um das Fenster **Disassemblierung** während des Debuggens zu öffnen, wählen Sie **Fenster** > **Disassemblierung** aus, oder drücken Sie **ALT**+**8**.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

Um optionale Informationen anzuzeigen oder auszublenden, klicken Sie mit der rechten Maustaste in das Fenster **Disassemblierung**, und aktivieren bzw. deaktivieren Sie im Kontextmenü die gewünschten Optionen.

Ein gelber Pfeil am linken Rand kennzeichnet den aktuellen Ausführungspunkt. Bei nativem Code entspricht der Ausführungspunkt dem Programmzähler der CPU. Diese Position zeigt die nächste Anweisung an, die im Programm ausgeführt wird.

## <a name="see-also"></a>Siehe auch

* [Paging up or down in memory (Vertikales Paging im Arbeitsspeicher)](../debugger/how-to-page-up-or-down-in-memory.md)
* [Viewing data in the debugger (Anzeigen von Daten im Debugger)](../debugger/viewing-data-in-the-debugger.md)
* [How to: Verwenden des Fensters „Register“](../debugger/how-to-use-the-registers-window.md)