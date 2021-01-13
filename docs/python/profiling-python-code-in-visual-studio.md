---
title: Messen der Leistung von Python-Code
description: Verwenden der Visual Studio-Profilerstellung zum Überprüfen der Leistung von Python-Code beim Einsatz von auf CPython basierenden Interpretern
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6e6a37301477b43063169143456fc21a3c783968
ms.sourcegitcommit: 4976419fae731860295dbcd072e6778832f7255d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2021
ms.locfileid: "97917922"
---
# <a name="profile-python-code"></a>Profilerstellung für Python-Code

Sie können eine Python-Anwendung unter Verwendung von CPython-basierten Interpreten profilen. (Weitere Informationen zur Verfügbarkeit dieses Features für die verschiedenen Visual Studio-Versionen finden Sie unter [Featurematrix: Profilerstellung](overview-of-python-tools-for-visual-studio.md#matrix-profiling).)

## <a name="profiling-for-cpython-based-interpreters"></a>Profilerstellung für CPython-basierte Interpreter

Die Profilerstellung wird mit dem Menübefehl **Debuggen** > **Python-Profilerstellung starten** gestartet, worauf ein Konfigurationsdialogfeld geöffnet wird:

![Konfigurationsdialogfeld für Profilerstellung](media/profiling-start.png)

Wenn Sie die Option **OK** wählen, wird der Profiler ausgeführt und öffnet einen Leistungsbericht, anhand dessen Sie den Zeitaufwand in der Anwendung untersuchen können:

![Leistungsbericht für Profilerstellung](media/profiling-results.png)

> [!Note]
> Wenn Sie die Profilerstellung für eine Python-Anwendung durchführen, werden von Visual Studio während der gesamten Lebensdauer des Prozesses Daten gesammelt. Derzeit ist es nicht möglich, die Profilerstellung anzuhalten. Wir würden uns über Ihr Feedback zu zukünftigen Funktionen freuen. Verwenden Sie unten auf dieser Seite die Schaltfläche **Produktfeedback**.

## <a name="profiling-for-ironpython"></a>Profilerstellung für IronPython

Da IronPython kein CPython-basierter Interpreter ist, funktioniert die oben genannte Profilerstellungsfunktion nicht.

Verwenden Sie stattdessen den Visual Studio .NET-Profiler, indem Sie *ipy.exe* direkt als Zielanwendung starten und die entsprechenden Argumente zum Starten Ihres Startskripts verwenden. Beziehen Sie `-X:Debug` in die Befehlszeile ein, um sicherzustellen, dass für Ihren gesamten Python-Code Debugging und Profilerstellung durchgeführt werden kann. Dieses Argument generiert einen Leistungsbericht einschließlich der sowohl in der IronPython-Laufzeit als auch Ihrem Code aufgewendeten Zeit. Ihr Code wird anhand beschädigter Namen identifiziert.

Alternativ verfügt IronPython über eigene integrierte Profilerstellungsmethoden, wofür es derzeit aber keine gute Schnellansicht gibt. Unter [An IronPython-Profiler](/archive/blogs/curth/an-ironpython-profiler) (Ein IronPython-Profiler) (MSDN-Blogs) erfahren Sie, was verfügbar ist.