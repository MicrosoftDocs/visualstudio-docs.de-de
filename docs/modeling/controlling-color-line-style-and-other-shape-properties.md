---
title: Festlegen von Farbe, Linienstil und anderen Eigenschaften von Formen
description: Stellt Informationen zum Steuern von Formeigenschaften wie Farbe und Linienart bereit.
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 759c7def23cf8ac0df33a75d25eb5bcbcf44b209
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100426"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Steuern von Farbe, Linienstil und anderen Eigenschaften von Formen

Einige Formeigenschaften, z. b. Farbe, können "verfügbar" sein. Das heißt, dass die Eigenschaften mit einer Domänen Eigenschaft der Form verknüpft werden können. Andere müssen direkt gesteuert werden.

## <a name="exposing-a-property"></a>Verfügbar machen einer Eigenschaft
 Einige Formeigenschaften, z. b. Farbe, können mit dem Wert einer Domänen Eigenschaft verknüpft werden.

 Wählen Sie in der DSL-Definition eine Form, einen Connector oder eine Diagramm Klasse aus. Wählen Sie im Kontextmenü die Option verfügbar **Hinzufügen**aus, und wählen Sie dann die gewünschte Eigenschaft aus, z. b. Füllfarbe.

 Die Form verfügt jetzt über eine Domänen Eigenschaft, die Sie im Programmcode oder als Benutzer festlegen können.

## <a name="dynamically-updating-an-exposed-property"></a>Dynamisches Aktualisieren einer verfügbar gemachten Eigenschaft
 In der Regel möchten Sie die verfügbar gemachte Eigenschaft von einer anderen Eigenschaft abhängig machen. Beispielsweise kann es vorkommen, dass eine Form rot werden soll, wenn eine bestimmte Domänen Eigenschaft kleiner als 0 (null) ist. Erstellen Sie eine [Regel](../modeling/rules-propagate-changes-within-the-model.md), um diese Abhängigkeit zu treffen. Beispiel:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```