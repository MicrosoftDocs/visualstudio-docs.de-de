---
title: 'Häufig gestellte Fragen: Suchen Ihrer Debugfunktion'
description: Enthält häufig gestellte Fragen zur Identifizierung der Debugfunktion, die Ihnen beim Debuggen Ihrer App als Hilfe dient.
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c215b232c64b97c57285618056ee4675587b48e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870713"
---
# <a name="faq---find-the-debugging-feature-you-need-in-visual-studio"></a>Häufig gestellte Fragen: Suchen nach der benötigten Debugfunktion in Visual Studio

Wenn Sie Hilfe benötigen, um die Debugaufgabe der richtigen Funktion des Visual Studio-Debuggers zuzuordnen, die relevant ist, verwenden Sie die in diesem Artikel bereitgestellten Links. Die Liste der Aufgaben enthält allgemeine Aufgaben, z. B. das Anhalten von Code zum Debuggen, Untersuchen von Variablen und Senden von Meldungen an das **Ausgabe** fenster. Einen allgemeineren Überblick über die Funktionen des Debuggers finden Sie unter [Ein erster Blick auf den Debugger](debugger-feature-tour.md).

## <a name="fix-an-exception"></a>Beseitigen einer Ausnahme

- Weitere Informationen finden Sie unter [Beseitigen einer Ausnahme](write-better-code-with-visual-studio.md#fix-an-exception).

## <a name="pause-running-code"></a>Anhalten von aktuell ausgeführtem Code

- **Anhalten des ausgeführten Codes, um eine Codezeile zu untersuchen, die möglicherweise einen Fehler enthält**

  Festlegen eines Haltepunkts. Weitere Informationen finden Sie unter [Verwenden von Haltepunkten](using-breakpoints.md).

- **Anhalten und Untersuchen der App, wenn sie einen bestimmten Zustand erreicht**

  Probieren Sie einen bedingten Breakpoint aus, um mithilfe von bedingter Logik zu steuern, wo und wann ein Breakpoint aktiviert wird. Weitere Informationen finden Sie unter [Breakpointbedingungen](using-breakpoints.md#breakpoint-conditions).

- **Code nur anhalten, wenn sich die Eigenschaft oder der Wert eines bestimmten Objekts ändert**

  Legen Sie für C++ einen [Datenbreakpoint](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus) fest. 
  ::: moniker range=">= vs-2019"
  Für Apps, die .NET Core 3 verwenden, können Sie ebenfalls einen [Datenbreakpoint](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed) festlegen.
  ::: moniker-end

  Andernfalls können Sie nur für C# und F# eine [Objekt-ID mit einem bedingten Breakpoint nachverfolgen](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

- **Anhalten von Code innerhalb einer Schleife bei einer bestimmten Iteration**

  Legen Sie einen Breakpoint mithilfe von **Trefferanzahl** als Bedingung fest. Weitere Informationen finden Sie unter [Trefferanzahl](using-breakpoints.md#set-a-hit-count-condition).

- **Anhalten von Code am Anfang einer Funktion, wenn Sie den Funktionsnamen, aber nicht den Speicherort kennen**

  Hierfür können Sie einen Funktionsbreakpoint verwenden. Weitere Informationen finden Sie unter [Festlegen von Funktionbreakpoints](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Anhalten von Code am Anfang mehrerer Funktionen mit dem gleichen Namen**

  Wenn Sie über mehrere Funktionen mit dem gleichen Namen (überladene Funktionen oder Funktionen in unterschiedlichen Projekten) verfügen, können Sie einen [Funktionsbreakpoint](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file) verwenden.

- **Verwalten und Nachverfolgen von Breakpoints**

  Verwenden Sie das Fenster **Breakpoints**. Weitere Informationen finden Sie unter [Verwalten von Breakpoints](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

- **Anhalten von Code und Debuggen, wenn eine bestimmte behandelte oder nicht behandelte Ausnahme ausgelöst wird**

  Obwohl das Ausnahmehilfsprogramm zeigt, wo ein Fehler aufgetreten ist, können Sie den [Debugger anweisen, eine Unterbrechung vorzunehmen, wenn eine Ausnahme ausgelöst wird](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown), wenn Sie die Ausführung anhalten und den spezifischen Fehler debuggen möchten.

- **Festlegen eines Breakpoints aus der Aufrufliste**

  Wenn Sie Code anhalten und debuggen möchten, während Sie den Ausführungsfluss untersuchen oder Funktionen in den **Aufruflistenfenstern** anzeigen, finden Sie weitere Informationen unter [Festlegen eines Breakpoints im Aufruflistenfenster](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

- **Anhalten von Code an einer bestimmten Assemblyanweisung**

  Dies können Sie erreichen, indem Sie im [Fenster „Disassemblierung“ einen Breakpoint festlegen](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Ausführen von Code

- **Erlernen der Befehle zum schrittweisen Durchlaufen des Codes während des Debuggens**

  Weitere Informationen finden Sie unter [Navigieren im Code mit dem Debugger](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Untersuchen von Daten

- **Überprüfen des Werts von Variablen beim Ausführen der App**

  Zeigen Sie mit der Maus auf Variablen, und verwenden Sie [Datentipps](view-data-values-in-data-tips-in-the-code-editor.md), oder [untersuchen Sie Variablen im Fenster für automatische und lokale Variablen](autos-and-locals-windows.md).

- **Beobachten des sich ändernden Werts einer bestimmten Variablen**

  Legen ein Überwachungselement für die Variable fest. Weitere Informationen finden Sie unter [Festlegen eines Überwachungselements für Variablen](watch-and-quickwatch-windows.md).

- **Anzeigen von Zeichenfolgen, die zu lang für das Debuggerfenster sind**

  Öffnen Sie beim Debuggen die integrierte [Zeichenfolgenschnellansicht](view-strings-visualizer.md).

## <a name="debug-an-app-that-is-already-running"></a>Debuggen einer App, die bereits ausgeführt wird

- Weitere Informationen finden Sie unter [Anfügen an laufenden Prozess](attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="debug-multithreaded-applications"></a>Debuggen von Multithreadanwendungen

- Weitere Informationen finden Sie unter [Debuggen von Multithreadanwendungen](debug-multithreaded-applications-in-visual-studio.md).

## <a name="configure-debugging"></a>Konfigurieren des Debuggens

- **Konfigurieren von Debuggereinstellungen**

  Weitere Informationen zum Konfigurieren von Debuggeroptionen und Debuggerprojekteinstellungen finden Sie unter [Debuggereinstellungen und -vorbereitung](debugger-settings-and-preparation.md).

- **Anpassen der im Debugger angezeigten Informationen**

  Möglicherweise möchten Sie andere Informationen als den Objekttyp als Wert in anderen Debuggerfenstern anzeigen. Verwenden Sie für C#-, Visual Basic-, F#- und C++/CLI-Code das [DebuggerDisplay](using-the-debuggerdisplay-attribute.md)-Attribut. Für erweiterte Optionen können Sie die Benutzeroberfläche auch anpassen, indem Sie eine [benutzerdefinierte Schnellansicht](create-custom-visualizers-of-data.md) erstellen.

  Verwenden Sie für natives C++ das [NatVis-Framework](create-custom-views-of-native-objects.md).

## <a name="additional-tasks"></a>Zusätzliche Aufgaben

- **Bearbeiten von Code während einer Debugsitzung**

  Verwenden Sie [Bearbeiten und fortfahren](edit-and-continue.md). Verwenden Sie für XAML [XAML Hot Reload](../xaml-tools/xaml-hot-reload.md).

- **Senden von Nachrichten an das Ausgabefenster, ohne Code zu ändern**

  Legen Sie einen Ablaufverfolgungspunkt fest. Weitere Informationen finden Sie unter [Verwenden von Ablaufverfolgungspunkten](using-tracepoints.md).

- **Anzeigen der Reihenfolge, in der Funktionen aufgerufen werden**

  Weitere Informationen finden Sie unter [Anzeigen der Aufrufliste](how-to-use-the-call-stack-window.md).

- **Debuggen auf Remotecomputern**

  Weitere Informationen finden Sie unter [Remote debugging (Remotedebuggen)](remote-debugging.md).

- **Beheben der Leistungsprobleme**

  Weitere Informationen finden Sie unter [Einführung in Profilerstellungstools](../profiling/profiling-feature-tour.md)
