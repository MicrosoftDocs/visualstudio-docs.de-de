---
title: Debuggen von nativem Code | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 61ee852f75737d85604fda106b15e61dc3634899
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196420"
---
# <a name="debugging-native-code"></a>Debuggen von systemeigenem Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Abschnitt werden einige allgemeine Debugprobleme und -verfahren für systemeigene Anwendungen erörtert. Bei den in diesem Abschnitt behandelten Verfahren wird Programmiererfahrung vorausgesetzt. Die Funktionsweise der Verwendung des Visual Studio-Debuggers finden Sie unter Übersicht über den [Debugger](../debugger/debugger-basics.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [How to: Debuggen von optimiertem Code](../debugger/how-to-debug-optimized-code.md)  
 Enthält Tipps zum Debuggen optimierten Codes, im Einzelnen werden das Debuggen einer nicht optimierten Version eines Programms beschrieben, Standardoptimierungseinstellungen für Debug- und Releasekonfigurationen und das Auffinden von Fehlern, die nur in optimiertem Code vorkommen (Aktivieren der Optimierung in einer Debugbuildkonfiguration).  
  
 [DebugBreak und "_debugbreak"](../debugger/debugbreak-and-debugbreak.md)  
 Hier finden Sie eine Beschreibung der Win32-Funktion `DebugBreak` sowie einen Link zum betreffenden Referenzthema im Plattform-SDK. Dort wird auch die systeminterne Funktion `__debugbreak` beschrieben.  
  
 [C/C++-Assertionen](../debugger/c-cpp-assertions.md)  
 Hier werden Assertionsanweisungen, deren Funktionsweise, die Vorteile ihrer Verwendung (Erfassen von Logikfehlern, Überprüfen der Ergebnisse einer OPeration, Testen von Fehlerzuständen), die Interaktion von Assertionsanweisungen mit `_DEBUG` sowie die in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] unterstützten Assertionstypen beschrieben.  
  
 [Vorgehensweise: Debuggen von Inline-Assemblycode](../debugger/how-to-debug-inline-assembly-code.md)  
 Hier finden Sie kurze Anweisungen zur Verwendung des Disassemblierungsfensters, in dem Assemblyanweisungen angezeigt werden, und des Fensters Register, in dem Registerinhalte angezeigt werden, sowie Links zu Themen über diese Fenster.  
  
 [MFC-Debugverfahren](../debugger/mfc-debugging-techniques.md)  
 Enthält Links zu Debugtechniken für MFC‑Programme, darunter afxDebugBreak, das TRACE-Makro, Erkennen von Speicherverlusten in MFC, MFC‑Assertionen und Verringern der Größe eines MFC‑Debugbuilds.  
  
 [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md)  
 Enthält Links zu Debugtechniken für die C-Laufzeitbibliothek, darunter Verwenden der CRT-Debugbibliothek, Makros für die Berichterstellung, Unterschiede zwischen malloc und _malloc_dbg, Schreiben von Hookfunktionen für das Debuggen und CRT-Debugheap.  
  
 [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)  
 Bietet Antworten auf häufig gestellte Fragen zum Debuggen von Visual C++-Programmen  
  
 [Debuggen von COM und ActiveX](../debugger/com-and-activex-debugging.md)  
 Bietet Informationen zum Debuggen von COM- und ActiveX-Anwendungen, einschließlich der Tools, die für das Debuggen von COM und ActiveX verwendet werden können.  
  
 [Gewusst wie: Debuggen von systemeigenen DLLs](../debugger/how-to-debug-native-dlls.md)  
 Erläutert das Einrichten des Debuggens für DLLs aus systemeigenem Code.  
  
 [Vorgehensweise: Debuggen von eingefügtem Code](../debugger/how-to-debug-injected-code.md)  
 Bietet Hinweise zum Debuggen von Code, in dem Attribute verwendet werden. Zu den behandelten Themen gehören das Aktivieren von Quellcodeanmerkungen, das Anzeigen von eingefügtem Code sowie das Anzeigen des Disassemblycodes am aktuellen Ausführungspunkt.  
  
 [Exemplarische Vorgehensweise: Debuggen einer Parallelanwendung](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Beschreibt, wie die Toolfenster **Parallele Aufgaben** und **Parallele Stapel** zum Debuggen einer parallelen Anwendung verwendet werden.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Visual C++-Projekttypen](../debugger/debugging-preparation-visual-cpp-project-types.md)  
 Enthält Links zu Themen über das Debuggen systemeigener Projekttypen, die durch die Visual C++-Projektvorlagen erstellt werden.  
  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)  
 Enthält Links zu den ausführlicheren Abschnitten der Debugdokumentation. Die Informationen umfassen: Neues im Debugger, Einstellungen und Vorbereitung, Haltepunkte, Ausnahmebehandlung, Bearbeiten und Fortfahren, Debuggen von verwaltetem Code, Debuggen von nativem Code, Debuggen von SQL sowie Referenzen zur Benutzeroberfläche.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugger-Sicherheit](../debugger/debugger-security.md)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)
