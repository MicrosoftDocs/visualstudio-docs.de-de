---
title: Sammeln von Daten der Ereignisablaufverfolgung für Windows (ETW) | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie mit der Ereignisablaufverfolgung für Windows (Event Tracing for Windows, ETW) ermitteln, wo in der Anwendung Leistungsprobleme auftreten. Hierfür zeigen Sie die Daten mit VSPerfReport.exe an.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 853e27c51b626ef63a7e0924d4c0164a6386cda2
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801554"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Vorgehensweise: Sammeln von Daten der Ereignisablaufverfolgung für Windows (ETW)

Ereignisablaufverfolgung für Windows (ETW) ist eine effiziente Ablaufverfolgungsfunktion auf Kernelebene, mit dem der Profiler kernel- oder anwendungsdefinierte Ereignisse protokollieren kann. Die vom Ereignisanbieter gesammelten Daten können nur mithilfe der Option /**Summary:ETW** des Befehlszeilentools [VSPerfReport](../profiling/vsperfreport.md) angezeigt werden. In diesem Bericht können Sie bestimmen, wo Leistungsprobleme in der Anwendung aufgetreten.

> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>So aktivieren Sie Ereignisablaufverfolgungsanbieter

1. Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie in den **Eigenschaftenseiten** auf die Eigenschaften **Windows-Ereignisse** .

3. Wählen Sie von der Liste **Ereignisablaufverfolgungsanbieter zur Datensammlung auswählen** den gewünschten Ereignisanbieter zur Profilerstellung aus.

## <a name="see-also"></a>Siehe auch

[Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
