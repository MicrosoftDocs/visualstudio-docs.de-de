---
title: 'Gewusst wie: Zugreifen auf die und Einschränken der aktuellen Auswahl'
description: Erfahren Sie, wie Sie bestimmen können, auf welches Element der Benutzer mit der rechten Maustaste geklickt hat, wenn Sie einen Befehls-oder Gesten Handler für Ihre domänenspezifische Sprache schreiben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ba656793b630dd55fc2ebc7242e5d45484b0f8e
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363392"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Gewusst wie: Zugreifen auf die und Einschränken der aktuellen Auswahl

Wenn Sie einen Befehls-oder Gesten Handler für Ihre domänenspezifische Sprache schreiben, können Sie bestimmen, mit welchem Element der Benutzer mit der rechten Maustaste geklickt hat. Sie können auch verhindern, dass einige Formen oder Felder ausgewählt werden. Sie können z. b. anordnen, dass die Form, in der es enthalten ist, stattdessen ausgewählt wird, wenn der Benutzer auf einen symboldecorator klickt. Wenn Sie die Auswahl auf diese Weise einschränken, wird die Anzahl von Handlern, die Sie schreiben müssen, reduziert. Außerdem wird der Benutzer leichter, wenn er an eine beliebige Stelle in der Form klicken kann, ohne den Decorator zu vermeiden.

## <a name="access-the-current-selection-from-a-command-handler"></a>Zugreifen auf die aktuelle Auswahl über einen Befehls Handler

Die Befehlssatz Klasse für eine domänenspezifische Sprache enthält die Befehls Handler für Ihre benutzerdefinierten Befehle. Die- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasse, von der die Befehlssatz Klasse für eine domänenspezifische Sprache abgeleitet wird, stellt einige Member für den Zugriff auf die aktuelle Auswahl bereit.

Abhängig vom Befehl benötigt der Befehls Handler möglicherweise die Auswahl im Modell-Designer, im Modell-Explorer oder im aktiven Fenster.

### <a name="to-access-selection-information"></a>So greifen Sie auf Auswahl Informationen zu

1. Die- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasse definiert die folgenden Member, die verwendet werden können, um auf die aktuelle Auswahl zuzugreifen.

    |Member|BESCHREIBUNG|
    |-|-|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>-Methode|Gibt zurück, wenn eines der `true` im Modell-Designer ausgewählten Elemente eine Depot-Form ist, andernfalls `false` .|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>-Methode|Gibt zurück `true` , wenn das Diagramm im Modell-Designer ausgewählt ist, andernfalls `false` .|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>-Methode|Gibt zurück `true` , wenn im Modell-Designer genau ein Element ausgewählt ist, andernfalls `false` .|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>-Methode|Gibt zurück `true` , wenn im aktiven Fenster genau ein Element ausgewählt ist, andernfalls `false` .|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> -Eigenschaft|Ruft eine schreibgeschützte Auflistung der im Modell-Designer ausgewählten Elemente ab.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> -Eigenschaft|Ruft eine schreibgeschützte Auflistung der im aktiven Fenster ausgewählten Elemente ab.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> -Eigenschaft|Ruft das primäre Element der Auswahl im Modell-Designer ab.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> -Eigenschaft|Ruft das primäre Element der Auswahl im aktiven Fenster ab.|

2. Die <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> -Eigenschaft der- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasse ermöglicht den Zugriff auf das <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> -Objekt, das das Modell-Designer-Fenster darstellt, und bietet zusätzlichen Zugriff auf die ausgewählten Elemente im Modell-Designer.

3. Außerdem definiert der generierte Code eine Explorer-Tool Fenster Eigenschaft und eine Explorer-Auswahl Eigenschaft in der Befehlssatz Klasse für die domänenspezifische Sprache.

    - Die Explorer Tool Window-Eigenschaft gibt eine Instanz der Explorer Tool Window-Klasse für die domänenspezifische Sprache zurück. Die Explorer-Tool Fenster Klasse wird von der <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> -Klasse abgeleitet und stellt den Modell-Explorer für die domänenspezifische Sprache dar.

    - Die- `ExplorerSelection` Eigenschaft gibt das ausgewählte Element im Modell-Explorer-Fenster für die domänenspezifische Sprache zurück.

## <a name="determine-which-window-is-active"></a>Bestimmen, welches Fenster aktiv ist

Die- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Schnittstelle enthält Elemente, die den Zugriff auf den aktuellen Auswahl Zustand in der Shell ermöglichen. Sie können ein <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Objekt entweder von der Paket Klasse oder von der Befehlssatz Klasse für die domänenspezifische Sprache über die `MonitorSelection` Eigenschaft, die in der Basisklasse der einzelnen definiert ist, erhalten. Die-Paket Klasse wird von der <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> -Klasse abgeleitet, und die Befehlssatz Klasse wird von der- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasse abgeleitet.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>So bestimmen Sie mithilfe eines Befehls Handlers, welcher Typ von Fenster aktiv ist

1. Die- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> Eigenschaft der- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> Klasse gibt ein <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Objekt zurück, das den Zugriff auf den aktuellen Auswahl Zustand in der Shell ermöglicht.

2. Die- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> Eigenschaft der- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> Schnittstelle ruft den aktiven Auswahl Container ab, der sich vom aktiven Fenster unterscheiden kann.

3. Fügen Sie der Befehlssatz Klasse die folgenden Eigenschaften für die domänenspezifische Sprache hinzu, um zu bestimmen, welcher Typ von Fenster aktiv ist.

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>Auswahl einschränken

Durch Hinzufügen von Auswahlregeln können Sie steuern, welche Elemente ausgewählt werden, wenn der Benutzer ein Element im Modell auswählt. Wenn Sie z. b. dem Benutzer gestatten möchten, eine Reihe von Elementen als einzelne Einheit zu behandeln, können Sie eine Auswahl Regel verwenden.

### <a name="to-create-a-selection-rule"></a>So erstellen Sie eine Auswahl Regel

1. Erstellen einer benutzerdefinierten Codedatei im DSL-Projekt

2. Definieren Sie eine Auswahl Regelklasse, die von der-Klasse abgeleitet wird <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> .

3. Überschreiben <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> Sie die-Methode der Auswahl Regelklasse, um die Auswahlkriterien anzuwenden.

4. Fügen Sie der benutzerdefinierten Codedatei eine partielle Klassendefinition für die classdiagram-Klasse hinzu.

     Die `ClassDiagram` -Klasse wird von der <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> -Klasse abgeleitet und in der generierten Codedatei Diagram.cs im DSL-Projekt definiert.

5. Überschreiben <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> Sie die-Eigenschaft der- `ClassDiagram` Klasse, um die benutzerdefinierte Auswahl Regel zurückzugeben.

     Die Standard Implementierung der- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> Eigenschaft ruft ein Auswahl Regel Objekt ab, das die Auswahl nicht ändert.

### <a name="example"></a>Beispiel

Mit der folgenden Codedatei wird eine Auswahl Regel erstellt, mit der die Auswahl erweitert wird, um alle Instanzen der einzelnen Domänen Formen einzuschließen, die anfänglich ausgewählt wurden.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>