---
title: Navigieren im UML-Modell | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: 6d789b6d-2aa9-4ceb-92c4-84a300065a76
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23f87c81e43b2dfafb1c9c78c3135faff809bb9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "74289857"
---
# <a name="navigate-the-uml-model"></a>Navigieren im UML-Modell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema werden die Haupttypen des UML-Modells vorgestellt.

## <a name="the-model-elements-model-and-model-store"></a>Modellelemente, Modell und Modellspeicher
 Die in der Assembly definierten Typen **Microsoft.VisualStudio.Uml.Interfaces.dll** den Typen entsprechen, die in der [UML-Spezifikation, Version 2.1.2, definiert sind](https://www.omg.org/spec/UML/2.1.2/Superstructure/PDF/).

 Die Typen in der UML-Spezifikation werden in Visual Studio als Schnittstellen realisiert. Dem Namen jedes Typs wird der Buchstabe "I" vorangestellt. Beispiel: [IElement](/previous-versions/dd516035(v=vs.140)), [iCLASS](/previous-versions/dd523539%28v%3dvs.140%29), [IOperation](/previous-versions/dd481186(v=vs.140)).

 Alle Typen mit Ausnahme von IElement erben Eigenschaften von einem oder mehreren Obertypen (Supertypes).

- Eine Zusammenfassung der Modelltypen finden Sie unter [UML-Modellelement Typen](../modeling/uml-model-element-types.md).

- Ausführliche Informationen zur API finden Sie unter [API-Referenz für UML-Modellierungs Erweiterbarkeit](../modeling/api-reference-for-uml-modeling-extensibility.md).

### <a name="relationships"></a>Beziehungen
 Eigenschaften und Beziehungen, die in der UML-Spezifikation definiert sind, werden als .NET-Eigenschaften implementiert.

 Die meisten Beziehungen ermöglichen eine bidirektionale Navigation. Eine Beziehung entspricht einem Eigenschaftenpaar mit je einer Eigenschaft im Typ an beiden Enden. Beispielsweise stellen die `IElement.Owner`-Eigenschaft und die `IElement.OwnedElements`-Eigenschaft zwei Enden einer Beziehung dar. Daher ergibt dieser Ausdruck immer "true":

 `IElement c; ...  c.OwnedElements.All(x => x.Owner == c)`

 Viele Beziehungen wie IAssociation werden auch durch ein Objekt dargestellt, das über eigene Eigenschaften verfügen kann.

 Wenn Sie ein Element aus dem Modell löschen, werden alle Beziehungen, in denen es vorkommt, automatisch gelöscht, und die Eigenschaft am anderen Ende wird aktualisiert.

 Wenn die UML-Spezifikation einer Eigenschaft eine Multiplizität von 0..1 zuweist, kann diese den Wert `null` haben. Eine Multiplizität mit einem maximalen Wert größer als 1 bedeutet, dass die .net-Eigenschaft den Typ hat: `IEnumerable<` *Type* `>` .

 Weitere Informationen zum Durchsuchen von Beziehungen finden Sie unter [Navigieren in Beziehungen mit der UML-API](../modeling/navigate-relationships-with-the-uml-api.md).

### <a name="the-ownership-tree"></a>Besitzstruktur
 Ein Modell enthält eine Struktur von [IElement](/previous-versions/dd516035(v=vs.140)) -Objekten. Jedes Element verfügt über die `OwnedElements`-Eigenschaft und über die `Owner`-Eigenschaft.

 In den meisten Fällen wird auf die Ziele der `Owner`-Eigenschaft und der `OwnedElements`-Eigenschaft auch von anderen Eigenschaften verwiesen, die über spezifischere Namen verfügen. So befindet sich jeder UML-Vorgang beispielsweise im Besitz einer UML-Klasse. Daher verfügt [IOperation](/previous-versions/dd481186(v=vs.140)) über eine Eigenschaft mit dem Namen [IOperation. Class](/previous-versions/dd473473%28v%3dvs.140%29)und in jedem [IOperation](/previous-versions/dd481186(v=vs.140)) -Objekt `Class == Owner` .

 Das oberste Element der Struktur, das keinen Besitzer hat, ist ein `AuxiliaryConstructs.IModel` . Das IModel ist in einer enthalten `IModelStore` , bei der es sich um die [IModelStore. root](/previous-versions/ee789368(v=vs.140))-Datei handelt.

 Jedes Modellelement wird mit einem Besitzer erstellt. Weitere Informationen finden Sie unter [Erstellen von Elementen und Beziehungen in UML-Modellen](../modeling/create-elements-and-relationships-in-uml-models.md).

 ![Klassendiagramm: Modell, Diagramm, Form und Element](../modeling/media/uml-mm1.png)

## <a name="shapes-and-diagrams"></a>Formen und Diagramme
 Elemente im UML-Modell können in einem Diagramm angezeigt werden. Je nach Diagrammtyp können unterschiedliche Untertypen von IElement anzeigen.

 In einigen Fällen kann ein Element in mehr als einem Diagramm angezeigt werden. IUseCase-Elemente können z. B. über mehrere IShapes verfügen, die in einem Diagramm oder in unterschiedlichen Diagrammen angezeigt werden können.

 Formen werden in einer Struktur angeordnet. Die Ränder der Struktur werden durch die ParentShape-Eigenschaft und die ChildShapes-Eigenschaft dargestellt. Diagramme sind die einzigen Formen, die keine übergeordneten Elemente haben. Die Formen auf der Oberfläche eines Diagramms bestehen aus kleineren Teilen. So weist eine Klassenform etwa Depots für Attribute und Operationen auf.

 Weitere Informationen zu Formen finden Sie unter [Anzeigen eines UML-Modells in Diagrammen](../modeling/display-a-uml-model-on-diagrams.md).

## <a name="access-to-the-model-in-extensions"></a>Zugreifen auf das Modell in Erweiterungen
 In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Erweiterungen, die als MEF-Komponenten definiert werden, können Sie Eigenschaften deklarieren, die Informationen aus dem Kontext importieren, in dem die Erweiterung ausgeführt wird.

|Attributtyp|Bietet Zugriff auf|Weitere Informationen|
|--------------------|----------------------------------|----------------------|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation<br /><br /> .IDiagramContext<br /><br /> (in Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll)|Aktuelles Fokusdiagramm|[Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|
|Microsoft.VisualStudio.Modeling.ExtensionEnablement<br /><br /> .ILinkedUndoContext<br /><br /> (in Microsoft.VisualStudio.Modeling.Sdk.[version].dll)|Gruppieren von Änderungen in Transaktionen|[Verknüpfen von UML-Modellaktualisierungen mithilfe von Transaktion](../modeling/link-uml-model-updates-by-using-transactions.md)|
|Microsoft.VisualStudio.Shell .SVsServiceProvider<br /><br /> (in Microsoft.VisualStudio.Shell.Immutable.[version].dll)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Host. Von dort können Sie auf Dateien, Projekte und andere Aspekte zugreifen.|[Öffnen eines UML-Modells über die Visual Studio-API](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)|

### <a name="to-get-the-context"></a>So rufen Sie den Kontext ab
 Deklarieren Sie eine oder beide der folgenden Schnittstellen in der Erweiterungsklasse:

```
[Import] public IDiagramContext DiagramContext { get; set; }

```

 Das Managed Extensibility Framework (MEF) bindet diese Schnittstellen an Definitionen, aus denen Sie das aktuelle Diagramm, den Modellspeicher, das Stammobjekt usw. abrufen können:

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
IClassDiagram classDiagram = diagram as IClassDiagram;
       // or diagrams of other types
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IDiagram diagram in modelStore.Diagrams) {...}
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}
```

### <a name="to-get-the-current-selection"></a>So rufen Sie die aktuelle Auswahl ab

```
// All selected shapes and their elements
foreach (IShape shape in diagram.SelectedShapes)
{
   IDiagram selectedDiagram = shape as IDiagram;
   if (selectedDiagram != null)
   { // no shape selected - user right-clicked the diagram
     ... Context.CurrentDiagram ...
   }
   else
   {
     IElement selectedElement = shape.Element;
   ...}
// All selected shapes that display a specfic type of element
foreach (IShape<IInterface> in
   diagram.GetSelectedShapes<IInterface>())
{...}
```

## <a name="accessing-another-model-or-diagrams"></a>Zugriff auf ein anderes Modell oder Diagramme
 Sie können:

- Erstellen Sie mit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-ModelBus Links zwischen Elementen in unterschiedlichen Modellen. Weitere Informationen finden Sie unter [integrieren von UML-Modellen in andere Modelle und Tools](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- Laden Sie ein Modellierungsprojekt und Diagramme im schreibgeschützten Modus, ohne sie in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Benutzeroberfläche anzuzeigen. Weitere Informationen finden Sie unter [Lesen eines UML-Modells im Programmcode](../modeling/read-a-uml-model-in-program-code.md).

- Öffnen Sie ein Modellierungsprojekt und die darin enthaltenen Diagramme in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], und greifen Sie dann auf den Inhalt zu. Weitere Informationen finden Sie unter [Öffnen eines UML-Modells mithilfe der Visual Studio-API](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).

## <a name="see-also"></a>Weitere Informationen

- [Erweitern von UML-Modellen und -Diagrammen](../modeling/extend-uml-models-and-diagrams.md)
- [Programmieren mit der UML-API](../modeling/programming-with-the-uml-api.md)
