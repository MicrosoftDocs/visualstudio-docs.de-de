---
title: Scrollleisten-Zuordnungsmodus und -Leistenmodus
description: Erfahren Sie, wie Sie Änderungen in Ihrem Code durch die Anpassung der Scrollleiste nachverfolgen, und wie Sie den Leisten- und Zuordnungsmodus verwenden können.
ms.custom: SEO-VS-2020
ms.date: 03/20/2020
ms.topic: how-to
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c59ac152be9528ef3e01410f0a3b5f34dd882286
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596936"
---
# <a name="how-to-customize-the-scroll-bar"></a>Vorgehensweise: Anpassen der Scrollleiste

Wenn Sie mit umfangreichen Codedateien arbeiten, kann es schwierig sein, den Überblick zu behalten, wo sich die einzelnen Elemente in der Datei befinden. Sie können die Scrollleiste des Code-Editors anpassen, um sich ein Gesamtbild davon zu machen, was in Ihrem Code geschieht.

## <a name="annotations"></a>Anmerkungen

Sie können auswählen, ob die Scrollleiste Anmerkungen wie Codeänderungen, Haltepunkte, Lesezeichen, Fehler und die Position der Einfügemarke anzeigt.

   1. Öffnen Sie die Optionsseite **Scrollleisten**, indem Sie **Extras** > **Optionen** > **Text-Editor** > **Alle Sprachen** > **Scrollleisten** auswählen.

   2. Wählen Sie **Anmerkungen über vertikaler Bildlaufleiste anzeigen** aus, und klicken Sie dann auf die Anmerkungen, die angezeigt werden sollen. Die verfügbaren Anmerkungen sind:

      - Änderungen
      - Markierungen
      - Fehler
      - Position der Einfügemarke

      > [!TIP]
      > Die Option **Markierungen anzeigen** umfasst Haltepunkte und Lesezeichen.

Probieren Sie es aus, indem Sie eine umfangreiche Codedatei öffnen und Text ersetzen, der an mehreren Stellen in der Datei vorkommt. Die Bildlaufleiste zeigt die Auswirkungen der Ersetzungen an. Sie können also Änderungen rückgängig machen, wenn ein Element nicht ersetzt werden soll.

So sieht die Bildlaufleiste aus, nachdem eine Zeichenfolge gesucht wurde. Beachten Sie, dass alle Instanzen der Zeichenfolge in der Scrollleiste angezeigt werden.

![Visual Studio-Scrollleiste nach der Suche nach einer Zeichenfolge](../ide/media/enhancedscrollbarsearch.png)

So sieht die Bildlaufleiste aus, nachdem alle Instanzen der Zeichenfolge ersetzt wurden. Die roten Markierungen in die Scrollleiste zeigen an, wo durch die Textersetzung Fehler aufgetreten sind.

![Visual Studio-Scrollleiste mit Fehlern nach dem Ersetzen einer Zeichenfolge](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>Anzeigemodi

Die Scrollleiste verfügt über zwei Modi: den Leistenmodus und den Zuordnungsmodus.

### <a name="bar-mode"></a>Leistenmodus

Im *Leistenmodus* werden Anmerkungsindikatoren auf der Scrollleiste angezeigt. Wenn Sie auf die Scrollleiste klicken, wird die Seite nach oben oder unten gescrollt, der Cursor springt aber nicht an die entsprechende Stelle in der Datei.

### <a name="map-mode"></a>Zuordnungsmodus

Im *Zuordnungsmodus* werden Codezeilen klein auf der Scrollleiste angezeigt. Sie können auswählen, wie breit die Zuordnungsspalte ist, indem Sie einen Wert in **Quellübersicht** auswählen. Um eine größere Vorschau des Codes zu aktivieren, wenn Sie den Mauszeiger auf der Zuordnung positionieren, wählen Sie die Option **Vorschau-QuickInfo anzeigen** aus. Zugeklappte Bereiche werden anders schattiert und durch einen Doppelklick aufgeklappt.

> [!TIP]
> Sie können die Miniaturcodeansicht im Zuordnungsmodus deaktivieren, indem Sie **Quellübersicht** auf **Aus** festlegen. Wenn **Vorschau-QuickInfo anzeigen** ausgewählt ist, sehen Sie immer noch eine Vorschau des Codes an dieser Stelle, wenn Sie den Mauszeiger auf der Scrollleiste positionieren, und der Mauszeiger springt immer noch zu dieser Stelle in der Datei, wenn Sie klicken.

Die folgende Abbildung zeigt das Suchbeispiel, wenn der Zuordnungsmodus aktiviert und die Breite auf **Mittel** festgelegt ist:

![Visual Studio-Scrollleiste im Zuordnungsmodus](../ide/media/enhancedscrollbar.png)

Die folgende Abbildung zeigt die Option **Vorschau-QuickInfo anzeigen**:

![Visual Studio-Scrollleiste mit QuickInfo](../ide/media/enhancedscrollbarsearchtooltip.png)

> [!TIP]
> Sie können die Farben im Zuordnungsmodus ändern, indem Sie auf **Extras** > **Optionen** > **Umgebung** > **Schriftarten und Farben** klicken. Wählen Sie als Nächstes unter **Elemente anzeigen** eines der Elemente aus, denen „Overview“ (Übersicht) vorangestellt ist, und nehmen Sie die gewünschten Farbänderungen vor. Klicken Sie dann auf **OK**.

## <a name="see-also"></a>Siehe auch

- [Features des Code-Editors](../ide/writing-code-in-the-code-and-text-editor.md)
