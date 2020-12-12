---
title: Anpassen von Text- und Image-Feldern
description: Erfahren Sie mehr über das Anpassen von Text-und Bilddateien. Wenn Sie einen Text-Decorator in einer Form definieren, wird er auch durch ein Textfeld dargestellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6effda90580a184bb8ebfb8c4f4830dc6cb844d5
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362858"
---
# <a name="customizing-text-and-image-fields"></a>Anpassen von Text- und Image-Feldern
Wenn Sie einen Text-Decorator in einer Form definieren, wird er durch ein Textfeld dargestellt. Beispiele für die Initialisierung von textfields und anderen shapefields-Werten finden Sie unter dsl\generatedcode\shapes.cs in ihrer DSL-Lösung.

 Ein TextField-Objekt ist ein Objekt, das einen Bereich innerhalb einer Form verwaltet, z. b. den Platz, der einer Bezeichnung zugewiesen ist. Eine TextField-Instanz wird von vielen Formen derselben Klasse gemeinsam genutzt. Die TextField-Instanz speichert den Text der Bezeichnung nicht separat für jede Instanz: stattdessen `GetDisplayText(ShapeElement)` nimmt die Methode die Form als Parameter an und kann den Text nachschlagen, der vom aktuellen Zustand der Form und dem zugehörigen Modellelement abhängig ist.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Bestimmen der Darstellung eines Textfelds
 Die- `DoPaint()` Methode wird aufgerufen, um das Feld auf dem Bildschirm anzuzeigen. Sie können entweder den Standardwert `DoPaint(),` überschreiben oder einige der Methoden außer Kraft setzen, die er aufruft. Mithilfe der folgenden vereinfachten Version der Standardmethoden können Sie verstehen, wie Sie das Standardverhalten überschreiben:

```csharp
// Simplified version:
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)
{
  string text = GetDisplayText(shape);
  StringFormat format = GetStringFormat(parentShape);
  Brush brush = GetTextBrush(e.View, shape);
  using (Font font = GetFont(shape))
  {
    e.Graphics.DrawString(text, font, brush, format);
  }
}
// StringFormat determines whether the string is centered etc.
// To customize statically for all instances of this shape field,
// assign to DefaultStringFormat.
// To customize dynamically or per shape, override this:
public virtual StringFormat GetStringFormat(ShapeElement shape)
{ return DefaultStringFormat; }

// Override to customize the displayed string:
public virtual string GetDisplayText(ShapeElement shape)
{ return this.GetValue(shape).ToString(); }

// Brush determines the text color.
// To change the brush for every field, change the shape's styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application's styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape's styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application's styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }
```

 Es gibt mehrere andere Paare von `Get` Methoden und `Default` Eigenschaften, z `DefaultMultipleLine/GetMultipleLine()` . b.. Sie können der Default-Eigenschaft einen Wert zuweisen, um den Wert für alle Instanzen des Shape-Felds zu ändern. Überschreiben Sie die-Methode, um den Wert von einer Shape-Instanz zu einer anderen oder vom Zustand der Form oder des zugehörigen Modell Elements abhängig zu machen `Get` .

## <a name="static-customizations"></a>Statische Anpassungen
 Wenn Sie jede Instanz dieses Shape-Felds ändern möchten, ermitteln Sie zunächst, ob Sie die-Eigenschaft in der DSL-Definition festlegen können. Beispielsweise können Sie den Schrift Grad und den Schrift Schnitt im Eigenschaftenfenster festlegen.

 Wenn dies nicht der Wert ist, `InitializeShapeFields` Überschreiben Sie die-Methode Ihrer Shape-Klasse, und weisen Sie der entsprechenden `Default...` Eigenschaft des Textfelds einen Wert zu.

> [!WARNING]
> Um dies zu überschreiben `InitializeShapeFields()` , müssen Sie in der DSL-Definition die Eigenschaft **generiert Double abgeleitet** der Shape-Klasse auf festlegen `true` .

 In diesem Beispiel verfügt eine Form über ein Textfeld, das für Benutzerkommentare verwendet wird. Wir möchten die standardmäßige Kommentar Schriftart verwenden. Da es sich um eine Standard Schriftart aus dem Stilsatz handelt, können wir die Standard Schriftart-ID festlegen:

```csharp

 partial class ExampleShape
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Find and update comment field:
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;
      // Use the standard font for comments:
      commentField.DefaultFontId = DiagramFonts.CommentText;
```

