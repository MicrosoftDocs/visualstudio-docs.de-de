---
title: Debuggen von Zugriffsverletzungen beim Ausführen der App außerhalb von Visual Studio
titleSuffix: ''
description: Verwenden des Just-in-Time-Debuggers zum Debuggen einer Zugriffsverletzung, die außerhalb der Visual Studio-Umgebung auftritt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dd4709807b176806d8a7ca56de4adda8cdfe13ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904323"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Wie können Zugriffsverletzungen, die beim Ausführen des Programms außerhalb des Debuggers auftreten, gedebuggt werden?

## <a name="problem-description"></a>Problembeschreibung
 Das Programm läuft in der Visual Studio-Umgebung einwandfrei. Wird es jedoch eigenständig unter dem Windows-Betriebssystem ausgeführt, generiert es eine Zugriffsverletzung. Wie kann dieses Problem behoben werden?

## <a name="solution"></a>Lösung
 Legen Sie die Option für das [Just-In-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md) fest, und führen Sie das Programm im eigenständigen Modus aus, bis eine Zugriffsverletzung auftritt. Dann können Sie im Dialogfeld **Zugriffsverletzung** auf **Abbrechen** klicken, um den Debugger zu starten.

## <a name="see-also"></a>Siehe auch
- [FAQs zum Debuggen von nativem Code](../debugger/debugging-native-code-faqs.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)