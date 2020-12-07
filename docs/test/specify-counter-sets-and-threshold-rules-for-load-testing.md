---
title: Indikatorensätze und Schwellenwertregeln für Auslastungstests
description: Hier erfahren Sie, wie Sie Indikatorensätze und Schwellenwertregeln in einem Auslastungstest festlegen. Fügen Sie die zu testenden Server der Liste der Computern hinzu, für die Indikatoren erfasst werden.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- load tests, thresholds
- counter sets
- load tests, performance
- load tests, counter sets
- load tests, threshold rules
ms.assetid: 9e14d955-f3a4-4717-bbfe-7f08cdda5678
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 04348eb2d88c560e9687c687486e6b44d8394371
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328950"
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest

Auslastungstests stellen benannte Indikatorensätze zur Verfügung, die bei der Analyse von Leistungsindikatordaten von Nutzen sind. Die Indikatorensätze sind nach Technologie organisiert und umfassen "Anwendung", "ASP.NET", ".NET-Anwendung", "IIS" und "SQL". Wenn Sie mit dem **Assistenten für neuen Auslastungstest** einen Auslastungstest erstellen, fügen Sie einen anfänglichen Satz von Indikatoren hinzu. Dadurch erhalten Sie einen Satz vordefinierter wichtiger Indikatorensätze für den Auslastungstest. Sie können die Indikatoren mit dem **Auslastungstest-Editor** verwalten.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Bei der Verteilung der Auslastungstests auf mehrere Remotecomputer werden Indikatoren für Controller und Agents den Controller- und Agent-Indikatorensätzen zugeordnet. Weitere Informationen zur Verwendung von Remotecomputern im Auslastungstest finden Sie unter [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md).

Indikatorensätze werden auf den von Ihnen angegebenen Computern erfasst. Die während eines Auslastungstests verwendete Zuordnung eines Indikatorensatzes zu einem Computer wird als *Indikatorensatzzuordnung* bezeichnet. Beispielsweise verfügt der von Ihnen getestete Webserver über Indikatorensatzzuordnungen für ASP.NET-, IIS- und .NET-Anwendungen.

Standardmäßig werden Leistungsindikatoren für Controller und Agents erfasst. Weitere Informationen finden Sie im Artikel zu [Testcontrollern und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md).

Es ist wichtig, dass Sie die zu testenden Server der Liste von Computern hinzufügen, für die Indikatoren erfasst werden. Anschließend werden während des Auslastungstests alle wichtigen Systemdaten gesammelt und überwacht.

## <a name="tasks"></a>Aufgaben

