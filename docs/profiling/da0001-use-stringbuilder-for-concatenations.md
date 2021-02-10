---
title: 'DA0001: StringBuilder für Verkettungen verwenden | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e94aac22eae270abdffef5c7a866b353bce90fd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938445"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: StringBuilder für Verkettungen verwenden

|Element|Wert|
|-|-|
|Regel-ID|DA0001|
|Kategorie|.NET Framework-Verwendung|
|Profilerstellungsmethoden|Sampling<br /><br /> Instrumentation|
|Meldung|Verwenden Sie für Verkettungen ggf. StringBuilder.|
|Nachrichtentyp|Warnung|

## <a name="cause"></a>Ursache
 Aufrufe von System.String.Concat machen einen großen Teil der Profilerstellungsdaten aus. Verwenden Sie ggf. die <xref:System.Text.StringBuilder>-Klasse zum Erstellen von Zeichenfolgen aus mehreren Segmenten.

## <a name="rule-description"></a>Regelbeschreibung
 Ein <xref:System.String>-Objekt ist unveränderlich. Daher entsteht bei jeder Änderung an der Zeichenfolge ein neues Zeichenfolgenobjekt und die Garbage Collection des Originals. Dieses Verhalten ist dasselbe, egal, ob Sie String.Concat explizit aufrufen oder Zeichenfolgenverkettungsoperatoren wie + oder += verwenden. Die Programmleistung kann abfallen, wenn diese Methoden häufig aufgerufen werden, beispielsweise wenn in einer engen Schleife Zeichen zu einer Zeichenfolge hinzugefügt werden.

 Bei der StringBuilder-Klasse handelt es sich um ein änderbares Objekt. Im Gegensatz zu System.String geben die meisten Methoden für StringBuilder, mit denen eine Instanz dieser Klasse geändert wird, einen Verweis auf diese Instanz zurück. In einer StringBuilder-Instanz können Sie Zeichen hinzufügen oder Text anfügen und Zeichen entfernen oder ersetzen, ohne eine neue Instanz zuordnen und die ursprüngliche Instanz löschen zu müssen.

## <a name="how-to-investigate-a-warning"></a>Vorgehensweise zur Überprüfung einer Warnung
 Doppelklicken Sie auf die Meldung im Fenster **Fehlerliste**, um zur [Funktionsdetailansicht](../profiling/function-details-view.md) der Samplingprofildaten zu navigieren. Suchen Sie die Abschnitte des Programms, in denen Zeichenfolgenverkettungen am häufigsten verwendet werden. Verwenden Sie die StringBuilder-Klasse für komplexe Zeichenfolgenbearbeitungen, wie häufige Zeichenfolgenverkettungsoperationen.

 Weitere Informationen zum Arbeiten mit Zeichenfolgen finden Sie im Abschnitt [String Operations (Zeichenfolgenoperationen)](/previous-versions/msp-n-p/ff647790(v=pandp.10)#string-operations) in [Chapter 5 – Improving Managed Code Performance (Kapitel 5 – Verbessern der Leistung von verwaltetem Code)](/previous-versions/msp-n-p/ff647790(v=pandp.10)) in der Microsoft-Bibliothek für Muster und Vorgehensweisen.
