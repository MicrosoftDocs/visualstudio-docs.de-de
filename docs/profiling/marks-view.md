---
title: Markierungsansicht | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur Ansicht „Markierungen“. Diese zeigt Sampling- und ETW-Ereignisse, die in die Anwendung eingefügt wurden.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.marks
helpviewer_keywords:
- profiling tools, Marks view
- profiling tools reports, Marks view
ms.assetid: b2773344-8081-4116-85a1-58f770448f6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 969bf0debfc1da9f7ca1763d8c9c001d565ce64a
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718979"
---
# <a name="marks-view"></a>Markierungsansicht
In der Ansicht "Markierungen" werden Sampling- und ETW-Ereignisse angezeigt, die in die Anwendung eingefügt wurden.

 Die bereits im Bericht enthaltenen Standardmarkierungen kennzeichnen den Start und das Ende des Programms.

 In dieser Ansicht werden auch Windows-Indikatordaten von automatisch generierten Markierungen dargestellt. Weitere Informationen finden Sie unter [Vorgehensweise: Sammeln von Windows-Indikatordaten](../profiling/how-to-collect-windows-counter-data.md).

 Um zwischen zwei Markierungen einen Filter zu erstellen, wählen Sie die Markierungen aus, klicken mit der rechten Maustaste und klicken dann auf **Filter für Markierungen hinzufügen** oder auf **Filter für Zeitstempel hinzufügen**.

 In der folgenden Tabelle sind die Definitionen der in der Ansicht "Markierungen" verfügbaren Spalten aufgeführt:

 **Markierungs-ID:** eindeutiger Bezeichner der Profilerstellungsmarkierung.

 **Markierungsname:** der Name des Ereignisses.

 **Zeitstempel:** die Zeit vom Start der Profilerstellung bis zu dem Zeitpunkt, an dem das Ereignis aufgezeichnet wurde.

 Windows-Leistungsindikatordaten: Wenn Windows-Leistungsindikatordaten gesammelt werden, werden die Werte in einer Spalte angezeigt, die den Namen des Leistungsindikators hat.

## <a name="see-also"></a>Siehe auch
- [Leistungsberichtübersicht](../profiling/performance-report-overview.md)
- [Vorgehensweise: Sammeln von Windows-Indikatordaten](../profiling/how-to-collect-windows-counter-data.md)
- [&#91;NIB&#93; Data Collection Control window (Fenster zur Steuerung der Datensammlung für &#91;NIB&#93)](/previous-versions/bb385767(v=vs.110))