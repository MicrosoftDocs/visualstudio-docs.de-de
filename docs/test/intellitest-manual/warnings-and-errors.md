---
title: Warnungen und Fehler | Microsoft IntelliTest-Test-Tool für Entwickler
description: Dieser Artikel enthält nach Kategorie sortierte IntelliTest-Warnungen und -Fehler und Beschreibungen zu den einzelnen Warnungen und Fehlern.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Warnings and errors
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 69fea3216602bf78084ef9141280fd4ba7aa4c57
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920411"
---
# <a name="warnings-and-errors"></a>Warnungen und Fehler

## <a name="warnings-and-errors-by-category"></a>Warnungen und Fehler nach Kategorie

* **Standortgrenzen**
  * [MaxBranches überschritten](#maxbranches-exceeded)
  * [MaxConstraintSolverTime überschritten](#maxconstraintsolvertime-exceeded)
  * [MaxConditions überschritten](#maxconditions-exceeded)
  * [MaxCalls überschritten](#maxcalls-exceeded)
  * [MaxStack überschritten](#maxstack-exceeded)
  * [MaxRuns überschritten](#maxruns-exceeded)
  * [MaxRunsWithoutNewTests überschritten](#maxrunswithoutnewtests-exceeded)

* **Auflösen von Einschränkung**
  * [Die Lösung kann nicht konkretisiert werden](#cannot-concretize-solution)

* **Domänen oder Runtime**
  * [Benötigen Sie Hilfe bei der Objekterstellung?](#help-construct)
  * [Benötigen Sie Hilfe beim Suchen von Typen?](#help-types)
  * [Verwendbaren Typ erraten](#usable-type-guessed)

* **Ausführung**
  * [Unerwarteter Fehler während der Durchsuchung](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)

* **Instrumentation**
  * [Nicht instrumentierte aufgerufene Methode](#uninstrumented-method-called)
  * [Externe aufgerufene Methode](#external-method-called)
  * [Nicht instrumentierbare aufgerufene Methode](#uninstrumentable-method-called)
  * [Probleme mit der Testfähigkeit](#testability-issue)
  * [Einschränkung](#limitation)

* **Interpreter**
  * [Erkannter Aufrufkonflikt](#observed-call-mismatch)
  * [In einem statischen Feld gespeicherter Wert](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>MaxBranches überschritten

IntelliTest begrenzt die Länge eines jeden Ausführungspfads, den es während einer [Eingabeerzeugung](input-generation.md) durchsucht. Diese Funktion soll verhindern, dass IntelliTest nicht mehr reagiert, wenn das Programm sich in einer Endlosschleife befindet.

Jeder bedingte und unbedingte Branch des ausgeführten und überwachten Codes wird in diese Einschränkung einbezogen. Dazu zählen auch Branches, die nicht von den Eingaben eines [parametrisierten Unittest](test-generation.md#parameterized-unit-testing) abhängen.

Der folgende Code verwendet z.B. Branches in einer Reihenfolge von 100:

```csharp
for (int i=0; i<100; i++) { }
```

Sie können die Option **MaxBranches** eines von **PexSettingsAttributeBase** abgeleiteten Attributs bearbeiten, wie z.B. [PexClass](attribute-glossary.md#pexclass) oder [PexMethod](attribute-glossary.md#pexmethod). In folgendem Beispiel wird diese Grenze effektiv entfernt:

```csharp
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Sie können auch die Option **TestExcludePathBoundsExceeded** festlegen, um IntelliTest zu sagen, wie es mit diesen Problemen umgehen soll.

Sie können [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) im Testcode verwenden, um von der Schleifenbedingung generierte Einschränkungen zu ignorieren:

```csharp
for (int i=0;
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++)
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>MaxConstraintSolverTime exceeded

IntelliTest verwendet einen [Einschränkungs-Solver](input-generation.md#constraint-solver), um neue Testeingaben zu berechnen. Das Lösen von Einschränkungen kann ein sehr zeitaufwendiger Prozess sein, weshalb IntelliTest es Ihnen ermöglicht, Grenzen zu konfigurieren – insbesondere **MaxConstraintSolverTime**.

Bei vielen Anwendungen führt das deutlichen Erhöhen des Timeouts jedoch nicht zu besserer Codeabdeckung. Dies liegt daran, dass die meisten Timeouts von Einschränkungssystemen verursacht werden, für die es keine Lösungen gibt. IntelliTest kann jedoch möglicherweise nicht bestimmen, dass es inkonsistent ist, ohne alle möglichen Lösungen auszuprobieren, was zu einem Timeout führt.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>MaxConditions überschritten

IntelliTest begrenzt die Länge eines jeden Ausführungspfads, den es während einer [Eingabeerzeugung](input-generation.md) durchsucht. Diese Funktion soll verhindern, dass IntelliTest nicht mehr reagiert, wenn das Programm in eine Endlosschleife eintritt.

Jeder bedingte Branch, der von den Eingaben des [parametrisierten Unittest](test-generation.md#parameterized-unit-testing) abhängt, wird in diese Einschränkung einbezogen.

Jeder Pfad im folgenden Code verwendet z.B. **n + 1** Bedingungen:

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    // conditions are "0<n", "1<n", ..., "!(n<n)"
    for (int i=0; i<n; i++)
    { ... }

    // irrelevant for MaxConditions, since conditions do not depend on input
    for (int i=0; i<100; i++)
    { ... }
}
```

Sie können die Option **MaxConditions** eines von **PexSettingsAttributeBase** abgeleiteten Attributs bearbeiten, wie z.B. [PexClass](attribute-glossary.md#pexclass) oder [PexMethod](attribute-glossary.md#pexmethod). Zum Beispiel:

```csharp
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

Sie können auch die Option **TestExcludePathBoundsExceeded** festlegen, um IntelliTest zu sagen, wie es mit diesen Problemen umgehen soll.

Sie können [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) verwenden, um von der Schleifenbedingung generierte Einschränkungen zu ignorieren:

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    int nshadow = PexSymbolicValue.Ignore(n); // IntelliTest looses track of 'n'

    // irrevelant for MaxConditions, since nshadow is not related to input
    for (int i=0; i<nshadow; i++)
    {...}
}
```

<a name="maxcalls-exceeded"></a>
## <a name="maxcalls-exceeded"></a>MaxCalls überschritten

IntelliTest begrenzt die Länge eines jeden Ausführungspfads, den es während einer [Eingabeerzeugung](input-generation.md) durchsucht. Diese Funktion soll verhindern, dass IntelliTest nicht mehr reagiert, wenn das Programm in eine Endlosschleife eintritt.

Jeder Aufruf (direkt, indirekt, virtuell, Springen) des ausgeführten und überwachten Codes wird in die Einschränkung einbezogen.

Sie können die Option **MaxCalls** eines von **PexSettingsAttributeBase** abgeleiteten Attributs bearbeiten, wie z.B. [PexClass](attribute-glossary.md#pexclass) oder [PexMethod](attribute-glossary.md#pexmethod). In folgendem Beispiel wird diese Grenze effektiv entfernt:

```csharp
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Sie können auch die Option **TestExcludePathBoundsExceeded** festlegen, um IntelliTest zu sagen, wie es mit diesen Problemen umgehen soll.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>MaxStack überschritten

IntelliTest begrenzt die Größe des Aufrufstapels jedes Ausführungspfads, den es während einer [Eingabeerzeugung](input-generation.md) durchsucht. Diese Funktion verhindert, dass IntelliTest beendet wird, wenn es zu einem Stapelüberlauf kommt.

Sie können die Option **MaxStack** eines von **PexSettingsAttributeBase** abgeleiteten Attributs bearbeiten, wie z.B. [PexClass](attribute-glossary.md#pexclass) oder [PexMethod](attribute-glossary.md#pexmethod). In folgendem Beispiel wird diese Grenze effektiv entfernt (nicht empfohlen):

```csharp
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Sie können auch die Option **TestExcludePathBoundsExceeded** festlegen, um IntelliTest zu sagen, wie es mit diesen Problemen umgehen soll.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>MaxRuns überschritten

IntelliTest begrenzt die Zahl der Ausführungspfade, die es während einer [Eingabeerzeugung](input-generation.md) durchsucht. Diese Funktion stellt sicher, dass IntelliTest beendet wird, wenn das Programm Schleifen oder Rekursionen hat.

Möglicherweise gibt IntelliTest nicht nach jedem ausgeführten parametrisierten Test mit einer bestimmten Eingabe auch einen neuen Testfall aus. Weitere Informationen finden Sie unter [TestEmissionFilter](exploration-bounds.md#testemissionfilter).

Sie können die Option **MaxRuns** eines von **PexSettingsAttributeBase** abgeleiteten Attributs bearbeiten, wie z.B. [PexClass](attribute-glossary.md#pexclass) oder [PexMethod](attribute-glossary.md#pexmethod). In folgendem Beispiel wird diese Grenze effektiv entfernt (nicht empfohlen):

```csharp
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>MaxRunsWithoutNewTests überschritten

IntelliTest begrenzt die Zahl der Ausführungspfade, die es während einer [Eingabeerzeugung](input-generation.md) durchsucht. Diese Funktion stellt sicher, dass IntelliTest beendet wird, wenn das Programm Schleifen oder Rekursionen hat.

Möglicherweise gibt IntelliTest nicht nach jedem ausgeführten parametrisierten Test mit einer bestimmten Eingabe auch einen neuen Testfall aus. Weitere Informationen finden Sie unter [TestEmissionFilter](exploration-bounds.md#testemissionfilter).

Möglicherweise findet IntelliTest anfänglich viele interessante Testeingaben, aber gibt nach einer Weile möglicherweise keine Tests mehr aus. Diese Option bestimmt, wie lange IntelliTest nach einer weiteren relevanten Testeingabe suchen darf.

Sie können die Option **MaxRunsWithoutNewTests** eines von **PexSettingsAttributeBase** abgeleiteten Attributs bearbeiten, wie z.B. [PexClass](attribute-glossary.md#pexclass) oder [PexMethod](attribute-glossary.md#pexmethod). In folgendem Beispiel wird diese Grenze effektiv entfernt (nicht empfohlen):

```csharp
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>Die Lösung kann nicht konkretisiert werden

Dieser Fehler ist häufig eine Folge eines früheren Fehlers. IntelliTest verwendet einen [Einschränkungs-Solver](input-generation.md#constraint-solver), um neue Testeingaben zu bestimmen. Manchmal sind vom [Einschränkungs-Solver](input-generation.md#constraint-solver) vorgeschlagene Testeingaben ungültig. Dies kann passieren, wenn:

* bestimmte Einschränkungen unbekannt sind
* Werte auf vom Benutzer definierte Weise erstellt werden, sodass Fehler im Benutzercode auftreten
* einige der involvierten Typen Initialisierungslogik aufweisen, die nicht von IntelliTest gesteuert wird (z.B. COM-Klassen)

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Benötigen Sie Hilfe bei der Objekterstellung?

IntelliTest [generiert Testeingaben](input-generation.md), und einige der Eingaben sind möglicherweise Objekte mit Feldern.
Hier versucht IntelliTest eine Instanz einer Klasse zu generieren, die ein privates Feld hat, und es geht davon aus, dass ein interessantes Programmverhalten auftritt, wenn dieses private Feld einen bestimmten Wert hat.

Obwohl dies mit der Reflektion möglich ist, erstellt IntelliTest keine Objekte mit arbiträren Feldwerten.
In diesen Fällen verlässt es sich stattdessen darauf, dass der Benutzer Hinweise gibt, wie die öffentlichen Methoden einer Klasse verwendet werden sollen, um ein Objekt zu erstellen und es in einen Zustand zu versetzen, in dem sein privates Feld den gewünschten Wert enthält.

Lesen Sie den Artikeln zum [Instanziieren vorhandener Klassen](input-generation.md#existing-classes), um zu erfahren, wie Sie IntelliTest beim Konstruieren interessanter Objekte unterstützen können.

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Benötigen Sie Hilfe beim Suchen von Typen?

IntelliTest [generiert Testeingaben](input-generation.md) für jeden .NET-Typen. Hier versucht IntelliTest eine Instanz zu erstellen, die von einer abstrakten Klasse abgeleitet wird oder eine abstrakte Schnittstelle implementiert, und IntelliTest kennt keinen Typ, der die Einschränkungen erfüllt.

Sie können IntelliTest helfen, indem Sie auf mindestens einen Typ zeigen, der den Einschränkungen entspricht. Normalerweise hilft eines der folgenden Attribute:

* **PexUseTypeAttribute**, das auf einen bestimmten Typ zeigt.

  Wenn IntelliTest z.B. meldet, dass es „von keinen Typen weiß, die **System.Collections.IDictionary** zugewiesen werden können“, können Sie ihm helfen, indem Sie das folgende **PexUseTypeAttribute** dem Test anfügen (oder der fixture-Klasse):

  ```csharp
  [PexMethod]
  [PexUseType(typeof(System.Collections.Hashtable))]
  public void MyTest(IDictionary[] dictionaries) { ... }
  ```

* **Ein Attribut auf Assemblyebene**

  ```csharp
  [assembly: PexUseType(typeof(System.Collections.Hashtable))]
  ```

<a name="usable-type-guessed"></a>
## <a name="usable-type-guessed"></a>Verwendbaren Typ erraten

IntelliTest [generiert Testeingaben](input-generation.md) für jeden .NET-Typen. Wenn ein Typ abstrakt oder eine Schnittstelle ist, muss IntelliTest eine bestimmte Implementierung des Typs auswählen. Um diese Wahl treffen zu können, muss es wissen, welche Typen existieren.

Wenn diese Warnung angezeigt wird, gibt dies an, dass sich IntelliTest einige der Assemblys angesehen hat, auf die verwiesen wird, und einen Implementierungstyp gefunden hat, sich aber nicht sicher ist, ob es diesen Typen verwenden soll oder ob es an anderer Stelle besser passende Typen gibt. IntelliTest hat einfach einen vielversprechenden Typen ausgewählt.

Um diese Warnung zu vermeiden, können Sie entweder die Typwahl von IntelliTest akzeptieren oder IntelliTest beim Verwenden anderer Typen helfen, indem Sie einen entsprechenden [PexUseType](attribute-glossary.md#pexusetype) hinzufügen.

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>Unerwarteter Fehler während der Durchsuchung

Eine unerwartete Ausnahme wurde während der Durchsuchung eines Tests abgefangen.

Bitte [melden Sie dies als Fehler](#report-bug).

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException

Eine Ausnahme ist im Benutzercode aufgetreten. Inspizieren Sie die Stapelüberwachung, und entfernen Sie den Fehle in Ihrem Code.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>Nicht instrumentierte aufgerufene Methode

IntelliTest [generiert Testeingaben](input-generation.md), indem es die Programmausführung überwacht. Es ist unerlässlich, dass der relevante Code ordnungsgemäß instrumentiert ist, sodass IntelliTest dessen Verhalten überwachen kann.

Diese Warnung wird angezeigt, wenn der instrumentierte Code Methoden in einer andere, nicht instrumentierten Assembly aufruft.
Wenn Sie möchten, dass IntelliTest die Interaktion beider durchsucht, müssen Sie die andere Assembly auch instrumentieren (oder zumindest Teile davon).

<a name="external-method-called"></a>
## <a name="external-method-called"></a>Externe aufgerufene Methode

IntelliTest [generiert Testeingaben](input-generation.md), indem es die Ausführung von .NET-Anwendungen überwacht.
IntelliTest kann keine aussagekräftigen Testeingaben für Code generieren, der nicht in einer .NET-Sprache geschrieben ist.

Diese Warnung wird angezeigt, wenn der instrumentierte Code eine nicht verwaltete, native Methode aufruft, die IntelliTest nicht analysieren kann. Wenn Sie möchte, dass IntelliTest die Interaktion beider durchsucht, müssen Sie ein Pseudoobjekt für die nicht verwaltete Methode erstellen.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>Nicht instrumentierbare aufgerufene Methode

IntelliTest [generiert Testeingaben](input-generation.md), indem es die Ausführung von .NET-Anwendungen überwacht. Es gibt allerdings einige Methoden, die IntelliTest aus technischen Gründen nicht überwachen kann. IntelliTest kann z.B. keinen statischen Konstruktor überwachen.

Diese Warnung wird angezeigt, wenn der instrumentierte Code eine Methode aufruft, die IntelliTest nicht überwachen kann.

<a name="testability-issue"></a>
## <a name="testability-issue"></a>Probleme mit der Testfähigkeit

IntelliTest [generiert Testeingaben](input-generation.md), indem es die Programmausführung überwacht. Es kann nur relevante Testeingaben erzeugen, wenn das Programm deterministisch ist und wenn das relevante Verhalten von den Testeingaben gesteuert wird.

Diese Warnung wird angezeigt, weil eine Methode während der Ausführung Ihres Testfalls aufgerufen wurde, die sich entweder nicht deterministisch verhält oder die mit der Umgebung interagiert. Dies können z.B. Methoden von **System.Random** oder **System.IO.File** sein. Wenn Sie möchten, dass IntelliTest aussagekräftige Testeingaben erstellt, müssen Sie ein Pseudoobjekt für die Methode erstellen.

<a name="limitation"></a>
## <a name="limitation"></a>Einschränkung

IntelliTest [generiert Testeingaben](input-generation.md) mit einem [Einschränkungs-Solver](input-generation.md#constraint-solver).
Es gibt jedoch einige Vorgänge, die sich außerhalb des Bereichs des [Einschränkungs-Solver](input-generation.md#constraint-solver) befinden.
Dazu zählen aktuell:

* die meisten Vorgänge mit Gleitkommas (es wird nur ein geringer Anteil an linearer Arithmetik für Gleitkommazahlen unterstützt)
* Konvertierungen zwischen Gleitkommazahlen und ganzen Zahlen
* alle Vorgänge mit dem Typ **System.Decimal**

Diese Warnung wird angezeigt, wenn der ausgeführte Code einen Vorgang oder Aufruf einer Methode durchführt, die IntelliTest nicht interpretieren kann.

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>Erkannter Aufrufkonflikt

IntelliTest [generiert Testeingaben](input-generation.md), indem es die Programmausführung überwacht. Allerdings kann es sein, dass IntelliTest nicht all Anweisungen überwachen kann. Es kann z.B. keinen nativen Code und keinen nicht instrumentierten Code überwachen.

Wenn IntelliTest Code nicht überwachen kann, kann es auch keine für diesen Code relevanten Testeingaben erzeugen.
Häufig ist IntelliTest nicht bewusst, dass es eine Methode nicht überwachen kann, bis ein Aufruf dieser Methode etwas zurückgibt. Der Grund für diese Warnung ist:

* IntelliTest hat Code überwacht, der einen Aufruf einer nicht instrumentierten Methode initiiert hat.
* Die nicht instrumentierte Methode hat eine Methode aufgerufen, die instrumentiert ist.
* IntelliTest überwacht die instrumentierte Methode, die aufgerufen wurde.

IntelliTest weiß nicht, was die nicht instrumentierte Zwischenmethode gemacht hat, sodass es möglicherweise keine Testeingaben generieren kann, die für diesen geschachtelten, instrumentierten Aufruf relevant sind.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>In einem statischen Feld gespeicherter Wert

IntelliTest kann nur dann systematisch [relevante Testeingaben](input-generation.md) bestimmen, wenn der Unittest deterministisch ist, dass er sich also bei den gleichen Testeingaben immer gleich verhält. Insbesondere bedeutet dies, dass der Test das System in einen Zustand versetzen sollte, der das erneute Ausführen des Tests ermöglicht.
Idealerweise sollte der Unittest keinen globalen Zustand verändern, sondern es sollten Pseudooobjekte für alle Interaktionen mit globalen Elementen erstellt werden.

Diese Warnung gibt an, dass ein statisches Feld geändert wurde. Dadurch verhält sich der Test möglicherweise nicht deterministisch.

In einigen Situationen ist das Ändern eines statischen Feld akzeptabel:

* wenn die Testeingaben dazu führen, dass Setup- oder Bereinigungscode die Änderungen rückgängig macht
* wenn das Feld nur einmal initiiert wird, und sich der Wert anschließend nicht ändert

<a name="report-bug"></a>

## <a name="got-feedback"></a>Sie haben Fragen oder Anmerkungen?

Posten Sie Ihre Ideen und Featureanfragen in der [Entwicklercommunity](https://aka.ms/feedback/suggest?space=8).
