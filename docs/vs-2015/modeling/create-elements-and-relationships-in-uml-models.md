---
title: Erstellen von Elementen und Beziehungen in UML-Modellen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: cae81d32-8cc7-4f7c-9f00-20119952bc51
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ea066aa31cbc1f6408ee55c92a5ca761608f534
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667811"
---
# <a name="create-elements-and-relationships-in-uml-models"></a>Erstellen von Elementen und Beziehungen in UML-Modellen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im Programmcode für eine Visual Studio-Erweiterung können Sie Elemente und Beziehungen erstellen und löschen.

## <a name="create-a-model-element"></a>Erstellen eines Modellelements

### <a name="namespace-imports"></a>Namespaceimporte
 Sie müssen die folgenden `using`-Anweisungen einschließen.

 Die Erstellungsmethoden sind als Erweiterungsmethoden in diesem Namespace definiert:

 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

### <a name="obtain-the-owner-of-the-element-you-want-to-create"></a>Abrufen des Besitzers des zu erstellenden Elements
 Ein Modell bildet eine einzelne Struktur, sodass jedes Element mit Ausnahme des Modellstamms einen Besitzer hat. Der Modellstamm weist den Typ `IModel` auf, der ein Typ von `IPackage` ist.

 Wenn Sie ein Element erstellen, das in einem bestimmten Diagramm angezeigt wird, z. B. im aktuellen Diagramm des Benutzers, erstellen Sie es normalerweise in dem Paket, das mit diesem Diagramm verknüpft ist. Beispiel:

```
IPackage linkedPackage = Context.CurrentDiagram.Element as IPackage;
```

 In dieser Tabelle wird der Besitz von allgemeinen Modellelementen zusammengefasst:

|Zu erstellendes Element|Besitzer|
|---------------------------|-----------|
|`IActor, IUseCase, IComponent, IClass, IInterface, IEnumeration`<br /><br /> `IActivity, IInteraction`|`IPackage, IModel`|
|`IAttribute, IOperation`|`IClass, IInterface`|
|`IPart, IPort`|`IComponent`|
|`IAction, IObjectNode`|`IActivity`|
|`ILifeline, IMessage, ICombinedFragment`|`IInteraction`|

### <a name="invoke-the-create-method-on-the-owner"></a>Aufrufen der Create-Methode für den Besitzer
 Der Methodenname hat folgendes Format: `Create` *ownedtype* `()` . Beispiel:

```
IUseCase usecase1 = linkedPackage.CreateUseCase();
```

 Einige Typen verfügen über komplexere Erstellungsmethoden, insbesondere in Sequenzdiagrammen. Siehe [Bearbeiten von UML-Sequenzdiagrammen mit der UML-API](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 Für einige Elementtypen kann der Besitzer eines Elements während der Elementlebensdauer mithilfe von `SetOwner(newOwner)` geändert werden.

### <a name="set-the-name-and-other-properties"></a>Festlegen des Namens und anderer Eigenschaften

```
usecase1.Name = "user logs in";
```

### <a name="example"></a>Beispiel

```
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.Uml.Extensions;
...
 void InstantiateObserverPattern (IPackage package, string namePrefix)
 {    IInterface observer = package.CreateInterface();
      observer.Name = namePrefix + "Observer";
      IOperation operation = observer.CreateOperation();
      operation.Name = "Update";
      IClass subject = package.CreateClass();
      subject.Name = namePrefix + "Subject"; ...
```

## <a name="create-an-association"></a>Erstellen einer Zuordnung

#### <a name="to-create-an-association"></a>So erstellen Sie eine Zuordnung

1. Rufen Sie den Besitzer der Zuordnung ab. Dabei handelt es sich normalerweise um das Paket oder Modell, in dem das Quellende der Beziehung enthalten ist.

2. Rufen Sie die erforderliche Create-Methode für den Besitzer auf.

3. Legen Sie die Eigenschaften der Beziehung fest, z. B. den Namen.

     Beispiel:

    ```
    IAssociation association = subject.Package.CreateAssociation(subject, observer);
    association .Name = "Observes";
    ```

4. Legen Sie die Eigenschaften der beiden Enden der Beziehung fest. Es sind immer zwei `MemberEnds` vorhanden. Beispiel:

    ```
    association .MemberEnds[0].Name = "subject";   // role name
    association .MemberEnds[1].Name = "observers"; // role name
    association .MemberEnds[1].SetBounds("0..*");
                // multiplicity defaults to "1"
    association.MemberEnds[0].Aggregation = AggregationKind.Composite;
    ```

## <a name="create-a-generalization"></a>Erstellen einer Generalisierung

```
IGeneralization generalization =
  subclass.CreateGeneralization(superClass);
```

## <a name="delete-an-element-relationship-or-generalization-from-the-model"></a>Löschen eines Elements, einer Beziehung oder einer Generalisierung aus dem Modell

```
anElement.Delete();
```

 Wenn Sie ein Element aus einem Modell löschen, gilt Folgendes:

- Jede Beziehung, die mit dem Element verknüpft ist, wird ebenfalls gelöscht.

- Jede Form, die das Element im Diagramm dargestellt hat, wird ebenfalls gelöscht.

## <a name="see-also"></a>Weitere Informationen
 [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md) [Anzeigen eines UML-Modells in Diagrammen](../modeling/display-a-uml-model-on-diagrams.md)
