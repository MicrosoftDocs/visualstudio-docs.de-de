---
title: Diagrammansicht im XML-Schema-Designer
description: Erfahren Sie mehr über die Diagrammansicht im XML-Schema-Designer, die eine grafische Darstellung der globalen Schemaknoten und der Beziehungen zwischen den Knoten bereitstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 39a988ed4742f34fa2a3e6e2680d5eec8ccd2b07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879305"
---
# <a name="graph-view"></a>Diagrammansicht

Die Diagrammansicht bietet eine grafische Darstellung der globalen Schemaknoten und der Beziehungen zwischen den Knoten. In der Diagrammansicht kann das Layout des Schemasets auf der Entwurfsoberfläche nicht geändert werden. Die Diagrammansicht enthält auch die Symbolleiste des XML-Schema-Designers und die Breadcrumb-Leiste.

Das folgende Bild zeigt die Diagrammansicht mit sechs globalen Knoten auf der Entwurfsoberfläche.

![Diagrammansicht im XML-Schema-Designer](../xml-tools/media/xsddesigner_graphview.gif)

## <a name="design-surface"></a>Entwurfsoberfläche

Auf der Entwurfsoberfläche der Diagrammansicht wird der Inhalt des [Arbeitsbereichs des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md) angezeigt. Wenn der Arbeitsbereich globale Knoten aus dem Schemaset enthält, werden die Knoten auf der Entwurfsoberfläche der Diagrammansicht angezeigt, und zwischen Knoten mit Beziehungen werden Pfeile gezeichnet.

Per Doppelklick auf einen Knoten in der Diagrammansicht öffnen Sie den XML-Editor.

Verwenden Sie die XSD-Designer-Symbolleiste oder die **ENTF**-TASTE, um ausgewählte Knoten aus dem Arbeitsbereich zu löschen.

Wenn die Entwurfsoberfläche leer ist, werden der XML-Editor, der **XML-Schema-Explorer** und das Wasserzeichen angezeigt. Das *Wasserzeichen* ist eine Liste von Links zu allen Ansichten des XSD-Designers.

![XSD-Designer, Diagrammansicht](../xml-tools/media/xsdgraphviewwatermark.gif)

Wenn das Schemaset Fehler enthält, wird der folgende Text am Ende der Liste angezeigt:  „Verwenden Sie die Fehlerliste, um die Fehler im Schemaset anzuzeigen und zu beheben.“

## <a name="breadcrumb-bar"></a>Breadcrumb-Leiste

Die Breadcrumb-Leiste am unteren Rand der Diagrammansicht zeigt an, wo sich der ausgewählte Knoten im Schemaset befindet. Wenn mehrere Elemente ausgewählt sind, ist die Breadcrumb-Leiste leer.

## <a name="context-right-click-menu"></a>Kontextmenü (Rechtsklick)

In der folgenden Tabelle werden die Optionen beschrieben, die für alle Knoten auf der Entwurfsoberfläche der Diagrammansicht verfügbar sind.

