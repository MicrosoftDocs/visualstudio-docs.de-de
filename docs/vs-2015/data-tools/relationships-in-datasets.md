---
title: Beziehungen in Datasets | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eb13ad7db9a4f13ce9bf983ce6327045f885f4d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652884"
---
# <a name="relationships-in-datasets"></a>Beziehungen in DataSets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Datasets, die Verwandte Datentabellen enthalten, verwenden- <xref:System.Data.DataRelation> Objekte zum Darstellen einer über-/Unterordnungsbeziehung zwischen den Tabellen und zum Zurückgeben von verknüpften Datensätzen voneinander. Durch das Hinzufügen verknüpfter Tabellen zu Datasets mithilfe des **Assistenten zum Konfigurieren von Datenquellen**oder des **DataSet-Designer**wird das Objekt erstellt und konfiguriert <xref:System.Data.DataRelation> .

 Das- <xref:System.Data.DataRelation> Objekt führt zwei Funktionen aus:

- Sie kann die Datensätze im Zusammenhang mit einem Datensatz verfügbar machen, mit dem Sie arbeiten. Sie stellt untergeordnete Datensätze bereit, wenn Sie sich in einem übergeordneten Datensatz ( <xref:System.Data.DataRow.GetChildRows%2A> ) und einem übergeordneten Datensatz befinden, wenn Sie mit einem untergeordneten Datensatz arbeiten ( <xref:System.Data.DataRow.GetParentRow%2A> ).

- Sie kann Einschränkungen für die referenzielle Integrität erzwingen, z. b. das Löschen verwandter untergeordneter Datensätze, wenn Sie einen übergeordneten Datensatz löschen.

  Es ist wichtig, den Unterschied zwischen einem echten Join und der-Funktion eines-Objekts zu verstehen <xref:System.Data.DataRelation> . Bei einem echten Join werden Datensätze aus übergeordneten und untergeordneten Tabellen entnommen und in ein einzelnes, flaches Recordset eingefügt. Wenn Sie ein- <xref:System.Data.DataRelation> Objekt verwenden, wird kein neues Recordset erstellt. Stattdessen verfolgt die DataRelations die Beziehung zwischen Tabellen nach und speichert übergeordnete und untergeordnete Datensätze synchron.

## <a name="datarelation-objects-and-constraints"></a>DataRelations-Objekte und-Einschränkungen
 Ein <xref:System.Data.DataRelation> -Objekt wird auch zum Erstellen und erzwingen der folgenden Einschränkungen verwendet:

- Eine Unique-Einschränkung, die sicherstellt, dass eine Spalte in der Tabelle keine Duplikate enthält.

