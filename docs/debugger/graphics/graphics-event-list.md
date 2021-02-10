---
title: Grafikereignisliste | Microsoft-Dokumentation
description: Verwenden Sie die Grafikereignisliste in der Visual Studio-Grafikanalyse, um die Direct3D-Ereignisse zu untersuchen, die während des Renderings eines Frames Ihres Spiels oder Ihrer App aufgezeichnet wurden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c964cda5cbe2903cf9511659b9a8f9bfb9f4aad6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884519"
---
# <a name="graphics-event-list"></a>Grafikereignisliste
Verwenden Sie die Grafikereignisliste in der Visual Studio-Grafikanalyse, um die Direct3D-Ereignisse zu untersuchen, die während des Renderings eines Frames Ihres Spiels oder Ihrer App aufgezeichnet wurden.

 Dies ist die Ereignisliste:

 ![Eine Liste von Ereignissen mit „Index“ im Namen.](media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")

## <a name="using-the-event-list"></a>Verwenden der Ereignisliste
 Wenn Sie ein Ereignis in der Ereignisliste auswählen, wird dieses in den Informationen wiedergegeben, die von anderen Grafikanalysetools angezeigt werden. Wenn Sie die Ereignisliste in Verbindung mit diesen anderen Tools verwenden, können Sie ein eventuelles Renderingproblem detailliert untersuchen, um seine Ursache zu ermitteln. Mehr Informationen über die Lösung von Renderingproblemen durch Verwendung der Ereignisliste in Verbindung mit anderen Grafikanalysetools finden Sie unter [Beispiele](graphics-diagnostics-examples.md).

 Die Verwendung dieser Funktionen der Ereignisliste ist sehr wichtig für die Umgehung komplexer Frames, die Tausende von Ereignissen enthalten können. Wählen Sie die Ansicht, die für Ihre Arbeit am besten geeignet ist, um die Ereignisliste effektiv zu nutzen. Verwenden Sie die Suche, um die Ereignisliste zu filtern, folgen Sie Links, um mehr über die Direct3D-Objekte zu erfahren, die mit einem Ereignis verknüpft sind, und nutzen Sie die Pfeiltasten, um schnell zwischen den Zeichnen-Befehlen zu navigieren.

### <a name="color-coded-events-in-direct3d-12"></a>Farbcodierte Ereignisse in Direct3D 12
 Direct3D 12 stellt mehrere Warteschlangen zur Verfügung, die unterschiedlicher Hardwarefunktionalitäten entsprechen. Zur Identifizierung von mit einem bestimmen Grafikereignis in Direct3D 12 verknüpfter Warteschlange werden die Ereignisse entsprechend der zugehörigen Warteschlange in der Ereignisliste farblich gekennzeichnet, wenn Sie mit einer Dircet3D 12-App-Erfassung arbeiten.

|Direct3D 12-Warteschlange|Farbe|
|-----------------------|-----------|
|Rendern der Warteschlange|Grün|
|Berechnen der Warteschlange|Gelb|
|Kopieren der Warteschlange|Orange|

 In Direct3D 11 sind mehrere Warteschlangen nicht zulässig, sodass Ereignisse in der Ereignisliste nicht farblich gekennzeichnet werden, wenn Sie mit einer Direct3D 11-App-Erfassung arbeiten.

### <a name="event-list-views"></a>Ereignislistenansichten
 Die Ereignisliste bietet zwei verschiedene Ansichten zur Organisation von Grafikereignissen in verschiedener Weise, um Ihren Workflow und Ihre Präferenzen zu unterstützen. Die erste Ansicht ist die Ansicht *GPU-Arbeiten*, in der Ereignisse und ihre Status hierarchisch organisiert werden. Die zweite Ansicht ist die Ansicht *Zeitachse* , in der Ereignisse chronologisch in einer flachen Liste organisiert werden.

 In der Ansicht **GPU-Arbeiten** werden erfasste Ereignisse und ihr Status in der Hierarchie angezeigt. Die oberste Ebene der Hierarchie besteht aus Ereignissen wie Zeichnen-Befehlen, gelöschten und d vorhandenen Ereignissen und solchen, die mit Ansichten zu tun haben. In der Ereignisliste können Sie Zeichnen-Befehle erweitern, um den Gerätestatus zum Zeitpunkt des Zeichnen-Befehls anzuzeigen, und jede Art von Status noch weiter erweitern, um die Ereignisse zu zeigen, die deren Werte festlegen. Auf dieser Ebene können Sie auch feststellen, ob ein bestimmter Status in einem vorherigen Frame festgelegt wurde oder ob er seit dem letzten Zeichnen-Befehl mehr als einmal festgelegt wurde.

 In der Ansicht **Zeitachse** wird jedes erfasste Ereignis in chronologischer Reihenfolge angezeigt. Diese Art, die Ereignisliste zu organisieren, ist dieselbe wie in vorherigen Versionen von Visual Studio.

##### <a name="to-change-the-event-list-view-mode"></a>So ändern Sie den Ansichtsmodus der Ereignisliste

- Suchen Sie im Fenster **Grafikereignisliste** über der Ereignisliste die Dropdownliste **Ansicht**, und wählen Sie die Ansicht **Zeitachse** oder die Ansicht **GPU-Arbeiten** aus.

### <a name="filtering-events"></a>Filtern von Ereignissen
 Sie können mithilfe des Feldes "Suchen" in der oberen rechten Ecke des Fensters **Grafikereignisliste** die Ereignisliste so filtern, dass sie nur Ereignisse enthält, in deren Namen bestimmte Schlüsselwörter vorkommen. Sie können einzelne Schlüsselwörter wie `Vertex`(s. Abbildung oben) oder mehrere Schlüsselwörter angeben, indem Sie eine durch Semikola getrennte Liste wie z.B. `Draw;Primitive`erstellen. Diese findet alle Ereignisse, in deren Namen entweder `Draw` oder `Primitive` vorkommt. Suchen sind leerzeichenspezifisch -– `VSSet` und `VS Set` sind z.B. verschiedene Suchvorgänge. Stellen Sie daher sicher, dass Sie Ihre Suchen sorgfältig ausführen.

### <a name="moving-between-draw-calls"></a>Navigieren zwischen Zeichnen-Befehlen
 Da die Untersuchung von `Draw` -Befehlen sehr wichtig ist, können Sie die Schaltflächen **Zum nächsten Zeichnen-Befehl wechseln** und **Zum vorherigen Zeichnen-Befehl wechseln** in der oberen linke Ecke des Fensters **Graphics Event List** verwenden, um schnell nach einzelnen Zeichnen-Befehlen zu suchen und zwischen diesen zu navigieren.

### <a name="links-to-graphics-objects"></a>Links zu Grafikobjekten
 Für das richtige Verständnis bestimmter Grafikereignisse können eventuell zusätzliche Informationen über den aktuellen Status von Direct3D oder über Direct3D-Objekte erforderlich sein, auf die das Ereignis verweist. Viele Ereignisse enthalten Links zu diesen Informationen, denen Sie folgen können, um mehr Details zu erfahren.

## <a name="kinds-of-events-and-event-markers"></a>Arten von Ereignissen und Ereignismarkern
 Die Ereignisse, die in der Ereignisliste angezeigt werden, sind in vier Kategorien organisiert: allgemeine Ereignisse, Zeichnen-Ereignisse, benutzerdefinierte Ereignisgruppen und benutzerdefinierte Ereignismarker. Außer allgemeinen Ereignissen wird jedes Ereignis zusammen mit einem Symbol angezeigt, das angibt, zu welcher Kategorie es gehört.

|Symbol|Ereignisbeschreibung|
|----------|-----------------------|
|(kein Symbol)|Allgemeines Ereignis<br /> Ein Ereignis, das kein benutzerdefiniertes Ereignis, keine benutzerdefinierte Ereignisgruppe und kein Zeichnen-Ereignis ist.|
|![Symbol für Zeichnen-Ereignis](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|Zeichnen-Ereignis<br /> Markiert ein Zeichnen-Ereignis, das während des erfassten Frames aufgetreten ist.|
|![Symbol „Benutzerdefinierter Ereignismarker“](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Benutzerdefinierte Ereignisgruppe<br /> Gruppiert verwandte Ereignisse auf von der App definierte Art.|
|![Symbol „Benutzerdefinierter Ereignismarker“](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Benutzerdefinierter Ereignismarker<br /> Markiert einen bestimmten Speicherort auf von der App definierte Art.|

## <a name="marking-user-defined-events-in-your-app"></a>Markieren von benutzerdefinierten Ereignissen in Ihrer App
 Benutzerdefinierte Ereignisse sind spezifisch für Ihre App. Sie können sie verwenden, um wichtige Ereignisse zuzuordnen, die in Ihrer App mit Ereignissen in der Grafikereignisliste auftreten. Sie können z. B. benutzerdefinierte Ereignisgruppen erstellen, um verwandte Ereignisse in Gruppen oder Hierarchien zu organisieren – z. B. diejenigen, die Ihre Benutzeroberfläche rendern –, sodass Sie die Ereignisliste leichter durchsuchen können, oder Sie können Marker erstellen, wenn eine bestimmte Art von Objekten gezeichnet wird, sodass Sie leicht die entsprechenden Grafikereignisse in der Ereignisliste finden können.

 Zur Erstellung von Gruppen und Marken in Ihrer App verwenden Sie dieselben APIs, die Direct3D zur Verwendung mit anderen Direct3D-Debugging-Tools bereitstellt. Diese APIs können in unterschiedlichen Versionen von Direct3D abweichen, die grundlegende Funktionalität bleibt jedoch identisch.

### <a name="user-defined-events-in-direct3d-12"></a>Benutzerdefinierte Ereignisse in Direct3D 12
 Verwenden Sie zum Erstellen von Gruppen und Markierungen in Direct3D 12 die in diesem Abschnitt beschriebenen APIs. In der folgenden Tabelle werden die APIs aufgeführt, die Sie je nachdem, ob Sie Ereignisse in einer Befehlswarteschlange oder einer Befehlsliste markieren, verwenden können.

|API-Beschreibung|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|
|---------------------| - | - |
|Überprüfen der Verfügbarkeit des benutzerdefinierten Ereignisses|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|
|Start einer Ereignisgruppe|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-beginevent)|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-beginevent)|
|Ende einer Ereignisgruppe|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-endevent)|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-endevent)|
|Erstellen eines Ereignismarkers|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-setmarker)|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-setmarker)|

### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Benutzerdefinierte Ereignisse in Direct3D 11 und früheren Versionen
 Verwenden Sie zum Erstellen von Gruppen und Markierungen in Direct3D 11 oder in früheren Versionen die in diesem Abschnitt beschriebenen APIs. In der Tabelle unten sind die APIs aufgeführt, die Sie in verschiedenen Versionen von Direct3D 11 und in früheren Versionen von Direct3D verwenden können.

|API-Beschreibung|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](/windows/win32/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) (Direct3D 11.1)|D3DPerf_ API-Familie (Direct3D 11.0 und früher)|
|---------------------| - | - | - |
|Start einer Ereignisgruppe|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|
|Ende einer Ereignisgruppe|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|
|Erstellen eines Ereignismarkers|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|

 Sie können jede dieser APIs verwenden, die Ihre Version von Direct3D unterstützt – wenn Sie z. B. wenn Sie die API Direct3D 11.1 verwenden möchten, können Sie entweder `SetMarker` oder `D3DPerf_SetMarker` verwenden, um einen Ereignismarker zu erstellen, aber nicht `SetMarkerInt` , da es nur in Direct3D 11.2 enthalten ist. Sie können auch APIs, die verschiedene Versionen von Direct3D verwenden, zusammen in derselben App kombinieren.

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## <a name="resource-history"></a>Ressourcenverlauf
Visual Studio 2017 und höher enthalten das Fenster **Ressourcenverlauf**.  Durch Auswählen des ![Überwachungssymbols](media/gfx_watch.png) neben einem Eintrag im Fenster **Ereignisliste** wird das nachstehend dargestellte Fenster **Ressourcenverlauf** geöffnet:

