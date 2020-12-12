---
title: Ereignishandler propagieren Änderungen außerhalb des Modells
description: Erfahren Sie, dass Sie im Visualisierungs-und Modellierungs-SDK Ereignishandler für die Speicherung definieren können, um Änderungen an Ressourcen außerhalb des Stores weiterzugeben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b0780007361115aa485b91db70cc413029a6f8f
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361676"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Ereignishandler propagieren Änderungen außerhalb des Modells

Im Visualisierungs-und Modellierungs-SDK können Sie Ereignishandler für die Speicherung definieren, um Änderungen an Ressourcen außerhalb des Speichers weiterzugeben, z. b. nicht-Speicher Variablen, Dateien, Modelle in anderen speichern oder anderen Visual Studio-Erweiterungen. Speicher Ereignishandler werden nach dem Ende der Transaktion ausgeführt, in der das auslösende Ereignis aufgetreten ist. Sie werden auch in einem Undo-oder Redo-Vorgang ausgeführt. Im Gegensatz zu Geschäftsregeln sind Store-Ereignisse daher am nützlichsten zum Aktualisieren von Werten, die sich außerhalb des Speicher befinden. Im Gegensatz zu .NET-Ereignissen werden Store-Ereignishandler für das Lauschen auf eine Klasse registriert: Sie müssen keinen separaten Handler für jede Instanz registrieren. Weitere Informationen zur Auswahl der verschiedenen Methoden zum Verarbeiten von Änderungen finden Sie unter [reagieren auf und](../modeling/responding-to-and-propagating-changes.md)weitergeben von Änderungen.

Die grafische Oberfläche und andere Steuerelemente der Benutzeroberfläche sind Beispiele für externe Ressourcen, die von Store-Ereignissen verarbeitet werden können.

### <a name="to-define-a-store-event"></a>So definieren Sie ein Store-Ereignis

1. Wählen Sie den Ereignistyp aus, den Sie überwachen möchten. Eine vollständige Liste finden Sie in den Eigenschaften von <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory> . Jede Eigenschaft entspricht einem Ereignistyp. Die am häufigsten verwendeten Ereignis Typen sind:

    - `ElementAdded` : wird ausgelöst, wenn ein Modellelement, beziehungslink, eine Form oder ein Connector erstellt wird.

    - Elementpropertychanged: wird ausgelöst, wenn der Wert einer `Normal` Domänen Eigenschaft geändert wird. Das-Ereignis wird nur ausgelöst, wenn die neuen und alten Werte nicht gleich sind. Das Ereignis kann nicht auf berechnete und benutzerdefinierte Speicher Eigenschaften angewendet werden.

         Sie kann nicht auf die Rollen Eigenschaften angewendet werden, die Beziehungslinks entsprechen. Verwenden Sie stattdessen, `ElementAdded` um die Domänen Beziehung zu überwachen.

    - `ElementDeleted` -ausgelöst, nachdem ein Modellelement, eine Beziehung, eine Form oder ein Connector gelöscht wurde. Sie können weiterhin auf die Eigenschaftswerte des Elements zugreifen, aber es sind keine Beziehungen zu anderen Elementen vorhanden.

2. Fügen Sie eine partielle Klassendefinition für _yourdsl_**docdata** in einer separaten Codedatei im **dslpackage** -Projekt hinzu.

3. Schreiben Sie den Code des Ereignisses als Methode, wie im folgenden Beispiel gezeigt. Dies ist möglich `static` , es sei denn, Sie möchten auf zugreifen `DocData` .

4. `OnDocumentLoaded()`Überschreiben, um den Handler zu registrieren. Wenn Sie mehr als einen Handler haben, können Sie alle am gleichen Ort registrieren.

Der Speicherort des Registrierungscodes ist nicht kritisch. `DocView.LoadView()` ist ein alternativer Speicherort.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.MusicLib
{
  partial class MusicLibDocData
  {
    // Register store events here or in DocView.LoadView().
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded(); // Don't forget this.

      #region Store event handler registration.
      Store store = this.Store;
      EventManagerDirectory emd = store.EventManagerDirectory;
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));
      emd.ElementAdded.Add(linkInfo,
          new EventHandler<ElementAddedEventArgs>(AddLink));
      emd.ElementDeleted.Add(linkInfo,
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));

      #endregion Store event handlers.
    }

    private void AddLink(object sender, ElementAddedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);
    }
    private void RemoveLink(object sender, ElementDeletedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);
    }
  }
}
```

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Verwenden Sie Ereignisse, um nicht wiederholbare Anpassungen im Speicher vorzunehmen.

Store-Ereignisse werden normalerweise nicht für die Weitergabe von Änderungen im Speicher verwendet, da der Ereignishandler ausgeführt wird, nachdem ein Commit für die Transaktion ausgeführt wurde. Stattdessen verwenden Sie eine Speicher Regel. Weitere Informationen finden Sie unter [Regeln verbreiten Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).

Sie können jedoch einen Ereignishandler verwenden, um zusätzliche Updates für den Speicher vorzunehmen, wenn Sie möchten, dass der Benutzer die zusätzlichen Updates getrennt vom ursprünglichen Ereignis rückgängig machen kann. Nehmen wir beispielsweise an, dass Kleinbuchstaben die übliche Konvention für Albumtitel sind. Sie könnten einen Store-Ereignishandler schreiben, der den Titel in einen Kleinbuchstaben korrigiert, nachdem der Benutzer ihn in Großbuchstaben eingegeben hat. Der Benutzer kann jedoch den Befehl "Rückgängig" verwenden, um die Korrektur abzubrechen und die Großbuchstaben wiederherzustellen. Eine zweite Rückgängig-Aktion entfernt die Änderung des Benutzers.

Wenn Sie dagegen eine Speicher Regel für denselben Zweck geschrieben haben, befinden sich die Änderung des Benutzers und die Korrektur in derselben Transaktion, sodass der Benutzer die Anpassung nicht rückgängig machen kann, ohne die ursprüngliche Änderung zu verlieren.

```csharp
partial class MusicLibDocView
{
    // Register store events here or in DocData.OnDocumentLoaded().
    protected override void LoadView()
    {
      /* Register store event handler for Album Title property. */
      // Get reflection data for property:
      DomainPropertyInfo propertyInfo =
        this.DocData.Store.DomainDataDirectory
        .FindDomainProperty(Album.TitleDomainPropertyId);
      // Add to property handler list:
      this.DocData.Store.EventManagerDirectory
        .ElementPropertyChanged.Add(propertyInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));

