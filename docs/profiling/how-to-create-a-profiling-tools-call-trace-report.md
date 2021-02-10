---
title: Erstellen eines Aufrufablaufverfolgungsberichts für Profilerstellungstools | Microsoft-Dokumentation
description: Erstellen Sie einen Aufrufnachverfolgungsbericht für die Leistungstools, um Informationen zum Timing für Ihre Funktionen und von Ihren Funktionen aufgerufene Funktionen anzuzeigen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 12d294202c3cea2c19f4f88ca4e7bd1dfd62df67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860827"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Vorgehensweise: Erstellen eines Aufrufablaufverfolgungsberichts für Profilerstellungstools
Im *Aufrufablaufverfolgungsbericht* für die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools werden Zeitsteuerungsinformationen für jeden Einstiegs- und Endpunkt der Funktionen Ihrer Anwendung sowie jeder Aufruf anderer Funktionen durch die Funktion aufgeführt. Aufrufablaufverfolgungsberichte sind nur für Profilerstellungsdaten verfügbar, wenn diese mit der Instrumentationsmethode gesammelt wurden.

> [!NOTE]
> Sie können keine Aufrufablaufverfolgungsberichte in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] anzeigen. Sie müssen das Befehlszeilentool **VSPerfReport** verwenden, um einen durch Trennzeichen getrennten Wert (.*csv*) oder eine *XML*-Datei zu generieren. Weitere Informationen zu diesem Tool finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>So erstellen Sie einen Aufrufablaufverfolgungsbericht

1. Öffnen Sie ein **Eingabeaufforderungsfenster**.

2. Geben Sie an der Eingabeaufforderung folgenden Befehl ein:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**

    |Element|Beschreibung|
    |-|-|
    |*ToolsPath*|Der Pfad zu den Befehlszeilentools der Profilerstellungstools. Weitere Informationen finden Sie unter [Angeben des Pfads für Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Die Datendatei für die Profilerstellung (.*vsp* oder .*vsps*). Es werden vollständige und partielle Pfade angenommen.|
    |Xml|Generiert einen Bericht im XML-Format.|

## <a name="see-also"></a>Siehe auch
- [How to: Sammeln von Daten der Ereignisablaufverfolgung für Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [APIs für Profilerstellungstools](../profiling/profiling-tools-apis.md)
