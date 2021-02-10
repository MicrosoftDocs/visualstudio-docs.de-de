---
title: Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern
description: Erfahren Sie, wie Sie Analyzer auf Code Maps ausführen können, um Ihnen zu helfen, Code zu identifizieren, der möglicherweise übermäßig Komplex ist oder verbessert werden kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 77e5d8f6241f6f1978f24b9ebb5ad49aa9f24331
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934987"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern

Führen Sie Analyzer auf Code Maps aus, die Ihnen beim Auffinden sehr komplexer oder verbesserungswürdiger Codeabschnitte helfen. Sie können beispielsweise folgende Analyzer verwenden:

|**Um Code mit diesem Problem zu finden**|**Prüfen Sie, ob diese Abschnitte...**|
|-|-|
|Schleifen oder Ringabhängigkeiten|...vereinfacht werden können, und überlegen Sie, ob sich diese Kreisläufe auflösen lassen.|
|Zu viele Abhängigkeiten|...zu viele Funktionen durchführen oder stellen Sie die Auswirkungen einer Änderung in diesen Bereichen fest. Eine wohlgeformte Code Map weist eine minimale Anzahl von Abhängigkeiten auf. Damit Code einfacher zu verwalten, zu ändern, zu testen und wiederzuverwenden ist, erwägen Sie, ob Sie diese Bereiche so umgestalten können, dass sie eindeutig definiert sind, oder ob Code zusammengeführt werden kann, der ähnliche Funktionen ausführt.|
|Keine Abhängigkeiten|...wirklich benötigt werden oder ob Sie diesen Code entfernen können.|

## <a name="analyze-code-maps"></a>Analysieren von Code Maps

Wählen Sie auf der Zuordnungs Symbolleiste **layoutanalyzers**  >  und dann das Analysetool aus, das Sie ausführen möchten:

|**Analyzer**|**Zur Identifizierung der Knoten, die...**|
|-|-|
|**Zirkelverweis-Analyzer**|...Ringabhängigkeiten untereinander aufweisen. **Hinweis:**  Zirkuläre Abhängigkeiten in der **Generika** Gruppe werden nicht in der Zuordnung angezeigt, wenn Sie die Gruppe erweitern.|
|**Hubs Analyzer suchen**|...zu den obersten 25 % der Knoten mit den meisten Verbindungen gehören<br /><br /> **So blenden Sie alle anderen Knoten auf der Map aus**<br /><br /> -Öffnen Sie das Kontextmenü für die Karte, wählen Sie **erweitert**, **auswählen**, **nicht ausgewählt ausblenden** aus.<br />     Nicht markierte Knoten werden auf der Map ausgeblendet und neue Knoten werden vom Analyzer als Hubs identifiziert.|
|**Analyzer für Knoten, auf die nicht verwiesen wird**|...keine Verweise aus anderen Knoten haben. **Vorsicht:**  Überprüfen Sie jeden dieser Fälle, bevor Sie davon ausgehen, dass der Code nicht verwendet wird. Bestimmte Abhängigkeiten wie XAML- und Laufzeitabhängigkeiten können im Code nicht statisch gefunden werden.|

Code Map Analyzer werden weiterhin ausgeführt, nachdem Sie sie anwenden. Wenn Sie die Map ändern, verarbeiten alle angewendeten Analyzer automatisch die aktualisierte Map erneut. Um die Ausführung eines Analyzers zu beenden, wählen Sie auf der Kartensymbol Leiste **layoutanalyzers** aus  >  . Deaktivieren Sie den ausgewählten Analyzer.

> [!TIP]
> Bei einer sehr großen Map tritt bei der Ausführung eines Analyzers,möglicherweise eine Ausnahme aufgrund unzureichenden Arbeitsspeichers auf. Bearbeiten Sie in diesem Fall die Map, um den Umfang zu verringern oder eine kleinere Map zu generieren, und führen Sie dann den Analyzer aus.

## <a name="see-also"></a>Siehe auch

- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)
- [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)
- [Zuordnen von Methoden in der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
