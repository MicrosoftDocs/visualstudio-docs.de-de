---
title: Was bedeutet „Debuggen“?
description: Hier erfahren Sie, was es bedeutet, eine App zu debuggen.
ms.custom: debug-experiment
ms.date: 10/17/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3435b7a270d89dc38f5ff10a1350418a24f91c0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883934"
---
# <a name="what-is-debugging"></a>Was bedeutet „Debuggen“?

Der Visual Studio-Debugger ist ein praktisches Tool. Bevor wir Ihnen zeigen, wie Sie ihn verwenden, möchten wir zunächst auf einige Begriffe wie *Debugger*, *Debuggen* und *Debugmodus* eingehen. So haben wir später eine gemeinsame Basis, wenn wir uns mit der Fehlersuche und -behebung beschäftigen.

## <a name="debugger-vs-debugging"></a>Gegenüberstellung von „Debugger“ und „Debuggen“

Der Begriff *Debuggen* kann viele verschiedene Bedeutungen haben. Wortwörtlich bezeichnet Debuggen jedoch das Entfernen von Fehlern (Bugs) aus Ihrem Code. Dies kann auf unterschiedliche Weise erreicht werden. So können Sie zum Debuggen beispielsweise Ihren Code auf Tippfehler untersuchen oder eine Codeanalyse verwenden. Sie können Ihren Code aber auch mithilfe eines Leistungs-Profilers debuggen. Oder Sie verwenden einen *Debugger*.

Ein Debugger ist hoch spezialisiertes Entwicklertool, das an Ihre laufende App angefügt wird und es Ihnen ermöglicht, den Code zu untersuchen. Das ist in der Regel gemeint, wenn in der Dokumentation zum Debuggen für Visual Studio von „Debuggen“ die Rede ist.

## <a name="debug-mode-vs-running-your-app"></a>Gegenüberstellung von Debugmodus und App-Ausführung

Wenn Sie Ihre App in Visual Studio zum ersten Mal ausführen, können Sie sie starten, indem Sie auf der Symbolleiste auf die grüne Pfeilschaltfläche ![Debuggen starten](../debugger/media/dbg-tour-start-debugging.png "Debugging starten") auf der Symbolleiste klicken (oder **F5** drücken). In der Dropdownliste links davon ist standardmäßig der Wert **Debuggen** angegeben. Wenn Sie noch nicht mit Visual Studio vertraut sind, entsteht unter Umständen der Eindruck, dass das Debuggen Ihrer App mit der App-Ausführung zusammenhängt. Das stimmt zwar, trotzdem handelt es sich hierbei um zwei grundlegend verschieden Aufgaben.

![Auswählen eines Debugbuilds](../debugger/media/what-is-debugging-debug-build.png)

Der Wert **Debuggen** gibt an, dass eine Debugkonfiguration verwendet wird. Wenn Sie die App in einer Debugkonfiguration starten (durch Klicken auf den grünen Pfeil oder durch Drücken von **F5**), wird die App im *Debugmodus* gestartet. Das bedeutet, dass die App mit einem angefügten Debugger ausgeführt wird. Dadurch stehen Ihnen umfassende Debugfeatures zur Verfügung, die Sie bei der Suche nach Fehlern in Ihrer App unterstützen.

Wählen Sie bei geöffnetem Projekt die mit **Debuggen** beschriftete Dropdownauswahl und anschließend die Option **Release** aus.

![Auswählen eines Releasebuilds](../debugger/media/what-is-debugging-release-build.png)

Wenn Sie diese Einstellung ändern, wird für Ihr Projekt anstelle einer Debugkonfiguration eine Releasekonfiguration verwendet. Visual Studio-Projekte verfügen über separate Release- und Debugkonfigurationen für Ihr Programm. Die Debugversion wird zum Debuggen und die Releaseversion für das endgültige Release verwendet. Ein Releasebuild ist leistungsoptimiert, während der Debugbuild besser zum Debuggen geeignet ist.

## <a name="when-to-use-a-debugger"></a>Verwendung eines Debuggers

Der Debugger ist ein unentbehrliches Tool für die Fehlersuche und -behebung in Ihren Apps. Es hängt jedoch alles vom Kontext ab, und es ist wichtig, alle zur Verfügung stehenden Hilfsmittel zu nutzen, um Fehler möglichst schnell zu beseitigen. Manchmal bedarf es hierzu unter Umständen einer besseren Programmierung. Wenn Sie lernen, wann Sie den Debugger und wann besser ein anderes Tool verwenden, können Sie den Debugger auch effektiver einsetzen.

## <a name="next-steps"></a>Nächste Schritte

In diesem Artikel haben Sie einige grundlegende Konzepte für das Debuggen kennengelernt. Als Nächstes können Sie sich mit dem Debuggen mit Visual Studio vertraut machen und sich darüber informieren, wie Sie Fehler beim Programmieren vermeiden. Die folgenden Artikel enthalten zwar Codebeispiele in C#, die Konzepte gelten jedoch für alle von Visual Studio unterstützten Sprachen.

> [!div class="nextstepaction"]
> [Debuggen für Einsteiger](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [Debugging techniques and tools (Debugverfahren und -tools)](../debugger/write-better-code-with-visual-studio.md)
