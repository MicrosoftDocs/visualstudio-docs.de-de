---
title: Debuggen von nativem Code | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über allgemeine Debuggingprobleme und Techniken für native Anwendungen in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/11/2017
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 8f65cb1a373bdff95e068f78137edf5237ec2905
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872546"
---
# <a name="debugging-native-code"></a>Debuggen von systemeigenem Code
In diesem Abschnitt werden einige allgemeine Debugprobleme und -verfahren für systemeigene Anwendungen erörtert. Bei den in diesem Abschnitt behandelten Verfahren wird Programmiererfahrung vorausgesetzt. Informationen zur Verwendung des Visual Studio-Debuggers finden Sie unter [Ein erster Blick auf den Visual Studio-Debugger](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>In diesem Abschnitt
 [How to: Debug Optimized Code](../debugger/how-to-debug-optimized-code.md) (Debuggen von optimiertem Code): Dieser Artikel enthält Tipps für das Debuggen von optimiertem Code. Dabei wird erläutert, warum Sie eine nicht optimierte Version eines Programms debuggen sollten. Außerdem wird auf Standardoptimierungseinstellungen für die Debug- und Releasekonfiguration eingegangen sowie auf das Finden von Fehlern, die nur bei optimiertem Code auftreten (Aktivieren der Optimierung in einer Debugbuildkonfiguration).

 [DebugBreak und "_debugbreak":](../debugger/debugbreak-and-debugbreak.md) Hier finden Sie eine Beschreibung der Win32-Funktion `DebugBreak` sowie einen Link zum betreffenden Referenzthema im Plattform-SDK. Dort wird auch die systeminterne Funktion `__debugbreak` beschrieben.

 [C-/C++-Assertionen:](../debugger/c-cpp-assertions.md) Hier werden Assertionsanweisungen, ihre Funktionsweise, die Vorteile ihrer Verwendung (Erfassen von Logikfehlern, Überprüfen der Ergebnisse von Vorgängen und Testen von Fehlerzuständen) sowie die Interaktion dieser Anweisungen mit `_DEBUG` und die in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unterstützten Assertionstypen beschrieben.

 [How to: Debug Inline Assembly Code](../debugger/how-to-debug-inline-assembly-code.md) (Debuggen von Inline-Assemblycode): Hier finden Sie kurze Anleitungen zur Verwendung des Disassemblierungsfensters zum Anzeigen von Assemblyanweisungen und des Fensters „Register“ zum Anzeigen von Registerinhalten sowie Links zu Artikeln über diese Fenster.

 [MFC-Debugverfahren:](../debugger/mfc-debugging-techniques.md) Dieser Artikel enthält Links zu Debugtechniken für MFC-Programme, darunter afxDebugBreak, das TRACE-Makro, das Erkennen von Arbeitsspeicherverlust in MFC, MFC-Assertionen und das Verringern der Größe von MFC-Debugbuilds.

 [CRT-Debugverfahren:](../debugger/crt-debugging-techniques.md) Dieser Artikel enthält Links zu Debugtechniken für die C-Laufzeitbibliothek, darunter das Verwenden der CRT-Debugbibliothek, Makros für die Berichterstellung, Unterschiede zwischen malloc und _malloc_dbg, das Schreiben von Hookfunktionen für das Debuggen und der CRT-Debugheap.

 [FAQs zum Debuggen von nativem Code:](../debugger/debugging-native-code-faqs.md) Dieser Artikel enthält Antworten auf häufig gestellte Fragen zum Debuggen von C++-Programmen.

 [Debuggen von COM und ActiveX:](../debugger/com-and-activex-debugging.md) Dieser Artikel enthält Informationen zum Debuggen von COM- und ActiveX-Anwendungen, einschließlich der Tools, die für das Debuggen von COM und ActiveX verwendet werden können.

 [How to: Debug Injected Code](../debugger/how-to-debug-injected-code.md) (Debuggen von eingefügtem Code): Dieser Artikel enthält Hinweise zum Debuggen von Code, in dem Attribute verwendet werden. Zu den behandelten Themen gehören das Aktivieren von Quellcodeanmerkungen, das Anzeigen von eingefügtem Code sowie das Anzeigen des Disassemblycodes am aktuellen Ausführungspunkt.

 [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung in Visual Studio (C#, Visual Basic, C++):](../debugger/walkthrough-debugging-a-parallel-application.md) In diesem Artikel wird beschrieben, wie Sie eine parallele Anwendung mithilfe der Toolfenster **Parallele Aufgaben** und **Parallele Stapel** debuggen.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Vorbereitung des Debugvorgangs: C++-Projekttypen:](../debugger/debugging-preparation-visual-cpp-project-types.md) Dieser Abschnitt enthält Links zu Artikeln über das Debuggen der von den C++-Projektvorlagen erstellten nativen Projekttypen.

 [Debuggen von DLLs in Visual Studio (C#, C++, Visual Basic, F#):](../debugger/debugging-dll-projects.md) Dieser Abschnitt enthält Informationen zum Debuggen von nativen und verwalteten DLLs.

 [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md) enthält Links zu den ausführlicheren Abschnitten der Debugdokumentation. Die Informationen umfassen: Neues im Debugger, Einstellungen und Vorbereitung, Haltepunkte, Ausnahmebehandlung, Bearbeiten und Fortfahren, Debuggen von verwaltetem Code, Debuggen von nativem Code, Debuggen von SQL sowie Referenzen zur Benutzeroberfläche.

## <a name="see-also"></a>Siehe auch

- [Debuggersicherheit](../debugger/debugger-security.md)
- [Debuggen in Visual Studio](../debugger/index.yml)