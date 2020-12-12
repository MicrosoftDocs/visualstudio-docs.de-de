---
title: Aktualisieren von Formen und Konnektoren zur Darstellung des Modells
description: Erfahren Sie, dass Sie in einer domänenspezifischen Sprache in Visual Studio die Darstellung einer Form, die den Zustand des zugrunde liegenden Modells widerspiegelt, festlegen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3d16cbc35c468c0101db479799215bcccf64ef6
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362599"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>Aktualisieren von Formen und Connectors zur Darstellung des Modells

In einer domänenspezifischen Sprache in Visual Studio können Sie festlegen, dass eine Form den Zustand des zugrunde liegenden Modells widerspiegelt.

Die Codebeispiele in diesem Thema sollten einer `.cs` Datei in Ihrem Projekt hinzugefügt werden `Dsl` . Sie benötigen diese Anweisungen in jeder Datei:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Festlegen von Form Zuordnungs Eigenschaften zum Steuern der Sichtbarkeit eines Decorator-Elements

Sie können die Sichtbarkeit eines Decorator-Elements steuern, ohne Programmcode zu schreiben, indem Sie die Zuordnung zwischen der Form und der Domänen Klasse in der DSL-Definition konfigurieren. Weitere Informationen finden Sie unter Vorgehens [Weise beim Definieren einer Domain-Specific Sprache](../modeling/how-to-define-a-domain-specific-language.md).

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Die Farbe und den Stil einer Form als Eigenschaften verfügbar machen

Klicken Sie in der DSL- **Definition mit der** rechten Maustaste auf die Shape-Klasse, zeigen Sie auf verfügbar machen, und klicken Sie dann auf eines der Elemente, z. b. **Füllfarbe**.

Die Form verfügt jetzt über eine Domänen Eigenschaft, die Sie im Programmcode oder als Benutzer festlegen können. Wenn Sie diese z. b. im Programmcode eines Befehls oder einer Regel festlegen möchten, können Sie Folgendes schreiben:

`shape.FillColor = System.Drawing.Color.Red;`

