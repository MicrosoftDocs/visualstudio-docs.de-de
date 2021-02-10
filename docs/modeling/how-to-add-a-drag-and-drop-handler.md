---
title: 'Gewusst wie: Hinzufügen eines Drag & Drop-Handlers'
description: Erfahren Sie, wie Sie Ihrer DSL Handler für Drag & Drop-Ereignisse hinzufügen können, damit Benutzer Elemente aus anderen Diagrammen in das Diagramm ziehen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c9e6960cdd84e518b2d58eb77c25278bd52475d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941436"
---
# <a name="how-to-add-a-drag-and-drop-handler"></a>Gewusst wie: Hinzufügen eines Drag & Drop-Handlers

Sie können Ihrer DSL Handler für Drag & Drop-Ereignisse hinzufügen, sodass Benutzer Elemente aus anderen Diagrammen oder aus anderen Teilen von Visual Studio auf das Diagramm ziehen können. Sie können auch Handler für Ereignisse wie Doppelklicks hinzufügen. Drag & amp; Drop-und Doppelklick Handler werden in kombinieren als *Gesten Handler* bezeichnet.

In diesem Thema werden Drag &amp; Drop-Gesten behandelt, deren Ursprung in anderen Diagrammen liegt. Für Verschiebe- und Kopierereignisse innerhalb eines Diagramms könnten Sie alternativ eine Unterklasse von `ElementOperations` definieren. Weitere Informationen finden Sie unter [Anpassen des Kopier Verhaltens](../modeling/customizing-copy-behavior.md). Eine Anpassung der DSL-Definition kann auch möglich sein.

## <a name="defining-gesture-handlers-by-overriding-shapeelement-methods"></a>Definieren von Gestenhandlern durch Überschreiben von ShapeElement-Methoden

`OnDragDrop`, `OnDoubleClick` , `OnDragOver` und andere Methoden können überschrieben werden.

