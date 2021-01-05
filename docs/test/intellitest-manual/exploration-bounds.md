---
title: Durchsuchungsbegrenzungen | Microsoft IntelliTest-Test-Tool für Entwickler
description: PexSettingsAttributeBase ist die abstrakte Basisklasse zum Festlegen von Grenzen als Attribute. Hier erfahren Sie, wie Sie Einstellungen mithilfe von benannten Eigenschaften ändern.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 075eaa4613a1afe6bdeb83a9e46e639b073a200a
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2020
ms.locfileid: "97667922"
---
# <a name="exploration-bounds"></a>Durchsuchungsbegrenzungen

**PexSettingsAttributeBase** ist die abstrakte Basisklasse zum Festlegen von Grenzen als Attribute. Einen Überblick der Einstellungen in IntelliTest finden Sie unter [Einstellungswasserfall](settings-waterfall.md).

Sie können die Einstellungen anpassen, indem Sie deren benannte Eigenschaften und abgeleitete Attribute verwenden:

```csharp
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **Grenzen der Einschränkungs-Solver**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime): Die Sekundenzahl, die dem [Einschränkungs-Solver](input-generation.md#constraint-solver) zur Verfügung stehen, um die Eingaben zu finden, die dazu führen, dass neue und andere Ausführungspfade befolgt werden
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory): Die Größe in Megabyte, die der [ verwenden darf](input-generation.md#constraint-solver), um Eingaben zu finden
* **Grenzen des Explorationspfads**
  * [MaxBranches](#maxbranches): Die maximale Anzahl von Verzweigungen, die entlang eines einzelnen Ausführungspfads genommen werden können
  * [MaxCalls](#maxcalls): Die maximale Anzahl von Aufrufen, die während eines einzelnen Ausführungspfads durchgeführt werden können
  * [MaxStack](#maxstack): Die maximale Größe des Stapels während eines einzigen Ausführungspfads, gemessen als Anzahl der aktiven Aufrufframes
  * [MaxConditions](#maxconditions): Die maximale Anzahl von Bedingungen zu den Eingaben, die während eines einzelnen Ausführungspfads überprüft werden können
* **Durchsuchungsbegrenzungen**
  * [MaxRuns](#maxruns): Die maximale Anzahl von Ausführungen, die während einer Durchsuchung versucht werden
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests): Die maximale Anzahl aufeinanderfolgender Ausführungen, ohne dass ein neuer Test ausgegeben wird
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths): Die maximale Anzahl von Ausführungen mit einem eindeutigen Ausführungspfad, die während einer Durchsuchung versucht werden
  * [MaxExceptions](#maxexceptions): Die maximale Anzahl von Ausnahmen, die für eine Kombination aus allen gefundenen Ausführungspfade gefunden werden dürfen
* **Einstellungen für die Codegenerierung von Testsammlungen**
  * [TestExcludePathBoundsExceeded](#testexcludepathboundsexceeded): Wenn TRUE, werden Ausführungspfade, die die Grenzen des Pfads überschreiten ([MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), [MaxConditions](#maxconditions)) ignoriert.
  * [TestEmissionFilter](#testemissionfilter): Gibt an, unter welchen Umständen IntelliTest Tests ausgeben soll.
  * [TestEmissionBranchHits](#testemissionbranchhits): Steuert, wie viele Tests von IntelliTest ausgegeben werden

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

Die Sekundenzahl, die dem [Einschränkungs-Solver](input-generation.md#constraint-solver) zur Verfügung stehen, um die Eingaben zu berechnen, die dazu führen, dass neue und andere Ausführungspfade befolgt werden Dies ist eine Option von **PexSettingsAttributeBase** und dessen abgeleiteten Typen.

Je tiefer IntelliTest in den Ausführungspfad eines Programms vordringt, desto komplexer werden die Einschränkungssysteme, die IntelliTest aus dem Steuerungs- und Datenfluss des Programms erstellt. Je nach Ihrer Zeiteinschränkung können Sie diesen Wert festlegen, um IntelliTest mehr oder weniger Zeit zum Suchen neuer Ausführungspfade zu geben.

Normalerweise ist der Grund für ein Timeout, dass IntelliTest versucht, eine Projektmappe für ein Einschränkungssystem zu finden, das keine Projektmappe aufweist, was IntelliTest jedoch nicht bewusst ist. Weil dies der häufigste Grund für ein Timeout ist, kann es möglicherweise sinnlos sein, die Grenze zu erhöhen.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

Die Anzahl von Megabyte, die dem [Einschränkungs-Solver](input-generation.md#constraint-solver) zur Verfügung stehen, um die Eingaben zu berechnen, die dazu führen, dass neue und andere Ausführungspfade befolgt werden Dies ist eine Option von *PexSettingsAttributeBase** und dessen abgeleiteten Typen.

Je tiefer IntelliTest in den Ausführungspfad eines Programms vordringt, desto komplexer werden die Einschränkungssysteme, die IntelliTest aus dem Steuerungs- und Datenfluss des Programms erstellt. Je nach verfügbarem Speicherplatz auf Ihrem Computer können Sie diesen Wert festlegen, um es IntelliTest zu erlauben, sich mit komplexeren Einschränkungssystemen zu befassen.

Normalerweise ist der Grund für ein Timeout, dass IntelliTest versucht, eine Projektmappe für ein Einschränkungssystem zu finden, das keine Projektmappe aufweist, was IntelliTest jedoch nicht bewusst ist. Weil dies der häufigste Grund für ein Szenario mit zu wenig Speicherplatz ist, kann es möglicherweise sinnlos sein, die Grenze zu erhöhen.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

Die maximale Anzahl von Branches, die entlang eines Ausführungspfads genommen werden können.

Diese Durchsuchungsbegrenzung soll die Länge von Ausführungspfaden einschränken, die IntelliTest während einer [Eingabeerzeugung](input-generation.md) durchsucht. Insbesondere soll es verhindern, dass IntelliTest nicht mehr reagiert, wenn das Programm sich in einer Endlosschleife befindet.

Jeder bedingte und unbedingte Branch des ausgeführten und überwachten Codes wird in diese Einschränkung einbezogen. Dazu zählen auch Branches, die nicht von den Eingaben eines parametrisierten Test abhängen.

Der folgende Code verwendet z.B. Branches in einer Reihenfolge von 100:

```csharp
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

