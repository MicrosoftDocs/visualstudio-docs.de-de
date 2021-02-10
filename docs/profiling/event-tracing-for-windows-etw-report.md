---
title: Bericht der Ereignisablaufverfolgung für Windows (ETW) | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über den ETW-Bericht (Event Tracing for Windows, Ereignisablaufverfolgung für Windows), in dem die ETW-Ereignisse aufgeführt sind, die in einer Leistungssitzung der Visual Studio Profilerstellungstools erfasst wurden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1a5a962ba3eaeee2c9f1e26132bf4ce6b12d9347
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955293"
---
# <a name="event-tracing-for-windows-etw-report"></a>Bericht der Ereignisablaufverfolgung für Windows (ETW)
In dem Bericht „Ereignisablaufverfolgung für Windows (ETW)“ werden die ETW-Ereignisse aufgeführt, die in einer Leistungssitzung für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools aufgezeichnet wurden. ETW-Daten werden in einer Binärdatei (*ETL*) erfasst.

> [!NOTE]
> ETW-Berichte werden in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Schnittstellen nicht angezeigt.

- Weitere Informationen zum Erfassen der ETW über die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Schnittstelle mithilfe von Profilerstellungstools finden Sie unter [Vorgehensweise: Erfassen von Daten der Ereignisablaufverfolgung für Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Weitere Informationen zum Erfassen von ETW-Daten über die Befehlszeilentools [VSPerfCmd](../profiling/vsperfcmd.md) finden Sie unter [Events (Ereignisse)](../profiling/events-vsperfcmd.md).

- Der ETW-Bericht wird über den Befehl **VSReport/Summary:ETW** erstellt. Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).

|Spalte|Beschreibung|
|------------|-----------------|
|**Timestamp**|Gibt an, wann das Ereignis aufgetreten ist|
|**Prozess-ID**|Gibt den Prozess an, der das Ereignis generiert hat|
|**Thread-ID**|Gibt den Thread an, der das Ereignis generiert hat|
|**Beschreibung**|Gibt den Ereignisanbieter an|
|**Type**|Gibt den Ereignistyp an|
|**Eigenschaften**|Eigenschaften des Ereignisses Jedes Ereignis besteht aus einem durch Kommas abgetrennten Name/Wert-Paar in Klammern.|