Fügen Sie Ihrem DSL-Projekt eine neue Codedatei hinzu. Bei Gesten Handlern benötigen Sie in der Regel mindestens die folgenden `using` Direktiven:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Linq;
```

Definieren Sie in einer neuen Datei eine partielle Klasse für die Form- oder Diagrammklasse, die auf den Ziehvorgang reagieren soll. Überschreiben Sie die folgenden Methoden:

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragOver%2A>-Diese Methode wird aufgerufen, wenn der Mauszeiger während eines Zieh Vorgangs in die Form eintritt. Die Methode sollte das Element untersuchen, das der Benutzer zieht, und die Effect-Eigenschaft festlegen, um anzugeben, ob der Benutzer das Element auf der Form ablegen kann. Mit der Effect-Eigenschaft wird die Darstellung des Cursors bestimmt, während er sich über dieser Form befindet. Darüber hinaus wird mit der Eigenschaft festgelegt, ob `OnDragDrop()` aufgerufen wird, wenn der Benutzer die Maustaste loslässt.

    ```csharp
    partial class MyShape // MyShape generated from DSL Definition.
    {
        public override void OnDragOver(DiagramDragEventArgs e)
        {
          base.OnDragOver(e);
          if (e.Effect == System.Windows.Forms.DragDropEffects.None
               && IsAcceptableDropItem(e)) // To be defined
          {
            e.Effect = System.Windows.Forms.DragDropEffects.Copy;
          }
        }
    ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragDrop%2A> -Diese Methode wird aufgerufen, wenn der Benutzer die Maustaste loslässt, während sich der Mauszeiger über dieser Form oder diesem Diagramm befindet, wenn er `OnDragOver(DiagramDragEventArgs e)` zuvor `e.Effect` auf einen anderen Wert als festgelegt wurde `None` .

    ```csharp
    public override void OnDragDrop(DiagramDragEventArgs e)
    {
          if (!IsAcceptableDropItem(e))
          {
            base.OnDragDrop(e);
          }
          else
          { // Process the dragged item, for example merging a copy into the diagram
            ProcessDragDropItem(e); // To be defined
          }
    }
    ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDoubleClick%2A> -Diese Methode wird aufgerufen, wenn der Benutzer auf die Form oder das Diagramm doppelklickt.

     Weitere Informationen finden Sie unter Gewusst [wie: Abfangen eines Klick auf eine Form oder einen Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Definieren Sie `IsAcceptableDropItem(e)`, um zu bestimmen, ob das gezogene Element akzeptiert werden kann, und "ProcessDragDropItem(e)", um das Modell zu aktualisieren, wenn das Element abgelegt wird. Diese Methoden müssen das Element zuerst aus den Ereignisargumenten extrahieren. Weitere Informationen hierzu finden Sie unter Gewusst wie: beziehen [eines Verweises auf das gezogene Element](#to-send-an-object-from-a-source-dsl).

## <a name="define-gesture-handlers-by-using-mef"></a>Definieren von Gesten Handlern mit MEF

Nutzen Sie diese Methoden, wenn Entwickler von Drittanbietern in der Lage sein sollen, eigene Handler für Ihre DSL zu definieren. Die Benutzer könnten Erweiterungen von Drittanbietern installieren, nachdem sie Ihre DSL installiert haben.

Mit MEF (Managed Extensibility Framework) können Sie Komponenten definieren, die mit minimaler Konfiguration installiert werden können. Weitere Informationen finden Sie unter [Übersicht über das Managed Extensibility Framework](/dotnet/framework/mef/index).

### <a name="to-define-a-mef-gesture-handler"></a>So definieren Sie einen MEF-Gestenhandler

1. Fügen Sie die **mefextension** -Dateien, die in [Erweitern Ihrer DSL mithilfe von MEF](../modeling/extend-your-dsl-by-using-mef.md)beschrieben werden, zu Ihrem **DSL** -und **dslpackage** -Projekt hinzu.

2. Jetzt können Sie einen Gestenhandler als MEF-Komponente definieren:

    ```csharp
    // This attribute is defined in the generated file
    // DslPackage\MefExtension\DesignerExtensionMetaDataAttribute.cs:
    [MyDslGestureExtension]
    public class MyGestureHandlerClassName : IGestureExtension
    {
      /// <summary>
      /// Called to determine whether a drag onto the diagram can be accepted.
      /// </summary>
      /// <param name="diagramDragEventArgs">Contains a link to the item that is being dragged</param>
      /// <param name="targetMergeElement">The shape or connector that the mouse is over</param>
      /// <returns>True if the item can be accepted on the targetMergeElement.</returns>
      public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null) return false;
        if (target.IsAcceptableDropItem(diagramDragEventArgs)) return true;
        return false;
      }
      public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null || ! target.IsAcceptableDropItem(diagramDragEventArgs)) return;
        // Process the dragged item, for example merging a copy into the diagram:
        target.ProcessDragDropItem(diagramDragEventArgs);
     }
    ```

     Sie können mehr als eine Gestenhandlerkomponente definieren, beispielweise wenn Sie unterschiedliche Typen gezogener Objekte nutzen.

3. Fügen Sie partielle Klassendefinitionen für die Zielform-, Konnektor- oder Diagrammklassen hinzu, und definieren Sie die Methoden `IsAcceptableDropItem()` und `ProcessDragDropItem()`. Diese Methoden müssen beginnen, indem sie das gezogene Element aus den Ereignisargumenten extrahieren. Weitere Informationen finden Sie unter Vorgehens [Weise beim beziehen eines Verweises auf das gezogene Element](#to-send-an-object-from-a-source-dsl).

## <a name="how-to-decode-the-dragged-item"></a>Decodieren des gezogenen Elements

Elemente können aus einem beliebigen Fenster, vom Desktop oder aus einer DSL gezogen werden.

Wenn der Benutzer ein Element auf Ihr Diagramm oder von einem Teil des Diagramm in einen anderen zieht, sind Informationen zum gezogenen Element in `DiagramDragEventArgs` verfügbar. Da der Ziehvorgang bei jedem Objekt auf dem Bildschirm begonnen werden kann, können die Daten in einer Vielzahl von Formaten vorliegen. Ihr Code muss die Formate erkennen, die er verarbeiten kann.

Sie können die Formate ermitteln, in denen die Quellinformationen beim Ziehen verfügbar sein können, indem Sie den Code im Debuggingmodus ausführen und einen Haltepunkt beim Beginn von `OnDragOver()` oder `CanDragDrop()` festlegen. Prüfen Sie die Werte des `DiagramDragEventArgs`-Parameters. Die Informationen werden in zwei Formen bereitgestellt:

- <xref:System.Windows.Forms.IDataObject>  `Data` : Diese Eigenschaft enthält serialisierte Versionen der Quell Objekte (in der Regel in mehr als einem Format). Die nützlichsten Funktionen sind:

  - diagrammventargs. Data. getdataformats ()-listet die Formate auf, in denen Sie das gezogene Objekt decodieren können. Wenn der Benutzer beispielsweise eine Datei vom Desktop zieht, enthalten die verfügbaren Formate den Dateinamen (`FileNameW`).

  - `diagramEventArgs.Data.GetData(format)` -Decodiert das gezogene Objekt im angegebenen Format. Wandeln Sie das Objekt in den geeigneten Typ um. Beispiel:

    `string fileName = diagramEventArgs.Data.GetData("FileNameW") as string;`

    Sie können auch Objekte wie Modellbusverweise aus der Quelle in Ihr eigenes benutzerdefiniertes Format übertragen. Weitere Informationen finden Sie unter Gewusst [wie: Senden von modellbus verweisen per Drag & Drop](#to-send-an-object-from-a-source-dsl).

- <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>`Prototype`-Verwenden Sie diese Eigenschaft, wenn Sie möchten, dass Benutzer Elemente aus einem DSL-oder UML-Modell ziehen. Ein Elementgruppenprototyp enthält mindestens ein Objekt, einen Link und deren Eigenschaftswerte. Er kann auch bei Einfügevorgängen und beim Hinzufügen eines Elements aus der Toolbox verwendet werden. In einem Prototyp werden Objekte und deren Typen anhand der GUID identifiziert. Mit diesem Code kann der Benutzer beispielsweise Klassenelemente aus einem UML-Diagramm oder dem UML-Modell-Explorer ziehen:

    ```csharp
    private bool IsAcceptableDropItem(DiagramDragEventArgs e)
    {
      return e.Prototype != null && e.Prototype.RootProtoElements.Any(element =>
            element.DomainClassId.ToString()
            == "3866d10c-cc4e-438b-b46f-bb24380e1678"); // Accept UML class shapes.
     // Or, from another DSL: SourceNamespace.SourceShapeClass.DomainClassId
    }
    ```

     Um UML-Formen zu akzeptieren, bestimmen Sie die GUIDs der UML-Form Klassen nach Experiment. Denken Sie daran, dass ein Diagramm meist mehr als einen Elementtyp aufweist. Denken Sie außerdem daran, dass ein Objekt, das aus einem DSL- oder UML-Diagramm gezogen wird, die Form und nicht das Modellelement ist.

`DiagramDragEventArgs` verfügt auch über Eigenschaften, die die aktuelle Mauszeigerposition angeben und angeben, ob der Benutzer die STRG-Taste, die Alt-Taste oder die UMSCHALTTASTE drückt.

## <a name="how-to-get-the-original-of-a-dragged-element"></a>Abrufen des Originals eines gezogenen Elements

Wenn es sich bei dem gezogenen Element um ein DSL-Element handelt, können Sie das Quellmodell öffnen und auf das Element zugreifen.

Die Eigenschaften `Data` und `Prototype` der Ereignisargumente enthalten nur einen Verweis auf die gezogene Form. Wenn Sie ein Objekt in der Ziel-DSL erstellen möchten, das vom Prototyp abgeleitet ist, benötigen Sie Zugriff auf das Original. Dies kann beispielsweise das Lesen von Dateiinhalten oder das Navigieren zum Modellelement sein, das durch die Form abgebildet wird. Dabei kann Ihnen Visual Studio-Modellbus helfen.

### <a name="to-prepare-a-dsl-project-for-model-bus"></a>So bereiten Sie ein DSL-Projekt mit Modellbus vor

Machen Sie die Quell-DSL für den Visual Studio-modellbus zugänglich:

1. Öffnen Sie die DSL-Definitionsdatei der Quell-DSL im DSL-Designer. Klicken Sie mit der rechten Maustaste auf die Entwurfs Oberfläche und dann auf **ModelBus aktivieren**. Wählen Sie im Dialogfeld eine oder beide Optionen aus.  Klicken Sie auf **OK**. Der DSL-Projektmappe wird ein neues ModelBus-Projekt hinzugefügt.

2. Klicken Sie auf **alle Vorlagen transformieren** , und erstellen Sie die Lösung neu.

### <a name="to-send-an-object-from-a-source-dsl"></a>So senden Sie ein Objekt aus einer Quell-DSL

1. Überschreiben Sie in der ElementOperations-Unterklasse `Copy()`, sodass ein Modellbusverweis (Model Bus Reference, MBR) in "IDataObject" codiert wird. Diese Methode wird aufgerufen, wenn ein Benutzer einen Ziehvorgang im Quelldiagramm beginnt. Der codierte MBR ist dann im "IDataObject" verfügbar, wenn der Benutzer den Ablegevorgang im Zieldiagramm ausführt.

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Shell;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Integration;
    using Microsoft.VisualStudio.Modeling.Integration.Shell;
    using System.Drawing; // PointF
    using  System.Collections.Generic; // ICollection
    using System.Windows.Forms; // for IDataObject
    ...
    public class MyElementOperations : DesignSurfaceElementOperations
    {
        public override void Copy(System.Windows.Forms.IDataObject data, System.Collections.Generic.ICollection<ModelElement> elements, ClosureType closureType, System.Drawing.PointF sourcePosition)
        {
          base.Copy(data, elements, closureType, sourcePosition);

          // Get the ModelBus service:
          IModelBus modelBus =
              this.Store.GetService(typeof(SModelBus)) as IModelBus;
          DocData docData = ((VSDiagramView)this.Diagram.ActiveDiagramView).DocData;
          string modelFile = docData.FileName;
          // Get an adapterManager for the target DSL:
          ModelBusAdapterManager manager =
              (modelBus.FindAdapterManagers(modelFile).First());
          ModelBusReference modelReference = manager.CreateReference(modelFile);
          ModelBusReference elementReference = null;
          using (ModelBusAdapter adapter = modelBus.CreateAdapter(modelReference))
          {
            elementReference = adapter.GetElementReference(elements.First());
          }

          data.SetData("ModelBusReference", elementReference);
        }
    ...}
    ```

