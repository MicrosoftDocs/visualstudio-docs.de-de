---
title: Bildbearbeitung
description: Erfahren Sie, wie Sie mit der Bildbearbeitung von Visual Studio Textur- und Bildressourcen anzeigen und bearbeiten können, die bei der Entwicklung von DirectX-Apps eingesetzt werden.
ms.custom: SEO-VS-2020
ms.date: 08/10/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bf8610f1db4b08d822d8a6c32172efde5efd0966
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880293"
---
# <a name="image-editor"></a>Grafik-Editor

In diesem Artikel wird beschrieben, wie Sie sich mit der **Bildbearbeitung** von Visual Studio Textur- und Bildressourcen anzeigen lassen und diese bearbeiten.

Mit der **Bildbearbeitung** können Sie mit aufwändigen Textur- und Bildformaten arbeiten, die bei der Entwicklung von DirectX-Apps verwendet werden. Unterstützt werden dabei gängige Bilddateiformate und Farbcodierungen, Features wie Alphakanäle und MIP-Zuordnungen sowie viele stark komprimierte Texturformate mit Hardwarebeschleunigung, die auch DirectX unterstützt.

## <a name="supported-formats"></a>Unterstützte Formate

Folgende Bildformate werden von der **Bildbearbeitung** unterstützt:

|Formatname|Dateinamenerweiterung|
|-----------------| - |
|Portable Network Graphics|*.png*|
|JPEG|*.jpg*, *.jpeg*, *.jpe*, *.jfif*|
|Direct Draw Surface|*.dds*|
|Graphics Interchange Format|*.gif*|
|Bitmap|*.bmp*, *.dib*|
|Tagged Image File Format|*.tif*, *.tiff*|
|TGA (Targa)|*.tga*|

## <a name="get-started"></a>Erste Schritte

In diesem Abschnitt wird beschrieben, wie Sie Ihrem Visual Studio-Projekt ein Bild hinzufügen und dieses Ihren Anforderungen gemäß konfigurieren.

