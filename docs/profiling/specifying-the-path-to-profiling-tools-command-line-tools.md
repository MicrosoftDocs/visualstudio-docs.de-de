---
title: Angeben des Pfads zu Befehlszeilentools für die Profilerstellung
description: Geben Sie den Pfad zu Befehlszeilentools der Profilerstellungstools an, wenn deren Pfad nicht zur Umgebungsvariablen PATH hinzugefügt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fa1cb81d46f0977de2db9d78c6db53f542faa70f
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720032"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Angeben des Pfads zu Befehlszeilentools für Profilerstellungstools

Der Pfad der Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools wird der PATH-Umgebungsvariablen nicht hinzugefügt. Auf 32-Bit-Computern befinden sich die Tools in einem einzigen Verzeichnis. Es gibt 32-Bit und 64-Bit-Versionen der Profilerstellungstools auf 64-Bit-Computern.

## <a name="32-bit-computers"></a>32-Bit-Computer

Für nativen Code befinden sich die Visual Studio-Profiler-APIs in der Datei *VSPerf.dll*. Die Headerdatei *VSPerf.h* und die Importbibliothek *VSPerf.lib* befinden sich im Verzeichnis *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*.

 Für verwalteten Code befinden sich die Profiler-APIs in *Microsoft.VisualStudio.Profiler.dll*. Diese DLL befindet sich im Verzeichnis *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*.

## <a name="64-bit-computers"></a>64-Bit-Computer

Auf 64-Bit-Computern legen Sie den Pfad entsprechend der Zielplattform der profilierten Anwendung fest.

- Bei 32-Bit-Anwendungen lautet das Standardverzeichnis für Profilerstellungstools:

     (nativ) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*
     
     (verwaltet) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- Bei 64-Bit-Anwendungen lautet das Standardverzeichnis für Profilerstellungstools:

     (nativ) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*

     (verwaltet) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
