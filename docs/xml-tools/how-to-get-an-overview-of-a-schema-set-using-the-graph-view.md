---
title: 'XML-Schema-Designer: Abrufen einer Schemasetübersicht mithilfe der Diagrammansicht'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50813b37bf8f0fa7b3a8dbbb8fd38c101f6bbadf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817150"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Vorgehensweise: Abrufen einer Übersicht über ein Schemaset in der Diagrammansicht

In diesem Thema wird beschrieben, wie Sie mithilfe der [Diagrammansicht](../xml-tools/graph-view.md) eine allgemeine Ansicht der Knoten in einem Schemaset und der Beziehungen zwischen den Knoten anzeigen.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>So erstellen Sie eine neue XSD-Datei und zeigen Sie das Stammelement in der Inhaltsmodellansicht an

1. Erstellen Sie eine neue XML-Schemadatei, und speichern Sie die Datei unter dem Namen *Relationships.xsd*.

2. Klicken Sie in der Ausgangsansicht auf den Link **Verwenden Sie den XML-Editor, um die zugrunde liegende XML-Schemadatei anzuzeigen und zu bearbeiten**.

3. Kopieren Sie den XML-Schemabeispielcode aus [XML-Beispielschema: Beziehungen](../xml-tools/sample-xsd-file-relationships.md), und fügen Sie ihn ein, um den Standardcode zu ersetzen, der der neuen XSD-Datei hinzugefügt wurde.

4. Klicken Sie mit der rechten Maustaste an einer beliebigen Stelle im XML-Editor, und wählen Sie **Ansichts-Designer** aus.

5. Wählen Sie auf der **XSD-Symbolleiste** die Diagrammansicht aus.

6. Markieren Sie im **XML-Schema-Explorer** den Knoten **Schemaset**, und ziehen Sie den Knoten von der Entwurfsoberfläche in die Diagrammansicht. Nun sollten alle globalen Knoten und Verbindungspfeile zwischen den Knoten mit Beziehungen angezeigt werden.

     ![Diagrammansicht](../xml-tools/media/relationshipingraphview.gif)

7. Klicken Sie auf der Entwurfsoberfläche auf einen Knoten, und überprüfen Sie in der Breadcrumb-Leiste, wo sich der ausgewählte Knoten im Schemaset befindet.

8. Klicken Sie auf der Entwurfsoberfläche mit der rechten Maustaste auf einen Elementknoten, und wählen Sie **Beispiel-XML generieren** aus, um das XML-Instanzdokument anzuzeigen.
