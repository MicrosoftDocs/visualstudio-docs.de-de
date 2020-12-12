---
title: Grundlagen von Modellen, Klassen und Beziehungen
description: Erfahren Sie, wie eine domänenspezifische Sprache (DSL) durch die DSL-Definitionsdatei definiert wird und dass der meiste Programmcode in der DSL-Lösung aus dieser Datei generiert wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d912e98d01448a378acbed79e2278f70f62436e7
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362690"
---
# <a name="understanding-models-classes-and-relationships"></a>Grundlagen von Modellen, Klassen und Beziehungen
Eine domänenspezifische Sprache (DSL) wird durch die DSL-Definitionsdatei sowie durch benutzerdefinierten Programmcode definiert, den Sie möglicherweise schreiben. Der meiste Programmcode in der DSL-Lösung wird aus dieser Datei generiert.

 In diesem Thema werden die zentralen Funktionen der DSL-Definition erläutert.

## <a name="the-dsl-definition"></a>Die DSL-Definition
 Wenn Sie öffnen `Dsl\DslDefinition.dsl` , ähnelt das Visual Studio-Fenster der folgenden Abbildung.

 ![DSL-Designer](../modeling/media/dsl_designer.png)

 Die wichtigsten Informationen in der DSL-Definition werden im DSL-Definitions Diagramm angezeigt. Weitere Informationen, die ebenfalls Teil von "DslDefinition. DSL" sind, werden im DSL-Explorer angezeigt, der in der Regel auf der Seite des Diagramms angezeigt wird. Sie arbeiten mit dem Diagramm für die häufigsten Aufgaben und mit dem DSL-Explorer, um erweiterte Anpassungen vorzunehmen.

 Das DSL-Definitions Diagramm zeigt die Domänen Klassen, die Modellelemente definieren, und die Beziehungen, die Verknüpfungen zwischen Modellelementen definieren. Außerdem werden die Formen und Connectors angezeigt, die verwendet werden, um dem Benutzer die Modellelemente anzuzeigen.

 ![DSL-Designer mit Swimlane](../modeling/media/dsl_desinger.png)

 Wenn Sie ein Element in der DSL-Definition entweder im Diagramm oder im DSL-Explorer auswählen, werden Informationen dazu im Eigenschaftenfenster angezeigt. Im Fenster DSL-Details können zusätzliche Informationen angezeigt werden.

### <a name="models-are-instances-of-dsls"></a>Modelle sind Instanzen von DSLs.
 Ein *Modell* ist eine Instanz Ihrer DSL, die von einem Benutzer erstellt wurde. Ein Modell enthält Modellelemente, bei denen es sich um Instanzen der von Ihnen definierten Domänen Klassen handelt, sowie Links zwischen den Elementen, bei denen es sich um Instanzen der von Ihnen definierten Domänen Beziehungen handelt. Ein Modell kann auch Formen und Connectors aufweisen, die die Modellelemente und Verknüpfungen in einem Diagramm anzeigen. Die DSL-Definition enthält die Form Klassen, die Verbindungs Klassen und eine Klasse für das Diagramm.

 Eine DSL-Definition wird auch als *Domänen Modell* bezeichnet. Eine DSL-Definition oder ein Domänen Modell ist die Entwurfszeit Darstellung der domänenspezifischen Sprache, während es sich bei dem Modell um die Lauf Zeit Instanziierung der domänenspezifischen Sprache handelt.

## <a name="domain-classes-define-model-elements"></a>Domänen Klassen definieren Modellelemente
 Domänen Klassen werden verwendet, um die verschiedenen Elemente in der Domäne zu erstellen, und Domänen Beziehungen sind die Links zwischen den Elementen. Dabei handelt es sich um die Entwurfszeit Darstellung der Elemente und Links, die von den Benutzern der Entwurfs spezifischen Sprache instanziiert werden, wenn Sie Ihre Modelle erstellen.

 Diese Abbildung zeigt ein Modell, das vom Benutzer einer Musikbibliothek-DSL erstellt wurde. Musikalben werden durch Felder dargestellt, die Listen von Liedern enthalten. Künstler werden durch Runde in-Kurven-Felder dargestellt und sind mit den Alben verbunden, zu denen Sie beigetragen haben.

 ![Instanzmodell für generierte DSL](../modeling/media/music_instance.png)

 Die DSL-Definition trennt zwei Aspekte. Die Darstellung der Modellelemente im Modell Diagramm wird mithilfe von Form Klassen und Verbindungs Klassen definiert. Die im Modell enthaltenen Informationen werden mithilfe von Domänen Klassen und Domänen Beziehungen definiert.

 Die folgende Abbildung zeigt die Domänen Klassen und Beziehungen in der DSL-Definition der Musikbibliothek.

 ![Einbetten von und Verweisen auf Beziehungen](../modeling/media/music_classes.png)

 Die Abbildung zeigt vier Domänen Klassen: Musik, Album, Artist und Song. Die Domänen Klassen definieren Domänen Eigenschaften, z. b. Name, Titel usw. Im instanzmodell werden die Werte einiger dieser Eigenschaften im Diagramm angezeigt.

 Zwischen den-Klassen handelt es sich um Domänen Beziehungen: musichasalben, musichasartists, albumbhassongs und artistappearedonalben. Die Beziehungen haben Multiplizitäten, wie z. b. 1.. 1, 0.. *. Beispielsweise muss jeder Song mit genau einem Album durch die "albumhassongs"-Beziehung verknüpft werden. Jedes Album kann eine beliebige Anzahl von Liedern enthalten.

