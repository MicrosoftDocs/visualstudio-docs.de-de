---
title: Zeilenansicht | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur Zeilenansicht. Diese ist nur für Profilerdaten verfügbar, die mit der Samplingmethode erfasst wurden.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ac0d7785071e5f2928e7eabb4a29b1655b42c5ad
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721293"
---
# <a name="lines-view"></a>Zeilenansicht
Die Zeilenansicht ist nur für Profilerdaten verfügbar, die mit der Samplingmethode gesammelt wurden. Die Ansicht ist nicht für Daten verfügbar, die mit der Instrumentationsmethode gesammelt wurden.

 Für das Sampling von Profildaten identifiziert die Zeilenansicht die Anweisungen in einer Funktion, die direkt ausgeführt wurde, als das Sampling gesammelt wurde. Die Zeilenansicht identifiziert für .NET-Speicherdaten die Anweisungen, die Speicher zuweisen.

 In einer Quelldatei kann eine Anweisung mehrere Zeilen umfassen, und eine einzelne Zeile kann mehr als eine Anweisung enthalten.

 Eine Anweisung wird mit dem Folgenden identifiziert:

- Die Quelldatei, die die Funktionsanweisung enthält.

- Die Funktion, die die Anweisung enthält.

- Die Quellzeile, an der die Anweisung beginnt.

- Das Zeichen in der Quellzeile, an dem die Anweisung beginnt.

- Die Quellzeile, an der die Anweisung endet.

- Das Zeichen in der Quellzeile, an dem die Anweisung endet.

## <a name="see-also"></a>Siehe auch
- [Zeilenansicht](../profiling/lines-view-sampling-data.md)
- [Zeilenansicht: Sampling](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Zeilenansicht](../profiling/lines-view-contention-data.md)