### <a name="to-receive-a-model-bus-reference-from-a-dsl-in-a-target-dsl-or-uml-project"></a>So empfangen Sie einen Modellbusverweis aus einer DSL in einem Ziel-DSL- oder UML-Projekt

1. Fügen Sie im Ziel-DSL-Projekt Projektverweise auf Folgendes hinzu:

    - Das Quell-Dsl-Projekt.

    - Das Quell-ModelBus-Projekt.

2. Fügen Sie in der Codedatei des Gestenhandlers die folgenden Namespaceverweise hinzu:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Integration;
    using SourceDslNamespace;
    using SourceDslNamespace.ModelBusAdapters;
    ```

3. Das folgende Beispiel veranschaulicht, wie Zugriff auf das Quellmodellelement eingerichtet wird:

    ```csharp
    partial class MyTargetShape // or diagram or connector
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
        // Verify that we're being passed an Object Shape.
        ElementGroupPrototype prototype = diagramDragEventArgs.Prototype;
        if (prototype == null) return;
        if (Company.InstanceDiagrams.ObjectShape.DomainClassId
          != prototype.RootProtoElements.First().DomainClassId)
          return;
        // - This is an ObjectShape.
        // - We need to access the originating Store, find the shape, and get its object.

        IModelBus modelBus = targetDropElement.Store.GetService(typeof(SModelBus)) as IModelBus;

        // Unpack the MBR that was packed in Copy:
        ModelBusReference reference = diagramDragEventArgs.Data.GetData("ModelBusReference") as ModelBusReference;
        using (SourceDslAdapter adapter = modelBus.CreateAdapter(reference) as SourceDslAdapter)
        {
          using (ILinkedUndoTransaction t = LinkedUndoContext.BeginTransaction("doing things"))
          {
            // Quickest way to get the shape from the MBR:
            ObjectShape firstShape = adapter.ResolveElementReference<ObjectShape>(reference);

            // But actually there might be several shapes - so get them from the prototype instead:
            IElementDirectory remoteDirectory = adapter.Store.ElementDirectory;
            foreach (Guid shapeGuid in prototype.SourceRootElementIds)
            {
              PresentationElement pe = remoteDirectory.FindElement(shapeGuid) as PresentationElement;
              if (pe == null) continue;
              SourceElement instance = pe.ModelElement as SourceElement;
              if (instance == null) continue;

              // Do something with the object:
          instance...
            }
            t.Commit();
          }
        }
    }
    ```

### <a name="to-accept-an-element-sourced-from-a-uml-model"></a>So akzeptieren Sie ein aus einem UML-Modell stammendes Element

- Mit dem folgenden Codebeispiel wird ein Objekt akzeptiert, das aus einem UML-Diagramm abgelegt wurde.

    ```csharp
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Uml.Classes;
    using System;
    using System.ComponentModel.Composition;
    using System.Linq;
    ...
    partial class TargetShape
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
            EnvDTE.DTE dte = this.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
            // Find the UML project
            foreach (EnvDTE.Project project in dte.Solution.Projects)
            {
              IModelingProject modelingProject = project as IModelingProject;
              if (modelingProject == null) continue; // not a modeling project
              IModelStore store = modelingProject.Store;
              if (store == null) return;

              foreach (IDiagram dd in store.Diagrams())
              {
                  // Get Modeling.Diagram that implements UML.IDiagram:
                  Diagram diagram = dd.GetObject<Diagram>();

                  foreach (Guid elementId in e.Prototype.SourceRootElementIds)
                  {
                    ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;
                    if (shape == null) continue;
                    // This example assumes the shape is a UML class:
                    IClass classElement = shape.ModelElement as IClass;
                    if (classElement == null) continue;

                    // Now do something with the UML class element ...
                  }
            }
          break; // don't try any more projects
    }  }  }
    ```

## <a name="using-mouse-actions-dragging-compartment-items"></a>Verwenden von Mausaktionen: Ziehen von Depotelementen

Sie können einen Handler schreiben, der Mausaktionen für die Felder einer Form abfängt. Im folgenden Beispiel kann der Benutzer die Elemente in einem Depot neu anordnen, indem er Sie mit der Maus zieht.

Um dieses Beispiel zu erstellen, erstellen Sie eine Projekt Mappe mithilfe der Lösungs Vorlage für **Klassendiagramme** . Fügen Sie eine Codedatei und den folgenden Code hinzu. Ändern Sie den Namespace in Ihren eigenen.

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
// This code assumes that the embedding relationships displayed in the compartments
// don't use inheritance (don't have base or derived domain relationships).

namespace Company.CompartmentDrag  // EDIT.
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
  /// click somewhere else in the source shape. Yuk.
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
   dragStartElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item, but still inside the compartment,
  /// create an Action to supervise the cursor and handle subsequent mouse events.
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

- [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md)
- [Bereitstellen von domänenspezifischen Sprachlösungen](msi-and-vsix-deployment-of-a-dsl.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
