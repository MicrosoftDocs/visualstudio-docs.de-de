---
title: GPU-Nutzung | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie das Tool zur GPU-Nutzung im Leistungs-Profiler verwenden, um die allgemeine Hardwarenutzung Ihrer Direct3D-App besser zu verstehen.
ms.date: 11/01/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 78f847acaf67a61064e64b765d9c138ec2fe93a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959024"
---
# <a name="gpu-usage"></a>GPU-Nutzung

Verwenden Sie das Tool zur GPU-Nutzung im Leistungs-Profiler, um die allgemeine Hardwarenutzung Ihrer Direct3D-App besser zu verstehen. Sie können damit feststellen, ob die Leistung Ihrer App CPU- oder GPU-gebunden ist, und Sie erhalten Erkenntnisse darüber, wie Sie die Plattformhardware effektiver nutzen können. Das Tool für die GPU-Nutzung unterstützt Apps, die Direct3D 12, Direct3D 11 und Direct3D 10 verwenden. Andere Grafik-APIs, beispielsweise Direct2D oder OpenGL, werden nicht unterstützt.

Das Fenster mit dem **Bericht zur GPU-Nutzung** sieht folgendermaßen aus:

![Screenshot des GPU-Nutzungsberichts mit CPU- und GPU-Zeitplänen](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>Anforderungen

Zusätzlich zu den Anforderungen der Grafikdiagnose gelten für die Verwendung des Tools zur GPU-Nutzung die folgenden Anforderungen:

- Ein Grafikprozessor und Treiber, die die erforderliche zeitliche Timinginstrumentierung unterstützen.

  > [!NOTE]
  > Weitere Informationen zu unterstützter Hardware und unterstützten Treibern finden Sie unter [Unterstützte Hardware und Treiber](#hwsupport) am Ende dieses Dokuments.

Weitere Informationen zu Anforderungen für die Grafikdiagnose finden Sie unter [Erste Schritte](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md).

## <a name="use-the-gpu-usage-tool"></a>Das Tool zur GPU-Nutzung

Wenn Sie Ihre App mit dem Tool zur GPU-Nutzung untersuchen, erstellt Visual Studio eine Diagnosesitzung. In dieser Sitzung werden allgemeine Informationen zur Renderingleistung Ihrer App und zur GPU-Nutzung in Echtzeit grafisch dargestellt.

So starten Sie das GPU-Nutzungstool:

1. Wählen Sie im Hauptmenü **Debuggen** > **Leistung und Diagnose** aus (oder drücken Sie auf der Tastatur ALT+F2).

2. Aktivieren Sie im **Leistungs- und Diagnosehub** das Kontrollkästchen neben **GPU-Nutzung**. Aktivieren Sie optional die Kontrollkästchen neben anderen gewünschten Tools. Sie können mehrere Leistungs- und Diagnosetools gleichzeitig ausführen, um ein umfassenderes Bild zur Leistung Ihrer App zu erhalten.

    ![Screenshot des Leistungs-Profilers mit ausgewählter Option zur GPU-Nutzung](media/gpuusageselected.png "GPU-Nutzung ausgewählt")

   > [!NOTE]
   > Nicht alle Leistungs- und Diagnosetools können gleichzeitig verwendet werden.

3. Klicken Sie am unteren Rand des **Leistungs- und Diagnosehubs** auf die blaue Schaltfläche **Start**, um Ihre App mit den ausgewählten Tools auszuführen.

Die allgemeinen Informationen, die in Echtzeit angezeigt werden, umfassen Frametiming, Framerate und GPU-Nutzung. Jede dieser Informationen wird unabhängig von den anderen in einem Diagramm dargestellt, es wird jedoch eine gemeinsame Zeitskala verwendet, sodass Sie die Beziehungen leicht erkennen können.

Die Diagramme **Framedauer (ms)** und **Frames pro Sekunde (FPS)** enthalten jeweils zwei rote horizontale Linien, die Leistungsziele von 60 und 30 Frames pro Sekunde darstellen. Im Diagramm „Framedauer“ überschreitet Ihre App das Leistungsziel, wenn sich der Graph unterhalb der Linie befindet, und verfehlt das Ziel, wenn sich der Graph oberhalb der Linie befindet. Im Diagramm „Frames pro Sekunde“ verhält es sich umgekehrt: Wenn sich der Graph oberhalb der Linie befindet, überschreitet die App das Leistungsziel, und wenn sich der Graph unterhalb der Linie befindet, verfehlt sie das Ziel. Diese Diagramme werden in erster Linie verwendet, um eine allgemeine Vorstellung von der Leistung Ihrer App zu erhalten und Leistungseinbußen zu ermitteln, die dann näher untersucht werden können. Beispielsweise kann eine weitere Untersuchung angebracht sein, wenn Sie einen plötzlichen Abfall der Framerate oder eine Spitze bei der GPU-Auslastung verzeichnen.

Wenn Sie Ihre App im GPU-Nutzungstool ausführen, erfasst die Diagnosesitzung auch detaillierte Informationen zu den auf der GPU ausgeführten Grafikereignissen. Sie verwenden diese Informationen, um einen präziseren Bericht zur Hardwarenutzung Ihrer App zu erstellen. Da es einige Zeit dauert, diesen Bericht anhand der erfassten Informationen zu generieren, steht dieser nur zur Verfügung, wenn die Diagnosesitzung das Erfassen von Informationen bereits abgeschlossen hat.

Wenn Sie sich ein Problem mit der Leistung oder Auslastung näher anschauen möchten, müssen Sie die Erfassung von Leistungsinformationen beenden, um den Bericht generieren zu können.

So generieren Sie einen GPU-Nutzungsbericht und zeigen diesen an

1. Wählen Sie im unteren Bereich des Fensters „Diagnosesitzung“ den Link **Sammlung beenden** aus, oder klicken Sie oben links auf **Beenden**.

   ![Screenshot eines Diagnosesitzungsfenster im GPU-Nutzungstool, das Frames pro Sekunde, die GPU-Auslastung, die Schaltfläche „Beenden“ und den Link „Sammlung beenden“ zeigt.](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. Wählen Sie im oberen Bereich des Berichts einen Abschnitt aus einem der Diagramme, die das Problem anzeigt, das Sie untersuchen möchten. Ihre Auswahl kann bis zu 3 Sekunden lang sein. Längere Abschnitte werden am Anfang abgeschnitten.

   ![Screenshot eines Diagnosesitzungsfensters im GPU-Nutzungstool mit teilweise ausgewählter Diagnosesitzungs-Zeitachse.](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. Um eine detaillierte Zeitachse für Ihre Auswahl anzuzeigen, wählen Sie im unteren Bereich des Berichts in der Meldung **...Klicken Sie hier, um detaillierte Informationen zur GPU-Nutzung für diesen Bereich anzuzeigen** den Link **Details anzeigen** aus.

   ![Screenshot des Fensters für die Diagnosesitzung mit ausgewähltem Bereich](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

Mit dieser Auswahl wird ein neues Dokument im Registerkartenformat mit dem Bericht geöffnet. Anhand des GPU-Nutzungsberichts können Sie sehen, wann ein Grafikereignis auf der CPU gestartet wurde, wann es die GPU erreicht und wie lange die Ausführung durch die GPU gedauert hat. Anhand dieser Informationen können Sie Engpässe und Möglichkeiten für eine verbesserte Parallelität in Ihrem Code erkennen.

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>Exportieren zu GPUView oder Windows Performance Analyzer

Ab Visual Studio 2017 können Sie diese Daten mit [GPUView](/windows-hardware/drivers/display/using-gpuview) und [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer) öffnen. Wählen Sie einfach in der unteren rechten Ecke der Diagnosesitzung den Link **In GpuView öffnen** oder **In WPA öffnen** aus.

![Screenshot des Fensters für die Diagnosesitzung mit hervorgehobenen Links](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="use-the-gpu-usage-report"></a>Verwenden des GPU-Nutzungsberichts

Im oberen Abschnitt des GPU-Nutzungsberichts werden Zeitachsen für CPU-Verarbeitungsvorgänge, GPU-Renderingvorgänge und GPU-Kopiervorgänge angezeigt. Diese Zeitachsen werden durch hellgraue vertikale Balken unterteilt, die die vertikale Synchronisierung (vsync) der Anzeige darstellen. Die Häufigkeit der Balken entspricht der Aktualisierungsrate einer der Anzeigen (ausgewählt mithilfe des Dropdownmenüs **Anzeige**), aus der die GPU-Nutzungsdaten erfasst wurden.

Da die Anzeige eine höhere Aktualisierungsrate als das Leistungsziel Ihrer App haben kann, besteht ggf. keine 1:1-Beziehung zwischen VSync und der Framerate, die Ihre App erreichen soll. Um das Leistungsziel zu erreichen, muss eine App alle Verarbeitungsvorgänge abschließen, das Rendering ausführen und einen `Present()`-Aufruf mit der angestrebten Framerate senden. Der gerenderte Frame wird jedoch erst bei der nächsten VSync nach `Present()` angezeigt.

Im unteren Abschnitt werden des Berichts zur GPU-Nutzung werden Grafikereignisse aufgelistet, die innerhalb des Berichtszeitraums aufgetreten sind. Wenn Sie ein Ereignis auswählen, wird ein Marker bei entsprechenden Ereignissen auf den relevanten Zeitachsen angezeigt. In der Regel zeigt ein Ereignis auf einem CPU-Thread den API-Aufruf an, während ein anderes Ereignis auf einer der GPU-Zeitachsen anzeigt, wann die GPU die Aufgabe abgeschlossen hat. Wenn Sie ein Ereignis auf einer Zeitachse auswählen, wird umgekehrt das entsprechende Grafikereignis im unteren Bereich des Berichts hervorgehoben.

Wenn Sie die Zeitachsen im oberen Bereich des Berichts verkleinern, werden nur die Ereignisse mit dem höchsten Zeitaufwand angezeigt. Um Ereignisse mit einer kürzeren Dauer anzuzeigen, können Sie die Zeitachsen mithilfe von STRG+Mausrad oder mithilfe des Skalierungssteuerelements in der unteren linken Ecke des oberen Bereichs vergrößern. Sie können auch die Inhalte des Zeitachsenbereichs ziehen, um durch die erfassten Ereignisse zu navigieren.

Filtern Sie den GPU-Nutzungsbericht nach Prozessnamen, Thread-IDs und dem Ereignisnamen, um das gesuchte Element zu finden. Darüber hinaus können auswählen, welche Aktualisierungsrate der Anzeige die VSync-Zeilen bestimmt. Sie können Ereignisse hierarchisch sortieren, wenn Ihre App die Schnittstelle [ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) verwendet, um Renderingbefehle zu gruppieren.

 Nachstehend finden Sie weitere Details:

|Filtersteuerelement|Beschreibung|
|--------------------|-----------------|
|**Prozess**|Der Name des Prozesses, der Sie interessiert. Alle Prozesse, die GPU während der Diagnosesitzung verwenden, sind in dieser Dropdownliste enthalten. Die dem Prozess zugeordnete Farbe entspricht der Farbe der Threadvorgänge auf den Zeitachsen.|
|**Thread**|Die Thread-ID, die Sie interessiert. In einer Multithread-App können Sie mit diesen Informationen bestimmte Threads isolieren, die mit dem gewünschten Prozess verknüpft sind. Die im Zusammenhang mit dem ausgewählten Thread stehenden Ereignisse werden auf jeder Zeitachse hervorgehoben.|
|**Anzeige**|Die Nummer der Anzeige, deren Aktualisierungsrate angezeigt wird. Einige Treiber können so konfiguriert werden, dass mehrere physische Anzeigen als eine einzelne, große virtuelle Anzeige dargestellt werden. Selbst wenn mehrere Monitore an den Computer angeschlossen sind, wird ggf. nur eine Anzeige aufgeführt.|
|**Filter**|Die Schlüsselwörter, die Sie interessieren. Im unteren Bereich des Berichts werden nur die Ereignisse angezeigt, die mit einem Schlüsselwort ganz oder teilweise übereinstimmen. Sie können mehrere Schlüsselwörter durch Semikolons (;) getrennt angeben.|
|**Hierarchische Sortierung**|Ein Kontrollkästchen, das angibt, ob durch Benutzermarkierungen definierte Ereignishierarchien beibehalten oder ignoriert werden.|

Die Liste der Ereignisse im unteren Bereich des GPU-Nutzungsberichts zeigt detaillierte Informationen zu jedem Ereignis.

|Spalte|Beschreibung|
|------------|-----------------|
|**Ereignisname**|Der Name des Grafikereignisses. Ein Ereignis entspricht in der Regel einem Ereignis auf einer CPU-Threadzeitachse und einem Ereignis auf einer GPU-Zeitachse. Ereignisnamen sind möglicherweise mit dem Vermerk *ohne Attribute* gekennzeichnet, wenn die GPU-Nutzung nicht den Namen eines Ereignisses bestimmen konnte. Weitere Informationen finden Sie im Hinweis unter dieser Tabelle.|
|**CPU-Start (ns)**|Die Zeit, zu der das Ereignis auf der CPU durch Aufrufen einer Direct3D-API initiiert wurde. Die Zeit wird in Nanosekunden relativ zum Start der Anwendung gemessen.|
|**GPU-Start (ns)**|Die Zeit, zu der das Ereignis auf der GPU initiiert wurde. Die Zeit wird in Nanosekunden relativ zum Start der App gemessen.|
|**GPU-Dauer (ns)**|Die Zeit in Nanosekunden, die zum Abschließen des Ereignisses in der GPU benötigt wurde.|
|**Prozessname**|Der Name der App, von der das Ereignis stammt.|
|**Thread-ID**|Die Thread-ID, von der das Ereignis stammt.|

> [!IMPORTANT]
> Wenn GPU oder Treiber nicht die erforderlichen Instrumentationsfeatures unterstützen, werden alle Ereignisse mit dem Zusatz *ohne Attribute* gekennzeichnet. Falls dieses Problem auftritt, aktualisieren Sie Ihren GPU-Treiber, und versuchen Sie es noch mal. Weitere Informationen finden Sie unter [Hardware- und Treiberunterstützung](#hwsupport) am Ende dieses Dokuments.

## <a name="gpu-usage-settings"></a>GPU-Nutzungseinstellungen

Sie können das GPU-Nutzungstool so konfigurieren, dass die Erfassung von Profilerstellungsinformationen zurückgestellt wird, und nicht bereits beim Appstart beginnt. Da der Umfang der Profilerstellungsinformationen beträchtlich sein kann, ist diese Aktion hilfreich, um zu wissen, dass es erst zu einem späteren Zeitpunkt zur Verlangsamung der Leistung Ihrer App kommt.

So stellen Sie die Profilerstellung beim Start der App zurück

1. Wählen Sie im Hauptmenü **Debuggen** > **Leistung und Diagnose** aus (oder drücken Sie auf der Tastatur ALT+F2).

2. Klicken Sie im **Leistungs- und Diagnosehub** auf den Link **Einstellungen** neben **GPU-Nutzung**.

3. Deaktivieren Sie unter **GPU-Profilerstellungskonfiguration** auf der Eigenschaftenseite **Allgemein** das Kontrollkästchen **Profilerstellung bei App-Start beginnen**, um die Profilerstellung zurückzustellen.

   ![Screenshot der Objekteigenschaftenseiten mit Anzeige der Sammlungsoptionen](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> Aktuell können Sie die Profilerstellung für Direct3D 12-Apps nicht zurückstellen.

Wenn Sie Ihre App unter dem GPU-Nutzungstool ausführen, wird ein zusätzlicher Link im unteren Bereich des Fensters des GPU-Nutzungstools verfügbar. Wählen Sie zum Starten der Erfassung von Profilinformationen den Link **Starten** in der Meldung **Erfassung detaillierter GPU-Nutzungsdaten starten**.

## <a name="hardware-and-driver-support"></a><a name="hwsupport"></a> Unterstützte Hardware und Treiber

Folgende GPU-Hardware und Treiber werden unterstützt:

|Hersteller|GPU-Beschreibung|Erforderliche Treiberversion|
|------------|---------------------|-----------------------------|
|Intel®|Intel® Core Prozessoren der vierten Generation („Haswell“)<br /><br /> -   Intel® HD-Grafik (GT1)<br />-   Intel® HD-Grafik 4200 (GT2)<br />-   Intel® HD-Grafik 4400 (GT2)<br />-   Intel® HD-Grafik 4600 (GT2)<br />-   Intel® HD-Grafik P4600 (GT2)<br />-   Intel® HD-Grafik P4700 (GT2)<br />-   Intel® HD-Grafik 5000 (GT3)<br />-   Intel® Iris™ Grafik 5100 (GT3)<br />-   Intel® Iris™ Pro Grafik 5200 (GT3e)|(Verwenden Sie die neuesten Treiber)|
|AMD®|Die meisten Modelle ab der AMD Radeon™ HD 7000-Serie (AMD Radeon™ HD 7350-7670 ausgeschlossen)<br /><br /> AMD Radeon™-GPU, AMD FirePro™-GPUs und GPU-Beschleuniger von AMD FirePro mit GCN-Architektur (Graphics Core Next)<br /><br /> Accelerated Processing Units (APUs) der AMD® E-Serie und AMD A-Serie mit Graphics Core Next (GCN)-Architektur („Kaveri“, „Kabini“, „Temash“, „Beema“, „Mullins“)|14.7 RC3 oder höher|
|NVIDIA®|Die meisten Modelle ab der NVIDIA® GeForce®-400-Serie.<br /><br /> NVIDIA® GeForce®-GPUs, NVIDIA Quadro®-GPUs und NVIDIA® Tesla™-GPU-Beschleuniger mit Fermi™-, Kepler™-, oder Maxwell™-Architektur|343.37 oder höher|

 Multi-GPU-Konfigurationen wie z. B. NVIDIA® SLI™ und AMD Crossfire™ werden aktuell nicht unterstützt. Ein Hybrid-Grafik-Setup, z. B. NVIDIA® Optimus™ und AMD Enduro™ wird unterstützt.