      /*
      // Alternatively, you can set one handler for
      // all properties of a class.
      // Your handler has to determine which property changed.
      DomainClassInfo classInfo = this.Store.DomainDataDirectory
           .FindDomainClass(typeof(Album));
      this.Store.EventManagerDirectory
          .ElementPropertyChanged.Add(classInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));
       */
      return base.LoadView();
    }

// Undoable adjustment after a property is changed.
// Method can be static since no local access.
private static void AlbumTitleAdjuster(object sender,
         ElementPropertyChangedEventArgs e)
{
  Album album = e.ModelElement as Album;
  Store store = album.Store;

  // We mustn't update the store in an Undo:
  if (store.InUndoRedoOrRollback
      || store.InSerializationTransaction)
      return;

  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)
  {
    string newValue = (string)e.NewValue;
    string lowerCase = newValue.ToLowerInvariant();
    if (!newValue.Equals(lowerCase))
    {
      using (Transaction t = store.TransactionManager
            .BeginTransaction("adjust album title"))
      {
        album.Title = lowerCase;
        t.Commit();
      } // Beware! This could trigger the event again.
    }
  }
  // else other properties of this class.
}
```

Wenn Sie ein Ereignis schreiben, das den Speicher aktualisiert:

- Verwenden `store.InUndoRedoOrRollback` Sie, um zu vermeiden, dass Änderungen an den Modellelementen in rückgängig Der Transaktions-Manager legt alle Elemente im Speicher auf den ursprünglichen Zustand zurück.

- Verwenden `store.InSerializationTransaction` Sie, um Änderungen vorzunehmen, während das Modell aus einer Datei geladen wird.

- Die Änderungen führen dazu, dass weitere Ereignisse ausgelöst werden. Stellen Sie sicher, dass Sie eine Endlosschleife vermeiden.

## <a name="store-event-types"></a>Speicher Ereignis Typen

Jeder Ereignistyp entspricht einer Sammlung in "Store. eventmanagerdirectory". Sie können Ereignishandler jederzeit hinzufügen oder entfernen, aber es ist üblich, Sie hinzuzufügen, wenn das Dokument geladen wird.

|`EventManagerDirectory` Eigenschaftsname|Wird ausgeführt, wenn|
|-|-|
|Element hinzugefügt|Eine Instanz einer Domänen Klasse, einer Domänen Beziehung, einer Form, eines Connector oder eines Diagramms wird erstellt.|
|Element Deleted|Ein Modellelement wurde aus dem Element Verzeichnis des Stores entfernt und ist nicht mehr die Quelle oder das Ziel einer Beziehung. Das Element wird nicht tatsächlich aus dem Arbeitsspeicher gelöscht, sondern wird bei einem späteren Rückgängigmachen beibehalten.|
|Elementeventsbegonnene|Wird am Ende einer äußeren Transaktion aufgerufen.|
|Elementeventsended|Wird aufgerufen, wenn alle anderen Ereignisse verarbeitet wurden.|
|Element verschoben|Ein Modellelement wurde von einer Speicher Partition in eine andere verschoben.<br /><br /> Dies steht nicht im Zusammenhang mit dem Speicherort einer Form im Diagramm.|
|Elementpropertychanged|Der Wert einer Domänen Eigenschaft hat sich geändert. Diese wird nur ausgeführt, wenn die alten und neuen Werte ungleich sind.|
|Roleplayerchanged|Eine der beiden Rollen (enden) einer Beziehung verweist auf ein neues Element.|
|Roleplayerorderchanged|In einer Rolle mit einer Multiplizität größer als 1 hat sich die Sequenz der Links geändert.|
|Transaktionat||
|Transaktioncommit||
|Transaktionrolledback||

## <a name="see-also"></a>Siehe auch

- [Reagieren auf und Propagieren von Änderungen](../modeling/responding-to-and-propagating-changes.md)
- [Beispielcode: Leitungs Diagramme](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