|Aufgaben|Verwandte Themen|
|-|-----------------------|
|**Verwalten der Indikatorensätze für den Auslastungstest**: Nachdem Sie den Auslastungstest erstellt haben, können Sie den Indikatorensatz im Auslastungstest-Editor bearbeiten. Das Verwalten von Indikatorensätzen umfasst die Auswahl der Computer, für die Leistungsdaten gesammelt werden, und das Zuweisen von Indikatorensätzen, die auf jedem der Computer erfasst werden. Sie können die Indikatoren im Auslastungstest-Editor verwalten.|-   [Vorgehensweise: Verwalten von Indikatorensätzen](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**Hinzufügen von Indikatorensätzen zum Auslastungstest**: Wenn Sie einen Auslastungstest mit dem **Assistenten für neuen Auslastungstest** erstellen, fügen Sie einen ersten Indikatorensatz hinzu. Dadurch erhalten Sie einen Satz vordefinierter Indikatorensätze für den Auslastungstest. Nachdem Sie einen Auslastungstest erstellt haben, können Sie vorhandenen Indikatorensätzen mithilfe des Auslastungstest-Editors neue Indikatoren hinzufügen.|-   [Vorgehensweise: Hinzufügen von Indikatoren zu Indikatorensätzen](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [Vorgehensweise: Hinzufügen von benutzerdefinierten Indikatorensätzen](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**Angeben einer Schwellenwertregel mithilfe von Indikatoren für den Auslastungstest**: Eine Schwellenwertregel ist eine Regel, die für einen einzelnen Leistungsindikator festgelegt wird, um die Systemressourcenauslastung während eines Auslastungstests zu überwachen. Die Indikatorsatzdefinitionen enthalten vordefinierte Schwellenwertregeln für viele wichtige Leistungsindikatoren. In Auslastungstests werden mithilfe von Schwellenwertregeln Leistungsindikatorwerte entweder mit einem konstanten Wert oder mit einem anderen Leistungsindikatorwert verglichen.|-   [Vorgehensweise: Hinzufügen einer Schwellenwertregel](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**Zuweisen von Anzeigenamen für die Computer, denen Indikatorensätze zugeordnet werden**: Sie können Computertags hinzufügen, mit deren Hilfe Sie einem Computer einen leicht erkennbaren Namen zuweisen können. Die Tags werden im Knoten **Indikatorensatzzuordnungen** der Struktur im Auslastungstest-Editor angezeigt. Wichtiger ist jedoch, dass die Tags in Excel-Berichten angezeigt werden, sodass die Projektbeteiligten die Rolle des Computers im Auslastungstest erkennen können, z. B. "Webserver1 in Lab2" oder "SQL Server2 im Phoenix-Büro".<br /><br /> Weitere Informationen finden Sie unter [Erstellen von Berichten zu Auslastungstestergebnissen für Testvergleiche oder die Trendanalyse](../test/compare-load-test-results.md).||

## <a name="use-counter-sets"></a>Verwenden von Indikatorensätzen

Die Auslastungstesttools erfassen mithilfe von Indikatoren die Leistungsdaten über einen bestimmten Zeitraum und stellen diese grafisch dar. Indikatordaten werden während eines Auslastungstestlaufs in den vom Benutzer angegebenen Intervallen erfasst. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben der Abtastrate](../test/how-to-specify-the-sample-rate-for-a-load-test.md). Die Indikatoren können zur Laufzeit oder nach Abschluss eines Auslastungstestlaufs mit dem *Auslastungstest-Analyzer* angezeigt werden.

Indikatordaten werden für den Server und alle Computer erfasst, auf denen ein Test ausgeführt wird. Wenn Sie eine Gruppe von Agent-Computern eingerichtet haben, auf denen die Tests ausgeführt werden sollen, werden außerdem auch Indikatoren für alle diese Computer erfasst.

Es gibt drei Indikatorkategorien: Prozentwerte, Zähler und Mittelwerte. Beispiele hierfür sind die prozentuale CPU-Auslastung, die Anzahl der SQL Server-Sperren und die IIS-Anforderungen pro Sekunde.

![Auslastungstest-Indikatorensätze](../test/media/loadtestcountersets.png)

Leistungsdaten für einzelne HTTP-Anforderungen werden von dem Computer gemeldet, auf dem der Test ausgeführt wird, beispielsweise von einem Agent-Computer. Für Anforderungen können Sie Daten wie Durchschn. Zeit bis zum ersten Byte, Antwortzeit und Anforderungen pro Sekunde überwachen.

Um das Erfassen von Leistungsdaten für einen Webserver zu erleichtern, stellt Visual Studio Enterprise für verschiedene Technologien vordefinierte, benannte Indikatorensätze zur Verwendung in Auslastungstests bereit. Diese Sätze sind nützlich, wenn Sie einen Server analysieren, der unter IIS, ASP.NET oder SQL Server ausgeführt wird. Nicht im Standardindikatorensatz bereitgestellte Indikatoren können im Auslastungstest-Editor hinzugefügt werden. Es ist wichtig, dass Sie dem Auslastungstest die zu testenden Computer bzw. Server hinzufügen, um sicherzustellen, dass die Ressourcenauslastung für diese Computer überwacht werden kann. Weitere Informationen finden Sie unter [Vorgehensweise: Verwalten von Indikatorensätzen](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

Die Ergebnisanalyse von Auslastungstestläufen erfordert häufig domänenspezifische Kenntnisse eines bestimmten Gebiets, damit bekannt ist, welche Daten erfasst und wo Schwellenwertregeln eingerichtet werden müssen, und wie ermittelt werden kann, wann ein Messwert ein bestimmtes Problem in einer Anwendung widerspiegelt. Weitere Informationen finden Sie unter [Schwellenwertregeln](#about-threshold-rules).

### <a name="performance-counter-sampling-interval-considerations"></a>Überlegungen zum Leistungsindikator-Samplingintervall

Wählen Sie basierend auf der Länge des Auslastungstests einen entsprechenden Wert für die Eigenschaft **Samplingrate** in den Laufzeiteinstellungen des Auslastungstests aus. Eine kleinere Samplingrate (z. B. der Standardwert von fünf Sekunden) erfordert mehr Speicherplatz in der Datenbank für die Auslastungstestergebnisse. Bei längeren Auslastungstests wird durch eine höhere Samplingrate die Menge gesammelter Daten reduziert. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben der Abtastrate](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Die folgende Tabelle enthält Richtlinien für Samplingraten.

|Dauer des Auslastungstests|Empfohlene Samplingrate|
|-|-----------------------------|
|\< 1 Stunde|5 Sekunden|
|1 – 8 Stunden|15 Sekunden|
|8 – 24 Stunden|30 Sekunden|
|> 24 Stunden|60 Sekunden|

## <a name="store-performance-data"></a>Speichern von Leistungsdaten

Während eines Auslastungstestlaufs werden die Leistungsindikatordaten im *Repository für Auslastungstestergebnisse* erfasst und gespeichert. Weitere Informationen finden Sie unter [Verwalten von Auslastungstestergebnissen im Ergebnisrepository für Auslastungstests](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="about-threshold-rules"></a>Schwellenwertregeln

Eine *Schwellenwertregel* wird für einen bestimmten Leistungsindikator festgelegt, um die Verwendung von Systemressourcen während eines Auslastungstests zu überwachen. Die Indikatorsatzdefinitionen enthalten vordefinierte Schwellenwertregeln für viele wichtige Leistungsindikatoren. Weitere Informationen finden Sie unter [Verwenden von Indikatorensätzen für das Unterstützen der Analyse von Leistungsindikatordaten in Auslastungstests](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="threshold-rules-and-levels"></a>Schwellenwertregeln und -stufen

Beim Erstellen von Schwellenwertregeln in Auslastungstests können Sie zwei Regeltypen auswählen:

Mit Konstante vergleichen &mdash; Ein Leistungsindikatorwert wird mit einem konstanten Wert verglichen.

Mit Indikator vergleichen &mdash; Ein Leistungsindikatorwert wird mit einem anderen Leistungsindikatorwert verglichen.

Beim Erstellen von Schwellenwertregeln legen Sie auch die Stufen der Regel fest. Diese Stufen sind der Warnschwellenwert und der kritische Schwellenwert. Beim Anzeigen eines Auslastungstests werden Verletzungen des Warnschwellenwerts durch ein gelbes Symbol und Verletzungen des kritischen Schwellenwerts durch eine rotes Symbol angezeigt.

## <a name="the-alert-if-over-property"></a>Die Eigenschaft „Warnung bei Überschreiten“

Legen Sie die **Warnung bei Überschreiten**-Eigenschaft auf **TRUE** fest, um anzugeben, dass das Überschreiten eines Schwellenwerts ein Problem darstellt. Wenn die Schwellenwertregel beispielsweise für **% Prozessorzeit** festgelegt wurde, und Sie eine Warnung erhalten möchten, wenn der Wert 90 überschreitet, verwenden Sie den Regeltyp **Mit Konstante vergleichen**, und legen Sie für **Kritischer Schwellenwert** den Wert 90 sowie für **Warnung bei Überschreiten** den Wert **TRUE** fest.

Legen Sie die **Warnung bei Überschreiten**-Eigenschaft auf **FALSE** fest, um anzugeben, dass das Unterschreiten eines Schwellenwerts ein Problem darstellt. Wenn die Schwellenwertregel beispielsweise für **Anforderungen/s** festgelegt wurde, und Sie eine Warnung erhalten möchten, wenn der Wert 50 unterschreitet, verwenden Sie den Regeltyp **Mit Konstante vergleichen** und legen den **Kritischen Schwellenwert** auf 50 sowie **Warnung bei Überschreiten** auf **FALSE** fest.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Hinzufügen einer Schwellenwertregel](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [Analysieren von Verstößen gegen Schwellenwertregeln](../test/analyze-threshold-rule-violations-in-load-tests.md)
