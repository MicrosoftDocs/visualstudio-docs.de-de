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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b5b7eedaf7aac4a22ca10580395e085243f831ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851971"
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