|Option|Beschreibung|
|-|-----------------|
|**In XML-Schema-Explorer anzeigen**|Legt den Fokus auf den Schema-Explorer und hebt den Schemasetknoten hervor.|
|**In Diagrammansicht anzeigen**|Wechselt zur Diagrammansicht (abgeblendet).|
|**Beispiel-XML generieren**|Ist nur für globale Elemente verfügbar. Generiert eine Beispiel-XML-Datei für das globale Element.|
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Diagramm als Bild exportier**|Speichert die Entwurfsoberfläche in einer XPS-Datei.|
|**Alles markieren**|Wählt alle Knoten auf der Entwurfsoberfläche aus.|
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML-Editor. Das im **XML-Schema-Explorer** ausgewählte Element wird auch im XML-Editor ausgewählt.|
|**Eigenschaftenfenster**|Öffnet das Fenster **Eigenschaften** (sofern es noch nicht geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|

Neben den oben beschriebenen allgemeinen Optionen enthält das Kontextmenü für globale Elemente die folgenden Optionen:

|Option|Beschreibung|
|-|-----------------|
|**Typdefinition hinzufügen**|Fügt dem Diagramm den Basistyp hinzu.|
|**Alle Verweise hinzufügen**|Fügt alle Knoten, die auf das Element verweisen, hinzu und zeichnet Pfeile, um die Beziehungen anzugeben.|
|**Ersetzungsgruppenmitglieder hinzufügen**|Fügt alle Ersetzungsgruppenelemente hinzu. Diese Option wird in der Ansicht angezeigt, wenn das Element der Kopf oder das Mitglied einer Ersetzungsgruppe ist.|
|**Beispiel-XML generieren**|Generiert eine Beispiel-XML-Datei für das globale Element.|

Neben den oben beschriebenen allgemeinen Optionen enthält das Kontextmenü für globale einfache und globale komplexe Typen die folgenden Optionen:

|Option|Beschreibung|
|-|-----------------|
|**Basistyp hinzufügen**|Fügt den Basistyp des ausgewählten Typs hinzu, wenn der ausgewählte Typ von einem globalen Typ abgeleitet ist.|
|**Alle Verweise hinzufügen**|Fügt alle Verweise des ausgewählten Typs hinzu. Dazu zählen Elemente und Attribute des ausgewählten Typs und vom ausgewählten Typ abgeleitete Typen.|
|**Alle abgeleiteten Typen hinzufügen**|Fügt alle Typen hinzu, die direkt und indirekt vom ausgewählten Typ abgeleitet sind.|
|**Alle Vorgänger hinzufügen**|Fügt alle übergeordneten (Basis-)Typen hinzu.|

Neben den oben beschriebenen allgemeinen Optionen enthält das Kontextmenü für globale Gruppen und Attributgruppen die folgenden Optionen:

|Option|Beschreibung|
|-|-----------------|
|**Alle Verweise hinzufügen**|Fügt alle Knoten, die auf die Gruppe verweisen, hinzu und zeichnet Pfeile, um die Beziehungen anzugeben.|
|**Alle Mitglieder hinzufügen**|Fügt alle Mitglieder der Gruppe hinzu und zeichnet Pfeile, um die Beziehungen anzugeben.|

Neben den oben beschriebenen allgemeinen Optionen enthält das Kontextmenü für globale Attribute die folgenden Optionen:

|Option|Beschreibung|
|-|-----------------|
|**Alle Verweise hinzufügen**|Fügt alle Knoten, die auf die Gruppe verweisen, hinzu und zeichnet Pfeile, um die Beziehungen anzugeben.|

## <a name="properties-window"></a>Eigenschaftenfenster

Verwenden Sie das Kontextmenü (Rechtsklick), um das Fenster **Eigenschaften** zu Beginn zu öffnen. Das Fenster **Eigenschaften** wird standardmäßig in der rechten unteren Ecke von Visual Studio angezeigt. Wenn Sie auf einen in der Inhaltsmodellansicht gerenderten Knoten klicken, werden die Eigenschaften dieses Knotens im Fenster **Eigenschaften** angezeigt.

## <a name="xsd-toolbar"></a>XSD-Symbolleiste

Die folgenden XSD-Symbolleistenschaltflächen sind aktiviert, wenn die Diagrammansicht aktiv ist.

![Symbolleiste für XML-Schema-Designer](../xml-tools/media/xsdgraphviewtoolbar.gif)

|Option|Beschreibung|
|-|-----------------|
|**Ausgangsansicht anzeigen**|Wechselt zur [Ausgangsansicht](../xml-tools/start-view.md). Auf diese Ansicht können Sie auch mit der Tastenkombination zugreifen: **STRG**+**1**.|
|**Inhaltsmodellansicht anzeigen**|Wechselt zur [Inhaltsmodellansicht](../xml-tools/content-model-view.md). Auf diese Ansicht können Sie auch mit der Tastenkombination zugreifen: **STRG**+**2**.|
|**Diagrammansicht anzeigen**|Wechselt zur [Diagrammansicht](../xml-tools/graph-view.md). Auf diese Ansicht können Sie auch mit der Tastenkombination zugreifen: **STRG**+**3**.|
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche. Diese Option ist in der Inhaltsmodellansicht und der Diagrammansicht aktiviert.|
|**Von links nach rechts**|Ändert das Layout in der Diagrammansicht in eine von links nach rechts angeordnete hierarchische Darstellung der Knoten. Auf diese Option können Sie auch mit der Tastenkombination zugreifen: **ALT**+**NACH-RECHTS-TASTE**.|
|**Von rechts nach links**|Ändert das Layout in der Diagrammansicht in eine von rechts nach links angeordnete hierarchische Darstellung der Knoten. Auf diese Option können Sie auch mit der Tastenkombination zugreifen: **ALT**+**NACH-LINKS-TASTE**.|
|**Von oben nach unten**|Ändert das Layout in der Diagrammansicht in eine von oben nach unten angeordnete hierarchische Darstellung der Knoten. Auf diese Option können Sie auch mit der Tastenkombination zugreifen: **ALT**+**NACH-UNTEN-TASTE**.|
|**Von unten nach oben**|Ändert das Layout in der Diagrammansicht in eine von unten nach oben angeordnete hierarchische Darstellung der Knoten. Auf diese Option können Sie auch mit der Tastenkombination zugreifen: **ALT**+**NACH-OBEN-TASTE**.|

## <a name="panscroll"></a>Schwenken/Bildlauf

Sie können die Entwurfsoberfläche mit den Bildlaufleisten oder durch Drücken der **STRG**-TASTE und gleichzeitiges Klicken und Ziehen der Maus schwenken. Wenn Sie die Entwurfsoberfläche mittels Klicken und Ziehen schwenken, wird der Cursor als vier sich kreuzende und in unterschiedliche Richtungen weisende Pfeile angezeigt.

## <a name="undoredo"></a>Rückgängig/Wiederholen

Die Funktion zum Rückgängigmachen bzw. Wiederholen ist in der Diagrammansicht für folgende Aktionen aktiviert:

- Hinzufügen eines einzelnen Knotens per Drag &amp; Drop

- Hinzufügen mehrerer Knoten aus dem Suchergebnisfenster im Schema-Explorer oder Abfragen in der Ausgangsansicht

- Löschen einzelner oder mehrerer Knoten

## <a name="zoom"></a>Zoom

Die Zoomfunktion befindet sich in der unteren rechten Ecke der Diagrammansicht.

Der Zoomfaktor kann wie folgt gesteuert werden:

- Halten Sie die **STRG**-TASTE gedrückt, und drehen Sie das Mausrad, während Sie die Maus über die Oberfläche der Diagrammansicht bewegen.

- Verwenden Sie das Schieberegler-Steuerelement. Auf dem Schieberegler wird der aktuelle Zoomfaktor angezeigt.

Der Zoomschieberegler ist nicht transparent, wenn Sie ihn auswählen, mit der Maus darauf zeigen oder mit der **STRG**-TASTE und dem Mausrad zoomen. Ansonsten ist er transparent.

## <a name="xml-editor-integration"></a>Integration des XML-Editors

Klicken Sie auf einen Knoten, und wählen Sie das Kontextmenüelement (Rechtsklick) „Code anzeigen“ aus, um zwischen der Diagrammansicht und dem XML-Editor hin- und herzuwechseln.

Wenn Sie im XML-Editor Änderungen am Schemaset vornehmen, werden die Änderungen in der Diagrammansicht synchronisiert. Weitere Informationen finden Sie unter [Integration in XML-Editor](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Siehe auch

- [Designoberfläche](../xml-tools/xml-schema-designer-workspace.md)
