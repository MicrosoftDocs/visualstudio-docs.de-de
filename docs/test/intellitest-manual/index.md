---
title: Übersicht | Microsoft IntelliTest-Test-Tool für Entwickler
description: Hier erfahren Sie, wie IntelliTest ein automatisiertes und transparentes Testvorgehen verwendet, um eine Kandidatensammlung von Tests für Ihren .NET-Code zu erzeugen.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 6853ef6040df943ac3050621a5b3a2528d599d9f
ms.sourcegitcommit: 4e28314dc2be59b4c5fd44545c0653f625e74489
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/23/2020
ms.locfileid: "97756616"
---
# <a name="overview-of-microsoft-intellitest"></a>Überblick über Microsoft IntelliTest

IntelliTest ermöglicht es Ihnen, Fehler früh zu erkennen und reduziert die Kosten für die Wartung von Tests. Durch ein automatisiertes und transparentes Testvorgehen kann IntelliTest eine Kandidatensammlung von Tests für Ihren .NET-Code erzeugen. Die Erzeugung von Testsammlungen kann zusätzlich durch von Ihnen festgelegte *Eigenschaften für die Richtigkeit* gesteuert werden. IntelliTest entwickelt die Testsammlung sogar automatisch weiter, wenn sich der getestete Code weiterentwickelt.

> [!NOTE]
> IntelliTest ist nur in der Enterprise Edition verfügbar. Das Feature wird für C#-Code unterstützt, das auf .NET Framework abzielt. .NET Core und .NET Standard werden zurzeit nicht unterstützt.

**Charakterisierungstests** Mit IntelliTest können Sie das Verhalten von Code bezüglich einer Sammlung herkömmlicher Komponententests bestimmen.
Eine derartige Testsammlung kann als Regressionssammlung verwendet werden, die die Grundlage bildet, um das komplexe Thema der Refactoringlegacy und unbekannten Codes in Angriff zu nehmen.

**Eingabeerzeugung geführter Tests** IntelliTest verwendet eine offene Codeanalyse und ein Vorgehen zum Lösen von Einschränkungen, um automatisch präzise Testeingabewerte zu erzeugen. Dazu sind meistens keine Benutzereingriffe erforderlich. Für komplexe Objekttypen werden automatisch Factorys erstellt. Sie können die Testeingabeerzeugung führen, indem Sie die Factorys erweitern und so konfigurieren, dass Sie ihren Anforderungen entsprechen. Eigenschaften der Richtigkeit, die als Assertionen im Code angegeben werden, werden auch automatisch verwendet, um die Testeingabeerzeugung zusätzlich zu führen.

**IDE-Integration** IntelliTest ist vollständig in die IDE von Visual Studio integriert. Alle während der Erzeugung der Testsammlung erfassten Informationen (wie die automatisch erzeugten Eingaben, die Ausgaben Ihres Codes, die erzeugten Testfälle und deren Status: erfolgreich oder fehlgeschlagen) werden in der IDE von Visual Studio angezeigt. Sie können ganz leicht zwischen dem Bereinigen Ihres Codes und dem erneuten Ausführen von IntelliTest wechseln, ohne die Visual Studio-IDE verlassen zu müssen.
Der Test kann in der Projektmappe als Unittestprojekt gespeichert werden und wird anschließend automatisch vom Test-Explorer von Visual Studio erkannt.

**Ergänzen vorhandener Testmethoden** Verwenden Sie IntelliTest, um vorhandene Testmethoden zu ergänzen, die Sie möglicherweise bereits befolgen.

Wenn Sie Folgendes testen möchten:

