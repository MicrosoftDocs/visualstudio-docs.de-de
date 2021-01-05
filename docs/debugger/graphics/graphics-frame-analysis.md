---
title: Grafikframe-Analyse | Microsoft-Dokumentation
description: Verwenden Sie die Grafikframe-Analyse in der Visual Studio-Grafikanalyse zum Analysieren und Optimieren der Renderingleistung ihres Direct3D-Spiels oder Ihrer -App.
ms.custom: SEO-VS-2020
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.frameanalysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f87686290842e0bbc3c575b5c72e3d1eeb24f351
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727722"
---
# <a name="graphics-frame-analysis"></a>Grafikframe-Analyse
Verwenden Sie die Grafikframe-Analyse in der Visual Studio-Grafikanalyse zum Analysieren und Optimieren der Renderingleistung ihres Direct3D-Spiels oder Ihrer -App.

## <a name="frame-analysis"></a>Frame-Analyse
 Für die Frame-Analyse werden die Informationen verwendet, die zu Diagnosezwecken in einer Grafikprotokolldatei erfasst wurden – hier jedoch zu dem Zweck, die Renderingleistung zusammenzufassen. Die Leistungsinformationen werden während der Erfassung nicht im Protokoll gespeichert, aber später während der Frame-Analyse durch Timing von Ereignissen und Sammlung von Statistiken erstellt, wenn der Frame wiedergegeben wird. Dieser Ansatz weist einige Vorteile gegenüber der Aufzeichnung der Leistungsinformationen während der Erfassung auf:

- Die Frame-Analyse kann den Durchschnitt aus Ergebnissen mehrerer Abspielungen desselben Frames berechnen, um zu gewährleisten, dass die Leistungszusammenfassung statistisch sicher ist.

- Die Frame-Analyse kann Leistungsinformationen für andere Hardwarekonfigurationen und Geräte generieren als diejenigen, in denen die Informationen erfasst wurden.

- Die Frame-Analyse kann neue Leistungszusammenfassungen aus zuvor erfassten Informationen erstellen – z.B., wenn GPU-Treiber optimiert werden – oder zusätzliche Debuggingfunktionen bereitstellen.

  Zusätzlich zu diesen Vorteilen kann die Frame-Analyse auch verwendet werden, um die Art zu ändern, in der der Frame während der Wiedergabe dargestellt wird, so dass er Informationen darüber darstellen kann, wie sich diese Änderungen auf die Rendering-Leistung einer App auswirken könnten. Sie können diese Informationen verwenden, um zwischen potenziellen Optimierungsstrategien zu wählen, ohne sie alle implementieren zu müssen, und dann alle Ergebnisse zu erfassen und miteinander zu vergleichen.

  Obwohl die Frame-Analyse hauptsächlich den Zweck hat, eine schnellere Renderingleistung zu erreichen, kann sie auch helfen, eine bessere visuelle Qualität bei einem angegebenen Leistungsziel zu erreichen oder den GPU-Stromverbrauch zu reduzieren.

  Sehen Sie sich das Video zur [Visual Studio-Grafikframe-Analyse](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) auf Channel 9 an, um eine Demonstration der Möglichkeiten der Frame-Analyse für Ihre App zu sehen.

## <a name="using-frame-analysis"></a>Verwenden der Frame-Analyse
 Bevor Sie die Frame-Analyse verwenden können, müssen Sie die Grafikinformationen von Ihrer App erfassen, während diese ausgeführt wird, und zwar so wie Sie dies mit einem anderen der Grafikanalysetools vornehmen würden. Wählen Sie anschließend im Fenster mit dem Grafikprotokolldokument die Registerkarte **Frame-Analyse**.

 ![Wählen Sie die Registerkarte „Frame-Analyse“ aus.](media/pix_frame_analysis_select_tab.png "pix_frame_analysis_select_tab")

 Wenn die Analyse abgeschlossen ist, werden die Ergebnisse angezeigt. Oben auf der Registerkarte Frame-Analyse werden die Zeitachse und die Zusammenfassungstabelle angezeigt. Im unteren Teil werden die Detailtabellen angezeigt. Wenn bei der Abspielung Fehler oder Warnungen ausgegeben wurden, werden diese über der Zeitachse angezeigt. Hier können Sie den Links folgen, um mehr über die Fehler und Warnungen zu erfahren.

