---
title: 'Exemplarische Vorgehensweise: Fehlende Objekte durch Gerätestatus | Microsoft-Dokumentation'
description: Ausführen einer Untersuchung, die einen falsch konfigurierten Gerätezustand ermittelt. Zeigt die Verwendung der Grafikereignisliste, Stufen der Grafikpipeline und den Grafikpixelverlauf.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b0d2bbd-0729-4aa5-8308-70c5bf1468c5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c29e240d4be2f66fb0684bf5372d59fe5d4d825a
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995056"
---
# <a name="walkthrough-missing-objects-due-to-device-state"></a>Exemplarische Vorgehensweise: Fehlende Objekte durch Gerätestatus
Diese exemplarische Vorgehensweise veranschaulicht, wie mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Grafikdiagnose ein Objekt untersucht werden kann, das wegen eines falsch konfigurierten Gerätestatus fehlt.

 In dieser exemplarischen Vorgehensweise wird Folgendes veranschaulicht:

- Verwenden der **Grafikereignisliste** , um mögliche Quellen des Problems zu finden

- Verwenden des Fensters **Grafikpipelinestufen** , um die Wirkung der `DrawIndexed` -Direct3D-API-Aufrufe zu prüfen

- Verwenden des Fensters **Grafikpixelverlauf** , um spezieller nach dem Problem zu suchen

- Überprüfen des Gerätestatus auf mögliche Probleme oder fehlerhafte Konfigurationen

## <a name="scenario"></a>Szenario
 Einer der Gründe dafür, dass Objekte nicht an den gewünschten Stellen in einer 3D-App angezeigt werden, kann eine fehlerhafte Konfiguration des Grafikgeräts sein, die zur Folge hat, dass die Objekte nicht gerendert werden. Dies kann z. B. der Fall sein, wenn die Windungsreihenfolge dazu führt, dass Dreiecke fälschlicherweise herausgefiltert werden, oder wenn die Tiefentestfunktion dazu führt, dass alle Pixel im Objekt abgelehnt werden.

 In dem Szenario, das in dieser exemplarischen Vorgehensweise beschrieben ist, haben Sie soeben den ersten Meilenstein in der Entwicklung Ihrer 3D-App erreicht und möchten diese nun zum ersten Mal testen. Wenn Sie die App ausführen, wird jedoch nur die Benutzeroberfläche auf dem Bildschirm gerendert. Mithilfe der Grafikdiagnose erfassen Sie das Problem in einer Grafikprotokolldatei, sodass Sie die App debuggen können. Das Problem sieht in der App wie folgt aus:

 ![Die Anwendung vor Behebung des Problems](media/vsg_walkthru1_firstview.png "vsg_walkthru1_firstview")

 Informationen zum Erfassen von Grafikproblemen in einem Grafikprotokoll finden Sie unter [Capturing Graphics Information](capturing-graphics-information.md).

## <a name="investigation"></a>Untersuchung
 Mithilfe der Grafikdiagnosetools können Sie die Grafikprotokolldatei laden, um die Frames zu untersuchen, die während des Tests erfasst wurden.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>So überprüfen Sie einen Frame in einem Grafikprotokoll

1. Laden Sie in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ein Grafikprotokoll, das einen Frame enthält, der das fehlende Modell darstellt. Eine neue Grafikdiagnose-Registerkarte wird in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]angezeigt. Ganz oben auf dieser Registerkarte befindet sich die Renderingzielausgabe des ausgewählten Frames. Im unteren Teil befindet sich die **Frameliste**, in der alle aufgezeichneten Frames als Miniaturansichten angezeigt werden.

