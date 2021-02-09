---
title: Berechnen von Codemetriken
ms.date: 11/02/2018
description: Erfahren Sie mehr über die zyklomatische Komplexität, Klassen Kopplung und andere Visual Studio-Codemetriken. Erfahren Sie, wie Metriken den Entwicklungsfortschritt verfolgen und Risiken identifizieren können.
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.codemetrics.toolwindow
dev_langs:
- CSharp
- VB
- FSharp
helpviewer_keywords:
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e77667feae806b66092195f30b028ccca653b2b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860450"
---
# <a name="code-metrics-values"></a>Codemetrikwerte

Die höhere Komplexität moderner Softwareanwendungen erhöht außerdem die Schwierigkeit, den Code zuverlässig und verwaltierbar zu gestalten. Bei der Codemetrik handelt es sich um eine Reihe von Softwaremaßstäben, die Entwicklern einen besseren Einblick in den von ihnen entwickelten Code bieten. Durch die Nutzung von Codemetriken können Entwickler erkennen, welche Typen und/oder Methoden überarbeitet oder gründlich getestet werden sollen. Entwicklungsteams können potenzielle Risiken erkennen, den aktuellen Status eines Projekts verstehen und den Fortschritt während der Softwareentwicklung nachverfolgen.

Entwickler können Visual Studio zum Generieren von Codemetrikdaten verwenden, die die Komplexität und Verwaltbarkeit Ihres verwalteten Codes messen. Codemetrikdaten können für eine gesamte Projekt Mappe oder für ein einzelnes Projekt generiert werden.

Weitere Informationen zum Generieren von Codemetrikdaten in Visual Studio finden Sie unter Gewusst [wie: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Software Messungen

In der folgenden Liste sind die Code Metrikergebnisse aufgeführt, die von Visual Studio berechnet werden:

- **Wart barkeits Index** : berechnet einen Indexwert zwischen 0 und 100, der die relative einfache Verwaltung des Codes darstellt. Ein hoher Wert bedeutet eine bessere Wartbarkeit. Farb codierte Bewertungen können verwendet werden, um schnell Probleme im Code zu erkennen. Eine grüne Bewertung liegt zwischen 20 und 100 und zeigt an, dass der Code eine gute Wartbarkeit hat. Eine gelbe Bewertung liegt zwischen 10 und 19 und gibt an, dass der Code nicht nur in der Lage ist. Eine rote Bewertung ist eine Bewertung zwischen 0 und 9 und deutet auf eine geringe Wartbarkeit hin. Weitere Informationen finden Sie unter der [Bereich der Wartbarkeitsindex und Bedeutung](code-metrics-maintainability-index-range-and-meaning.md).

- **Zyklomatische Komplexität** : misst die strukturelle Komplexität des Codes. Sie wird erstellt, indem die Anzahl der unterschiedlichen Codepfade im Fluss des Programms berechnet wird. Ein Programm, das eine komplexe Ablauf Steuerung aufweist, erfordert mehr Tests, um eine gute Code Coverage zu erzielen und weniger wart Bar zu sein. Weitere Informationen finden Sie im [Wikipedia-Eintrag für die zyklomatische Komplexität](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Vererbungs Tiefe** : gibt die Anzahl der verschiedenen Klassen an, die von einem anderen erben, bis hin zur Basisklasse. Die Vererbungs Tiefe ähnelt der Klassen Kopplung darin, dass sich eine Änderung in einer Basisklasse auf eine beliebige geerbte Klasse auswirken kann. Je höher diese Zahl ist, desto tiefer die Vererbung und desto höher ist das Potenzial für Basisklassen Änderungen, die zu einer Breaking Change führen. Bei einer tiefen Vererbung ist ein niedriger Wert gut, und ein hoher Wert ist schlecht.

- **Klassen Kopplung** : misst die Kopplung mit eindeutigen Klassen durch Parameter, lokale Variablen, Rückgabe Typen, Methodenaufrufe, generische oder Vorlagen Instanziierungen, Basisklassen, Schnittstellen Implementierungen, für externe Typen definierte Felder und die Attribut Ergänzung. Ein guter Software Entwurf legt fest, dass die Typen und Methoden eine hohe Kohäsion und eine geringe Kopplung aufweisen sollten. Hohe Kopplung weist auf einen Entwurf hin, der aufgrund der vielen Abhängigkeiten von anderen Typen schwierig zu verwenden und zu warten ist. Weitere Informationen finden Sie unter [Klassen Kopplung](code-metrics-class-coupling.md).

::: moniker range=">=vs-2019"

- **Zeilen des Quellcodes** : gibt die genaue Anzahl von Quell Codezeilen an, die in der Quelldatei vorhanden sind, einschließlich leerer Zeilen. Diese Metrik ist ab Visual Studio 2019 Version 16,4 und Microsoft. Code Analysis. Metrics (2.9.5) verfügbar.

- **Zeilen des ausführbaren Codes** : gibt die ungefähre Anzahl von ausführbaren Codezeilen oder Vorgängen an. Dies ist eine Anzahl von Vorgängen in ausführbarem Code. Diese Metrik ist ab Visual Studio 2019 Version 16,4 und Microsoft. Code Analysis. Metrics (2.9.5) verfügbar. Der Wert ist in der Regel eine genaue Entsprechung zur vorherigen Metrik, **Code Zeilen**, bei der es sich um die auf MSIL-Anweisungen basierende Metrik handelt, die im Legacy Modus verwendet wird.
::: moniker-end
::: moniker range="vs-2017"

- **Codezeilen** : gibt die ungefähre Anzahl von Zeilen im Code an. Die Anzahl basiert auf dem IL-Code und ist daher nicht die genaue Anzahl von Zeilen in der Quell Code Datei. Eine hohe Anzahl kann darauf hindeuten, dass ein Typ oder eine Methode versucht, zu viele Aufgaben zu erledigen und aufgeteilt zu werden. Es kann auch darauf hindeuten, dass der Typ oder die Methode möglicherweise schwierig zu verwalten ist.

   > [!NOTE]
   > Die [Befehlszeilenversion](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) des codemetriktools zählt tatsächliche Codezeilen, da der Quellcode anstelle von Il analysiert wird.
::: moniker-end

## <a name="anonymous-methods"></a>Anonymen Methoden

Eine *anonyme Methode* ist nur eine Methode, die über keinen Namen verfügt. Anonyme Methoden werden am häufigsten verwendet, um einen Codeblock als Delegatparameter zu übergeben. Codemetrikergebnisse für eine anonyme Methode, die in einem Member deklariert wird, z. b. eine Methode oder ein Accessor, werden dem Member zugeordnet, der die Methode deklariert. Sie sind nicht mit dem Member verknüpft, der die-Methode aufruft.

## <a name="generated-code"></a>Generierter Code

Einige Software Tools und Compiler generieren Code, der einem Projekt hinzugefügt wird und der vom Projektentwickler entweder nicht angezeigt wird oder nicht geändert werden darf. Größtenteils ignoriert Codemetriken generierten Code, wenn die Metrikwerte berechnet werden. Dadurch können die Metrikwerte angeben, was der Entwickler sehen und ändern kann.

Der für Windows Forms generierte Code wird nicht ignoriert, da es sich um einen Code handelt, den der Entwickler sehen und ändern kann.

## <a name="next-steps"></a>Nächste Schritte

- [Gewusst wie: Generieren von Codemetrikdaten](../code-quality/how-to-generate-code-metrics-data.md)
- [Verwenden des Fensters "Code Metrikergebnisse"](../code-quality/working-with-code-metrics-data.md)