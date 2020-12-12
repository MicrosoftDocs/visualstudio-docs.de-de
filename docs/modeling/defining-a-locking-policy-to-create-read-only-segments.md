---
title: Definieren einer Sperrrichtlinie zum Erstellen von schreibgeschützten Segmenten
description: Erfahren Sie, wie Sie eine Richtlinie für ein Programm definieren, um ein oder alle domänenspezifischen DSL-Modelle zu sperren, damit Sie gelesen, aber nicht geändert werden können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a76ae38b686e1c77acd9561e9c48fd3444565b0a
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363197"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definieren einer Sperrrichtlinie zum Erstellen von schreibgeschützten Segmenten
Mit der unveränderlichkeits-API des Visual Studio-Visualisierungs-und Modellierungs-SDKs kann ein Programm ein Domänen spezifisches DSL-Modell (Domain-Specific Language) sperren, sodass es gelesen, aber nicht geändert werden kann. Diese schreibgeschützte Option kann z. b. verwendet werden, damit ein Benutzer die Kollegen bitten kann, ein DSL-Modell zu kommentieren und zu überprüfen, es jedoch nicht möglich ist, die ursprüngliche zu ändern.

 Außerdem können Sie als Autor einer DSL eine *Sperr Richtlinie definieren.* Eine Sperr Richtlinie definiert, welche Sperren zulässig, nicht zulässig oder obligatorisch sind. Wenn Sie z. b. eine DSL veröffentlichen, können Sie Entwickler von Drittanbietern ermutigen, Sie durch neue Befehle zu erweitern. Sie können jedoch auch eine Sperr Richtlinie verwenden, um zu verhindern, dass Sie den schreibgeschützten Status der angegebenen Teile des Modells ändern.

> [!NOTE]
> Eine Sperr Richtlinie kann mithilfe von Reflektion umgangen werden. Er bietet eine klare Grenze für Entwickler von Drittanbietern, bietet aber keine hohe Sicherheit.

 Weitere Informationen und Beispiele finden Sie unter Visual Studio- [Visualisierungs-und Modellierungs-SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) -Website.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>Festlegen und erhalten von Sperren
 Sie können Sperren für den Speicher, für eine Partition oder für ein einzelnes Element festlegen. Mit dieser Anweisung wird beispielsweise verhindert, dass ein Modellelement gelöscht wird, und es wird außerdem verhindert, dass die Eigenschaften geändert werden:

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 Andere Sperr Werte können verwendet werden, um Änderungen in Beziehungen, Element Erstellung, Bewegung zwischen Partitionen und Neuanordnung von Verknüpfungen in einer Rolle zu verhindern.

 Die Sperren gelten sowohl für Benutzeraktionen als auch für Programmcode. Wenn Programmcode versucht, eine Änderung vorzunehmen, wird eine ausgelöst `InvalidOperationException` . Sperren werden bei einem Vorgang zum Rückgängigmachen oder wiederholen ignoriert.

 Mithilfe von können Sie feststellen, ob ein Element über eine beliebige Sperre verfügt, `IsLocked(Locks)` und Sie können den aktuellen Satz von Sperren für ein Element mithilfe von abrufen `GetLocks()` .

 Sie können eine Sperre festlegen, ohne eine Transaktion zu verwenden. Die Sperr Datenbank ist nicht Teil des Stores. Wenn Sie als Antwort auf eine Änderung eines Werts im Speicher, z. b. in OnValueChanged, eine Sperre festgelegt haben, sollten Sie Änderungen zulassen, die Teil eines Rückgängig-Vorgangs sind.

 Diese Methoden sind Erweiterungs Methoden, die im- <xref:Microsoft.VisualStudio.Modeling.Immutability> Namespace definiert sind.

### <a name="locks-on-partitions-and-stores"></a>Sperren für Partitionen und Speicher
 Sperren können auch auf Partitionen und den Speicher angewendet werden. Eine Sperre, die für eine Partition festgelegt wird, gilt für alle Elemente in der Partition. Mit der folgenden Anweisung wird beispielsweise verhindert, dass alle Elemente in einer Partition gelöscht werden, unabhängig von den Zuständen ihrer eigenen Sperren. Trotzdem können auch andere Sperren, wie z. b., `Locks.Property` für einzelne Elemente festgelegt werden:

