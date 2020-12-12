---
title: Regeln propagieren Änderungen im Modell
description: Erfahren Sie, wie Sie eine Geschäftsregel erstellen können, um eine Änderung von einem Element zu einem anderen im Visualisierungs-und Modellierungs-SDK (vmsdk) weiterzugeben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4ff2273c8c71582c3ef634eeb398b12e29401d0
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363951"
---
# <a name="rules-propagate-changes-within-the-model"></a>Regeln propagieren Änderungen im Modell
Sie können eine Speicher Regel erstellen, um eine Änderung von einem Element zu einem anderen im Visualisierungs-und Modellierungs-SDK (vmsdk) weiterzugeben. Wenn eine Änderung an einem Element im Speicher vorgenommen wird, werden die Regeln für die Ausführung geplant, in der Regel, wenn für die äußerste Transaktion ein Commit ausgeführt wird. Es gibt verschiedene Typen von Regeln für verschiedene Arten von Ereignissen, z. b. das Hinzufügen eines Elements oder das Löschen. Sie können Regeln an bestimmte Typen von Elementen, Formen oder Diagrammen anfügen. Viele integrierte Funktionen werden durch Regeln definiert: beispielsweise stellen Regeln sicher, dass ein Diagramm aktualisiert wird, wenn sich das Modell ändert. Sie können Ihre domänenspezifische Sprache anpassen, indem Sie Ihre eigenen Regeln hinzufügen.

 Speicher Regeln sind besonders nützlich für das Weitergeben von Änderungen im Speicher, d. h. Änderungen an Modellelementen, Beziehungen, Formen oder Connectors und ihren Domänen Eigenschaften. Regeln werden nicht ausgeführt, wenn der Benutzer die Befehle zum Rückgängigmachen oder wiederholen aufruft. Stattdessen stellt der Transaktions-Manager sicher, dass die Speicherinhalte im richtigen Zustand wieder hergestellt werden. Wenn Sie Änderungen an Ressourcen außerhalb des Stores weitergeben möchten, verwenden Sie Store-Ereignisse. Weitere Informationen finden Sie unter [Ereignishandler verbreiten Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Nehmen Sie beispielsweise an, dass Sie angeben möchten, dass jedes Mal, wenn der Benutzer (oder Ihr Code) ein neues Element vom Typ "exampledomainclass" erstellt, ein zusätzliches Element eines anderen Typs in einem anderen Teil des Modells erstellt wird. Sie könnten ein AddRule schreiben und es mit exampledomainclass verknüpfen. Sie würden Code in der Regel schreiben, um das zusätzliche Element zu erstellen.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;

namespace ExampleNamespace
{
 // Attribute associates the rule with a domain class:
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class MyAddRule : AddRule
 {
  // Override the abstract method:
  public override void ElementAdded(ElementAddedEventArgs e)
  {
    base.ElementAdded(e);
    ExampleDomainClass element = e.ModelElement;
    Store store = element.Store;
    // Ignore this call if we're currently loading a model:
    if (store.TransactionManager.CurrentTransaction.IsSerializing)
       return;

    // Code here propagates change as required - for example:
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);
      echo.Name = element.Name;
      echo.Parent = element.Parent;
    }
  }
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
   protected override Type[] GetCustomDomainModelTypes()
   {
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
     types.Add(typeof(MyAddRule));
     // If you add more rules, list them here.
     return types.ToArray();
   }
 }
}
```

> [!NOTE]
> Der Code einer Regel sollte nur den Status von Elementen innerhalb des Stores ändern. Das heißt, die Regel sollte nur Modellelemente, Beziehungen, Formen, Connectors, Diagramme oder deren Eigenschaften ändern. Wenn Sie Änderungen an Ressourcen außerhalb des Stores weitergeben möchten, definieren Sie Store-Ereignisse. Weitere Informationen finden Sie unter [Ereignishandler verbreiten Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).

### <a name="to-define-a-rule"></a>So definieren Sie eine Regel

1. Definieren Sie die Regel als eine Klasse, die das-Attribut als Präfix hat `RuleOn` . Das-Attribut ordnet die Regel einer der Domänen Klassen, Beziehungen oder Diagramm Elemente zu. Die Regel wird auf jede Instanz dieser Klasse angewendet, die möglicherweise abstrakt ist.

2. Registrieren Sie die Regel, indem Sie Sie der von `GetCustomDomainModelTypes()` in ihrer Domänen Modell Klasse zurückgegebenen Menge hinzufügen.

3. Leiten Sie die Regelklasse von einer der abstrakten Regelklassen ab, und schreiben Sie den Code der Ausführungs Methode.

   In den folgenden Abschnitten werden diese Schritte ausführlicher beschrieben.

### <a name="to-define-a-rule-on-a-domain-class"></a>So definieren Sie eine Regel für eine Domänen Klasse

- Definieren Sie in einer benutzerdefinierten Codedatei eine-Klasse, und stellen Sie Ihr das- <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> Attribut voran:

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- Der subjekttyp im ersten Parameter kann eine Domänen Klasse, eine Domänen Beziehung, eine Form, ein Connector oder ein Diagramm sein. Normalerweise wenden Sie Regeln auf Domänen Klassen und Beziehungen an.

     `FireTime`Ist in der Regel `TopLevelCommit` . Dadurch wird sichergestellt, dass die Regel erst ausgeführt wird, nachdem alle primären Änderungen der Transaktion vorgenommen wurden. Die Alternativen sind Inline, wodurch die Regel kurz nach der Änderung ausgeführt wird. und localcommit, das die Regel am Ende der aktuellen Transaktion ausführt (was möglicherweise nicht der äußerste Wert ist). Sie können auch die Priorität einer Regel festlegen, um die Reihenfolge in der Warteschlange zu beeinflussen, aber dies ist eine unzuverlässige Methode, um das gewünschte Ergebnis zu erzielen.

- Sie können eine abstrakte Klasse als subjekttyp angeben.

- Die Regel gilt für alle Instanzen der Subject-Klasse.

- Der Standardwert für `FireTime` ist Timeto Fire. toplevelcommit. Dies bewirkt, dass die Regel ausgeführt wird, wenn für die äußerste Transaktion ein Commit ausgeführt wird. Eine Alternative ist timetofire. Inline. Dies bewirkt, dass die Regel bald nach dem auslösenden Ereignis ausgeführt wird.

### <a name="to-register-the-rule"></a>So registrieren Sie die Regel

- Fügen Sie die Regelklasse der Liste der Typen hinzu, die von `GetCustomDomainModelTypes` in Ihrem Domänen Modell zurückgegeben werden:

    ```csharp
    public partial class ExampleDomainModel
     {
       protected override Type[] GetCustomDomainModelTypes()
       {
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
         types.Add(typeof(MyAddRule));
         // If you add more rules, list them here.
         return types.ToArray();
       }
     }

    ```

- Wenn Sie sich nicht sicher sind, welchen Namen die Domänen Modell Klasse hat, suchen Sie in der Datei " **dsl\generatedcode\domainmodel.cs** ".

- Schreiben Sie diesen Code in eine benutzerdefinierte Codedatei in Ihrem DSL-Projekt.

### <a name="to-write-the-code-of-the-rule"></a>So schreiben Sie den Code der Regel

- Leiten Sie die Regelklasse von einer der folgenden Basisklassen ab:

  | Basisklasse | Trigger |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Ein Element, ein Link oder eine Form wird hinzugefügt.<br /><br /> Verwenden Sie diese Informationen, um neue Beziehungen zusätzlich zu neuen Elementen zu erkennen. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Ein Domänen Eigenschafts Wert wurde geändert. Das Method-Argument stellt die alten und neuen Werte bereit.<br /><br /> Bei Formen wird diese Regel ausgelöst, wenn die integrierte `AbsoluteBounds` Eigenschaft geändert wird, wenn die Form verschoben wird.<br /><br /> In vielen Fällen ist es bequemer, `OnValueChanged` oder `OnValueChanging` im Eigenschaften Handler zu überschreiben. Diese Methoden werden unmittelbar vor und nach der Änderung aufgerufen. Im Gegensatz dazu wird die Regel am Ende der Transaktion ausgeführt. Weitere Informationen finden Sie unter [Domänen Eigenschafts Wert-Änderungs Handler](../modeling/domain-property-value-change-handlers.md). **Hinweis:**  Diese Regel wird nicht ausgelöst, wenn ein Link erstellt oder gelöscht wird. Schreiben Sie stattdessen einen `AddRule` und einen `DeleteRule` für die Domänen Beziehung. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Wird ausgelöst, wenn ein Element oder Link im Begriff ist, gelöscht zu werden. Die Eigenschaft "ModelElement. islösch" ist bis zum Ende der Transaktion "true". |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Wird ausgeführt, wenn ein Element oder ein Link gelöscht wurde. Die Regel wird ausgeführt, nachdem alle anderen Regeln ausgeführt wurden, einschließlich Delta ingrules. ModelElement. IsDeleted ist false, und ModelElement. IsDeleted ist "true". Damit eine nachfolgende Rückgängig-Aktion zulässig ist, wird das Element nicht tatsächlich aus dem Arbeitsspeicher entfernt, sondern aus "Store. Element Directory" entfernt. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Ein Element wird von einer Speicher Partition in eine andere verschoben.<br /><br /> (Beachten Sie, dass dies nicht mit der grafischen Position einer Form verknüpft ist.) |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Diese Regel gilt nur für Domänen Beziehungen. Sie wird ausgelöst, wenn Sie ein Modellelement explizit an beide Enden eines Links zuweisen. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Wird ausgelöst, wenn die Reihenfolge von Verknüpfungen zu oder von einem Element mithilfe der Methoden "muvebefore" oder "muvedeindex" in einem Link geändert wird. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Wird ausgeführt, wenn eine Transaktion erstellt wird. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | Wird ausgeführt, wenn ein Commit für die Transaktion ausgeführt wird. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | Wird ausgeführt, wenn ein Rollback für die Transaktion ausgeführt wird. |

- Jede Klasse verfügt über eine Methode, die Sie überschreiben. Geben `override` Sie Ihre Klasse ein, um Sie zu ermitteln. Der-Parameter dieser Methode identifiziert das Element, das geändert wird.

  Beachten Sie die folgenden Punkte zu Regeln:

1. Der Satz von Änderungen in einer Transaktion löst möglicherweise viele Regeln aus. Normalerweise werden die Regeln ausgeführt, wenn für die äußerste Transaktion ein Commit ausgeführt wird. Sie werden in einer nicht angegebenen Reihenfolge ausgeführt.

2. Eine Regel wird immer innerhalb einer Transaktion ausgeführt. Daher ist es nicht erforderlich, eine neue Transaktion zu erstellen, um Änderungen vorzunehmen.

3. Regeln werden nicht ausgeführt, wenn für eine Transaktion ein Rollback ausgeführt wird oder wenn die rückgängig-oder Redo-Vorgänge ausgeführt werden. Mit diesen Vorgängen wird der gesamte Inhalt des Stores auf den vorherigen Zustand zurückgesetzt. Wenn die Regel den Zustand von etwas außerhalb des Stores ändert, wird die Synchronisierung mit dem Speicherinhalt daher möglicherweise nicht synchron gehalten. Um den Zustand außerhalb des Stores zu aktualisieren, ist es besser, Ereignisse zu verwenden. Weitere Informationen finden Sie unter [Ereignishandler verbreiten Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4. Einige Regeln werden ausgeführt, wenn ein Modell aus einer Datei geladen wird. Verwenden Sie, um zu bestimmen, ob das Laden oder speichern gerade ausgeführt wird `store.TransactionManager.CurrentTransaction.IsSerializing` .

5. Wenn der Code Ihrer Regel weitere Regel Trigger erstellt, werden Sie am Ende der auslösenden Liste hinzugefügt und vor Abschluss der Transaktion ausgeführt. Deletedrules werden nach allen anderen Regeln ausgeführt. Eine Regel kann mehrmals für jede Änderung in einer Transaktion ausgeführt werden.

6. Um Informationen an und von Regeln zu übergeben, können Sie Informationen in der speichern `TransactionContext` . Dabei handelt es sich nur um ein Wörterbuch, das während der Transaktion beibehalten wird. Sie wird verworfen, wenn die Transaktion endet. Die Ereignis Argumente in jeder Regel ermöglichen den Zugriff darauf. Beachten Sie, dass Regeln nicht in einer vorhersagbaren Reihenfolge ausgeführt werden.

7. Verwenden Sie Regeln, nachdem Sie andere Alternativen geprüft haben. Wenn Sie z. b. eine Eigenschaft aktualisieren möchten, wenn sich ein Wert ändert, sollten Sie eine berechnete Eigenschaft verwenden. Wenn Sie die Größe oder Position einer Form einschränken möchten, verwenden Sie eine `BoundsRule` . Wenn Sie auf eine Änderung in einem Eigenschafts Wert reagieren möchten, fügen Sie `OnValueChanged` der-Eigenschaft einen-Handler hinzu. Weitere Informationen finden Sie unter [reagieren auf und](../modeling/responding-to-and-propagating-changes.md)weitergeben von Änderungen.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird eine-Eigenschaft aktualisiert, wenn eine Domänen Beziehung zum Verknüpfen von zwei Elementen instanziiert wird. Die Regel wird nicht nur ausgelöst, wenn der Benutzer einen Link in einem Diagramm erstellt, sondern auch, wenn der Programmcode einen Link erstellt.

 Um dieses Beispiel zu testen, erstellen Sie eine DSL mithilfe der Lösungs Vorlage für den Task Fluss, und fügen Sie den folgenden Code in eine Datei im DSL-Projekt ein. Erstellen Sie die Projekt Mappe, und führen Sie Sie aus, und öffnen Sie die Beispieldatei im debugprojekt. Zeichnen Sie einen Kommentar Link zwischen einer Kommentar Form und einem Flow-Element. Der Text im Kommentar ändert sich in Bericht über das letzte Element, mit dem Sie eine Verbindung hergestellt haben.

 In der Praxis würden Sie in der Regel eine DeleteRule für jedes AddRule schreiben.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.TaskRuleExample
{

  [RuleOn(typeof(CommentReferencesSubjects))]
  public class RoleRule : AddRule
  {

    public override void ElementAdded(ElementAddedEventArgs e)
    {
      base.ElementAdded(e);
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;
      Comment comment = link.Comment;
      FlowElement subject = link.Subject;
      Transaction current = link.Store.TransactionManager.CurrentTransaction;
      // Don't want to run when we're just loading from file:
      if (current.IsSerializing) return;
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";
    }

  }

  public partial class TaskRuleExampleDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(RoleRule));
      return types.ToArray();
    }
  }

}
```

## <a name="see-also"></a>Siehe auch

- [Ereignishandler propagieren Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md)