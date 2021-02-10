---
title: Wechseln zu einem anderen Thread während des Debuggens
description: In diesem Artikel finden Sie verschiedene Methoden zum Wechseln zu anderen Threads beim Debuggen einer Multithreadanwendung in Visual Studio.
ms.custom: SEO-VS-2020, seodec18
ms.date: 04/27/2017
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: affc4dec196169580ff23c5faf2f7876a71fbba9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896522"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Vorgehensweise: Wechseln zu einem anderen Thread während des Debuggens in Visual Studio (C#, Visual Basic, C++)
Beim Debuggen einer Multithreadanwendung können Sie verschiedene Methoden verwenden, um vom bearbeiteten Thread zu einem anderen Thread zu wechseln.

> [!NOTE]
> Wenn Sie die Reihenfolge steuern möchten, in der die Threads ausgeführt werden, müssen Sie die Threads [einfrieren und reaktivieren](../debugger/get-started-debugging-multithreaded-apps.md).

Wenn Sie Threads im Code-Editor und unterschiedlichen Multithreaddebugfenstern untersuchen, zeigt der gelbe Pfeil den aktuellen Thread an. Ein grüner Pfeil in Wellenform zeigt an, dass ein nicht aktueller Thread über den aktuellen Debuggerkontext verfügt.

### <a name="to-switch-to-any-thread-that-appears"></a>Wechseln zu einem angezeigten Thread

- Doppelklicken Sie im Fenster **Threads** oder **Parallele Überwachung** auf den Thread.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>So wechseln Sie zu einem Thread in einem Quellcodefenster

- Klicken Sie im linken Bundsteg mit der rechten Maustaste auf das Threadmarkersymbol (![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker")), zeigen Sie auf **Wechseln zu**, und klicken Sie dann auf den Namen des Threads, zu dem gewechselt werden soll. Im Kontextmenü werden nur die Threads an dieser bestimmten Position angezeigt.

     Wenn keine Threadmarker angezeigt werden, klicken Sie mit der rechten Maustaste in das Fenster **Threads**, und überprüfen Sie, ob **Threads in Quelle anzeigen** ausgewählt ist.

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>So wechseln Sie über die Symbolleiste Debugspeicherort zu einem Thread

1. Klicken Sie auf der Symbolleiste **Debugspeicherort** auf die Liste **Thread**.

2. Klicken Sie in der Liste auf den Thread, zu dem Sie wechseln möchten.

## <a name="see-also"></a>Siehe auch
- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
