---
title: Validierung in einer domänenspezifischen Sprache
description: Erfahren Sie, wie Sie Validierungs Einschränkungen definieren können, um zu überprüfen, ob das vom Benutzer erstellte Modell sinnvoll ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, constraints
- Domain-Specific Language, validation
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 44ee0d9e10a4f96979362d8613dc6ca949ff2fd7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924256"
---
# <a name="validation-in-a-domain-specific-language"></a>Validierung in einer domänenspezifischen Sprache
Als Autor einer domänenspezifischen Sprache (Domain-Specific Language, DSL) können Sie Validierungseinschränkungen definieren, um zu überprüfen, ob das vom Benutzer erstellte Modell sinnvoll ist. Wenn Benutzer in Ihrer DSL beispielsweise einen Stammbaum von Personen und deren Vorfahren zeichnen können, könnten Sie eine Einschränkung schreiben, mit der sichergestellt wird, dass die Geburtstage der Kinder nach denen der Eltern liegen.

 Die Validierungs Einschränkungen können beim Speichern des Modells, beim Öffnen und beim expliziten ausführen **des Menübefehls** überprüfen ausgeführt werden. Sie können die Validierung auch vom Programm gesteuert ausführen. Sie könnten die Validierung beispielsweise als Reaktion auf die Änderung eines Eigenschaftswerts oder einer Beziehung ausführen.

 Die Überprüfung ist besonders wichtig, wenn Sie Textvorlagen oder andere Tools schreiben, mit denen die Modelle ihrer Benutzer verarbeitet werden. Durch die Validierung wird sichergestellt, dass die Modelle die von den Tools angenommenen Vorbedingungen erfüllen.

> [!WARNING]
> Sie können auch zulassen, dass Validierungseinschränkungen in separaten Erweiterungen Ihrer DSL zusammen mit Menübefehlen und Gestenhandlern der Erweiterungen definiert werden. Die Benutzer könnten dann diese Erweiterungen zusätzlich zu Ihrer DSL installieren. Weitere Informationen finden Sie unter [Erweitern Ihrer DSL mithilfe von MEF](../modeling/extend-your-dsl-by-using-mef.md).

## <a name="running-validation"></a>Ausführen der Validierung
 Wenn ein Benutzer ein Modell bearbeitet, also eine Instanz Ihrer domänenspezifischen Sprache, kann die Validierung mit den folgenden Aktionen ausgeführt werden:

- Klicken Sie mit der rechten Maustaste auf das Diagramm und wählen Sie **alle** überprüfen

- Klicken Sie mit der rechten Maustaste auf den obersten Knoten im Explorer ihrer DSL, und wählen Sie **alle** überprüfen aus.

- Speichern Sie das Modell.

- Öffnen Sie das Modell.

- Darüber hinaus können Sie Programmcode schreiben, mit dem die Validierung ausgeführt wird, beispielsweise als Teil eines Menübefehls oder als Reaktion auf eine Änderung.

  Alle Validierungs Fehler werden im Fenster **Fehlerliste** angezeigt. Der Benutzer kann auf eine Fehlermeldung doppelklicken, um die Modellelemente auszuwählen, die den Fehler verursachen.

## <a name="defining-validation-constraints"></a>Definieren von Validierungseinschränkungen
 Sie definieren Validierungseinschränkungen, indem Sie den Domänenklassen und Beziehungen Ihrer DSL Validierungsmethoden hinzufügen. Wenn eine Validierung vom Benutzer oder durch das Programm ausgeführt wird, werden einige oder alle Validierungsmethoden ausgeführt. Jede Methode wird auf jede Instanz ihrer Klasse angewendet, und in jeder Klasse sind mehrere Validierungsmethoden möglich.

 Die von Validierungsmethoden gefundenen Fehler werden ausgegeben.