![Ressourcenverlauf](media/gfx_diag_resource_history.png)

In diesem Fenster können Sie den Verlauf des ausgewählten Elements in der Ereignisliste anzeigen.  Über die Dropdownliste im oberen Bereich können andere Elemente ausgewählt werden, deren Verlauf angezeigt werden soll.  Die obere Hälfte des Fensters enthält die **Framesetupereignisse**.  Diese Ereignisse fallen in die Kategorie *Erstellen* und stehen für Aufrufe, die in der Regel die Ressource initialisieren und erstellen.  Die untere Hälfte des Fensters enthält den Bereich **Frameereignisse**.  Dabei handelt es sich um die normalen Lese- und Schreibereignisse, die während der Verwendung der Ressource stattfinden.

| Spalte | Beschreibung |
|-----------| - |
| **Type** | Zeigt den Typ des Eintrags an, normalerweise *Erstellen*, *Lesen* oder *Schreiben*. |
| **Ansicht** | Zeigt eine Miniaturansicht der Ressource zu diesem Zeitpunkt an.  Doppelklicken Sie auf die Miniaturansicht, um eine Detailansicht der Ressource zu diesem Zeitpunkt zu öffnen. |
| **Event** | Zeigt den aufgetretenen Methodenaufruf, der das Ereignis generiert hat.  Alle weiteren Verläufe für einzelne Elemente können Sie anzeigen, indem Sie das Symbol „Überwachen“ ![Symbol „Überwachen“](media/gfx_watch.png) in der entsprechenden Zeile auswählen.  Außerdem können alle Elemente, die in blauem Text gezeichnet werden (z. B. `m_commandList` im obigen Screenshot) ausgewählt werden, um weitere Informationen zu erhalten. |

<!-- /VERSIONLESS -->

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Fehlende Objekte durch Gerätestatus](walkthrough-missing-objects-due-to-device-state.md)