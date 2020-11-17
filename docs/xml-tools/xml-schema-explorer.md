---
title: XML-Schema-Explorer
description: In diesem Artikel erfahren Sie mehr über die Features des XML-Schema-Explorers, der mit Visual Studio und dem XML-Editor integriert ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31edea44741249c5d75a53e291c766824dc3b8ea
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351296"
---
# <a name="xml-schema-explorer"></a>XML-Schema-Explorer

Der **XML-Schema-Explorer** ist in Microsoft Visual Studio und den XML-Editor integriert, um die Arbeit mit XSD-Schemas (XML-Schemadefinitionssprache) zu ermöglichen. Wenn Sie eine XML-Schemadatei öffnen, wird der Knoten **Schemaset** im **XML-Schema-Explorer** angezeigt. Alle enthaltenen, importierten oder neu definierten Schemas für die Zieldatei und alle Dateien, auf die durch eine `include`- oder `import`-Anweisung verwiesen wird, werden auch im **XML-Schema-Explorer** angezeigt.

Der **XML-Schema-Explorer** ermöglicht folgende Tätigkeiten:

- Abrufen einer kurzen Übersicht über das Schemaset.

- Durchsuchen und Navigieren in der Struktur.

- Durchführen von schlüsselwort- und schemaspezifischen Suchvorgängen. Weitere Informationen finden Sie unter [Durchsuchen des Schemasets](../xml-tools/searching-the-schema-set.md).

- Hinzufügen der Suchergebnisse zur Diagramm- oder Inhaltsmodellansicht

- Sortieren der Struktur nach Dokumentreihenfolge, Typ oder Namen. Weitere Informationen finden Sie unter [Sortieren, Filtern und Gruppieren](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

- Öffnen Sie den XML-Editor, und springen Sie zu Codepositionen in der XSD-Datei. Weitere Informationen finden Sie unter [Integration in XML-Editor](../xml-tools/integration-with-xml-editor.md).

- Generieren von Beispiel-XML für globale Elemente.

Der **XML-Schema-Explorer** stellt mit einer Strukturansicht eine hierarchische Ansicht des Schemasets bereit. Der **XML-Schema-Explorer** stellt auch Funktionen zu Suche, Filterung, Navigation und Sortierung bereit. Führen Sie einen der folgenden Schritte aus, um auf den **XML-Schema-Explorer** zuzugreifen:

- Wenn Sie sich in der [Ausgangsansicht](../xml-tools/start-view.md) befinden, klicken Sie auf den Link **XML-Schema-Explorer**.

- Wenn Sie sich in der [Diagrammansicht](../xml-tools/graph-view.md) oder [Inhaltsmodellansicht](../xml-tools/content-model-view.md) befinden und Knoten in Ihrem Arbeitsbereich haben, verwenden Sie das Kontextmenü (rechts klicken), um den **XML-Schema-Explorer** auszuwählen.

- Sie können den **XML-Schema-Explorer** auch im Menü **Ansicht** auswählen.

- Sie können über eine *VB*-Datei mit einem Visual Basic-XML-Literal, das einer *XSD*-Datei zugeordnet ist, auf den **XML-Schema-Explorer** zugreifen. Klicken Sie mit der rechten Maustaste auf einen XML-Knoten in einem XML-Literal oder einem XML-Namespaceimport, und wählen Sie den Befehl **In XML-Schema-Explorer anzeigen** aus, um das Schemaset im **XML-Schema-Explorer** anzuzeigen. Weitere Informationen finden Sie unter [Integration von XML-Literalen in den XML-Schema-Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Strukturansicht
Der **XML-Schema-Explorer** zeigt vorkompilierte Schemasetinformationen in einer Struktur an. Die Struktur ist wie folgt aufgebaut:

- Auf oberster Ebene befindet sich der Schemasetknoten.

- Die zweite Ebene enthält die Namespaces.

- Die dritte Ebene enthält die Dateien.

- Die vierte Ebene enthält die globalen Knoten. Dazu können Elemente, Gruppen, komplexe Typen, einfache Typen, Attribute, Attributgruppen und `include`-, `import`- und `redefine`-Anweisungen gehören.

Im Folgenden Sie ein Beispiel für eine Struktur:

![XML-Schema-Explorer](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Auswahl und Aktivierung
Klicken Sie im Schema-Explorer einmal auf einen Knoten, um ihn hervorzuheben und auszuwählen.

Doppelklicken Sie auf einen Knoten, oder markieren Sie einen Knoten und drücken Sie die **EINGABETASTE**, um einen Knoten zu aktivieren.

- Durch das Aktivieren eines Knotens wird die Datei, in der dieser Knoten definiert ist, geöffnet (wenn sie nicht bereits geöffnet ist), und der Knoten wird in der Datei ausgewählt.

- Durch das Aktivieren eines Dateiknotens wird die ausgewählte Datei geöffnet (wenn sie nicht bereits geöffnet ist), und der Knoten `<schema>` wird hervorgehoben.

- Beim Aktivieren eines Schemaset- oder Namespaceknotens geschieht nichts.

## <a name="drag-and-drop-nodes"></a>Drag & Drop mit Knoten
Sie können globale Knoten, Dateiknoten und Namespaceknoten per Drag &amp; Drop in einer XSD-Designer-Ansicht ablegen. Wenn die aktuelle Ansicht die [Ausgangsansicht](../xml-tools/start-view.md) ist, wird die [Diagrammansicht](../xml-tools/graph-view.md) geöffnet, wenn Sie einen Knoten in die Ansicht ziehen. Wenn die aktuelle Ansicht die [Inhaltsmodellansicht](../xml-tools/content-model-view.md) oder die „Diagrammansicht“ ist, ändert sich die Ansicht nicht, wenn Sie einen Knoten in der Ansicht ablegen.

Wenn Sie eine Datei in der Ansicht ablegen, werden alle globalen Knoten in der Datei dem [Arbeitsbereich des XSD-Designers](../xml-tools/xml-schema-designer-workspace.md) hinzugefügt. Wenn Sie Namespaces in der Ansicht ablegen, werden dem Arbeitsbereich alle globalen Knoten im Namespace hinzugefügt. Der Arbeitsbereich wird für alle Ansichten verwendet.

 Lokale Knoten oder Importe können nicht per Drag &amp; Drop verschoben werden.

## <a name="see-also"></a>Siehe auch

- [How to: Hinzufügen von Knoten aus dem XML-Schema-Explorer zum Arbeitsbereich](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