- Eine FOREIGN KEY-Einschränkung, die zur Aufrechterhaltung der referenziellen Integrität zwischen einer übergeordneten und untergeordneten Tabelle in einem DataSet verwendet werden kann.

  Einschränkungen, die Sie in einem-Objekt angeben, <xref:System.Data.DataRelation> werden implementiert, indem automatisch geeignete Objekte erstellt oder Eigenschaften festgelegt werden. Wenn Sie eine FOREIGN KEY-Einschränkung mithilfe des- <xref:System.Data.DataRelation> Objekts erstellen, werden Instanzen der <xref:System.Data.ForeignKeyConstraint> -Klasse der-Eigenschaft des-Objekts hinzugefügt <xref:System.Data.DataRelation> <xref:System.Data.DataRelation.ChildKeyConstraint%2A> .

  Eine Unique-Einschränkung wird entweder durch einfaches Festlegen der <xref:System.Data.DataColumn.Unique%2A> -Eigenschaft einer Datenspalte auf `true` oder durch Hinzufügen einer Instanz der <xref:System.Data.UniqueConstraint> -Klasse zur <xref:System.Data.DataRelation> -Eigenschaft des-Objekts implementiert <xref:System.Data.DataRelation.ParentKeyConstraint%2A> . Informationen zum Anhalten von Einschränkungen in einem Dataset finden Sie unter [Deaktivieren von Einschränkungen beim Auffüllen eines Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

### <a name="referential-integrity-rules"></a>Regeln für die referenzielle Integrität
 Als Teil der FOREIGN KEY-Einschränkung können Sie referenzielle Integritäts Regeln angeben, die an drei Punkten angewendet werden:

- Wenn ein übergeordneter Datensatz aktualisiert wird

- Wenn ein übergeordneter Datensatz gelöscht wird

- Wenn eine Änderung akzeptiert oder abgelehnt wird

  Die Regeln, die Sie vornehmen können, werden in der <xref:System.Data.Rule> -Enumeration angegeben und sind in der folgenden Tabelle aufgeführt.

|Foreign Key-Einschränkungs Regel|Aktion|
|----------------------------------|------------|
|<xref:System.Data.Rule>|Die Änderung (aktualisieren oder löschen), die am übergeordneten Datensatz vorgenommen wurde, erfolgt auch in verknüpften Datensätzen in der untergeordneten Tabelle.|
|<xref:System.Data.Rule>|Untergeordnete Datensätze werden nicht gelöscht, aber der Fremdschlüssel in den untergeordneten Datensätzen wird auf festgelegt <xref:System.DBNull> . Mit dieser Einstellung können untergeordnete Datensätze als "verwaiste" verbleiben, d. –., Sie haben keine Beziehung zu übergeordneten Datensätzen. **Hinweis:**  Die Verwendung dieser Regel kann zu ungültigen Daten in der untergeordneten Tabelle führen.|
|<xref:System.Data.Rule>|Der Fremdschlüssel in den zugehörigen untergeordneten Datensätzen wird auf seinen Standardwert festgelegt (wie durch die-Eigenschaft der Spalte festgelegt <xref:System.Data.DataColumn.DefaultValue%2A> ).|
|<xref:System.Data.Rule>|An verwandten untergeordneten Datensätzen wird keine Änderung vorgenommen. Mit dieser Einstellung können untergeordnete Datensätze Verweise auf ungültige übergeordnete Datensätze enthalten.|

 Weitere Informationen zu Updates in Dataset-Tabellen finden [Sie unter Speichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md).

### <a name="constraint-only-relations"></a>Nur einschränkende Beziehungen
 Wenn Sie ein- <xref:System.Data.DataRelation> Objekt erstellen, können Sie angeben, dass die Beziehung nur verwendet werden soll, um Einschränkungen zu erzwingen, d. –., dass Sie nicht auch für den Zugriff auf verwandte Datensätze verwendet wird. Sie können diese Option verwenden, um ein DataSet zu generieren, das etwas effizienter ist und weniger Methoden als eine mit der Funktion für verbundene Datensätze enthält. Allerdings sind Sie nicht in der Lage, auf zugehörige Datensätze zuzugreifen. Beispielsweise verhindert eine Einschränkung nur Einschränkung, dass ein übergeordneter Datensatz gelöscht wird, der noch über untergeordnete Datensätze verfügt, und Sie können nicht über das übergeordnete Element auf die untergeordneten Datensätze zugreifen.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Manuelles Erstellen einer Daten Beziehung im DataSet-Designer
 Wenn Sie Datentabellen mit den Daten Entwurfs Tools in Visual Studio erstellen, werden die Beziehungen automatisch erstellt, wenn die Informationen aus der Datenquelle erfasst werden können. Wenn Sie Datentabellen manuell von der Registerkarte **DataSet** der **Toolbox**hinzufügen, müssen Sie die Beziehung möglicherweise manuell erstellen. Informationen zum programmgesteuerten Erstellen von <xref:System.Data.DataRelation> Objekten finden Sie unter [Hinzufügen von DataRelations](https://msdn.microsoft.com/library/a4a564fb-c1c4-4135-b6c2-b030e51195e4)-Objekten.

 Beziehungen zwischen Datentabellen werden in der **DataSet-Designer**als Zeilen angezeigt, wobei ein Schlüssel-und Unendlichkeits Symbol den 1: n-Aspekt der Beziehung darstellt. Standardmäßig wird der Name der relationshipcommentend-ID = ' 1c8c78e19b7fa441 ' nicht auf der Entwurfs Oberfläche angezeigt.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>So erstellen Sie eine Beziehung zwischen zwei Datentabellen

1. Öffnen Sie das Dataset im **DataSet-Designer**. Weitere Informationen finden Sie unter Gewusst [wie: Öffnen eines Datasets in der DataSet-Designer](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Ziehen Sie ein **Beziehungs** Objekt aus der **DataSet** -Toolbox auf die untergeordnete Datentabelle in der Beziehung.

     Das Dialogfeld **Beziehung** wird geöffnet, in dem Sie das untergeordnete **Tabellen** Feld mit der Tabelle auffüllen, auf die Sie das **Beziehungs** Objekt gezogen haben.

3. Wählen Sie die übergeordnete Tabelle aus dem Feld über **geordnete Tabelle** aus. Die übergeordnete Tabelle enthält Datensätze auf der 1-Seite einer 1: n-Beziehung.

4. Vergewissern Sie sich, dass im Feld untergeordnete **Tabelle** die richtige untergeordnete Tabelle angezeigt wird. Die untergeordnete Tabelle enthält Datensätze auf der Seite "Many" einer 1: n-Beziehung.

5. Geben Sie im Feld **Name** einen Namen für die Beziehung ein, oder belassen Sie den Standardnamen auf der Grundlage der ausgewählten Tabellen. Dies ist der Name des eigentlichen <xref:System.Data.DataRelation> Objekts im Code.

6. Wählen Sie die Spalten aus, die die Tabellen in den Listen **Schlüssel Spalten** und **Fremdschlüssel Spalten** verknüpfen.

7. Wählen Sie aus, ob eine Beziehung, eine Einschränkung oder beides erstellt werden soll. Weitere Informationen finden [Sie unter Introduction to DataRelations Objects](https://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).

8. Aktivieren bzw. deaktivieren Sie das Feld für die Feld- **Beziehung** . Wenn Sie diese Option auswählen <xref:System.Data.DataRelation.Nested%2A> , wird die-Eigenschaft auf festgelegt `true` und bewirkt, dass die untergeordneten Zeilen der Beziehung innerhalb der übergeordneten Spalte geschachtelt werden, wenn diese Zeilen als XML-Daten geschrieben oder mit synchronisiert werden <xref:System.Xml.XmlDataDocument> . Weitere Informationen finden Sie unter Schachteln von [DataRelations](https://msdn.microsoft.com/library/9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab)-Elementen.

9. Legen Sie die Regeln fest, die erzwungen werden sollen, wenn Sie Änderungen an Datensätzen in diesen Tabellen vornehmen. Weitere Informationen finden Sie unter <xref:System.Data.Rule>.

10. Klicken Sie auf **OK** , um die Beziehung zu erstellen. Im Designer wird zwischen den beiden Tabellen eine Beziehungs Linie angezeigt.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>So zeigen Sie einen Beziehungs Namen im DataSet-Designer an

1. Öffnen Sie das Dataset im **DataSet-Designer**. Weitere Informationen finden Sie unter Gewusst [wie: Öffnen eines Datasets in der DataSet-Designer](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Wählen Sie im Menü **Daten** den Befehl **Relation Labels anzeigen** aus, um den Beziehungs Namen anzuzeigen. Löschen Sie diesen Befehl, um den Beziehungs Namen auszublenden.
