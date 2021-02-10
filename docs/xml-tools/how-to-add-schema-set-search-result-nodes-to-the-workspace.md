---
title: Hinzufügen von Knoten aus dem Schemaset-Suchergebnis
description: Erfahren Sie, wie dem Arbeitsbereich Knoten hinzugefügt werden, die im XML-Schema-Explorer als Ergebnis einer Schlüsselwortsuche hervorgehoben sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 762992ab2649e59055af8fd656514f3e82e9e8de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879214"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Vorgehensweise: Hinzufügen von Knoten aus Schemaset-Suchergebnissen zum Arbeitsbereich

In diesem Thema wird erläutert, wie dem Arbeitsbereich Knoten hinzugefügt werden, die im **XML-Schema-Explorer** als Ergebnis einer Schlüsselwortsuche hervorgehoben sind.

> [!NOTE]
> Dem [Arbeitsbereich](../xml-tools/xml-schema-designer-workspace.md) können nur globale Knoten hinzugefügt werden.

In diesem Beispiel wird das Beispiel-[Bestellungsschema](../xml-tools/sample-xsd-file-purchase-order-schema.md) verwendet.

## <a name="to-add-schema-set-result-nodes"></a>So fügen Sie Knoten aus Ergebnissen einer Schemasetsuche hinzu

1. Führen Sie die unter [Vorgehensweise: Erstellen und Bearbeiten einer XSD-Schemadatei](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md) aufgeführten Schritte durch.

2. Geben Sie „purchaseOrder“ in das Suchtextfeld auf der [XML-Explorer](../xml-tools/xml-schema-explorer.md)-Symbolleiste ein, und klicken Sie auf die Suchschaltfläche.

     ![Schlüsselwortsuche im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearch.gif)

     Die Suchergebnisse werden im **XML-Schema-Explorer** hervorgehoben und auf der vertikalen Bildlaufleiste durch Teilstriche markiert.

3. Fügen Sie die Suchergebnisse dem Arbeitsbereich hinzu, indem Sie im Bereich mit der Ergebniszusammenfassung auf die Schaltfläche **Hervorgehobene Knoten zu Arbeitsbereich hinzufügen** klicken.

     ![Suchergebnis im XML-Schema-Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

     Der `purchaseOrder`-Knoten und der `PurchaseOrderType`-Knoten werden nebeneinander auf der Entwurfsoberfläche der [Diagrammansicht](../xml-tools/graph-view.md) angezeigt. Da die zwei Knoten miteinander verknüpft sind (das `purchaseOrder`-Element ist vom `PurchaseOrderType`-Typ), wird ein Pfeil zwischen den Elementen gezeichnet.
