---
title: Testgenerierung | Microsoft IntelliTest-Test-Tool für Entwickler
description: Hier erfahren Sie, wie IntelliTest Testfälle aus den Methoden Ihrer Implementierung generiert, dann Eingaben für die Methoden erzeugt und Assertionen für die Daten überprüft.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Test generation
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 790146e3014765224f22bd247732c7ac3f062269
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329444"
---
# <a name="test-generation"></a>Testerzeugung

Unittests haben in der Regel die folgenden Bestandteile:

* Eine [Sequenz von Methodenaufrufen](test-generation.md#test-generators)
* Die Argumente, mit denen die Methoden aufgerufen werden, wobei die Argumente [Testeingaben](input-generation.md) sind
* Überprüfung des beabsichtigten Verhaltens der getesteten Anwendung, indem eine Reihe von [Assertionen](#assumptions-and-assertions) angegeben wird

Im Folgenden finden Sie eine Beispielteststruktur:

```csharp
[Test]
void MyTest() {
    // data
    ArrayList a = new ArrayList();

    // method sequence
    a.Add(5);

    // assertions
    Assert.IsTrue(a.Count==1);
    Assert.AreEqual(a[0], 5);
}
```

IntelliTest kann relevante Argumentwerte für allgemeinere [parametrisierte Unittests](#parameterized-unit-testing), in welchen die Sequenz der Methodenaufrufe und Assertionen angegeben werden, häufig automatisch bestimmen.

<a name="test-generators"></a>
## <a name="test-generators"></a>Testgeneratoren

IntelliTest generiert Testfälle, indem es eine Sequenz von Methoden der zu testenden Implementierung zum Ausführen auswählt, und dann Eingaben für die Methoden generiert, während es Assertionen zu den abgeleiteten Daten überprüft.

Ein [parametrisierter Unittest](#parameterized-unit-testing) gibt in seinem Text direkt eine Sequenz von Methodenaufrufen an.

Wenn IntelliTest Objekte erstellen muss, werden der Sequenz nach Bedarf automatisch Aufrufe an die Konstruktoren und Factorymethoden hinzugefügt.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Parametrisierte Unittests

*Parametrisierte Unittests* (PUTs) sind Tests, die Parameter annehmen. Im Gegensatz zu herkömmlichen Unittests, bei denen es sich in der Regel um geschlossene Methoden handelt, nehmen PUTs einen beliebigen Satz von Parametern an. Ist es wirklich so einfach? Ja: von dort aus versucht IntelliTest, [die (minimale) Gruppe der Eingaben zu generieren](input-generation.md), die den aus dem Test erreichbaren Code [vollständig abdecken](input-generation.md#dynamic-code-coverage).

PUTs werden mit dem benutzerdefinierten [PexMethod](attribute-glossary.md#pexmethod)-Attribut definiert, ähnlich wie MSTest (oder NUnit, xUnit). PUTs sind Instanzmethoden, die logisch in Klassen gruppiert sind, die mit [PexClass](attribute-glossary.md#pexclass) markiert wurden. Das folgende Beispiel zeigt einen einfachen PUT, der in der **MyPexTest**-Klasse gespeichert ist:

```csharp
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

wobei **ReplaceFirstChar** eine Methode ist, die das erste Zeichen einer Zeichenfolge ersetzt:

```csharp
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

Aus diesen Test kann IntelliTest für einen PUT, die viele Ausführungspfade des getesteten Codes abdeckt, automatisch [Eingaben generieren](input-generation.md). Jede Eingabe, die einen unterschiedlichen Ausführungspfad abdeckt, wird als ein Unittest „serialisiert“:

```csharp
[TestMethod, ExpectedException(typeof(ArgumentNullException))]
void ReplaceFirstChar0() {
    this.ReplaceFirstChar(null, 0);
}
...
[TestMethod]
void ReplaceFirstChar10() {
    this.ReplaceFirstChar("a", 'c');
}
```

<a name="generic-parameterized"></a>
## <a name="generic-parameterized-unit-testing"></a>Generische parametrisierte Unittests

Parametrisierte Unittests können generische Methoden sein. In diesem Fall muss der Benutzer die verwendeten Typen angeben, um die Methode mit [PexGenericArguments](attribute-glossary.md#pexgenericarguments) zu instanziieren.

```csharp
[PexClass]
public partial class ListTest {
    [PexMethod]
    [PexGenericArguments(typeof(int))]
    [PexGenericArguments(typeof(object))]
    public void AddItem<T>(List<T> list, T value)
    { ... }
}
```

<a name="allowing-exceptions"></a>
## <a name="allowing-exceptions"></a>Zulassen von Ausnahmen

IntelliTest bietet zahlreiche Validierungsattribute, um bei der Selektierung der Ausnahmen in erwarteten Ausnahmen und unerwartete Ausnahmen zu helfen.

Erwartete Ausnahmen generieren negative Testfälle mit den entsprechenden Anmerkungen wie z.B. **ExpectedException(typeof(*xxx*))**, während unerwartete Ausnahmen fehlgeschlagene Testfälle generieren.

```csharp
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

Die Validierungssteuerelemente sind:

* [PexAllowedException](attribute-glossary.md#pexallowedexception): ermöglicht einen bestimmten Ausnahmetyp von überall aus
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly): ermöglicht einen bestimmten Ausnahmetyp aus einer angegebenen Assembly
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype): ermöglicht einen bestimmten Ausnahmetyp aus einem angegebenen Typ
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest): ermöglicht einen bestimmten Ausnahmetyp aus dem getesteten Typ

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>Testen von internen Typen

IntelliTest kann interne Typen „testen“, sofern sie angezeigt werden können. Damit IntelliTest die folgenden Typen erkennen kann, wird das folgende Attribut Ihrem Produkt oder Testprojekt von den Visual Studio-IntelliTest-Assistenten hinzugefügt:

```csharp
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293")]
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Annahmen und Assertionen

Benutzer können Annahmen und Assertionen verwenden, um [Vorbedingungen](#precondition) (Annahmen) und [Nachbedingungen](#postcondition) (Assertionen) zu ihren Tests auszudrücken. Wenn IntelliTest einen Satz von Parameterwerten generiert und den Code „untersucht“, könnte möglicherweise eine Annahme des Tests verletzt werden. In diesem Fall wird für diesen Pfad kein Test generiert, sondern er wird ohne Benachrichtigung ignoriert.

Assertionen sind ein bekanntes Konzept in regulären Unittest-Frameworks, weshalb IntelliTest die integrierten **Assert**-Klassen, die von jedem unterstützten Testframework bereitgestellt werden, bereits „versteht“. Die meisten Frameworks stellen jedoch keine **Assume**-Klasse zur Verfügung. In diesem Fall stellt IntelliTest die [PexAssume](static-helper-classes.md#pexassume)-Klasse zur Verfügung. Wenn Sie kein bereits vorhandenes Testframework verwenden, verfügt IntelliTest auch über die [PexAssert](static-helper-classes.md#pexassert)-Klasse.

```csharp
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

Insbesondere kann die „Non-Nullness“-Annahme („Nicht-NULL“-Annahme) als benutzerdefiniertes Attribut codiert werden:

```csharp
[PexMethod]
public void Test2([PexAssumeNotNull] object o)
// precondition: o should not be null
{
   ...
}
```

<a name="precondition"></a>
## <a name="precondition"></a>Precondition

Eine Vorbedingung einer Methode drückt die Bedingungen aus, unter denen die Methode erfolgreich ausgeführt wird.

In der Regel wird die Vorbedingung durch Überprüfen der Parameter und des Objektzustands, und, wenn sie verletzt wird, durch Auslösen einer **ArgumentException** oder **InvalidOperationException** erzwungen.

In IntelliTest wird eine Vorbedingung eines [parametrisierten Unittests](#parameterized-unit-testing) mit [PexAssume](static-helper-classes.md#pexassume) ausgedrückt.

<a name="postcondition"></a>
## <a name="postcondition"></a>Nachbedingung

Eine Nachbedingung einer Methode drückt die Bedingungen aus, die während und nach der Ausführung der Methode gelten sollen, vorausgesetzt, dass die Vorbedingungen gültig sind.

Die Nachbedingung wird in der Regel durch Aufrufe an **Assert**-Methoden erzwungen.

In IntelliTest wird eine Nachbedingung eines [parametrisierten Unittests](#parameterized-unit-testing) mit [PexAssert](static-helper-classes.md#pexassert) ausgedrückt.

<a name="test-failures"></a>
## <a name="test-failures"></a>Fehlgeschlagenen Tests
Wann schlägt ein generierter Test fehl?

1. Wenn er nicht innerhalb der [konfigurierten Pfadgrenzen](exploration-bounds.md) beendet wird, wird er als fehlgeschlagen betrachtet, es sei denn, die Option [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded) wurde festgelegt

1. Wenn der Test eine **PexAssumeFailedException** auslöst, ist er erfolgreich. Allerdings wird er in der Regel herausgefiltert, es sei denn, [TestEmissionFilter](exploration-bounds.md#testemissionfilter) ist auf **Alle** festgelegt

1. Wenn der Test eine [Assertion](#assumptions-and-assertions) verletzt, z.B. durch Auslösen einer Assertionsverletzungsausnahme eines Unittestframeworks, schlägt er fehl

Wenn keiner der oben genannten Fälle eine Entscheidung erzeugt, ist ein Test nur dann erfolgreich, wenn er keine Ausnahme auslöst. Assertionsverstöße werden auf die gleiche Weise wie Ausnahmen behandelt.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Einrichtung und Löschung

Im Rahmen der Integration mit Testframeworks unterstützt IntelliTest das Erkennen und Ausführen von Setup- und Löschmethoden.

**Beispiel**

```csharp
using Microsoft.Pex.Framework;
using NUnit.Framework;

namespace MyTests
{
    [PexClass]
    [TestFixture]
    public partial class MyTestClass
    {
        [SetUp]
        public void Init()
        {
            // monitored
        }

        [PexMethod]
        public void MyTest(int i)
        {
        }

        [TearDown]
        public void Dispose()
        {
            // monitored
        }
    }
}
```

<a name="further-reading"></a>
## <a name="further-reading"></a>Weitere nützliche Informationen

* [Test to code binding (Bindung eines Tests an Code)](https://devblogs.microsoft.com/devops/smart-unit-tests-test-to-code-binding-test-case-management/)
* [One Test to rule them all (IntelliTest – Ein Test für alle)](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>Sie haben Fragen oder Anmerkungen?

Posten Sie Ihre Ideen und Featureanfragen in der [Entwicklercommunity](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