### <a name="interpreting-results"></a>Interpretieren der Ergebnisse
 Durch die Interpretation der Ergebnisse jeder Variante erhalten Sie hilfreiche Informationen über die Renderingleistung und das Verhalten Ihrer App. Weitere Informationen über Rendering-Varianten finden Sie unter [Varianten](#Variants) weiter unten in diesem Artikel.

 Einige Ergebnisse zeigen direkt an, wie die jeweilige Variante die Renderingleistung beeinflusst:

- Wenn sich bei der Variante "Bilineare Texturfilterung" Leistungssteigerungen ergeben, dann wird die Verwendung der bilinearen Texturfilterung in Ihrer App zu ähnlichen Leistungssteigerungen führen.

- Wenn sich bei der Variante "1x1 Viewport" Leistungssteigerungen ergeben, dann wird durch Verkleinerung der Renderziele in Ihrer App die Renderingleistung verbessert.

- Wenn sich bei der Variante "BC-Texturkomprimierung" Leistungssteigerungen ergeben, dann wird die Verwendung der BC-Texturkomprimierung in Ihrer App zu ähnlichen Leistungssteigerungen führen.

- Wenn sich bei der Variante 2xMSAA eine ähnliche Leistung wie bei der Variante 0xMSAA ergibt, können Sie 2xMSAA in Ihrer App aktivieren, um die Renderingqualität zu erhöhen, ohne Abstriche bei der Leistung machen zu müssen.

  Andere Ergebnisse können eine noch tiefergehende, subtilere Bedeutung für die Leistung Ihrer App haben:

- Wenn sich bei der Variante "1x1 Viewport" großer Leistungssteigerungen ergeben, verbraucht ihre App wahrscheinlich eine größere Füllrate, als verfügbar ist. Wenn sich bei dieser Variante keine Leistungssteigerungen ergeben, verarbeitet die App wahrscheinlich zu viele Scheitelpunkte.

- Wenn sich bei der Variante "16bpp-Renderzielformat" deutliche Leistungssteigerungen ergeben, verbraucht Ihre App wahrscheinlich zu viel Speicherbandbreite.

- Wenn sich bei der Variante "Halbe/Viertel-Texturdimensionen" deutliche Leistungssteigerungen ergeben, belegen Ihre Texturen wahrscheinlich zu viel Speicher, verbrauchen zu viel Bandbreite oder verwenden den Texturcache ineffizient. Wenn sich bei dieser Variante keine Leistungsänderungen ergeben, können Sie wahrscheinlich auch größere und detailliertere Texturen verwenden, ohne Abstriche bei der Leistung machen zu müssen.

  Wenn Hardwarezähler zur Verfügung stehen, können Sie sie verwenden, um sehr genaue Informationen darüber zu gewinnen, warum die Renderingleistung Ihrer App niedrig sein könnte. Alle Geräte mit Funktionsebene 9.2 oder höher unterstützen alle Tiefenokklusionsabfragen (Zähler für **okkludierte Pixel**) und Zeitstempel. Eventuell sind noch andere Hardwarezähler verfügbar. Dies hängt davon ab, ob der GPU-Hersteller Hardwarezähler implementiert und sie in seinen Treiber integriert hat. Sie können diese Zähler verwenden, um den genauen Grund der in der Zusammenfassungstabelle aufgeführten Ergebnisse zu bestätigen – Sie können z. B. ermitteln, ob Überzeichnung ein Faktor ist, indem Sie den Prozentsatz an Pixeln untersuchen, die durch den Tiefentest okkludiert wurden.

### <a name="timeline-and-summary-table"></a>Zeitachse und Zusammenfassungstabelle
 Standardmäßig werden die Zeitachse und die Zusammenfassungstabelle angezeigt und die anderen Abschnitte ausgeblendet.

#### <a name="timeline"></a>Zeitachse
 Die Zeitachse zeigt eine relative Übersicht über die Zeichnen-Befehle. Da längere Balken längeren Zeichnungszeiten entsprechen, können Sie die Zeitachse verwenden, um schnell die teuersten Zeichnen-Befehle im betreffenden Frame zu finden. Wenn der erfasste Frame eine sehr große Anzahl von Zeichnen-Befehlen enthält, werden mehrere Zeichnen-Befehle in einem Balken kombiniert, dessen Länge der Summe dieser Zeichnen-Befehle entspricht.

 ![Die Zeitachse zeigt Zeichnen&#45;Aufrufkosten.](media/pix_frame_analysis_timeline.png "pix_frame_analysis_timeline")

 Sie können mit dem Zeiger auf einen Balken zeigen, um zu sehen, welchem Zeichnen-Befehlsereignis der Balken entspricht. Die Auswahl des Balkens führt zu einer Synchronisation der Ereignisliste mit dem entsprechenden Ereignis.

#### <a name="table"></a>Tabelle
 Die Tabelle mit Zahlen unter der Zeitachse zeigt die Leistung jeder Rendering-Variante für jeden Zeichnen-Befehl relativ zum Standard-Rendering Ihrer App. In jeder Spalte wird eine andere Rendering-Variante angezeigt, und jede Zeile steht für einen anderen Zeichnen-Befehl, der in der Spalte ganz links identifiziert wird. Hier können Sie einem Link zum betreffenden Ereignis im Fenster "Grafikereignisliste" folgen.

 ![Die Zusammenfassungstabelle zeigt verschiedene Varianten.](media/pix_frame_analysis_summary.png "pix_frame_analysis_summary")

 In der zweite Spalte von links der Zusammenfassungstabelle wird die Baseline-Rendering-Zeit Ihrer App angezeigt – dies ist die Dauer, in der das Standard-Rendering der App den Zeichnen-Befehl abschließt. In den anderen Spalten wird die relative Leistung jeder Rendering-Variante als Prozentsatz der Baseline dargestellt, sodass leichter festzustellen ist, ob die Leistung verbessert wurde. Prozentsätze über 100 bedeuten, dass das Rendering länger gedauert hat als die Baseline - d. h., dass die Leistung zurückgegangen ist –, und Prozentsätze unter 100 bedeuten, dass weniger Zeit benötigt wurde, die Leistung also gestiegen ist.

 Die Werte der absoluten Dauer der Baseline und der relativen Dauer der Rendering-Varianten sind in Wirklichkeit Mittelwerte mehrerer Durchgänge – standardmäßig 5. Diese Mittelwertbildung sichert die Zuverlässigkeit und Konsistenz der Zeitachsendaten. Sie können mit dem Zeiger auf jede Zelle in der Tabelle zeigen, um die minimalen, maximalen, mittleren und Median-Zeitwerte zu ermitteln, die erfasst wurden, als die Ergebnisse für diesen Zeichnen-Befehl und diese Zeichnen-Variante erzeugt wurden. Die Baseline-Dauer wird ebenfalls angezeigt.

#### <a name="hot-draw-calls"></a>"Heiße" Zeichnen-Befehle
 Um die Aufmerksamkeit auf Zeichnen-Befehle zu lenken, die einen größeren proportionalen Anteil der gesamten Rendering-Zeit verbrauchen oder aus vermeidbaren Gründen ungewöhnlich langsam sind, wird die Zeile, die diese "heißen" Zeichnen-Befehle enthält, rot schattiert, wenn ihre Baseline-Dauer um mehr als eine Standardabweichung länger ist als die durchschnittliche Baseline-Dauer aller Zeichnen-Befehle in diesem Rahmen.

 ![Dieser DrawIndexed-Aufruf weist kalte und heiße Varianten auf.](media/pix_frame_analysis_hot_calls.png "pix_frame_analysis_hot_calls")

#### <a name="statistical-significance"></a>Statistische Bedeutung
 Um Aufmerksamkeit auf die Rendering-Variationen mit der potenziell höchsten Relevanz zu lenken, ermittelt die Frame-Analyse die statistische Bedeutung jeder Rendering-Variante und zeigt die wichtigen in Fettdruck an. Die Varianten, die die Leistung verbessern, werden in grün angezeigt, diejenigen, die sie verschlechtern, in rot. Ergebnisse, die keine statistische Bedeutung haben, werden in normaler Schrift angezeigt.

 ![Die statistische Relevanz der Zeichnen-Aufrufvariante](media/pix_frame_analysis_summary_stats.png "pix_frame_analysis_summary_stats")

 Zum Ermitteln der statistischen Relevanz verwendet die Frame-Analyse den [t-Test](https://en.wikipedia.org/wiki/Student's_t-test).

### <a name="details-table"></a>Detailtabelle
 Unter der Zusammenfassungstabelle befindet sich die Detailtabelle, die standardmäßig reduziert ist. Der Inhalt der Detailtabelle hängt von der Hardwareplattform des Wiedergabecomputers ab. Weitere Informationen zu den unterstützten Hardwareplattformen finden Sie unter [Hardwaresupport](#HardwareSupport).

#### <a name="platforms-that-do-not-support-hardware-counters"></a>Plattformen, die keine Hardwarezähler unterstützen
 Die meisten Plattformen unterstützen Hardware-GPU-Zähler nicht vollständig. Zu diesen Plattformen gehören alle zurzeit von Intel, AMD und nVidia angebotenen GPUs. Wenn es keine Hardwarezähler zu sammeln gibt, wird nur eine Detailtabelle angezeigt. Diese enthält dann die mittleren absoluten Zeitwerte aller Varianten.

 ![Die Detailtabelle und einige Wiedergabevarianten.](media/pix_frame_analysis_details.png "pix_frame_analysis_details")

#### <a name="platforms-that-support-hardware-counters"></a>Plattformen, die Hardwarezähler unterstützen
 Für Plattformen, die Hardware-GPU-Zähler unterstützen – z. B. die nVidia T40 SOC und alle SOCs von Qualcomm – werden mehrere Detailtabellen angezeigt, eine pro Variante. Jeder verfügbare Hardwarezähler wird für jede Rendering-Variante erfasst und in seiner eigenen Detailtabelle angezeigt.

 ![Hardwareindikatoren werden angezeigt, wenn sie unterstützt werden.](media/pix_frame.png "pix_frame")

 Mit den Hardwarezähler-Informationen erhalten Sie eine sehr detaillierte Übersicht über das spezifische Hardwareplattform-Verhalten für jeden Zeichnen-Befehl, die Ihnen hilft, die Gründe für Leistungsengpässe sehr genau zu ermitteln.

> [!NOTE]
> Verschiedene Hardwareplattformen unterstützen verschiedene Zähler; es gibt keinen Standard. Welche Zähler vorhanden sind und was sie darstellen, wird allein von jedem GPU-Hersteller entschieden.

### <a name="marker-regions-and-events"></a>Markerbereiche und Ereignisse
 Die Frame-Analyse unterstützt benutzerdefinierte Ereignismarker und Ereignisgruppen. Sie werden in der Tabelle Zusammenfassung und in der Tabelle Detail angezeigt.

 Sie können entweder die ID3DUserDefinedAnnotation-APIs oder die veraltete D3DPERF_ API-Familie verwenden, um Marker und Gruppen zu erstellen. Wenn Sie die D3DPERF_ API-Familie verwenden, können Sie jedem Marker und jeder Gruppe eine Farbe zuweisen, die als farbiges Band in den Zeilen angezeigt wird, die den Ereignismarker oder die Begin/End-Marker für die Ereignisgruppen und ihre Inhalte enthält. Mit dieser Funktion können Sie schnell wichtige Rendering-Ereignisse oder Ereignisgruppen identifizieren.

### <a name="warnings-and-errors"></a>Warnungen und Fehler
 Die Frame-Analyse wird manchmal mit Warn- oder Fehlermeldungen abgeschlossen, die über der Zeitachse zusammengefasst und detailliert im unteren Teil der Registerkarte Frame-Analyse angezeigt werden.

 In der Regel werden Warnungen und Fehler nur zu Informationszwecken verwendet und ein Eingriff ist nicht erforderlich.

 Warnmelden zeigen normalerweise an, dass ein Hardwaresupport fehlt (was in diesem Fall jedoch umgangen werden kann), Hardwarezähler nicht gesammelt werden können oder bestimmte Leistungsdaten eventuell nicht zuverlässig sind – z. B., wenn eine Problemumgehung sie beeinflusst.

 Fehlermeldungen zeigen normalerweise an, dass die Implementierung der Frame-Analyse oder ein Treiber Fehler aufweist, ein Hardwaresupport fehlt (was in diesem Fall nicht umgangen werden kann) oder die App etwas versucht, was nicht von der Wiedergabe unterstützt wird.

### <a name="retries"></a>Wiederholungen
 Wenn die GPU während der Frame-Analyse einen Leistungsstatusübergang erfährt, muss die betroffene Analyse erneut ausgeführt werden, da in diesem Falle die GPU-Taktgeschwindigkeit geändert wurde und dadurch die betreffenden Zeitachsen-Ergebnisse ungültig geworden sind.

 Die Anzahl der Wiederholungen der Frame-Analyse ist auf 10 beschränkt. Wenn Ihre Plattform ein aggressives Leistungsmanagement oder Takt-Gating aufweist, kann die Frame-Analyse fehlschlagen und einen Fehler melden, falls der Wiederholungsgrenzwert überschritten wird. Sie können dieses Problem eventuell abschwächen, indem Sie das Leistungsmanagement und die Taktgeschwindigkeit auf weniger aggressive Werte zurücksetzen, wenn die Plattform dies erlaubt.

## <a name="hardware-support"></a><a name="HardwareSupport"></a> Hardwaresupport

### <a name="timestamps-and-occlusion-queries"></a>Zeitstempel und Okklusionsabfragen
 Zeitstempel werden auf allen Plattformen unterstützt, die die Frame-Analyse unterstützen. Tiefenokklusionsabfragen – die für den Zähler "Okkludierte Pixel" erforderlich sind – werden auf Plattformen unterstützt, die die Funktionsebene 9.2 oder höher unterstützen.

> [!NOTE]
> Obwohl Zeitstempel auf allen Plattformen unterstützt werden, die Frame-Analyse unterstützen, ist die Genauigkeit und Konsistenz der Zeitstempel von Plattform zu Plattform unterschiedlich.

### <a name="gpu-counters"></a>GPU-Zähler
 Die Unterstützung für GPU-Hardwarezähler ist hardwareabhängig.

 Da GPU-Hardwarezähler von keiner derzeit von Intel, AMD oder nVidia angebotenen Computer-GPU zuverlässig unterstützt werden, sammelt die Frame-Analyse von diesen keine Zähler. Jedoch sammelt die Frame-Analyse Hardwareindikatoren von der folgenden GPU, die sie zuverlässig unterstützt:

- nVidia T40 (Tegra4)

  Keine andere Plattform, die die Frame-Analyse unterstützt, sammelt GPU-Hardwarezähler.

> [!NOTE]
> Da GPU Hardware-Ressourcen Hardwareindikatoren sind, dauert es mehrere Durchgänge um den vollständigen Satz der Hardware-Leistungsindikatoren für jede Rendering-Variante zu erfassen. Daher ist die Reihenfolge, in der die GPU-Leistungsindikatoren erfasst wurden, nicht angegeben.

## <a name="unsupported-scenarios"></a>Nicht unterstützte Szenarien
 Bestimmte Verwendungsarten der Frame-Analyse werden nicht unterstützt oder sind einfach nicht sinnvoll.

### <a name="playback-of-high-feature-level-captures-on-down-level-devices"></a>Wiedergabe von Erfassungen mit hoher Funktionsebene auf Geräten mit niedriger Funktionsebene
 Wenn Sie in der Grafikanalyse eine Grafikprotokolldatei wiedergeben, die eine höhere Funktionsebene verwendet, als der Wiedergabecomputer unterstützt, fällt die Wiedergabe automatisch auf WARP zurück. In der Frame-Analyse fällt sie nicht explizit auf WARP zurück und erzeugt einen Fehler. WARP ist sinnvoll zur Untersuchung der Korrektheit Ihrer Direct3D-App, aber nicht zur Untersuchung von deren Leistung.

> [!NOTE]
> Obwohl es wichtig ist, die Probleme mit verschiedenen Funktionsebenen zu bedenken, können Sie Grafikprotokolldateien in verschiedenen Hardwarekonfigurationen und auf verschiedenen Geräten erfassen und abspielen. Die Grafikprotokolldatei kann wiedergegeben werden, solange sie keine APIs enthält oder Funktionsebenen verwendet, die auf dem Wiedergabecomputer nicht unterstützt werden.

### <a name="direct3d-10-and-lower"></a>Direct3D 10 und niedriger
 Wenn Ihre App die API Direct3D 10 aufruft, kann die Frame-Analyse sie nicht erkennen oder profilieren, auch wenn sie von anderen Grafikanalysetools erkannt und verwendet wird.

> [!NOTE]
> Dies gilt nur für Aufrufe der Direct3D-API, die Sie verwenden, nicht für Funktionsebenen.

### <a name="warp"></a>WARP
 Die Frame-Analyse ist zur Profilierung und Verbesserung der Renderingleistung auf echter Hardware gedacht. Die Ausführung der Frame-Analyse auf WARP-Geräten ist möglich, lohnt sich aber im Normalfall nicht, da die Ausführung von WARP auf einer High-End-CPU langsamer ist als mit den leistungsschwächsten modernen GPUs und da die WARP-Leistung je nach der CPU, auf der sie ausgeführt wird, erheblich variieren kann.

## <a name="variants"></a><a name="Variants"></a> Varianten
 Jede Änderung, die die Frame-Analyse an der Art durchführt, in der ein Frame während der Wiedergabe gerendert wird, wird *Variante* genannt. Die Varianten, die die Frame-Analyse untersucht, entsprechen allgemeinen, relativ einfachen Änderungen, die Sie vornehmen können, um die Renderingleistung oder die visuelle Qualität Ihrer App zu verbessern – z. B. Reduzierung der Größe von Texturen, Verwendung von Texturkomprimierungen oder Aktivierung verschiedener Arten von Anti-Aliasing. Varianten überschreiben den normalen Rendering-Kontext und die Parameter Ihrer App. Hier finden Sie eine Zusammenfassung:

|Variante|Beschreibung|
|-------------|-----------------|
|**1×1-Viewportgröße**|Reduziert die Viewport-Dimensionen auf allen Renderzielen auf 1x1 Pixel.<br /><br /> Weitere Informationen finden Sie unter [1×1-Viewportgrößenvariante](1x1-viewport-size-variant.md).|
|**0× MSAA**|Deaktiviert das Multi-Sample Anti-Aliasing (MSAA) auf allen Renderzielen.<br /><br /> Weitere Informationen finden Sie unter [0×/2×/4×-MSAA-Varianten](0x-2x-4x-msaa-variants.md)|
|**2× MSAA**|Aktiviert das 2x Multi-Sample Anti-Aliasing (MSAA) auf allen Renderzielen.<br /><br /> Weitere Informationen finden Sie unter [0×/2×/4×-MSAA-Varianten](0x-2x-4x-msaa-variants.md)|
|**4× MSAA**|Aktiviert das 4x Multi-Sample Anti-Aliasing (MSAA) auf allen Renderzielen.<br /><br /> Weitere Informationen finden Sie unter [0×/2×/4×-MSAA-Varianten](0x-2x-4x-msaa-variants.md)|
|**Punkttexturfilterung**|Setzt den Filtermodus für alle passenden Textur-Samples auf `DXD11_FILTER_MIN_MAG_MIP_POINT` (Punkttexturfilterung).<br /><br /> Weitere Informationen finden Sie unter [Punkt-, bilineare, trilineare und anisotrope Texturfiltervarianten](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Bilineare Texturfilterung**|Setzt den Filtermodus für alle passenden Textur-Samples auf `DXD11_FILTER_MIN_MAG_LINEAR_MIP_POINT` (bilineare Texturfilterung).<br /><br /> Weitere Informationen finden Sie unter [Punkt-, bilineare, trilineare und anisotrope Texturfiltervarianten](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Trilineare Texturfilterung**|Setzt den Filtermodus für alle passenden Textur-Samplings auf `DXD11_FILTER_MIN_MAG_MIP_LINEAR` (trilineare Texturfilterung).<br /><br /> Weitere Informationen finden Sie unter [Punkt-, bilineare, trilineare und anisotrope Texturfiltervarianten](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Anisotrope Texturfilterung**|Legt den Filtermodus für alle passenden Textur-Samplings auf `DXD11_FILTER_ANISOTROPIC` und `MaxAnisotropy` auf `16` (16× anisotrope Texturfilterung).<br /><br /> Weitere Informationen finden Sie unter [Punkt-, bilineare, trilineare und anisotrope Texturfiltervarianten](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**16bpp-Renderzielformat**|Setzt das Pixelformat für alle Renderziele und Hintergrundpuffer auf `DXGI_FORMAT_B5G6R5_UNORM` (16bpp, Format 565).<br /><br /> Weitere Informationen finden Sie unter [16bpp-Renderzielformat-Variante](16bpp-render-target-format-variant.md).|
|**Mipmap-Generierung**|Aktiviert Mipmaps auf allen Texturen, die keine Renderziele sind.<br /><br /> Weitere Informationen finden Sie unter [Mipmap-Generierungsvariante](mip-map-generation-variant.md).|
|**Halbe Texturdimensionen**|Reduziert die Texturdimensionen auf allen Texturen, die keine Renderziele sind, auf die Hälfte in jeder Dimension ihrer ursprünglichen Größe. Eine Textur der Größe 256x128 wird z. B. auf 128x64 Texel reduziert.<br /><br /> Weitere Informationen finden Sie unter [Halb-/Viertel-Texturdimensionsvariante](half-quarter-texture-dimensions-variant.md).|
|**Viertel-Texturdimensionen**|Reduziert die Texturdimensionen auf allen Texturen, die keine Renderziele sind, in jeder Dimension auf ein Viertel ihrer ursprünglichen Größe. Eine Textur der Größe 256x128 wird z. B. auf 64x32 Texel reduziert.<br /><br /> Weitere Informationen finden Sie unter [Halb-/Viertel-Texturdimensionsvariante](half-quarter-texture-dimensions-variant.md).|
|**BC-Texturkomprimierung**|Aktiviert die Blockkomprimierung auf allen Texturen mit der Pixelformatvariante B8G8R8X8, B8G8R8A8 oder R8G8B8A8. Varianten im Format B8G8R8X8 werden mit BC1 komprimiert; die Formatvarianten B8G8R8A8 und R8G8B8A8 werden mit BC3 komprimiert.<br /><br /> Weitere Informationen finden Sie unter [BC-Texturkomprimierungsvariante](bc-texture-compression-variant.md).|

 Das Ergebnis ist für die meisten Varianten präskriptiv: „Die Reduzierung der Texturgröße um die Hälfte ist um 25 % schneller“ oder „die Aktivierung von 2x MSAA ist nur um 2 % langsamer“. Andere Variationen können mehr Interpretation erfordern – z, B. wenn die Variante, die die Viewport-Dimensionen in 1x1 ändert, zu einer bedeutenden Leistungssteigerung führt. Dies kann bedeuten, dass das Rendering durch eine geringe Füllrate verlangsamt wird. Andererseits kann es, falls keine bedeutende Leistungsänderung auftritt, bedeuten, dass das Rendering durch die Scheitelpunktverarbeitung verlangsamt wird.