> [!NOTE]
> Validierungsmethoden geben Fehler aus, nehmen aber keine Änderungen am Modell vor. Wenn Sie bestimmte Änderungen anpassen oder verhindern möchten, finden Sie weitere Informationen unter [Alternativen zur Validierung](#alternatives).

#### <a name="to-define-a-validation-constraint"></a>So definieren Sie eine Validierungseinschränkung

1. Aktivieren Sie die Validierung im Knoten **Editor \ Validierung** :

   1. Öffnen Sie **Dsl\DslDefinition.DSL**.

   2. Erweitern Sie im DSL-Explorer den Knoten **Editor** , und wählen Sie über **Prüfung** aus.

   3. Legen Sie im Eigenschaftenfenster die Eigenschaften **verwendet**  auf fest `true` . Am zweckmäßigsten ist es, alle dieser Eigenschaften festzulegen.

   4. Klicken Sie in der Symbolleiste **Projektmappen-Explorer** auf **alle Vorlagen transformieren** .

2. Schreiben Sie partielle Klassendefinitionen für mindestens eine Ihrer Domänenklassen oder -beziehungen. Schreiben Sie diese Definitionen in eine neue Codedatei im **DSL** -Projekt.

3. Stellen Sie jeder Klasse das folgende Attribut voran:

   ```csharp
   [ValidationState(ValidationState.Enabled)]
   ```

   - Standardmäßig aktiviert dieses Attribut auch die Validierung für abgeleitete Klassen. Wenn Sie die Validierung für eine bestimmte abgeleitete Klasse deaktivieren möchten, können Sie `ValidationState.Disabled` verwenden.

4. Fügen Sie den Klassen Validierungsmethoden hinzu. Jede Validierungsmethode kann einen beliebigen Namen aufweisen, muss aber einen Parameter mit dem Typ <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationContext> enthalten.

    Ihm muss mindestens ein `ValidationMethod`-Attribut vorangestellt werden:

   ```csharp
   [ValidationMethod (ValidationCategories.Open | ValidationCategories.Save | ValidationCategories.Menu ) ]
   ```

    Mit "ValidationCategories" wird angegeben, wann die Methode ausgeführt wird.

   Beispiel:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;

// Allow validation methods in this class:
[ValidationState(ValidationState.Enabled)]
// In this DSL, ParentsHaveChildren is a domain relationship
// from Person to Person:
public partial class ParentsHaveChildren
{
  // Identify the method as a validation method:
  [ValidationMethod
  ( // Specify which events cause the method to be invoked:
    ValidationCategories.Open // On file load.
  | ValidationCategories.Save // On save to file.
  | ValidationCategories.Menu // On user menu command.
  )]
  // This method is applied to each instance of the
  // type (and its subtypes) in a model:
  private void ValidateParentBirth(ValidationContext context)
  {
    // In this DSL, the role names of this relationship
    // are "Child" and "Parent":
     if (this.Child.BirthYear < this.Parent.BirthYear
        // Allow user to leave the year unset:
        && this.Child.BirthYear != 0)
      {
        context.LogError(
             // Description:
                       "Child must be born after Parent",
             // Unique code for this error:
                       "FAB001ParentBirthError",
              // Objects to select when user double-clicks error:
                       this.Child,
                       this.Parent);
    }
  }
```

 Beachten Sie die folgenden Punkte zu diesem Code:

- Sie können Validierungsmethoden Domänenklassen oder -beziehungen hinzufügen. Der Code für diese Typen befindet sich in " **dsl\generated code\domain \* . cs**".

- Jede Validierungsmethode wird auf jede Instanz ihrer Klasse und deren Unterklassen angewendet. Bei einer Domänenbeziehung ist jede Instanz ein Link zwischen zwei Modellelementen.

- Validierungsmethoden werden nicht in einer angegebenen Reihenfolge angewendet, und die einzelnen Methoden werden nicht in einer vorhersagbaren Reihenfolge auf die Instanzen ihrer Klassen angewendet.

- Es ist normalerweise nicht empfehlenswert, dass eine Validierungsmethode den Speicherinhalt aktualisiert, da dies zu inkonsistenten Ergebnissen führen würde. Stattdessen sollten die Methode Fehler ausgeben, indem `context.LogError`, `LogWarning` oder `LogInfo` aufgerufen wird.

- Im LogError-Aufruf können Sie eine Liste der Modellelemente oder Beziehungslinks bereitstellen, die ausgewählt werden, wenn der Benutzer auf die Fehlermeldung doppelklickt.

- Informationen zum Lesen des Modells im Programmcode finden Sie unter [navigieren und Aktualisieren eines Modells im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Das Beispiel gilt für das folgende Domänenmodell. Die ParentsHaveChildren-Beziehung weist die Rollen "Child" und "Parent" auf.

  ![DSL-Definitions Diagramm &#45; Familienstruktur Modell](../modeling/media/familyt_person.png)

## <a name="validation-categories"></a>Validierungskategorien
 Im Attribut <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> geben Sie an, wann die Validierungsmethode ausgeführt werden soll.

|Category|Ausführung|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Wenn der Benutzer den Menübefehl "Überprüfen" aufruft.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Wenn die Modelldatei geöffnet wird.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Wenn die Datei gespeichert wird. Bei Validierungsfehlern erhält der Benutzer die Option, den Speichervorgang abzubrechen.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Wenn die Datei gespeichert wird. Bei Fehlern von Methoden in dieser Kategorie wird der Benutzer gewarnt, dass die Datei möglicherweise nicht wieder geöffnet werden kann.<br /><br /> Verwenden Sie diese Kategorie für Validierungsmethoden, die auf doppelte Namen oder IDs bzw. auf andere Bedingungen, die zu Ladefehlern führen können, prüfen.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Wenn die ValidateCustom-Methode aufgerufen wird. Validierungen in dieser Kategorie können nur vom Programmcode aufgerufen werden.<br /><br /> Weitere Informationen finden Sie unter [benutzerdefinierte Validierungs Kategorien](#custom).|

## <a name="where-to-place-validation-methods"></a>Platzierung von Validierungsmethoden
 Häufig erreichen Sie den gleichen Effekt, indem Sie eine Validierungsmethode für einen anderen Typ festlegen. Sie könnten beispielsweise eine Methode der Person-Klasse statt der ParentsHaveChildren-Beziehung hinzufügen und eine Iteration durch die Links einrichten:

```
[ValidationState(ValidationState.Enabled)]
public partial class Person
{[ValidationMethod
 ( ValidationCategories.Open
 | ValidationCategories.Save
 | ValidationCategories.Menu
 )
]
  private void ValidateParentBirth(ValidationContext context)
  {
    // Iterate through ParentHasChildren links:
    foreach (Person parent in this.Parents)
    {
        if (this.BirthYear <= parent.BirthYear)
        { ...
```

 **Aggregieren von Validierungseinschränkungen.**  Definieren Sie zur Anwendung der Validierung in einer vorhersagbaren Reihenfolge eine Validierungsmethode für eine Besitzerklasse wie dem Stammelement Ihres Modells. Mit dieser Technik können Sie mehrere Fehlerberichte in einer Meldung aggregieren.

 Zu den Nachteilen gehört, dass die Verwaltung der kombinierten Methode schwieriger ist und dass alle Einschränkungen die gleichen `ValidationCategories` aufweisen müssen. Daher empfiehlt es sich, jede Einschränkung möglichst in einer gesonderten Methode zu belassen.

 **Übergeben von Werten in den Kontextcache.**  Der Kontextparameter weist ein Wörterbuch auf, in das Sie beliebige Werte aufnehmen können. Das Wörterbuch bleibt für die Dauer der Validierung erhalten. Eine bestimmte Validierungsmethode könnte beispielsweise eine Fehleranzahl im Kontext speichern und dazu verwenden, eine Überflutung des Fehlerfensters mit wiederholten Meldungen zu vermeiden. Beispiel:

```csharp
List<ParentsHaveChildren> erroneousLinks;
if (!context.TryGetCacheValue("erroneousLinks", out erroneousLinks))
erroneousLinks = new List<ParentsHaveChildren>();
erroneousLinks.Add(this);
context.SetCacheValue("erroneousLinks", erroneousLinks);
if (erroneousLinks.Count < 5) { context.LogError( ... ); }
```

## <a name="validation-of-multiplicities"></a>Validierung von Multiplizitäten
 Validierungsmethoden zur Überprüfung der minimalen Multiplizität werden für Ihre DSL automatisch generiert. Der Code wird in **dsl\generated code\multipitvalidation.cs** geschrieben. Diese Methoden treten in Kraft, wenn Sie die Validierung im Knoten **editor\validation** im DSL-Explorer aktivieren.

 Wenn Sie als Multiplizität einer Rolle in einer Domänenbeziehung 1..* oder 1..1 festlegen, der Benutzer aber keinen Link mit dieser Beziehung erstellt, wird eine Validierungsfehlermeldung angezeigt.

 Wenn Ihre DSL beispielsweise die Klassen Person und Town und eine Beziehung personlivesintown mit der Beziehung 1 hat **. \\** * in der Rolle "Ort" wird für jede Person, die keine Stadt hat, eine Fehlermeldung angezeigt.

## <a name="running-validation-from-program-code"></a>Ausführen der Validierung über den Programmcode
 Sie können die Validierung ausführen, indem Sie auf einen ValidationController zugreifen oder ihn erstellen. Wenn die Fehler im Fehler Fenster für den Benutzer angezeigt werden sollen, verwenden Sie den validationcontroller, der an die docdata Ihres Diagramms angehängt ist. Wenn Sie beispielsweise einen Menübefehl schreiben, ist `CurrentDocData.ValidationController` in der Befehlssatzklasse verfügbar:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Modeling.Shell;
...
partial class MyLanguageCommandSet
{
  private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
  {
   ValidationController controller = this.CurrentDocData.ValidationController;
...
```

 Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Befehls zum Kontextmenü](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

 Sie können auch einen gesonderten Validierungscontroller erstellen und Fehler selbst verwalten. Beispiel:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Modeling.Shell;
...
Store store = ...;
VsValidationController validator = new VsValidationController(s);
// Validate all elements in the Store:
if (!validator.Validate(store, ValidationCategories.Save))
{
  // Deal with errors:
  foreach (ValidationMessage message in validator.ValidationMessages) { ... }
}
```

## <a name="running-validation-when-a-change-occurs"></a>Ausführen der Validierung bei einer Änderung
 Wenn Sie sicherstellen möchten, dass der Benutzer sofort gewarnt wird, sobald das Modell ungültig wird, können Sie ein Speicherereignis definieren, das die Validierung ausführt. Weitere Informationen zu Speicher Ereignissen finden Sie unter [Ereignishandler verbreiten Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Fügen Sie dem **dslpackage** -Projekt neben dem Validierungscode eine benutzerdefinierte Codedatei mit Inhalt ähnlich dem folgenden Beispiel hinzu. In diesem Code wird der an das Dokument angefügte `ValidationController` verwendet. Dieser Controller zeigt die Validierungs Fehler in der Visual Studio-Fehlerliste an.

```csharp
using System;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
namespace Company.FamilyTree
{
  partial class FamilyTreeDocData // Change name to your DocData.
  {
    // Register the store event handler:
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded();
      DomainClassInfo observedLinkInfo = this.Store.DomainDataDirectory
         .FindDomainClass(typeof(ParentsHaveChildren));
      DomainClassInfo observedClassInfo = this.Store.DomainDataDirectory
         .FindDomainClass(typeof(Person));
      EventManagerDirectory events = this.Store.EventManagerDirectory;
      events.ElementAdded
         .Add(observedLinkInfo, new EventHandler<ElementAddedEventArgs>(ParentLinkAddedHandler));
      events.ElementDeleted.Add(observedLinkInfo, new EventHandler<ElementDeletedEventArgs>(ParentLinkDeletedHandler));
      events.ElementPropertyChanged.Add(observedClassInfo, new EventHandler<ElementPropertyChangedEventArgs>(BirthDateChangedHandler));
    }
    // Handler will be called after transaction that creates a link:
    private void ParentLinkAddedHandler(object sender,
                                ElementAddedEventArgs e)
    {
      this.ValidationController.Validate(e.ModelElement,
           ValidationCategories.Save);
    }
    // Called when a link is deleted:
    private void ParentLinkDeletedHandler(object sender,
                                ElementDeletedEventArgs e)
    {
      // Don't apply validation to a deleted item!
      // - Validate store to refresh the error list.
      this.ValidationController.Validate(this.Store,
           ValidationCategories.Save);
    }
    // Called when any property of a Person element changes:
    private void BirthDateChangedHandler(object sender,
                      ElementPropertyChangedEventArgs e)
    {
      Person person = e.ModelElement as Person;
      // Not interested in changes in other properties:
      if (e.DomainProperty.Id != Person.BirthYearDomainPropertyId)
          return;

      // Validate all parent links to and from the person:
      this.ValidationController.Validate(
        ParentsHaveChildren.GetLinksToParents(person)
        .Concat(ParentsHaveChildren.GetLinksToChildren(person))
        , ValidationCategories.Save);
    }
  }
}
```

 Die Handler werden auch nach Vorgängen zum Rückgängigmachen oder Wiederholen aufgerufen, wenn die Vorgänge Auswirkungen auf die Links oder Elemente haben.

## <a name="custom-validation-categories"></a><a name="custom"></a> Benutzerdefinierte Validierungs Kategorien
 Neben den standardmäßigen Validierungskategorien wie "Menü" und "Öffnen" können Sie eigene Kategorien erstellen. Sie können diese Kategorien über Programmcode aufrufen. Sie können nicht direkt vom Benutzer aufgerufen werden.

 Ein typischer Einsatzbereich benutzerdefinierter Kategorien ist die Definition einer Kategorie, mit der getestet wird, ob das Modell die Vorbedingungen eines bestimmten Tools erfüllt.

 Um einer bestimmten Kategorie eine Validierungsmethode hinzuzufügen, stellen Sie ihr beispielsweise das folgende Attribut voran:

```csharp
[ValidationMethod(CustomCategory = "PreconditionsForGeneratePartsList")]
[ValidationMethod(ValidationCategory.Menu)]
private void TestForCircularLinks(ValidationContext context)
{...}
```

> [!NOTE]
> Sie können einer Methode beliebig viele `[ValidationMethod()]`-Attribute voranstellen. Sie können benutzerdefinierten und standardmäßigen Kategorien eine Methode hinzufügen.

 So rufen Sie eine benutzerdefinierte Validierung auf

```csharp

// Invoke all validation methods in a custom category:
validationController.ValidateCustom
  (store, // or a list of model elements
   "PreconditionsForGeneratePartsList");
```

## <a name="alternatives-to-validation"></a><a name="alternatives"></a> Alternativen zur Validierung
 Validierungseinschränkungen geben Fehler aus, nehmen aber keine Änderungen am Modell vor. Wenn Sie allerdings verhindern möchten, dass das Modell ungültig wird, können Sie andere Techniken einsetzen.

 Diese Techniken werden jedoch nicht empfohlen. Normalerweise ist es besser, den Benutzer entscheiden zu lassen, wie ein ungültiges Modell korrigiert wird.

 **Passen Sie die Änderung an, um die Gültigkeit des Modells wiederherzustellen.**  Beispiel: Wenn der Benutzer eine Eigenschaft oberhalb des zulässigen Maximums festlegt, könnten Sie die Eigenschaft auf den maximalen Wert zurücksetzen. Definieren Sie dazu eine Regel. Weitere Informationen finden Sie unter [Regeln verbreiten Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).

 **Setzen Sie die Transaktion zurück, wenn eine ungültige Änderung vorgenommen wird.** Sie können für diesen Zweck auch eine Regel definieren, aber in einigen Fällen ist es möglich, einen Eigenschaftenhandler **onvaluechanging ()** zu überschreiben oder eine Methode zu überschreiben, z `OnDeleted().` . b. um ein Rollback für eine Transaktion auszuführen `this.Store.TransactionManager.CurrentTransaction.Rollback().` . Weitere Informationen finden Sie unter [Ändern von Domänen Eigenschafts Wert-Handlern](../modeling/domain-property-value-change-handlers.md).

> [!WARNING]
> Stellen Sie sicher, dass der Benutzer weiß, dass die Änderung angepasst oder zurückgesetzt wurde. Verwenden Sie beispielsweise `System.Windows.Forms.MessageBox.Show("message").`.

## <a name="see-also"></a>Weitere Informationen

- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Ereignishandler propagieren Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md)
