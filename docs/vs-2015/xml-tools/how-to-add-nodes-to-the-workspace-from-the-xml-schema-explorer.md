---
title: 'Vorgehensweise: Hinzufügen von Knoten zum Arbeitsbereich aus dem XML-Schema-Explorer | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e0c8fe9d5ba8c096a03de7a9df85945f4aeb4a0a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656348"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Gewusst wie: Hinzufügen von Knoten aus dem XML-Schema-Explorer zum Arbeitsbereich
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird erläutert, wie Knoten im XML-Schema-Explorer zum [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md) hinzugefügt werden. Knoten können einer XSD-Designer-Ansicht per Drag &amp; Drop oder über das Kontextmenü des XML-Schema-Explorers hinzugefügt werden. Sie können auch Knoten hinzufügen, die als Ergebnis einer Suche zurückgegeben wurden und im XML-Schema-Explorer hervorgehoben sind. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen von Schema Satz-Suchergebnis Knoten zum Arbeitsbereich](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Dem [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md)können nur globale Knoten hinzugefügt werden.

### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>So fügen Sie Knoten über das Kontextmenü des XML-Explorers hinzu

1. Befolgen Sie die Schritte unter Gewusst [wie: Erstellen und Bearbeiten einer XSD-Schema Datei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Klicken Sie im XSD-Explorer mit der rechten Maustaste auf den `PurchaseOrderType`-Knoten. Wählen Sie **In Diagrammansicht anzeigen** aus.

     Der `purchaseOrderType`-Knoten wird auf der Entwurfsoberfläche der Diagrammansicht angezeigt.

### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>So verschieben Sie Knoten per Drag &amp; Drop in eine Ansicht

1. Klicken Sie mit der rechten Maustaste auf den `PurchaseOrderType`-Knoten in der Diagrammansicht. Wählen Sie **In XML-Schema-Explorer anzeigen** aus.

     Der Knoten wird im XML-Schema-Explorer hervorgehoben.

2. Klicken Sie mit der rechten Maustaste auf den `PurchaseOrderType`-Knoten im XML-Schema-Explorer, und wählen Sie **Alle Verweise anzeigen** aus.

     Der `purchaseOrder`-Knoten wird hervorgehoben.

3. Ziehen Sie den `purchaseOrder`-Knoten in die Diagrammansicht.

     Der `purchaseOrder`-Knoten und der `PurchaseOrderType`-Knoten werden nebeneinander auf der Entwurfsoberfläche der Diagrammansicht angezeigt. Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.

### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>So fügen Sie Knoten mithilfe der Suchfunktion des Schema-Explorers hinzu

1. Geben Sie „purchaseOrder“ in das Suchtextfeld auf der [XML-Explorer](../xml-tools/xml-schema-explorer.md)-Symbolleiste ein, und klicken Sie auf die Suchschaltfläche.

     ![Schlüsselwortsuche im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     Die Suchergebnisse werden im XML-Schema-Explorer hervorgehoben und auf der vertikalen Bildlaufleiste durch Teilstriche markiert.

2. Fügen Sie die Suchergebnisse dem Arbeitsbereich hinzu, indem Sie im Bereich mit der Ergebniszusammenfassung auf die Schaltfläche **Hervorgehobene Knoten zu Arbeitsbereich hinzufügen** klicken.

     ![Suchergebnis im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     Der `purchaseOrder`-Knoten und der `PurchaseOrderType`-Knoten werden nebeneinander auf der Entwurfsoberfläche der [Diagrammansicht](../xml-tools/graph-view.md) angezeigt. Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.

## <a name="see-also"></a>Weitere Informationen
 [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)
