---
title: 'Gewusst wie: Erweitern des DSL-Designers'
description: Erfahren Sie, wie Sie Erweiterungen für den Designer erstellen können, den Sie zum Bearbeiten von DSL-Definitionen (Domain-Specific Language) verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a7a48c5a314dd52893bc7f0675915f0d68297ab
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361507"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>Gewusst wie: Erweitern des DSL-Designers

Sie können Erweiterungen für den Designer vornehmen, mit dem Sie DSL-Definitionen bearbeiten. Zu den Erweiterungs Typen, die Sie vornehmen können, zählen das Hinzufügen von Menübefehlen, das Hinzufügen von Handlern für Drag-und Doppelklick Gesten und Regeln, die ausgelöst werden, wenn bestimmte Werte oder Beziehungen geändert werden. Die Erweiterungen können als Visual Studio-Integrations Erweiterung (VSIX) verpackt und an andere Benutzer verteilt werden.

Beispielcode und weitere Informationen zu dieser Funktion finden Sie im Visual Studio- [SDK für Visualisierung und Modellierung](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).

## <a name="set-up-the-solution"></a>Einrichten der Lösung

Richten Sie ein Projekt ein, das den Code der Erweiterung enthält, und ein VSIX-Projekt, das das Projekt exportiert. Die Projekt Mappe kann andere Projekte enthalten, die in dieselbe VSIX integriert sind.

### <a name="to-create-a-dsl-designer-extension-solution"></a>So erstellen Sie eine DSL-Designer-Erweiterungs Lösung

1. Erstellen Sie ein neues Projekt mithilfe der- **Klassenbibliothek** -Projektvorlage. Dieses Projekt enthält den Code der Erweiterungen.

2. Erstellen Sie ein neues **VSIX-Projekt** Projekt.

     Wählen Sie zu Projekt Mappe **Hinzufügen**.

     " *Source. Extension. vsixmanifest* " wird im VSIX-Manifest-Editor geöffnet.

3. Klicken Sie oberhalb des Inhalts Felds auf **Inhalt hinzufügen**.

4. Legen Sie im Dialogfeld **Inhalt hinzufügen** **einen Inhaltstyp** auf die **MEF-Komponente** auswählen fest, und legen Sie **Projekt** auf das Klassen Bibliotheksprojekt fest.

5. Klicken Sie auf **Editionen auswählen** , und stellen Sie sicher, dass **Visual Studio Enterprise** aktiviert ist.

6. Stellen Sie sicher, dass es sich bei dem VSIX-Projekt um das Startprojekt der Projekt Mappe handelt.

7. Fügen Sie im Klassen Bibliotheksprojekt Verweise auf die folgenden Assemblys hinzu:

     Microsoft. VisualStudio. coreutility

     Microsoft. VisualStudio. Modeling. SDK. 11.0

     Microsoft. VisualStudio. Modeling. SDK. Diagramms. 11.0

     Microsoft. VisualStudio. Modeling. SDK. DslDefinition. 11.0

     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

     System.ComponentModel.Composition

     System.Drawing

     System.Drawing.Design

     System.Windows.Forms

## <a name="test-and-deployment"></a>Test und Bereitstellung

Erstellen Sie die Projekt Mappe, und führen Sie Sie aus, um eine der Erweiterungen in diesem Thema zu testen. Eine experimentelle Instanz von Visual Studio wird geöffnet. Öffnen Sie in dieser Instanz eine DSL-Projekt Mappe. Bearbeiten Sie das DslDefinition-Diagramm. Das Erweiterungs Verhalten ist sichtbar.

Führen Sie die folgenden Schritte aus, um die Erweiterungen für Visual Studio und andere Computer bereitzustellen:

1. Suchen Sie die VSIX-Installationsdatei in Ihrem VSIX-Projekt in bin \\ * \\ \* . VSIX.

2. Kopieren Sie diese Datei auf den Zielcomputer, und doppelklicken Sie dann im Windows-Explorer (oder Datei-Explorer) auf die Datei.

     Der Visual Studio-Erweiterungs-Manager wird geöffnet, um zu bestätigen, dass die Erweiterung installiert wurde.

Um die Erweiterung zu deinstallieren, führen Sie die folgenden Schritte aus:

1. Klicken Sie in Visual Studio im **Menü Extras** auf **Erweiterungs-Manager**.

2. Wählen Sie die Erweiterung aus, und löschen Sie Sie.

## <a name="add-a-shortcut-menu-command"></a>Befehl "Kontextmenü hinzufügen"

Damit ein Kontextmenü Befehl auf der DSL-Designer-Oberfläche oder im Fenster DSL-Explorer angezeigt wird, schreiben Sie eine Klasse, die der folgenden ähnelt.

