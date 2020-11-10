---
title: Shader-Designer
description: Erfahren Sie, wie Sie mit dem Shader-Designer in Visual Studio benutzerdefinierte visuelle Effekte – auch Shader genannt – erstellen, bearbeiten und exportieren können.
ms.custom: SEO-VS-2020
ms.date: 09/21/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f932c6c02bf8b3e60487b781dd3211f6019d49c9
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134373"
---
# <a name="shader-designer"></a>Shader-Designer

Dieses Dokument beschreibt, wie Sie mit dem **Shader-Designer** in Visual Studio benutzerdefinierte visuelle Effekte, auch *Shader* genannt, erstellen, bearbeiten und exportieren können.

Sie können den **Shader-Designer** dazu verwenden, benutzerdefinierte visuelle Effekte für Spiele und Apps zu erstellen, selbst wenn Sie sich nicht mit der HLSL-Programmierung (High Level Shader Language) auskennen. Um einen Shader im **Shader-Designer** zu erstellen, legen Sie ihn als Diagramm an. Das heißt, fügen Sie der Entwurfsoberfläche *Knoten* hinzu, die Daten und Vorgänge darstellen, und verbinden Sie sie dann, um zu definieren, wie die Vorgänge die Daten verarbeiten. An jedem Vorgangsknoten wird eine Vorschau des Effekts bis zu diesem Zeitpunkt bereitgestellt, sodass Sie das Ergebnis visuell darstellen können. Daten fließen über die Knoten in Richtung eines letzten Knotens, der die Ausgabe des Shaders darstellt.

## <a name="supported-formats"></a>Unterstützte Formate

Der **Shader-Designer** unterstützt diese Shaderformate:

|Formatname|Dateierweiterung|Unterstützte Vorgänge (Anzeigen, Bearbeiten, Exportieren)|
|-----------------| - | - |
|Directed Graph Shader Language|*.dgsl*|Anzeigen, Bearbeiten|
|HLSL-Shader (Quellcode)|*.hlsl*|Exportieren|
|HLSL-Shader (Bytecode)|*.cso*|Exportieren|
|C++-Header (HLSL-Bytecode-Array)|*.h*|Exportieren|

## <a name="get-started"></a>Erste Schritte

Diese Abschnitt beschreibt, wie Sie Ihrem Visual Studio C++-Projekt einen DGSL-Shader hinzufügen und wie die ersten Schritte aussehen.

> [!NOTE]
> Die automatische Buildintegration von grafischen Elementen wie Shaderdiagrammen (DGSL-Dateien) wird nur für C++-Projekte unterstützt.

### <a name="to-add-a-dgsl-shader-to-your-project"></a>So fügen Sie einen DGSL-Shader zu Ihrem Projekt hinzu

1. Überprüfen Sie, ob die erforderliche Visual Studio-Komponente installiert ist, die Sie für die Verwendung von Grafiken benötigen. Die Komponente heißt **Bild- und 3D-Modell-Editoren**.

   Öffnen Sie für die Installation den Visual Studio-Installer, indem Sie in der Menüleiste **Tools** > **Tools und Features abrufen** auswählen und dann die Registerkarte **Einzelne Komponenten** auswählen. Wählen Sie in der Kategorie **Spiele und Grafiken** die Komponente **Bild- und 3D-Modell-Editoren** und dann **Ändern** aus.

   ![Komponente „Bild- und 3D-Modell-Editoren“](media/image-3d-model-editors-component.png)

2. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü des C++-Projekts, dem Sie den Shader hinzufügen möchten, und wählen Sie dann **Hinzufügen** > **Neues Element** aus.

3. Wählen Sie im Dialogfeld **Neues Element hinzufügen** unter **Installiert** die Option **Grafiken** und anschließend **Visual Shader-Diagramm (.dgsl)** aus.

   > [!NOTE]
   > Wenn die Kategorie **Grafiken** im Dialogfeld **Neues Element hinzufügen** nicht angezeigt wird, und die Komponente **Bild- und 3D-Modell-Editoren** installiert ist, werden grafische Elemente für Ihren Projekttyp nicht unterstützt.

4. Geben Sie den **Namen** der Shader-Datei und den **Speicherort** an, an dem sie erstellt werden soll.

5. Wählen Sie die Schaltfläche **Hinzufügen** aus.

### <a name="the-default-shader"></a>Der Standard-Shader

