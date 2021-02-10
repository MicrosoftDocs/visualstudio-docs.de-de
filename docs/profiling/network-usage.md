---
title: Analysieren der Netzwerkauslastung in UWP-Apps
description: In diesem Artikel erhalten Sie Informationen zum Diagnosetool „Netzwerk“ von Visual Studio. Dieses erfasst mithilfe der Windows.Web.Http-API Daten zu Netzwerkvorgängen.
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: c09b50a4f7089367a82a54f285cb4bf401360b03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964718"
---
# <a name="analyze-network-usage-in-uwp-apps"></a>Analysieren der Netzwerkauslastung in UWP-Apps
Das Diagnosetool **Netzwerk** von Visual Studio erfasst mithilfe der [Windows.Web.Http-API](/uwp/api/windows.web.http) Daten zu Netzwerkoperationen. Durch Analysieren der Daten können Sie Probleme wie Zugriffs- und Authentifizierungsprobleme, falsche Cacheverwendung und schlechte Anzeige- und Downloadleistung in den Griff bekommen.

 Das Netzwerktool unterstützt nur UWP-Apps. Andere Plattformen werden derzeit nicht unterstützt.

> [!NOTE]
> Detailliertere Informationen zum Netzwerk-Tool finden Sie unter [Introducing Visual Studio’s network tool (Einführung in das Netzwerk-Tool von Visual Studio)](https://devblogs.microsoft.com/visualstudio/introducing-visual-studios-network-tool/).

## <a name="collect-network-tool-data"></a>Sammeln von Netzwerktooldaten
 Sie sollten das Tool **Netzwerk** mit einem geöffneten Visual Studio-Projekt auf dem Computer mit Visual Studio ausführen.

1. Öffnen Sie das Projekt in Visual Studio.

2. Wählen Sie im Menü die Option **Debug / Performance Profiler** (Debuggen / Leistungsprofiler) aus. Wählen Sie **Netzwerk** aus, und klicken Sie anschließend auf **Starten**.

3. Das Netzwerktool beginnt mit dem Erfassen des HTTP-Datenverkehrs Ihrer App.

    Während der Ausführung der App zeigt die Zusammenfassungsansicht im linken Bereich automatisch eine Liste der erfassten HTTP-Vorgänge an. Wählen Sie ein Element in der Zusammenfassungsansicht aus, um weitere Informationen im Detailbereich rechts anzuzeigen.

4. Klicken Sie auf **Beenden**, um die App zu schließen.

   Das Berichtsfenster sollte in etwa wie folgt aussehen:

   ![Fenster „Netzwerk“](../profiling/media/network_fullwindow.png "NETWORK_FullWindow")

## <a name="analyze-data"></a>Analysieren von Daten
 Sie können erfassten HTTP-Datenverkehr analysieren, während die App ausgeführt wird oder nachdem sie geschlossen wurde. Wählen Sie dazu einen der in der Zusammenfassungsansicht angezeigten Netzwerkvorgänge aus.

 Die Zusammenfassungsansicht **Netzwerk** zeigt die Daten der einzelnen ausgeführten Netzwerkoperationen Ihrer App an. Wählen Sie eine Spaltenüberschrift aus, um die Liste zu sortieren, oder wählen Sie die Inhaltstypen aus, die in der Filteransicht **Inhaltstyp** angezeigt werden sollen.

 Wählen Sie **Als HAR speichern** aus, um eine JSON-Datei zu erstellen, die von Drittanbietertools wie Fiddler genutzt werden kann.

 Die Detailansicht **Netzwerk** enthält weitere Informationen zu den einzelnen in der Zusammenfassungsansicht angezeigten Netzwerkoperationen.

 ![Detailbereich des Netzwerktools](../profiling/media/network_detailsviewpane.png "NETWORK_DetailsViewPane")

|name|Beschreibung|
|-|-|
|**Header**|Informationen zu den Anforderungsheadern des Ereignisses.|
|**Text**|Die Nutzlastdaten von Anforderung und Antwort.|
|**Parameter**|Die Parameternamen und Werte der Abfragezeichenfolge.|
|**Cookies**|Cookiedaten von Antwort und Anforderung.|
|**Zeiten**|Ein Diagramm der Phasen beim Abrufen der ausgewählten Ressourcen.|

 Die **Zusammenfassungsleiste** in der Ansicht „Netzwerk“ zeigt die jeweils angezeigte Anzahl von Netzwerkoperationen, die Menge der übertragenen Daten, die für das Herunterladen der Daten aufgewendete Zeit und die Anzahl von sichtbaren Fehlern (Anforderungen mit Antworten „4xx“ oder „5xx“).

### <a name="analysis-tips"></a>Tipps für die Analyse
 Dieses Tool hebt bestimmte Bereiche hervor, die bei der Ausführung von netzwerkbezogenen Analysen nützlich sein können:

1. Anforderungen, die vollständig aus dem Cache bedient werden, werden in der Spalte **Empfangen** als **(aus Cache)** angezeigt. Dies kann dabei helfen, herauszufinden, ob der Cache effektiv genutzt und damit Bandbreite für die Benutzer gespart wird, oder ob versehentlich überflüssige Antworten zwischengespeichert und den Endbenutzern Ihrer Anwendung veraltete Daten bereitgestellt werden.

2. Fehlerantworten (4xx oder 5xx) werden mit einem roten Statuscode in der Spalte **Ergebnisse** angezeigt und auch in der Zusammenfassungsleiste hervorgehoben. So lassen sich unter den vielen potenziellen Anforderungen Ihrer Anwendung Fehler ganz einfach erkennen.

3. Die Schaltfläche für eine automatische Strukturierung und Einrückung (auf der Registerkarte mit dem Haupttext) kann Ihnen helfen, auf JSON-, XML-, HTML-, CSS-, JavaScript- und TypeScript-Antworten zu reagieren, indem Sie Lesbarkeit des Inhalts erhöhen.

## <a name="see-also"></a>Siehe auch

- [Ausführen von Profilerstellungstools mit oder ohne den Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Visual Studio-Blog: Introducing Visual Studio's network inspector (Visual Studi-Blog: Einführung in die Netzwerkinspektion von Visual Studio)](https://devblogs.microsoft.com/visualstudio/)
- [Channel 9-Video: VS Diagnostics tools – New Network Profiler (Channel-9-Video: Diagnosetools von Visual Studio – Neuer Profiler „Netzwerk“)](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
- [Profilerstellung in Visual Studio](../profiling/index.yml)
- [Einführung in Profilerstellungstools](../profiling/profiling-feature-tour.md)