---
title: Inhaltsmodellansicht im XML-Schema-Designer
description: Erfahren Sie mehr über die Inhaltsmodellansicht im XAML-Schema-Designer, die eine grafische Darstellung lokaler und globaler Schemaknoten und ihrer Komponenten bereitstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05db6f02f2d00a5c0aca1ff91e15c61cf6bf8d4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948595"
---
# <a name="content-model-view"></a>Inhaltsmodellansicht

Die Inhaltsmodellansicht bietet eine grafische Darstellung lokaler und globaler Schemaknoten und ihrer Komponenten. Dazu zählen einfache und komplexe Typen, Elemente, Modellgruppen, Attribute und Attributgruppen. XML-Kommentare und -Verarbeitungsanweisungen können nicht in der Inhaltsmodellansicht angezeigt werden. Die Inhaltsmodellansicht enthält zwei Bereiche: einen **Arbeitsbereich** mit einer Liste der Knoten im [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md) und die Entwurfsoberfläche, auf der das Inhaltsmodell der im **Arbeitsbereich** ausgewählten Schemaknoten angezeigt wird. Die Inhaltsmodellansicht enthält auch die Symbolleiste des XML-Schema-Designers und die Breadcrumb-Leiste.

Das folgende Bild zeigt den **Arbeitsbereich** mit sechs Schemaknoten. Der `purchaseOrder`-Knoten ist im **Arbeitsbereich** ausgewählt und wird auf der Entwurfsoberfläche angezeigt.

