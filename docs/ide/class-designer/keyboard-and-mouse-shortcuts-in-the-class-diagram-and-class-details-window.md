---
title: Tastenkombinationen und Mausaktionen für den Klassen-Designer
description: Lernen Sie, zusätzlich zur Maus die Tastatur zu verwenden, um im Klassen-Designer und im Fenster „Klassendetails“ Navigationsvorgänge auszuführen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.classdetails.window
helpviewer_keywords:
- class diagrams, keyboard shortcuts
- class diagrams, mouse shortcuts
ms.assetid: c12d8dac-9902-4fde-b721-2a8116da53b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c184a12474e2d7ff0b626547acaaf2a37d460c8e
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901101"
---
# <a name="keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window"></a>Tastenkombinationen und Mausaktionen im Klassendiagramm und im Fenster „Klassendetails“

Zusätzlich zur Maus können Sie die Tastatur verwenden, um im **Klassen-Designer** und im Fenster **Klassendetails** Navigationsvorgänge auszuführen.

## <a name="use-the-mouse-in-class-designer"></a>Verwenden der Maus im Klassen-Designer

Die folgenden Mausaktionen werden in Klassendiagrammen unterstützt:

|Mauskombination|Kontext|Beschreibung|
| - |-------------|-----------------|
|Doppelklicken|Shape-Elemente|Öffnet den Code-Editor.|
|Doppelklicken|Lollipop-Connector|Lollipop erweitern/reduzieren.|
|Doppelklicken|Lollipop-Connectorbezeichnung|Ruft den Befehl **Schnittstelle anzeigen** auf|
|Mausrad|Klassendiagramm|Vertikaler Bildlauf.|
|**UMSCHALT**+Mausrad|Klassendiagramm|Horizontaler Bildlauf.|
|**STRG**+Mausrad|Klassendiagramm|Zoomen|
|**STRG**+**UMSCHALT**+Klick|Klassendiagramm|Zoomen|

## <a name="use-the-mouse-in-the-class-details-window"></a>Verwenden der Maus im Fenster „Klassendetails“

Mit einer Maus können Sie die Darstellung des Fensters **Klassendetails** und der in ihm angezeigten Daten folgendermaßen ändern:

- Nach Klicken in einer bearbeitbaren Zelle können Sie den Inhalt dieser Zelle bearbeiten. Ihre Änderungen werden an allen Stellen übernommen, an denen diese Daten gespeichert sind oder angezeigt werden, somit auch im **Eigenschaftenfenster** und im Quellcode.

- Ein Klicken in eine beliebige Zelle einer Zeile bewirkt, dass im **Eigenschaftenfenster** die Eigenschaften für das Element angezeigt werden, das durch diese Zeile dargestellt wird.

- Um die Breite einer Spalte zu ändern, ziehen Sie die Begrenzung der rechten Seite der Spaltenüberschrift solange, bis die Spalte die von Ihnen gewünschte Breite hat.

- Sie können Depot- oder Eigenschaftsknoten erweitern oder reduzieren, indem Sie auf die Pfeilsymbole links neben der Zeile klicken.

- Das Fenster **Klassendetails** enthält mehrere Schaltflächen zum Erstellen neuer Member in der aktuellen Klasse sowie zum Navigieren zwischen den Depots der Member im Raster des Fensters **Klassendetails**.

## <a name="use-the-keyboard-in-class-designer"></a>Verwenden der Tastatur im Klassen-Designer

Die folgenden Tastaturaktionen werden in Klassendiagrammen unterstützt:

