---
title: Überschreiben und Erweitern der generierten Klassen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
ms.assetid: 30baa60d-a8ea-4611-96c1-8fcc3317cf21
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 16a09a5b0f5e534d310092036b8e7eb1d4c344d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668473"
---
# <a name="overriding-and-extending-the-generated-classes"></a>Überschreiben und Erweitern der generierten Klassen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bei ihrer DSL-Definition handelt es sich um eine Plattform, auf der Sie einen leistungsstarken Satz von Tools erstellen können, die auf einer domänenspezifischen Sprache basieren. Viele Erweiterungen und Anpassungen können vorgenommen werden, indem die von der DSL-Definition generierten Klassen überschrieben und erweitert werden. Diese Klassen umfassen nicht nur die Domänen Klassen, die Sie explizit im DSL-Definitions Diagramm definiert haben, sondern auch andere Klassen, die die Toolbox, den Explorer, die Serialisierung usw. definieren.

## <a name="extensibility-mechanisms"></a>Erweiterbarkeits Mechanismen
 Es werden mehrere Mechanismen bereitgestellt, mit denen Sie den generierten Code erweitern können.

### <a name="overriding-methods-in-a-partial-class"></a>Überschreiben von Methoden in einer partiellen Klasse
 Partielle Klassendefinitionen ermöglichen es, dass eine Klasse an mehr als einem Ort definiert wird. Dies ermöglicht es Ihnen, den generierten Code von dem Code zu trennen, den Sie selbst schreiben. In Ihrem manuell geschriebenen Code können Sie Klassen überschreiben, die vom generierten Code geerbt wurden.

 Wenn Sie in ihrer DSL-Definition z. b. eine Domänen Klasse mit dem Namen definieren `Book` , können Sie benutzerdefinierten Code schreiben, der Überschreibungs Methoden hinzufügt:

 `public partial class Book`

 `{`

 `protected override void OnDeleting()`

 `{`

 `MessageBox.Show("Deleting book " + this.Title);`

 `base.OnDeleting();`

 `} }`

> [!NOTE]
> Um Methoden in einer generierten Klasse zu überschreiben, schreiben Sie den Code immer in einer Datei, die von den generierten Dateien getrennt ist. In der Regel befindet sich die Datei in einem Ordner mit dem Namen "customcode". Wenn Sie Änderungen am generierten Code vornehmen, gehen diese verloren, wenn Sie den Code aus der DSL-Definition neu generieren.

 Um zu ermitteln, welche Methoden Sie außer Kraft setzen können, geben Sie **override** in der-Klasse ein, gefolgt von einem Leerzeichen. Die IntelliSense-QuickInfo informiert Sie darüber, welche Methoden überschrieben werden können.

### <a name="double-derived-classes"></a>Doppelte abgeleitete Klassen
 Die meisten Methoden in generierten Klassen werden von einem festgelegten Satz von Klassen in den modellierungsnamespaces geerbt. Einige Methoden werden jedoch im generierten Code definiert. Normalerweise bedeutet dies, dass Sie Sie nicht überschreiben können. Sie können in einer partiellen Klasse nicht die Methoden überschreiben, die in einer anderen partiellen Definition der gleichen Klasse definiert sind.

 Dennoch können Sie diese Methoden überschreiben, indem Sie das Flag für die **doppelte abgeleitete** Generierung für die Domänen Klasse festlegen. Dies bewirkt, dass zwei Klassen generiert werden, von denen eine eine abstrakte Basisklasse der anderen ist. Alle Methoden-und Eigenschafts Definitionen befinden sich in der Basisklasse, und nur der Konstruktor ist in der abgeleiteten Klasse.

 Beispielsweise ist in der Beispiel Bibliothek. DSL für die `CirculationBook` Domänen Klasse die- `Generates``Double Derived` Eigenschaft auf festgelegt `true` . Der generierte Code für diese Domänen Klasse enthält zwei Klassen:

- `CirculationBookBase`, bei dem es sich um eine abstrakte handelt, die alle Methoden und Eigenschaften enthält.

- `CirculationBook`, die von abgeleitet ist `CirculationBookBase` . Es ist leer, außer für seine Konstruktoren.

  Um eine beliebige Methode zu überschreiben, erstellen Sie eine partielle Definition der abgeleiteten Klasse, z `CirculationBook` . b.. Sie können sowohl die generierten Methoden als auch die Methoden überschreiben, die vom Modellierungs Framework geerbt wurden.

  Sie können diese Methode mit allen Elementtypen verwenden, einschließlich Modellelemente, Beziehungen, Formen, Diagrammen und Connectors. Sie können auch Methoden anderer generierter Klassen überschreiben. Einige generierte Klassen, z. b. toolboxhelper, sind immer doppelt abgeleitet.

