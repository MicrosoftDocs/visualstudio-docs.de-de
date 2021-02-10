---
title: Übersicht über Leistungssitzungen | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie die Leistungstools verwenden, um schneller produktiv arbeiten zu können und die Leistung Ihres Codes zu verbessern.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, performance session
- performance sessions
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8db336c38b330eb0702875b08078c1cac69ea7f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922204"
---
# <a name="performance-session-overview"></a>Übersicht über Leistungssitzungen
In dieser Übersicht werden die Grundlagen der Profilerstellung erläutert. Entwickler, die wenig Erfahrung mit Leistungsarbeit haben, werden lernen, wie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools ihnen helfen, schnell produktiv zu werden und die Leistung ihres Codes zu steigern. Entwickler, die bereits Erfahrung mit der Profilerstellung haben, erhalten eine Übersicht über besondere Features und Vorgänge der Profilerstellungstools.

 Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools helfen Ihnen, Leistungsprobleme im Quellcode zu identifizieren und die Leistung von möglichen Lösungen zu vergleichen. Die Assistenten und Standardeinstellungen für Profierstellungen geben Ihnen unmittelbaren Einblick in viele Leistungsprobleme. Die Features und Optionen des Profilerstellungstools stellen eine exakte Kontrolle über den Profilerstellungsvorgang zur Verfügung. Diese Kontrolle umfasst das präzise Ansteuern von Codeabschnitten, das Erfassen von Zeitinformationen auf Blockebene und die Aufnahme zusätzlicher Prozessor- und Systemleistungsdaten in Ihre Daten.

 Die folgenden Schritte bilden den grundlegenden Vorgang der Verwendung von Profilerstellungstools:

1. Konfigurieren der Leistungssitzung durch Angabe der Auflistungsmethode und der Daten, die Sie sammeln möchten

2. Erfassen von Profildaten durch Ausführen der Anwendung in der Leistungssitzung

3. Analysieren der Daten zur Ermittlung von Leistungsproblemen

4. Ändern des Codes in die integrierte Entwicklungsumgebung (IDE) von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zur Erhöhung der Leistung des Anwendungscodes

5. Erfassen von Profilerstellungsdaten zum geänderten Code, und Vergleichen der Profilerstellungsdaten der ursprünglichen und geänderten Daten

6. Erstellen eines Berichts, der die Leistungszunahme dokumentiert

   Um mit den Informationen zu arbeiten, die durch Profilerstellung bereitgestellt werden, sollten Sie Symbolinformationen für die Binärdateien, für die Sie ein Profil erstellen möchten, und für die Binärdateien der Windows-Betriebssysteme zur Verfügung haben.

## <a name="configure-the-performance-session"></a>Konfigurieren der Leistungssitzung
 Um eine Profilerstellungssitzung zu konfigurieren, wählen Sie die Profilerstellungsmethode aus, die Sie verwenden und die Daten, die Sie sammeln möchten. Die Profilerstellungstools **Leistungsassistent** können Sie durch die grundlegende Konfiguration führen, und Sie können Eigenschaftenseiten der Leistungssitzung verwenden, um weitere Optionen hinzuzufügen:

- Profilerstellungsmethoden enthalten Sampling, Verfolgung und Speicherreservierung.

- Datenwerte umfassen Zeit, Prozessor, Betriebssystemleistungsindikatoren und Anwendungsereignisse wie z.B. Seitenfehler und Kernelübergänge.

  Sie können eine Leistungssitzung in einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projekt als Teil der Projektlösung oder beliebige Binärdateien durch ein Profil der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-IDE konfigurieren. Sie können auf den Eigenschaftenseiten der Leistungssitzung Sitzungseigenschaften angeben oder Sie können den Assistent der Profilerstellungstools verwenden.