|Key|Kontext|Beschreibung|
|---------|-------------|-----------------|
|**Pfeiltasten**|In Typformen|Navigation im Strukturstil in Forminhalten (Umschließen einer Form wird unterstützt). Nach-links- und Nach-rechts-Taste erweitern/reduzieren das aktuelle Element, sofern es erweiterbar ist, und navigieren andernfalls zum übergeordneten Element (ausführliches Verhalten entsprechend Navigation in Strukturansicht).|
|**Pfeiltasten**|Formen der obersten Ebene|Verschieben von Formen im Diagramm.|
|**UMSCHALT**+**Pfeiltasten**|In Typformen|Erstellen einer fortlaufenden Auswahl, die aus Formelementen wie Member, geschachtelte Typen oder Depots besteht. Diese Tastenkombinationen unterstützen kein Umschließen.|
|**Home**|In Typformen|Navigiert zum Titel der Form der obersten Ebene.|
|**Home**|Formen der obersten Ebene|Navigiert zur ersten Form im Diagramm.|
|**ENDE**|In Typformen|Navigiert zum letzten sichtbaren Element in der Form.|
|**ENDE**|Formen der obersten Ebene|Navigiert zur letzten Form im Diagramm.|
|**UMSCHALT**+**POS1**|In Typform|Wählt Elemente innerhalb der Form aus, beginnend mit dem aktuellen Element und endend mit dem obersten Element in derselben Form.|
|**UMSCHALT**+**Ende**|In Typform|Identisch mit **UMSCHALT**+**POS1**, aber in Von-oben-nach-unten-Richtung.|
|**EINGABETASTE**|Alle Kontexte|Ruft die Standardaktion für die Form auf, die auch durch Doppelklicken verfügbar ist. In den meisten Fällen ist dies "Code anzeigen", aber für einige Elemente ist das unterschiedlich definiert (Lollipops, Depot-Header, Lollipop Bezeichnungen).|
|**+** und **-**|Alle Kontexte|Wenn das Element, das aktuell den Fokus hat, erweiterbar ist, wird es mit diesen Tasten erweitert oder reduziert.|
|**>**|Alle Kontexte|Bei einem Element mit untergeordneten Elementen wird hiermit das Element erweitert, wenn es reduziert ist, und zum ersten untergeordneten Element navigiert.|
|**<**|Alle Kontexte|Navigiert zum übergeordneten Element.|
|**Alt**+**UMSCHALT**+**L**|In und auf Typformen.|Navigiert zum Lollipop der aktuell ausgewählten Form (sofern vorhanden).|
|**Alt**+**UMSCHALT**+**B**|In und auf Typformen.|Wird die Basistypenliste auf der Typform angezeigt, und enthält die Liste mehrere Elemente, wird hiermit der Erweiterungszustand der Liste umgeschaltet (reduzieren/erweitern).|
|**Löschen**|Auf Typ- und Kommentarformen|Ruft den Befehl **Aus Diagramm entfernen** auf|
|**Löschen**|Auf irgendeinem anderen Element|Ruft den Befehl **Aus Code löschen** auf (Member, Parameter, Zuordnungen, Vererbung, Lollipop-Bezeichnungen)|
|**STRG**+**ENTF**|Alle Kontexte|Ruft den Befehl **Aus Code löschen** für die Auswahl auf|
|**TAB**|Alle Kontexte|Navigiert zum nächsten untergeordneten Element desselben übergeordneten Elements (unterstützt Umschließen).|
|**UMSCHALT**+**Tab**|Alle Kontexte|Navigiert zum vorhergehenden untergeordneten Element desselben übergeordneten Elements (unterstützt Umschließen).|
|**LEERTASTE**|Alle Kontexte|Schaltet die Auswahl für das aktuelle Element um.|

## <a name="use-the-keyboard-in-the-class-details-window"></a>Verwenden der Tastatur im Fenster „Klassendetails“

> [!NOTE]
> Die folgenden Tastenbindungen wurden gewählt, um speziell die Erfahrung des Eingebens von Code zu imitieren.

Verwenden Sie die folgenden Tasten, um im Fenster **Klassendetails** zu navigieren:

