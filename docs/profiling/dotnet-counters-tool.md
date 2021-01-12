---
title: Visualisieren von DotNet-Leistungsindikatoren | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie das .NET-Leistungsindikatortool im Leistungs-Profiler von Visual Studio verwenden.
ms.date: 12/7/2020
ms.topic: conceptual
helpviewer_keywords:
- dotnet, counters, profiling
author: sagar-shetty
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 7a09cc073b2886ab0d374bccaf8b85f3bb729dd7
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97905066"
---
# <a name="visualize-dotnet-counters-from-the-visual-studio-profiler"></a>Visualisieren von DotNet-Leistungsindikatoren vom Leistungs-Profiler von Visual Studio


Mithilfe des .NET-Leistungsindikatortools können Sie [DotNet-Leistungsindikatoren](/dotnet/core/diagnostics/dotnet-counters) im Zeitverlauf direkt im Leistungs-Profiler von Visual Studio visualisieren.


> [!NOTE]
> Das .NET-Leistungsindikatortool erfordert Version 16.7 oder höher von Visual Studio 2019 und ist für .NET Core 3.0 und höher vorgesehen.

## <a name="setup"></a>Einrichten

1. Öffnen Sie den Leistungs-Profiler in Visual Studio (**ALT + F2** oder **Debuggen > Leistungs-Profiler**).

2. Aktivieren Sie das Kontrollkästchen **.NET-Leistungsindikatoren**.

   :::image type="content" source="../profiling/media/dotnet-counters-tool-selected.png" alt-text="Aktiviertes Leistungsindikatortool":::

3. Klicken Sie auf die Schaltfläche **Start**, um das Tool auszuführen.

Weitere Informationen zur Optimierung der Toolleistung finden Sie unter [Optimieren der Profiler-Einstellungen](../profiling/optimize-profiler-settings.md).


## <a name="understand-your-data"></a>Verstehen Ihrer Daten

Während das Tool anfänglich Daten sammelt, werden Ihnen Echtzeitwerte für die [DotNet-Leistungsindikatoren](/dotnet/core/diagnostics/dotnet-counters) angezeigt.

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text="Erfassung des .NET-Leistungsindikatortools":::

Sie können auch Graphen für die Leistungsindikatoren anzeigen, indem Sie das Kontrollkästchen neben den jeweiligen Leistungsindikatornamen aktivieren. Sie können Graphen für mehrere Leistungsindikatoren gleichzeitig anzeigen.


Sobald Sie mit der Ausführung Ihrer App und der Sammlung von Daten fertig sind, können Sie die Sammlung beenden, um einen ausführlicheren Bericht zu erhalten. Klicken Sie hierzu auf **Sammlung beenden**.


Sobald der Bericht geladen wurde, sollte Ihnen ähnlich wie unten gezeigt ein fertiggestellter Bericht angezeigt werden.

:::image type="content" source="../profiling/media/dotnet-counters-tool-report.png" alt-text="Bericht des .NET-Leistungsindikatortools":::

Der Bericht enthält die folgenden Werte:

- Min: Hierbei handelt es sich um den Mindestwert für den Leistungsindikator im ausgewählten Zeitbereich.
- Max: Hierbei handelt es sich um den Höchstwert für den Leistungsindikator im ausgewählten Zeitbereich.
- Durchschnitt: Hierbei handelt es sich um den Durchschnittswert für den Leistungsindikator im ausgewählten Zeitbereich.

Sie können die Tabelle filtern oder Spalten hinzufügen, indem Sie mit der rechten Maustaste auf die Spaltenüberschriften klicken und eine Überschrift angeben.

:::image type="content" source="../profiling/media/dotnet-counters-tool-columns.png" alt-text="Spalten des .NET-Leistungsindikatortools":::

Sie können Graphen auch im ausführlichen Bericht anzeigen, indem Sie die Kontrollkästchen neben den Leistungsindikatoren aktivieren. Die Daten in den Tabellen repräsentieren standardmäßig die Werte des gesamten Zeitraums der erfassten Überwachung. Zum Filtern der Daten nach einem spezifischen Zeitraum können Sie auf die Graphen klicken und diese ziehen.

:::image type="content" source="../profiling/media/dotnet-counters-tool-time-filtering.png" alt-text="Zeitfilterung des .NET-Leistungsindikatortools":::

Die Tabelle wird mit relevanten Werten für den in den Graphen ausgewählten Zeitraum aktualisiert. Verwenden Sie die Schaltfläche **Auswahl löschen**, um den ausgewählten Zeitbereich auf die gesamte Überwachung zurückzusetzen.


## <a name="see-also"></a>Siehe auch

- [Optimieren der Profilereinstellungen](../profiling/optimize-profiler-settings.md)
- [DotNet-Leistungsindikatoren](/dotnet/core/diagnostics/dotnet-counters)