## <a name="collect-profiling-data"></a>Sammeln von Profilerstellungsdaten
 Sie starten die Erfassung der Profilerstellungsdaten aus dem **Leistungs-Explorer**. Sie können die Profilerstellung anhalten und fortsetzen, um die Menge der Daten, die Sie erfassen, einzuschränken. Sie können auch einen Prozess anfügen, der bereits ausgeführt wird.

 Sobald die Anwendung gestartet wird, wird das Fenster **Steuerung der Datensammlung** in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-IDE angezeigt. Im Fenster **Steuerung der Datensammlung** können Sie bestimmte Teile Ihrer Anwendung durch Anhalten und Fortsetzen des Sammlungsvorgangs profilieren. Sie können das Fenster **Steuerung der Datensammlung** auch zum Einfügen von Markierungen in die gesammelten Daten nutzen. Markierungen sind benutzerdefinierte Datenpunkte, die in Profilansichten angezeigt, und die verwendet werden können, um Profilerstellungsdaten zu filtern.

 Beim Herunterfahren der Zielanwendung generiert das Profilerstellungstool eine Profilerstellungsdatendatei (*.vsp) und zeigt den Zusammenfassungsbericht in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-IDE an.

## <a name="analyze-the-data-and-identify-performance-issues"></a>Analysieren der Daten und Ermitteln von Leistungsproblemen
 Wenn Sie eine Profilerstellung beenden, werden die Daten analysiert und in den Ansichtsfenstern **Leistungsbericht** der Profilerstellungstools wird eine Zusammenfassung angezeigt. Es werden Profilerstellungsdaten für die Aufrufliste und einzelne Funktionen der Anwendung gesammelt. Berichtansichten zeigen Leistungsanalysen für Datenbereiche der Prozesse, Threads, Module, Funktionen und Quellcodezeilen der Anwendung an. Profilerstellungsdatenwerte für eine Funktion enthalten:

- Die gesamte Zeit in der Funktion und in untergeordneten Funktionen, die von der Funktion (inklusive Werte) aufgerufen wurden

- Die Zeit für die Ausführung des Codes in der Funktion (exklusive Werte)

  Über zwölf verschiedene Ansichten ermöglichen Ihnen die Analyse der Profilerstellungsdaten auf möglichst effiziente Weise. Durch Ansichtsanpassungen können Sie die Daten filtern und sortieren, um die Funktionen zu suchen, die Leistungsprobleme verursachen könnten. Das Filtern des langsamsten Pfads markiert die aktivsten Pfade unmittelbar in der Aufrufstruktur und der Modulansicht.

## <a name="modify-the-application-code"></a>Ändern des Anwendungscodes
 Nachdem Sie eines oder mehrere relevante Leistungsprobleme isoliert haben, können Sie den Code mit der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-IDE ändern, und dann die Profilerstellungsdaten für Ihre Änderungen sammeln.

## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>Erneutes Auflisten von Profilerstellungsdaten und Vergleichen der Daten zwischen den Profilerstellungsvorgängen
 Die Ansicht des Vergleichsberichts der Profilerstellungstools zeigt den Unterschied in Modul-, Funktions- oder Zeilenleistung zwischen zwei ausgewählten Profilerstellungsdatendateien. Sie können die Datenwerte der Profilerstellung angeben, die Sie vergleichen möchten, und Sie können zwischen der Vergleichsansicht und Ansichten der einzelnen Dateien wechseln.

## <a name="generate-a-report-of-the-results"></a>Erstellen eines Berichts mit den Ergebnissen
 Sie können die Zeilen jeder Leistungsberichtansicht in E-Mails und Kalkulationstabellen einfügen, und Sie können Berichte erstellen, die Daten für eine oder mehrere Ansichten enthalten.

## <a name="see-also"></a>Siehe auch
- [Übersichten](../profiling/overviews-performance-tools.md)
- [Exemplarische Vorgehensweise: Identifizieren von Leistungsproblemen](beginners-guide-to-cpu-sampling.md)
