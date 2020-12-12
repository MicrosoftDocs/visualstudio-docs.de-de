---
title: Hinzufügen benutzerdefinierter Eigenschaften zu Abhängigkeitsdiagrammen
description: Erfahren Sie, wie Sie Werte mit jedem Element in einem Abhängigkeits Diagramm speichern können, wenn Sie Erweiterungs Code für Abhängigkeits Diagramme schreiben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3073a42faf0dcc6fbf586847382ba3a83d88ed4
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360766"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Hinzufügen benutzerdefinierter Eigenschaften zu Abhängigkeitsdiagrammen

Wenn Sie Erweiterungs Code für Abhängigkeits Diagramme schreiben, können Sie Werte mit jedem Element in einem Abhängigkeits Diagramm speichern. Die Werte bleiben erhalten, wenn das Diagramm gespeichert und erneut geöffnet wird. Diese Eigenschaften können auch im **Eigenschaften** Fenster angezeigt werden, damit Sie von Benutzern angezeigt und bearbeitet werden können. Beispielsweise können Sie Benutzer für jede Ebene einen regulären Ausdruck angeben lassen und Validierungscode schreiben, um sicherzustellen, dass die Namen der Klassen in jeder Ebene dem Muster entsprechen, das vom Benutzer angegeben wird.

## <a name="non-visible-properties"></a>Nicht sichtbare Eigenschaften

Wenn Sie möchten, dass Ihr Code nur Werte an ein beliebiges Element in einem Abhängigkeits Diagramm anfügt, müssen Sie keine MEF-Komponente definieren. Es ist ein Wörterbuch `Properties` mit dem Namen in [ilayerelement](/previous-versions/ff644511(v=vs.140))vorhanden. Fügen Sie einfach Werte zum Wörterbuch jedes Ebenenelements hinzu, die gemarshallt werden können. Sie werden als Teil des Abhängigkeits Diagramms gespeichert.

## <a name="editable-properties"></a>Bearbeitbare Eigenschaften

**Erste Vorbereitung**

> [!IMPORTANT]
> Nehmen Sie die folgenden Änderungen an den einzelnen Computern vor, auf denen Ebeneneigenschaften angezeigt werden sollen, um die Eigenschaften anzuzeigen:
>
> 1. Führen Sie Notepad mithilfe von **als Administrator ausführen** aus. Öffnen Sie " *%ProgramFiles%\Microsoft Visual Studio [Version] \common7\ide\extensions\microsoft\architecture tools\extensibilityruntime\extension.vsixmanifest*".
> 2. Fügen Sie im **Content** -Element Folgendes hinzu:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
> 3. Öffnen Sie im **Visual Studio-Tools** Abschnitt des Visual Studio-Anwendungs Startmenüs **Developer-Eingabeaufforderung**. Geben Sie Folgendes ein:
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Starten Sie Visual Studio neu.

**Stellen Sie sicher, dass sich der Code in einem VSIX-Projekt befindet**

Wenn Ihre Eigenschaft Teil eines Befehls-, Gesten-oder Validierungs Projekts ist, müssen Sie nichts hinzufügen. Der Code für die benutzerdefinierte Eigenschaft sollte in einem Visual Studio-Erweiterungsprojekt definiert werden, das als MEF-Komponente definiert wird. Weitere Informationen finden Sie unter [Hinzufügen von Befehlen und Gesten zu Abhängigkeits Diagrammen](../modeling/add-commands-and-gestures-to-layer-diagrams.md) oder [Hinzufügen einer benutzerdefinierten Architektur Validierung zu Abhängigkeits Diagrammen](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

**Definieren der benutzerdefinierten Eigenschaft**

Um eine benutzerdefinierte Eigenschaft zu erstellen, definieren Sie eine Klasse folgendermaßen:

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

Sie können Eigenschaften für [ilayerelement](/previous-versions/ff644511(v=vs.140)) oder eine der abgeleiteten Klassen definieren, die Folgendes umfassen:

- `ILayerModel` -das Modell

- `ILayer` -jede Ebene

- `ILayerDependencyLink` - die Links zwischen Ebenen

- `ILayerComment`

- `ILayerCommentLink`

## <a name="example"></a>Beispiel

Der folgende Code entspricht einem typischen benutzerdefinierten Eigenschaftendeskriptor. Er definiert eine boolesche Eigenschaft für das Ebenenmodell (`ILayerModel`), mit dem der Benutzer Werte für eine benutzerdefinierte Validierungsmethode bereitstellen kann.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;

namespace MyNamespace
{
  /// <summary>
  /// Custom properties are added to the Layer Designer via a custom
  /// Property Descriptor. We have to export this Property Descriptor
  /// using MEF to make it available in the Layer Designer.
  /// </summary>
  [Export(typeof(IPropertyExtension))]
  public class AllTypesMustBeReferencedProperty
      : PropertyExtension<ILayerModel>
  {
    /// <summary>
    /// Each custom property must have a unique name.
    /// Usually we use the full name of this class.
    /// </summary>
    public static readonly string FullName =
      typeof(AllTypesMustBeReferencedProperty).FullName;

    /// <summary>
    /// Construct the property. Notice the use of FullName.
    /// </summary>
    public AllTypesMustBeReferencedProperty()
            : base(FullName)
    {  }

    /// <summary>
    /// The display name is shown in the Properties window.
    /// We therefore use a localizable resource.
    /// </summary>
    public override string DisplayName
    {
      get { return Strings.AllTypesMustBeReferencedDisplayName; }
    }

    /// <summary>
    /// Description shown at the bottom of the Properties window.
    /// We use a resource string for easier localization.
    /// </summary>
    public override string Description
    {
      get { return Strings.AllTypesMustBeReferencedDescription; }
    }

    /// <summary>
    /// This is called to set a new value for this property. We must
    /// throw an exception if the value is invalid.
    /// </summary>
    /// <param name="component">The target ILayerElement</param>
    /// <param name="value">The new value</param>
    public override void SetValue(object component, object value)
    {
      ValidateValue(value);
      base.SetValue(component, value);
    }
    /// <summary>
    /// Helper to validate the value.
    /// </summary>
    /// <param name="value">The value to validate</param>
    private static void ValidateValue(object value)
    {  }

    public override Type PropertyType
    { get { return typeof(bool); } }

    /// <summary>
    /// The segment label of the properties window.
    /// </summary>
    public override string Category
    {
      get
      {
        return Strings.AllTypesMustBeReferencedCategory;
      }
    }
  }
}
```

## <a name="see-also"></a>Siehe auch

- [Erweitern von Abhängigkeitsdiagrammen](../modeling/extend-layer-diagrams.md)
