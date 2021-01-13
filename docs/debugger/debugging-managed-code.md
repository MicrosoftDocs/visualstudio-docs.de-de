---
title: Debuggen von verwaltetem Code | Microsoft-Dokumentation
description: Hier finden Sie Informationen zu allgemeinen Debugproblemen und -techniken in Visual Studio für verwaltete Anwendungen oder Apps in Sprachen, die auf die Common Language Runtime abzielen.
ms.custom: SEO-VS-2020
ms.date: 09/23/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e7dadfbc6a02382165b623aeff9d866e9edc975a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727020"
---
# <a name="debug-managed-code-c-visual-basic-f-ccli"></a>Debuggen von verwaltetem Code (C#, Visual Basic, F#, C++/CLI)

In diesem Abschnitt werden die häufigsten Probleme beim Debuggen sowie Verfahrensweisen für verwaltete Anwendungen bzw. Anwendungen erörtert, die in Sprachen für die Common Language Runtime geschrieben wurden, z. B. Visual Basic, C# und C++/CLI. Die in diesem Abschnitt behandelten Verfahren setzen Programmiererfahrung voraus. [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>In diesem Abschnitt

[Diagnosemeldungen im Ausgabefenster](../debugger/diagnostic-messages-in-the-output-window.md)\
Erläutert die <xref:System.Diagnostics.Debug>-Klasse und die <xref:System.Diagnostics.Trace>-Klasse, mit denen Sie Laufzeitmeldungen ins **Ausgabefenster** schreiben können. Die in diesen Klassen enthaltenen Ausgabemethoden ermöglichen die Datenausgabe, ohne die Ausführung zu unterbrechen, sowie die Datenausgabe mit Unterbrechung der Ausführung, wenn eine bestimmte Bedingung nicht erfüllt ist.

[Assertionen in verwaltetem Code](../debugger/assertions-in-managed-code.md)\
Hier werden Assertionen in verwaltetem Code beschrieben. Diese testen Bedingungen, die Sie als Argumente für `Assert`-Methoden angeben. Sie finden in diesem Abschnitt außerdem Beispielcode, Informationen zum Verwenden der <xref:System.Diagnostics.Debug>-Klassenmethode und der <xref:System.Diagnostics.Trace>-Klassenmethode, zur Debug- und zur Releaseversion von Code, Nebeneffekten, Assert-Argumenten, dem Anpassen des Assert-Verhaltens und zu Konfigurationsdateien.

[Stop-Anweisungen in Visual Basic](../debugger/stop-statements-in-visual-basic.md)\
Hier wird die `Stop`-Anweisung beschrieben, die eine Alternative zum Festlegen eines Haltepunkts bietet. Sie finden hier außerdem Beispielcode sowie Vergleiche zwischen der `Stop`-Anweisung und der `End`-Anweisung sowie zwischen der `Stop`-Anweisung und der `Assert`-Anweisung.

[Exemplarische Vorgehensweise: Debuggen eines Windows Forms-Projekts](../debugger/walkthrough-debugging-a-windows-form.md)\
Hier finden Sie Schritt-für-Schritt-Anweisungen zum Erstellen eines Windows Forms und zum Debuggen dieses Formulars. Ein Windows Form, eine Standardkomponente verwalteter Windows-Anwendungen, ist eine der am häufigsten verwendeten verwalteten Anwendungen. In dieser exemplarischen Vorgehensweise werden Visual C# und Visual Basic verwendet, die Verfahrensweisen zum Erstellen eines Windows Forms mit C++ sind jedoch grundsätzlich vergleichbar.

[Debuggen der OnStart-Methode](../debugger/how-to-debug-the-onstart-method.md)\
Dieser Abschnitt enthält Codebeispiele zum Debuggen der `OnStart`-Methode eines verwalteten Windows-Diensts. Um die `OnStart`-Methode eines Windows-Diensts zu debuggen, müssen Sie ein paar Codezeilen hinzufügen, mit denen der Dienst simuliert wird.