Die maximale Anzahl von Aufrufen, die während eines einzelnen Ausführungspfads durchgeführt werden können

Diese Durchsuchungsbegrenzung soll die Länge von Ausführungspfaden einschränken, die IntelliTest während einer [Eingabeerzeugung](input-generation.md) durchsucht. Dies verhindert insbesondere, dass IntelliTest nicht mehr reagiert, wenn das Programm eine Methode unendlich oft rekursiv aufruft, was zum Überlauf eines Stapels führt. Danach kann IntelliTest nicht mehr wiederhergestellt werden.

Jeder Aufruf (direkt, indirekt, virtuell, Springen) des ausgeführten und überwachten Codes wird in die Einschränkung einbezogen.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

Die maximale Größe des Stapels während eines einzigen Ausführungspfads, gemessen anhand der Anzahl der aktiven Aufrufframes

Diese Durchsuchungsbegrenzung soll die Größe des Stapels eines Ausführungspfads einschränken, den IntelliSense während einer [Eingabeerzeugung](input-generation.md) durchsucht. Dies soll insbesondere verhindern, dass IntelliTest allen verfügbaren Stapelplatz verwendet. Dies würde zu einem Stapelüberlauf führen, wodurch IntelliTest nicht mehr wiederhergestellt werden kann.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

Die maximale Anzahl von Bedingungen zu den Eingaben, die während eines einzelnen Ausführungspfads überprüft werden können

Diese Durchsuchungsbegrenzung soll die Komplexität von Ausführungspfaden einschränken, die IntelliTest während einer [Eingabeerzeugung](input-generation.md) durchsucht. Jeder bedingte Branch, der von den Eingaben des parametrisierten Test abhängt, wird in diese Einschränkung einbezogen.

Jeder Pfad im folgenden Code verwendet z.B. n + 1 Bedingungen:

```csharp
[PexMethod]
void ParameterizedTest(int n)
{
     for (int i=0; i<n; i++) { // conditions are "0<n", "1<n", ..., "!(n<n)"
          ...
     }
     for (int i=0; i<100; i++) { // irrelevant for MaxConditions, since conditions do not depend on input
          ...
     }
}
```

<a name="maxruns"></a>
## <a name="maxruns"></a>MaxRuns

Die maximale Anzahl von Ausführungen, die von IntelliTest während der Durchsuchung eines Tests versucht werden.

Diese Durchsuchungsbegrenzung soll IntelliTest während der [Eingabeerzeugung](input-generation.md) einschränken, da jeder Code, der Schleifen oder Rekursionen enthält, möglicherweise eine unendliche Anzahl von Ausführungspfaden enthält.

Die beiden Einstellungen **MaxRuns** und **MaxRunsWithUniquePaths** sind folgendermaßen miteinander verknüpft.

* IntelliTest ruft eine parametrisierte Testmethode so oft auf, wie von **MaxRuns** angegeben. Dabei werden unterschiedliche Testeingaben verwendet.
* Wenn der ausgeführte Code deterministisch ist, nimmt IntelliTest jedes Mal einen anderen Ausführungspfad. Unter bestimmten Umständen kann der ausgeführte Code jedoch einem Ausführungspfad folgen, den er bereits genommen hat, dann aber mit anderen Eingaben.
* IntelliTest zählt, wie viele eindeutige Ausführungspfade es findet. Diese Zahl wird durch die Option **MaxRunsWithUniquePaths** eingeschränkt.

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

Die maximale Anzahl aufeinanderfolgender Ausführungen, ohne dass ein neuer Test ausgegeben wird