```csharp
partition.SetLocks(Locks.Delete);
```

 Eine Sperre, die für den Speicher festgelegt wird, gilt für alle zugehörigen Elemente, unabhängig von den Einstellungen dieser Sperre für die Partitionen und die Elemente.

### <a name="using-locks"></a>Verwenden von Sperren
 Sie können Sperren verwenden, um Schemas wie die folgenden Beispiele zu implementieren:

- Lassen Sie Änderungen an allen Elementen und Beziehungen außer denen, die Kommentare darstellen, nicht zu. Dies ermöglicht es Benutzern, ein Modell zu kommentieren, ohne es zu ändern.

- Nicht zulassen von Änderungen in der Standard Partition, aber das Zulassen von Änderungen in der Diagramm Partition. Der Benutzer kann das Diagramm neu anordnen, das zugrunde liegende Modell jedoch nicht ändern.

- Nehmen Sie keine Änderungen am Speicher vor, außer eine Gruppe von Benutzern, die in einer separaten Datenbank registriert sind. Für andere Benutzer sind das Diagramm und das Modell schreibgeschützt.

- Änderungen am Modell nicht zulassen, wenn eine boolesche Eigenschaft des Diagramms auf true festgelegt ist. Geben Sie einen Menübefehl an, um diese Eigenschaft zu ändern. Dadurch wird sichergestellt, dass Benutzer nicht versehentlich Änderungen vornehmen.

- Hiermit wird das Hinzufügen und Löschen von Elementen und Beziehungen bestimmter Klassen nicht zugelassen, aber Eigenschafts Änderungen werden zugelassen. Dadurch erhält der Benutzer ein festes Formular, in dem die Eigenschaften ausgefüllt werden können.

## <a name="lock-values"></a>Sperr Werte
 Sperren können für einen Speicher, eine Partition oder ein einzelnes ModelElement festgelegt werden. Sperren sind eine- `Flags` Enumeration: Sie können ihre Werte mithilfe von ' &#124; ' kombinieren.

- Sperren von ModelElement enthalten immer die Sperren der Partition.

- Sperren einer Partition enthalten immer die Sperren des Stores.

  Eine Sperre für eine Partition oder einen Speicher kann nicht festgelegt werden, und gleichzeitig wird die Sperre für ein einzelnes Element deaktiviert.

|Wert|Dies bedeutet, wenn `IsLocked(Value)` true ist.|
|-|-|
|Keine|Keine Einschränkung.|
|Eigenschaft|Domänen Eigenschaften von Elementen können nicht geändert werden. Dies gilt nicht für Eigenschaften, die von der Rolle einer Domänen Klasse in einer Beziehung generiert werden.|
|Hinzufügen|Neue Elemente und Verknüpfungen können nicht in einer Partition oder einem Speicher erstellt werden.<br /><br /> Gilt nicht für `ModelElement` .|
|Verschieben|Das Element kann nicht zwischen Partitionen verschoben werden `element.IsLocked(Move)` , wenn true ist, oder wenn `targetPartition.IsLocked(Move)` true ist.|
|Löschen|Ein Element kann nicht gelöscht werden, wenn diese Sperre für das Element selbst oder für eines der Elemente festgelegt wird, an die der Löschvorgang weitergegeben werden soll, z. b. eingebettete Elemente und Formen.<br /><br /> Sie können verwenden `element.CanDelete()` , um zu ermitteln, ob ein Element gelöscht werden kann.|
|Neu anordnen|Die Reihenfolge der Links auf einem das RolePlayer kann nicht geändert werden.|
|Das RolePlayer|Der Satz von Links, die von diesem Element stammen, kann nicht geändert werden. Beispielsweise können neue Elemente unter diesem Element nicht eingebettet werden. Dies wirkt sich nicht auf Verknüpfungen aus, für die dieses Element das Ziel ist.<br /><br /> Wenn dieses Element ein Link ist, sind die Quelle und das Ziel nicht betroffen.|
|Alle|Bitweises OR der anderen-Werte.|

