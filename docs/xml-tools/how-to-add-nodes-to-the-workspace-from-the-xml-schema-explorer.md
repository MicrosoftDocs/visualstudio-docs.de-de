---
title: Hinzufügen von Knoten aus dem XML-Schema-Explorer zum Arbeitsbereich
description: Erfahren Sie, wie Sie dem Arbeitsbereich des XML-Schema-Designers Knoten entweder über das Kontextmenü oder durch das Ziehen und Ablegen von Knoten auf eine Ansicht im XML-Schema-Explorer hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f895d29e46556bff8543563841939640c501f84d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879266"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Vorgehensweise: Hinzufügen von Knoten aus dem XML-Schema-Explorer zum Arbeitsbereich

In diesem Thema wird beschrieben, wie dem [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md) Knoten aus dem **XML-Schema-Explorer** hinzugefügt werden. Knoten können einer XSD-Designer-Ansicht per Drag & Drop oder über das Kontextmenü des **XML-Schema-Explorers** hinzugefügt werden. Sie können auch Knoten hinzufügen, die als Ergebnis einer Suche zurückgegeben wurden und im **XML-Schema-Explorer** hervorgehoben sind. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von Knoten aus Schemaset-Suchergebnissen zum Arbeitsbereich](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md)

> [!NOTE]
> Dem [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md) können nur globale Knoten hinzugefügt werden.

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>So fügen Sie Knoten über das Kontextmenü des XML-Explorers hinzu

1. Führen Sie die unter [Vorgehensweise: Erstellen und Bearbeiten einer XSD-Schemadatei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md) aufgeführten Schritte durch.

2. Klicken Sie im XSD-Explorer mit der rechten Maustaste auf den `PurchaseOrderType`-Knoten. Wählen Sie **In Diagrammansicht anzeigen** aus.

     Der `purchaseOrderType`-Knoten wird auf der Entwurfsoberfläche der Diagrammansicht angezeigt.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>So verschieben Sie Knoten per Drag &amp; Drop in eine Ansicht

1. Klicken Sie mit der rechten Maustaste auf den `PurchaseOrderType`-Knoten in der Diagrammansicht. Wählen Sie **In XML-Schema-Explorer anzeigen** aus.

     Der Knoten wird im **XML-Schema-Explorer** hervorgehoben.

2. Klicken Sie mit der rechten Maustaste auf den `PurchaseOrderType`-Knoten im **XML-Schema-Explorer**, und wählen Sie **Alle Verweise anzeigen** aus.

     Der `purchaseOrder`-Knoten wird hervorgehoben.

3. Ziehen Sie den `purchaseOrder`-Knoten in die Diagrammansicht.

     Der `purchaseOrder`-Knoten und der `PurchaseOrderType`-Knoten werden nebeneinander auf der Entwurfsoberfläche der Diagrammansicht angezeigt. Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>So fügen Sie Knoten mithilfe der Suchfunktion des Schema-Explorers hinzu

1. Geben Sie „purchaseOrder“ in das Suchtextfeld auf der [XML-Explorer](../xml-tools/xml-schema-explorer.md)-Symbolleiste ein, und klicken Sie auf die Suchschaltfläche.

     ![Schlüsselwortsuche im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearch.gif)

     Die Suchergebnisse werden im **XML-Schema-Explorer** hervorgehoben und auf der vertikalen Bildlaufleiste durch Teilstriche markiert.

2. Fügen Sie die Suchergebnisse dem Arbeitsbereich hinzu, indem Sie im Bereich mit der Ergebniszusammenfassung auf die Schaltfläche **Hervorgehobene Knoten zu Arbeitsbereich hinzufügen** klicken.

     ![Suchergebnis im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

     Der `purchaseOrder`-Knoten und der `PurchaseOrderType`-Knoten werden nebeneinander auf der Entwurfsoberfläche der [Diagrammansicht](../xml-tools/graph-view.md) angezeigt. Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.

## <a name="see-also"></a>Siehe auch

- [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)
