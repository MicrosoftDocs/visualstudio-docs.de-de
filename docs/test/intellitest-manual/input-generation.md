---
title: Dynamische symbolische Ausführung | Microsoft IntelliTest-Test-Tool für Entwickler
description: Hier erfahren Sie, wie IntelliTest Eingaben für parametrisierte Unittests erzeugt, indem die Branchbedingungen im Programm analysiert werden.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Dynamic symbolic execution
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 62c06333af1e296c7e9745b70f33577d45ede68b
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668767"
---
# <a name="input-generation-using-dynamic-symbolic-execution"></a>Eingabeerzeugung mithilfe der dynamischen symbolischen Ausführung

IntelliTest erzeugt Eingaben für [parametrisierte Unittests](test-generation.md#parameterized-unit-testing), indem es die Branchbedingungen im Programm analysiert. Testeingaben werden danach ausgewählt, ob sie neues Branchingverhalten des Programm auslösen können. Die Analyse ist ein inkrementeller Prozess. Sie verfeinert das Prädikat `q: I -> {true, false}` über die formalen Eingabeparameter des Tests `I`. `q` stellt die Menge an Verhaltensweisen dar, die IntelliTest bereits beobachtet hat. Zunächst ist dies `q := false`, weil noch nichts beobachtet wurde.

Die Schritte der Schleife sind wie folgt:

1. IntelliTest bestimmt Eingaben `i` mit einem [Einschränkungs-Solver](#constraint-solver), sodass `q(i)=false` ist. Aufgrund der Konstruktion nimmt die Eingabe `i` einen neuen Ausführungspfad. Zunächst bedeutet dies, dass `i` jede Eingabe sein kann, weil noch kein Ausführungspfad gefunden wurde.

1. IntelliTest führt den Test mit der ausgewählten Eingabe `i` aus und überwacht die Ausführung des Test sowie das getestete Programm.

1. Während der Ausführung nimmt das Programm einen bestimmten Pfad, der von alle bedingten Branches des Programms bestimmt wird. Der Satz aller Bedingungen, die die Ausführung bestimmen, wird als *Pfadbedingung* bezeichnet. Diese wird über die formellen Eingabeparameter als Prädikat `p: I -> {true, false}` geschrieben. IntelliTest berechnet eine Repräsentation dieses Prädikats.

1. IntelliTest legt `q := (q or p)` fest. Anders gesagt bedeutet dies, dass erfasst wird, dass es den Pfad gesehen hat, der mit `p` dargestellt wird.

1. Gehen Sie zu Schritt 1.

Der [Einschränkungs-Solver](#constraint-solver) von IntelliTest kann Werte aller Typen behandeln, die in .NET-Programmen vorkommen können:

* [Ganze Zahlen](#integers-and-floats) und [Gleitkommas](#integers-and-floats)
* [Objekte](#objects)
* [Strukturen](#structs)
* [Arrays](#arrays-and-strings) und [Zeichenfolgen](#arrays-and-strings)

IntelliTest filtert Eingaben heraus, die gegen angegebenen Annahmen verstoßen.

Neben direkten Eingaben (Argumente an [parametrisierte Unittests](test-generation.md#parameterized-unit-testing)) kann ein Test weitere Eingabewerte aus der statischen Klasse [PexChoose](static-helper-classes.md#pexchoose) ziehen. Die Wahl bestimmt auch das Verhalten der [parametrisierten Pseudoobjekte](#parameterized-mocks).

## <a name="constraint-solver"></a>Einschränkungs-Solver

IntelliTest verwendet einen Einschränkungs-Solver, um die relevanten Eingabewerte eines Tests und des getesteten Programms zu bestimmen.

IntelliTest verwendet den Einschränkungs-Solver [Z3](https://github.com/Z3Prover/z3/wiki).

## <a name="dynamic-code-coverage"></a>Dynamische Code Coverage

Als Nebenwirkung der Laufzeitüberwachung sammelt IntelliTest Daten zu dynamischen Code Coverage.
Dies wird als *dynamisch* bezeichnet, da IntelliTest nur von Code weiß, der bereits ausgeführt wurde. Deshalb kann es keine absoluten Werte für die Coverage angeben, wie dies andere Coveragetools machen.

Wenn IntelliTest z.B. angibt, dass die Coverage aus 5/10 Basisblöcken besteht, bedeutet dies, das fünf von zehn Blöcken abgedeckt wurden, wobei die gesamte Zahl an Blöcken in allen bis jetzt von der Analyse erreichten Methoden zehn ist (im Gegensatz zu allen Methode in der getesteten Assembly vorhanden sind).
Je weiter die Analyse fortschreitet und je mehr erreichbare Methoden gefunden werden, desto höher können der Zähler (in diesem Fall 5) und der Nenner (in diesem Fall 10) sein.

## <a name="integers-and-floats"></a>Ganze Zahlen und Gleitkommas

Der [Einschränkungs-Solver](#constraint-solver) von IntelliTest bestimmt Testeingabewerte primitiver Typen wie z.B. **byte**, **int**, **float** und anderer, um verschiedene Ausführungspfade für den Test und das getestete Programm auszulösen.

## <a name="objects"></a>Objekte

IntelliTest kann entweder [Instanzen vorhandener .NET-Klassen erstellen](#existing-classes), oder Sie können IntelliTest verwenden, um automatisch [Pseudoobjekte zu erstellen](#parameterized-mocks), die eine spezifische Schnittstelle implementieren und sich je nach Verwendung anders verhalten.

<a name="existing-classes"></a>
## <a name="instantiate-existing-classes"></a>Instanziieren vorhandener Klassen

**Wo liegt das Problem?**

IntelliTest überwacht die ausgeführten Anweisungen, wenn es einen Test und das getestete Programm ausführt. Insbesondere überwacht es jeden Zugriff auf Felder. Dann verwendet es einen [Einschränkungs-Solver](#constraint-solver), um neue Testeingaben zu bestimmen, einschließlich Objekte und deren Feldwerte, sodass der Test und das getestete Programm sich anders verhalten.

Dies bedeutet, dass IntelliTest Objekte eines bestimmten Typs erstellen und deren Feldwerte festlegen muss. Wenn die Klasse [sichtbar](#visibility) ist und über einen [sichtbaren](#visibility) Konstruktor verfügt, kann IntelliTest eine Instanz der Klasse erstellen.
Wenn alle Felder der Klasse [sichtbar](#visibility) sind, kann IntelliTest die Felder automatisch festlegen.

Wenn der Typ nicht sichtbar ist oder wenn die Felder nicht [sichtbar](#visibility) sind, benötigt IntelliTest Hilfe beim Erstellen von Objekten und dabei, diese in interessante Zustände zu versetzen, um die maximale Code Coverage zu erreichen. IntelliTest könnte Reflektion verwenden, um auf beliebige Weise Instanzen zu erstellen und zu initialisieren. Dies ist in der Regel allerdings nicht die Ideallösung, da dadurch möglicherweise das Objekt in einen Zustand versetzt wird, der bei der normalen Programmausführung nicht auftreten würde. Stattdessen verlässt sich IntelliTest auf Hinweise des Benutzers.

## <a name="visibility"></a>Sichtbarkeit

.NET hat ein aufwendiges Sichtbarkeitsmodell: Typen, Methoden, Felder und andere Member können **privat**, **öffentlich**, **intern** usw. sein.

Wenn IntelliTest Tests erzeugt, versucht es, nur Aktionen durchzuführen, die gemäß den Sichtbarkeitsregeln von .NET Framework innerhalb des Kontexts der erzeugten Tests zulässig sind (wie das Aufrufen von Konstruktoren, Methoden und das Festlegen von Feldern).

Die folgenden Regeln gelten:

* **Sichtbarkeit von internen Membern**
  * IntelliTest geht davon aus, dass erzeugte Tests Zugriff auf interne Member haben, die für die einschließende Klasse [PexClass](attribute-glossary.md#pexclass) sichtbar sind.
  .NET verfügt über das **InternalsVisibleToAttribute**, um die Sichtbarkeit interner Member auf andere Assemblys auszuweiten.

* **Sichtbarkeit privater Member und Member der Familie (in C# geschützt) der Klasse [PexClass](attribute-glossary.md#pexclass)**
  * IntelliTest platziert die erzeugten Tests immer direkt in die Klasse [PexClass](attribute-glossary.md#pexclass) oder in eine Unterklasse. Deshalb geht IntelliTest davon aus, dass es alle sichtbaren Member der Familie (in C# **geschützt**) verwenden darf.
  * Wenn die erzeugten Tests direkt in die Klasse [PexClass](attribute-glossary.md#pexclass) platziert werden (üblicherweise durch das Verwenden partieller Klassen), geht IntelliTest davon aus, dass es auch alle privaten Member der Klasse [PexClass](attribute-glossary.md#pexclass) verwenden darf.

* **Sichtbarkeit öffentlicher Member**
  * IntelliTest geht davon aus, dass es alle exportierten Member, die im Kontext der Klasse [PexClass](attribute-glossary.md#pexclass) sichtbar sind, verwenden darf.

## <a name="parameterized-mocks"></a>Parametrisierte Pseudoobjekte

Wie teste ich eine Methode, die einen Parameter eines Schnittstellentyps hat? Oder einer nicht versiegelten Klasse? IntelliTest weiß nicht, welche Implementierungen später verwendet werden, wenn diese Methode aufgerufen wird. Möglicherweise ist zur Zeit des Tests noch nicht mal eine Implementierung verfügbar.

Die konventionelle Antwort ist das Verwenden von *Pseudoobjekten* mit explizitem Verhalten.

Ein Pseudoobjekt implementiert eine Schnittstelle (oder weitet eine nicht versiegelte Klasse aus). Dies stellt keine tatsächliche Implementierung dar, sondern ist nur eine Verknüpfung, die die Ausführung von Tests mit dem Pseudoobjekt ermöglicht. Sein Verhalten wird manuell im Rahmen jedes Testfalls definiert, in dem es zum Einsatz kommt. Es gibt viele Tools, die das Definieren eines Pseusoobjekts und dessen erwarteten Verhaltens erleichtern. Dennoch muss dieses Verhalten manuell definiert werden.

Statt hart codierter Werte in Pseudoobjekten kann IntelliTest die Werte erzeugen. Neben [parametrisierten Unittests](test-generation.md#parameterized-unit-testing) ermöglicht IntelliTest auch parametrisierte Pseudoobjekte.

Parametrisierte Pseudoobjekte haben zwei verschiedene Ausführungsmodi:

* **choosing** (auswählen): Beim Durchsuchen von Code sind Pseudoobjekte eine Quelle zusätzlicher Testeingaben, und IntelliTest versucht, interessante Werte auszuwählen.
* **replay** (wiedergeben): Beim Ausführen eines bereits erzeugten Test verhalten sich Pseudoobjekte genauso wie Stubs mit Verhalten (also mit vordefiniertem Verhalten).

Verwenden Sie [PexChoose](static-helper-classes.md#pexchoose), um Werte für parametrisierte Pseudoobjekte abzurufen.

## <a name="structs"></a>Strukturen

Der Ansatzpunkt von IntelliTest zu **struct**-Werten ist ähnlich zu seiner Vorgehensweise bei [Objekten](#objects).

## <a name="arrays-and-strings"></a>Arrays und Zeichenfolgen

IntelliTest überwacht die ausgeführten Anweisungen, wenn es einen Test und das getestete Programm ausführt. Es beobachtet insbesondere, wann das Programm von einer bestimmten Länge der Zeichenfolge oder eines Arrays abhängt (und die unteren Grenzen und Längen eines mehrdimensionalen Arrays).
Außerdem beobachtet es, wie das Programm die unterschiedlichen Elemente einer Zeichenfolge oder eines Arrays verwendet. Anschließend verwendet es einen [Einschränkungs-Solver](#constraint-solver), um zu bestimmen, welche Längen und Elementwerte möglicherweise dazu führen, dass sich der Test und das getestete Programm interessant verhalten.

IntelliTest versucht, die Größe der Arrays und der Zeichenfolgen zu senken, die benötigt werden, um interessantes Programmverhalten auszulösen.

<a name="additional-inputs"></a>
## <a name="obtain-additional-inputs"></a>Abrufen zusätzlicher Eingaben

Die statische Klasse [PexChoose](static-helper-classes.md#pexchoose) kann verwendet werden, um zusätzliche Eingaben für einen Test abzurufen. Zudem kann sie verwendet werden, um [parametrisierte Pseudoobjekte](#parameterized-mocks) zu implementieren.

## <a name="got-feedback"></a>Sie haben Fragen oder Anmerkungen?

Posten Sie Ihre Ideen und Featureanfragen in der [Entwicklercommunity](https://aka.ms/feedback/suggest?space=8).

## <a name="further-reading"></a>Weitere nützliche Informationen

* [Wie funktioniert dies?](https://devblogs.microsoft.com/devops/smart-unit-tests-a-mental-model/)