## <a name="dynamic-customizations"></a>Dynamische Anpassungen
 Um die Darstellung von dem Zustand einer Form oder des Modell Elements abhängig zu machen, leiten Sie eine eigene Unterklasse von ab, und überschreiben Sie mindestens `TextField` eine `Get...` Methode. Außerdem müssen Sie die initializeshapeer Fields-Methode der Form überschreiben und die Instanz des Textfelds durch eine Instanz Ihrer eigenen Klasse ersetzen.

 Im folgenden Beispiel wird die Schriftart eines Textfelds vom Zustand einer booleschen Domänen Eigenschaft des Modell Elements der Form abhängig.

 Um diesen Beispielcode auszuführen, erstellen Sie eine neue DSL-Lösung mithilfe der Vorlage für minimale Sprache. Fügen Sie `AlternateState` der "ExampleElement"-Domänen Klasse eine boolesche Domänen Eigenschaft hinzu. Fügen Sie der Klasse exampleshape ein symboldecorator-Symbol hinzu, und legen Sie dessen Bild auf eine Bitmapdatei fest. Klicken Sie auf **alle Vorlagen transformieren**. Fügen Sie im DSL-Projekt eine neue Codedatei hinzu, und fügen Sie den folgenden Code ein.

 Um den Code zu testen, drücken Sie F5, und öffnen Sie in der Projekt Mappe Debuggen ein Beispiel Diagramm. Der Standardzustand des Symbols sollte angezeigt werden. Wählen Sie die Form aus, und ändern Sie in der Eigenschaftenfenster den Wert der Eigenschaft **Alternativen** Wert. Die Schriftart des Element namens sollte sich ändern.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...

  partial class ExampleShape
  {
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Replace the text field for NameDecorator:
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;
      shapeFields.Remove(oldField);
      // Replace with my text field based on DSL Definition values:
      MyTextField newField = new MyTextField(oldField);
      shapeFields.Add(newField);
    }
  }
  /// <summary>
  /// Dynamic font depends on state of model element.
  /// </summary>
  public class MyTextField : TextField
  {
    public MyTextField(TextField prototype)
      : base(prototype.Name)
    {
      DefaultText = prototype.DefaultText;
      DefaultFocusable = prototype.DefaultFocusable;
      DefaultAutoSize = prototype.DefaultAutoSize;
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;
      DefaultAccessibleState = prototype.DefaultAccessibleState;
    }

    public override System.Drawing.Font GetFont(ShapeElement parentShape)
    {
      // Access the Boolean domain property of the model element:
      if ((parentShape.ModelElement as ExampleElement).AlternateState)
        return new System.Drawing.Font("Callisto", 14.0f,
               System.Drawing.FontStyle.Italic |
               System.Drawing.FontStyle.Bold);
      else
        return base.GetFont(parentShape);
    }

  }