### <a name="custom-constructors"></a>Benutzerdefinierte Konstruktoren
 Ein Konstruktor kann nicht überschrieben werden. Auch in doppelten abgeleiteten Klassen muss der Konstruktor in der abgeleiteten Klasse sein.

 Wenn Sie einen eigenen Konstruktor bereitstellen möchten, können Sie dies erreichen, indem Sie `Has Custom Constructor` für die Domänen Klasse in der DSL-Definition festlegen. Wenn Sie auf **alle Vorlagen transformieren**klicken, enthält der generierte Code keinen Konstruktor für die Klasse. Dies schließt einen aufzurufenden Konstruktor ein. Dies verursacht einen Fehlerbericht, wenn Sie die Projekt Mappe erstellen. Doppelklicken Sie auf den Fehlerbericht, um einen Kommentar im generierten Code anzuzeigen, in dem erläutert wird, was Sie bereitstellen sollten.

 Schreiben Sie eine partielle Klassendefinition in einer Datei, die von den generierten Dateien getrennt ist, und stellen Sie den Konstruktor bereit.

### <a name="flagged-extension-points"></a>Markierte Erweiterungs Punkte
 Ein gekennzeichnter Erweiterungs Punkt ist eine Stelle in der DSL-Definition, in der Sie eine Eigenschaft oder ein Kontrollkästchen festlegen können, um anzugeben, dass Sie eine benutzerdefinierte Methode bereitstellen. Benutzerdefinierte Konstruktoren sind ein Beispiel. Weitere Beispiele hierfür sind das Festlegen des `Kind` einer Domänen Eigenschaft auf einen berechneten oder benutzerdefinierten Speicher oder das Festlegen des **benutzerdefinierten Flag ist** in einem Verbindungs-Generator.

 Wenn Sie in jedem Fall das Flag festlegen und den Code neu generieren, wird ein Buildfehler ausgegeben. Doppelklicken Sie auf den Fehler, um einen Kommentar anzuzeigen, in dem erläutert wird, was Sie bereitstellen müssen.

### <a name="rules"></a>Regeln
 Mit dem Transaktions-Manager können Sie Regeln definieren, die vor dem Ende einer Transaktion ausgeführt werden, in der ein bestimmtes Ereignis aufgetreten ist, z. b. eine Änderung in einer Eigenschaft. Regeln werden in der Regel verwendet, um den Synchronität zwischen verschiedenen Elementen im Speicher beizubehalten. Beispielsweise werden Regeln verwendet, um sicherzustellen, dass im Diagramm der aktuelle Zustand des Modells angezeigt wird.

 Regeln werden pro Klasse definiert, sodass Sie nicht über Code verfügen müssen, der die Regel für jedes Objekt registriert. Weitere Informationen finden Sie unter [Regeln verbreiten Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Speichern von Ereignissen
 Der Modellierungs Speicher bietet einen Ereignis Mechanismus, mit dem Sie auf bestimmte Arten von Änderungen im Speicher lauschen können, einschließlich hinzufügen und Löschen von Elementen, Änderungen an Eigenschafts Werten usw. Die Ereignishandler werden nach dem Schließen der Transaktion aufgerufen, in der die Änderungen vorgenommen wurden. Diese Ereignisse werden in der Regel zum Aktualisieren von Ressourcen außerhalb des Stores verwendet.

### <a name="net-events"></a>.Net-Ereignisse
 Sie können einige Ereignisse in Form von Formen abonnieren. Sie können z. b. mit Mausklicks auf eine Form lauschen. Sie müssen Code schreiben, der das-Ereignis für jedes-Objekt abonniert. Dieser Code kann in einer außer Kraft Setzung von initializeingestanceresources () geschrieben werden.

 Einige Ereignisse werden für shapefields generiert, die zum Zeichnen von decoratoren in einer Form verwendet werden. Ein Beispiel finden Sie unter Gewusst [wie: Abfangen eines Klick auf eine Form oder einen Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

 Diese Ereignisse treten in der Regel nicht innerhalb einer Transaktion auf. Sie sollten eine Transaktion erstellen, wenn Sie Änderungen im Speicher vornehmen möchten.
