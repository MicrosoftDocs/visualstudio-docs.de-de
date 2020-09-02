---
title: Senden von Meldungen an das Ausgabefenster | Microsoft-Dokumentation
ms.date: 11/08/2018
ms.topic: how-to
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85d3c146775ac06b3118186738ee74932a4c452a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350471"
---
# <a name="send-messages-to-the-output-window"></a>Senden von Meldungen an das Ausgabefenster

Laufzeitmeldungen können im **Ausgabefenster** mithilfe der <xref:System.Diagnostics.Debug>-Klasse oder der <xref:System.Diagnostics.Trace>-Klasse ausgegeben werden. Beide sind Bestandteil der <xref:System.Diagnostics>-Klassenbibliothek. Falls die Ausgabe lediglich in der *Debugversion* des Programms erfolgen soll, verwenden Sie die <xref:System.Diagnostics.Debug>-Klasse. Soll die Ausgabe sowohl in der *Debug*- als auch in der *Releaseversion* erfolgen, verwenden Sie die <xref:System.Diagnostics.Trace>-Klasse.

## <a name="output-methods"></a>Ausgabemethoden
 Die <xref:System.Diagnostics.Trace>-Klasse und die <xref:System.Diagnostics.Debug>-Klasse stellen die folgenden Ausgabemethoden bereit:

- Verschiedene `Write`-Methoden, die die Ausgabe von Informationen ermöglichen, ohne dass die Ausführung unterbrochen wird. Diese Methoden ersetzen die `Debug.Print`-Methode, die in früheren Versionen von Visual Basic verwendet wurde.

- Die <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>-Methode und die <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>-Methode, durch die die Ausführung unterbrochen wird und Informationen ausgegeben werden, wenn eine festgelegte Bedingung nicht erfüllt ist. Standardmäßig werden die Informationen der `Assert`-Methode in einem Dialogfeld angezeigt. Weitere Informationen finden Sie unter [Assertionen in verwaltetem Code](../debugger/assertions-in-managed-code.md).

- Die <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName>-Methode und die <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>-Methode, durch die die Ausführung stets unterbrochen wird und Informationen ausgegeben werden. Standardmäßig werden die Informationen der `Fail`-Methoden in einem Dialogfeld angezeigt.

Im Fenster **Ausgabe** können auch Informationen zu Folgendem angezeigt werden:

- Module, die der Debugger geladen oder entladen hat.

- Ausnahmen, die ausgelöst werden.

- Prozesse, die beendet werden.

- Threads, die beendet werden.

## <a name="see-also"></a>Siehe auch
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Ausgabefenster](../ide/reference/output-window.md)
- [Stapelüberwachung und Instrumentieren von Anwendungen](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
