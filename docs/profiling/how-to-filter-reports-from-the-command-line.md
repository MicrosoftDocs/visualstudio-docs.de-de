---
title: Filtern von Berichten über die Befehlszeile | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1b6408975e8a3d7189db26913f3de75ad1c7c595
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851137"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Vorgehensweise: Filtern von Berichten über die Befehlszeile
Mithilfe von Optionen für den Befehl **VSPerfReport** können Sie Berichte nach einem bestimmten Zeitsegment der Profilerstellungsdatei filtern oder die Daten auf einen oder mehr Prozesse oder Threads beschränken. Weitere Informationen zu diesem Befehl finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).

|Optionen|Beschreibung|
|-------------|-----------------|
|**StartTime:** [*Wert*]|Zeigt nur Daten an, die nach dem Wert erfasst werden (in Millisekunden)|
|**EndTime:** [*Wert*]|Zeigt nur Daten an, die vor dem Wert erfasst werden (in Millisekunden)|
|**FilterFile:** `VSPFFile`|Gibt den Speicherort einer Filterdatei an, die aus dem Visual Studio-Fenster **Leistungsbericht** generiert wurde|
|**MsFilter:** [*Startzeit, Dauer*]|Zeigt nur Daten ab `StartTime` bis zur Länge von `Duration` (in Millisekunden) an|
|**Process:** [*PID*]|Zeigt nur Daten aus dem angegebenen Prozess an|
|**Thread:** [*Thread-ID*]|Zeigt nur Daten aus dem angegebenen Thread an|
|**Thread:** [*Thread-ID, Prozess-ID*]|Zeigt nur Daten aus dem angegebenen Thread an, der dem angegebenen Prozess zugeordnet ist|
