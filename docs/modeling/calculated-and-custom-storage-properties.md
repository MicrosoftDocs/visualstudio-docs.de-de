---
title: Berechnete und benutzerdefinierte Speichereigenschaften
description: Erfahren Sie, wie dem Benutzer alle Domänen Eigenschaften in einer domänenspezifischen Sprache (DSL) im Diagramm und im sprach-Explorer angezeigt werden können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c50d205745917b3af7de638a17921f4bcdca509
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363548"
---
# <a name="calculated-and-custom-storage-properties"></a>Berechnete und benutzerdefinierte Speichereigenschaften
Alle Domänen Eigenschaften in einer domänenspezifischen Sprache (DSL) können dem Benutzer im Diagramm und im sprach-Explorer angezeigt werden, und Sie können über Programmcode darauf zugreifen. Eigenschaften unterscheiden sich jedoch in der Art und Weise, in der ihre Werte gespeichert werden.

## <a name="kinds-of-domain-properties"></a>Arten von Domänen Eigenschaften
 In der DSL-Definition können Sie die **Art** einer Domänen Eigenschaft festlegen, wie in der folgenden Tabelle aufgeführt:

|Art der Domänen Eigenschaft|Beschreibung|
|-|-|
|**Standard** (Standard)|Eine Domänen Eigenschaft, die im *Speicher* gespeichert und in eine Datei serialisiert wird.|
|**Berechnet**|Eine schreibgeschützte Domänen Eigenschaft, die nicht im Speicher gespeichert wird, sondern aus anderen Werten berechnet wird.<br /><br /> Beispielsweise `Person.Age` könnte aus berechnet werden `Person.BirthDate` .<br /><br /> Sie müssen den Code bereitstellen, der die Berechnung ausführt. In der Regel berechnen Sie den Wert aus anderen Domänen Eigenschaften. Sie können jedoch auch externe Ressourcen verwenden.|
|**Benutzerdefinierter Speicher**|Eine Domänen Eigenschaft, die nicht direkt im Speicher gespeichert wird, sondern sowohl Get als auch festgelegt werden kann.<br /><br /> Sie müssen die Methoden bereitstellen, mit denen der Wert erhalten und festgelegt wird.<br /><br /> Beispielsweise `Person.FullAddress` kann in `Person.StreetAddress` , und gespeichert werden `Person.City` `Person.PostalCode` .<br /><br /> Sie können auch auf externe Ressourcen zugreifen, z. b. um Werte aus einer Datenbank zu erhalten und festzulegen.<br /><br /> Der Code sollte keine Werte im Speicher festlegen, wenn den Wert "true" hat `Store.InUndoRedoOrRollback` . Weitere Informationen finden Sie unter [Transaktionen und benutzerdefinierte Setter](#setters).|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Bereitstellen des Codes für eine berechnete oder benutzerdefinierte Speicher Eigenschaft
 Wenn Sie den Typ einer Domänen Eigenschaft auf einen berechneten oder einen benutzerdefinierten Speicher festgelegt haben, müssen Sie Zugriffsmethoden bereitstellen. Wenn Sie die Projekt Mappe erstellen, werden Sie in einem Fehlerbericht darüber informiert, was erforderlich ist.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>So definieren Sie eine berechnete oder benutzerdefinierte Speicher Eigenschaft

1. Wählen Sie in der Datei "DslDefinition. DSL" die Domänen Eigenschaft entweder im Diagramm oder im **DSL-Explorer** aus.

2. Legen Sie im Fenster **Eigenschaften** für das Feld **Kind** den Wert **berechneter** oder **benutzerdefinierter Speicher** fest.

     Stellen Sie sicher, dass Sie auch den **Typ** auf den gewünschten Wert festgelegt haben.

3. Klicken Sie in der Symbolleiste von **Projektmappen-Explorer** auf **alle Vorlagen transformieren** .

4. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

     Sie erhalten die folgende Fehlermeldung: "*YourClass* enthält keine Definition für get *yourproperty*".

5. Doppelklicken Sie auf die Fehlermeldung.

     "Dsl\generatedcode\domainclasses.cs" oder "DomainRelationships.cs" wird geöffnet. Oberhalb des hervorgehobenen Methoden Aufrufes werden Sie in einem Kommentar aufgefordert, eine Implementierung für get *yourproperty*() bereitzustellen.

    > [!NOTE]
    > Diese Datei wird aus "DslDefinition. DSL" generiert. Wenn Sie diese Datei bearbeiten, gehen Ihre Änderungen beim nächsten Klicken auf **alle Vorlagen transformieren** verloren. Fügen Sie stattdessen die erforderliche Methode in einer separaten Datei hinzu.

6. Erstellen oder öffnen Sie eine Klassendatei in einem separaten Ordner, z. b. customcode \\ *yourdomainclass*. cs.

     Stellen Sie sicher, dass der Namespace mit dem des generierten Codes identisch ist.

7. Schreiben Sie in der Klassendatei eine partielle Implementierung der Domänen Klasse. Schreiben Sie in der-Klasse eine Definition für die fehlende `Get` Methode, die dem folgenden Beispiel ähnelt:

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. Wenn Sie **Art** auf **benutzerdefinierten Speicher** festlegen, müssen Sie auch eine-Methode bereitstellen `Set` . Zum Beispiel:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     Der Code sollte keine Werte im Speicher festlegen, wenn den Wert "true" hat `Store.InUndoRedoOrRollback` . Weitere Informationen finden Sie unter [Transaktionen und benutzerdefinierte Setter](#setters).

9. Erstellen Sie das Projekt, und führen Sie es aus.

10. Testen Sie die-Eigenschaft. Stellen Sie sicher, dass Sie **Rückgängig** und wieder **holen** versuchen.

## <a name="transactions-and-custom-setters"></a><a name="setters"></a> Transaktionen und benutzerdefinierte Setter
 In der Set-Methode der Custom Storage-Eigenschaft muss keine Transaktion geöffnet werden, da die-Methode in der Regel innerhalb einer aktiven Transaktion aufgerufen wird.

 Die Set-Methode kann jedoch auch aufgerufen werden, wenn der Benutzer Rückgängigmachen oder wiederholen aufruft oder wenn für eine Transaktion ein Rollback ausgeführt wird. Wenn <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> den Wert true hat, sollte sich die Set-Methode wie folgt Verhalten:

- Es sollten keine Änderungen im Speicher vorgenommen werden, wie z. b. das Zuweisen von Werten zu anderen Domänen Eigenschaften. Der rückgängig-Manager legt seine Werte fest.

- Allerdings sollten alle externen Ressourcen, z. b. Datenbank-oder Dateiinhalte, oder Objekte außerhalb des Stores aktualisiert werden. Dadurch wird sichergestellt, dass Sie synchron mit den Werten im Speicher aufbewahrt werden.

  Zum Beispiel:

```
void SetAgeValue(int value)
{
  // If we are in Undo, no changes to Store objects:
  if (!this.Store.InUndoRedoOrRollback)
  {
    this.BirthYear = System.DateTime.Today.Year - value;
  }
  // But always update external objects:
  System.IO.File.WriteAllText(AgeFile, value);
}
```

 Weitere Informationen zu Transaktionen finden Sie unter [navigieren und Aktualisieren eines Modells im Programm Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Siehe auch

- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Eigenschaften von Domäneneigenschaften](../modeling/properties-of-domain-properties.md)
- [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)
