---
title: Grafikereignisliste | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9e56f2d8ef72121e8b34117436019251449fbb75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845045"
---
# <a name="graphics-event-list"></a>Grafikereignisliste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden Sie die Grafikereignisliste in der Visual Studio-Grafikanalyse, um die Direct3D-Ereignisse zu untersuchen, die während des Renderings eines Frames Ihres Spiels oder Ihrer App aufgezeichnet wurden.  
  
 Dies ist die Ereignisliste:  
  
 ![Eine Liste von Ereignissen mit „Index“ im Namen.](../debugger/media/gfx-diag-demo-event-list-orientation.png "gfx_diag_demo_event_list_orientation")  
  
## <a name="using-the-event-list"></a>Verwenden der Ereignisliste  
 Wenn Sie ein Ereignis in der Ereignisliste auswählen, wird dieses in den Informationen wiedergegeben, die von anderen Grafikanalysetools angezeigt werden. Wenn Sie die Ereignisliste in Verbindung mit diesen anderen Tools verwenden, können Sie ein eventuelles Renderingproblem detailliert untersuchen, um seine Ursache zu ermitteln. Mehr Informationen über die Lösung von Renderingproblemen durch Verwendung der Ereignisliste in Verbindung mit anderen Grafikanalysetools finden Sie unter [Beispiele](../debugger/graphics-diagnostics-examples.md).  
  
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
 Die Ereignisliste bietet zwei verschiedene Ansichten zur Organisation von Grafikereignissen in verschiedener Weise, um Ihren Workflow und Ihre Präferenzen zu unterstützen. Die erste Ansicht ist die Ansicht *Zeichnen-Befehle* , in der Ereignisse und ihre Status hierarchisch organisiert werden. Die zweite Ansicht ist die Ansicht *Zeitachse* , in der Ereignisse chronologisch in einer flachen Liste organisiert werden.  
  
 Die Ansicht **Zeichnen-Befehle**  
 Zeigt erfasste Ereignisse und Ihren Status in der Hierarchie an. Die oberste Ebene der Hierarchie besteht aus Ereignissen wie Zeichnen-Befehlen, gelöschten und d vorhandenen Ereignissen und solchen, die mit Ansichten zu tun haben. In der Ereignisliste können Sie Zeichnen-Befehle erweitern, um den Gerätestatus zum Zeitpunkt des Zeichnen-Befehls anzuzeigen, und jede Art von Status noch weiter erweitern, um die Ereignisse zu zeigen, die deren Werte festlegen. Auf dieser Ebene können Sie auch feststellen, ob ein bestimmter Status in einem vorherigen Frame festgelegt wurde oder ob er seit dem letzten Zeichnen-Befehl mehr als einmal festgelegt wurde.  
  
 Die Ansicht **Zeitachse**  
 Zeigt jedes erfasste Ereignis in chronologischer Reihenfolge an. Diese Art, die Ereignisliste zu organisieren, ist dieselbe wie in vorherigen Versionen von Visual Studio.  
  
##### <a name="to-change-the-event-list-view-mode"></a>So ändern Sie den Ansichtsmodus der Ereignisliste  
  
