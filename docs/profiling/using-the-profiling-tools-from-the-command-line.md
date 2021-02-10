---
title: Verwenden der Profilerstellungstools über die Befehlszeile | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie mithilfe der Befehlszeilentools der Profilerstellungstools in Visual Studio Profile für Anwendungen erstellen und die Profilerstellung mithilfe von Batchdateien und Skripts automatisieren können.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6cfb8f26486c731d3900522d72ac62ff6997005e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885949"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Verwenden der Profilerstellungstools über die Befehlszeile
Mithilfe der Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools können Sie über die Eingabeaufforderung für Anwendungen Profile erstellen und die Profilerstellung mithilfe von Batchdateien und Skripts automatisieren. Darüber hinaus können Sie über eine Eingabeaufforderung auch Berichtsdateien erstellen. Sie können Daten auf Computern, auf denen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nicht installiert ist, mithilfe des einfachen eigenständigen Profilers sammeln.

> [!NOTE]
> Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Informationen hierzu finden Sie unter [Performance Tools on Windows 8 and Windows Server 2012 applications (Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen)](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Allgemeine Aufgaben

| Aufgabe | Verwandte Inhalte |
| - | - |
| **Festlegen des Speicherorts von Symbolen:** Damit die Namen von Funktionen und Parametern angezeigt werden, muss der Profiler Zugriff auf die Symboldateien (*PDB*) der Binärdateien haben, für die eine Profilerstellung durchgeführt wurde. Diese Dateien müssen die Symboldateien für das Microsoft-Betriebssystem und Microsoft-Anwendungen umfassen, die Sie in der Analyse anzeigen möchten. Sie können mithilfe des öffentlichen Microsoft-Symbolservers sicherstellen, dass Sie über die richtigen *PDB-Dateien* für die Microsoft-Binärdateien verfügen. | -   [Vorgehensweise: Angeben von Symboldateispeicherorten über die Befehlszeile](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Profilerstellung für die Anwendung:** Welche Befehlszeilentools und -optionen Sie für die Profilerstellung einer Zielanwendung verwenden, hängt vom Typ der Anwendung, der Profilerstellungsmethode und davon ab, ob das Ziel eine verwaltete oder eine native Anwendung ist. | -   [Verwenden von Profilerstellungsmethoden über die Befehlszeile](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md) |
| **Erstellen von XML- und CSV-Berichten:** Durch die Profilerstellung über die Eingabeaufforderung werden Datendateien erstellt, die auf der Benutzeroberfläche von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] angezeigt werden können. Mit dem Befehlszeilentool „VSPerfReport“ können auch *XML-Dateien* oder *CSV-Dateien* der Daten generiert werden. | -   [Erstellen von Profiler-Berichten über die Befehlszeile](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md) |
| **Profilerstellung von Code auf Computern ohne Visual Studio:** Sie können den eigenständigen Profiler der Profilerstellungstools verwenden, um Daten für Anwendungen auf Computern zu sammeln, auf denen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nicht installiert ist. | -   [Vorgehensweise: Installieren des eigenständigen Profilers](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Verweis
- [Referenz zu Profilerstellungstools für die Befehlszeile](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>Siehe auch
- [Leistungs-Explorer](../profiling/performance-explorer.md)
