---
title: Konfigurieren von Leistungssitzungen | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie die Visual Studio Profilerstellungstools so konfigurieren, dass sie die gewünschten Leistungsdaten erfassen. In diesem Artikel sind die allgemeinen Aufgaben sowie Links enthalten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 52e2575e034dbabe5e380857edd95e4bc46f56d2
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721020"
---
# <a name="configure-performance-sessions"></a>Konfigurieren von Leistungssitzungen
Mithilfe von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profilerstellungstools können Sie eine Vielzahl von Leistungsdaten für eine große Anzahl von Anwendungstypen sammeln. In diesem Abschnitt erfahren Sie, wie Sie mit dem Leistungs-Assistenten und den Eigenschaften der Leistungssitzung sowie der Zielbinärdatei die Profilerstellungstools für das Sammeln von für Sie interessanten Daten konfigurieren. Die Konfigurationseigenschaften von Profilerstellungstools lassen sich außerdem dazu verwenden, um zu steuern, wie viele Daten während einer Profilerstellung gesammelt werden. Weitere Informationen finden Sie unter [Control data collection (Steuern der Datensammlung)](../profiling/controlling-data-collection.md).

> [!NOTE]
> In vielen Fällen können Sie mithilfe der Standardeigenschaften des Leistungsassistenten das Sammeln von Profilerstellungsdaten effizient steuern. Weitere Informationen finden Sie unter [Einführung in die Leistungsprofilerstellung](../profiling/beginners-guide-to-performance-profiling.md) und [Erste Schritte](../profiling/getting-started-with-performance-tools.md).

## <a name="common-tasks"></a>Allgemeine Aufgaben

| Aufgabe | Verwandte Inhalte |
| - | - |
| **Festlegen der grundlegenden Profilerstellungsoptionen:** Konfigurieren Sie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], um den Microsoft-Symbolserver zu verwenden. So stellen Sie sicher, dass Sie für die aktuelle Version von Windows und für andere Microsoft-Anwendungen Zugriff auf Symbole wie Funktions- und Parameternamen haben. Sie können auch andere allgemeinen Optionen angeben, bevor Sie mit einer Profilerstellungssitzung beginnen, wie z.B. Systemberechtigungen für die Profilerstellungstools und die Namen von Profilerstellungs-Datendateien. | -   [Vorgehensweise: Verweisen auf Windows-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Vorgehensweise: Serialisieren von Symbolinformationen](../profiling/how-to-serialize-symbol-information.md)<br />-   [Vorgehensweise: Festlegen der aktuellen Sitzung](../profiling/how-to-set-the-current-session.md)<br />-   [Vorgehensweise: Festlegen von Berechtigungen](../profiling/how-to-set-permissions.md)<br />-   [Vorgehensweise: Dateinamensoptionen für Profilerstellungsdaten](../profiling/how-to-set-performance-data-file-name-options.md) |
| **Festlegen der zu erfassenden Daten:** Die Prozeduren zur Konfigurierung einer Profilerstellungssitzung sind abhängig vom Typ der Zielanwendung, für die Sie ein Profil erstellen möchten, sowie vom Typ der Leistungsdaten, die Sie sammeln möchten. | -   [Vorgehensweise: Auswählen von Sammlungsmethoden](../profiling/how-to-choose-collection-methods.md)<br />-   [Sammeln von Leistungsstatistiken durch Sampling](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Sammeln von Daten zur .NET-Speicherbelegung und -lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Vorgehensweise: Profilerstellung für JavaScript-Code in Webseiten](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Sammeln von Parallelitätsdaten zu Threads und Prozessen](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Sammeln zusätzlicher Leistungsdaten](../profiling/collecting-additional-performance-data.md) |
| **Festlegen von erweiterten Konfigurationsoptionen:** Wenn Sie das Profil von .NET Framework-Anwendungen anlegen, die mehrere CLR-Versionen laden, können Sie angeben, für welche Version Sie das Profil anlegen möchten. Wenn Ihre Leistungssitzung mehrere EXE-Dateien umfasst, können Sie die Startreihenfolge der Binärdateien festlegen. | -   [Vorgehensweise: Angeben der .NET Framework-Laufzeit](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Vorgehensweise: Angeben der zu startenden Binärdatei](../profiling/how-to-specify-the-binary-to-start.md) |

## <a name="related-sections"></a>Verwandte Abschnitte
- [Steuerung der Datensammlung](../profiling/controlling-data-collection.md)

## <a name="see-also"></a>Siehe auch
- [Leistungs-Explorer](../profiling/performance-explorer.md)
