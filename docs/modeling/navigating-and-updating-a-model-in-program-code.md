---
title: Navigieren in und Aktualisieren von Modellen im Programmcode
description: Erfahren Sie, wie Sie Code schreiben können, um Modellelemente zu erstellen und zu löschen, ihre Eigenschaften festzulegen und Verknüpfungen zwischen Elementen zu erstellen und zu löschen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb7c78351ccd03247d458ca403c81d379ec18d29
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362209"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Navigieren in und Aktualisieren von Modellen im Programmcode

Sie können Code schreiben, um Modellelemente zu erstellen und zu löschen, deren Eigenschaften festzulegen und Verknüpfungen zwischen Elementen zu erstellen und zu löschen. Alle Änderungen müssen innerhalb einer Transaktion vorgenommen werden. Wenn die Elemente in einem Diagramm angezeigt werden, wird das Diagramm automatisch am Ende der Transaktion "korrigiert".

## <a name="an-example-dsl-definition"></a><a name="example"></a> Eine Beispiel-DSL-Definition
 Dies ist der Hauptteil der Datei "DslDefinition. DSL" für die Beispiele in diesem Thema:

 ![DSL-Definitions Diagramm &#45; Familienstruktur Modell](../modeling/media/familyt_person.png)

 Dieses Modell ist eine Instanz dieser DSL:

 ![Tudor-Stammbaummodell](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>Verweise und Namespaces
 Um den Code in diesem Thema auszuführen, sollten Sie Folgendes referenzieren:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Der Code verwendet diesen Namespace:

 `using Microsoft.VisualStudio.Modeling;`

 Wenn Sie den Code in einem anderen Projekt als dem Schreiben, in dem die DSL definiert ist, sollten Sie außerdem die Assembly importieren, die durch das DSL-Projekt erstellt wurde.

## <a name="navigating-the-model"></a><a name="navigation"></a> Navigieren im Modell

### <a name="properties"></a>Eigenschaften
 Domänen Eigenschaften, die Sie in der DSL-Definition definieren, werden zu Eigenschaften, auf die Sie im Programmcode zugreifen können:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Wenn Sie eine Eigenschaft festlegen möchten, müssen Sie dies innerhalb einer [Transaktion](#transaction)tun:

 `henry.Name = "Henry VIII";`

 Wenn in der DSL-Definition die **Art** einer Eigenschaft **berechnet** wird, können Sie Sie nicht festlegen. Weitere Informationen finden Sie unter [berechnete und benutzerdefinierte Speicher Eigenschaften](../modeling/calculated-and-custom-storage-properties.md).

### <a name="relationships"></a>Beziehungen
 Domänen Beziehungen, die Sie in der DSL-Definition definieren, werden zu Paaren von Eigenschaften, eine für die Klasse an jedem Ende der Beziehung. Die Namen der Eigenschaften werden im DslDefinition-Diagramm als Bezeichnungen für die Rollen auf den einzelnen Seiten der Beziehung angezeigt. Abhängig von der Multiplizität der Rolle ist der Typ der Eigenschaft entweder die Klasse am anderen Ende der Beziehung oder eine Auflistung dieser Klasse.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Die Eigenschaften an umgekehrten Enden einer Beziehung sind immer gegenseitig. Wenn ein Link erstellt oder gelöscht wird, werden die Rollen Eigenschaften für beide Elemente aktualisiert. Der folgende Ausdruck (der die Erweiterungen von verwendet `System.Linq` ) gilt immer für die Beziehung "parametershavechildren" im Beispiel:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **Elementlinks**. Eine Beziehung wird auch durch ein Modellelement dargestellt, das als *Link* bezeichnet wird, das eine Instanz des Domänen Beziehungstyp ist. Ein Link verfügt immer über ein Quell Element und ein Ziel Element. Das Quell Element und das Ziel Element können identisch sein.

 Sie können auf einen Link und seine Eigenschaften zugreifen:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Standardmäßig darf nicht mehr als eine Instanz einer Beziehung ein paar von Modellelementen verknüpfen. Wenn in der DSL-Definition das `Allow Duplicates` Flag jedoch für die Beziehung true ist, können mehrere Links vorhanden sein, und Sie müssen Folgendes verwenden `GetLinks` :

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Es gibt auch andere Methoden zum Zugreifen auf Links. Zum Beispiel:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Ausgeblendete Rollen** Wenn in der DSL-Definition die **Eigenschaft** wird für eine bestimmte Rolle den Wert **false** hat, wird keine Eigenschaft generiert, die dieser Rolle entspricht. Sie können jedoch weiterhin auf die Verknüpfungen zugreifen und die Verknüpfungen mithilfe der Methoden der Beziehung durchlaufen:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 Das am häufigsten verwendete Beispiel ist die <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> Beziehung, mit der ein Modellelement mit der Form verknüpft wird, die es in einem Diagramm anzeigt:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Das Element Verzeichnis
 Sie können mit dem Element Verzeichnis auf alle Elemente im Speicher zugreifen:

 `store.ElementDirectory.AllElements`

 Es gibt auch Methoden zum Suchen von Elementen, wie z. b.:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

## <a name="accessing-class-information"></a><a name="metadata"></a> Zugreifen auf Klassen Informationen
 Sie können Informationen zu den Klassen, Beziehungen und anderen Aspekten der DSL-Definition erhalten. Zum Beispiel:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Die Vorgänger Klassen von Modellelementen lauten wie folgt:

- ModelElement-alle Elemente und Beziehungen sind modelelements.

- Element Link-alle Beziehungen sind elementlinks.

## <a name="perform-changes-inside-a-transaction"></a><a name="transaction"></a> Ausführen von Änderungen innerhalb einer Transaktion
 Jedes Mal, wenn der Programmcode etwas im Speicher ändert, muss dies innerhalb einer Transaktion durchzuführen sein. Dies gilt für alle Modellelemente, Beziehungen, Formen, Diagramme und deren Eigenschaften. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Die einfachste Methode zur Verwaltung einer Transaktion ist eine-Anweisung, die `using` in einer-Anweisung eingeschlossen ist `try...catch` :

```
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 Sie können eine beliebige Anzahl von Änderungen innerhalb einer Transaktion vornehmen. Sie können neue Transaktionen innerhalb einer aktiven Transaktion öffnen.

 Um die Änderungen dauerhaft zu machen, sollten Sie `Commit` die Transaktion ausführen, bevor Sie verworfen wird. Wenn eine Ausnahme auftritt, die nicht innerhalb der Transaktion abgefangen wird, wird der Speicher auf seinen Zustand vor den Änderungen zurückgesetzt.

## <a name="creating-model-elements"></a><a name="elements"></a> Erstellen von Modellelementen
 In diesem Beispiel wird ein Element einem vorhandenen Modell hinzugefügt:

```csharp
FamilyTreeModel familyTree = ...; // The root of the model.
using (Transaction t =
    familyTree.Store.TransactionManager
    .BeginTransaction("update model"))
{
  // Create a new model element
  // in the same partition as the model root:
  Person edward = new Person(familyTree.Partition);
  // Set its embedding relationship:
  edward.FamilyTreeModel = familyTree;
          // same as: familyTree.People.Add(edward);
  // Set its properties:
  edward.Name = "Edward VII";
  t.Commit(); // Don't forget this!
}
```

 Dieses Beispiel veranschaulicht diese wichtigen Punkte zum Erstellen eines Elements:

- Erstellen Sie das neue Element in einer bestimmten Partition des Stores. Für Modellelemente und-Beziehungen, aber keine Formen, ist dies normalerweise die Standard Partition.

- Legen Sie es als Ziel für eine Embedding Relationship. In der DslDefinition dieses Beispiels muss jede Person das Ziel Embedding Relationship familytreehaspeople sein. Um dies zu erreichen, können wir entweder die Rolle "familytreemodel" für das Person-Objekt festlegen oder die Person der People Role-Eigenschaft des familytreemodel-Objekts hinzufügen.

- Legen Sie die Eigenschaften eines neuen Elements fest, insbesondere die Eigenschaft, für die `IsName` in der DslDefinition auf true festgelegt ist. Dieses Flag markiert die Eigenschaft, die zum Identifizieren des Elements innerhalb seines Besitzers dient. In diesem Fall weist die Name-Eigenschaft das Flag auf.

- Die DSL-Definition dieser DSL muss in den Speicher geladen worden sein. Wenn Sie eine Erweiterung, z. b. einen Menübefehl, schreiben, ist dies in der Regel bereits true. In anderen Fällen können Sie das Modell explizit in den Speicher laden oder [ModelBus](/previous-versions/ee904639(v=vs.140)) verwenden, um es zu laden. Weitere Informationen finden Sie unter Gewusst [wie: Öffnen eines Modells aus einer Datei im Programm Code](../modeling/how-to-open-a-model-from-file-in-program-code.md).

  Wenn Sie ein Element auf diese Weise erstellen, wird automatisch eine Form erstellt (wenn die DSL ein Diagramm aufweist). Sie wird an einem automatisch zugewiesenen Speicherort mit Standardform, Farbe und anderen Features angezeigt. Wenn Sie steuern möchten, wo und wie die zugeordnete Form angezeigt wird, finden Sie weitere Informationen unter [Erstellen eines Elements und seiner Form](#merge).

## <a name="creating-relationship-links"></a><a name="links"></a> Erstellen von Beziehungs Links
 In der Beispiel-DSL-Definition sind zwei Beziehungen definiert. Jede Beziehung definiert eine *Role-Eigenschaft* für die Klasse an jedem Ende der Beziehung.

 Es gibt drei Möglichkeiten, wie Sie eine Instanz einer Beziehung erstellen können. Jede dieser drei Methoden hat denselben Effekt:

- Legen Sie die-Eigenschaft des Quell Rollen Players fest. Zum Beispiel:

  - `familyTree.People.Add(edward);`

  - `edward.Parents.Add(henry);`

- Legen Sie die-Eigenschaft des Ziel Rollen Players fest. Zum Beispiel:

  - `edward.familyTreeModel = familyTree;`

       Die Multiplizität dieser Rolle ist `1..1` , daher weisen wir den Wert zu.

  - `henry.Children.Add(edward);`

       Die Multiplizität dieser Rolle ist `0..*` , daher fügen wir der Auflistung hinzu.

- Erstellen Sie explizit eine Instanz der Beziehung. Zum Beispiel:

  - `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  - `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  Die letzte Methode ist nützlich, wenn Sie Eigenschaften für die Beziehung selbst festlegen möchten.

  Wenn Sie ein Element auf diese Weise erstellen, wird automatisch ein Connector für das Diagramm erstellt, verfügt aber über eine Standardform, Farbe und andere Features. Informationen zum Steuern, wie der zugeordnete Connector erstellt wird, finden Sie unter [Erstellen eines Elements und seiner Form](#merge).

## <a name="deleting-elements"></a><a name="deleteelements"></a> Löschen von Elementen

Löschen Sie ein Element, indem Sie Folgendes aufrufen `Delete()` :

`henry.Delete();`

Mit diesem Vorgang wird auch Folgendes gelöscht:

- Beziehungslinks zu und aus dem Element. Beispielsweise `edward.Parents` enthält nicht mehr `henry` .

- Elemente bei Rollen, für die das `PropagatesDelete` Flag "true" ist. Beispielsweise wird die Form, in der das Element angezeigt wird, gelöscht.

Standardmäßig ist jede Embedding Relationship für `PropagatesDelete` die Zielrolle "true". Durch `henry` das Löschen wird das nicht gelöscht `familyTree` , sondern `familyTree.Delete()` alle werden gelöscht `Persons` .

Standardmäßig `PropagatesDelete` gilt für die Rollen von Verweis Beziehungen nicht.

Sie können bewirken, dass die Löschregeln bestimmte Weiterungen weglassen, wenn Sie ein Objekt löschen. Dies ist hilfreich, wenn Sie ein Element für ein anderes ersetzen. Sie geben die GUID für eine oder mehrere Rollen an, für die der Löschvorgang nicht weitergegeben werden soll. Der GUID kann aus der Beziehungs Klasse abgerufen werden:

`henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

(Dieses spezielle Beispiel hätte keine Auswirkung, da `PropagatesDelete` `false` für die Rollen der `ParentsHaveChildren` Beziehung ist.)

In einigen Fällen wird das Löschen durch das vorhanden sein einer Sperre verhindert, entweder für das Element oder für ein Element, das durch die Weitergabe gelöscht würde. Sie können verwenden `element.CanDelete()` , um zu überprüfen, ob das Element gelöscht werden kann.

## <a name="deleting-relationship-links"></a><a name="deletelinks"></a> Löschen von Beziehungs Links
 Sie können einen beziehungslink löschen, indem Sie ein Element aus einer Rollen Eigenschaft entfernen:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 Sie können den Link auch explizit löschen:

 `edwardHenryLink.Delete();`

 Diese drei Methoden haben die gleiche Wirkung. Sie müssen nur eine davon verwenden.

 Wenn die Rolle eine Multiplizität von 0.. 1 oder 1.. 1 hat, können Sie Sie auf `null` oder auf einen anderen Wert festlegen:

 `edward.FamilyTreeModel = null;` noch

 `edward.FamilyTreeModel = anotherFamilyTree;`

## <a name="re-ordering-the-links-of-a-relationship"></a><a name="reorder"></a> Neuordnen der Verknüpfungen einer Beziehung
 Die Verknüpfungen einer bestimmten Beziehung, die auf ein bestimmtes Modellelement zugeschnitten sind, haben eine bestimmte Sequenz. Sie werden in der Reihenfolge angezeigt, in der Sie hinzugefügt wurden. Diese Anweisung gibt z. b. immer die untergeordneten Elemente in derselben Reihenfolge aus:

 `foreach (Person child in henry.Children) ...`

 Sie können die Reihenfolge der Links ändern:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

## <a name="locks"></a><a name="locks"></a> Schleusen
 Ihre Änderungen werden möglicherweise durch eine Sperre verhindert. Sperren können für einzelne Elemente, für Partitionen und für den Speicher festgelegt werden. Wenn eine dieser Ebenen eine Sperre aufweist, die die Art der Änderung verhindert, die Sie vornehmen möchten, wird möglicherweise eine Ausnahme ausgelöst, wenn Sie versuchen, Sie zu ändern. Sie können ermitteln, ob Sperren mithilfe des-Elements festgelegt werden. Getlocks (), eine Erweiterungsmethode, die im-Namespace definiert ist <xref:Microsoft.VisualStudio.Modeling.Immutability> .

 Weitere Informationen finden Sie unter [Definieren einer Sperr Richtlinie zum Erstellen von Read-Only Segmenten](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

## <a name="copy-and-paste"></a><a name="copy"></a> Kopieren und Einfügen
 Sie können Elemente oder Gruppen von Elementen in einen kopieren <xref:System.Windows.Forms.IDataObject> :

```csharp
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Die-Elemente werden als serialisierte Element Gruppe gespeichert.

 Sie können Elemente aus einem IDataObject in ein Modell zusammenführen:

```csharp
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` kann entweder oder akzeptieren `PresentationElement` `ModelElement` . Wenn Sie einen angeben `PresentationElement` , können Sie auch eine Position im Ziel Diagramm als dritten Parameter angeben.

## <a name="navigating-and-updating-diagrams"></a><a name="diagrams"></a> Navigieren in und Aktualisieren von Diagrammen
 In einer DSL ist das Domänen Modellelement, das ein Konzept wie Person oder Song darstellt, getrennt vom Shape-Element, das die Darstellung des Diagramms darstellt. Das Domänen Modellelement speichert die wichtigen Eigenschaften und Beziehungen der Konzepte. Das Shape-Element speichert die Größe, Position und Farbe der Objekt Ansicht im Diagramm sowie das Layout der Komponenten Teile.

### <a name="presentation-elements"></a>Präsentationselemente
 ![Klassendiagramm für grundlegende Form- und Elementtypen](../modeling/media/dslshapesandelements.png)

 In ihrer DSL-Definition erstellt jedes Element, das Sie angeben, eine Klasse, die von einer der folgenden Standardklassen abgeleitet ist.

|Art des Elements|Basisklasse|
|-|-|
|Domänen Klasse|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Domänen Beziehung|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Form|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Connector|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diagramm|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Ein Element in einem Diagramm stellt in der Regel ein Modellelement dar. In der Regel (aber nicht immer) <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> stellt eine Instanz einer Domänen Klasse dar, und eine <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> stellt eine Domänen Beziehungs Instanz dar. Die <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> Beziehung verknüpft eine Knoten-oder Linkform mit dem Modellelement, das Sie darstellt.

 Jede Knoten-oder Linkform gehört zu einem Diagramm. Eine binäre Linkform verbindet zwei Knoten Formen.

 Formen können untergeordnete Formen in zwei Sätzen aufweisen. Eine Form in der `NestedChildShapes` Menge ist auf das umgebende Feld des übergeordneten Elements beschränkt. Eine Form in der `RelativeChildShapes` Liste kann außerhalb oder teilweise außerhalb der Grenzen des übergeordneten Elements angezeigt werden, z. b. eine Bezeichnung oder ein Port. Ein Diagramm hat No `RelativeChildShapes` und No `Parent` .

### <a name="navigating-between-shapes-and-elements"></a><a name="views"></a> Navigieren zwischen Formen und Elementen
 Domänen Modellelemente und Shape-Elemente werden durch die <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> Beziehung verknüpft.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 Dieselbe Beziehung verknüpft Beziehungen mit Connectors im Diagramm:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Mit dieser Beziehung wird auch der Stamm des Modells mit dem Diagramm verknüpft:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Um das Modellelement, das durch eine Form dargestellt wird, zu erhalten, verwenden Sie:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Navigieren um das Diagramm
 Im Allgemeinen ist es nicht empfehlenswert, zwischen Formen und Connectors im Diagramm zu navigieren. Es ist besser, die Beziehungen im Modell zu durchsuchen und zwischen den Formen und Connectors zu wechseln, wenn es erforderlich ist, an der Darstellung des Diagramms zu arbeiten. Mit diesen Methoden werden Connectors an jedem Ende mit den Formen verknüpft:

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Viele Formen sind Composite. Sie bestehen aus einer übergeordneten Form und einer oder mehreren Ebenen untergeordneter Elemente. Formen *, die relativ* zu einer anderen Form positioniert sind, werden als untergeordnete Elemente bezeichnet. Wenn die übergeordnete Form verschoben wird, werden die untergeordneten Elemente mit dem Element bewegt.

 *Relative* untergeordnete Elemente können außerhalb des umgebenden Felds der übergeordneten Form angezeigt werden.  Geschachtelte untergeordnete Elemente werden strikt innerhalb der Grenzen des übergeordneten Elements angezeigt.

 Um den obersten Satz von Formen in einem Diagramm zu erhalten, verwenden Sie Folgendes:

 `Diagram.NestedChildShapes`

 Die Vorgänger Klassen von Formen und Connectors sind:

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *Yourshape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *Yourconnector*

### <a name="properties-of-shapes-and-connectors"></a><a name="shapeProperties"></a> Eigenschaften von Formen und Connectors
 In den meisten Fällen ist es nicht erforderlich, explizite Änderungen an Formen vorzunehmen. Wenn Sie die Modellelemente geändert haben, werden die Formen und Connectors durch die "Korrektur"-Regeln aktualisiert. Weitere Informationen finden Sie unter [reagieren auf und](../modeling/responding-to-and-propagating-changes.md)weitergeben von Änderungen.

 Es ist jedoch sinnvoll, einige explizite Änderungen an Formen in Eigenschaften vorzunehmen, die unabhängig von den Modellelementen sind. Beispielsweise können Sie folgende Eigenschaften ändern:

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> : bestimmt die Höhe und Breite der Form.

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> -Position in Bezug auf die übergeordnete Form oder das übergeordnete Diagramm

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> -der Satz von Stiften und Pinsel zum Zeichnen der Form oder des Verbindungs-und-Anschlusses

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> -macht die Form unsichtbar

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> -macht die Form sichtbar nach einem `Hide()`

### <a name="creating-an-element-and-its-shape"></a><a name="merge"></a> Erstellen eines Elements und seiner Form

Wenn Sie ein Element erstellen und es mit der Struktur der Einbettungs Beziehungen verknüpfen, wird automatisch eine Form erstellt und zugeordnet. Dies erfolgt durch die "Fixup"-Regeln, die am Ende der Transaktion ausgeführt werden. Die Form wird jedoch an einem automatisch zugewiesenen Speicherort angezeigt, und die Form, Farbe und andere Features haben Standardwerte. Um zu steuern, wie die Form erstellt wird, können Sie die Merge-Funktion verwenden. Sie müssen zunächst die Elemente, die Sie hinzufügen möchten, zu einer Element Gruppe hinzufügen und dann die Gruppe in das Diagramm zusammenführen.

Diese Methode:

- Legt den Namen fest, wenn Sie eine Eigenschaft als Elementnamen zugewiesen haben.

- Beachtet alle elementmergedirektiven, die Sie in der DSL-Definition angegeben haben.

In diesem Beispiel wird eine Form an der Mausposition erstellt, wenn der Benutzer auf das Diagramm doppelklickt. In der DSL-Definition für dieses Beispiel wurde die- `FillColor` Eigenschaft von verfügbar `ExampleShape` gemacht.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
partial class MyDiagram
{
  public override void OnDoubleClick(DiagramPointEventArgs e)
  {
    base.OnDoubleClick(e);

    using (Transaction t = this.Store.TransactionManager
        .BeginTransaction("double click"))
    {
      ExampleElement element = new ExampleElement(this.Store);
      ElementGroup group = new ElementGroup(element);

      { // To use a shape of a default size and color, omit this block.
        ExampleShape shape = new ExampleShape(this.Partition);
        shape.ModelElement = element;
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);
        shape.FillColor = System.Drawing.Color.Azure;
        group.Add(shape);
      }

      this.ElementOperations.MergeElementGroupPrototype(
        this,
        group.CreatePrototype(),
        PointD.ToPointF(e.MousePosition));
      t.Commit();
    }
  }
}
```

 Wenn Sie mehr als eine Form angeben, legen Sie ihre relativen Positionen mithilfe von fest `AbsoluteBounds` .

 Mit dieser Methode können Sie auch die Farbe und andere verfügbare Eigenschaften von Connectors festlegen.

### <a name="use-transactions"></a>Verwenden von Transaktionen
 Formen, Connectors und Diagramme sind Untertypen von <xref:Microsoft.VisualStudio.Modeling.ModelElement> und im Store. Daher müssen Sie Änderungen nur innerhalb einer Transaktion vornehmen. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden von Transaktionen zum Aktualisieren des Modells](../modeling/how-to-use-transactions-to-update-the-model.md).

## <a name="document-view-and-document-data"></a><a name="docdata"></a> Dokument Ansicht und Dokument Daten
 ![Klassendiagramm für Standarddiagrammtypen](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>Partitionen speichern
 Wenn ein Modell geladen wird, wird das zugehörige Diagramm gleichzeitig geladen. In der Regel wird das Modell in "Store. DefaultPartition" geladen, und der Diagramm Inhalt wird in eine andere Partition geladen. In der Regel wird der Inhalt der einzelnen Partitionen geladen und in einer separaten Datei gespeichert.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [Validierung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md)
- [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)
- [Gewusst wie: Verwenden von Transaktionen zum Aktualisieren des Modells](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Integrieren von Modellen mit Visual Studio-ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Reagieren auf und Propagieren von Änderungen](../modeling/responding-to-and-propagating-changes.md)
