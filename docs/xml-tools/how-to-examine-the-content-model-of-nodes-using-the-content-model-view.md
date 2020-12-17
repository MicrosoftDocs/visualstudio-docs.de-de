---
title: Untersuchen des Inhaltsmodells von Knoten
description: In diesem Artikel erfahren Sie, wie Sie die Inhaltsmodellansicht im XML-Schema-Designer verwenden, um das Inhaltsmodell der Knoten in einem XML-Schema zu untersuchen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3ce3d1a47125c446521ceb60a851322c37209d0
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995277"
---
# <a name="how-to-examine-the-content-model-of-nodes-by-using-the-content-model-view"></a>Vorgehensweise: Untersuchen des Inhaltsmodells von Knoten mithilfe der Inhaltsmodellansicht

In diesem Thema wird das Untersuchen der Knoten mithilfe der [Inhaltsmodellansicht](../xml-tools/content-model-view.md) beschrieben.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>So erstellen Sie eine neue XSD-Datei und zeigen Sie das Stammelement in der Inhaltsmodellansicht an

1. Erstellen Sie eine neue XML-Schemadatei.

2. Klicken Sie in der Ausgangsansicht auf **Verwenden Sie den XML-Editor, um die zugrunde liegende XML-Schemadatei anzuzeigen und zu bearbeiten**.

3. Kopieren Sie den XML-Beispielschemacode aus [XML-Beispielschema: Bestellungsschema](../xml-tools/sample-xsd-file-purchase-order-schema.md), und fügen Sie ihn ein, um den Standardcode zu ersetzen, der der neuen XSD-Datei hinzugefügt wurde.

4. Wählen Sie im Schema-Explorer das `purchaseOrder`-Element aus, indem Sie im XML-Editor mit der rechten Maustaste auf das `purchaseOrder`-Element klicken und **In XML-Schema-Explorer anzeigen** auswählen.

5. Klicken Sie im XML-Explorer mit der rechten Maustaste auf `purchaseOrder`, und wählen Sie **In Inhaltsmodellansicht anzeigen** aus.

     Das `purchaseOrder`-Element wird auf der Entwurfsoberfläche der Inhaltsmodellansicht angezeigt.

6. Erweitern Sie die Knoten `shipTo`, `billTo` und `items`, indem Sie auf jeden Knoten doppelklicken oder auf den Doppelpfeil rechts neben jedem Knoten klicken.

     Die Knoten des `purchaseOrder`-Elements werden jetzt erweitert, und Sie können das Inhaltsmodell des Elements sehen.

7. Klicken Sie auf einen Knoten unter dem `purchaseOrder`-Element, und überprüfen Sie in der Breadcrumb-Leiste, wo sich der ausgewählte Knoten im Schemaset befindet.

8. Klicken Sie auf der XSD-Symbolleiste auf die Schaltfläche **Dokumentation anzeigen**, um die Dokumentation ein- oder auszublenden. Die Dokumentation kann auch über das Kontextmenü der Entwurfsoberfläche ein- und ausgeblendet werden.

9. Klicken Sie mit der rechten Maustaste auf den Knoten `purchaseOrder`, und wählen Sie **Beispiel-XML generieren** aus, um das XML-Instanzdokument anzuzeigen.
