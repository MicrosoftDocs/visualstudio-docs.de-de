---
title: WinCounter | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur Option „WinCounter“. Insbesondere erhalten Sie Informationen dazu, dass sie einen Leistungsindikator für Windows oder die Anwendung angibt, um bei der Profilerstellung festgelegte Intervalle zu erfassen.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 595a8003992c92871a8476743288d3072aff63c8
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723048"
---
# <a name="wincounter"></a>WinCounter
Über die Option **WinCounter** wird ein Leistungsindikator für Windows oder die Anwendung angegeben, um bei der Profilerstellung festgelegte Intervalle zu erfassen. Leistungsindikatoren für Windows und die Anwendung werden als Markierungen in den Profilerstellungs-Datendateien aufgeführt. Sie können mehrere Leistungsindikatoren angeben, die in separaten Optionen erfasst werden sollen.

 Standardmäßig werden Leistungsindikatoren alle 500 ms erfasst. Verwenden Sie die Option **AutoMark**, um ein anderes Intervall für die Erfassung festzulegen.

 Es wird nur die Option **AutoMark** verwendet. Wenn mehrere Optionen **AutoMark** angegeben sind, wird nur die letzte verwendet.

 Die Option **WinCounter** kann nur mit der Option **Start** verwendet werden.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]
```

#### <a name="parameters"></a>Parameter
 `Path`: der Windows-Leistungsindikator im PDH-Indikatorpfadformat.

## <a name="required-options"></a>Erforderliche Optionen
 Die Option **WinCounter** kann nur mit der Option **Start** verwendet werden.

 **Start:** `Method`: Die Option **Start** initialisiert den Profiler mit der angegebenen Profilerstellungsmethode.

## <a name="exclusive-options"></a>Ausschließende Optionen
 Die Option **AutoMark** kann nur mit der Option **WinCounter** verwendet werden.

 **AutoMark:** `Milliseconds` gibt die Zeit in Millisekunden zwischen Datenerfassungen mit einem Windows-Leistungsindikator an.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden zwei Windows-Leistungsindikatoren angeben, die in einem Intervall von 1000 ms erfasst werden.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000
```

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)