### <a name="rearranging-the-dsl-definition-diagram"></a>Neuanordnung des DSL-Definitions Diagramms
 Beachten Sie, dass eine Domänen Klasse mehrmals im DSL-Definitions Diagramm angezeigt werden kann, wie in Album in dieser Abbildung dargestellt. Es gibt immer eine Hauptansicht, und es können einige *Verweis* Sichten vorhanden sein.

 Zum erneuten Anordnen des DSL-Definitions Diagramms können Sie folgende Aktionen ausführen:

- Tauschen Sie die Haupt-und Verweis Ansichten mithilfe der Befehle "Struktur **hier** einfügen" und "Struktur **Teilen** " aus. Klicken Sie mit der rechten Maustaste auf eine einzelne Domänen Klasse, um diese Befehle anzuzeigen.

- Ordnen Sie die Domänen Klassen und Form Klassen durch Drücken von STRG + nach-oben und STRG + nach-unten neu an.

- Reduzieren oder erweitern Sie Klassen mithilfe des Symbols in der oberen rechten Ecke jeder Form.

- Reduzieren Sie Teile der Struktur durch Klicken auf das Minuszeichen (-) am unteren Rand einer Domänen Klasse.

## <a name="inheritance"></a>Vererbung
 Domänen Klassen können mithilfe der Vererbung definiert werden. Um eine Vererbungs Ableitung zu erstellen, klicken Sie auf das Vererbungs Tool, klicken Sie auf die abgeleitete Klasse, und klicken Sie dann auf die Basisklasse. Ein Modellelement verfügt über alle Eigenschaften, die in der eigenen Domänen Klasse definiert sind, sowie alle Eigenschaften, die von der Basisklasse geerbt wurden. Er erbt auch seine Rollen in Beziehungen.

 Vererbung kann auch zwischen Beziehungen, Formen und Connectors verwendet werden. Die Vererbung muss innerhalb derselben Gruppe beibehalten werden. Eine Form kann nicht von einer Domänen Klasse erben.

## <a name="domain-relationships"></a>Domänen Beziehungen
 Modellelemente können durch Beziehungen verknüpft werden. Links sind immer Binär; Sie verknüpfen genau zwei-Elemente. Jedes Element kann jedoch viele Links zu anderen Objekten enthalten, und es kann sogar mehrere Links zwischen dem gleichen Paar von Elementen geben.

 Ebenso wie Sie verschiedene Klassen von Elementen definieren können, können Sie unterschiedliche Klassen von Links definieren. Die Klasse eines Links wird als *Domänen Beziehung* bezeichnet. Eine Domänen Beziehung gibt an, welche Klassen von Elementen eine Verbindung herstellen können. Jedes Ende einer Beziehung wird als *Rolle* bezeichnet, und die Domänen Beziehung definiert Namen für die beiden Rollen sowie für die Beziehung selbst.

 Es gibt zwei Arten von Domänen Beziehungen: Einbetten von Beziehungen und Verweis Beziehungen. Im DSL-Definitions Diagramm verfügen Einbett Ende Beziehungen über voll solide Linien an jeder Rolle, und Verweis Beziehungen haben gestrichelte Linien.