2. Wählen Sie in der **Frameliste** einen Frame aus, der veranschaulicht, dass das Modell nicht angezeigt wird. Das Renderziel wird aktualisiert und gibt den ausgewählten Frame wieder. In diesem Szenario sieht die Grafikprotokoll-Registerkarte wie folgt aus:

    ![.vsglog-Registerkarte - Framepuffer-Vorschau und Frameliste](media/vsg_walkthru1_experiment.png "vsg_walkthru1_experiment")

   Wenn Sie einen Frame ausgewählt haben, der das Problem demonstriert, können Sie die **Grafikereignisliste** verwenden, um das Problem zu diagnostizieren. Die **Grafikereignisliste** enthält jeden Direct3D-API-Aufruf, der zum Rendern des aktiven Frames erfolgt ist, z. B. API-Aufrufe zum Einrichten des Gerätestatus, zum Erstellen und Aktualisieren von Puffern und zum Zeichnen von Objekten, die im Frame dargestellt werden. Viele Arten von Aufrufen sind interessant, weil sie häufig (aber nicht immer) mit einer entsprechenden Änderung beim Renderziel einhergehen, wenn die App erwartungsgemäß funktioniert. Dies gilt z. B. für Draw-, Dispatch-, Copy- oder Clear-Aufrufe. Draw-Aufrufe sind besonders interessant, da jeder Aufruf Geometrie darstellt, die von der App gerendert wird (auch Dispatch-Aufrufe können Geometrie rendern).

#### <a name="to-ensure-that-draw-calls-are-being-made"></a>So vergewissern Sie sich, dass Zeichnen-Befehle (Draw-Aufrufe) ausgeführt werden

1. Öffnen Sie das Fenster **Grafikereignisliste** . Wählen Sie auf der Symbolleiste **Grafikdiagnose** die **Ereignisliste** aus.

2. Suchen Sie in der **Grafikereignisliste** nach Zeichnen-Befehlen (Draw-Aufrufe). Zur Vereinfachung können Sie im Feld **Suche** in oberen rechten Ecke des Fensters **Grafikereignisliste** das Wort "Zeichnen" eingeben. Damit wird die Liste gefiltert und enthält nur Ereignisse, die "Zeichnen" im Titel haben. In diesem Szenario stellen Sie fest, dass mehrere Draw-Aufrufe ausgeführt wurden:

    ![Grafikereignisliste mit erfassten Ereignissen](media/vsg_walkthru1_.png "vsg_walkthru1_")

   Nachdem Sie bestätigt haben, dass Draw-Aufrufe ausgeführt werden, können Sie ermitteln, welcher Aufruf der fehlenden Geometrie entspricht. Da Sie wissen, dass die fehlende Geometrie im Renderziel nicht gezeichnet wird (in diesem Fall), können Sie im Fenster **Grafikpipelinestufen** feststellen, welcher Zeichnen-Befehl (Draw-Aufruf) der fehlenden Geometrie entspricht. Das Fenster **Grafikpipelinestufen** zeigt die Geometrie an, die an jeden Zeichnen-Befehl gesendet wurde, unabhängig von seiner Wirkung auf das Renderziel. Während Sie sich durch die Draw-Aufrufe bewegen, werden die Pipelinestufen aktualisiert, sodass die Geometrie angezeigt wird, die dem jeweiligen Aufruf zugeordnet ist, und es wird das Renderziel aktualisiert, um den Zustand des Renderziels nach dem Abschluss des Aufrufs anzuzeigen.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>So finden Sie den Zeichnen-Befehl für die fehlende Geometrie

1. Öffnen Sie das Fenster **Grafikpipelinestufen** . Wählen Sie auf der Symbolleiste **Grafikdiagnose** die **Pipelinestufen** aus.

2. Durchlaufen Sie jeden Draw-Aufruf, und beobachten Sie dabei das Fenster **Grafikpipelinestufen** , um das fehlende Modell zu ermitteln. In der **Eingabeassembler** -Stufe werden die Rohdaten des Modells angezeigt. In der **Vertexshader** -Stufe werden die transformierten Modelldaten angezeigt. In der **Pixelshader** -Stufe wird die Ausgabe des Pixelshaders angezeigt. In der **Ausgabezusammenführung** -Stufe werden das zusammengeführte Renderziel dieses Draw-Aufrufs und alle vorherigen Aufrufe angezeigt.

