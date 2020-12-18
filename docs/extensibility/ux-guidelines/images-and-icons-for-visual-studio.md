---
title: Bilder und Symbole für Visual Studio | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Entwurfskonzepte der Bilder und Symbole für Visual Studio.
ms.date: 04/26/2017
ms.topic: overview
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f29fd0a69ceafa33c00593b67f6775a723780c26
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668650"
---
# <a name="images-and-icons-for-visual-studio"></a>Bilder und Symbole für Visual Studio
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a> Verwendung von Bildern in Visual Studio
 Bevor Sie selbst Grafiken erstellen, sollten Sie die mehr als 1.000 Bilder in Erwägung ziehen, die in der [Visual Studio-Bildbibliothek](https://www.microsoft.com/download/details.aspx?id=35825) zur Verfügung gestellt werden.

### <a name="types-of-images"></a>Arten von Bildern

- **Symbole:** Hierbei handelt es sich um kleine Bilder, die in Befehlen, Hierarchien, Vorlagen und mehr angezeigt werden. Die in Visual Studio verwendete Standardsymbolgröße ist 16x16 mit dem Dateiformat PNG. Vom Bilddienst erstellte Symbole generieren automatisch das XAML-Format für HDPI-Unterstützung.

    > [!NOTE]
    > Bilder werden zwar im Menüsystem verwendet, jedoch sollten Sie nicht für jeden Befehl ein Symbol erstellen. Informationen darüber, ob Sie einem Befehl ein Symbol zuweisen sollten, finden Sie unter [Menüs und Befehle für Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

- **Miniaturbilder:** Diese Bilder werden im Vorschaubereich eines Dialogfelds verwendet, z. B. im Dialogfeld „Neues Projekt“.

- **Dialogfeldbilder:** Diese Bilder werden in Dialogfeldern oder Assistenten angezeigt und fungieren entweder als beschreibende Grafiken oder Nachrichtenindikatoren. Verwenden Sie diese Bilder selten und nur bei Bedarf, um ein schwieriges Konzept zu veranschaulichen oder die Aufmerksamkeit des Benutzers auf etwas zu lenken (Warnungen).

- **Animierte Bilder:** Diese Bilder werden in Fortschrittsindikatoren, Statusleisten und Dialogfeldern zu Vorgängen verwendet.

- **Cursor:** Diese Bilder werden verwendet, um mithilfe des Mauszeigers anzugeben, ob ein Vorgang zulässig ist, wo ein Objekt gelöscht werden kann und mehr.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a> Symbolentwurf

### <a name="overview"></a>Übersicht
 Visual Studio nutzt moderne Symbole mit einer sauberen Geometrie und einem 50/50-Gleichgewicht aus positiven/negativ Kontrast (hell/dunkel). Außerdem werden direkte und leicht verständliche Metaphern verwendet. Zu den wichtigen Aspekten des Symbolentwurfs gehören Klarheit, Vereinfachung und Kontext.

- **Klarheit:** Konzentrieren Sie sich auf die zugrunde liegende Bedeutung und Individualität des Symbols.

- **Vereinfachung:** Reduzieren Sie das Symbol auf die Kernbedeutung, versuchen Sie, nur die notwendigen Elemente zu verwenden, um die Bedeutung zu verbildlichen.

- **Kontext:** Berücksichtigen Sie alle Aspekte der Rolle eines Symbols während der Konzeptionierung. Dies ist insbesondere bei der Auswahl der Elemente wichtig, die die Bedeutung des Symbols bilden.

  Beim Entwerfen von Symbolen gibt es einige Punkte, die Sie vermeiden sollten:

- Verwenden Sie keine Symbole, die für Benutzeroberflächenelemente stehen, es sei denn, Sie haben guten Grund dazu. Wählen Sie einen abstrakteren oder symbolischen Ansatz, wenn das Benutzeroberflächenelement weder gängig noch offensichtlich oder eindeutig ist.

- Verwenden Sie gängige Elemente wie Dokumente, Ordner, Pfeile und Lupen nicht übermäßig. Verwenden Sie solche Elemente nur, wenn sie für die Bedeutung des Symbols unerlässlich sind. Beispielsweise sollte die nach rechts ausgerichteten Lupen nur für Suchvorgänge verwendet werden.

- Obwohl einige alte Symbolelemente die Verwendung von Perspektiven beibehalten, sollten Sie keine neuen Symbole mit Perspektive erstellen, es sei denn, die Bedeutung des Elements ist andernfalls undeutlich.

- Packen Sie nicht zu viele Informationen in ein Symbol. Ein einfaches Bild, das ein leicht zu erkennendes Symbol darstellt, ist viel nützlicher als ein übermäßig komplexes Bild. Ein Symbol kann nicht alle Informationen enthalten.

### <a name="icon-creation"></a>Symbolerstellung

#### <a name="concept-development"></a>Konzeptionierung
 Visual Studio verfügt über eine Vielzahl an Symboltypen in der Benutzeroberfläche. Berücksichtigen die Art des Symbols während der Entwicklung. Verwenden Sie keine unklaren oder ungewöhnlichen Benutzeroberflächenobjekte für Ihre Symbolelemente. Entscheiden Sie sich in diesen Fällen für die symbolische Bedeutung wie im unten gezeigten Symbol für Smarttags. Beachten Sie, dass die Bedeutung des abstrakten Etiketts auf der linken Seite offensichtlicher als die undeutliche, auf der Benutzeroberfläche basierende Version rechts ist:

|**Korrekte Verwendung symbolischer Bilder**|**Falsche Verwendung symbolischer Bilder**|
|-|-|
|![Symbol für richtiges Smarttag](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Symbol für falsches Smarttag](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Es gibt Fälle, in denen herkömmliche, einfach erkennbare Benutzeroberflächenelemente sich für Symbole eignen. „Fenster hinzufügen“ ist ein Beispiel hierfür:

|**Korrekte Verwendung eines Benutzeroberflächenelements für ein Symbol**|**Falsche Verwendung eines Benutzeroberflächenelements für ein Symbol**|
|-|-|
|![Richtiges Symbol zum Hinzufügen von Fenstern](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Falsches Symbol zum Hinzufügen von Fenstern](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Verwenden Sie kein Dokumentsymbol als Basiselement, es sei denn, es ist für die Bedeutung des Symbols wichtig. Ohne das Dokumentelement für „Dokument hinzufügen“ (siehe unten) geht die Bedeutung verloren. Für eine Funktion wie „Aktualisieren“ ist das Dokumentelement jedoch nicht für die Bedeutung notwendig.

|**Korrekte Verwendung des Dokumentsymbols**|**Falsche Verwendung des Dokumentsymbols**|
|-|-|
|![Richtiges Dokumentsymbol](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Falsches Dokumentsymbol](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 Das Konzept von „Anzeigen“ sollte mit einem Symbol dargestellt werden, das am besten veranschaulicht, was angezeigt wird. „Alle Dateien anzeigen“ ist ein gutes Beispiel hierfür. Eine Vergrößerungsmetapher kann bei Bedarf dazu verwenden werden, das Konzept einer „Ansicht“ zu verdeutlichen. Dies wird im Beispiel „Ressourcenansicht“ veranschaulicht.

|**„Anzeigen“**|**„Ansicht“**|
|-|-|
|![Symbol "Anzeigen"](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Symbol "Ansicht"](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 Das nach rechts zeigende Lupensymbol sollte nur für Suchvorgänge verwendet werden. Die nach links zeigende Variante mit einem Plus- oder Minuszeichen sollte nur für Funktionen zum Vergrößern und Verkleinern verwendet werden.

|**„Suche“**|**„Zoomen“**|
|-|-|
|![Suchsymbol](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Symbol "Zoom"](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 Verwenden Sie für Strukturansichten nicht gleichzeitig ein Ordnersymbol und einen Modifizierer. Verwenden Sie nach Möglichkeit nur den Modifizierer.

|**Richtige Strukturansichtssymbole**|**Falsche Strukturansichtssymbole**|
|-|-|
|![Richtiges Strukturansichtssymbol &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![Richtiges Strukturansichtssymbol &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Falsches Strukturansichtssymbol &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![Falsches Strukturansichtssymbol &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Informationen zum Stil

#### <a name="layout"></a>Layout
 Stapeln Sie Elemente für 16x16-Standardsymbole wie im Folgenden gezeigt:

 ![Layoutstack für 16x16-Symbole](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Layoutstack für 16x16-Symbole

 Elemente für Statusbenachrichtigungen eignen sich besser als eigenständige Symbole. Es gibt jedoch Kontexte, in denen eine Benachrichtigung auf das Basiselement gestapelt werden sollte, z. B. das Symbol „Aufgabe abgeschlossen“:

 ![Eigenständige Benachrichtigungen in Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Eigenständige Benachrichtigungssymbole

 ![Symbol für abgeschlossene Aufgabe](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Symbol für abgeschlossene Aufgabe

 Bei Projektsymbolen handelt es sich in der Regel um ICO-Dateien, die mehrere Größen enthalten. Die meisten 16x16-Symbole enthalten dieselben Elemente. Die 32x32-Versionen sind detailreicher und umfassen in geeigneten Fällen den Projekttyp.

 ![Projektsymbole in Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />16x16- und 32x32-Symbole für VB-Windows-Steuerelementbibliothek-Projekte

 Zentrieren Sie das Symbol im Pixelrahmen. Wenn das nicht möglich ist, richten Sie das Symbol am oberen und/oder rechten Rand des Rahmens aus.

 ![Innerhalb des Pixelframes zentriertes Symbol](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Innerhalb des Pixelframes zentriertes Symbol

 ![Am Pixelframe oben rechts ausgerichtetes Symbol](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Oben rechts am Rahmen ausgerichtetes Symbol

 ![Am Pixelframe oben rechts ausgerichtetes und zentriertes Symbol](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Am oberen Rand des Rahmens ausgerichtetes und zentriertes Symbol

 Zum Erzielen einer idealen Ausrichtung und eines Gleichgewichts, sollten Sie vermeiden, das Grundelement eines Symbols mit Aktionsglyphen zu verdecken. Platzieren Sie die Glyphe in die obere linke Ecke das Basiselements. Achten Sie auf die Ausrichtung und das Gleichgewicht des Symbols, wenn Sie ein zusätzliches Element hinzufügen.

|**Richtige Ausrichtung und Gleichgewicht**|**Falsche Ausrichtung und Gleichgewicht**|
|-|-|
|![Richtige Symbolverteilung und -ausrichtung](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Falsche Symbolverteilung und -ausrichtung](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Stellen Sie sicher, dass Symbole, die die gleichen Elemente nutzen und in Gruppen verwendet werden, die gleichen Größen aufweisen. Beachten Sie, dass der Kreis und der Pfeil bei den fehlerhaften Beispielen zu groß sind und nicht übereinstimmen.

|**Richtige Gleichheit der Größen**|**Fehlende Gleichheit der Größen**|
|-|-|
|![Richtige Symbolgröße und -parität](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Falsche Symbolgröße und -parität](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Nutzen Sie konsistente Linien und visuelle Gewichtungen. Vergleichen Sie das Symbol, das Sie erstellen, mit anderen Symbolen. Verwenden Sie nie den gesamten 16x16-Rahmen, verwenden Sie stattdessen 15x15 oder kleinere Flächen. Das Verhältnis von heller zu dunkler Fläche sollte 50/50 sein.

|**Richtiges Verhältnis**|**Falsches Verhältnis**|
|-|-|
|![Richtige optische Gewichtung für Symbole &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Richtige optische Gewichtung für Symbole &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Richtige optische Gewichtung für Symbole &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Falsche optische Gewichtung für Symbole](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Verwenden Sie einfache, vergleichbare Formen und komplementäre Winkel, um Ihre Elemente zu erstellen, ohne die Elementintegrität zu vernachlässigen. Verwenden Sie nach Möglichkeit Winkel von 45° oder 90°.

 ![Richtige Symbolwinkel](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspektive
 Das Symbol sollte klar und verständlich sein. Verwenden Sie Perspektiven und Lichtquellen nur, wenn es erforderlich ist. Zwar sollten Sie Perspektiven für Symbolelemente vermeiden, jedoch sind manche Elemente ohne Perspektive nicht erkennbar. In solchen Fällen unterstützt eine stilisierte Perspektive die Klarheit des Elements.

 ![3-Punkt-Perspektive](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />3-Punkt-Perspektive

 ![1-Punkt-Perspektive](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />1-Punkt-Perspektive

 Die meisten Elemente sollten nach rechts zeigen oder ausgerichtet sein:

 ![Symbole rechts angeschrägt](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Verwenden Sie Lichtquellen nur, wenn Sie einem Objekt dadurch die erforderliche Klarheit verleihen.

|**Richtige Verwendung von Lichtquellen**|**Falsche Verwendung von Lichtquellen**|
|-|-|
|![Richtige Lichtquellen für Symbole](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Falsche Lichtquellen für Symbole](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Verwenden Sie Konturen nur, um die Lesbarkeit zu verbessern oder die Bedeutung zu verdeutlichen. Das Verhältnis von heller zu dunkler Fläche sollte 50/50 sein.

|**Richtige Verwendung von Konturen**|**Falsche Verwendung von Konturen**|
|-|-|
|![Richtige Konturen](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Falsche Konturen](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Symboltypen
 **Shell- und Befehlsleistensymbole** bestehen aus nicht mehr als drei der folgenden Elemente: ein Basiselement, ein Modifizierer, eine Aktion und ein Statuselement.

 ![Beispiele für Shell- und Befehlsleistensymbole](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Beispiele für Shell- und Befehlsleistensymbole

 **Toolfenster-/Befehlsleistensymbole** bestehen aus nicht mehr als drei der folgenden Elemente: ein Basiselement, ein Modifizierer, eine Aktion und ein Statuselement.

 ![Beispiele für Toolfenster-/Befehlsleistensymbole](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Beispiele für Toolfenster-/Befehlsleistensymbole

 **Strukturansichtssymbole zur Begriffserklärung** bestehen aus nicht mehr als drei der folgenden Elemente: ein Basiselement, ein Modifizierer, eine Aktion und ein Statuselement.

 ![Beispiele für Strukturansichtssymbole zur Begriffserklärung](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Beispiele für Strukturansichtssymbole zur Begriffserklärung

 **Symbole für die zustandsbasierte Wertklassifizierung** stehen in den folgenden Zuständen zur Verfügung: „aktiv“, „aktiv deaktiviert“ und „inaktiv deaktiviert“.

 ![Beispiele für Symbole für die zustandsbasierte Wertklassifizierung](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Beispiele für Symbole für die zustandsbasierte Wertklassifizierung

 **IntelliSense-Symbole** bestehen aus nicht mehr als drei der folgenden Elemente: ein Basiselement, ein Modifizierer und ein Statuselement.

 ![Beispiele für IntelliSense-Symbole](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Beispiele für IntelliSense-Symbole

 **Kleine Projektsymbole (16x16)** sollten nicht mehr als zwei Elemente enthalten: ein Basiselement und einen Modifizierer.

 ![Beispiele für kleine Projektsymbole (16x16)](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![16x16-Projektsymbol &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![16x16-Projektsymbol &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Beispiele für kleine Projektsymbole (16x16)

 **Große Projektsymbole (32x32)** bestehen aus nicht mehr als vier der folgenden Elemente: ein Basiselement, ein bis zwei Modifizierer und eine Sprachüberlagerung.

 ![Beispiele für große Projektsymbole (32x32)](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Beispiele für große Projektsymbole (32x32)

### <a name="production-details"></a>Informationen zur Produktion
 Alle neuen Benutzeroberflächenelemente sollten mit Windows Presentation Foundation (WPF) erstellt werden, und alle neuen Symbole für WPF sollten das 32-Bit-PNG-Format aufweisen. Das 24-Bit-PNG-Format ist veraltet und unterstützt die Transparenz nicht. Daher wird von diesem Format für Symbole abgeraten.

 Speichern Sie die Auflösung mit 96 DPI.

#### <a name="file-types"></a>Dateitypen

- **32-Bit-PNG:** Dies ist das bevorzugte Format für Symbole. Hierbei handelt es sich um ein Dateiformat zur verlustfreien Datenkomprimierung, das ein einzelnes Rasterbild (Pixel) speichern kann. 32-Bit-PNG-Dateien unterstützen Alphakanaltransparenz, Gammakorrektur und das Zeilensprungverfahren.

- **32-Bit-BMP:** Dies ist ein Format für Steuerelemente, die nicht für WPF vorgesehen sind. Das 32-Bit-BMP-Format ist ein RGB/A-Bildformat, ein Echtfarbenbild mit Alphakanaltransparenz. Der Alphakanal ist eine in Adobe Photoshop designierte transparente Ebene, die dann als zusätzlicher (vierter) Farbkanal in der Bitmap gespeichert wird. Während der Erstellung der Grafik wird allen 32-Bit-BMP-Dateien ein schwarzer Hintergrund hinzugefügt, um schnell einen visuellen Hinweis für die Farbtiefe bereitzustellen. Dieser schwarze Hintergrund stellt die Fläche dar, die in der Benutzeroberfläche ausgeblendet werden soll.

- **32-Bit-ICO:** Dies ist ein Format für Projektsymbole und zum Hinzufügen von Elementen. Alle ICO-Dateien sind 32-Bit-Echtfarbenbilder mit Alphakanaltransparenz (RGB/A). Da ICO-Dateien mehrere Größen und Farbtiefen speichern können, weisen Vista-Symbole oft ein ICO-Format mit Bildgrößen von 16x16, 32x32, 48x48 und 256x256 auf. Damit ICO-Dateien ordnungsgemäß in Windows Explorer angezeigt werden, müssen ICO-Dateien mit 24-Bit- und 8-Bit-Farbtiefen für jede Bildgröße gespeichert werden.

- **XAML:** Dies ist ein Format für Entwurfsoberflächen und Adorner-Elemente für Windows. XAML-Symbole sind vektorbasierte Bilddateien, die Skalierung, Rotation, Dateispeicherung und Transparenz unterstützen. XAML-Symbole werden derzeit nicht häufig in Visual Studio verwendet, jedoch werden sie aufgrund ihrer Flexibilität immer beliebter.

- **SVG**

- **24-Bit-BMP:** Dies ist ein Format für die Visual Studio-Befehlsleiste. Hierbei handelt es sich um ein Echtfarben-RGB-Bildformat. 24-Bit-BMP stellt eine Symbolkonvention dar, bei der eine leicht erkennbare transparente Ebene mit Magenta (R=255, G=0, B=255) als Transparenzfarbe erstellt wird. Im 24-Bit-BMP-Format werden alle magentafarbenen Flächen mit der Hintergrundfarbe dargestellt.

- **24-Bit-GIF:** Dies ist ein Format für die Visual Studio-Befehlsleiste. Hierbei handelt es sich um ein Echtfarben-RGB-Bildformat, das Transparenz unterstützt. GIF-Dateien werden häufig für Grafiken in Assistenten und für GIF-Animationen verwendet.

### <a name="icon-construction"></a>Symbolerstellung
 Die kleinste Symbolgröße in Visual Studio ist 16x16. Die größte häufig verwendete Symbolgröße ist 32x32. Denken Sie daran, nicht den gesamten 16x16-, 24x24- oder 32x32-Rahmen zu füllen, wenn Sie ein Symbol entwerfen. Eine erkennbare, einheitliche Symbolerstellung ist entscheidend dafür, dass Benutzer die Symbole erkennen. Halten Sie sich beim Erstellen von Symbolen an die folgenden Richtlinien.

- Symbole sollten klar, verständlich und konsistent sein.

- Es ist besser, die Statusbenachrichtigungselemente als einzelne Symbole zu verwenden, anstatt diese auf ein Basiselement eines Symbols zu stapeln. In gewissen Kontexten erfordert die Benutzeroberfläche möglicherweise, dass das Statuselement mit einem Basiselement verknüpft wird.

- Bei Projektsymbolen handelt es sich in der Regel um ICO-Dateien, die mehrere Größen enthalten. Nur die 16x16-, 24x24- und 32x32-Symbole werden aktualisiert. Die meisten 16x16- und 24x24-Symbole enthalten dieselben Elemente. Die 32x32-Versionen sind detailreicher und umfassen in geeigneten Fällen sie Sprache für das Projekt.

- Für 32x32-Symbole verfügen die Basiselemente in der Regel eine Linienstärke von zwei Pixeln. Eine Linienstärke von einem oder zwei Pixeln kann für detaillierte Elemente verwendet werden. Entscheiden Sie nach bestem gewissen, was sich am besten eignet.

- Es sollte mindestens ein Abstand von einem Pixel zwischen Elementen für 16x16- und 24x24-Symbole bestehen. Verwenden Sie für 32x32-Symbole einen Abstand von zwei Pixeln zwischen Elementen sowie zwischen dem Modifizierer und dem Basiselement.

  ![Elementabstand für Symbole der Größen 16x16, 24x24 und 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Elementabstand für Symbole der Größen 16x16, 24x24 und 32x32

#### <a name="color-and-accessibility"></a>Farben und Barrierefreiheit
 Gemäß der Konformitätsrichtlinien von Visual Studio ist erforderlich, dass alle Symbole im Produkt die Barrierefreiheitsanforderungen für Farben und Kontraste einhalten. Dies wird durch eine Inversion des Symbols erzielt. Beim Entwerfen des Symbols sollten Sie also berücksichtigen, dass es im Produkt programmgesteuert invertiert wird.

 Weitere Informationen zur Verwendung von Farben in Symbolen für Visual Studio finden Sie unter [Verwenden von Farben in Bildern](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a> Verwenden von Farben in Bildern

### <a name="overview"></a>Übersicht
 Symbole in Visual Studio sind hauptsächlich monochromatisch. Die Farbe soll spezifische Informationen vermitteln und gilt nie nur zur Dekoration. Farbe wird für folgende Zwecke verwendet:

- Zum Angeben einer Aktion

- Zum Benachrichtigen des Benutzers über eine Statusbenachrichtigung

- Zum Angeben der Sprache

- Zum Unterscheiden von Elementen in IntelliSense

### <a name="accessibility"></a>Zugriff
 Gemäß der Konformitätsrichtlinien von Visual Studio ist erforderlich, dass alle zum Produkt hinzugefügten Symbole die Barrierefreiheitsanforderungen für Farben und Kontraste einhalten. Die Farben in der visuellen Sprachpalette wurden getestet und erfüllen diese Anforderungen.

#### <a name="color-inversion-for-dark-themes"></a>Farbinversion für dunkle Designs
 Damit Symbole mit dem richtigen Kontrastverhältnis im dunklen Design von Visual Studio angezeigt werden, wird eine programmgesteuerte Inversion angewendet. Die in diesem Handbuch veranschaulichten Farben wurden zum Teil aus dem Grund ausgewählt, dass sie ordnungsgemäß invertiert werden. Begrenzen Sie die Farben, die Sie verwenden, auf diese Palette. Andernfalls können Sie unvorhersehbare Ergebnisse erhalten, wenn die Inversion angewendet wird.

 ![Beispiele für Symbole mit invertierten Farben](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Beispiele für Symbole mit invertierten Farben

### <a name="base-palette"></a>Basispalette
 Alle Standardsymbole enthalten drei Grundfarben. Symbole enthalten mit Ausnahme von ein oder zwei Symbolen für 3D-Tools keine Farbverläufe oder Schlagschatten.

|Verwendung|Name|Helligkeit (Helles Design)|Muster|Beispiel|
|-----------|----------|---------------------------|------------|-------------|
|Hintergrund/Dunkel|VS BG|424242 / 66,66,66|![Muster 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Beispiel für Basispalette](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Vordergrund/Hell|VS FG|F0EFF1 / 240,239,241|![Muster F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Outline|VS Out|F6F6F6 / 246,246,246|![Muster F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Zusätzlich zu den Grundfarben kann jedes Symbol eine zusätzliche Farbe aus der erweiterten Palette enthalten.

### <a name="extended-palette"></a>Erweiterte Palette

#### <a name="action-modifiers"></a>Aktionsmodifizierer
 Die vier unten gezeigten Farben geben die Arten von Aktionen an, die von Aktionsmodifizierern benötigt werden:

|Verwendung|Name|Helligkeit (alle Designs)|Muster|
|-----------|----------|--------------------------|------------|
|Positiv|VS Action Green|388A34 / 56,138,52|![Muster 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Negativ|VS Action Red|A1260D / 161,38,13|![Muster A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutral|VS Action Blue|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Erstellen/Neu|VS Action Orange|C27D1A / 194,156,26|![Muster C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Beispiele
 Grün wird für positive Aktionsmodifizierer wie „Hinzufügen“, „Ausführen“, „Abspielen“ und „Überprüfen“ verwendet.

|Ausführen|Abfrage ausführen|Alle Schritte wiedergeben|Steuerelement hinzufügen|
|-|-|-|-|
|![Symbol "Ausführen"](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Symbol "Abfrage ausführen"](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")|![Symbol "Alle Schritte wiedergeben"](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")|![Symbol "Steuerelement hinzufügen"](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")|

 Rot wird für negative Aktionsmodifizierer wie „Löschen“, „Beenden“, „Abbrechen“ und „Schließen“ verwendet.

|Löschen der Beziehung|Spalte löschen|Abfrage beenden|Verbindung offline|
|-|-|-|-|
|![Symbol "Beziehung löschen"](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")|![Symbole "Spalte löschen"](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")|![Symbol "Abfrage beenden"](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")|![Symbol "Verbindung offline"](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")|

 Blau wird für neutrale Aktionsmodifizierer verwendet, die in den meisten Fällen mit Pfeilen dargestellt werden, z. B. „Öffnen“, „Weiter“, „Zurück“, „Importieren“ und „Exportieren“.

|Gehe zu Feld|Im Batch einchecken|Adress-Editor|Zuordnungs-Editor|
|-|-|-|-|
|![Symbol "Gehe zu Feld"](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")|![Symbol „Im Batch einchecken“](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")|![Symbol "Adress-Editor"](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")|![Symbol "Zuordnungs-Editor"](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")|

 Dunkelgold wird hauptsächlich für den Modifizierer „Neu“ verwendet.

|Neues Projekt|Neues Diagramm erstellen|Neuer Komponententest|Neues Listenelement|
|-|-|-|-|
|![Symbol "Neues Projekt"](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")|![Symbol "Neues Diagramm erstellen"](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")|![Symbol "Neuer Komponententest"](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")|![Symbol "Neues Listenelement"](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")|

#### <a name="special-cases"></a>Spezialfälle
 In besonderen Fällen kann ein farbiger Aktionsmodifizierer unabhängig als eigenständiges Symbol verwendet werden. Die für das Symbol verwendete Farbe stellt die Aktionen dar, mit denen das Symbol in Verbindung steht. Diese Verwendung ist auf eine kleine Teilmenge von Symbolen beschränkt, einschließlich:

|Ausführen|Beenden|Löschen|Speichern|Rückwärts navigieren|
|-|-|-|-|-|
|![Symbol "Ausführen"](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Symbol „Anhalten“ (einfarbiges rotes Quadrat)](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")|![Symbol „Löschen“](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")|![Symbol „Speichern“](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")|![Symbol "Rückwärts navigieren"](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")|

### <a name="code-hierarchy-palette"></a>Codehierarchiepalette

#### <a name="folder"></a>Ordner

|Verwendung|Name|Helligkeit (alle Designs)|Muster|Beispiel|
|-----------|----------|--------------------------|------------|-------------|
|Ordner|Ordner|DCB67A / 220,182,122|![Muster DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Symbol "Ordnerfarbe"](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Visual Studio-Sprachen
 Allen gängigen in Visual Studio verfügbaren Sprachen oder Plattformen ist eine Farbe zugeordnet. Diese Farben werden für das Basissymbol oder für Sprachmodifizierer verwendet, die in der oberen rechten Ecke von zusammengesetzten Symbolen angezeigt werden.

|Verwendung|Name|Helligkeit (alle Designs)|Muster|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF Blue|0095D7 / 0,149,215|![Muster 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP Purple|9B4F96 / 155,79,150|![Muster 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS Green (VS Action Green)|388A34 / 56,138,52|![Muster 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS Red|BD1E2D / 189,30,45|![Muster BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS Purple|672878 / 103,40,120|![Muster 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS Orange|F16421 / 241,100,33|![Muster F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB Blue (VS Action Blue)|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS Orange|E04C06 / 224,76,6|![Muster E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|PY Green|879636 / 135,150,54|![Muster 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Beispiele für Symbole mit Sprachmodifizierern

|VB|C#|F#|JavaScript|Python|
|-|-|-|-|-|-|
|![Visual Basic-Symbol](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")|![C&#35;-Symbol](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")|![C&#43;&#43;-Symbol](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")|![F&#35;-Symbol](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")|![JavaScript-Symbol](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")|![Python-Symbol](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")|

|HTML|WPF|ASP|CSS|TypeScript|
|-|-|-|-|-|-|
|![HTML-Symbol](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![WPF-Symbol](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![ASP-Symbol](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![CSS-Symbol](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![TypeScript-Symbol](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 IntelliSense-Symbole nutzen eine exklusive Farbpalette. Diese Farben werden dazu verwendet, Benutzer dabei zu helfen, schnell zwischen verschiedenen Elementen in der IntelliSense-Pop-Up-Liste zu unterscheiden.

|Verwendung|Name|Helligkeit (alle Designs)|Muster|
|-----------|----------|--------------------------|------------|
|Klassen, Ereignisse|VS Action Orange|C27D1A / 194,125,26|![Muster C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Erweiterungsmethoden, Methoden, Module, Delegate|VS Action Purple|652D90 / 101,45,144|![Muster 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Felder, Enum-Elemente, Makros, Strukturen, Union-Werttypen, Operatoren, Schnittstellen|VS Action Blue|00539C / 0,83,156|![Muster 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Object|VS Action Green|388A34 / 56,138,52|![Muster 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Konstanten, Ausnahmen, Enum-Elemente, Zuordnungen, Zuordnungselemente, Namespaces, Vorlagen, Typdefinitionen|Background (VS BG)|424242 / 66,66,66|![Muster 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Beispiele für IntelliSense-Symbole

|Klasse|Privates Ereignis|Delegat|Friend-Methode|Feld|
|-|-|-|-|-|
|![Symbol für IntelliSense-Klasse](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")|![Symbol für privates IntelliSense-Ereignis](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")|![Symbol für IntelliSense-Delegat](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")|![Symbol für IntelliSense-Methode "Friend"](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")|![Feldsymbol](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")|

|Geschütztes Enum-Element|Object|Vorlage|Ausnahmeverknüpfung|
|-|-|-|-|
|![Symbol für geschütztes IntelliSense-Enum-Element](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")|![Symbol für IntelliSense-Objekt](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")|![Symbol für IntelliSense-Vorlage](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")|![Symbol für IntelliSense-Ausnahmeverknüpfung](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")|

### <a name="notifications"></a>Benachrichtigungen
 Benachrichtigungen in Visual Studio werden zum Angeben des Status verwendet. Die Farbpalette für Benachrichtigungen enthält die folgenden vier Farben, einschließlich der Optionen zum Füllen des Vordergrunds mit Schwarz oder Weiß, um Benachrichtigungen mit den folgenden Status zu definieren.

|Verwendung|Name|Helligkeit (alle Designs)|Muster|
|-----------|----------|--------------------------|------------|
|Status: Neutral|Notification Blue (VS Blue)|1BA1E2 / 27,161,226|![Muster 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Status: Positiv|Notification Green (VS Green)|339933 / 51,153,51|![Muster 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Status: Negativ|Notification Red (VS Red)|E51400 / 229,20,0|![Muster E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Status: Warnung|Notification Yellow (VS Orange)|FFCC00 / 255,204,0|![Muster FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Füllen des Vordergrunds|Notification Black (Black)|000000 / 0,0,0|![Muster &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Füllen des Vordergrunds|Notification White (White)|FFFFFF / 255,255,255|![Muster FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Beispiele für Benachrichtigungssymbole

|Warnung|Warnung|Abgeschlossen|Beenden|
|-|-|-|-|
|![Warnungssymbol](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")|![Warnungssymbol](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")|![Symbol "Abgeschlossen"](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")|![Symbol „Anhalten“ (einfarbiger roter Kreis mit einem weißen Quadrat in der Mitte)](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")|