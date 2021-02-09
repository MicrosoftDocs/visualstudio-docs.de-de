---
title: 'Gewusst wie: Abfangen eines Klicks auf eine Form oder einen Decorator'
description: Erfahren Sie, wie Sie einen Klick auf eine Form oder einen symboldecorator abfangen und wie Sie Klicks, Doppelklicks, Drags und andere Gesten abfangen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2697e3d17e289297bcad57155c1c9ea6f1880acc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922716"
---
# <a name="how-to-intercept-a-click-on-a-shape-or-decorator"></a>Gewusst wie: Abfangen eines Klicks auf eine Form oder einen Decorator
Die folgenden Prozeduren veranschaulichen, wie ein Klick auf eine Form oder einen symboldecorator abgefangen wird. Sie können Klicks, Doppelklicks, Drags und andere Gesten abfangen und das Element dann antworten.

## <a name="to-intercept-clicks-on-shapes"></a>So fangen Sie Klicks auf Formen ab
 Schreiben Sie im DSL-Projekt in einer Code Datei, die von den generierten Code Dateien getrennt ist, eine partielle Klassendefinition für die Shape-Klasse. Überschreiben Sie `OnDoubleClick()` oder eine der anderen Methoden mit einem Namen, der mit beginnt `On...` . Beispiel:

```csharp
public partial class MyShape // change
  {
    public override void OnDoubleClick(DiagramPointEventArgs e)
    {
      base.OnDoubleClick(e);
      System.Windows.Forms.MessageBox.Show("Click");
      e.Handled = true;
  }  }
```

> [!NOTE]
> Legen `e.Handled` Sie auf fest `true` , es sei denn, Sie möchten, dass das Ereignis an die enthaltende Form oder das enthaltende Diagramm

## <a name="to-intercept-clicks-on-decorators"></a>So fangen Sie Klicks auf Decorators ab
 Bild-decoratoren werden auf eine Instanz der ImageField-Klasse übertragen, die über eine OnDoubleClick-Methode verfügt. Sie können die Klicks abfangen, wenn Sie eine ImageField-Unterklasse schreiben. Die Felder werden in der initializeshapeer Fields-Methode eingerichtet. Daher müssen Sie diese Methode ändern, um die Unterklasse anstelle des regulären ImageField zu instanziieren. Die initializeshapeer Fields-Methode befindet sich im generierten Code der Shape-Klasse. Sie können die Shape-Klasse überschreiben, wenn Sie die- `Generates Double Derived` Eigenschaft wie im folgenden Verfahren beschrieben festlegen.

 Obwohl initializeshapeer Fields eine Instanzmethode ist, wird Sie nur einmal für jede Klasse aufgerufen. Daher ist für jedes Feld in jeder Klasse nur eine Instanz von clickableimagefield vorhanden, nicht für jede Form im Diagramm. Wenn der Benutzer auf eine Instanz doppelklickt, müssen Sie identifizieren, welche Instanz gefunden wurde, wie der Code im Beispiel veranschaulicht.

#### <a name="to-intercept-a-click-on-an-icon-decorator"></a>So fangen Sie einen Klick auf einen symboldecorator ab

1. Öffnen oder erstellen Sie eine DSL-Projekt Mappe.

2. Wählen Sie eine Form aus, die ein symboldecorator-Symbol enthält, und ordnen Sie Sie einer Domänen Klasse zu.