Während IntelliTest oft viele interessante Testeingaben in kurzer Zeit findet, findet es jedoch nach längerer Zeit keine neuen Testeingaben mehr und gibt keine Komponententests mehr aus. Diese Konfigurationsoption legt einen Grenzwert für die Zahl der aufeinanderfolgenden Versuche fest, die IntelliTest durchführen kann, ohne neue Tests auszugeben. Wenn dieser Grenzwert erreicht wird, wird die Durchsuchung angehalten.

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

Die maximale Anzahl von eindeutigen Pfaden, die IntelliTest während einer Durchsuchung beachtet.

Diese Durchsuchungsbegrenzung soll IntelliTest während der [Eingabeerzeugung](input-generation.md) einschränken, da jeder Code, der Schleifen oder Rekursionen enthält, möglicherweise eine unendliche Anzahl von Ausführungspfaden enthält.

Die beiden Einstellungen **MaxRuns** und **MaxRunsWithUniquePaths** sind folgendermaßen miteinander verknüpft.

* IntelliTest ruft eine Methode eine parametrisierte Testmethode so oft auf, wie von **MaxRuns** angegeben. Dabei werden unterschiedliche Testeingaben verwendet.
* Wenn der ausgeführte Code deterministisch ist, nimmt IntelliTest jedes Mal einen anderen Ausführungspfad. Unter bestimmten Umständen kann der ausgeführte Code jedoch einem Ausführungspfad folgen, den er bereits genommen hat, dann aber mit anderen Eingaben.
* IntelliTest zählt, wie viele eindeutige Ausführungspfade es findet. Diese Zahl wird durch die Option **MaxRunsWithUniquePaths** eingeschränkt.

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

Die maximale Anzahl von Ausnahmen, die ausgelöst werden dürfen, bevor die Durchsuchung angehalten wird.

Diese Durchsuchungsbegrenzung soll das Durchsuchen von Code verhindern, der viele Fehler enthält. Wenn IntelliTest zu viele Fehler im Code findet, wird die Durchsuchung beendet.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

Ausführungspfade, die die konfigurierten Pfadbegrenzungen überschreiten, werden [MaxCalls](#maxcalls), [Max Branches](#maxbranches), [MaxStack](#maxstack) und [MaxConditions](#maxconditions) ignoriert.

Diese Durchsuchungsbegrenzung ist zum Behandeln von (hauptsächlich) nicht endenden Test gedacht. Wenn IntelliTest eine Durchsuchungsbegrenzung wie z.B. [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack) oder [MaxConditions](#maxconditions) erreicht, geht es davon aus, dass der Test kein nicht endender Prozess ist und verursacht später keinen Stapelüberlauf. Derartige Testfälle verursachen möglicherweise Probleme für andere Testframeworks. Dieses Attribut bietet eine Möglichkeit, um zu verhindern, dass IntelliTest Testfälle für potentielle nicht endende Prozesse oder Testfälle ausgibt, die zu einem Stapelüberfluss führen.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

Gibt die Testtypen an, die IntelliTest ausgeben soll. Mögliche Werte sind:

* **All**: Ausgeben von Tests für alles, einschließlich Annahmeverletzungen
* **FailuresAndIncreasedBranchHits** (Standard): Ausgeben von Tests für alle eindeutigen Fehler und immer dann, wenn ein Testfall die Coverage erhöht, wie von [TestEmissionBranchHits](#testemissionbranchhits) gesteuert
* **FailuresAndUniquePaths**: Ausgeben von Tests für alle von IntelliTest gefundenen Fehler sowie für jede Testeingabe, die einen eindeutigen Ausführungspfad verursacht
* **Failures**: Ausgeben von Test nur für Fehler

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

Je nach aktueller [TestEmissionFilter](#testemissionfilter)-Einstellung gibt IntelliTest neue Testfälle aus, wenn diese einen Branch im Programm abdecken, der vorher nicht abgedeckt wurde.

Die Einstellung **TestEmissionBranchHits** legt fest, ob IntelliTest nur darauf achten soll, ob ein Branch überhaupt abgedeckt wurde (**TestEmissionBranchHits=1**) oder ob ein Test ihn ein- oder zweimal abgedeckt hat (**TestEmissionBranchHits=2**) usw.

**TestEmissionBranchHits=1** erzeugt eine sehr kleine Testsammlung, die alle Branches abdeckt, die IntelliTest erreichen konnte. Diese Testsammlung deckt insbesondere alle grundlegenden Blöcke und Anweisungen ab, die es erreicht hat.

Die Standardeinstellung ist **TestEmissionBranchHits=2**, welche eine ausdrucksstärkere Testsammlung generiert, die sich zudem besser zum Erkennen zukünftiger Regressionsfehler eignet.

## <a name="got-feedback"></a>Sie haben Fragen oder Anmerkungen?

Posten Sie Ihre Ideen und Featureanfragen in der [Entwicklercommunity](https://aka.ms/feedback/suggest?space=8).