Wenn Sie die Eigenschaften Variable nur unter der Programmsteuerung und nicht vom Benutzer erstellen möchten, wählen Sie im DSL-Definitions Diagramm die neue Domänen Eigenschaft aus, z. b. **Füllfarbe** . Legen Sie dann im Eigenschaftenfenster **die Einstellung für** durchsuchbar auf fest, `false` oder legen Sie die Einstellung **Benutzeroberfläche ist** schreibgeschützt auf fest `true` .

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definieren von Änderungs Regeln, um die Farbe, den Stil oder den Speicherort von Modellelement Eigenschaften abhängig zu machen
 Sie können Regeln definieren, mit denen die Darstellung der Form von anderen Teilen des Modells abhängig ist. Beispielsweise können Sie eine Änderungs Regel für ein Modellelement definieren, die die Farbe der Form aktualisiert, die von den Eigenschaften des Modell Elements abhängig ist. Weitere Informationen zu Änderungs Regeln finden Sie unter [Regeln verbreiten Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).

 Regeln sollten nur verwendet werden, um Eigenschaften zu aktualisieren, die im Speicher verwaltet werden, da Regeln nicht aufgerufen werden, wenn der Befehl "Rückgängig" ausgeführt wird. Dies umfasst keine grafischen Features, wie z. b. die Größe und Sichtbarkeit einer Form. Informationen zum Aktualisieren dieser Funktionen einer Form finden Sie unter [Aktualisieren von nicht-Store-grafischen Features](#OnAssociatedProperty).

 Im folgenden Beispiel wird davon ausgegangen, dass Sie `FillColor` als Domänen Eigenschaft verfügbar gemacht haben, wie im vorherigen Abschnitt beschrieben.

```csharp
[RuleOn(typeof(ExampleElement))]
  class ExampleElementPropertyRule : ChangeRule
  {
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)
    {
      base.ElementPropertyChanged(e);
      ExampleElement element = e.ModelElement as ExampleElement;
      // The rule is called for every property that is updated.
      // Therefore, verify which property changed:
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)
      {
        // There is usually only one shape:
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))
        {
          ExampleShape shape = pel as ExampleShape;
          // Replace this with a useful condition:
          shape.FillColor = element.Name.EndsWith("3")
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;
        }
      }
    }
  }
  // The rule must be registered:
  public partial class OnAssociatedPropertyExptDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(ExampleElementPropertyRule));
      // If you add more rules, list them here.
      return types.ToArray();
    }
  }
```

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Verwenden von onchildkonfiguriertem, um die Eigenschaften einer Form zu initialisieren

Um die Eigenschaften einer Form bei der ersten Erstellung festzulegen, wird die Überschreibung `OnChildConfigured()` in einer partiellen Definition ihrer Diagramm Klasse festgelegt. Die Diagramm Klasse wird in ihrer DSL-Definition angegeben, und der generierte Code befindet sich in " **dsl\generated code\diagram.cs**". Zum Beispiel:

```csharp
partial class MyLanguageDiagram
{
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)
  {
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);
    ExampleShape shape = child as ExampleShape;
    if (shape != null)
    {
      if (!createdDuringViewFixup) return; // Ignore load from file.
      ExampleElement element = shape.ModelElement as ExampleElement;
      // Replace with a useful condition:
      shape.FillColor = element.Name.EndsWith("3")
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;
    }
    // else deal with other types of shapes and connectors.
  }
}
```

Diese Methode kann sowohl für Domänen Eigenschaften als auch für nicht-Speicherfunktionen verwendet werden, z. b. die Größe der Form.

## <a name="use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a> Verwenden von associatevaluewith () zum Aktualisieren anderer Funktionen einer Form

Für einige Funktionen einer Form, z. b. ob Sie einen Schatten oder den Pfeil Stil eines Verbindungs Diensts aufweist, gibt es keine integrierte Methode, die Funktion als Domänen Eigenschaft verfügbar zu machen.  Änderungen an solchen Features unterliegen nicht der Kontrolle des Transaktions Systems. Daher ist es nicht angebracht, Sie mithilfe von Regeln zu aktualisieren, da Regeln nicht aufgerufen werden, wenn der Benutzer den Befehl "Rückgängig" ausführt.

Stattdessen können Sie diese Features mithilfe von aktualisieren <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> . Im folgenden Beispiel wird der Pfeil Stil eines Connector durch einen Wert einer Domänen Eigenschaft in der Beziehung gesteuert, die der Connector anzeigt:

```csharp
public partial class ArrowConnector // My connector class.
{
    /// <summary>
    /// Called whenever a registered property changes in the associated model element.
    /// </summary>
    /// <param name="e"></param>
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)
    {
      base.OnAssociatedPropertyChanged(e);
      // Can be called for any property change. Therefore,
      // Verify that this is the property we're interested in:
      if ("IsDirected".Equals(e.PropertyName))
      {
        if (e.NewValue.Equals(true))
        { // Update the shape's built-in Decorator feature:
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;
        }
        else
        {
          this.DecoratorTo = null; // No arrowhead.
        }
      }
    }

    // OnAssociatedPropertyChanged is called only for properties
    // that have been registered using AssociateValueWith().
    // InitializeResources is a convenient place to call this.
    // This method is invoked only once per class, even though
    // it is an instance method.
    protected override void InitializeResources(StyleSet classStyleSet)
    {
      base.InitializeResources(classStyleSet);
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);
      // Add other properties here.
    }
}
```

`AssociateValueWith()` sollte einmal für jede Domänen Eigenschaft aufgerufen werden, die Sie registrieren möchten. Nachdem er aufgerufen wurde, werden alle Änderungen an der angegebenen Eigenschaft `OnAssociatedPropertyChanged()` in allen Formen aufgerufen, die das Modellelement der Eigenschaft darstellen.

Es ist nicht erforderlich, `AssociateValueWith()` für jede Instanz aufzurufen. Obwohl initializeresources eine Instanzmethode ist, wird Sie nur einmal für jede Shape-Klasse aufgerufen.