[Debuggen im gemischten Modus](../debugger/debugging-mixed-mode-applications.md)\
Erörtert das Debuggen von Anwendungen im gemischten Modus. Dies sind alle Anwendungen, die nativen Code mit verwaltetem Code kombinieren.

[Fehler: Debuggen ist nicht möglich, da ein Kerneldebugger im System aktiviert ist](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)\
In diesem Abschnitt wird eine Fehlermeldung beschrieben, die auftritt, wenn Sie versuchen, verwalteten Code auf einem [!INCLUDE[win7](../debugger/includes/win7_md.md)]-, [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)]-, [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)]-, [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)]- oder Windows NT-System zu debuggen, das im Debugmodus gestartet wurde.

[JIT-Optimierung und -Debuggen](../debugger/jit-optimization-and-debugging.md)\
Beschreibt die Auswirkungen der JIT-Optimierung auf das Debuggen.

[Debuggen von LINQ und DLINQ](../debugger/debugging-linq.md)\
Erörtert Verfahren zum Debuggen von LINQ-Abfragen.

[Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md)\
Beschreibt, wie die Toolfenster **Parallele Aufgaben** und **Parallele Stapel** zum Debuggen einer parallelen Anwendung verwendet werden.

## <a name="related-sections"></a>Verwandte Abschnitte

[IntelliTrace](../debugger/intellitrace.md)\
Fehler werden einfacher und schneller gefunden, da der Ausführungsverlauf mit IntelliTrace aufgezeichnet wird. Sehen Sie sich die aufgezeichneten Ereignisse und Aufrufe sorgfältig an, um den Zustand der Anwendung zu wichtigen Zeitpunkt zu überprüfen. Debuggen Sie den Code, ohne viele Haltepunkte festzulegen oder Ihre Anwendung häufig neu zu starten. Erfordert Visual Studio Enterprise.

[Ablaufverfolgung und Instrumentieren von Anwendungen](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)\
Hier werden die Ablaufverfolgung (eine Methode zum Überwachen der Ausführung einer Anwendung) und die Instrumentation (das Platzieren von Ablaufverfolgungsanweisungen an strategischen Stellen im Code) beschrieben. Die Links in diesem Abschnitt bringen Sie zu den folgenden Themen: Einführung in die Instrumentation und die Ablaufverfolgung, Ablaufverfolgungsschalter, Ablaufverfolgungslistener, Ablaufverfolgung für Code in einer Anwendung, Hinzufügen von Ablaufverfolgungsanweisungen zu Anwendungscode und bedingte Kompilierung mit <xref:System.Diagnostics.Debug> und <xref:System.Diagnostics.Trace>.

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)\
Beschreibt eine Linkeroption, die <xref:System.Diagnostics.DebuggableAttribute> mit C++ geschriebenem Code hinzufügt. Dieses Attribut wird für die Verwendung von Debugfeatures, wie das Anhängen, mit C++ benötigt.

[Debuggen von Windows-Dienstanwendungen](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)\
Hier finden Sie Hinweise zum Debuggen von Windows-Dienstanwendungen, z. B. zum Einrichten, Anhängen an den Prozess, Debuggen des Codes in der `OnStart`-Methode des Diensts und in der Main-Methode, zum Festlegen von Haltepunkten sowie zum Verwenden des Dienststeuerungs-Managers zum Starten, Beenden, Anhalten und Fortsetzen eines Diensts.

[Debuggen und Profilerstellung](/dotnet/framework/debug-trace-profile/index)\
Hier werden das Debuggen von .NET-Anwendungen sowie die Konfigurationsanforderungen beschrieben.

[Debuggen von Skript- und Webanwendungen](how-to-enable-debugging-for-aspnet-applications.md)\
Beschreibt allgemeine Probleme und Verfahren, die beim Debuggen von Skript- und Webanwendungen auftreten können.

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Debuggen von benutzerdefinierten Windows Forms-Steuerelementen zur Entwurfszeit](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)