### <a name="add-an-image-to-your-project"></a>Hinzufügen eines Bildes zu einem Projekt

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü des Projekts, zu dem Sie das Bild hinzufügen möchten, und klicken Sie dann auf **Hinzufügen** > **Neues Element**.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** unter **Installiert** die Option **Grafiken** und anschließend ein entsprechendes Dateiformat für das Bild aus.

   > [!NOTE]
   > Wenn im Dialogfeld **Neues Element hinzufügen** nicht die Kategorie **Grafiken** angezeigt wird, müssen Sie möglicherweise die Komponente **Bild- und 3D-Modell-Editoren** installieren. Schließen Sie den Dialog, und klicken Sie in der Menüleiste auf **Extras** > **Get Tools and Features** (Extras und Features abrufen), um den **Visual Studio-Installer** herunterzuladen. Klicken Sie erst auf die Registerkarte **Einzelne Komponenten** und dann unter der Kategorie **Spiele und Grafiken** auf die Komponente **Bild- und 3D-Modell-Editoren**. Wählen Sie **Ändern** aus.
   >
   > ![Komponente „Bild- und 3D-Modell-Editoren“](media/image-3d-model-editors-component.png)

   Informationen zur Auswahl eines Dateiformats, das Ihren Anforderungen entspricht, finden Sie unter [Auswählen des Bildformats](#choose-the-image-format).

3. Legen Sie den **Namen** der Bilddatei und den **Speicherort** fest, an dem diese erstellt werden soll.

4. Wählen Sie die Schaltfläche **Hinzufügen** aus.

### <a name="choose-the-image-format"></a>Auswählen des Bildformats

Abhängig von der geplanten Verwendung des Bilds sind bestimmte Dateiformate möglicherweise besser geeignet als andere. Features wie Transparenz oder bestimmte Farbformate werden möglicherweise nicht von allen Formaten unterstützt. Auch eine geeignete Komprimierung für die beabsichtigten Bildinhalte ist eventuell nicht verfügbar.

Die folgenden Informationen können Ihnen bei der Auswahl eines Bildformats helfen, das Ihre Anforderungen erfüllt:

**Bitmapbild (BMP)**

Das Bitmap-Bildformat. Ein nicht komprimiertes Bildformat, das 24-Bit-Farbe unterstützt. Das Bitmapformat unterstützt keine Transparenz.

**GIF-Bild (GIF)**

Das GIF-Bildformat (Graphics Interchange Format). Ein LZW-komprimiertes, verlustfreies Bildformat, das bis zu 256 Farben unterstützt. Ungeeignet für Fotografien und Bilder mit hohen Farbendetails. Es verfügt jedoch über gute Komprimierungsverhältnisse für Bilder mit wenig Farbe aber einem hohen Grad an Farbenkohärenz.

**JPG-Bild (JPG)**

Das JPEG-Bildformat (Joint Photographic Experts Group). Ein stark komprimiertes, verlustbehaftetes Bildformat, das 24-Bit-Farben unterstützt und für allgemeine Zwecke zur Komprimierung von Bildern mit hoher Farbkohärenz geeignet ist.

**PNG-Bild (PNG)**

Das PNG-Bildformat (Portable Network Graphics). Ein mittelmäßig stark komprimiertes, verlustfreies Bildformat, das 24-Bit-Farben und Alphatransparenz unterstützt. Es ist sowohl für natürliche als auch künstliche Bilder geeignet. Die Komprimierungsverhältnisse sind jedoch nicht so gut wie bei verlustbehafteten Formaten, wie JPG oder GIF.

**TIFF-Bild (TIFF)**

Das TIFF- oder TIF-Bildformat (Tagged Image File Format). Ein flexibles Bildformat, das mehrere Komprimierungsschemas unterstützt.

**DDS-Textur (DDS)**

Das DDS-Texturformat (DirectDraw Surface-Texturformat). Ein stark komprimiertes, verlustbehaftetes Texturformat, das 24-Bit-Farben und Alphatransparenz unterstützt. Die Komprimierungsverhältnisse können bis zu 8:1 betragen. Es basiert auf dem Texturkomprimierungssystem "S3 Texture Compression", das mithilfe von Grafikhardware dekomprimiert werden kann.

**TGA-Bild (TGA)**

Das TGA-Bildformat (Truevision Graphics Adapter-Format; auch unter der Bezeichnung Targa bekannt). Ein RLE-komprimiertes, verlustfreies Bildformat, das sowohl farbzugeordnete (Farbpalette) oder Direct Color-Bilder bis zu 24-Bit-Farben und Alphatransparenz unterstützt. Unpassend für Fotografien und Bilder mit hohem Farbendetails. Es stellt verfügt jedoch über gute Komprimierungsverhältnisse für Bilder mit weitflächigen identischen Farben.

### <a name="configure-the-image"></a>Konfigurieren des Bilds

Bevor Sie mit dem erstellten Bild zu arbeiten beginnen, können Sie seine Standardkonfiguration ändern. Beispielsweise können Sie seine Abmessungen oder das verwendete Farbformat ändern. Weitere Informationen zur Konfiguration dieser und anderer Bildeigenschaften finden Sie unter [Bildeigenschaften](#image-properties).

> [!NOTE]
> Bevor Sie Ihre Arbeit speichern, legen Sie die Eigenschaft **Farbformat** fest, wenn Sie ein bestimmtes Farbformat verwenden möchten. Sie können die Komprimierungseinstellungen anpassen, wenn Sie die Datei zum ersten Mal speichern oder **Speichern unter** auswählen, sofern das Dateiformat die Komprimierung unterstützt.

## <a name="work-with-the-image-editor"></a>Arbeiten mit dem Bild-Editor

In diesem Abschnitt wird beschrieben, wie Sie mit der **Bildbearbeitung** Texturen und Bilder erstellen und ändern.

Auf der Symbolleiste für den **Bildbearbeitungsmodus** finden Sie Befehle, die Auswirkungen auf den Zustand der **Bildbearbeitung** haben, sowie erweiterte Befehle. Die Symbolleiste befindet sich am oberen Rand der Entwurfsoberfläche der **Bildbearbeitung**. Die Zeichentools befinden sich auf der Symbolleiste der **Bildbearbeitung** am linken Rand der Entwurfsoberfläche der **Bildbearbeitung**.

### <a name="image-editor-mode-toolbar"></a>Symbolleiste für Bildbearbeitungsmodus

![Symbolleiste für Bildbearbeitungsmodus in Visual Studio](../designers/media/digit-tre-modal-toolbar.png)

In der folgenden Tabelle werden die Elemente der Symbolleiste des **Bildbearbeitungsmodus** beschrieben und in der Reihenfolge aufgelistet, in der sie auf der Symbolleiste von links nach rechts angezeigt werden:

|Element der Symbolleiste|Beschreibung|
|------------------|-----------------|
|**Auswählen**|Ermöglicht die Auswahl eines rechteckigen Bereichs eines Bilds. Nachdem Sie einen Bereich ausgewählt haben, können Sie ihn ausschneiden, kopieren, verschieben, skalieren, drehen, spiegeln oder löschen. Wenn eine aktive Auswahl vorhanden ist, haben die Zeichenwerkzeuge nur Auswirkungen auf den ausgewählten Bereich.|
|**Unregelmäßige Auswahl**|Ermöglicht die Auswahl eines unregelmäßigen Bereichs eines Bilds. Nachdem Sie einen Bereich ausgewählt haben, können Sie ihn ausschneiden, kopieren, verschieben, skalieren, drehen, spiegeln oder löschen. Wenn eine aktive Auswahl vorhanden ist, haben die Zeichenwerkzeuge nur Auswirkungen auf den ausgewählten Bereich.|
|**Stabsauswahl**|Ermöglicht die Auswahl eines Bildbereichs, der eine ähnliche Farbe aufweist. Die *Toleranz*, d.h. der maximale Unterschied zwischen benachbarten Farben, innerhalb dessen sie als ähnlich betrachtet werden, lässt sich so konfigurieren, dass ein kleinerer oder größerer Bereich von ähnlichen Farben berücksichtigt werden kann. Nachdem Sie einen Bereich ausgewählt haben, können Sie ihn ausschneiden, kopieren, verschieben, skalieren, drehen, spiegeln oder löschen. Wenn eine aktive Auswahl vorhanden ist, haben die Zeichenwerkzeuge nur Auswirkungen auf den ausgewählten Bereich.|
|**Schwenken**|Ermöglicht das Verschieben des Bilds relativ zum Fensterrahmen. Wählen Sie im **Schwenken**-Modus einen Punkt auf dem Bild aus, und bewegen Sie ihn.<br /><br /> Sie können den **Schwenken**-Modus vorübergehend aktivieren, indem Sie **STRG** gedrückt halten.|
|**Zoomen**|Ermöglicht das Anzeigen von mehr oder weniger Bilddetails relativ zum Fensterrahmen. Wählen Sie im **Zoom**-Modus einen Punkt auf dem Bild aus, und verschieben Sie ihn: zum Vergrößern nach rechts oder nach unten und zum Verkleinern nach links oder nach oben.<br /><br /> Sie können ihn vergrößern oder verkleinern, indem Sie **STRG** gedrückt halten, während Sie entweder das Mausrad verwenden oder das Pluszeichen (**+**) oder Minuszeichen (**-**) drücken.|
|**Originalgröße anzeigen**|Zeigt das Bild in einem 1:1-Verhältnis zwischen Pixel des Bilds und Pixel des Bildschirms.|
|**Mit Zoom anpassen**|Zeigt das ganze Bild im Fensterrahmen an.|
|**Auf Breite vergrößern**|Zeigt die gesamte Breite des Bilds im Fensterrahmen an.|
|**Grid**|Aktiviert oder deaktiviert das Raster, das die Pixelgrenzen anzeigt. Das Raster wird möglicherweise erst angezeigt, wenn Sie das Bild vergrößern.|
|**Nächste MIP-Ebene anzeigen**|Aktiviert die nächsthöhere MIP-Ebene in einer MIP-Zuordnungskette. Die aktive MIP-Ebene wird auf der Entwurfsoberfläche angezeigt. Dieses Element ist nur für Texturen mit MIP-Ebenen verfügbar.|
|**Vorherige MIP-Ebene anzeigen**|Aktiviert die nächstkleinere MIP-Ebene in einer MIP-Zuordnungskette. Die aktive MIP-Ebene wird auf der Entwurfsoberfläche angezeigt. Dieses Element ist nur für Texturen mit MIP-Ebenen verfügbar.|
|**Roter Kanal**<br /><br /> **Grüner Kanal**<br /><br /> **Blauer Kanal**<br /><br /> **Alphakanal**|Aktiviert oder deaktiviert den spezifischen Farbkanal. **Hinweis:** Durch systematisches Aktivieren oder Deaktivieren von Farbkanälen können Sie Probleme isolieren, die mit einem oder mehreren Farbkanälen zusammenhängen. Sie können beispielsweise eine falsche Alphatransparenz identifizieren.|
|**Hintergrund**|Aktiviert oder deaktiviert die Anzeige des Hintergrunds durch transparente Teile des Bilds. Sie können durch Auswahl einer der folgenden Optionen konfigurieren, wie der Hintergrund angezeigt wird:<br /><br /> **Schachbrett**<br /> Verwendet eine grüne Farbe zusammen mit der angegebenen Hintergrundfarbe, um den Hintergrund als Schachbrettmuster darzustellen. Sie können diese Option verwenden, um transparente Teile des Bilds sichtbarer zu machen.<br /><br /> Weißer Hintergrund<br /> Verwendet die Farbe Weiß, um den Hintergrund anzuzeigen.<br /><br /> Schwarzer Hintergrund<br /> Verwendet die Farbe Schwarz, um den Hintergrund anzuzeigen.<br /><br /> Hintergrund animieren<br /> Schwenkt das Schachbrettmuster langsam. Sie können diese Option verwenden, um transparente Teile des Bilds sichtbarer zu machen.|
|**Eigenschaften**|Öffnet bzw. schließt das Fenster **Eigenschaften**.|
|**Erweitert**|Enthält zusätzliche Befehle und Optionen.<br /><br /> **Filter**<br /><br /> Stellt einige allgemeine Bildfilter bereit: **Schwarz und weiß**, **Weichzeichner**, **Aufhellen**,**Abdunkeln**, **Kantenerkennung**, **Relief**, **Farben umkehren**, **Wellen**, **Sepia** und **Scharfzeichnen**.<br /><br /> **Grafik-Engines**<br /><br /> **Mit D3D11 rendern**<br /> Verwendet Direct3D 11 zum Rendern der Entwurfsoberfläche der **Bildbearbeitung**.<br /><br /> **Mit D3D11WARP rendern**<br /> Verwendet Direct3D 11 Windows Advanced Rasterization Platform (WARP) zum Rendern der Entwurfsoberfläche der **Bildbearbeitung**.<br /><br /> **Extras**<br /><br /> **Horizontal spiegeln**<br /> Vertauscht das Bild um seine horizontale bzw. X-Achse.<br /><br /> **Vertikal spiegeln**<br /> Vertauscht das Bild um seine vertikale bzw. Y-Achse.<br /><br /> **MIPS generieren**<br /> Generiert MIP-Ebenen für ein Bild. Wenn bereits MIP-Ebenen vorhanden sind, werden sie von der größten MIP-Ebene neu erstellt. Alle Änderungen, die an kleineren MIP-Ebenen vorgenommen wurden, gehen verloren. Wenn Sie die MIP-Ebenen speichern möchten, die Sie generiert haben, müssen Sie zum Speichern des Bilds das *DDS*-Format verwenden.<br /><br /> **Anzeigen**<br /><br /> **Bildfrequenz**<br /> Bei aktivierter Option wird in der rechten oberen Ecke der Entwurfsoberfläche die Framerate angezeigt. Die Einzelbildrate ist die Anzahl von Bildern, die pro Sekunde gezeichnet werden. **Tipp:** Klicken Sie zum erneuten Ausführen des letzten Befehls auf die Schaltfläche **Erweitert**.|

### <a name="image-editor-toolbar"></a>Symbolleiste der Bildbearbeitung

![Symbolleiste der Bildbearbeitung](../designers/media/digit-tre-toolbar.png)

In der folgenden Tabelle werden die Elemente der Symbolleiste der **Bildbearbeitung** beschrieben und in der Reihenfolge aufgelistet, in der sie auf der Symbolleiste von oben nach unten angezeigt werden:

|Element der Symbolleiste|Beschreibung|
|------------------|-----------------|
|**Pencil**|Verwendet die aktive Farbauswahl, um einen Aliasstrich zu zeichnen. Sie können Farbe und Stärke des Strichs im Fenster **Eigenschaften** festlegen.|
|**Brush**|Verwendet die aktive Farbauswahl, um einen Strich mit Antialiasing zu zeichnen. Sie können Farbe und Stärke des Strichs im Fenster **Eigenschaften** festlegen.|
|**Airbrush**|Verwendet die aktive Farbauswahl, um einen Strich mit Antialiasing zu zeichnen, der in das Bild übergeht und im Laufe der Zeit mehr an Sättigung gewinnt. Sie können Farbe und Stärke des Strichs im Fenster **Eigenschaften** festlegen.|
|**Eyedropper**|Legt die aktive Farbauswahl für die Farbe des ausgewählten Pixels fest.|
|**Ausfüllen**|Verwendet die aktive Farbauswahl, um einen Bereich des Bilds auszufüllen. Der betreffende Bereich wird als der Pixel definiert, auf den die Füllung angewendet wird, zusammen mit jedem Pixel, das mit ihm durch Pixel derselben Farbe verbunden ist und dieselbe Farbe aufweist. Wenn die Füllung innerhalb einer aktiven Auswahl angewendet wird, wird der betroffene Bereich von der Auswahl beschränkt.<br /><br /> Standardmäßig geht die aktive Farbauswahl in den betroffenen Bereich des Bilds entsprechend des Alphaanteils über. Wenn der betroffene Bereich mit der aktiven Farbauswahl überschrieben werden soll, halten Sie die **UMSCHALTTASTE** gedrückt, während Sie das Füllwerkzeug verwenden.|
|**Eraser**|Legt Pixel auf eine vollständig transparente Farbe fest, wenn das Bild einen Alphakanal unterstützt. Andernfalls werden die Pixel auf die aktuelle Hintergrundfarbe festgelegt.|
|**Linie**, **Rechteck**, **Abgerundetes Rechteck**, **Ellipse**|Zeichnet eine Form auf dem Bild. Sie können Farbe und Stärke der Kontur im Fenster **Eigenschaften** festlegen.<br /><br /> Halten Sie die **UMSCHALTTASTE** beim Zeichnen gedrückt, um ein Primitiv mit gleicher Breite und Höhe zu zeichnen.|
|**Text**|Verwendet die Vordergrundfarben-Auswahl, um Text zu zeichnen. Die Hintergrundfarbe wird durch die Hintergrundfarben-Auswahl bestimmt. Für einen transparenten Hintergrund muss der Alphawert der Hintergrundfarben-Auswahl 0 sein. Wenn der Textbereich aktiv ist, können Sie festlegen, ob der Text mit einem Strich mit Antialiasing gezeichnet wird. Im Fenster **Eigenschaften** können Sie **Wert**, **Schriftart**, **Größe** und Stil (**Fett**, **Kursiv** oder **Unterstrichen**) für den Text festlegen. Der Inhalt und die Darstellung des Texts wird fertig gestellt, wenn der Textbereich nicht mehr aktiv ist.|
|**Drehen**|Dreht das Bild um 90 Grad im Uhrzeigersinn.|
|**Trim**|Schneidet das Bild gemäß der aktuellen Auswahl ab.|

### <a name="work-with-mip-levels"></a>Arbeiten mit MIP-Ebenen

Einige Bildformate, z.B. DirectDraw Surface (*.dds*), unterstützen MIP-Ebenen für den Detaillierungsgrad (LOD) des Texturraums. Informationen zum Generieren von und Arbeiten mit MIP-Ebenen finden Sie unter [Vorgehensweise: Erstellen und Ändern von MIP-Ebenen](../designers/how-to-create-and-modify-mip-levels.md).

### <a name="work-with-transparency"></a>Arbeiten mit Transparenz

Einige Bildformate, z.B. DirectDraw Surface (*.dds*), unterstützen Transparenz. Es gibt mehrere Möglichkeiten, Transparenz zu verwenden. Diese hängen von Ihrem Tool ab. Legen Sie im Fenster **Eigenschaften** die Komponente **A** (Alpha) für die Farbauswahl fest, um die Ebene der Transparenz für eine Farbauswahl anzugeben.

In der folgende Tabelle wird beschrieben, wie unterschiedliche Tools Transparenz anwenden:

|Tool|Beschreibung|
|----------|-----------------|
|**Zeichenstift**, **Pinsel**, **Airbrush**, **Linie**, **Rechteck**, **Abgerundetes Rechteck**, **Ellipse**, **Text**|Erweitern Sie zum Verschmelzen der aktiven Farbauswahl mit dem Bild die Eigenschaftengruppe **Kanäle** im Fenster **Eigenschaften**, und aktivieren Sie das Kontrollkästchen **Zeichnen** des **Alphakanals**. Zeichnen Sie dann ganz normal.<br /><br /> Deaktivieren Sie das Kontrollkästchen **Zeichnen** des **Alphakanals**, und zeichnen Sie normal weiter, um mit der aktiven Farbauswahl zu zeichnen und den Alphawert des Bilds unverändert zu lassen.|
|**Ausfüllen**|Um die aktive Farbauswahl mit dem Bild zu verschmelzen, wählen Sie einfach den Bereich aus, der gefüllt werden soll.<br /><br /> Wenn das Bild mit der aktiven Farbauswahl (einschließlich des Werts des Alphakanals) überschrieben werden soll, halten Sie die **UMSCHALTTASTE** gedrückt, und wählen Sie dann den zu füllenden Bereich aus.|

### <a name="image-properties"></a>Image-Eigenschaften

Über das Fenster **Eigenschaften** können Sie verschiedene Eigenschaften des Bilds festlegen. Sie können beispielsweise die Breite und Höhe festlegen, um die Größe des Bilds zu ändern.

In der folgenden Tabelle werden die Bildeigenschaften beschrieben:

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|Breite|Die Breite des Bilds.|
|Höhe|Die Höhe des Bilds.|
|Bits pro Pixel|Die Anzahl der Bits, die jedes Pixel darstellen. Der Wert dieser Eigenschaft hängt vom **Farbformat** des Bilds ab.|
|Transparente Auswahl|**TRUE**, um die Auswahlebene mit dem Hauptbild basierend auf dem Alphawert der Auswahlebene zu verschmelzen; andernfalls **FALSE**. Dieses Element ist nur verfügbar für Bilder, die Alpha unterstützen.|
|Format|Das Farbformat des Bilds. Abhängig vom Bildformat können viele verschiedene Farbenformate angegeben werden. Das Farbformat definiert die Anzahl und Art der Farbkanäle, die im Bild enthalten sind, und auch die Größe und die Codierung der verschiedenen Kanäle.|
|Mip-Ebene|Die aktive MIP-Ebene. Dieses Element ist nur für Texturen mit MIP-Ebenen verfügbar.|
|Anzahl der Mip-Ebenen|Die Gesamtanzahl der MIP-Ebenen im Bild. Dieses Element ist nur für Texturen mit MIP-Ebenen verfügbar.|
|Anzahl der Frames|Die Gesamtanzahl der Frames im Bild. Dieses Element ist nur für Bilder verfügbar, die Texturarrays unterstützen.|
|Frame|Der aktuelle Frame. Nur der erste Frame kann angezeigt werden, alle anderen Frames gehen beim Speichern des Bilds verloren.|
|Anzahl der Tiefensegmente|Die Gesamtanzahl der Tiefensegmente im Bild. Dieses Element ist nur für Bilder nur verfügbar, die Umfangstexturen unterstützen.|
|Tiefensegment|Das aktuelle Tiefensegment. Nur das erste Tiefensegment kann angezeigt werden, alle anderen Segmente gehen beim Speichern des Bilds verloren.|

> [!NOTE]
> Die Eigenschaft **Drehen um** kann auf alle Tools und ausgewählte Bereiche angewendet werden und wird daher immer zusammen mit anderen Tooleigenschaften am unteren Rand des Fensters **Eigenschaften** angezeigt. **Drehen um** wird immer angezeigt, da das gesamte Bild implizit ausgewählt ist, wenn keine andere Auswahl oder kein aktives Tool vorhanden ist. Weitere Informationen zur Eigenschaft **Drehen um** finden Sie unter [Tooleigenschaften](#tool -properties).

### <a name="resize-images"></a>Ändern der Größe von Bildern

Es gibt die folgenden beiden Möglichkeiten, die Größe eines Bilds zu ändern. In beiden Fällen verwendet die **Bildbearbeitung** eine bilineare Interpolation, um das Bild neu zu berechnen.

- Geben Sie im Fenster **Eigenschaften** die neuen Werte für die Eigenschaften **Breite** und **Höhe** an.

- Wählen Sie das gesamte Bild aus, und ändern Sie die Größe des Bilds mithilfe der Rahmenmarker.

### <a name="selected-regions"></a>Ausgewählte Bereiche

Durch eine Auswahl in der **Bildbearbeitung** werden aktive Bildbereiche festgelegt. Diese werden von Tools und Transformationen beeinflusst. Wenn eine aktive Auswahl vorhanden ist, werden Bereiche außerhalb des ausgewählten Bereichs von den meisten Tools und Transformationen nicht beeinflusst. Gibt es keine aktive Auswahl, ist das gesamte Bild aktiv.

Die meisten Tools, wie z.B. **Pencil** (Bleistift), **Pinsel**, **Airbrush**, **Füllung**, **Radierer** und 2D-Primitive sowie Transformationen, z.B. **Drehen**, **Trim** (Zuschneiden), **Farben umkehren**, **Horizontal spiegeln** und **Vertikal spiegeln**, werden durch die aktive Auswahl eingeschränkt oder definiert. Einige Tools wie **Pipette** und **Text** sowie Transformationen wie **MIPS generieren** werden hingegen nicht von der aktiven Auswahl beeinflusst. Diese Tools funktionieren so, als würde das gesamte Bild der aktiven Auswahl entsprechen.

Beim Auswählen eines Bereichs können Sie die **UMSCHALTTASTE** gedrückt halten, um einen rechteckigen Teilbereich auszuwählen. Andernfalls wird die Auswahl nicht eingeschränkt.

#### <a name="resize-selections"></a>Ändern der Größe von Auswahlen

Nachdem Sie einen Bereich ausgewählt haben, können Sie dessen Größe oder die Größe des Bildinhalts ändern, indem Sie die Größe des Auswahlmarkers ändern. Beim Ändern der Größe des ausgewählten Bereichs können Sie die folgenden Zusatztasten verwenden, um das Verhalten des ausgewählten Bereichs zu ändern:

**STRG-TASTE:** Kopiert den Inhalt des ausgewählten Bereichs, bevor die Größe geändert wird. Belässt das Originalbild unverändert, während die Größe der Kopie geändert wird.

**UMSCHALTTASTE:** Passt die Größe des ausgewählten Bereichs relativ zur ursprünglichen Größe an.

**ALT-TASTE:** Ändert die Größe des ausgewählten Bereichs. Das Bild bleibt unverändert.

In der folgenden Tabelle werden die gültigen Zusatztasten beschrieben:

|STRG|UMSCHALTTASTE|ALT|Beschreibung|
|----------|-----------|---------|-----------------|
||||Ändert die Größe des Inhalts des ausgewählten Bereichs.|
||**Shift**||Ändert proportional die Größe des Inhalts des ausgewählten Bereichs.|
|||**Alt**|Ändert die Größe des ausgewählten Bereichs. Dadurch wird ein neuer Auswahlbereich definiert.|
||**Shift**|**Alt**|Ändert die Größe des ausgewählten Bereichs proportional. Dadurch wird ein neuer Auswahlbereich definiert.|
|**Ctrl**|||Kopiert und ändert dann die Größe des Inhalts des ausgewählten Bereichs.|
|**Ctrl**|**Shift**||Kopiert und ändert dann die Größe des Inhalts des ausgewählten Bereichs proportional.|

### <a name="tool-properties"></a>Tooleigenschaften

Wenn ein Tool ausgewählt ist, können Sie über das Fenster **Eigenschaften** angeben, wie es sich auf das Bild auswirken soll. Sie können z.B. die Breite des **Zeichenstift**-Tools oder die Farbe des **Pinsel**-Tools festlegen.

Sie können eine Vordergrundfarbe und eine Hintergrundfarbe festlegen. Beide unterstützen einen Alphakanal, um benutzerdefinierte Deckkraft bereitzustellen. Die Einstellungen gelten für alle Werkzeuge. Wenn Sie eine Maus verwenden, entspricht die linke Maustaste der Vordergrundfarbe und die rechte Maustaste der Hintergrundfarbe.

In der folgenden Tabelle werden die Tooleigenschaften beschrieben:

|Tool|Eigenschaften|
|----------|----------------|
|Alle Tools und Auswahlmöglichkeiten|**Drehen um**<br /> Definiert, um wie viel Grad die Auswahl oder der Tooleffekt im Uhrzeigersinn gedreht wird.|
|**Zeichenstift**, **Pinsel**, **Airbrush**, **Radierer**|**Stärke**<br /> Legt die Größe des Bereichs fest, der vom Werkzeug beeinflusst wird.|
|**Text**|**Antialiasing**<br /> Zeichnet Text, der über Ränder mit Antialiasing verfügt. Dadurch wird Text weicher dargestellt.<br /><br /> **Wert**<br /> Der zu zeichnende Text.<br /><br /> **Schriftart**<br /> Die Schriftart zum Zeichnen des Texts.<br /><br /> **Größe**<br /> Die Größe des Texts.<br /><br /> **Fett**<br /> Formatiert die Schrift fett.<br /><br /> **Kursiv**<br /> Formatiert die Schrift kursiv.<br /><br /> **Unterstrichen**<br /> Formatiert die Schrift unterstrichen.|
|**2D-Primitiv**|**Antialiasing**<br /> Zeichnet Primitive, die über Ränder mit Antialiasing verfügen. Dadurch werden sie weicher dargestellt.<br /><br /> **Stärke**<br /> Legt die Stärke der Linie fest, die die Begrenzung des Primitivs bildet.<br /><br /> **Radius X**<br /> (Nur abgerundetes Rechteck) Legt den Rundungsradius für die oberen und unteren Kanten des Primitivs fest.<br /><br /> **Radius Y**<br /> (Nur abgerundetes Rechteck) Legt den Rundungsradius für die linken und rechten Kanten des Primitivs fest.|
|**Zeichenstift**, **Pinsel**, **Airbrush**, **2D-Primitiv**|**Channels**<br /> Aktiviert oder deaktiviert bestimmte Farbkanäle für die Anzeige und das Zeichnen. Wenn **Ansicht** für einen bestimmten Farbkanal festgelegt wird, ist dieser Kanal im Bild sichtbar, andernfalls ist er nicht sichtbar. Wenn **Zeichnen** für einen bestimmten Farbkanal festgelegt wird, ist dieser Kanal von Zeichenvorgängen betroffen, andernfalls nicht.|
|**Stabsauswahl**, **Füllen**|**Toleranz**<br /> Definiert den maximalen Unterschied zwischen benachbarten Farben, innerhalb dessen sie als ähnlich betrachtet werden, sodass weniger oder mehr ähnliche Farben einen Teil des betroffenen oder ausgewählten Bereichs ausmachen. Standardmäßig lautet der Wert 32. Das bedeutet, dass benachbarte Pixel in 32 Schatten (heller oder dunkler) der ursprünglichen Farbe als Teil des Bereichs betrachtet werden.|

## <a name="keyboard-shortcuts"></a>Tastenkombinationen

|Get-Help|Tastenkombinationen|
|-------------| - |
|In den Modus **Auswählen** wechseln|**S**|
|In den Modus **Zoom** wechseln|**Z**|
|In den Modus **Schwenken** wechseln|**K**|
|Alles auswählen|**STRG**+**A**|
|Die aktuelle Auswahl löschen|**Löschen**|
|Brechen Sie die aktuelle Auswahl ab.|**ESC** (ESCAPE)|
|Vergrößern|**STRG**+**Mausrad vorwärts**<br /><br /> **STRG**+**BildAuf**<br /><br /> Pluszeichen ( **+** )|
|Verkleinern|**STRG**-**Mausrad rückwärts**<br /><br /> **STRG**-**BildAb**<br /><br /> Minuszeichen ( **-** )|
|Bild nach oben schwenken|**Mausrad rückwärts**<br /><br /> **BildAb**|
|Bild nach unten schwenken|**Mausrad vorwärts**<br /><br /> **BildAuf**|
|Bild nach links schwenken|**UMSCHALTTASTE**+**Mausrad rückwärts**<br /><br /> **Mausrad links**<br /><br /> **UMSCHALTTASTE**+**BildAb**|
|Bild nach rechts schwenken|**UMSCHALTTASTE**+**Mausrad vorwärts**<br /><br /> **Mausrad rechts**<br /><br /> **UMSCHALTTASTE**+**BildAuf**|
|Originalgröße anzeigen|**STRG**+**0** (null)|
|Bild an Fenster anpassen|**STRG**+**G**, **STRG**+**F**|
|Bildbreite an Fenster anpassen|**STRG**+**G**, **STRG**+**I**|
|Raster umschalten|**STRG**+**G**, **STRG**+**G**|
|Bild auf aktuelle Auswahl zuschneiden|**STRG**+**G**, **STRG**+**C**|
|Nächste MIP-Ebene (mehr Detail) anzeigen|**STRG**+**G**, **STRG**+**6**|
|Vorherige MIP-Ebene (weniger Detail) anzeigen|**STRG**+**G**, **STRG**+**7**|
|Roten Farbkanal ein-/ausschalten|**STRG**+**G**, **STRG**+**1**|
|Grünen Farbkanal ein-/ausschalten|**STRG**+**G**, **STRG**+**2**|
|Blauen Farbkanal ein-/ausschalten|**STRG**+**G**, **STRG**+**3**|
|Alphakanal (Transparenz) ein-/ausschalten|**STRG**+**G**, **STRG**+**4**|
|Alphaschachbrettmuster ein-/ausschalten|**STRG**+**G**, **STRG**+**B**|
|Zum unregelmäßigen Auswahlwerkzeug wechseln|**L**|
|Zum Stabsauswahlwerkzeug wechseln|**M**|
|Zum Stiftwerkzeug wechseln|**P**|
|Zum Pinselwerkzeug wechseln|**B**|
|Zum Füllwerkzeug wechseln|**F**|
|Zum Radiererwerkzeug wechseln|**E**|
|Zum nächsten Werkzeug wechseln|**T**|
|Zum Farbauswahlwerkzeug (Formatpipette) wechseln|**I**|
|Aktive Auswahl mit Inhalt verschieben.|**Pfeiltasten**|
|Größe der aktiven Auswahl mit Inhalt ändern.|**STRG**+**Pfeiltasten**|
|Aktive Auswahl ohne Inhalt verschieben.|**UMSCHALTTASTE**+**Pfeiltasten**|
|Größe der aktiven Auswahl ohne Inhalt ändern.|**UMSCHALTTASTE**+**STRG**+**Pfeiltasten**|
|Aktuelle Ebene bestätigen|**Return**|
|Stärke des Werkzeugs verringern|**[**|
|Stärke des Werkzeugs erhöhen|**]**|

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Arbeiten mit 3D-Objekten für Spiele und Apps](../designers/working-with-3-d-assets-for-games-and-apps.md)|Bietet eine Übersicht über die Visual Studio-Tools, die Sie bei der Arbeit mit Grafikressourcen wie Texturen und Bildern, 3D-Modellen und Shadereffekten verwenden können.|
|[Modell-Editor](../designers/model-editor.md)|In diesem Artikel wird beschrieben, wie sich der Modell-Editor von Visual Studio für die Arbeit mit 3D-Modellen einsetzen lässt.|
|[Shader-Designer](../designers/shader-designer.md)|Beschreibt die Verwendung des Shader-Designers von Visual Studio zur Arbeit mit Shadern.|
