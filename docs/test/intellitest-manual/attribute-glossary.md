---
title: Attributglossar | Microsoft IntelliTest-Test-Tool für Entwickler
description: Dieser Artikel enthält eine nach Namespace sortierte Liste der IntelliTest-Attribute sowie Details zu diesen.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 8c356893b0c9716374950df3edc3dc480f022100
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330224"
---
# <a name="attribute-glossary"></a>Attributglossar

## <a name="attributes-by-namespace"></a>Attribute nach Namespace

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
    * [PexExplorationAttributeBase](#pexexplorationattributebase)

* **Microsoft.Pex.Framework.Settings**
  * [PexAssemblySettings](#pexassemblysettings)

* **Microsoft.Pex.Framework.Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)

* **Microsoft.Pex.Framework.Using**
  * [PexUseType](#pexusetype)

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Dieses Attribut gibt an, dass der zugehörige Wert nicht **NULL** sein darf. Es kann folgenden Objekten zugeordnet werden:

* einem **Parameter** einer parametrisierten Testmethode

  ```csharp
  // assume foo is not null
  [PexMethod]
  public void SomeTest([PexAssumeNotNull]IFoo foo, ...) {}
  ```

* einem **Feld**

  ```csharp
  public class Foo {
     // this field should not be null
     [PexAssumeNotNull]
     public object Bar;
  }
  ```

* einem **Typ**

  ```csharp
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

Es kann auch an eine Testassembly, Testfixierung oder Testmethode angefügt werden; in diesem Fall müssen die ersten Argumente angeben, für welches Feld oder welchen Typ die Annahmen gelten. Wenn das Attribut für einen Typ gilt, dann gilt es für alle Felder mit diesem formalen Typ.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Dieses Attribut markiert eine Klasse, die *Durchsuchungsvorgänge* enthält. Dies entspricht dem **TestClassAttribute** von MSTest (oder dem **TestFixtureAttribute** von NUnit). Dieses Attribut ist optional.

Die mit [PexClass](#pexclass) markierten Klassen müssen *standardmäßig konstruierbar* sein:

* öffentlich exportierter Typ
* Standardkonstruktor
* nicht abstrakt

Wenn die Klasse diese Anforderungen nicht erfüllt, wird ein Fehler gemeldet, und das Durchsuchen schlägt fehl.

Es wird auch dringend empfohlen, diese Klassen **partiell** zu machen, damit IntelliTest neue Tests generieren kann, die Teil der Klasse sind, sich aber in einer separaten Datei befinden. Dieser Ansatz löst aufgrund der [Sichtbarkeit](input-generation.md#visibility) viele Probleme und ist ein übliches Verfahren in C#.

**Zusätzliche Sammlung und Kategorien**:

```csharp
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Angeben des getesteten Typs**:

```csharp
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

Die Klasse enthält möglicherweise Methoden, die mit [PexMethod](#pexmethod) versehen wurden. IntelliTest erkennt auch [Einrichtungs- und Löschmethoden](test-generation.md#setup-teardown).

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Dieses Attribut bietet ein Typtupel für die Instanziierung eines [generischen parametrisierten Unittests](test-generation.md#generic-parameterized).

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Dieses Attribut kennzeichnet eine Methode als [parametrisierten Unittest](test-generation.md#parameterized-unit-testing).
Die Methode muss sich in einer Klasse befinden, die mit dem [PexClass](#pexclass)-Attribut markiert ist.

IntelliTest generiert herkömmliche, parameterlose Tests, die den [parametrisierten Unittest](test-generation.md#parameterized-unit-testing) mit verschiedenen Parametern aufrufen.

Der parametrisierte Unittest:

* muss eine Instanzmethode sein
* muss für die Testklasse [sichtbar](input-generation.md#visibility) sein, in der die generierten Tests gemäß dem [Einstellungswasserfall](settings-waterfall.md) platziert werden
* kann eine beliebige Anzahl von Parametern annehmen
* kann generisch sein

**Beispiel**

```csharp
[PexClass]
public partial class MyTests {
     [PexMethod]
     public void MyTest(int i)
     { ... }
}
```

<a name="pexexplorationattributebase"></a>
## <a name="pexexplorationattributebase"></a>PexExplorationAttributeBase

[Weitere Informationen](xref:Microsoft.Pex.Framework.PexExplorationAttributeBase)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

Dieses Attribut kann auf Assemblyebene festgelegt werden, um die Werte der Standardeinstellung für alle Durchsuchungsvorgänge außer Kraft zu setzen.

```csharp
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "MSTestv2")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Dieses Attribut gibt an, dass eine Assembly im aktuellen Testprojekt getestet wird.

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Dieses Attribut wird für eine Assembly verwendet, die instrumentiert werden soll.

**Beispiel**

```csharp
using Microsoft.Pex.Framework;

// the assembly containing ATypeFromTheAssemblyToInstrument should be instrumented
[assembly: PexInstrumentAssembly(typeof(ATypeFromTheAssemblyToInstrument))]

// the assembly name can be used as well
[assembly: PexInstrumentAssembly("MyAssemblyName")]
```

<a name="pexusetype"></a>
## <a name="pexusetype"></a>PexUseType

Dieses Attribut teilt IntelliTest mit, dass ein bestimmter Typ zum Instanziieren (abstrakter) Basistypen oder Schnittstellen verwendet werden kann.

**Beispiel**

```csharp
[PexMethod]
[PexUseType(typeof(A))]
[PexUseType(typeof(B))]
public void MyTest(object testParameter)
{
     ... // IntelliTest will consider types A and B to instantiate 'testParameter'
}
```

<a name="pexallowedexception"></a>
## <a name="pexallowedexception"></a>PexAllowedException

Wenn dieses Attribut an eine [PexMethod](#pexmethod) (oder [PexClass](#pexclass)) angefügt wird, ändert sich die Standardlogik von IntelliTest, die angibt, wann der Test fehlschlägt. Der Test wird nicht als fehlgeschlagen angesehen, auch wenn er die angegebene Ausnahme auslöst.

**Beispiel**

Der folgende Test legt fest, dass der Konstruktor von **Stack** eine **ArgumentOutOfRangeException** auslösen kann:

```csharp
class Stack {
  int[] _elements;
  int _count;
  public Stack(int capacity) {
    if (capacity<0) throw new ArgumentOutOfRangeException();
    _elements = new int[capacity];
    _count = 0;
  }
  ...
}
```

Der Filter wird wie folgt an eine Fixierung angefügt (er kann auch auf Assembly- oder Testebene definiert werden):

```csharp
[PexMethod]
[PexAllowedException(typeof(ArgumentOutOfRangeException))]
class CtorTest(int capacity) {
  Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException
}
```

<a name="pexallowedexceptionfromassembly"></a>
## <a name="pexallowedexceptionfromassembly"></a>PexAllowedExceptionFromAssembly

[Weitere Informationen](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromAssemblyAttribute)

<a name="pexallowedexceptionfromtype"></a>
## <a name="pexallowedexceptionfromtype"></a>PexAllowedExceptionFromType

[Weitere Informationen](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeAttribute)

<a name="pexallowedexceptionfromtypeundertest"></a>
## <a name="pexallowedexceptionfromtypeundertest"></a>PexAllowedExceptionFromTypeUnderTest

[Weitere Informationen](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeUnderTestAttribute)

## <a name="got-feedback"></a>Sie haben Fragen oder Anmerkungen?

Posten Sie Ihre Ideen und Featureanfragen in der [Entwicklercommunity](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