### <a name="embedding-relationships"></a>Einbetten von Beziehungen
 Jedes Element in einem Modell, mit Ausnahme des Stamms, ist das Ziel eines Einbett enden Links. Das gesamte Modell bildet daher eine einzelne Struktur von Einbett enden Verknüpfungen. Eine Embedding Relationship die die Kapselung oder den Besitz darstellt. Zwei Modellelemente, die auf diese Weise verknüpft sind, werden auch als Parent und Child bezeichnet. Das untergeordnete Element wird als eingebettet in das übergeordnete Element bezeichnet.

 Einbett Ende Verknüpfungen werden in der Regel nicht explizit als Connectors in einem Diagramm angezeigt. Stattdessen werden Sie normalerweise durch Containment dargestellt. Der Stamm des Modells wird durch das Diagramm dargestellt, und die darin eingebetteten Elemente werden als Formen im Diagramm angezeigt.

 In diesem Beispiel verfügt die Klasse Musik der Stamm Klasse über einen Embedding Relationship musichasalben für das Album, das eine Einbett Ende "albumhassongs" enthält. Lieder werden als Elemente in einer Liste in jedem Album angezeigt. Musik verfügt auch über eine Einbett Ende musichasartists für die Klasse "Artist", deren Instanzen auch als Formen im Diagramm angezeigt werden.

 Eingebettete Elemente werden standardmäßig automatisch gelöscht, wenn ihre übergeordneten Elemente gelöscht werden.

 Wenn ein Modell in einer Datei im XML-Format gespeichert wird, werden eingebettete Elemente in ihren übergeordneten Elementen geschachtelt, es sei denn, Sie haben die Serialisierung angepasst.

> [!NOTE]
> Einbettung ist nicht identisch mit Vererbung. Untergeordnete Elemente in einem Embedding Relationship erben nicht die Eigenschaften des übergeordneten Elements. Eine Einbettung ist ein Linktyp zwischen Modellelementen. Vererbung ist eine Beziehung zwischen Klassen und erstellt keine Verknüpfungen zwischen Modellelementen.

### <a name="embedding-rules"></a>Einbetten von Regeln
 Jedes Element in einem instanzmodell muss das Ziel von genau einem Einbettungs Link sein, mit Ausnahme des Stamms des Modells.

 Daher muss jede nicht abstrakte Domänen Klasse, außer der Stamm Klasse, das Ziel mindestens eines Embedding Relationship sein, oder Sie muss eine Einbettung von einer Basisklasse erben. Eine Klasse kann das Ziel von mindestens zwei Einbettungen sein, aber ihre instanzmodellelemente können jeweils nur über ein übergeordnetes Element verfügen. Die Multiplizität Zwischenziel und Quelle muss 0.. 1 oder 1.. 1 sein.

### <a name="the-explorer-displays-the-embedding-tree"></a>Der Explorer zeigt den Einbettungs Baum an.
 Die DSL-Definition erstellt außerdem einen Explorer, den Benutzer neben Ihrem Modell Diagramm sehen.

 ![Generierter Explorer für DSL](../modeling/media/music_explorer.png)

 Im Explorer werden alle Elemente im Modell angezeigt, auch diejenigen, für die Sie keine Formen definiert haben. Es zeigt Elemente und Einbettungs Beziehungen, aber keine Verweis Beziehungen.

 Um die Werte der Domänen Eigenschaften eines Elements anzuzeigen, wählt der Benutzer ein Element aus, entweder im Modell Diagramm oder im Modell-Explorer, und öffnet die Eigenschaftenfenster. Es werden alle Domänen Eigenschaften angezeigt, einschließlich derjenigen, die nicht im Diagramm angezeigt werden. In diesem Beispiel hat jeder Song sowohl einen Titel als auch ein Genre, aber nur der Wert des Titels wird im Diagramm angezeigt.

## <a name="reference-relationships"></a>Verweis Beziehungen
 Eine Verweis Beziehung repräsentiert eine beliebige Art von Beziehung, die nicht eingebettet ist.

 Verweis Beziehungen werden in der Regel in einem Diagramm als Connectors zwischen den Formen angezeigt.

 In der XML-Darstellung des Modells wird ein Verweis Link zwischen zwei Elementen mithilfe von *Monikern dargestellt.* Das heißt, Moniker sind Namen, die jedes Element im Modell eindeutig identifizieren. Der XML-Knoten für jedes Modellelement enthält einen Knoten, der den Namen der Beziehung und den Moniker des anderen Elements angibt.

