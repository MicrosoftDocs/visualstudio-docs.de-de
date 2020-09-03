---
title: Bearbeiten und Fortfahren (Visual C++) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fef02f08ac635687eaaf071188ba0455c6389d9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "74301060"
---
# <a name="edit-and-continue-visual-c"></a>Bearbeiten und Fortfahren (Visual C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können „Bearbeiten und Fortfahren“ in Visual C++-Projekten verwenden. Weitere Informationen zu den Einschränkungen von „Bearbeiten und fortfahren“ finden Sie unter [Unterstützte Codeänderungen (C++)](../debugger/supported-code-changes-cpp.md).  
  
 Ab Visual Studio 2015 Update 1 können Sie jetzt "Bearbeiten und Fortfahren" in Windows Store C++-apps und DirectX-Apps verwenden, da jetzt der **/Zi** -Compilerschalter mit dem **/bigobj** -Schalter unterstützt wird. Sie können "Bearbeiten und Fortfahren" auch mit Binärdateien verwenden, die mit dem Schalter **/fastlink** kompiliert wurden.  
  
 Weitere Update 1-Verbesserungen sind ein neues Wartedialogfeld, das abgebrochen werden kann, sowie eine Benachrichtigung für den Fall, dass „Bearbeiten und Fortfahren“ für eine Datei nicht unterstützt wird. Weitere Informationen zu Update 1-Verbesserungen finden Sie unter [Verbesserungen für C++ bearbeiten und fortfahren in Visual Studio 2015 Update 1](https://devblogs.microsoft.com/cppblog/improvements-for-c-edit-and-continue-in-visual-studio-2015-update-1/).  
  
 Die Compileroption [/Zo (erweitertes optimiertes Debugging)](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f), die in Visual Studio 2013 Update 3 eingeführt wurde, fügt zusätzliche Informationen in PDB-Dateien (Symboldateien) für Binärdateien hinzu, die ohne die Option [/Od ((Debug) deaktivieren)](https://msdn.microsoft.com/library/aafb762y.aspx) kompiliert wurden.  
  
 **/Zo** deaktiviert „Bearbeiten und fortfahren“. Weitere Informationen finden Sie unter [How to: Debuggen von optimiertem Code](../debugger/how-to-debug-optimized-code.md).  
  
## <a name="enable-or-disable-edit-and-continue"></a><a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Aktivieren oder Deaktivieren von „Bearbeiten und Fortfahren“  
 Möglicherweise möchten Sie das automatische Aufrufen von „Bearbeiten und Fortfahren“ deaktivieren, wenn Sie Änderungen am Code vornehmen, die nicht während der aktuellen Debugsitzung angewendet werden sollen. Sie können das automatische Aufrufen von „Bearbeiten und Fortfahren“ später wieder aktivieren.  
  
1. Wählen Sie im Menü **Extras** den Befehl **Optionen**.  
  
2. Wählen Sie im Dialogfeld **Optionen** **Debuggen/allgemein**aus.  
  
3. Aktivieren bzw. deaktivieren Sie in der Gruppe **Bearbeiten und Fortfahren** das Kontrollkästchen **Bearbeiten und Fortfahren aktivieren** .  
  
   Eine Änderung dieser Einstellung betrifft alle Projekte, an denen Sie arbeiten. Sie müssen die Anwendung nicht neu erstellen, nachdem Sie die Einstellung geändert haben. Sie können die Einstellung sogar ändern, während Sie debuggen. Wenn Sie die Anwendung über die Befehlszeile oder ein Makefile-Element erstellen, aber in der Visual Studio-Umgebung Debuggen, können Sie dennoch "Bearbeiten und Fortfahren" verwenden, wenn Sie die Option **/Zi** festlegen.  
  
## <a name="how-to-apply-code-changes-explicitly"></a><a name="BKMK_How_to_apply_code_changes_explicitly"></a> Gewusst wie: Explizites Übernehmen von Codeänderungen  
 In Visual C++ kann „Bearbeiten und Fortfahren“ Codeänderungen auf zweierlei Weise übernehmen. Codeänderungen können implizit übernommen werden, wenn Sie einen Ausführungsbefehl wählen, oder explizit, wenn Sie den Befehl **Codeänderungen übernehmen** verwenden.  
  
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
  
 In Visual C++ werden Sie durch ein Dialogfeld über eine Änderung des Ausführungspunkts informiert. Überprüfen Sie, ob die Position richtig ist, bevor Sie das Debuggen fortsetzen. Ist die Position nicht korrekt, verwenden Sie den Befehl **Nächste Anweisung festlegen** . Weitere Informationen finden Sie unter [Nächste auszuführende Anweisung festlegen](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
## <a name="how-to-work-with-stale-code"></a><a name="BKMK_How_to_work_with_stale_code"></a> Gewusst wie: Arbeiten mit veraltetem Code  
 In einigen Fällen kann Bearbeiten und Fortfahren die Codeänderungen nicht sofort in die ausführbare Datei übernehmen, dies aber möglicherweise zu einem späteren Zeitpunkt nachholen, wenn Sie mit dem Debuggen fortfahren. Dies geschieht, wenn Sie eine Funktion bearbeiten, die die aktuelle Funktion aufruft, bzw. wenn Sie einer Funktion in der Aufrufliste neue Variablen von mehr als 64 Bytes hinzufügen.  
  
 In diesen Fällen fährt der Debugger so lange mit der Ausführung des ursprünglichen Codes fort, bis die Änderungen übernommen werden können. Der veraltete Code wird als temporäre Quelldatei in einem separaten Quellcodefenster angezeigt, mit einem Titel wie `enc25.tmp`. Der bearbeitete Quellcode wird weiterhin im ursprünglichen Quellcodefenster angezeigt. Wenn Sie versuchen, den veralteten Code zu bearbeiten, wird eine Warnmeldung angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterstützte Codeänderungen (C++)](../debugger/supported-code-changes-cpp.md)
