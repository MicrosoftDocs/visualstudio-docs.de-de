---
title: Bearbeiten und fortfahren (C#) | Microsoft-Dokumentation
description: „Bearbeiten und fortfahren“ ist für C++-Projekte verfügbar. Hier erfahren Sie, welche Änderungen unterstützt werden und wie Sie steuern können, ob und wann Ihre Änderungen angewendet werden.
ms.custom: SEO-VS-2020
ms.date: 05/31/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 0c4fd6d5214211318e2271418425a117a73eb0ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871883"
---
# <a name="edit-and-continue-c"></a>Bearbeiten und Fortfahren (C++)
Sie können „Bearbeiten und fortfahren“ in C++-Projekten verwenden. Weitere Informationen zu den Einschränkungen von „Bearbeiten und fortfahren“ finden Sie unter [Unterstützte Codeänderungen (C++)](../debugger/supported-code-changes-cpp.md).

Weitere Informationen zu den Verbesserungen von Visual Studio 2015 Update 3 finden Sie unter [C++ „Bearbeiten und fortfahren“ in Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

 Die Compileroption [/Zo (erweitertes optimiertes Debugging)](/cpp/build/reference/zo-enhance-optimized-debugging), die in Visual Studio 2013 Update 3 eingeführt wurde, fügt zusätzliche Informationen in PDB-Dateien (Symboldateien) für Binärdateien hinzu, die ohne die Option [/Od ((Debug) deaktivieren)](/cpp/build/reference/od-disable-debug) kompiliert wurden.

 **/Zo** deaktiviert „Bearbeiten und fortfahren“. Weitere Informationen finden Sie unter [How to: Debuggen von optimiertem Code](../debugger/how-to-debug-optimized-code.md).

## <a name="enable-or-disable-edit-and-continue"></a><a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Aktivieren oder Deaktivieren von „Bearbeiten und Fortfahren“
 Möglicherweise möchten Sie das automatische Aufrufen von „Bearbeiten und Fortfahren“ deaktivieren, wenn Sie Änderungen am Code vornehmen, die nicht während der aktuellen Debugsitzung angewendet werden sollen. Sie können das automatische Aufrufen von „Bearbeiten und Fortfahren“ später wieder aktivieren.

> [!IMPORTANT]
> Erforderliche Buildeinstellungen und weitere Informationen zur Featurekompatibilität finden Sie unter [C++ „Bearbeiten und fortfahren“ in Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

1. Wenn Sie sich in einer Debugsitzung befinden, brechen Sie das Debuggen ab (**UMSCHALT+F5**).

2. Wählen Sie im Menü **Extras** den Befehl **Optionen**.

3. Wählen Sie im Dialogfeld **Optionen** den Eintrag **Debugging > Allgemein** aus.

4. Wählen Sie zum Aktivieren **„Bearbeiten und fortfahren“ aktivieren** aus. Deaktivieren Sie das Kontrollkästchen, wenn Sie die Funktion deaktivieren möchten.

5. Aktivieren bzw. deaktivieren Sie in der Gruppe **Bearbeiten und Fortfahren** das Kontrollkästchen **Bearbeiten und Fortfahren aktivieren** .

   Eine Änderung dieser Einstellung betrifft alle Projekte, an denen Sie arbeiten. Sie müssen die Anwendung nicht neu erstellen, nachdem Sie die Einstellung geändert haben. Wenn Sie die Anwendung über die Befehlszeile oder mit einem Makefile erstellen, jedoch in der Visual Studio-Umgebung debuggen, können Sie die Option „Bearbeiten und Fortfahren“ trotzdem verwenden, sofern Sie die **/ZI**-Option festlegen.

## <a name="how-to-apply-code-changes-explicitly"></a><a name="BKMK_How_to_apply_code_changes_explicitly"></a> Gewusst wie: Explizites Übernehmen von Codeänderungen
 In C++ kann „Bearbeiten und fortfahren“ Codeänderungen auf zweierlei Weise übernehmen. Codeänderungen können implizit übernommen werden, wenn Sie einen Ausführungsbefehl wählen, oder explizit, wenn Sie den Befehl **Codeänderungen übernehmen** verwenden.

 Wenn Sie Codeänderungen explizit übernehmen, bleibt das Programm im Unterbrechungsmodus und wird nicht ausgeführt.

- Um Codeänderungen explizit zu übernehmen, wählen Sie im Menü **Debuggen** die Option **Codeänderungen übernehmen**.

## <a name="how-to-stop-code-changes"></a><a name="BKMK_How_to_stop_code_changes"></a> Gewusst wie: Anhalten von Codeänderungen
 Während Bearbeiten und Fortfahren Codeänderungen übernimmt, können Sie den Vorgang anhalten.

 So halten Sie das Übernehmen von Codeänderungen an:

- Wählen Sie im Menü **Debuggen** die Option **Übernehmen von Codeänderungen beenden**.

  Dieses Menüelement ist nur sichtbar, wenn Codeänderungen übernommen werden.

  Bei Verwendung dieser Option wird keine der Codeänderungen übernommen.

## <a name="how-to-reset-the-point-of-execution"></a><a name="BKMK_How_to_reset_the_point_of_execution"></a> Gewusst wie: Zurücksetzen des Ausführungspunkts
 Einige Codeänderungen können dazu führen, dass der Ausführungspunkt an eine neue Position verschoben wird, wenn die Änderung von "Bearbeiten und Fortfahren" übernommen wird. Mit "Bearbeiten und Fortfahren" wird der Ausführungspunkt so genau wie möglich platziert. Das Ergebnis ist jedoch möglicherweise nicht korrekt.

 In C++ werden Sie durch ein Dialogfeld über eine Änderung des Ausführungspunkts informiert. Überprüfen Sie, ob die Position richtig ist, bevor Sie das Debuggen fortsetzen. Ist die Position nicht korrekt, verwenden Sie den Befehl **Nächste Anweisung festlegen** . Weitere Informationen finden Sie unter [Nächste auszuführende Anweisung festlegen](./navigating-through-code-with-the-debugger.md#BKMK_Set_the_next_statement_to_execute).

## <a name="how-to-work-with-stale-code"></a><a name="BKMK_How_to_work_with_stale_code"></a> Gewusst wie: Arbeiten mit veraltetem Code
 In einigen Fällen kann Bearbeiten und Fortfahren die Codeänderungen nicht sofort in die ausführbare Datei übernehmen, dies aber möglicherweise zu einem späteren Zeitpunkt nachholen, wenn Sie mit dem Debuggen fortfahren. Dies geschieht, wenn Sie eine Funktion bearbeiten, die die aktuelle Funktion aufruft, bzw. wenn Sie einer Funktion in der Aufrufliste neue Variablen von mehr als 64 Bytes hinzufügen.

 In diesen Fällen fährt der Debugger so lange mit der Ausführung des ursprünglichen Codes fort, bis die Änderungen übernommen werden können. Der veraltete Code wird als temporäre Quelldatei in einem separaten Quellcodefenster angezeigt, mit einem Titel wie `enc25.tmp`. Der bearbeitete Quellcode wird weiterhin im ursprünglichen Quellcodefenster angezeigt. Wenn Sie versuchen, den veralteten Code zu bearbeiten, wird eine Warnmeldung angezeigt.

## <a name="see-also"></a>Siehe auch
- [Unterstützte Codeänderungen (C++)](../debugger/supported-code-changes-cpp.md)