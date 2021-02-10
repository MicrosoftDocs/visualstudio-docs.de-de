---
title: Vorbereitung zum Debuggen von Konsolenprojekten | Microsoft-Dokumentation
description: Hier erhalten Sie Informationen zum Vorbereiten des Debuggens von Konsolenprojekten (C#, C++, Visual Basic, F#) in Visual Studio.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e39cb7df53a12b97d297ee739338c42a3201089f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872520"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Vorbereitung des Debugvorgangs: Konsolenprojekte (C# , C++ , Visual Basic, F# )

Mit Ausnahme einiger zusätzlicher Punkte wie dem Festlegen von Befehlszeilenargumenten und Anhalten der App zum Debuggen ist die Vorbereitung für das Debuggen eines Konsolenprojekts der Vorbereitung für das Debuggen eines Windows-Projekts sehr ähnlich. Weitere Informationen finden Sie unter [Vorbereitung des Debugvorgangs: Windows Forms-Anwendungen](../debugger/debugging-preparation-windows-forms-applications.md) und [Vorbereitung des Debugvorgangs: Windows Forms-Anwendungen (.NET)](/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100)). Wegen der Ähnlichkeit aller Konsolenanwendungen deckt dieses Thema die folgenden Projekttypen ab:

- C#-, Visual Basic- und F#-Konsolenanwendungen

- C++-Konsolenanwendung (.NET)

- C++-Konsolenanwendung (Win32)

  Für die Eingabe und die Anzeige von Ausgabemeldungen verwendet eine Konsolenanwendung das Fenster **Konsole**. Damit im Fenster **Konsole** geschrieben werden kann, muss die Anwendung anstelle des Debug-Objekts das **Konsole**-Objekt verwenden. Verwenden Sie wie gewohnt das Debug-Objekt, um in das Fenster **Visual Studio-Ausgabe** zu schreiben. Sie sollten genau wissen, in welchem Fenster die Ausgabe erfolgt, da Sie ansonsten u. U. die Ausgabe im falschen Fenster überprüfen. Weitere Informationen finden Sie unter [Console-Klasse](/dotnet/api/system.console), [Debug-Klasse](/dotnet/api/system.diagnostics.debug) und [Ausgabefenster](../ide/reference/output-window.md).

## <a name="set-command-line-arguments"></a>Festlegen von Befehlszeilenargumenten

Für die Konsolenanwendung müssen u. U. Befehlszeilenargumente angegeben werden. Weitere Informationen finden Sie unter [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) oder [Projekteinstellungen für C#-Debugkonfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md).

Wie alle Projekteigenschaften bleiben diese Argumente über die Debug- und Visual Studio-Sitzungen hinweg erhalten. Wenn die Konsolenanwendung zuvor bereits debuggt wurde, sollten Sie daran denken, dass im Dialogfeld **\<Project>Eigenschaftenseiten** noch Argumente aus früheren Sitzungen enthalten sein können.

## <a name="start-the-application"></a>Starten der Anwendung

 Wenn einige Konsolenanwendungen gestartet werden, werden sie vollständig ausgeführt und dann beendet. Dieses Verhalten gibt Ihnen möglicherweise nicht genügend Zeit, um die Ausführung zu unterbrechen und einen Debugvorgang durchzuführen. Zum Debuggen einer Anwendung verwenden Sie eines der folgenden Verfahren, mit dem die Anwendung gestartet wird:

- Legen Sie einen Haltepunkt im Code fest, und starten Sie die Anwendung.

- Starten Sie die Anwendung mit **F10** (**Debuggen** > **Prozedurschritt**) oder **F11** (**Debuggen** > **Einzelschritt**), und navigieren Sie mithilfe anderer Optionen wie **Run to click** (Ausführung bis Klick) durch den Code.

- Klicken Sie im Code-Editor mit der rechten Maustaste auf eine Zeile und anschließend auf **Ausführen bis Cursor**.

  Beim Debuggen einer Konsolenanwendung möchten Sie die Anwendung möglicherweise über die Eingabeaufforderung und nicht von Visual Studio aus starten. In diesem Fall können Sie die Anwendung über die Eingabeaufforderung starten und den Visual Studio-Debugger an die Anwendung anfügen. Weitere Informationen finden Sie unter [Anfügen an laufende Prozesse mit dem Visual Studio Debugger](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

  Wenn Sie eine Konsolenanwendung in Visual Studio starten, wird das Fenster **Konsole** manchmal hinter dem Visual Studio-Fenster angezeigt. Wenn Sie die Konsolenanwendung über Visual Studio starten und anscheinend nichts geschieht, versuchen Sie, das Visual Studio-Fenster zu verschieben.

## <a name="see-also"></a>Siehe auch
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [Vorbereitung des Debugvorgangs: C++-Projekttypen](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Debuggersicherheit](../debugger/debugger-security.md)