3. Halten Sie an, wenn Sie den Zeichnen-Befehl (Draw-Aufruf) erreicht haben, der dem fehlenden Modell entspricht. In diesem Szenario ist dem Fenster **Grafikpipelinestufen** zu entnehmen, dass die Geometrie gerendert, aber im Renderziel nicht angezeigt wurde:

    ![Pipeline-Viewer mit dem fehlenden Objekt](media/vsg_walkthru1_pipeline.png "vsg_walkthru1_pipeline")

   Nachdem Sie bestätigt haben, dass die App die fehlende Geometrie gerendert hat, und den entsprechenden Draw-Aufruf gefunden haben, können Sie einen Teil der Renderzielausgabe auswählen, in dem die fehlende Geometrie angezeigt werden sollte, und anschließend im Fenster **Grafikpixelverlauf** ermitteln, warum die Pixel ausgeschlossen wurden. Der Pixelverlauf enthält eine Liste aller Draw-Aufrufe, die sich auf ein bestimmtes Pixel auswirken könnten. Jeder Draw-Aufruf im Fenster **Grafikpixelverlauf** ist durch eine Zahl gekennzeichnet, die ebenfalls im Fenster **Grafikereignisliste** angezeigt wird. Über diese Zahl können Sie bestätigen, dass das Pixel die fehlende Geometrie anzeigen sollte, und feststellen, warum das Pixel ausgeschlossen wurde.

#### <a name="to-determine-why-the-pixel-was-excluded"></a>So ermitteln Sie, warum das Pixel ausgeschlossen wurde

1. Öffnen Sie das Fenster **Grafikpixelverlauf** . Wählen Sie auf der Symbolleiste **Grafikdiagnose** das Symbol für **Pixelverlauf** aus.

2. Wählen Sie anhand der **Pixelshader** -Miniaturansicht ein Pixel in der Framepufferausgabe aus, das einen Teil der fehlenden Geometrie enthalten sollte. In diesem Szenario muss die Ausgabe des Pixelshaders den größten Teil des Renderziels überdecken. Nachdem ein Pixel ausgewählt wurde, sieht das Fenster **Grafikpixelverlauf** wie folgt aus:

    ![Pixelverlauffenster mit zugehörigen Zeichnen-Befehlen](media/vsg_walkthru1_hist1.png "vsg_walkthru1_hist1")

3. Vergewissern Sie sich, dass das ausgewählte Renderzielpixel einen Teil der Geometrie enthält. Gleichen Sie dazu die Zahl des Draw-Aufrufs, den Sie überprüfen (aus dem Fenster **Grafikereignisliste** ), mit den Draw-Aufrufen im Fenster **Grafikpixelverlauf** ab. Stimmt keiner der Aufrufe im Fenster **Grafikpixelverlauf** mit dem Draw-Aufruf überein, den Sie überprüfen, wiederholen Sie die Schritte (mit Ausnahme von Schritt 1), bis Sie eine Übereinstimmung gefunden haben. In diesem Szenario sieht der übereinstimmende Draw-Aufruf wie folgt aus:

    ![Pixelverlauffenster mit Fragmentinformationen](media/vsg_walkthru1_hist2.png "vsg_walkthru1_hist2")

4. Wenn Sie eine Übereinstimmung gefunden haben, erweitern Sie den zugehörigen Draw-Aufruf im Fenster **Grafikpixelverlauf** , und vergewissern Sie sich, dass das Pixel ausgeschlossen wurde. Jeder Draw-Aufruf im Fenster **Grafikpixelverlauf** entspricht mindestens einem Geometrieprimitiv (Punkt, Linie oder Dreieck), das dieses Pixel als Ergebnis der Geometrie des entsprechenden Objekts geschnitten hat. Jeder dieser Schnitte kann zur endgültigen Farbe des Pixels beitragen. Ein Primitiv, das ausgeschlossen wurde, weil es den Tiefentest nicht bestanden hat, wird durch ein Symbol dargestellt, das den Buchstaben Z auf einem Pfeil enthält, der von links oben nach rechts unten geneigt ist.

