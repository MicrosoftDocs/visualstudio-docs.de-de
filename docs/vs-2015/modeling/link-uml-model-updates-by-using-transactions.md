---
title: Verknüpfen von UML-Modell Aktualisierungen mithilfe von Transaktionen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, transactions
ms.assetid: a1df6c38-a3d1-4a3f-82bc-c8f363ab916e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8930bba76830a6116c3182f3fb2936cd4f1a3e47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657607"
---
# <a name="link-uml-model-updates-by-using-transactions"></a>Verknüpfen von UML-Modellaktualisierungen mithilfe von Transaktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie für die UML-Designer in Visual Studio eine Erweiterung definieren, können Sie mehrere Änderungen in einer einzelnen Transaktion gruppieren, die als *verknüpfter rückgängigkontext*bezeichnet wird. Welche Versionen von Visual Studio UML-Modelle unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Standardmäßig kann jede Änderung, die der Code an einem Modell vornimmt, vom Benutzer einzeln rückgängig gemacht werden. Wenn Sie z. B. einen Menübefehl definieren, der die Namen von zwei UML-Klassen vertauscht, kann ein Benutzer den Befehl aufrufen und dann einen einzelnen Rückgängig-Vorgang ausführen. Dabei wird die Änderung eines Namens rückgängig gemacht, nicht jedoch die Änderung des anderen Namens, sodass sich das Modell dann in einem unbeabsichtigten Zustand befindet.

 Um dies zu verhindern, kann der Code innerhalb einer Transaktion eine Reihe von Änderungen ausführen. Für die Benutzer sehen diese Änderungen dann wie eine einzelne Änderung aus. Wenn dann ein Rückgängig-Befehl ausgeführt wird, werden alle Änderungen rückgängig gemacht.

 Ein zusätzlicher Vorteil besteht darin, dass der Code einen teilweise vollständigen Satz von Änderungen rückgängig machen kann, indem er eine Ausnahme auslöst oder die Transaktion abbricht.

## <a name="to-group-changes-into-a-single-transaction"></a>So gruppieren Sie Änderungen in einer einzelnen Transaktion
 Stellen Sie sicher, dass die Projektverweise diese .NET-Assembly enthalten:

 **Microsoft. VisualStudio. Modeling. SDK. [Version]. dll**

 Deklarieren Sie in der Klasse eine importierte Eigenschaft vom Typ <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoContext>:

 `using Microsoft.VisualStudio.Modeling.ExtensionEnablement;`

 `...`

 `class … {`

 `[Import]`

 `public ILinkedUndoContext LinkedUndoContext { get; set; }`

 Schließen Sie die Änderungen in einer Methode, die das Modell ändert, in eine Transaktion ein:

 `using (ILinkedUndoTransaction transaction =`

 `LinkedUndoContext.BeginTransaction("my updates"))`

 `{`

 `// code to update model elements or shapes goes here`

 `transaction.Commit();`

 `}`

 Beachten Sie Folgendes:

- Sie müssen am Ende der Transaktion immer `Commit()` einschließen. Wenn eine Transaktion verworfen wird, ohne übermittelt worden zu sein, wird die Transaktion zurückgesetzt. Das heißt, dass für das Modell der Zustand zu Beginn der Transaktion wiederhergestellt wird.

- Wenn eine Ausnahme auftritt, die innerhalb der Transaktion nicht aufgefangen werden kann, wird die Transaktion zurückgesetzt. Es ist ein häufig verwendetes Muster, den `using`-Block der Transaktion in einen `try…catch`-Block einzuschließen.

- Sie können Transaktionen verschachteln.

- Sie können jeden nicht leeren Namen für `BeginTransaction()` bereitstellen.

- Nur der UML-Modellspeicher ist von diesen Transaktionen betroffen. Modellerstellungstransaktionen wirken sich nicht auf folgende Elemente aus: Variablen, externe Speicher wie Dateien und Datenbanken, Ebenendiagramme und Codemodelle.

## <a name="example"></a>Beispiel

```
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Uml.Interfaces;
    using Microsoft.VisualStudio.Uml.Classes;
    using Microsoft.VisualStudio.Uml.Extensions;
    using System.Linq;
    using System.ComponentModel.Composition;
 ...
  [Import]
  public ILinkedUndoContext LinkedUndoContext { get; set; }

  /// <summary>
  /// Swap the names of the currently selected elements.
  /// </summary>
  public void Execute(IMenuCommand command)
  {
    var selectedShapes =
      Context.CurrentDiagram.GetSelectedShapes<IClassifier>();
    if (selectedShapes.Count() < 2) return;
    IClassifier firstElement = selectedShapes.First().Element;
    IClassifier lastElement = selectedShapes.Last().Element;
    string firstName = firstElement.Name;
    // Perform changes inside a transaction so that undo
    // works as a single change.
    using (ILinkedUndoTransaction transaction =
      LinkedUndoContext.BeginTransaction("Swap names"))
    {
        firstElement.Name = lastElement.Name;
        lastElement.Name = firstName;
        transaction.Commit();
    }
 }
```

## <a name="see-also"></a>Weitere Informationen
 [Programmieren mit der UML-API](../modeling/programming-with-the-uml-api.md) [Definieren eines Menübefehls in einem Modellierungs Diagramm Erweitern von](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md)