* Algorithmen für primitive Daten oder Arrays primitiver Daten:
  * Schreiben Sie [parametrisierte Unittests](test-generation.md#parameterized-unit-testing).
* Algorithmen für komplexe Daten, wie z.B. ein Compiler:
  * Lassen Sie IntelliTest zunächst eine abstrakte Repräsentation der Daten erzeugen, und fügen Sie diese dann im Algorithmus ein.
  * Lassen Sie IntelliTest Instanzen mit [benutzerdefinierten Objekterstellungen](input-generation.md#objects) und Dateninvarianten erstellen, und rufen Sie anschließend den Algorithmus auf.
* Datencontainer:
  * Schreiben Sie [parametrisierte Unittests](test-generation.md#parameterized-unit-testing).
  * Lassen Sie IntelliTest Instanzen mit [benutzerdefinierten Objekterstellungen](input-generation.md#objects) und Dateninvarianten erstellen. Rufen Sie anschließend eine Methode des Containers auf, und prüfen Sie dann die Invarianten erneut.
  * Schreiben Sie [parametrisierte Unittests](test-generation.md#parameterized-unit-testing), die je nach Parameterwerten unterschiedliche Methoden der Implementierung aufrufen.
* Eine vorhandene Codebasis:
  * Verwenden Sie den IntelliTest-Assistenten von Visual Studio, um mit der Erzeugung von [parametrisierten Unittests (PUTs)](test-generation.md#parameterized-unit-testing) zu beginnen.

## <a name="the-hello-world-of-intellitest"></a>„Hello World“ von IntelliTest

IntelliTest findet für das getestete Programm relevante Eingaben. Dies bedeutet, dass Sie es verwenden können, um die bekannte **Hello World!** - Zeichenfolge zu generieren. Dabei wird davon ausgegangen, dass Sie ein MSTest-basiertes C#-Projekt erstellt und einen Verweis auf **Microsoft.Pex.Framework** hinzugefügt haben. Wenn Sie ein anderes Testframework verwenden, erstellen Sie eine C#-Klassenbibliothek, und konsultieren Sie die Dokumentation zum Testframework, um zu erfahren, wie Sie ein Projekt einrichten.

Im folgenden Beispiel werden zwei Einschränkungen in einem Parameter mit dem Namen **value** erstellt, sodass IntelliTest die erforderliche Zeichenfolge erzeugt:

```csharp
using System;
using Microsoft.Pex.Framework;
using Microsoft.VisualStudio.TestTools.UnitTesting;

[TestClass]
public partial class HelloWorldTest {
    [PexMethod]
    public void HelloWorld([PexAssumeNotNull]string value) {
        if (value.StartsWith("Hello")
            && value.EndsWith("World!")
            && value.Contains(" "))
            throw new Exception("found it!");
    }
}
```

Sobald dieser kompiliert und ausgeführt wurde, erzeugt IntelliTest mehrere Tests wie etwa die folgenden:

1. ""
2. "\0\0\0\0\0"
3. "Hello"
4. "\0\0\0\0\0\0"
5. "Hello\0"
6. "Hello\0\0"
7. "Hello\0World!"
8. "Hello World!"

> [!NOTE]
> Versuchen Sie bei Buildproblemen, die Verweise auf Microsoft.VisualStudio.TestPlatform.TestFramework und Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions durch einen Verweis auf Microsoft.VisualStudio.QualityTools.UnitTestFramework zu ersetzen.

Lesen Sie [Generieren von Komponententests für Code mit IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md), um zu erfahren, wo generierte Tests gespeichert werden. Der erzeugte Testcode sollte einen Test wie den folgenden Code enthalten:

```csharp
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

So einfach ist das!

Zusätzliche Ressourcen:
  * Sehen Sie sich dieses [Channel 9-Video](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest) an
  * Sehen Sie sich diese [Übersicht im MSDN-Magazin](/archive/msdn-magazine/2015/february/visual-studio-2015-build-better-software-with-smart-unit-tests) an

## <a name="important-attributes"></a>Wichtige Attribute

* [PexClass](attribute-glossary.md#pexclass) kennzeichnet einen Typ, der **PUT** enthält
* [PexMethod](attribute-glossary.md#pexmethod) markiert ein **PUT**-Objekt
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) kennzeichnet einen Parameter, der nicht NULL ist

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) bindet ein Testprojekt an ein Projekt an
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) gibt an, dass eine Assembly instrumentiert werden soll

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="important-static-helper-classes"></a><a name="helper-classes"></a> Wichtige statische Hilfsklassen

* [PexAssume](static-helper-classes.md#pexassume) wertet Annahmen aus (Eingabefilterung)
* [PexAssert](static-helper-classes.md#pexassert) wertet Assertionen aus
* [PexChoose](static-helper-classes.md#pexchoose) generiert neue Optionen (zusätzliche Eingaben)
* [PexObserve](static-helper-classes.md#pexobserve) protokolliert Live-Werte für die generierten Tests

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="limitations"></a>Einschränkungen

In diesem Abschnitt werden die Einschränkungen von IntelliTest beschrieben:

* [Nichtdeterminiertheit](#nondeterminism)
* [Parallelität](#concurrency)
* [Nativer .NET-Code](#native-code)
* [Plattform](#platform)
* [Sprache](#language)
* [Symbolischer Ansatzpunkt](#symbolic-reasoning)
* [Stapelüberwachung](#incorrect-stack-traces)

### <a name="nondeterminism"></a>Nichtdeterminiertheit

IntelliTest geht davon aus, dass das analysierte Programm deterministisch ist. Wenn dem nicht so ist, durchläuft IntelliTest so lange den Kreislauf, bis es eine Durchsuchungsbegrenzung erreicht.

IntelliTest sieht ein Programm als nicht deterministisch an, wenn es von Eingaben abhängt, die nicht von IntelliTest gesteuert werden können.

IntelliTest steuert die Eingaben, die an [parametrisierten Unittests](test-generation.md#parameterized-unit-testing) gegeben und von [PexChoose](static-helper-classes.md#pexchoose) abgerufen werden.
In diesem Sinne werden Aufrufe von nicht verwaltetem und nicht instrumentiertem Code auch als „Eingaben“ im instrumentierten Programm angesehen, die von IntelliTest nicht gesteuert werden können. Wenn die Ablaufsteuerung des Programms von spezifischen Werten abhängt, die aus diesen externen Quellen stammen, kann IntelliTest das Programm nicht zu vorher nicht abgedeckten Bereichen „steuern“.

Zusätzlich wird das Programm als nicht deterministisch angesehen, wenn sich die Werte aus externen Quellen ändern, wenn das Programm erneut ausgeführt wird. In derartigen Fällen verliert IntelliTest die Kontrolle über die Ausführung des Programms, und die Suche wird ineffizient.

Manchmal ist es nicht direkt ersichtlich, wenn dies passiert. Betrachten Sie die folgenden Beispiele:

* Das Ergebnis der **GetHashCode()** -Methode wird von nicht verwaltetem Code bereitgestellt und kann nicht vorausgesagt werden.
* Die **System.Random**-Klasse verwendet die aktuelle Systemzeit, um tatsächlich zufällige Werte zu liefern.
* Die **System.DateTime**-Klasse stellt die aktuelle Zeit bereit, die nicht von IntelliTest gesteuert werden kann.

### <a name="concurrency"></a>Parallelität

IntelliTest kann keine Multithreadprogramme verarbeiten.

### <a name="native-code"></a>Systemeigener Code

IntelliTest versteht keinen nativen Code wie etwa x86-Anweisungen, die über **P/Invoke** aufgerufen werden. Es weiß nicht, wie solche Aufrufe in Einschränkungen zu übersetzen sind, die an einen [Einschränkungs-Solver](input-generation.md#constraint-solver) übergeben werden können.
Selbst für .NET-Code kann es nur Code analysieren, den es auch instrumentiert. IntelliTest kann keine bestimmten Teile von **mscorlib** instrumentieren, einschließliche der Reflektionsbibliothek. **DynamicMethod** kann nicht instrumentiert werden.

Empfohlene Problemumgehung: Verwenden Sie einen Testmodus, in dem sich derartige Methoden in Typen in einer dynamischen Assembly befinden. Selbst wenn einige Methoden nicht instrumentiert sind, versucht IntelliTest trotzdem, so viel wie möglich vom instrumentierten Code abzudecken.

### <a name="platform"></a>Plattform

IntelliTest wird nur im x86, 32-Bit .NET Framework unterstützt.

### <a name="language"></a>Sprache

Grundsätzlich kann IntelliTest beliebige .NET-Programme analysieren, die in einer beliebigen .NET-Sprache geschrieben sind. In Visual Studio wird allerdings nur C# unterstützt.

### <a name="symbolic-reasoning"></a>Symbolischer Ansatzpunkt

IntelliTest verwendet einen automatischen [Einschränkungs-Solver](input-generation.md#constraint-solver), um zu bestimmen, welche Werte für den Test und das getestete Programm relevant sind. Die Möglichkeiten des Einschränkungs-Solvers sind jedoch begrenzt und werden es auch immer sein.

### <a name="incorrect-stack-traces"></a>Falsche Stapelüberwachungen

Da IntelliTest Ausnahmen abfängt und diese in jeder instrumentierten Methode erneut auslöst, sind die Zeilennummern in Stapelüberwachungen nicht korrekt. Dies ist eine entwurfsbedingte Einschränkung der „rethrow“-Anweisung (erneut auslösen).

## <a name="further-reading"></a>Weiterführende Themen

* [Einführender Blogpost](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/).
* [Generieren von Komponententests für Code mit IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md)