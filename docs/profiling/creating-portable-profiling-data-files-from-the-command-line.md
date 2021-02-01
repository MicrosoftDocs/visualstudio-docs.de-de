---
title: 'Profilerstellung über die Befehlszeile: Erstellen von portierbaren Datendateien'
description: Sie können das Befehlszeilentool „VSPerfReport.exe“ zum Einbetten der Symbole für eine Profilerstellungsausführung in die VSP-Datei verwenden, um die Freigabe der Profilerstellungsdaten zu vereinfachen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5df9f14fecce23eb72d08dcba87dee360269e078
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718966"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Erstellen portierbarer Profilerstellungsdatendateien über die Befehlszeile
Sie können das Befehlszeilentool [VSPerfReport](../profiling/vsperfreport.md) zum Einbetten der Symbole für eine Profilerstellungsausführung in die *VSP*-Datei verwenden, um die Freigabe der Profilerstellungsdaten zu vereinfachen.

 Sie können auch eine bereits analysierte Profilerstellungsdatendatei (*VSPS*) erstellen, die kleiner ist und schneller in der IDE geladen wird.

> [!NOTE]
> Stellen Sie sicher, dass die Symboldateien (*PDB*) von **VSPerfReport** verwendet werden können. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben von Symboldateispeicherorten über die Befehlszeile](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).
>
> Weitere Informationen zur Pfadangabe für **VSReport** finden Sie unter [Angeben des Pfads zu den Profilerstellungstools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).
>
> Die Profilerstellungsdaten in einer *VSPS*-Datei können nicht gefiltert werden.

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Einbetten von Symbolen in die Profilerstellungsdatendatei (*VSP*) für die Profilerstellungsausführung

- Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:

   \<Path><strong>VSPerfReport \<</strong>VSP-Datei> **/PackSymbols**

   Der Name der *VSPS*-Datei ist standardmäßig der Basisname der *VSP*-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.

### <a name="to-create-a-summary-profiling-data-file"></a>Erstellen einer zusammenfassenden Profilerstellungsdatendatei

- Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:

   \<Path><strong>VSPerfReport \<</strong>VSP-Datei> **/SummaryFile** [ **/Output:** \<File Name>]

   Der Name der *VSPS*-Datei ist standardmäßig der Basisname der *VSP*-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.