Jedes Mal, wenn Sie einen DGSL-Shader erstellen, startet er als minimaler Shader, der nur über einen Knoten **Punktfarbe** verfügt, der mit dem Knoten **Endgültige Farbe** verbunden ist. Obwohl dieser Shader vollständig und funktional ist, tut er nicht viel. Der erste Schritt beim Erstellen eines funktionierenden Shaders ist daher oft, den Knoten **Punktfarbe** zu löschen oder dessen Verbindung mit dem Knoten **Endgültige Farbe** zu trennen, um Platz für andere Knoten zu schaffen.

## <a name="work-with-the-shader-designer"></a>Arbeiten mit dem Shader-Designer

In den folgenden Abschnitten wird beschrieben, wie Sie den Shader-Designer für die Arbeit mit benutzerdefinierten Shadern verwenden können.

### <a name="shader-designer-toolbars"></a>Symbolleisten des Shader-Designers

Die Symbolleisten des Shader-Designers enthalten Befehle, die Sie bei der Arbeit mit DGSL-Shader-Diagrammen unterstützen.

Befehle, die den Zustand des Shader-Designers beeinflussen, finden Sie auf der Symbolleiste **Shader-Designer-Modus** im Visual Studio-Hauptfenster. Designtools und -befehle befinden sich auf der **Shader-Designer** -Symbolleiste auf der Shader-Designer-Entwurfsoberfläche.

So sieht die **Shader-Designer-Modus** -Symbolleiste aus:

![Modale Shader-Designer-Symbolleiste](../designers/media/digit-dsd-modal-toolbar.png)

In dieser Tabelle werden die Elemente der **Shader-Designer-Modus** -Symbolleiste beschrieben und in der Reihenfolge aufgelistet, in der sie auf der Symbolleiste von links nach rechts angezeigt werden:

|Element der Symbolleiste|Beschreibung|
|------------------|-----------------|
|**Auswählen**|Ermöglicht die Interaktion mit Knoten und Kanten im Diagramm. In diesem Modus können Sie Knoten auswählen und verschieben oder löschen. Zudem können Sie Kanten einrichten oder unterbrechen.|
|**Schwenken**|Ermöglicht das Bewegen eines Shader-Diagramms relativ zum Fensterrahmen. Wählen Sie zum Schwenken einen Punkt auf der Entwurfsoberfläche aus, und verschieben Sie ihn.<br /><br /> Im **Auswahl** -Modus können Sie den **Schwenken** -Modus durch Gedrückthalten der **STRG** -TASTE vorübergehend aktivieren.|
|**Zoomen**|Ermöglicht das Anzeigen von mehr oder weniger Details des Shader-Diagramms relativ zum Fensterrahmen. Wählen Sie im **Zoom** -Modus einen Punkt auf dem Bild aus, und verschieben Sie ihn zum Vergrößern nach rechts oder nach unten und zum Verkleinern nach links oder nach oben.<br /><br /> Im **Auswählen** -Modus können Sie zum Vergrößern oder Verkleinern das Mausrad verwenden. Halten Sie dazu **STRG** gedrückt.|
|**Mit Zoom anpassen**|Zeigt das gesamte Shader-Diagramm im Fensterrahmen an.|
|**Real-Time Rendering Mode** (Echtzeit-Renderingmodus)|Bei aktiviertem Rendering in Echtzeit, zeichnet Visual Studio die Entwurfsoberfläche auch dann neu, wenn keine Benutzeraktion ausgeführt wird. Ein hilfreicher Modus, bei der Arbeit mit Shadern, die sich im Laufe der Zeit ändern.|
|**Vorschau mit Kugel**|Wenn diese aktiviert ist, wird ein Modell einer Kugel für die Vorschau des Shaders verwendet. Es kann immer nur eine Vorschauform gleichzeitig aktiviert sein.|
|**Vorschau mit Würfel**|Wenn diese aktiviert ist, wird ein Modell eines Würfels für die Vorschau des Shaders verwendet. Es kann immer nur eine Vorschauform gleichzeitig aktiviert sein.|
|**Vorschau mit Zylinder**|Wenn diese aktiviert ist, wird ein Modell eines Zylinders für die Vorschau des Shaders verwendet. Es kann immer nur eine Vorschauform gleichzeitig aktiviert sein.|
|**Vorschau mit Kegel**|Wenn diese aktiviert ist, wird ein Modell eines Kegels für die Vorschau des Shaders verwendet. Es kann immer nur eine Vorschauform gleichzeitig aktiviert sein.|
|**Vorschau mit Teekanne**|Wenn diese aktiviert ist, wird ein Modell einer Teekanne für die Vorschau des Shaders verwendet. Es kann immer nur eine Vorschauform gleichzeitig aktiviert sein.|
|**Vorschau mit Ebene**|Wenn diese aktiviert ist, wird ein Modell einer Ebene für die Vorschau des Shaders verwendet. Es kann immer nur eine Vorschauform gleichzeitig aktiviert sein.|
|**Werkzeugkasten**|Zeigt die **Toolbox** entweder an oder blendet sie aus.|
|**Eigenschaften**|Zeigt das Fenster **Eigenschaften** entweder an oder blendet es aus.|
|**Erweitert**|Enthält erweiterte Befehle und Optionen.<br /><br /> **Exportieren** : Ermöglicht das Exportieren eines Shaders in verschiedene Formate.<br /><br /> **Exportieren als** : Exportiert den Shader entweder als HLSL-Quellcode oder als kompilierten Shader-Bytecode. Weitere Informationen zum Exportieren von Shadern finden Sie unter [Vorgehensweise: Exportieren eines Shaders](../designers/how-to-export-a-shader.md).<br /><br /> **Grafik-Engines** : Ermöglicht die Auswahl des Renderers, der für die Anzeige der Entwurfsoberfläche verwendet wird<br /><br /> **Rendern mit D3D11** : Verwendet Direct3D 11 zum Rendern der Entwurfsoberfläche des Shader-Designers<br /><br /> **Rendern mit D3D11WARP** : Verwendet Direct3D 11 Windows Advanced Rasterization Platform (WARP) zum Rendern der Entwurfsoberfläche des Shader-Designers.<br /><br /> **Ansicht** : Ermöglicht die Auswahl zusätzlicher Informationen über den Shader-Designer.<br /><br /> **Bildfrequenz** : Wenn diese aktiviert ist, wird in der rechten oberen Ecke der Entwurfsoberfläche die Bildfrequenz angezeigt. Die Einzelbildrate ist die Anzahl von Bildern, die pro Sekunde gezeichnet werden. Diese Option ist hilfreich, wenn Sie die Option **Real-Time Rendering Mode** (Echtzeit-Renderingmodus) aktivieren.|