## <a name="locking-policies"></a>Sperren von Richtlinien
 Als Autor einer DSL können Sie eine *Sperr Richtlinie* definieren. Eine Sperr Richtlinie moderiert den Betrieb von setlocks (), sodass Sie verhindern können, dass bestimmte Sperren festgelegt werden, oder Sie können festlegen, dass bestimmte Sperren festgelegt werden müssen. In der Regel verwenden Sie eine Sperr Richtlinie, um zu verhindern, dass Benutzer oder Entwickler versehentlich die beabsichtigte Verwendung einer DSL verletzen, und zwar auf dieselbe Weise, wie Sie eine Variable deklarieren können `private` .

 Sie können auch eine Sperr Richtlinie verwenden, um Sperren für alle Elemente festzulegen, die vom Typ des Elements abhängig sind. Der Grund hierfür ist, dass `SetLocks(Locks.None)` immer aufgerufen wird, wenn ein Element erstmalig aus einer Datei erstellt oder deserialisiert wird.

 Es ist jedoch nicht möglich, eine Richtlinie zu verwenden, um die Sperren eines Elements während des Lebenszyklus zu verändern. Um diesen Effekt zu erzielen, sollten Sie Aufrufe von verwenden `SetLocks()` .

 Zum Definieren einer Sperr Richtlinie müssen Sie folgende Schritte ausführen:

- Erstellen Sie eine Klasse, die das <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> implementiert.

- Fügen Sie diese Klasse den Diensten hinzu, die über die docdata ihrer DSL verfügbar sind.

### <a name="to-define-a-locking-policy"></a>So definieren Sie eine Sperr Richtlinie
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> weist die folgende Definition auf:

```csharp
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 Diese Methoden werden aufgerufen, wenn ein Aufruf `SetLocks()` von für einen Speicher, eine Partition oder ein ModelElement erfolgt. In jeder Methode erhalten Sie einen vorgeschlagenen Satz von Sperren. Sie können die vorgeschlagene Menge zurückgeben, oder Sie können Sperren hinzufügen oder subtrahieren.

 Zum Beispiel:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  public class MyLockingPolicy : ILockingPolicy
  {
    /// <summary>
    /// Moderate SetLocks(this ModelElement target, Locks locks)
    /// </summary>
    /// <param name="element">target</param>
    /// <param name="proposedLocks">locks</param>
    /// <returns></returns>
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)
    {
      // In my policy, users can never delete an element,
      // and other developers cannot easily change that:
      return proposedLocks | Locks.Delete);
    }
    public Locks RefineLocks(Store store, Locks proposedLocks)
    {
      // Only one user can change this model:
      return Environment.UserName == "aUser"
           ? proposedLocks : Locks.All;
    }
```

 Um sicherzustellen, dass Benutzer immer Elemente löschen können, auch wenn andere Code Aufrufe `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 So lassen Sie die Änderungen an allen Eigenschaften jedes Elements von MyClass nicht zu:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>So machen Sie Ihre Richtlinie als Dienst verfügbar
 `DslPackage`Fügen Sie in Ihrem Projekt eine neue Datei hinzu, die Code enthält, der dem folgenden Beispiel ähnelt:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  // Override the DocData GetService() for this DSL.
  internal partial class YourDslDocData // Change
  {
    /// <summary>
    /// Custom locking policy cache.
    /// </summary>
    private ILockingPolicy myLockingPolicy = null;

    /// <summary>
    /// Called when a service is requested.
    /// </summary>
    /// <param name="serviceType">Service requested</param>
    /// <returns>Service implementation</returns>
    public override object GetService(System.Type serviceType)
    {
      if (serviceType == typeof(SLockingPolicy)
       || serviceType == typeof(ILockingPolicy))
      {
        if (myLockingPolicy == null)
        {
          myLockingPolicy = new MyLockingPolicy();
        }
        return myLockingPolicy;
      }
      // Request is for some other service.
      return base.GetService(serviceType);
    }
}
```