Die-Klasse muss implementieren `ICommandExtension` und muss über das-Attribut verfügen `DslDefinitionModelCommandExtension` .

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDefinition;
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDesigner;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Command extending the DslDesigner.
  /// </summary>
  [DslDefinitionModelCommandExtension]
  public class MyDslDesignerCommand : ICommandExtension
  {
    /// <summary>
    /// Selection Context for this command
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Is the command visible and active?
    /// This is called when the user right-clicks.
    /// </summary>
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible = true;
      // Is there any selected DomainClasses in the Dsl explorer?
      command.Enabled =
        SelectionContext.AtLeastOneSelected<DomainClass>();

      // Is there any selected ClassShape on the design surface?
      command.Enabled |=
        (SelectionContext.GetCurrentSelection<ClassShape>()
                .Count() > 0);
    }
    /// <summary>
    /// Executes the command
    /// </summary>
    /// <param name="command">Command initiating this action</param>
    public void Execute(IMenuCommand command)
    {
      ...
    }
    /// <summary>
    /// Label for the command
    /// </summary>
    public string Text
    {
      get { return "My Command"; }
    }
  }
}
```

## <a name="handle-mouse-gestures"></a>Mausgesten behandeln

Der Code ähnelt dem Code des Menübefehls.

```csharp
[DslDefinitionModelGestureExtension]
 class MouseGesturesExtensions : IGestureExtension
 {
  /// <summary>
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box
  /// </summary>
  /// <param name="targetElement">Shape element on which the user has clicked</param>
  /// <param name="diagramPointEventArgs">event args for this double-click</param>
  public void OnDoubleClick(ShapeElement targetElement,
       DiagramPointEventArgs diagramPointEventArgs)
  {
   ModelElement modelElement = PresentationElementHelper.
        GetDslDefinitionModelElement(targetElement);
   if (modelElement != null)
   {
    MessageBox.Show(string.Format(
      "Double clicked on {0}", modelElement.ToString()),
      "Model element double-clicked");
   }
  }

  /// <summary>
  /// Tells if the DslDesigner can consume the to-be-dropped information
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we try to drop</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>
  public bool CanDragDrop(ShapeElement targetMergeElement,
        DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    diagramDragEventArgs.Effect = DragDropEffects.Copy;
    return true;
   }
   return false;
  }

  /// <summary>
  /// Processes the drop by displaying the dropped text
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we dropped</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    string[] droppedFiles =
      diagramDragEventArgs.Data.
               GetData(DataFormats.FileDrop) as string[];
    MessageBox.Show(string.Format("Dropped text {0}",
        string.Join("\r\n", droppedFiles)), "Dropped Text");
   }
  }
 }
```

## <a name="respond-to-value-changes"></a>Reagieren auf Wertänderungen

Dieser Handler benötigt ein Domänen Modell, um ordnungsgemäß zu funktionieren. Wir stellen ein einfaches Domänen Modell bereit.

```csharp
using System.Diagnostics;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Rule firing when the type of a domain model property is changed. The change is displayed
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)
  /// </summary>
  [RuleOn(typeof(PropertyHasType))]
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule
  {
    /// <summary>
    /// Method called when the Type of a Domain Property
    /// is changed by the user in a DslDefinition
    /// </summary>
    /// <param name="e"></param>
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)
    {
      // We are only interested in the type
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)
      {
        PropertyHasType relationship =
           e.ElementLink as PropertyHasType;
        DomainType newType = e.NewRolePlayer as DomainType;
        DomainType oldType = e.OldRolePlayer as DomainType;
        DomainProperty property = relationship.Property;

         // We write about the Type change in the debugguer
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",
          property.Name,
          property.Class.Name,
          oldType.GetFullName(false),
          newType.GetFullName(false))
} }  }  );
```

Der folgende Code implementiert ein einfaches Modell. Erstellen Sie eine neue GUID, um den Platzhalter zu ersetzen.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
    /// <summary>
    /// Simplest possible domain model
    /// needed only for extension rules.
    /// </summary>
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]
    public class SimpleDomainModelExtension : DomainModel
    {
        // Id of this domain model extension
        // Please replace this with a new GUID:
        public const string DomainModelId =
                  "00000000-0000-0000-0000-000000000000";

        /// <summary>
        /// Constructor for the domain model extension
        /// </summary>
        /// <param name="store">Store in which the domain model will be loaded</param>
        public SimpleDomainModelExtension(Store store)
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))
        {

        }

        /// <summary>
        /// Rules brought by this domain model extension
        /// </summary>
        /// <returns></returns>
        protected override System.Type[] GetCustomDomainModelTypes()
        {
            return new Type[] {
                     typeof(DomainPropertyTypeChangedRule)
                              };
        }
    }

    /// <summary>
    /// Provider for the DomainModelExtension
    /// </summary>
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]
    public class SimpleDomainModelExtensionProvider
          : DomainModelExtensionProvider
    {
        /// <summary>
        /// Extension model type
        /// </summary>
        public override Type DomainModelType
        {
            get
            {
                return typeof(SimpleDomainModelExtension);
            }
        }

    }
}
```