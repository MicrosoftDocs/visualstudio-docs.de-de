---
title: Sammeln von Samplingdaten auf Zeilenebene | Microsoft-Dokumentation
description: Hier erfahren Sie, wie das Sampling auf Zeilenebene des Profilers Code offenlegen kann, der viel Prozessorzeit in Anspruch nimmt. Dies funktioniert sowohl mit verwaltetem als auch mit nativem Code.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 222ba8cd5eb8e45be368d70c204a7c7c76b1a3e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886261"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Vorgehensweise: Sammeln von Samplingdaten auf Zeilenebene
Sampling auf Zeilenebene ermöglicht es dem Profiler zu bestimmen, wo eine prozessorintensive Funktion im Code ist, z.B. eine Funktion mit äußerst exklusiven Stichproben, die vom Prozessor die meiste Zeit beanspruchen.

## <a name="overview"></a>Übersicht
 Für das Sampling auf Zeilenebene, durchläuft der Profiler die Aufrufliste des Programms in festgelegten Intervallen und aggregiert diese Ergebnisse. Diese Ergebnisse zeigen, welche Anweisungen vom Prozessor ausgeführt wurde, als die Stichproben entnommen wurden. Die gesammelten Daten über exklusive Stichproben werden anschließend analysiert, um die Codezeile und den Anweisungszeiger (IP) zu identifizieren.

 Sampling auf Zeilenebene funktioniert sowohl für verwalteten als auch nativen Code. Leistungsberichte, die diese Daten anzeigen, enthalten die Zeilen- und Modulansicht.

 Begin/End-Zeicheninformationen sind nicht für nativen Code verfügbar. Für mehrzeilige Anweisungen sind Zeilenanfangsinformationen für nativen Code nicht verfügbar. Nur Zeilenendeinformationen sind verfügbar.

### <a name="available-data"></a>Verfügbare Daten
 Verfügbare Samplingdaten auf Zeilenebene umfassen die folgenden Informationen:

- Funktionsname

- Funktionsadresse

- Zeilenanfang: Zeilennummer des Samplingcodes.

- Zeilenende: Endquellzeilennummer. Dies ist normalerweise identisch mit den Daten „Line begin“, außer ein einzelner Programmauszug umfasst mehrere Quellcodezeilen.

- Zeichenanfang: Anfangsspalte der aggregierten Stichprobe. Dies ist normalerweise 0, außer eine einzelne Zeile enthält mehrere Programmauszüge.

- Zeilenende: Endspalte der aggregierten Stichprobe.

- IP: Adresse, von der die aggregierte Stichprobe (nur IP-Ansicht) erfasst wurde.

  Wenn eine Funktion über Statistiken auf Zeilenebene in der Ansicht **Module** verfügt, schachteln sich die Statistiken unter jeder Funktion ein. Darüber hinaus werden Statistiken auf IP-Ebene angezeigt, die unter jeder Zeile geschachtelt werden.

### <a name="turn-off-line-level-sampling-for-managed-code"></a>Deaktivieren des Samplings auf Zeilenebene für verwalteten Code
 Sampling auf Zeilenebene ist standardmäßig aktiviert. Sie können die Datensammlung auf Zeilenebene für verwalteten Code deaktivieren, indem Sie einen der folgenden Befehle verwenden:

- Bevor Sie ein Profil erstellen, geben Sie **VSPerfCLREnv /samplelineoff** ein. Dies wirkt sich auf Anwendungen und Dienste aus.

     \- oder -

- Geben Sie beim Starten einer Anwendung **VSPerfCmd /lineoff \<other arguments>** ein.

## <a name="see-also"></a>Siehe auch
- [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
- [Analysieren der durch Leistungstools erstellten Daten](../profiling/analyzing-performance-tools-data.md)