```

## <a name="style-sets"></a>Stil Gruppen
 Im vorangehenden Beispiel wird gezeigt, wie Sie das Textfeld in eine beliebige Schriftart ändern können, die verfügbar ist. Eine bevorzugte Methode ist jedoch, Sie in eine Gruppe von Stilen zu ändern, die der Form oder der Anwendung zugeordnet ist. Zu diesem Zweck überschreiben Sie <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> oder gettextbrushid ().

 Sie können auch den Stil Satz ihrer Form ändern, indem Sie überschreiben <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A> . Dies hat den Effekt, dass die Schriftarten und Pinsel für alle Form Felder geändert werden.

## <a name="customizing-image-fields"></a>Anpassen von Bildfeldern
 Wenn Sie in einer Form einen Bild-Decorator definieren und eine Bildform definieren, wird der Bereich, in dem die Form angezeigt wird, von einem ImageField verwaltet. Beispiele für die Initialisierung von imagefields und anderen shapefields-Werten finden Sie unter dsl\generatedcode\shapes.cs in ihrer DSL-Lösung.

 Ein ImageField ist ein Objekt, das einen Bereich innerhalb einer Form verwaltet, z. b. den einem Decorator zugewiesenen Raum. Eine ImageField-Instanz wird von vielen Formen derselben Shape-Klasse gemeinsam genutzt. Die ImageField-Instanz speichert kein separates Bild für jede Form: stattdessen `GetDisplayImage(ShapeElement)` nimmt die-Methode die Form als Parameter an und kann das Bild nach dem aktuellen Zustand der Form und dem zugehörigen Modellelement suchen.

 Wenn Sie ein spezielles Verhalten (z. b. ein Variablen Bild) wünschen, können Sie eine eigene Klasse erstellen, die von ImageField abgeleitet ist.

#### <a name="to-create-a-subclass-of-imagefield"></a>So erstellen Sie eine Unterklasse von ImageField

1. Legen Sie die Eigenschaft **generiert Double abgeleitet** der übergeordneten Shape-Klasse in der DSL-Definition fest.

2. Überschreiben `InitializeShapeFields` Sie die-Methode Ihrer Shape-Klasse.

    - Erstellen Sie eine neue Codedatei im DSL-Projekt, und schreiben Sie eine partielle Klassendefinition für die Shape-Klasse. Überschreiben Sie die Methoden Definition dort.

3. Überprüfen Sie den Code von `InitializeShapeFields` in dsl\generatedcode\shapes.cs.

     Rufen Sie in ihrer Überschreibungs Methode die Basis Methode auf, und erstellen Sie dann eine Instanz Ihrer eigenen Bild Feld Klasse. Verwenden Sie dieses, um das Feld reguläres Image in der Liste zu ersetzen `shapeFields` .

## <a name="dynamic-icons"></a>Dynamische Symbole
 In diesem Beispiel wird eine Symbol Änderung abhängig vom Zustand des Modell Elements der Form.

> [!WARNING]
> In diesem Beispiel wird veranschaulicht, wie ein Dynamic Image Decorator-Gerät gemacht wird. Wenn Sie jedoch nur zwischen einem oder zwei Bildern wechseln möchten (abhängig vom Zustand einer Modell Variablen), ist es einfacher, mehrere Bild-Decorator-Elemente zu erstellen, Sie an derselben Position in der Form zu suchen und dann den Sichtbarkeits Filter so festzulegen, dass Sie von bestimmten Werten der Modell Variablen abhängig sind. Um diesen Filter festzulegen, wählen Sie die Form Zuordnung in der DSL-Definition aus, öffnen Sie das Fenster DSL-Details, und klicken Sie auf die Registerkarte Decorators.

 Um diesen Beispielcode auszuführen, erstellen Sie eine neue DSL-Lösung mithilfe der Vorlage für minimale Sprache. Fügen Sie `AlternateState` der "ExampleElement"-Domänen Klasse eine boolesche Domänen Eigenschaft hinzu. Fügen Sie der Klasse exampleshape ein symboldecorator-Symbol hinzu, und legen Sie dessen Bild auf eine Bitmapdatei fest. Klicken Sie auf **alle Vorlagen transformieren**. Fügen Sie im DSL-Projekt eine neue Codedatei hinzu, und fügen Sie den folgenden Code ein.

 Um den Code zu testen, drücken Sie F5, und öffnen Sie in der Projekt Mappe Debuggen ein Beispiel Diagramm. Der Standardzustand des Symbols sollte angezeigt werden. Wählen Sie die Form aus, und ändern Sie in der Eigenschaftenfenster den Wert der Eigenschaft **Alternativen** Wert. Das Symbol sollte dann auf dieser Form um 90 Grad gedreht angezeigt werden.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...
partial class ExampleShape
{
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    /// <param name="shapeFields"></param>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);

      // Replace the image field:
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");
      shapeFields.Remove(oldField);
      // Must keep the same name:
      MyImageField newField = new MyImageField(oldField.Name);
      shapeFields.Add(newField);
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;
    }
  }

  public class MyImageField : ImageField
  {
    public MyImageField(string tag) : base(tag) { }

    /// <summary>
    /// Get the image for this field in the given shape.
    /// </summary>
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)
    {
      ExampleElement element = parentShape.ModelElement as ExampleElement;
      if (element.AlternateState == true)
        return AlternateImage;
      else
        return base.GetDisplayImage(parentShape);
    }

    private System.Drawing.Image alternateImage;
    public System.Drawing.Image AlternateImage
    {
      get
      {
        if (alternateImage == null)
        {
          // Alternate image is a copy of the default, rotated by 90 degrees:
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);
        }
        return alternateImage;
      }
    }
  }
}
```

## <a name="see-also"></a>Siehe auch

- [Definieren von Formen und Konnektoren](../modeling/defining-shapes-and-connectors.md)
- [Festlegen eines Hintergrundbilds für ein Diagramm](../modeling/setting-a-background-image-on-a-diagram.md)
- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)