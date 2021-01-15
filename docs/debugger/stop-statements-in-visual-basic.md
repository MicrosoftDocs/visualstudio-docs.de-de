---
title: Stop-Anweisungen in Visual Basic | Microsoft-Dokumentation
description: In diesem Artikel wird die Stop-Anweisung von Visual Basic erläutert, die eine programmgesteuerte Alternative zum Festlegen eines Breakpoints in Visual Studio darstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b36f00f628d9551d8e45075d790d8e5d2de294dc
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149429"
---
# <a name="stop-statements-in-visual-basic"></a>Stop-Anweisungen in Visual Basic

Die Stop-Anweisung in Visual Basic bietet eine Alternative zum Festlegen eines Haltepunktes. Wenn der Debugger auf eine Stop-Anweisung trifft, wird die Programmausführung unterbrochen (der Unterbrechungsmodus wird aktiviert). C#-Programmierer erzielen den gleichen Effekt mit einem Aufruf von <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>.

Sie legen Stop-Anweisungen fest oder entfernen sie, indem Sie den Quellcode bearbeiten. Stop-Anweisungen können im Gegensatz zu Haltepunkten jedoch nicht mithilfe von Debuggerbefehlen definiert oder entfernt werden.

Anders als eine End-Anweisung setzt die Stop-Anweisung keine Variablen zurück und kehrt auch nicht zum Entwurfsmodus zurück. Um mit der Programmausführung fortzufahren, können Sie im Menü Debuggen die Option Weiter auswählen.

Beim Ausführen einer Visual Basic-Anwendung außerhalb des Debuggers bewirkt eine Stop-Anweisung, dass der Debugger gestartet wird, sofern Just‑In‑Time-Debuggen aktiviert ist. Ist Just-In-Time-Debuggen nicht aktiviert, verhält sich die Stop-Anweisung wie eine End-Anweisung und beendet die Ausführung. Da kein QueryUnload-Ereignis oder Unload-Ereignis auftritt, müssen alle Stop-Anweisungen aus der Releaseversion der Visual Basic-Anwendung entfernt werden. Weitere Informationen hierzu finden Sie unter [Just-In-Time-Debuggen](just-in-time-debugging-in-visual-studio.md).

 Damit Sie Stop-Anweisungen nicht explizit entfernen müssen, können Sie die bedingte Kompilierung nutzen:

```vb
#If DEBUG Then
   Stop
#Else
   ' Don't stop
#End If
```

Eine weitere Alternative besteht darin, eine <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>-Anweisung anstelle der Stop-Anweisung zu verwenden. Eine <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>-Anweisung unterbricht die Ausführung nur, wenn eine angegebene Bedingung nicht erfüllt wird. <xref:System.Diagnostics.Debug.Assert%2A>-Anweisungen werden automatisch entfernt, wenn Sie eine Releaseversion erstellen. Weitere Informationen finden Sie unter [Assertionen in verwaltetem Code](assertions-in-managed-code.md). Wenn Sie eine <xref:System.Diagnostics.Debug.Assert%2A>-Anweisung benötigen, durch die die Ausführung in der Debugversion immer unterbrochen wird, verfahren Sie wie folgt:

```csharp
Debug.Assert(false);
```

```vb
Debug.Assert(False)
```

Eine weitere Alternative ist die Verwendung der <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>-Methode:

```csharp
Debug.Fail("a clever output string goes here");
```

```vb
Debug.Fail("a clever output string goes here")
```

## <a name="see-also"></a>Siehe auch

- [Debuggersicherheit](debugger-security.md)
- [C#-, F#- und Visual Basic-Projekttypen](debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Debuggen von verwaltetem Code](debugging-managed-code.md)