5. Erweitern Sie ein ausgeschlossenes Primitiv, um den Zustand weiter zu überprüfen, der zum Ausschluss geführt hat. Bewegen Sie den Zeiger in der Gruppe **Ausgabezusammenführung** auf das **Ergebnis**. Eine QuickInfo gibt an, warum das Primitiv ausgeschlossen wurde. In diesem Szenario ergibt die Überprüfung, dass das Primitiv ausgeschlossen wurde, weil es den Tiefentest nicht bestanden hat, weshalb es nicht zur endgültigen Farbe des Pixel beigetragen hat.

   Nachdem Sie ermittelt haben, dass die Geometrie nicht angezeigt wird, weil deren Primitive den Tiefentest nicht bestanden haben, können Sie davon ausgehen, dass dieses Problem durch eine fehlerhafte Konfiguration des Gerätestatus bedingt ist. Gerätestatus- und andere Direct3D-Objektdaten können über die **Grafikobjekttabelle** überprüft werden.

#### <a name="to-examine-device-state"></a>So untersuchen Sie den Gerätestatus

1. Öffnen Sie das Fenster **Grafikobjekttabelle** . Wählen Sie auf der Symbolleiste **Grafikdiagnose** die Option **Objekttabelle** aus.

2. Suchen Sie in der **Grafikobjekttabelle** nach dem **D3D10-Gerät**-Objekt, und öffnen Sie dann das **D3D10-Gerät** -Objekt. Eine neue Registerkarte **d3d10-Gerät** wird in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]geöffnet. Um dies zu vereinfachen, können Sie die **Grafikobjekttabelle** nach dem **Typ** sortieren:

    ![Grafikobjekttabelle und der zugehörige Gerätezustand](media/vsg_walkthru1_objtable.png "vsg_walkthru1_objtable")

3. Überprüfen Sie den Gerätestatus, der auf der Registerkarte **d3d10-Gerät** angezeigt wird, auf mögliche Probleme. Da die Geometrie nicht angezeigt wird, weil deren Primitive den Tiefentest nicht bestanden haben, können Sie sich auf den Gerätestatus, etwa die Tiefenschablone, konzentrieren, der den Tiefentest beeinflusst. In diesem Szenario enthält die **Beschreibung der Tiefenschablone** (unter **Status der Ausgabezusammenführung**) einen ungewöhnlichen Wert für den **Tiefenfunktion** -Member `D3D10_COMPARISON_GREATER`:

    ![D3D10-Gerätefenster mit Informationen zur Tiefenschablone](media/vsg_walkthru1_devicestate.png "vsg_walkthru1_devicestate")

   Nachdem Sie ermittelt haben, dass der Grund für den Renderfehler eine fehlerhaft konfigurierte Tiefenfunktion sein könnte, können Sie anhand dieser Information und Ihrer Kenntnisse des Codes feststellen, wo die Tiefenfunktion falsch eingestellt wird, und das Problem dann beheben. Wenn Ihnen der Code unbekannt ist, könnten Sie anhand der Anhaltspunkte, die Sie beim Debuggen gesammelt haben, nach dem Problem suchen: Beispielsweise könnten Sie entsprechend der **Beschreibung der Tiefenschablone** in diesem Szenario den Code nach Wörtern wie „depth“ oder „GREATER“ durchsuchen. Nachdem Sie den Code korrigiert haben, erstellen Sie die App neu und führen diese erneut aus, um nun festzustellen, dass das Renderproblem behoben ist:

   ![App nach Behebung des Problems](media/vsg_walkthru1_finalview.png "vsg_walkthru1_finalview")