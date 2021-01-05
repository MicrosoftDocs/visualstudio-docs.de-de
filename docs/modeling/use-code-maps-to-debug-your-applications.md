---
title: Verwenden von Code Maps zum Debuggen von Anwendungen
description: Erfahren Sie, wie Sie Code Maps verwenden können, um zu vermeiden, dass Sie in großen Codebasen, in unbekanntem Code oder Legacy Code verloren gehen.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d935ee5c4341a2d625c6f85226cc649d696d6e6e
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729391"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Verwenden von Code Maps zum Debuggen von Anwendungen

Code Maps helfen Ihnen, die Übersicht in umfangreichen Codebasen, nicht vertrautem Code oder Legacycode zu behalten. Wenn Sie z. b. Debuggen, müssen Sie möglicherweise den Code über mehrere Dateien und Projekte hinweg betrachten. Mithilfe von Code Maps können Sie in Codeabschnitten navigieren und Beziehungen zwischen ihnen verstehen. Auf diese Weise müssen Sie die den Code nicht gedanklich nachvollziehen oder ein separates Diagramm zeichnen. Wenn Sie die Arbeit unterbrechen müssen, können Code Maps Ihnen helfen, sich den Code wieder ins Gedächtnis zu rufen, an dem Sie arbeiten.

![Code Map &#45; Zuordnungs Beziehungen im Code](../modeling/media/codemapstoryboardpaint.png)

**Ein grüner Pfeil zeigt an, wo der Cursor im Editor angezeigt wird.**

Ausführliche Informationen zu den Befehlen und Aktionen, die Sie beim Arbeiten mit Code Maps verwenden können, finden Sie unter [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md).

> [!NOTE]
> Zum Erstellen und Bearbeiten von Code Maps benötigen Sie Visual Studio Enterprise Edition. In den Editionen von Visual Studio Community und Professional können Sie Diagramme öffnen, die in der Enterprise Edition generiert wurden, Sie können Sie jedoch nicht bearbeiten.

## <a name="understand-the-problem"></a>Verstehen des Problems
 Nehmen Sie an, in einem Zeichenprogramm, an dem Sie arbeiten, liegt ein Fehler vor. Um den Fehler zu reproduzieren, öffnen Sie die Projekt Mappe in Visual Studio, und drücken Sie **F5** , um das Debugging zu starten.

 Wenn Sie eine Linie zeichnen und den **letzten Strich rückgängig** machen auswählen, geschieht nichts, bis Sie die nächste Zeile zeichnen.

 ![Code Map &#45; Repro-Fehler](../modeling/media/codemapstoryboardpaint0.png)

 Daher beginnen Sie mit der Untersuchung, indem Sie nach der `Undo`-Methode suchen. Sie finden diese in der `PaintCanvas`-Klasse.

 ![Code Map &#45; Code suchen](../modeling/media/codemapstoryboardpaint1.png)

## <a name="start-mapping-the-code"></a>Die Codezuordnung starten
 Nun beginnen Sie mit dem Mapping der `undo`-Methode und ihrer Beziehungen. Fügen Sie im Code-Editor die `undo`-Methode und die Felder, auf die sie verweist, zu einer neuen Code Map hinzu. Wenn Sie eine neue Zuordnung erstellen, kann es einige Zeit dauern, den Code zu indizieren. Aufgrund der Indizierung können spätere Vorgänge schneller ausgeführt werden.

 ![Code Map &#45; Methode und verwandte Felder anzeigen](../modeling/media/codemapstoryboardpaint3.png)

> [!TIP]
> Die letzten zur Zuordnung hinzugefügten Elemente werden grün hervorgehoben. Der grüne Pfeil zeigt die Position des Cursors im Code an. Pfeile zwischen Elementen stellen verschiedene Beziehungen dar. Weitere Informationen zu Elementen in der Map enthalten die entsprechenden QuickInfos. Fahren Sie zur Anzeige einfach mit dem Mauszeiger über das Element.

 ![Code Map &#45; anzeigen von Quick Infos](../modeling/media/codemapstoryboardpaint4.png)

## <a name="navigate-and-examine-code-from-the-map"></a>Code aus der Zuordnung navigieren und untersuchen
 Um die Code Definition für jedes Feld anzuzeigen, doppelklicken Sie auf das Feld auf der Karte, oder wählen Sie das Feld aus, und drücken Sie **F12**. Der grüne Pfeil wird zwischen den Elementen in der Zuordnung verschoben. Der Cursor im Code-Editor wird automatisch ebenfalls bewegt.

 ![Screenshot eines Code Map Fensters mit ausgewähltem Feld Verlauf und einem Code-Editor-Fenster, in dem alle Instanzen von History hervorgehoben sind.](../modeling/media/codemapstoryboardpaint5.png)

 ![Screenshot eines Code Map Fensters mit ausgewähltem Feld "paintobjects" und einem Code-Editor-Fenster, in dem alle Vorkommen von "maltobjects" markiert sind.](../modeling/media/codemapstoryboardpaint5a.png)

> [!TIP]
> Sie können den grünen Pfeil in der Zuordnung auch verschieben, indem Sie den Cursor im Code-Editor bewegen.

## <a name="understand-relationships-between-pieces-of-code"></a>Beziehungen zwischen Teilen des Codes verstehen
 Nun möchten Sie wissen, in welchem anderen Code die Felder `history` und `paintObjects` verwendet werden. Sie können der Zuordnung alle Methoden hinzufügen, die auf diese Felder verweisen. Dies kann von der Map oder vom Code-Editor aus erfolgen.

 ![Code Map &#45; alle Verweise suchen](../modeling/media/codemapstoryboardpaint6.png)

 ![Öffnen einer Codezuordnung aus dem Code-Editor](../modeling/media/codemapstoryboardpaint6a.png)

> [!NOTE]
> Wenn Sie Elemente aus einem Projekt hinzufügen, das von mehreren Apps wie Windows Phone oder Windows Store gemeinsam genutzt wird, werden diese Elemente immer mit dem derzeit aktiven App-Projekt in der Map angezeigt. Wenn Sie also den Kontext auf ein anderes App-Projekt ändern, ändert sich auch der Kontext auf der Map für alle neu hinzugefügte Elemente aus dem freigegebenen Projekt. Vorgänge, die Sie mit einem Element in der Zuordnung ausführen, gelten nur für solche Elemente, die denselben Kontext gemeinsam verwenden.

 Ändern Sie das Layout, um den Ablauf der Beziehungen neu anzuordnen und die Zuordnung besser lesbar zu machen. Sie können Elemente in der Zuordnung auch verschieben, indem Sie sie an andere Positionen ziehen.

 ![Screenshot eines Code Map Fensters, in dem das Layoutmenü geöffnet und der Befehl Left to rgiht ausgewählt ist.](../modeling/media/codemapstoryboardpaint7a.png)

> [!TIP]
> Das **inkrementelle Layout** ist standardmäßig aktiviert. Dadurch wird die Zuordnung so wenig wie möglich neu angeordnet, wenn Sie neue Elemente hinzufügen. Deaktivieren Sie das **inkrementelle Layout**, um die gesamte Zuordnung bei jedem Hinzufügen neuer Elemente neu anzuordnen.

 ![Screenshot eines Code Map Fensters mit den relationshiop-Pfeilen zwischen den Feldern, die von links nach rechts zeigen.](../modeling/media/codemapstoryboardpaint7.png)

 Überprüfen Sie diese Methoden. Doppelklicken Sie auf der Karte auf die **paintcanvas** -Methode, oder wählen Sie diese Methode aus, und drücken Sie **F12**. Sie erfahren, dass `history` und `paintObjects` von dieser Methode als leere Listen erstellt werden.

 ![Screenshot eines Code Map Fensters, in dem die Pinsel Methode ausgewählt ist, und ein Code Ausschnitt Bild, das den markierten Name der malcanvas-Methode anzeigt.](../modeling/media/codemapstoryboardpaint8.png)

 Wiederholen Sie nun die gleichen Schritte, um die Definition der `clear`-Methode zu überprüfen. Sie erfahren, dass in `clear` einige Aufgaben mit `paintObjects` und `history` ausgeführt werden. Anschließend wird die `Repaint`-Methode aufgerufen.

 ![Screenshot eines Code Map Fensters, bei dem die Clear-Methode ausgewählt ist, und ein Code Ausschnitt Bild, das den Code für die Clear-Methode anzeigt.](../modeling/media/codemapstoryboardpaint9.png)

 Überprüfen Sie nun die Definition der `addPaintObject`-Methode. Darin werden ebenfalls einige Aufgaben mit `history` und `paintObjects` ausgeführt. Auch darin wird `Repaint` aufgerufen.

 ![Screenshot eines Code Map Fensters mit ausgewählter addpaintobject-Methode und einem Code Ausschnitt Bild, das den Code für die addpaintobject-Methode anzeigt.](../modeling/media/codemapstoryboardpaint10.png)

## <a name="find-the-problem-by-examining-the-map"></a>Das Problem durch Prüfen der Zuordnung suchen
 Anscheinend wird von allen Methoden, die `history` und `paintObjects` ändern, `Repaint` aufgerufen. Von der `undo`-Methode wird `Repaint` jedoch nicht aufgerufen, obwohl von `undo` die gleichen Felder geändert werden. Daher denken Sie, dass Sie dieses Problem beheben können, indem Sie `Repaint` von `undo` aus aufrufen.

 ![Code Map &#45; fehlenden Methodenaufrufe suchen](../modeling/media/codemapstoryboardpaint11.png)

 Wenn Sie keine Zuordnung zur Verfügung gehabt hätten, in der dieser fehlende Aufruf angezeigt wird, wäre es möglicherweise schwieriger gewesen, dieses Problem zu finden, insbesondere bei komplexerem Code.

## <a name="share-your-discovery-and-next-steps"></a>Ergebnisse freigeben und nächste Schritte
 Bevor Sie oder jemand anderes diesen Fehler behebt, können Sie in der Zuordnung Notizen zu dem Problem und dessen Behebung erstellen.

 ![Code Map &#45; Kommentar und Markieren von Elementen für die Nachverfolgung](../modeling/media/codemapstoryboardpaint12.png)

 Sie können der Zuordnung beispielsweise Kommentare hinzufügen und Elemente mit Farben kennzeichnen.

 ![Code Map &#45; kommentierte und gekennzeichnete Elemente](../modeling/media/codemapstoryboardpaint12a.png)

 Wenn Microsoft Outlook installiert ist, können Sie die Zuordnung per E-Mail an andere senden. Sie können die Zuordnung auch als Bild oder in einem anderen Format exportieren.

 ![Code Map &#45; Freigabe, Export, e-Mail-Nachricht](../modeling/media/codemapstoryboardpaint13.png)

## <a name="fix-the-problem-and-show-what-you-did"></a>Das Problem beheben und zeigen, was Sie getan haben
 Fügen Sie den Aufruf von `Repaint` zu `undo` hinzu, um diesen Fehler zu beheben.

 ![Code Map &#45; fehlenden Methodenaufrufe hinzufügen](../modeling/media/codemapstoryboardpaint14.png)

 Starten Sie die Debugsitzung neu, und versuchen Sie, den Fehler zu reproduzieren, um sicherzustellen, dass der Fehler behoben ist. Die Auswahl des **letzten Strichs rückgängig** ist erwartungsgemäß und bestätigt, dass Sie die richtige Lösung vorgenommen haben.

 ![Code Map &#45; Code Korrektur bestätigen](../modeling/media/codemapstoryboardpaint15.png)

 Sie können die Zuordnung aktualisieren, damit die Ihre Korrektur angezeigt wird.

 ![Code Map &#45; Update Zuordnung mit fehlendem Methodenaufrufe](../modeling/media/codemapstoryboardpaint16.png)

 Ihre Karte zeigt nun einen Link zwischen " **Rückgängig** " und " **neu zeichnen**" an.

 ![Code Map &#45; aktualisierte Zuordnung mit Methoden aufzurufen.](../modeling/media/codemapstoryboardpaint17.png)

> [!NOTE]
> Wenn Sie die Zuordnung aktualisieren, wird möglicherweise eine Meldung angezeigt, die besagt, dass der zum Erstellen der Zuordnung verwendete Codeindex aktualisiert wurde. Dies bedeutet, dass jemand den Code geändert hat, was dazu führt, dass die Zuordnung nicht mit dem aktuellen Code übereinstimmt. Das hindert Sie nicht daran, die Zuordnung zu aktualisieren. Sie müssen jedoch möglicherweise die Zuordnung neu erstellen, um sicherzustellen, dass sie dem Code entspricht.

 Nun sind Sie mit der Untersuchung fertig. Sie haben das Problem gefunden und erfolgreich korrigiert, indem Sie den Code zugeordnet haben. Außerdem verfügen Sie über eine Zuordnung, anhand der Sie im Code navigieren, sich an das Gelernte erinnern und die Schritte zur Behebung des Problems anzeigen können.

## <a name="see-also"></a>Weitere Informationen

- [Zuordnen von Methoden in der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Visualisieren von Code](../modeling/visualize-code.md)
