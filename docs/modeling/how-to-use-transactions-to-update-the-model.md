---
title: 'Gewusst wie: Verwenden von Transaktionen zum Aktualisieren des Modells'
description: Erfahren Sie, dass Transaktionen sicherstellen, dass Änderungen, die an dem Speicher vorgenommen wurden, als Gruppe behandelt werden und wie Transaktionen zum Aktualisieren des Modells verwendet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69a50ebdc7fff425224a454a491f05846105159d
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363834"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Gewusst wie: Verwenden von Transaktionen zum Aktualisieren des Modells
Transaktionen stellen sicher, dass Änderungen, die an dem Speicher vorgenommen wurden, als Gruppe behandelt werden. Für Änderungen, die gruppiert werden, kann ein Commit oder ein Rollback als einzelne Einheit ausgeführt werden.

 Jedes Mal, wenn der Programmcode Elemente im Speicher im Visual Studio-Visualisierungs-und Modellierungs-SDK ändert, hinzufügt oder löscht, muss dies innerhalb einer Transaktion durchzuführen sein. Es muss eine aktive Instanz von vorhanden sein, <xref:Microsoft.VisualStudio.Modeling.Transaction> die dem Speicher zugeordnet ist, wenn die Änderung auftritt. Dies gilt für alle Modellelemente, Beziehungen, Formen, Diagramme und deren Eigenschaften.

 Mit dem Transaktions Mechanismus können inkonsistente Zustände vermieden werden. Wenn während einer Transaktion ein Fehler auftritt, wird für alle Änderungen ein Rollback ausgeführt. Wenn der Benutzer einen Rückgängig-Befehl ausführt, wird jede aktuelle Transaktion als einzelner Schritt behandelt. Der Benutzer kann Teile einer aktuellen Änderung nicht rückgängig machen, es sei denn, Sie haben Sie explizit in separaten Transaktionen abgelegt.

## <a name="opening-a-transaction"></a>Öffnen einer Transaktion
 Die einfachste Methode zur Verwaltung einer Transaktion ist eine-Anweisung, die `using` in einer-Anweisung eingeschlossen ist `try...catch` :

```csharp
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 Wenn eine Ausnahme, die das abschließende verhindert `Commit()` , während der Änderungen auftritt, wird der Speicher auf seinen vorherigen Zustand zurückgesetzt. Auf diese Weise können Sie sicherstellen, dass das Modell nicht in einem inkonsistenten Zustand belassen wird.

 Sie können eine beliebige Anzahl von Änderungen innerhalb einer Transaktion vornehmen. Sie können neue Transaktionen innerhalb einer aktiven Transaktion öffnen. Vor dem Ende der enthaltenden Transaktion muss für die Vorgängen ein Commit oder ein Rollback ausgeführt werden. Weitere Informationen finden Sie im Beispiel für die- <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> Eigenschaft.

 Um die Änderungen dauerhaft zu machen, sollten Sie `Commit` die Transaktion ausführen, bevor Sie verworfen wird. Wenn eine Ausnahme auftritt, die nicht innerhalb der Transaktion abgefangen wird, wird der Speicher auf seinen Zustand vor den Änderungen zurückgesetzt.

## <a name="rolling-back-a-transaction"></a>Ausführen eines Rollbacks für eine Transaktion
 Um sicherzustellen, dass der Speicher in seinem Zustand vor der Transaktion verbleibt oder wieder hergestellt wird, können Sie eine der folgenden Taktiken verwenden:

1. Gibt eine Ausnahme aus, die nicht innerhalb des Bereichs der Transaktion abgefangen wird.

2. Explizites Rollback der Transaktion:

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>Transaktionen wirken sich nicht auf nicht-Speicher Objekte aus.
 Transaktionen steuern nur den Status des Stores. Sie können keine partiellen Änderungen rückgängig machen, die an externen Elementen wie z. b. Dateien, Datenbanken oder Objekten vorgenommen wurden, die Sie mit gewöhnlichen Typen außerhalb der DSL-Definition deklariert haben.

 Wenn eine Ausnahme eine solche Änderung mit dem Speicher inkonsistent lassen kann, sollten Sie diese Möglichkeit im Ausnahmehandler behandeln. Eine Möglichkeit, um sicherzustellen, dass externe Ressourcen mit den Speicher Objekten synchronisiert bleiben, besteht darin, jedes externe Objekt mithilfe von Ereignis Handlern mit einem Element im Speicher zu verknüpfen. Weitere Informationen finden Sie unter [Ereignishandler verbreiten Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).

## <a name="rules-fire-at-the-end-of-a-transaction"></a>Regeln werden am Ende einer Transaktion ausgelöst
 Am Ende einer Transaktion werden die an Elemente im Speicher angefügten Regeln ausgelöst, bevor die Transaktion verworfen wird. Jede Regel ist eine Methode, die auf ein Modellelement angewendet wird, das sich geändert hat. Beispielsweise gibt es "Korrektur Regeln", die den Zustand einer Form aktualisieren, wenn sich das Modellelement geändert hat, und das eine Form erstellt, wenn ein Modellelement erstellt wird. Es gibt keine auslösenden Reihenfolge. Eine von einer Regel vorgenommene Änderung kann eine andere Regel auslösen.

 Sie können eigene Regeln definieren. Weitere Informationen zu Regeln finden Sie unter [reagieren auf und](../modeling/responding-to-and-propagating-changes.md)weitergeben von Änderungen.

 Regeln werden nicht nach einem rückgängig-, Wiederholungs-oder Rollback-Befehl ausgelöst.

## <a name="transaction-context"></a>Transaktionskontext
 Jede Transaktion verfügt über ein Wörterbuch, in dem Sie alle gewünschten Informationen speichern können:

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 Dies ist besonders nützlich für die Übertragung von Informationen zwischen Regeln.

## <a name="transaction-state"></a>Transaktionsstatus
 In einigen Fällen müssen Sie eine Änderung vermeiden, wenn die Änderung durch das zurücknehmen oder Wiederholen einer Transaktion verursacht wird. Dies kann z. b. der Fall sein, wenn Sie einen Eigenschafts Wert Handler schreiben, der einen anderen Wert im Speicher aktualisieren kann. Da der Rückgängig-Vorgang alle Werte im Speicher auf die vorherigen Zustände zurücksetzt, ist es nicht erforderlich, aktualisierte Werte zu berechnen. Verwenden Sie diesen Code:

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 Regeln können ausgelöst werden, wenn der Speicher anfänglich aus einer Datei geladen wird. Verwenden Sie Folgendes, um eine Reaktion auf diese Änderungen zu vermeiden:

```csharp
if (!this.Store.InSerializationTransaction) {...}
```
