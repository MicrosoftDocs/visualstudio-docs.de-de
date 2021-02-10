---
title: Handler für Wertänderungen von Domäneneigenschaften
description: Weitere Informationen zu Domänen Eigenschafts Wert-Änderungs Handlern, die in einer domänenspezifischen Visual Studio-Sprache verwendet werden können.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a5a372d2e558b44753e9d0bc66d7c4c24b825533
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935091"
---
# <a name="domain-property-value-change-handlers"></a>Domänen Eigenschafts Wert-Änderungs Handler

Wenn in einer Visual Studio-domänenspezifischen Sprache der Wert einer Domänen Eigenschaft geändert wird, `OnValueChanging()` werden die-Methode und die- `OnValueChanged()` Methode im Domänen Eigenschaften Handler aufgerufen. Als Reaktion auf diese Änderung können Sie diese Methoden überschreiben.

## <a name="override-the-property-handler-methods"></a>Überschreiben der Eigenschaften Handlermethoden

Jede Domäneneigenschaft Ihrer domänenspezifischen Sprache wird von einer Klasse verarbeitet, die in der übergeordneten Domänenklasse geschachtelt ist. Der Name folgt dem Format *propertyName* propertyhandler. Sie können diese eigenschaftenhandlerklasse in der Datei **dsl\generated code\domainclasses.cs** überprüfen. In der Klasse wird `OnValueChanging()` unmittelbar vor der Wertänderung aufgerufen, und `OnValueChanged()` wird unmittelbar nach der Wertänderung aufgerufen.

Angenommen, Sie verfügen über eine Domänen Klasse mit dem Namen `Comment` , die eine Zeichen folgen-Domänen Eigenschaft mit dem Namen `Text` und eine ganzzahlige Eigenschaft namens aufweist `TextLengthCount` Damit `TextLengthCount` immer die Länge der `Text` Zeichenfolge enthält, können Sie den folgenden Code in eine separate Datei im DSL-Projekt schreiben:

```csharp
// Domain Class "Comment":
public partial class Comment
{
  // Domain Property "Text":
  partial class TextPropertyHandler
  {
    protected override void OnValueChanging(CommentBase element, string oldValue, string newValue)
    {
      base.OnValueChanging(element, oldValue, newValue);

      // To update values outside the Store, write code here.

      // Let the transaction manager handle undo:
      Store store = element.Store;
      if (store.InUndoRedoOrRollback || store.InSerializationTransaction) return;

      // Update values in the Store:
      this.TextLengthCount = newValue.Length;
    }
  }
}
```

Beachten Sie die folgenden Punkte zu Eigenschaftenhandlern:

- Die Eigenschaftenhandlermethoden werden aufgerufen, wenn der Benutzer Änderungen an einer Domäneneigenschaft vornimmt und wenn der Programmcode der Eigenschaft einen anderen Wert zuweist.

- Die Methoden werden nur aufgerufen, wenn der Wert tatsächlich geändert wird. Der Handler wird nicht aufgerufen, wenn der Programmcode einen Wert zuweist, der dem aktuellen Wert entspricht.

- Berechnete und benutzerdefinierte Speicherdomäneneigenschaften enthalten die Methoden "OnValueChanged" und "OnValueChanging" nicht.

- Sie können einen Änderungshandler nicht verwenden, um den neuen Wert zu ändern. Wenn Sie dies tun möchten, um beispielsweise den Wert auf einen bestimmten Bereich zu beschränken, definieren Sie `ChangeRule`.