## <a name="roles"></a>Rollen
 Jede Domänen Beziehung verfügt über zwei Rollen: eine Quell Rolle und eine Zielrolle.

 In der folgenden Abbildung ist die Linie zwischen der Domänen Klasse **Verleger** und der **publishercatalog** -Domänen Beziehung die Quell Rolle. Die Linie zwischen der Domänen Beziehung und der Domänen Klasse des **Albums** ist die Zielrolle.

 ![Rollen und Eigenschaften](../modeling/media/propertycode.png)

 Die einer Beziehung zugeordneten Namen sind besonders wichtig, wenn Sie Programmcode schreiben, der das Modell durchläuft. Wenn Sie z. b. die DSL-Projekt Mappe erstellen, verfügt der generierte Klassen Herausgeber über einen Eigenschaften Katalog, der eine Auflistung von Alben ist. Das Klassen Album verfügt über einen Eigenschaften Herausgeber, bei dem es sich um eine einzelne Instanz der Klasse Publisher handelt.

 Wenn Sie in einer DSL-Definition eine Beziehung erstellen, werden den Eigenschafts-und Beziehungs Namen Standardwerte zugewiesen. Sie können Sie jedoch ändern.

## <a name="multiplicities"></a>Multiplizitäten
 Multiplizitäten geben an, wie viele Elemente in einer Domänen Beziehung dieselbe Rolle aufweisen können. Im Beispiel gibt die NULL-zu-n-multiplizitätseinstellung (0.. \* ) für die- **Katalog** Rolle an, dass jede Instanz der **Verleger** Domänen Klasse so viele **publishercatalog** -Beziehungslinks haben kann, wie Sie Sie angeben möchten.

 Konfigurieren Sie die Multiplizität einer Rolle entweder durch Eingabe des Diagramms oder durch Ändern der- `Multiplicity` Eigenschaft im **Eigenschaften** Fenster. In der folgenden Tabelle werden die Einstellungen für diese Eigenschaft beschrieben.

|Multiplizitätstyp|Beschreibung|
|-|-|
|0.. * (null bis viele)|Jede Instanz der Domänen Klasse kann über mehrere Instanzen der Beziehung oder keine Instanzen der Beziehung verfügen.|
|0.. 1 (null bis eins)|Jede Instanz der Domänen Klasse kann nicht mehr als eine Instanz der Beziehung oder keine Instanzen der Beziehung aufweisen.|
|1.. 1 (eins)|Jede Instanz der Domänen Klasse kann über eine Instanz der Beziehung verfügen. Es ist nicht möglich, mehr als eine Instanz dieser Beziehung aus einer Instanz der Role-Klasse zu erstellen. Wenn die Validierung aktiviert ist, wird ein Validierungs Fehler angezeigt, wenn eine Instanz der Rollen Klasse keine Instanz der Beziehung hat.|
|1.. * (eins zu viele)|Jede Instanz der-Klasse für die Rolle, die über diese Multiplizität verfügt, kann über mehrere Instanzen der Beziehung verfügen, und jede Instanz muss über mindestens eine Instanz der Beziehung verfügen. Wenn die Validierung aktiviert ist, wird ein Validierungs Fehler angezeigt, wenn eine Instanz der Rollen Klasse keine Instanz der Beziehung hat.|

## <a name="domain-relationships-as-classes"></a>Domänen Beziehungen als Klassen
 Eine Verknüpfung wird im Speicher als eine Instanz von Linkelement dargestellt, bei der es sich um eine abgeleitete Klasse von ModelElement handelt. Sie können diese Eigenschaften im Domänen Modell Diagramm für Domänen Beziehungen definieren.

 Sie können auch eine Beziehung zur Quelle oder zum Ziel anderer Beziehungen machen. Klicken Sie im Domänen Modell Diagramm mit der rechten Maustaste auf die Domänen Beziehung, und klicken Sie dann auf **als Klasse anzeigen**. Ein zusätzliches Klassenfeld wird angezeigt. Sie können dann Beziehungen mit der Verbindung herstellen.

 Sie können eine Beziehung teilweise durch Vererbung definieren, ebenso wie bei Domänen Klassen. Wählen Sie die abgeleitete Beziehung aus, und legen Sie im Eigenschaftenfenster die **Basis Beziehung** fest.

 Eine abgeleitete Beziehung spezialisiert ihre Basis Beziehung. Die Domänen Klassen, mit denen Sie verknüpft ist, sollten von oder den gleichen Klassen abgeleitet werden, die durch die Basis Beziehung verknüpft sind. Wenn eine Verknüpfung der abgeleiteten Beziehung in einem Modell erstellt wird, handelt es sich um eine Instanz der abgeleiteten und der Basis Beziehungen. Sie können im Programmcode zum umgekehrten Ende der Verknüpfung navigieren, indem Sie die Eigenschaften verwenden, die entweder von der Basis oder von der abgeleiteten Klasse generiert werden.

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](/previous-versions/bb126564(v=vs.100))