|Key|Ergebnis|
|-|-|
|**,** (Komma)|Wenn sich der Cursor in einer Parameterzeile befindet, wird der Cursor nach Eingabe eines Kommas in das "Name"-Feld des nächsten Parameters verschoben. Wenn der Cursor sich in der letzten Parameterzeile einer Methode befindet, wird er in das Feld \<add parameter> verschoben, das Sie verwenden können, um einen neuen Parameter zu erstellen.<br /><br /> Befindet sich der Cursor an einer anderen Stelle im Fenster **Klassendetails**, wird durch ein Eingeben eines Kommas ein tatsächliches Komma im aktuellen Feld hinzugefügt.|
|**;** (Semikolon) oder **)** (schließende Klammer)|Verschiebt den Cursor in das Feld „Name“ der nächsten Memberzeile im Raster des Fensters **Klassendetails**.|
|**TAB**|Verschiebt den Cursor in das nächste Feld, wobei zunächst ein Verschieben von links nach rechts und dann von oben nach unten erfolgt. Wird der Cursor aus einem Feld bewegt, in das Text eingegeben wurde, wird dieser Text vom Fenster **Klassendetails** verarbeitet und gespeichert, sofern er keine Fehler erzeugt.<br /><br /> Befindet sich der Cursor in einem leeren Feld wie \<add parameter>, bewirkt TAB, dass der Cursor in das erste Feld der nächsten Zeile verschoben wird.|
|**LEERTASTE**|Verschiebt den Cursor in das nächste Feld, wobei zunächst ein Verschieben von links nach rechts und dann von oben nach unten erfolgt. Befindet sich der Cursor in einem leeren Feld wie \<add parameter>, wird er in das erste Feld der nächsten Zeile verschoben. Beachten Sie, dass \<space> unmittelbar nach einem Komma ignoriert wird.<br /><br /> Befindet sich der Cursor im Feld "Zusammenfassung", wird durch Eingeben eines Leerzeichens ein Leerzeichen hinzugefügt.<br /><br /> Befindet sich der Cursor in der "Ausblenden"-Spalte einer Zeile, bewirkt ein Eingeben eines Leerzeichens, dass der Wert des Kontrollkästchen "Ausblenden" umgeschaltet wird.|
|**STRG**+**TAB**|Wechselt zu einem anderen Dokumentfenster. Beispielsweise können Sie aus dem Fenster **Klassendetails** in eine geöffnete Codedatei wechseln.|
|**ESC**|Wenn Sie begonnen haben, Text in ein Feld einzugeben, fungiert Drücken von ESC wie eine Rückgängig-Taste, sodass der Inhalt des Feldes auf seinen vorherigen Wert zurückgesetzt wird. Wenn das Fenster „Klassendetails“ den allgemeinen Fokus besitzt, aber keine bestimmte Zelle fokussiert wird, bewirkt ein Drücken von ESC, dass der Fokus aus dem Fenster **Klassendetails** verschoben wird.|
|**NACH-OBEN**- und **NACH-UNTEN-TASTE**|Mit diesen Tasten wird der Cursor vertikal von Zeile zu Zeile im Raster des Fensters **Klassendetails** verschoben.|
|**NACH-LINKS-TASTE**|Befindet sich der Cursor in der Spalte "Name", bewirkt ein Drücken der NACH-LINKS-TASTE, dass der aktuelle Knoten in der Hierarchie reduziert wird (falls er geöffnet ist).|
|**NACH-RECHTS-TASTE**|Befindet sich der Cursor in der Spalte „Name“, bewirkt ein Drücken der NACH-RECHTS-TASTE, dass der aktuelle Knoten in der Hierarchie erweitert wird (falls er reduziert ist).|

## <a name="see-also"></a>Siehe auch

- [Erstellen und Konfigurieren von Typmembern](creating-and-configuring-type-members.md)
- [Vorgehensweise: Ausschließliches Verwenden der Tastatur](../reference/how-to-use-the-keyboard-exclusively.md)
- [Standardtastenkombinationen in Visual Studio](../default-keyboard-shortcuts-in-visual-studio.md)
- [Tastenkombinationen in Blend](../../xaml-tools/keyboard-shortcuts-in-blend.md)
