---
title: Grundlagen zu Ressourcenkonflikt-Datenwerten| Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur Profilerstellung für Ressourcenkonflikte. Dabei werden detaillierte Informationen dazu gesammelt, wann miteinander in Konflikt stehende Threads in einer Anwendung gezwungen werden, auf den Zugriff auf eine freigegebene Ressource zu warten.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1a724c360641926bcb64552f6f26e92d3c524011
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722203"
---
# <a name="understand-resource-contention-data-values"></a>Grundlagen zu Ressourcenkonflikt-Datenwerten

Bei der Profilerstellung für Ressourcenkonflikte werden immer dann ausführliche Aufruflisteninformationen gesammelt, wenn konkurrierende Threads in einer Anwendung auf den Zugriff auf eine gemeinsam genutzte Ressource warten müssen.

Ressourcenkonfliktberichte enthalten für die Module, Funktionen, Quellcodezeilen und Anweisungen, in denen die Verzögerung aufgetreten ist, die Gesamtanzahl von Konflikten sowie die Gesamtwartezeit für eine Ressource.

- Inklusive Werte geben Aufschluss über die Gesamtanzahl von Konflikten (sortiert nach Ressourcenkonflikten), aufgrund derer die Verzögerung für die Funktion aufgetreten ist, sowie über die Gesamtwartezeit der Funktion.  In den inklusiven Werten sind auch Konflikte enthalten, die durch untergeordnete, von der Funktion aufgerufene Funktionen verursacht wurden.

- Exklusive Werte geben nur Aufschluss über die Anzahl von Konflikten, die die Verzögerung einer Funktion zur Folge hatten und durch Code im Funktionstext verursacht wurden. Von untergeordneten Funktionen verursachte Konflikte werden nicht berücksichtigt. Die exklusive Zeit für die Funktion enthält auch nur die Wartezeiten, die von Anweisungen im Funktionsrumpf verursacht wurden.

Die Ansichten des Ressourcenkonfliktberichts enthalten auch Zeitachsendiagramme mit den einzelnen Konfliktereignissen im Zeitverlauf und die Aufruflisten, von denen das Ereignis erstellt wurde. Weitere Informationen finden Sie in einem der folgenden Themen:

- [Threaddetailansicht](../profiling/thread-details-view-contention-data.md)

- [Ressourcendetailansicht](../profiling/resource-details-view-contention-data.md)

Weitere Informationen zum zweiten Modus der Parallelitätsprofilerstellung finden Sie unter [Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md).