> [!TIP]
> Klicken Sie zum erneuten Ausführen des letzten Befehls auf die Schaltfläche **Erweitert**.

### <a name="work-with-nodes-and-connections"></a>Arbeiten mit Knoten und Verbindungen

Verwenden Sie den Modus **Auswählen** , um Knoten hinzuzufügen, zu entfernen, neu anzuordnen, zu verbinden und zu konfigurieren. So werden diese grundlegenden Vorgänge ausgeführt:

#### <a name="to-perform-basic-operations-in-select-mode"></a>Ausführen von grundlegenden Vorgängen im Modus „Auswählen“

- Gehen Sie dabei folgendermaßen vor:

  - Um einen Knoten zum Diagramm hinzuzufügen, wählen Sie diesen in der **Toolbox** aus, und verschieben Sie ihn anschließend auf die Entwurfsoberfläche.

  - Wenn Sie einen Knoten aus dem Diagramm entfernen möchten, wählen Sie ihn aus, und drücken Sie dann die **ENTF-TASTE**.

  - Um einen Knoten neu anzuordnen, wählen Sie diesen aus, und verschieben Sie ihn dann an einen neuen Speicherort.

  - Um zwei Knoten zu verbinden, verschieben Sie ein Ausgabeterminal eines Knotens in ein Eingabeterminal des anderen Knotens. Es können nur Terminals mit kompatiblen Typen verbunden werden. Eine Linie zwischen den Terminals zeigt die Verbindung.

  - Um eine Verbindung zu entfernen, wählen Sie im Kontextmenü eines der verbundenen Terminals **Zeilen umbrechen** aus.

  - Um die Eigenschaften eines Knotens zu konfigurieren, wählen Sie den Knoten aus, und geben Sie dann im Fenster **Eigenschaften** neue Werte für die Eigenschaften an.

### <a name="preview-shaders"></a>Shader (Vorschauversion)

Damit Sie verstehen, wie ein Shader in Ihrer App angezeigt wird, können Sie konfigurieren, wie der Effekt in der Vorschau angezeigt wird. Um Ihre App anzupassen, können Sie eine aus mehreren Formen zum Rendern auswählen, Texturen und andere Materialparameter konfigurieren, die Animation von zeitbasierten Effekten aktivieren und die Vorschau aus verschiedenen Perspektiven untersuchen.

