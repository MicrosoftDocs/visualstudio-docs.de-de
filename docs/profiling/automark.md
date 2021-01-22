---
title: AutoMark | Microsoft-Dokumentation
description: Verwenden Sie die AutoMark-Option, um das Zeitintervall zwischen Datensammlungsereignissen für Windows-Leistungsindikatoren anzugeben. Verwenden Sie sie mit der WinCounter-Option.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 94578571a9cfe6a170fd94019615eeec3071356a
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205761"
---
# <a name="automark"></a>AutoMark
Die Option **AutoMark** gibt die Zeit in Millisekunden an, die für die Erfassung von Leistungsindikatorereignissen für Windows-Software beansprucht wird. Windows-Leistungsindikatoren werden in der Option **WinCounter** angegeben.

 In der Befehlszeile kann nur eine **AutoMark**-Option angegeben werden. Bitte beachten Sie, dass das von **AutoMark** angegebene Samplingintervall **WinCounter** unabhängig vom Hauptsamplingintervall ist.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds
```

#### <a name="parameters"></a>Parameter
 `Milliseconds`: gibt die Zeit in Millisekunden an, die für die Erfassungen von Windows-Leistungsindikatorereignissen beansprucht wird.

## <a name="required-options"></a>Erforderliche Optionen
 **WinCounter:** `Path` gibt den Windows-Leistungsindikator an, der erfasst werden soll. Wenn Sie die Instrumentierungsmethode verwenden, können Sie mehrere Windows-Indikatoren angeben. Wenn Sie die Samplingmethode verwenden, können Sie nur einen Software-Indikator angeben. Die Option **WinCounter** muss in einer Befehlszeile angegeben sein, die die Option **Start** enthält.

## <a name="example"></a>Beispiel
 In diesem Beispiel ist ein Samplingintervall von 1000 ms für zwei Windows-Leistungsindikatoren festgelegt.

```cmd
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)