![Inhaltsmodellansicht im XML-Schema-Designer](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Arbeitsbereich

Nachdem Sie dem Arbeitsbereich Knoten hinzugefügt haben, wird die Liste der Knoten im **Arbeitsbereich** der Inhaltsmodellansicht angezeigt. Wenn Sie im **Arbeitsbereich** Knoten auswählen, werden sie auf der Entwurfsoberfläche der Inhaltsmodellansicht angezeigt. Verwenden Sie die XSD-Designer-Symbolleiste, das Kontextmenü des **Arbeitsbereichs** oder die **ENTF**-TASTE, um Knoten aus dem Arbeitsbereich zu löschen.

Informationen zum Hinzufügen von Knoten finden Sie im Abschnitt „Hinzufügen von Knoten zum Arbeitsbereich“ unter [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Entwurfsoberfläche

Wenn Sie einen Knoten im **Arbeitsbereich** auswählen, wird er der Entwurfsoberfläche der Inhaltsmodellansicht hinzugefügt, wo Sie die Details des Knotens anzeigen können.

Das Inhaltsmodell eines Knotens wird durch eine erweiterbare grafische Struktur mit Elementen und Attributen als Strukturknoten dargestellt. Standardmäßig wird nur eine Ebene erweitert. Weitere Informationen wie Compositors, Typnamen, Gruppen und andere Container werden (bei erweiterter Struktur) auf einer vertikalen Leiste neben den zugehörigen Elementen und Attributen angezeigt. Wenn Sie auf einen vertikalen Balken doppelklicken, wird er horizontal dargestellt, und die Struktur wird reduziert. Wenn Sie auf einen horizontalen Balken doppelklicken, wird er vertikal dargestellt, und die Struktur wird erweitert. Durch Auswahl des vertikalen Balkens werden alle Knoten im Container ausgewählt. Rechts neben einem Knoten werden Erweiterungsschaltflächen angezeigt, wenn ein Element erweitert oder reduziert werden kann.

Wenn die Entwurfsoberfläche leer ist, werden der XML-Editor, der **XML-Schema-Explorer** und das Wasserzeichen angezeigt. Das *Wasserzeichen* ist eine Liste von Links zu allen Ansichten des XSD-Designers. Wenn das Schemaset Fehler enthält, wird der folgende Text am Ende der Liste angezeigt:  „Verwenden Sie die Fehlerliste, um die Fehler im Schemaset anzuzeigen und zu beheben.“

## <a name="breadcrumb-bar"></a>Breadcrumb-Leiste

Die Breadcrumb-Leiste am unteren Rand der Inhaltsmodellansicht zeigt an, wo sich der ausgewählte Knoten im Schemaset befindet.

## <a name="context-menus"></a>Kontextmenüs

Wenn Sie auf der Entwurfsoberfläche oder im **Arbeitsbereich** mit der rechten Maustaste auf ein Element klicken, wird ein Kontextmenü angezeigt. In der folgenden Tabelle werden die Optionen beschrieben, die für die Entwurfsoberfläche der Inhaltsmodellansicht verfügbar sind.

|Option|Beschreibung|
|-|-----------------|
|**In XML-Schema-Explorer anzeigen**|Legt den Fokus auf den Schema-Explorer und hebt den Schemasetknoten hervor.|
|**In Diagrammansicht anzeigen**|Wechselt zur Diagrammansicht.|
|**Beispiel-XML generieren**|Ist nur für globale Elemente verfügbar. Generiert eine Beispiel-XML-Datei für das globale Element.|
|**Dokumentation anzeigen**|Blendet den Inhalt von Anmerkungs-/Dokumentationsknoten ein bzw. aus.|
|**Diagramm als Bild exportier**|Speichert die Entwurfsoberfläche in einer XPS-Datei.|
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML-Editor. Das im **XML-Schema-Explorer** ausgewählte Element wird auch im XML-Editor ausgewählt.|
|**Eigenschaftenfenster**|Öffnet das Fenster **Eigenschaften** (sofern es noch nicht geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|

In der folgenden Tabelle werden die Optionen beschrieben, die für den **Arbeitsbereich** verfügbar sind.

|Option|Beschreibung|
|-|-----------------|
|**In XML-Schema-Explorer anzeigen**|Legt den Fokus auf den Schema-Explorer und hebt den Schemasetknoten hervor.|
|**In Diagrammansicht anzeigen**|Wechselt zur Diagrammansicht.|
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Beispiel-XML generieren**|Ist nur für globale Elemente verfügbar. Generiert eine Beispiel-XML-Datei für das globale Element.|
|**Alles markieren**|Wählt alle Knoten im **Arbeitsbereich** aus.|
|**Code anzeigen**|Öffnet die Datei, die den ausgewählten Knoten enthält, im XML-Editor. Das im **XML-Schema-Explorer** ausgewählte Element wird auch im XML-Editor ausgewählt.|
|**Eigenschaftenfenster**|Öffnet das Fenster **Eigenschaften** (sofern es noch nicht geöffnet ist). In diesem Fenster werden Informationen zum Knoten angezeigt.|

## <a name="properties-window"></a>Eigenschaftenfenster

Verwenden Sie das Kontextmenü (Rechtsklick), um das Fenster **Eigenschaften** zu Beginn zu öffnen. Das Fenster **Eigenschaften** wird standardmäßig in der rechten unteren Ecke von Visual Studio angezeigt. Wenn Sie auf einen in der Inhaltsmodellansicht gerenderten Knoten klicken, werden die Eigenschaften dieses Knotens im Fenster **Eigenschaften** angezeigt.

## <a name="xsd-designer-toolbar"></a>XSD-Designer-Symbolleiste

Die folgenden XSD-Designer-Symbolleistenschaltflächen sind aktiviert, wenn die Inhaltsmodellansicht aktiv ist.

![Symbolleiste für XML-Schema-Designer](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Option|Beschreibung|
|-|-----------------|
|**Ausgangsansicht anzeigen**|Wechselt zur [Ausgangsansicht](../xml-tools/start-view.md). Auf diese Ansicht können Sie auch mit der Tastenkombination zugreifen: **STRG**+**1**.|
|**Inhaltsmodellansicht anzeigen**|Wechselt zur [Inhaltsmodellansicht](../xml-tools/content-model-view.md). Auf diese Ansicht können Sie auch mit der Tastenkombination zugreifen: **STRG**+**2**.|
|**Diagrammansicht anzeigen**|Wechselt zur [Diagrammansicht](../xml-tools/graph-view.md). Auf diese Ansicht können Sie auch mit der Tastenkombination zugreifen: **STRG**+**3**.|
|**Arbeitsbereich löschen**|Löscht den Arbeitsbereich und die Entwurfsoberfläche.|
|**Aus Arbeitsbereich entfernen**|Entfernt ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Alles außer Auswahl aus Arbeitsbereich entfernen**|Entfernt nicht ausgewählte Knoten aus dem Arbeitsbereich und der Entwurfsoberfläche.|
|**Dokumentation anzeigen**|Blendet den Inhalt von Anmerkungs-/Dokumentationsknoten ein bzw. aus.|

## <a name="panscroll"></a>Schwenken/Bildlauf

Sie können die Entwurfsoberfläche mit den Bildlaufleisten oder durch Drücken der **STRG**-TASTE und gleichzeitiges Klicken und Ziehen der Maus schwenken. Wenn Sie die Entwurfsoberfläche mittels Klicken und Ziehen schwenken, wird der Cursor als vier sich kreuzende und in unterschiedliche Richtungen weisende Pfeile angezeigt.

## <a name="undoredo"></a>Rückgängig/Wiederholen

Die Funktion zum Rückgängigmachen bzw. Wiederholen ist in der Inhaltsmodellansicht für folgende Aktionen aktiviert:

- Hinzufügen eines einzelnen Knotens per Drag &amp; Drop

- Hinzufügen mehrerer Knoten aus dem Suchergebnisfenster im Schema-Explorer

- Hinzufügen von Knoten aus der Ausgangsansicht

- Löschen einzelner oder mehrerer Knoten

## <a name="zoom"></a>Zoom

Die Zoomfunktion befindet sich in der unteren rechten Ecke der Inhaltsmodellansicht.

Der Zoomfaktor kann wie folgt gesteuert werden:

- Halten Sie die **STRG**-TASTE gedrückt, und drehen Sie das Mausrad, während Sie die Maus über die Oberfläche der Inhaltsmodellansicht bewegen.

- Verwenden Sie das Schieberegler-Steuerelement. Auf dem Schieberegler wird der aktuelle Zoomfaktor angezeigt.

Der Zoomschieberegler ist nicht transparent, wenn Sie ihn auswählen, mit der Maus darauf zeigen oder mit der **STRG**-TASTE und dem Mausrad zoomen. Ansonsten ist er transparent.

## <a name="xml-editor-integration"></a>Integration des XML-Editors

Sie können über das Kontextmenü (Rechtsklick) zwischen dem **XSD-Designer** und dem XML-Editor hin- und herwechseln.

Wenn Sie im XML-Editor Änderungen am Schemaset vornehmen, werden die Änderungen in der Inhaltsmodellansicht synchronisiert. Weitere Informationen finden Sie unter [Integration in XML-Editor](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Siehe auch

- [Arbeitsbereich des XML-Schema-Designers](../xml-tools/xml-schema-designer-workspace.md)