3. Erstellen Sie in einer Code Datei, die von den Dateien im `GeneratedCode` Ordner getrennt ist, die neue Unterklasse von ImageField:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using System.Collections.Generic;
    using System.Linq;

    namespace Fabrikam.MyDsl { // Change to your namespace
    internal class ClickableImageField : ImageField
    {
      // You can also override OnClick and so on.
      public override void OnDoubleClick(DiagramPointEventArgs e)
      {
        base.OnDoubleClick(e);
        // Work out which instance was hit.
        MyShape shapeHit = e.HitDiagramItem.Shape as MyShape;
        if (shapeHit != null)
        {
          MyDomainClass element =
              shapeHit.ModelElement as MyDomainClass;
          System.Windows.Forms.MessageBox.Show(
             "Double click on shape for " + element.Name);
          // If we do not set Handled, the event will
          // be passed to the containing shape:
          e.Handled = true;
        }
      }

       public ClickableImageField(string fieldName)
         : base(fieldName)
       { }
    }
    ```

     Legen Sie "behandelt" auf "true" fest, wenn Sie nicht möchten, dass das Ereignis an die enthaltende Form übermittelt wird.

4. Überschreiben Sie die initializeshapeer Fields-Methode in der Shape-Klasse, indem Sie die folgende partielle Klassendefinition hinzufügen.

    ```csharp
    public partial class MyShape // change
    {
     protected override void InitializeShapeFields
          (IList<ShapeField> shapeFields)
     {
      base.InitializeShapeFields(shapeFields);
      // You can see the above method in MyShapeBase
      // in the generated Shapes.cs
      // It has already added fields for the Icons.
      // So you will have to retrieve them and replace with your own.
      ShapeField unwantedField = shapeFields.First
          (field => field.Name == "IconDecorator1");
      shapeFields.Remove(unwantedField);

      // Now replicate the generated code from the base class
      // in Shape.cs, but with your own image constructor.
      ImageField field2 = new ClickableImageField("IconDecorator1");
      field2.DefaultImage = ImageHelper.GetImage(
        MyDslDomainModel.SingletonResourceManager
        .GetObject("MyShapeIconDecorator1DefaultImage"));
          shapeFields.Add(field2);
    }
    ```

1. Erstellen Sie das Projekt, und führen Sie es aus.

2. Doppelklicken Sie auf das Symbol für eine Instanz der Form. Die Testnachricht sollte angezeigt werden.

## <a name="intercepting-clicks-and-drags-on-compartmentshape-lists"></a>Abfangen von Klicks und zieht in "gliementshape"-Listen
 Im folgenden Beispiel können Benutzer Elemente in einer Depot-Form neu anordnen, indem Sie Sie ziehen. So führen Sie den folgenden Code aus:

1. Erstellen Sie eine neue DSL-Projekt Mappe mithilfe der Lösungs Vorlage für **Klassendiagramme** .

    Sie können auch mit einer eigenen Lösung arbeiten, die Depot Formen enthält. Bei diesem Code wird davon ausgegangen, dass es eine Embedding Relationship zwischen den Modellelementen gibt, die durch die Form dargestellt werden, und die in den Depot Listenelementen dargestellten Elemente.

2. Legen Sie die Eigenschaft **generiert Double abgeleitet** der Depot-Form fest.

3. Fügen Sie diesen Code in einer Datei im **DSL** -Projekt hinzu.

4. Passen Sie die Domänen Klassen-und Shape-Namen in diesem Code entsprechend ihrer eigenen DSL an.

   Zusammenfassend funktioniert der Code wie folgt. In diesem Beispiel `ClassShape` ist der Name der Depot Form.

- Eine Reihe von Maus Ereignis Handlern wird bei der Erstellung an jede Depot Instanz angefügt.

- Das- `ClassShape.MouseDown` Ereignis speichert das aktuelle Element.

- Wenn die Maus aus dem aktuellen Element bewegt wird, wird eine Instanz von MouseAction erstellt, mit der der Cursor festgelegt und die Maus bis zur Freigabe erfasst wird.

     Um das stören anderer Mausaktionen (z. b. das Auswählen des Texts eines Elements) zu vermeiden, wird MouseAction erst erstellt, wenn der Mauszeiger das ursprüngliche Element verlassen hat.

     Eine Alternative zum Erstellen einer moust Action wäre, einfach auf mousup zu lauschen. Dies funktioniert jedoch nicht ordnungsgemäß, wenn der Benutzer die Maus loslässt, nachdem er Sie außerhalb des Depots gezogen hat. MouseAction kann die geeignete Aktion ausführen, unabhängig davon, wo die Maus losgelassen wird.

- Wenn die Maus losgelassen wird, ordnet MouseAction. MouseUp die Reihenfolge der Links zwischen den Modellelementen an.

- Durch die Änderung der Rollen Reihenfolge wird eine Regel ausgelöst, die die Anzeige aktualisiert. Dieses Verhalten ist bereits definiert, und es ist kein zusätzlicher Code erforderlich.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Design;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Collections.Generic;
using System.Linq;

// This sample allows users to re-order items in a compartment shape by dragging.

// This example is built on the "Class Diagrams" solution template of VMSDK (DSL Tools).
// You will need to change the following domain class names to your own:
// ClassShape = a compartment shape
// ClassModelElement = the domain class displayed using a ClassShape
// This code assumes that the embedding relationships
// displayed in the compartments don't use inheritance
// (don't have base or derived domain relationships).

namespace Company.CompartmentDrag
{
 /// <summary>
 /// Manage the mouse while dragging a compartment item.
 /// </summary>
 public class CompartmentDragMouseAction : MouseAction
 {
  private ModelElement sourceChild;
  private ClassShape sourceShape;
  private RectangleD sourceCompartmentBounds;

  public CompartmentDragMouseAction(ModelElement sourceChildElement, ClassShape sourceParentShape, RectangleD bounds)
   : base (sourceParentShape.Diagram)
  {
   sourceChild = sourceChildElement;
   sourceShape = sourceParentShape;
   sourceCompartmentBounds = bounds; // For cursor.
  }

  /// <summary>
  /// Call back to the source shape to drop the dragged item.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   sourceShape.DoMouseUp(sourceChild, e);
   this.Cancel(e.DiagramClientView);
   e.Handled = true;
  }

  /// <summary>
  /// Ideally, this shouldn't happen. This action should only be active
  /// while the mouse is still pressed. However, it can happen if you
  /// move the mouse rapidly out of the source shape, let go, and then
  /// click somewhere else in the source shape.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseDown(DiagramMouseEventArgs e)
  {
   base.OnMouseDown(e);
   this.Cancel(e.DiagramClientView);
   e.Handled = false;
  }

  /// <summary>
  /// Display an appropriate cursor while the drag is in progress:
  /// Up-down arrow if we are inside the original compartment.
  /// No entry if we are elsewhere.
  /// </summary>
  /// <param name="currentCursor"></param>
  /// <param name="diagramClientView"></param>
  /// <param name="mousePosition"></param>
  /// <returns></returns>
  public override System.Windows.Forms.Cursor GetCursor(System.Windows.Forms.Cursor currentCursor, DiagramClientView diagramClientView, PointD mousePosition)
  {
   // If the cursor is inside the original compartment, show up-down cursor.
   return sourceCompartmentBounds.Contains(mousePosition)
    ? System.Windows.Forms.Cursors.SizeNS // Up-down arrow.
    : System.Windows.Forms.Cursors.No;
  }
 }

 /// <summary>
 /// Override some methods of the compartment shape.
 /// *** GenerateDoubleDerived must be set for this shape in DslDefinition.dsl. ****
 /// </summary>
 public partial class ClassShape
 {
  /// <summary>
  /// Model element that is being dragged.
  /// </summary>
  private static ClassModelElement dragStartElement = null;
  /// <summary>
  /// Absolute bounds of the compartment, used to set the cursor.
  /// </summary>
  private static RectangleD compartmentBounds;

  /// <summary>
  /// Attach mouse listeners to the compartments for the shape.
  /// This is called once per compartment shape.
  /// The base method creates the compartments for this shape.
  /// </summary>
  public override void EnsureCompartments()
  {
   base.EnsureCompartments();
   foreach (Compartment compartment in this.NestedChildShapes.OfType<Compartment>())
   {
    compartment.MouseDown += new DiagramMouseEventHandler(compartment_MouseDown);
    compartment.MouseUp += new DiagramMouseEventHandler(compartment_MouseUp);
    compartment.MouseMove += new DiagramMouseEventHandler(compartment_MouseMove);
   }
  }

  /// <summary>
  /// Remember which item the mouse was dragged from.
  /// We don't create an Action immediately, as this would inhibit the
  /// inline text editing feature. Instead, we just remember the details
  /// and will create an Action when/if the mouse moves off this list item.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseDown(object sender, DiagramMouseEventArgs e)
  {
   dragStartElement = e.HitDiagramItem.RepresentedElements
     .OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item,
  /// but still inside the compartment, create an Action
  /// to supervise the cursor and handle subsequent mouse events.
  /// Transfer the details of the initial mouse position to the Action.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseMove(object sender, DiagramMouseEventArgs e)
  {
   if (dragStartElement != null)
   {
    if (dragStartElement != e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault())
    {
     e.DiagramClientView.ActiveMouseAction = new CompartmentDragMouseAction(dragStartElement, this, compartmentBounds);
     dragStartElement = null;
    }
   }
  }

  /// <summary>
  /// User has released the mouse button.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseUp(object sender, DiagramMouseEventArgs e)
  {
    dragStartElement = null;
  }

  /// <summary>
  /// Forget the source item if mouse up occurs outside the
  /// compartment.
  /// </summary>
  /// <param name="e"></param>
  public override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   dragStartElement = null;
  }

  /// <summary>
  /// Called by the Action when the user releases the mouse.
  /// If we are still on the same compartment but in a different list item,
  /// move the starting item to the position of the current one.
  /// </summary>
  /// <param name="dragFrom"></param>
  /// <param name="e"></param>
  public void DoMouseUp(ModelElement dragFrom, DiagramMouseEventArgs e)
  {
   // Original or "from" item:
   ClassModelElement dragFromElement = dragFrom as ClassModelElement;
   // Current or "to" item:
   ClassModelElement dragToElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   if (dragFromElement != null && dragToElement != null)
   {
    // Find the common parent model element, and the relationship links:
    ElementLink parentToLink = GetEmbeddingLink(dragToElement);
    ElementLink parentFromLink = GetEmbeddingLink(dragFromElement);
    if (parentToLink != parentFromLink && parentFromLink != null && parentToLink != null)
    {
     // Get the static relationship and role (= end of relationship):
     DomainRelationshipInfo relationshipFrom = parentFromLink.GetDomainRelationship();
     DomainRoleInfo parentFromRole = relationshipFrom.DomainRoles[0];
     // Get the node in which the element is embedded, usually the element displayed in the shape:
     ModelElement parentFrom = parentFromLink.LinkedElements[0];

     // Same again for the target:
     DomainRelationshipInfo relationshipTo = parentToLink.GetDomainRelationship();
     DomainRoleInfo parentToRole = relationshipTo.DomainRoles[0];
     ModelElement parentTo = parentToLink.LinkedElements[0];

     // Mouse went down and up in same parent and same compartment:
     if (parentTo == parentFrom && relationshipTo == relationshipFrom)
     {
      // Find index of target position:
      int newIndex = 0;
      var elementLinks = parentToRole.GetElementLinks(parentTo);
      foreach (ElementLink link in elementLinks)
      {
       if (link == parentToLink) { break; }
       newIndex++;
      }

      if (newIndex < elementLinks.Count)
      {
       using (Transaction t = parentFrom.Store.TransactionManager.BeginTransaction("Move list item"))
       {
        parentFromLink.MoveToIndex(parentFromRole, newIndex);
        t.Commit();
       }
      }
     }
    }
   }
  }

  /// <summary>
  /// Get the embedding link to this element.
  /// Assumes there is no inheritance between embedding relationships.
  /// (If there is, you need to make sure you've got the relationship
  /// that is represented in the shape compartment.)
  /// </summary>
  /// <param name="child"></param>
  /// <returns></returns>
  ElementLink GetEmbeddingLink(ClassModelElement child)
  {
   foreach (DomainRoleInfo role in child.GetDomainClass().AllEmbeddedByDomainRoles)
   {
    foreach (ElementLink link in role.OppositeDomainRole.GetElementLinks(child))
    {
     // Just the assume the first embedding link is the only one.
     // Not a valid assumption if one relationship is derived from another.
     return link;
    }
   }
   return null;
  }
 }
}
```

## <a name="see-also"></a>Weitere Informationen

- [Reagieren auf und Propagieren von Änderungen](../modeling/responding-to-and-propagating-changes.md)
- [Eigenschaften von Decorators](../modeling/properties-of-decorators.md)
