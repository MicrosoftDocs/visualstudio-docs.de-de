---
title: 'DA0007: Verwenden Sie möglichst keine Ausnahmen für die routinemäßige Ablaufsteuerung | Microsoft-Dokumentation'
description: In den Profilerstellungsdaten wurde eine Vielzahl von .NET Framework-Ausnahmehandlern aufgerufen.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2648e287ea37e1ae78b14a65c02521f72a3491d0
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466127"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Vermeiden der Verwendung von Ausnahmen für die Ablaufsteuerung

|Element|Wert|
|-|-|
|Regel-ID|DA0007|
|Kategorie|.NET Framework-Verwendung|
|Profilerstellungsmethoden|Alle|
|Meldung|Es wird permanent eine hohe Anzahl von Ausnahmen ausgelöst. Verwenden Sie nach Möglichkeit weniger Ausnahmen in der Programmlogik.|
|Nachrichtentyp|Warnung|

 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 25 Samplings erfasst werden, damit diese Regel ausgelöst wird.

## <a name="cause"></a>Ursache
 In den Profilerstellungsdaten wurde eine Vielzahl von .NET Framework-Ausnahmehandlern aufgerufen. Verwenden Sie ggf. eine andere Kontrollflusslogik, um die Anzahl der ausgelösten Ausnahmen zu verringern.

## <a name="rule-description"></a>Regelbeschreibung
 Während die Verwendung von Ausnahmehandlern zum Abfangen von Fehlern und anderen Ereignissen, durch die die Programmausführung unterbrochen wird, eine empfohlene Vorgehensweise ist, kann die Verwendung des Ausnahmehandlers als Teil der regulären Programmausführungslogik sehr speicherintensiv sein und sollte vermieden werden. In der Regel sollten Ausnahmen nur für außergewöhnliche und unerwartete Umstände verwendet werden. Ausnahmen sollten nicht verwendet werden, um Werte als Teil des typischen Programmablaufs zurückzugeben. Häufig können Sie das Auslösen von Ausnahmen vermeiden, wenn Sie Werte überprüfen und mithilfe einer bedingten Logik die Ausführung von Anweisungen anhalten, von denen das Problem verursacht wird.

 Weitere Informationen finden Sie im Abschnitt [Exception Management (Ausnahmeverwaltung)](/previous-versions/msp-n-p/ff647790(v=pandp.10)#exception-management) in **Chapter 5 – Improving Managed Code Performance (Kapitel 5: Verbessern der Leistung von verwaltetem Code)** im Band **Improving .NET Application Performance and Scalability (Verbessern von Leistung und Skalierbarkeit von .NET-Anwendungen)** der Microsoft-Bibliothek für **Muster und Vorgehensweisen** im MSDN.

## <a name="how-to-investigate-a-warning"></a>Vorgehensweise zur Überprüfung einer Warnung
 Doppelklicken Sie auf die Meldung im Fenster „Fehlerliste“, um zur Ansicht „Markierungen“ zu navigieren. Suchen Sie die Spalte, die die Messung für **.NET CLR-Ausnahmen(@ProcessInstance)\\Anzahl der ausgelösten Ausnahmen/Sek.** enthält. Überprüfen Sie, ob die Ausnahmebehandlung in bestimmten Phasen der Programmausführung besonders häufig auftritt. Suchen Sie mithilfe eines Samplingprofils nach throw-Anweisungen und try/catch-Blöcken, die häufig Ausnahmen generieren. Ergänzen Sie ggf. catch-Blöcke mit einer Logik, die zeigt, welche Ausnahmen am häufigsten behandelt werden. Ersetzen Sie nach Möglichkeit häufig ausgeführte throw-Anweisungen oder catch-Blöcke durch einfache Flusssteuerungslogik oder Validierungscode.

 Wenn Sie beispielsweise feststellen, dass von Ihrer Anwendung häufig DivideByZeroException-Ausnahmen behandelt werden, können Sie die Leistung der Anwendung verbessern, indem Sie eine Logik zum Programm hinzufügen, mit der überprüft wird, ob Nenner mit dem Wert null (0) vorhanden sind.
