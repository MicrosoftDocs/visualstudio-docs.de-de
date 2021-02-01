---
title: Markerbericht | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zum Markerbericht. Dieser führt die Marker im angezeigten Zeitrahmen auf. Außerdem erfahren Sie, wie das Schwenken oder Zoomen dazu führen könnte, dass Marker angezeigt oder ausgeblendet werden.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e95cf3b14f804c481ff03ec6fbf72b360efedc7
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722112"
---
# <a name="markers-report"></a>Markerbericht
Der Markerbericht führt die Marker im angezeigten Zeitrahmen auf.  Das Schwenken, Zoomen oder Ausblenden von Bereichen führt, möglicherweise dazu, das Marker angezeigt werden oder wieder ausgeblendet werden. Der Bericht enthält folgende Informationen über jeden Marker:

- Die Startzeit, relativ zum Beginn der Ablaufverfolgung.

- Die Dauer. Die Dauer beträgt 0 (null) für Flags und Nachrichten, da sie einen Zeitpunkt darstellen.

- Die ID des Threads, der sie generiert hat.

- Die Ereignisablaufverfolgung (ETW) für den Windows-Anbieter, der diese generiert hat.

- Die Markerreihe aus die er geschrieben wurde.

- Die Kategorie der Ereignisse, denen er angehört.

- Die Wichtigkeitsstufe.

- Der Typ (span, flag oder message).

- Eine allgemeine Beschreibung der Bedeutung.

  Wählen Sie die Schaltfläche **Exportieren** aus, um den Markerbericht als CSV-Datei zu speichern. Sie können die Daten in der CSV-Datei mit anderen Apps oder Tools verwenden.

> [!NOTE]
> Der Markerbericht kann 1.000 Marker anzeigen. Um alle Marker anzuzeigen, exportieren Sie den vollständigen Bericht in eine CSV-Datei.