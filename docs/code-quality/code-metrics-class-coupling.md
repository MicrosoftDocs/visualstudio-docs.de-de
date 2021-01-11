---
title: Codemetrik-Klassen Kopplung
ms.date: 1/8/2021
description: Erfahren Sie mehr über die Klassen Kopplung-Metrik für Codemetriken in Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db1308843cb3c4fe8fb0a4aa32300e545e5e3a7c
ms.sourcegitcommit: b1f7e7d7a0550d5c6f46adff3bddd44bc1d6ee1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2021
ms.locfileid: "98069534"
---
# <a name="code-metrics---class-coupling"></a>Codemetrik-Klassen Kopplung

Die Klassen Kopplung wird auch von der namens Kopplung zwischen Objekten (CBO) wie ursprünglich durch [CK94](#ck94)definiert. Im Grunde ist die Klassen Kopplung ein Maß für die Anzahl der Klassen, die von einer einzelnen Klasse verwendet werden. Eine hohe Zahl ist schlecht, und eine niedrige Zahl ist in der Regel mit dieser Metrik gut. Die Klassen Kopplung ist ein genauer Prätor von Softwarefehlern, und in den jüngsten Studien wurde gezeigt, dass ein oberer Grenzwert von 9 die effizienteste [S2010](#s2010)ist.

Gemäß der Microsoft-Dokumentation misst die Klassen Kopplung die Kopplung mit eindeutigen Klassen durch Parameter, lokale Variablen, Rückgabe Typen, Methodenaufrufe, generische oder Vorlagen Instanziierungen, Basisklassen, Schnittstellen Implementierungen, für externe Typen definierte Felder und die Attribut Ergänzung. Ein guter Software Entwurf legt fest, dass die Typen und Methoden eine hohe Kohäsion und eine geringe Kopplung aufweisen sollten. Hohe Kopplung weist auf einen Entwurf hin, der aufgrund der vielen Abhängigkeiten von anderen Typen schwierig zu verwenden und zu warten ist. "

Die Konzepte von Kopplung und Kohäsion sind eindeutig miteinander verknüpft. Um diese Erörterung zu erörtern, werden wir uns nicht ausführlich mit dem Zusammenhang mit dem anderen zusammensetzen als eine kurze Definition von [KKLS2000](#kkls2000):

"Der Modul-Zusammenhalt wurde von Yourdon und Konstantin als ', wie eng gebunden oder verknüpft die internen Elemente eines Moduls sind, in ein anderes ' [YC79](#yc79)" eingeführt. Ein Modul hat einen starken Zusammenhalt, wenn es genau einen Task [...] darstellt und alle seine Elemente zu diesem einzelnen Task beitragen. Sie beschreiben den Zusammenhalt als Attribut des Entwurfs anstelle von Code und ein Attribut, das verwendet werden kann, um die Wiederverwendbarkeit, Wartbarkeit und changeability vorherzusagen. "

## <a name="class-coupling-example"></a>Beispiel für Klassen Kopplung

Betrachten wir nun die Klassen Kopplung in Aktion. Erstellen Sie zunächst eine neue Konsolenanwendung, und erstellen Sie eine neue Klasse mit dem Namen "Person" mit einigen Eigenschaften, und berechnen Sie dann die Codemetriken sofort:

![Klassen Kopplung, Beispiel 1](media/class-coupling-example-1.png)

Beachten Sie, dass die Klassen Kopplung 0 ist, da diese Klasse keine anderen Klassen verwendet. Erstellen Sie jetzt eine weitere Klasse mit dem Namen personstuff mit einer Methode, die eine Instanz von Person erstellt und die Eigenschaftswerte festlegt. Erneutes Berechnen der Codemetriken:

![Beispiel für Klassen Kopplung 2](media/class-coupling-example-2.png)

Sehen Sie, wie der Wert für die Klassen Kopplung ausfällt? Beachten Sie auch, dass unabhängig von der Anzahl der von Ihnen festgelegten Eigenschaften der Wert für die Klassen Kopplung nur 1 und nicht durch einen anderen Wert ist. Die Klassen Kopplung misst jede Klasse nur einmal für diese Metrik, unabhängig davon, wie viel Sie verwendet wird. Außerdem können Sie sehen, dass `DoSomething()` über einen 1 verfügt, der Konstruktor, `PersonStuff()` , aber einen Wert von 0 für seinen Wert hat? Aktuell gibt es keinen Code im Konstruktor, der eine andere Klasse verwendet.

Was geschieht, wenn Sie Code im Konstruktor platzieren, der eine andere Klasse verwendet hat? Hier finden Sie Folgendes:

![Klassen Kopplung, Beispiel 3](media/class-coupling-example-3.png)

Nun weist der Konstruktor eindeutig Code auf, der eine andere Klasse verwendet, und die Klassen Kopplung zeigt diese Tatsache. Auch hier können Sie sehen, dass die Gesamt Klassen Kopplung für den Wert `PersonStuff()` 1 hat und `DoSomething()` gleich 1 ist, um anzuzeigen, dass nur eine externe Klasse verwendet wird, unabhängig davon, wie viel Interner Code verwendet wird.

Erstellen Sie als nächstes eine neue Klasse. Benennen Sie diese Klasse, und erstellen Sie einige Eigenschaften darin:

![Beispiel für Klassen Kopplung-neue Klasse hinzufügen](media/class-coupling-example-add-new-class.png)

Nutzen Sie nun die-Klasse in unserer `DoSomething()` -Methode innerhalb der `PersonStuff` -Klasse, und berechnen Sie die Codemetriken erneut

![Klassen Kopplung, Beispiel 4](media/class-coupling-example-4.png)

Wie Sie sehen, wird die Klassen Kopplung für die personstuff-Klasse auf 2 hochskalieren. Wenn Sie einen Drilldown in die-Klasse durchführen, sehen Sie, dass die- `DoSomething()` Methode über die größte Kopplung verfügt, aber der Konstruktor verwendet immer noch nur eine Klasse.  Mithilfe dieser Metriken können Sie die maximale Gesamtzahl für eine bestimmte Klasse anzeigen und einen Drilldown in die Details pro Member ausführen.

## <a name="the-magic-number"></a>Die magische Zahl

Ebenso wie die zyklomatische Komplexität gibt es keine Beschränkung für alle Organisationen. [S2010](#s2010) gibt jedoch an, dass ein Limit von 9 optimal ist:

"Daher werden die Schwellenwerte berücksichtigt [...] Dies ist am effektivsten. Diese Schwellenwerte (bei einem einzelnen Member) lauten CBO = 9 [...]. " (Betonung hinzugefügt)

## <a name="code-analysis"></a>Codeanalyse

Die Code Analyse umfasst eine Kategorie von wart barkeits Regeln. Weitere Informationen finden Sie unter [wart barkeits Regeln](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). Wenn Sie die Legacy Code Analyse verwenden, enthält der Regelsatz für erweiterte Entwurfs Richtlinien einen verwaltbarkeitsbereich:

![Regeln für erweiterte Entwurfs Richtlinien für Klassen Kopplung](media/class-coupling-extended-design-guideline-rules.png)

Im wart barkeits Bereich ist eine Regel für die Klassen Kopplung:

![Klassen Kopplung (Regel)](media/class-coupling-maintainability-area-rules.png)

Diese Regel gibt eine Warnung aus, wenn die Klassen Kopplung übermäßig groß ist. Weitere Informationen finden Sie unter [CA1506: Vermeiden einer übermäßigen Klassen Kopplung](/dotnet/fundamentals/code-analysis/quality-rules/ca1506).

Eine Beschreibung dieser Regel finden Sie im Blogbeitrag Archivierte Code Analyse: [Codemetriken als Check-in-Richtlinie](/archive/blogs/codeanalysis/code-metrics-as-check-in-policy) und die Schwellenwert Beschreibungs *Warnung bei über 80 für die-Klasse und über 30 für eine-Methode*.  Diese Werte scheinen normalerweise hoch, aber zumindest eine extreme Obergrenze bereitzustellen. Wenn Sie diese Warnung erreichen, ist das fast sicherlich falsch.

## <a name="citations"></a>Zitate Dokumenten

### <a name="ck94"></a>CK94

Chidamber, S. R. & kemerer, C. F. (1994). Eine metriksuite für den objektorientierten Entwurf (IEEE-Transaktionen auf Software Engineering, Vol. 20, Nein. 6). Abgerufen am 14. Mai 2011, von der University of Pittsburgh-Website: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="kkls2000"></a>KKLS2000

Kabaili, H., Keller, R., LUSTMAN, F. und St-Denis, G. (2000). Die Zusammenarbeit der Klasse "Kohäsion": eine empirische Studie zu Industriesystemen (Workshop des Workshops zu quantitativen Ansätzen in Object-Oriented Software Engineering). Abgerufen am 20. Mai 2011 von der Université de Montréal-Website [http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf](http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf)

### <a name="sk2003"></a>SK2003

Subramanyam, R. & Krishnan, M. S. (2003). Empirische Analyse von ck-Metriken für Object-Oriented Design Komplexität: Auswirkungen auf Software Mängel (IEEE-Transaktionen bei der Software Entwicklung, Vol. 29, Nein. 4). Abgerufen am 14. Mai 2011 von University of Massachusetts Dartmouth Web Site [http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf](http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf)

### <a name="s2010"></a>S2010

Shatnawi, R. (2010). Eine quantitative Untersuchung der akzeptablen Risikostufen von Object-Oriented Metriken in Open-Source Systemen (IEEE-Transaktionen auf Software Engineering, Vol. 36, Nein. 2).

### <a name="yc79"></a>YC79

Edward Yourdon und Larry L. Konstantin. Strukturierter Entwurf. Prentice Hall, Englewood Cliffs, N.J., 1979.