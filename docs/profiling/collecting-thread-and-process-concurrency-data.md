---
title: Sammeln von Parallelitätsdaten zu Threads und Prozessen
description: Verwenden Sie die Nebenläufigkeitsprofilerstellungs-Methode der Profilerstellungstools, um Daten zu jedem Synchronisierungsereignis zu sammeln, das dazu führt, dass eine Funktion auf Ressourcenzugriff wartet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2f5065c3eafc9fb1cd9e36227a09bbf26ed321c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950207"
---
# <a name="collect-thread-and-process-concurrency-data"></a>Sammeln von Parallelitätsdaten zu Threads und Prozessen

Mit der Parallelitätsmethode zur Profilerstellung der Visual Studio-Profilerstellungstools können Sie Ressourcenkonfliktdaten sammeln, die Informationen zu jedem Synchronisierungsereignis enthalten, das dazu führt, dass eine Funktion in der mit einem Profil versehenen Anwendung auf den Zugriff auf eine Ressource warten muss.

Sie können die Parallelitätsmethode zur Profilerstellung mit einem der folgenden Verfahren angeben:

- Klicken Sie auf der ersten Seite des Profilerstellungs-Assistenten auf **Parallelität**.
- Klicken Sie auf der Seite **Allgemein** im Dialogfeld „Eigenschaften“ für die Leistungssitzung auf **Instrumentation**.
- Klicken Sie auf der Symbolleiste **Leistungs-Explorer** in der Liste **Methode** auf **Parallelität**.

## <a name="common-tasks"></a>Allgemeine Aufgaben

Weitere Optionen können Sie im Dialogfeld _Leistungssitzung_**Eigenschaftenseiten** der Leistungssitzung angeben. So öffnen Sie dieses Dialogfeld

- Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf den Namen der Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.

Die Aufgaben in der folgenden Tabelle beschreiben Optionen, die Sie im Dialogfeld _Leistungssitzung_**Eigenschaftenseiten** angeben können, wenn Sie die Profilerstellung mit der Parallelitätsmethode ausführen.

|Aufgabe|Verwandte Inhalte|
|----------|---------------------|
|Geben Sie auf der Seite **Allgemein** Namensdetails für die generierte Profilerstellungs-Datendatei (VSP) an.|- [Vorgehensweise: Dateinamensoptionen für Profilerstellungsdaten](../profiling/how-to-set-performance-data-file-name-options.md)|
|Wenn sich in Ihrer Codelösung mehrere EXE-Projekte befinden, geben Sie auf der Seite **Starten** die zu startende Anwendung an.|- [Vorgehensweise: Angeben der zu startenden Binärdatei](../profiling/how-to-specify-the-binary-to-start.md)|
|Fügen Sie der Profilerstellung auf der Seite **Ebeneninteraktion** ADO.NET-Aufrufdaten hinzu.|- [Erfassen von Ebeneninteraktionsdaten](../profiling/collecting-tier-interaction-data.md)|
|Geben Sie auf der Seite **Windows-Indikatoren** einen oder mehrere Betriebssystem-Leistungsindikatoren an, die den Profilerstellungsdaten als Markierungen hinzugefügt werden sollen.|- [Vorgehensweise: Sammeln von Windows-Indikatordaten](../profiling/how-to-collect-windows-counter-data.md)|
|Geben Sie auf der Seite **Erweitert** die Version der .NET Framework-Laufzeit für die Profilerstellung an, wenn Ihre Anwendungsmodule mehrere Versionen verwenden. Standardmäßig wird die zuerst geladene Version für die Profilerstellung verwendet.|- [Vorgehensweise: Angeben der .NET Framework-Laufzeit](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
