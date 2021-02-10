---
title: Zuordnen von Methoden in der Aufrufliste beim Debuggen
description: Erfahren Sie, wie Sie eine Code Map erstellen, um die aufrufsstapel während des Debuggens visuell zu verfolgen. Außerdem erfahren Sie, wie Sie auf der Karte Notizen machen können, um zu verfolgen, wie der Code ausgeführt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7196cf06e7d6bcde33bc1e4a6c5d0ebfac486576
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946487"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Zuordnen von Methoden in der Aufrufliste beim Debuggen in Visual Studio

Erstellen Sie eine Code Map, um die Aufrufliste während des Debuggens visuell zu verfolgen. Sie können Notizen auf der Zuordnung vermerken, um das Verhalten des Codes zu verfolgen, sodass Sie sich auf das Suchen von Fehlern konzentrieren können.

 ![Debuggen mit Aufruflisten in Codezuordnungen](../debugger/media/debuggermap_overview.png)

 Sie benötigen Folgendes:

 ::: moniker range="vs-2017"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads)

::: moniker-end

- Code, den Sie Debuggen können, z. b. Visual c#, Visual Basic, C++, JavaScript oder X + +

  Thema

- [Video: visuelles Debuggen mit der Code Map Debugger-Integration (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

- [Zuordnen der aufrufsstapel](#MapStack)

- [Notieren Sie sich den Code.](#MakeNotes)

- [Aktualisieren der Zuordnung mit der nächsten aufrufsstapel](#UpdateMap)

- [Fügen Sie der Karte verknüpften Code hinzu.](#AddRelatedCode)

- [Suchen von Fehlern mithilfe der Zuordnung](#FindBugs)

- [Q & A](#QA)

  Ausführliche Informationen zu den Befehlen und Aktionen, die Sie beim Arbeiten mit Code Maps verwenden können, finden Sie unter [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md).

## <a name="map-the-call-stack"></a><a name="MapStack"></a> Abbilden der Aufrufliste

1. Beginnen Sie mit dem Debuggen. (Tastatur: **F5**)

2. Nachdem Ihre APP in den Unterbrechungs Modus wechselt oder Sie eine Funktion schrittweise ausführen, wählen Sie **Code Map** aus. (Tastatur: **STRG**  +  **UMSCHALT**  +  **`** )

     ![Code Map auswählen, um Aufruflistenzuordnung zu starten](../debugger/media/debuggermap_choosecodemap.png)

     Die aktuelle Aufrufliste wird in einer neuen Code Map orange dargestellt:

     ![Aufrufliste in Code Maps](../debugger/media/debuggermap_seeundocallstack.png)

     Die Map wird beim Debuggen automatisch aktualisiert. Weitere Informationen finden Sie unter [Aktualisieren der Zuordnung mit der nächsten-Rückruf Stapel](#UpdateMap).

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> Erstellen von Notizen zum Code

 Fügen Sie Kommentare hinzu, um zu verfolgen, was im Code geschieht. Um eine neue Zeile in einem Kommentar hinzuzufügen, drücken Sie **UMSCHALT + Return**.

 ![Kommentar zu Aufrufliste in Code Map hinzufügen](../debugger/media/debuggermap_addcomment.png)

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> Aktualisieren der Code Map mit der nächsten Aufrufliste

 Führen Sie die Anwendung bis zum nächsten Haltepunkt aus, oder führen Sie eine Funktion schrittweise aus. Die Zuordnung fügt eine neue Aufrufliste hinzu.

 ![Code Map mit nächster Aufrufliste aktualisieren](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> Hinzufügen von zugehörigem Code zur Code Map

 Nun haben Sie eine Karte: wie geht es weiter? Wenn Sie mit c# oder Visual Basic arbeiten, fügen Sie Elemente hinzu, z. b. Felder, Eigenschaften und andere Methoden, um zu verfolgen, was im Code geschieht.

 Doppelklicken Sie auf eine Methode, um ihre Codedefinition anzuzeigen, oder verwenden Sie das Kontextmenü für die Methode. (Tastatur: Wählen Sie die Methode auf der Karte aus, und drücken Sie **F12**.)

 ![Für eine Methode in der Codezuordnung zur Codedefinition wechseln](../debugger/media/debuggermap_gotocodedefinition.png)

 Fügen Sie die Elemente hinzu, die Sie in der Zuordnung nachverfolgen möchten.

 ![Felder anzeigen, die mit einer Methode in der Aufruflisten-Codezuordnung verknüpft sind](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
> Standardmäßig werden beim Hinzufügen von Elementen zur Zuordnung auch die übergeordnete Gruppenknoten, wie Klasse, Namespace und Assembly, hinzugefügt. Dies ist zwar hilfreich, Sie können die Zuordnung jedoch auch einfach halten, indem Sie diese Funktion mithilfe der Schaltfläche übergeordnete Elemente **einschließen** auf der Kartensymbol Leiste oder durch Drücken von **STRG** beim Hinzufügen von Elementen deaktivieren.

 ![Felder, die mit einer Methode in der Aufruflisten-Codezuordnung verknüpft sind](../debugger/media/debuggermap_showedfields.png)

 Hier können Sie leicht erkennen, welche Methoden die gleichen Felder verwenden. Die zuletzt hinzugefügten Elemente werden grün dargestellt.

 Setzen Sie das Erstellen der Zuordnung fort, um weiteren Code anzuzeigen.

 ![Methoden, die ein Feld verwenden: Aufruflisten-Code Map](../debugger/media/debuggermap_findallreferences.png)

 ![Methoden, die ein Feld für die Aufruflisten-Code Maps verwenden](../debugger/media/debuggermap_foundallreferences.png)

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> Suchen von Fehlern mithilfe der Code Map

 Durch die Visualisierung des Codes können Sie Fehler schneller finden. Nehmen wir beispielsweise an, dass Sie einen Fehler in einem Zeichnungsprogramm untersuchen. Wenn Sie eine Linie zeichnen und versuchen, sie rückgängig zu machen, geschieht nichts, bis Sie eine andere Zeile zeichnen.

 Legen Sie die Haltepunkte `clear`, `undo` und `Repaint` fest, starten Sie das Debugging, und erstellen Sie eine Zuordnung wie die folgende:

 ![Weitere Aufrufliste zu Codezuordnung hinzufügen](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 Sie stellen fest, dass alle Benutzergesten in der Zuordnung die `Repaint`-Funktion aufrufen, außer `undo`. Dies erklärt möglicherweise, warum `undo` nicht sofort funktioniert.

 Nachdem Sie den Fehler korrigiert haben und die Ausführung des Programms fortsetzen, fügt die Zuordnung den neuen Aufruf von `undo` zur `Repaint`-Funktion hinzu:

 ![Neuen Methodenaufruf zu Aufrufliste in Code Maps hinzufügen](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="q--a"></a><a name="QA"></a> Fragen und Antworten

- **Nicht alle Aufrufe werden auf der Karte angezeigt. Dafür?**

   Standardmäßig wird nur Ihr eigener Code in der Code Map angezeigt. Um externen Code anzuzeigen, aktivieren Sie ihn im Fenster " **aufrufsstapel** ":

   ![Anzeige von externem Code über das Fenster "Aufrufliste"](../debugger/media/debuggermap_callstackmenu.png)

   oder deaktivieren Sie **nur eigenen Code** in den Visual Studio-Debugoptionen:

   ![Anzeige von externem Code über das Dialogfeld "Optionen"](../debugger/media/debuggermap_debugoptions.png)

- **Wird der Code durch Ändern der Zuordnung beeinflusst?**

   Das Ändern der Zuordnung wirkt sich nicht auf den Code aus. Sie können beliebigen Code in der Zuordnung gerne umbenennen, verschieben oder entfernen.

- **Was bedeutet diese Meldung: "das Diagramm basiert möglicherweise auf einer älteren Version des Codes"?**

   Der Code wurde möglicherweise geändert, nachdem Sie die Zuordnung zuletzt aktualisiert haben. Zum Beispiel befindet sich möglicherweise ein Aufruf für die Zuordnung nicht mehr im Code. Schließen Sie die Meldung, und versuchen Sie dann, die Projektmappe vor der erneuten Aktualisierung der Zuordnung neu zu erstellen.

- **Gewusst wie das Layout der Karte Steuern?**

   Öffnen Sie das **Layoutmenü** auf der Kartensymbol Leiste:

  - Ändern Sie das Standardlayout.

  - Wenn Sie das erneute Anordnen der Zuordnung beenden möchten, deaktivieren Sie das **automatische Layout beim Debuggen**.

  - Deaktivieren Sie das **inkrementelle Layout**, um die Zuordnung so wenig wie möglich neu anzuordnen, wenn Sie Elemente hinzufügen.

- **Kann ich die Zuordnung für andere Benutzer freigeben?**

   Sie können die Zuordnung exportieren, an andere Benutzer senden, wenn Sie über Microsoft Outlook verfügen, oder Sie können Sie in der Projekt Mappe speichern, damit Sie Sie in die Quell Code Verwaltung einchecken können.

   ![Aufruflisten-Code Map für andere Benutzer freigeben](../debugger/media/debuggermap_sharewithothers.png)

- **Wie kann ich verhindern, dass die Zuordnung neue Aufruflisten automatisch hinzufügt?**

   Wählen Sie ![ Schalt &#45; Fläche aus, ](../debugger/media/debuggermap_automaticupdateicon.gif) um die Code Map in der Kartensymbol Leiste automatisch auf anzuzeigen. Drücken Sie **STRG** + **UMSCHALT** +  **`** , um die aktuelle Aufrufliste der Code Map manuell hinzuzufügen.

   Beim Debuggen werden vorhandene Aufruf Listen auf der Karte durch die Zuordnung hervorgehoben.

- **Was bedeuten die Elementsymbole und Pfeile?**

   Um weitere Informationen zu einem Element zu erhalten, bewegen Sie den Mauszeiger darüber, und sehen Sie sich die QuickInfo des Elements an. Sie können sich auch die **Legende** ansehen, um zu erfahren, was die einzelnen Symbole bedeuten.

   ![Was bedeuten die Symbole in der Aufruflisten-Codezuordnung?](../debugger/media/debuggermap_showlegend.png)

  Thema

- [Zuordnen der aufrufsstapel](#MapStack)

- [Notieren Sie sich den Code.](#MakeNotes)

- [Aktualisieren der Zuordnung mit der nächsten aufrufsstapel](#UpdateMap)

- [Fügen Sie der Karte verknüpften Code hinzu.](#AddRelatedCode)

- [Suchen von Fehlern mithilfe der Zuordnung](#FindBugs)

## <a name="see-also"></a>Siehe auch

- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)
- [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)
- [Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md)