#### <a name="shapes"></a>Formen

Der Shader-Designer umfasst sechs Formen (eine Kugel, einen Würfel, einen Zylinder, einen Kegel, eine Teekanne und eine Ebene), die Sie für die Vorschau Ihrer Shader verwenden können. Je nach Shader bieten Ihnen bestimmte Formen möglicherweise eine bessere Vorschau.

Wählen Sie auf der **Shader-Designer-Modi** -Symbolleiste die gewünschte Form aus.

#### <a name="textures-and-material-parameters"></a>Texturen und Materialparameter

Viele Shader greifen auf Texturen und Materialeigenschaften zurück, um ein einheitliches Aussehen für jede Art von Objekt in Ihrer App zu erstellen. Um anzuzeigen, wie der Shader in Ihrer App aussieht, können Sie die Texturen und Materialeigenschaften, die zum Rendern der Vorschau verwendet werden, so einstellen, dass sie mit den Texturen und Parametern übereinstimmen, die Sie möglicherweise in Ihrer App verwenden.

So binden Sie eine andere Textur an ein Texturregister oder bearbeiten andere Materialparameter

1. Wählen Sie im Modus **Auswählen** einen leeren Bereich auf der Entwurfsoberfläche aus. Dadurch werden im Fenster **Eigenschaften** die globalen Shader-Eigenschaften angezeigt.

2. Geben Sie im Fenster **Eigenschaften** neue Werte für die Textur- und Parametereigenschaften an, die Sie ändern möchten.

Die folgende Tabelle enthält die Shaderparameter, die Sie ändern können:

|Parameter|Eigenschaften|
|---------------|----------------|
|**Textur 1** - **Textur 8**|**Zugriff** :                             **Öffentlich** , sodass die Eigenschaft im Modell-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Dateiname** : Der vollständige Pfad der Texturdatei, die diesem Texturregister zugeordnet ist.|
|**Material (Umgebung)**|**Zugriff** :                             **Öffentlich** , sodass die Eigenschaft im Modell-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Wert** : Die diffuse Farbe des aktuellen Pixels aufgrund indirekter oder Umgebungsbeleuchtung.|
|**Material (Diffus)**|**Zugriff** : **Öffentlich** , sodass die Eigenschaft im Modell-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Wert** : Eine Farbe, die beschreibt, wie das aktuelle Pixel die direkte Beleuchtung streut.|
|**Material (Selbstleuchtend)**|**Zugriff** :                              **Öffentlich** , sodass die Eigenschaft im Modell-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Wert** : Die Farbeinwirkung des aktuellen Pixels aufgrund der selbsterzeugten Beleuchtung.|
|**Material (Glanz)**|**Zugriff** :                              **Öffentlich** , sodass die Eigenschaft im Modell-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Wert** : Eine Farbe, die beschreibt, wie das aktuelle Pixel die direkte Beleuchtung reflektiert.|
|**Material (Glanzkraft)**|**Zugriff** :                             **Öffentlich** , sodass die Eigenschaft im Modell-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Wert** : Der Exponent, mit dem die Intensität von Glanzlichtern auf dem aktuellen Pixel definiert wird.|

#### <a name="time-based-effects"></a>Zeitbasierte Effekte

Einige Shader verfügen über eine zeitbasierte Komponente, die den Effekt animiert. Um anzuzeigen, wie der Effekt in Aktion aussieht, muss die Vorschau mehrmals pro Sekunde aktualisiert werden. Standardmäßig wird die Vorschau nur aktualisiert, wenn der Shader geändert wird. Um dieses Verhalten zu ändern, sodass Sie zeitbasierte Effekte anzeigen können, müssen Sie das Echtzeit-Rendering aktivieren.

Klicken Sie auf der Shader-Designer-Symbolleiste auf **Real time Rendering** (Rendering in Echtzeit).

#### <a name="examine-the-effect"></a>Untersuchen des Ergebnisses

Viele Shader werden von Variablen wie dem Anzeigewinkel oder der direktionalen Beleuchtung beeinflusst. Um zu untersuchen, wie der Effekt reagiert, wenn sich diese Variablen ändern, können Sie die Vorschauform frei drehen und beobachten, wie sich der Shader verhält.

Halten Sie hierzu **ALT** gedrückt, wählen Sie einen beliebigen Punkt auf der Entwurfsoberfläche aus, und verschieben Sie diesen.