- Suchen Sie im Fenster **Grafikereignisliste** über der Ereignisliste die Dropdownliste **Ansicht** , und wählen Sie entweder die Ansicht **Zeitachse** oder die Ansicht **Zeichnen-Befehle** .  
  
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
|![Symbol für Zeichnen-Ereignis](../debugger/media/vsg-eventlist-icon-draw.png "vsg_eventlist_icon_draw")|Zeichnen-Ereignis<br /> Markiert ein Zeichnen-Ereignis, das während des erfassten Frames aufgetreten ist.|  
|![Symbol „Benutzerdefinierter Ereignismarker“](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Benutzerdefinierte Ereignisgruppe<br /> Gruppiert verwandte Ereignisse auf von der App definierte Art.|  
|![Symbol „Benutzerdefinierter Ereignismarker“](../debugger/media/vsg-eventlist-icon-user.png "vsg_eventlist_icon_user")|Benutzerdefinierter Ereignismarker<br /> Markiert einen bestimmten Speicherort auf von der App definierte Art.|  
  
## <a name="marking-user-defined-events-in-your-app"></a>Markieren von benutzerdefinierten Ereignissen in Ihrer App  
 Benutzerdefinierte Ereignisse sind spezifisch für Ihre App. Sie können sie verwenden, um wichtige Ereignisse zuzuordnen, die in Ihrer App mit Ereignissen in der Grafikereignisliste auftreten. Sie können z. B. benutzerdefinierte Ereignisgruppen erstellen, um verwandte Ereignisse in Gruppen oder Hierarchien zu organisieren – z. B. diejenigen, die Ihre Benutzeroberfläche rendern –, sodass Sie die Ereignisliste leichter durchsuchen können, oder Sie können Marker erstellen, wenn eine bestimmte Art von Objekten gezeichnet wird, sodass Sie leicht die entsprechenden Grafikereignisse in der Ereignisliste finden können.  
  
 Zur Erstellung von Gruppen und Marken in Ihrer App verwenden Sie dieselben APIs, die Direct3D zur Verwendung mit anderen Direct3D-Debugging-Tools bereitstellt. Diese APIs können in unterschiedlichen Versionen von Direct3D abweichen, die grundlegende Funktionalität bleibt jedoch identisch.  
  
### <a name="user-defined-events-in-direct3d-12"></a>Benutzerdefinierte Ereignisse in Direct3D 12  
 Verwenden Sie zum Erstellen von Gruppen und Markierungen in Direct3D 12 die in diesem Abschnitt beschriebenen APIs. In der folgenden Tabelle werden die APIs aufgeführt, die Sie je nachdem, ob Sie Ereignisse in einer Befehlswarteschlange oder einer Befehlsliste markieren, verwenden können.  
  
|API-Beschreibung|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|  
|---------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Überprüfen der Verfügbarkeit des benutzerdefinierten Ereignisses|[PIXGetStatus](https://msdn.microsoft.com/f7ebd985-fb5d-46d7-abec-099df4b9be0e)|[PIXGetStatus](https://msdn.microsoft.com/1046ac43-a0a3-42bf-bae8-14aa72fa7567)|  
|Start einer Ereignisgruppe|[PIXBeginEvent](https://msdn.microsoft.com/5f51fff7-f313-4558-965b-2a443653cd7b)|[PIXBeginEvent](https://msdn.microsoft.com/4ddb3311-b9b5-449a-bbfb-7634e0d56e87)|  
|Ende einer Ereignisgruppe|[PIXEndEvent](https://msdn.microsoft.com/fb526bf2-c17d-4a2a-8665-3b577a0f7fba)|[PIXEndEvent](https://msdn.microsoft.com/a3cd34a9-9dd9-40e1-ae86-0214b25ff185)|  
|Erstellen eines Ereignismarkers|[PIXSetMarker](https://msdn.microsoft.com/0caf49ed-c99d-405e-89f4-0c887b8474ad)|[PIXSetMarker](https://msdn.microsoft.com/6610e5b9-a0c5-4236-b551-b6eb9fac64c1)|  
  
### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Benutzerdefinierte Ereignisse in Direct3D 11 und früheren Versionen  
 Verwenden Sie zum Erstellen von Gruppen und Markierungen in Direct3D 11 oder in früheren Versionen die in diesem Abschnitt beschriebenen APIs. In der Tabelle unten sind die APIs aufgeführt, die Sie in verschiedenen Versionen von Direct3D 11 und in früheren Versionen von Direct3D verwenden können.  
  
|API-Beschreibung|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](https://msdn.microsoft.com/library/windows/desktop/hh446881(v=vs.85).aspx) (Direct3D 11.1)|D3DPerf_ API-Familie (Direct3D 11.0 und früher)|  
|---------------------|---------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------|  
|Start einer Ereignisgruppe|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|  
|Ende einer Ereignisgruppe|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|  
|Erstellen eines Ereignismarkers|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|  
  
 Sie können jede dieser APIs verwenden, die Ihre Version von Direct3D unterstützt – wenn Sie z. B. wenn Sie die API Direct3D 11.1 verwenden möchten, können Sie entweder `SetMarker` oder `D3DPerf_SetMarker` verwenden, um einen Ereignismarker zu erstellen, aber nicht `SetMarkerInt` , da es nur in Direct3D 11.2 enthalten ist. Sie können auch APIs, die verschiedene Versionen von Direct3D verwenden, zusammen in derselben App kombinieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Exemplarische Vorgehensweise: Fehlende Objekte durch Gerätestatus](../debugger/walkthrough-missing-objects-due-to-device-state.md)