- Sie können einen Änderungshandler keiner Eigenschaft hinzufügen, die für eine Rolle einer Beziehung steht. Definieren Sie stattdessen `AddRule` und `DeleteRule` für die Beziehungsklasse. Diese Regeln werden ausgelöst, wenn die Links erstellt oder geändert werden. Weitere Informationen finden Sie unter [Regeln verbreiten Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="changes-in-and-out-of-the-store"></a>Änderungen innerhalb und außerhalb des Speichers

Eigenschaftenhandlermethoden werden innerhalb der Transaktion aufgerufen, die die Änderung initiiert hat. Daher können Sie weitere Änderungen im Speicher vornehmen, ohne eine neue Transaktion zu öffnen. Ihre Änderungen können zu weiteren Handleraufrufen führen.

Wenn eine Transaktion rückgängig gemacht, wiederholt oder zurückgesetzt wird, sollten Sie keine Änderungen im Speicher vornehmen, d. h. Änderungen an Modellelementen, Beziehungen, Formen, Konnektoren Diagrammen oder deren Eigenschaften.

Des Weiteren würden Sie normalerweise Werte nicht aktualisieren, wenn das Modell aus der Datei geladen wird.

Änderungen am Modell könnten also mit einem Test wie dem folgenden geschützt werden:

```csharp
if (!store.InUndoRedoOrRollback && !store. InSerializationTransaction)
{
   this.TextLength = ...; // in-store changes
}
```

Wenn der Eigenschafts Handler dagegen Änderungen außerhalb des Geschäfts, z. b. an eine Datei, eine Datenbank oder nicht-Speicher Variablen weitergibt, sollten Sie diese Änderungen immer vornehmen, damit die externen Werte aktualisiert werden, wenn der Benutzer rückgängig oder wiederholen aufruft.

### <a name="cancel-a-change"></a>Abbrechen einer Änderung

Wenn Sie eine Änderung verhindern möchten, können Sie die aktuelle Transaktion zurücksetzen. Sie könnten beispielsweise sicherstellen, dass eine Eigenschaft in einem bestimmten Bereich bleibt.

```csharp
if (newValue > 10)
{
   store.TransactionManager.CurrentTransaction.Rollback();
   System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}
```

### <a name="alternative-technique-calculated-properties"></a>Alternative Technik: Berechnete Eigenschaften

Das vorherige Beispiel veranschaulicht, wie mit "OnValueChanged()" Werte von einer Domäneneigenschaft an eine andere übertragen werden können. Jede Eigenschaft verfügt über einen eigenen gespeicherten Wert.

Sie könnten stattdessen die abgeleitete Eigenschaft als berechnete Eigenschaft definieren. In diesem Fall hat die Eigenschaft keinen eigenen Speicher und die definierende Funktion wird ausgewertet, wenn der Wert erforderlich ist. Weitere Informationen finden Sie unter [berechnete und benutzerdefinierte Speicher Eigenschaften](../modeling/calculated-and-custom-storage-properties.md).

Anstelle des vorherigen Beispiels können Sie das Feld **Kind** von so festlegen, `TextLengthCount` dass es in der DSL-Definition **berechnet** wird. Sie würden ihre eigene **Get** -Methode für diese Domänen Eigenschaft bereitstellen. Die **Get** -Methode gibt die aktuelle Länge der `Text` Zeichenfolge zurück.

Ein möglicher Nachteil berechneter Eigenschaften ist jedoch, dass der Ausdruck bei jeder Verwendung des Werts ausgewertet wird. Dies kann ein Leistungsproblem darstellen. Auch gibt es "OnValueChanging()" und "OnValueChanged()" nicht für eine berechnete Eigenschaft.

### <a name="alternative-technique-change-rules"></a>Alternative Technik: Änderungsregeln

Wenn Sie ein changerule definieren, wird es am Ende einer Transaktion ausgeführt, in der sich der Wert einer Eigenschaft ändert.  Weitere Informationen finden Sie unter [Regeln verbreiten Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).

Wenn in einer Transaktion mehrere Änderungen vorgenommen werden, wird die ChangeRule ausgeführt, wenn alle Änderungen abgeschlossen sind. Im Gegensatz dazu ist die onvalue... Methoden werden ausgeführt, wenn einige der Änderungen nicht durchgeführt wurden. Abhängig von Ihren Zielen kann eine ChangeRule daher für Sie vorteilhaft sein.

Sie können auch einen changerule verwenden, um den neuen Wert der Eigenschaft so anzupassen, dass er in einem bestimmten Bereich aufbewahrt wird.

> [!WARNING]
> Wenn eine Regel Änderungen am Speicherinhalt vornimmt, können andere Regeln und Eigenschaftenhandler ausgelöst werden. Wenn eine Regel die Eigenschaft ändert, von der die Regeln ausgelöst wurde, wird die Regel erneut aufgerufen. Sie müssen darauf achten, dass Ihre Regeldefinitionen nicht zu endlosem Auslösen führen.

```csharp
using Microsoft.VisualStudio.Modeling;
...
// Change rule on the domain class Comment:
[RuleOn(typeof(Comment), FireTime = TimeToFire.TopLevelCommit)]
class MyCommentTrimRule : ChangeRule
{
  public override void
    ElementPropertyChanged(ElementPropertyChangedEventArgs e)
  {
    base.ElementPropertyChanged(e);
    Comment comment = e.ModelElement as Comment;

    if (comment.Text.StartsWith(" ") || comment.Text.EndsWith(" "))
      comment.Text = comment.Text.Trim();
    // If changed, rule will trigger again.
  }
}

// Register the rule:
public partial class MyDomainModel
{
 protected override Type[] GetCustomDomainModelTypes()
 { return new Type[] { typeof(MyCommentTrimRule) };
 }
}
```

## <a name="example"></a>Beispiel

### <a name="description"></a>Beschreibung

Mit dem folgenden Beispiel wird der Eigenschaftenhandler einer Domäneneigenschaft überschrieben und der Benutzer informiert, wenn eine Eigenschaft der `ExampleElement`-Domänenklasse geändert wurde.

### <a name="code"></a>Code

```csharp
using DslModeling = global::Microsoft.VisualStudio.Modeling;
using DslDesign = global::Microsoft.VisualStudio.Modeling.Design;

namespace msft.FieldChangeSample
{
  public partial class ExampleElement
  {
    internal sealed partial class NamePropertyHandler
    {
      protected override void OnValueChanged(ExampleElement element,
         string oldValue, string newValue)
      {
        if (!this.Store.InUndoRedoOrRollback)
        {
           // make in-store changes here...
        }
        // This part is called even in undo:
        System.Windows.Forms.MessageBox.Show("Value Has Changed");
        base.OnValueChanged(element, oldValue, newValue);
      }
    }
  }
}
```