### <a name="export-shaders"></a>Exportieren von Shadern

Bevor Sie einen Shader in Ihrer App verwenden können, müssen Sie ihn in ein Format exportieren, das DirectX versteht.

Sie können Shader als HLSL-Quellcode oder als kompilierten Shader-Bytecode exportieren. HLSL-Quellcode wird in eine Textdatei exportiert, die über die Erweiterung *.hlsl* verfügt. Shader-Bytecode kann entweder in eine unformatierte Binärdatei exportiert werden, die über die Erweiterung *.cso* verfügt, oder in eine C++-Headerdatei ( *.h* ), die den Shader-Bytecode in ein Array codiert.

Weitere Informationen zum Exportieren von Shadern finden Sie unter [Vorgehensweise: Exportieren eines Shaders](../designers/how-to-export-a-shader.md).

## <a name="keyboard-shortcuts"></a>Tastenkombinationen

|Get-Help|Tastenkombinationen|
|-------------| - |
|In den Modus **Auswählen** wechseln|**STRG**+**G** , **STRG**+**Q**<br /><br /> **S**|
|In den Modus **Zoom** wechseln|**STRG**+**G** , **STRG**+**Z**<br /><br /> **Z**|
|In den Modus **Schwenken** wechseln|**STRG**+**G** , **STRG**+**P**<br /><br /> **K**|
|Alles auswählen|**STRG**+**A**|
|Die aktuelle Auswahl löschen|**Löschen**|
|Brechen Sie die aktuelle Auswahl ab.|**Escape** ( **ESC** )|
|Vergrößern|**STRG**+**Mausrad vorwärts**<br /><br /> Pluszeichen ( **+** )|
|Verkleinern|**STRG**+**Mausrad rückwärts**<br /><br /> Minuszeichen ( **-** )|
|Die Entwurfsoberfläche nach oben schwenken|**Mausrad rückwärts**<br /><br /> **BildAb**|
|Die Entwurfsoberfläche nach unten schwenken|**Mausrad vorwärts**<br /><br /> **BildAuf**|
|Die Entwurfsoberfläche nach links schwenken|**UMSCHALTTASTE**+**Mausrad rückwärts**<br /><br /> **Mausrad links**<br /><br /> **UMSCHALTTASTE**+**BildAb**|
|Die Entwurfsoberfläche nach rechts schwenken|**UMSCHALTTASTE**+**Mausrad vorwärts**<br /><br /> **Mausrad rechts**<br /><br /> **UMSCHALTTASTE**+**BildAuf**|
|Den Tastaturfokus auf einen anderen Knoten verschieben|Die **Pfeiltasten**|
|Wählen Sie den Knoten aus, der über den Tastaturfokus verfügt (fügt den Knoten der Auswahlgruppe hinzu)|**UMSCHALTTASTE**+**LEERTASTE**|
|Die Auswahl des Knotens wechseln, der über den Tastaturfokus verfügt|**STRG**+**LEERTASTE**|
|Die aktuelle Auswahl wechseln (wenn keine Knoten ausgewählt sind, wählen Sie den Knoten aus, der über den Tastaturfokus verfügt)|**LEERTASTE**|
|Die aktuelle Auswahl nach oben verschieben|**UMSCHALTTASTE**+**Nach-Oben-Taste**|
|Die aktuelle Auswahl nach unten verschieben|**UMSCHALTTASTE**+**Nach-Unten-Taste**|
|Die aktuelle Auswahl nach links verschieben|**UMSCHALTTASTE**+**Nach-Links-Taste**|
|Die aktuelle Auswahl nach rechts verschieben|**UMSCHALTTASTE**+**Nach-Rechts-Taste**|

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Arbeiten mit 3D-Objekten für Spiele und Apps](../designers/working-with-3-d-assets-for-games-and-apps.md)|Bietet eine Übersicht über die Visual Studio-Tools, die Sie beim Arbeiten mit Texturen, Bildern, 3D-Modellen und Shadereffekten verwenden können.|
|[Image Editor](../designers/image-editor.md)|Beschreibt die Verwendung der Visual Studio-Bildbearbeitung für die Arbeit mit Texturen und Bildern.|
|[Modell-Editor](../designers/model-editor.md)|In diesem Artikel wird beschrieben, wie sich der Modell-Editor von Visual Studio für die Arbeit mit 3D-Modellen einsetzen lässt.|
