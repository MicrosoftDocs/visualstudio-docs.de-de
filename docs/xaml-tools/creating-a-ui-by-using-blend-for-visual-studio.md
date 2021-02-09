---
title: Featuretour zu Blend für Visual Studio
titleSuffix: ''
description: Hier erfahren Sie mehr über die Benutzeroberfläche des Arbeitsbereichs sowie über Features von Blend für Visual Studio, eine Komponente zum Entwerfen XAML-basierter Windows-Anwendungen und Webanwendungen.
ms.custom: SEO-VS-2020
ms.date: 07/31/2019
ms.topic: overview
f1_keywords:
- Blend.Start.Dev12
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fdc3fc2241807cd1b36ec64d620c7b46a498918
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889264"
---
# <a name="blend-for-visual-studio-overview"></a>Übersicht über Blend für Visual Studio

Blend für Visual Studio unterstützt Sie beim Erstellen von XAML-basierten Windows- und Web-Anwendungen. Es bietet die gleiche einfache XAML-Entwurfsumgebung wie Visual Studio und fügt visuelle Designer für erweiterte Aufgaben hinzu, z. B. Animationen und Verhalten. Einen Vergleich zwischen Blend und Visual Studio finden Sie unter [Entwerfen von XAML in Visual Studio und Blend für Visual Studio](../xaml-tools/designing-xaml-in-visual-studio.md).

Blend für Visual Studio ist eine Komponente von Visual Studio. Wählen Sie für die Installation von Blend im **Visual Studio-Installer** entweder die Workload **Entwicklung für die universelle Windows-Plattform** oder **.NET Desktopentwicklung**. Beide Workloads umfassen die Komponente „Blend für Visual Studio“.

![Komponenten der UWP-Workload](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Komponenten der Workload „.NET Desktopentwicklung“](media/installer-dotnet-desktop.png)

Wenn Sie mit Blend für Visual Studio nicht vertraut sind, nehmen Sie sich einen Moment Zeit, um die besonderen Funktionen des Arbeitsbereichs kennenzulernen. In diesem Abschnitt erhalten Sie eine kurze Führung.

## <a name="tools-panel"></a>Werkzeugbereich

Mithilfe des Bereichs **Werkzeuge** in Blend für Visual Studio können Sie in Ihrer Anwendung Objekte erstellen und ändern. Der Bereich **Extras** wird auf der linken Seite im XAML-Designer angezeigt, wenn Sie eine *.XAML*-Datei geöffnet haben.

Die Objekte werden erstellt, indem Sie ein Werkzeug auswählen und die Objekte mit der Maus auf die Zeichenfläche ziehen.

![Screenshot: Bereich „Extras“ in Blend für Visual Studio](media/blend-tools-panel.png)

> [!TIP]
> Einige der Tools im Bereich **Tools** haben Variationen, beispielsweise können Sie anstelle eines Rechtecks eine Ellipse oder eine Linie auswählen. Wenn Sie auf diese Variationen zugreifen möchten, klicken Sie mit der rechten Maustaste auf das Tool, oder klicken Sie auf das Tool, und halten Sie die Maustaste dabei gedrückt.
>
> ![Screenshot: Formenwerkzeugvariationen in Blend für Visual Studio](media/blend-rectangle-tool-variations.png)

### <a name="selection-tools"></a>Auswahltools

Wählen Sie Objekte und Pfade aus. Verwenden Sie das Werkzeug **Direktauswahl**, um geschachtelte Objekte und Pfadsegmente auszuwählen.

### <a name="view-tools"></a>Ansichtstools

Mit diesen Werkzeugen kann die Ansicht der Zeichenfläche beispielsweise zum Schwenken und Zoomen verwendet werden.

### <a name="brush-tools"></a>Pinseltools

Arbeiten Sie mit den visuellen Attributen eines Objekts, wie z.B. der Transformation eines Pinsels oder der Anwendung eines Farbverlaufs.

### <a name="object-tools"></a>Objektbibliothekstools

Sie dienen zum Zeichnen der gängigsten Objekte auf der Zeichenfläche, z.B. Pfade, Formen, Layoutbereiche, Text und Steuerelemente.

### <a name="asset-tools"></a>Objekttools

Sie ermöglichen den Zugriff auf das Fenster „Objekt“ und die Anzeige des zuletzt verwendeten Objekts aus der Bibliothek.

## <a name="assets-window"></a>Objektfenster

Das **Objektfenster** enthält alle verfügbaren Steuerelemente und ähnelt der **Toolbox** in Visual Studio. Zusätzlich zu den Steuerelementen befinden sich alle zur Zeichenfläche hinzufügbaren Objekte im **Objektfenster**, einschließlich Stile, Medien, Verhalten und Effekte. Wenn Sie das **Objektfenster** öffnen möchten, wählen Sie entweder **Ansicht** > **Objektfenster** aus, oder Sie drücken **STRG**+**ALT**+**X**.

![Screenshot: Objektfenster in Blend für Visual Studio](media/blend-assets-window.png)

- Geben Sie in das Feld **Objekte suchen** Text ein, um die Liste der Objekte zu filtern.
- Wechseln Sie mithilfe der Schaltflächen in der oberen rechten Ecke zwischen dem Rastermodus und der Listenansicht für Objekte.

## <a name="objects-and-timeline-window"></a>Objekte und Zeitachsen (Fenster)

Verwenden Sie dieses Fenster, um die Objekte auf der Zeichenfläche zu organisieren und gegebenenfalls zu animieren. Um das Fenster **Objekte und Zeitachsen** zu öffnen, wählen Sie **Ansicht** > **Dokumentgliederung** aus. Zusätzlich zu den Funktionen, die im Fenster [Dokumentgliederung](creating-a-ui-by-using-xaml-designer-in-visual-studio.md#document-outline-window) in Visual Studio zur Verfügung stehen, enthält das Fenster „Objekte und Zeitachse“ in Blend für Visual Studio auf der rechten Seite einen Bereich für die Komposition der Zeitachse. Verwenden Sie die Zeitachse, wenn Sie Animationen erstellen und bearbeiten.

![Screenshot: Fenster „Objekte und Zeitachsen“ im Animationsmodus](media/storyboard-timeline.png)

Verwenden der Storyboard-Schaltflächen ![Storyboard-Schaltflächen in Blend für Visual Studio](media/storyboard-buttons.png) zum Erstellen, Löschen, Schließen oder Auszuwählen eines Storyboards. Verwenden Sie den Bereich für die Zeitachsenkomposition auf der rechten Seite, um die Zeitachse anzuzeigen und Keyframes zu verschieben.

Fahren Sie mit dem Mauszeiger über jede Schaltfläche im Fenster, um mehr über die verfügbaren Funktionen zu erfahren.

## <a name="see-also"></a>Weitere Informationen:

- [Animieren von Objekten](../xaml-tools/animate-objects-in-xaml-designer.md)
- [Zeichnen von Formen und Pfaden](../xaml-tools/draw-shapes-and-paths.md)
- [Designing XAML in Visual Studio and Blend for Visual Studio (Entwerfen von XAML-Code in Visual Studio und Blend für Visual Studio)](../xaml-tools/designing-xaml-in-visual-studio.md)
