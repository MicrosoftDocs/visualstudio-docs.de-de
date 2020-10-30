---
title: Organisieren von Objekten in Layoutcontainern im XAML-Designer
description: Erfahren Sie mehr über die Layoutpanels und Steuerelemente in XAML-Designer, die zum Anordnen von Objekten auf einer Seite verwendet werden, z. b. Raster, Canvas, Rahmen und Viewbox.
ms.custom: SEO-VS-2020
ms.date: 07/17/2020
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 6df200c5adb4993d13e896eaa6d2041e0e9db044
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047344"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>Organisieren von Objekten in Layoutcontainern im XAML-Designer

In diesem Artikel werden Layoutpanels und Steuerelemente für den XAML-Designer erläutert.

Stellen Sie sich vor, wo Objekte auf einer Seite angezeigt werden sollen&mdash;Objekte wie Bilder, Schaltflächen und Videos. Möglicherweise sollen sie in Zeilen und Spalten in einer einzigen Zeile, vertikal oder horizontal oder an festen Positionen anzeigt werden.

Nachdem Sie sich Gedanken über das Erscheinungsbild der Seite gemacht haben, wählen sie einen Layoutbereich aus. Alle Seiten starten mit einem, da Ihre Objekte zu etwas hinzugefügt werden müssen. Standardmäßig handelt es sich zwar um ein **Raster** , aber Sie können dies ändern.

LayoutPanel-Elemente helfen Ihnen, Objekte auf einer Seite anzuordnen, aber sie können noch mehr. Sie helfen Ihnen, für verschiedene Bildschirmgrößen und Auflösungen zu entwerfen. Wenn Benutzer Ihre Anwendung ausführen, wird alles in einem Layoutpanel passend zur Bildschirmfläche des Geräts angepasst. Wenn Sie dies nicht möchten, können Sie dieses Verhalten für einen Teil des Layouts oder das gesamte Layout natürlich überschreiben. Um dies zu steuern, können Sie Höhen-und Breiteneigenschaften verwenden.

## <a name="layout-panels"></a>Layoutpanels

Starten Sie die Seite durch Auswahl eines dieser Layoutpanels. Ihre Seite kann mehrere Panele enthalten. Sie können z.B. mit einem Layoutbereich des Typs **Raster** beginnen und dann einem Bereich des **Rasters** ein **StackPanel** hinzufügen, um in diesem Element Steuerelemente vertikal anzuordnen.

Die folgenden LayoutPanel-Elemente sind die meisten allgemein verwendeten, aber es gibt noch andere. Sie finden sie alle in der **Toolbox** in Visual Studio oder im Bereich **Objekte** in Blend für Visual Studio.

### <a name="grid"></a>Raster

Anordnen von Objekten in Zeilen und Spalten.

![Raster-Layoutpanel](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png)

### <a name="uniformgrid"></a>UniformGrid

Anordnen von Objekten in gleiche oder einheitliche Rasterbereiche. Dieser Bereich eignet sich hervorragend für die Anordnung einer Liste von Bildern.

(Nur für WPF-Projekte verfügbar.)

![Layoutpanel „UniformGrid“](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png)

### <a name="canvas"></a>Canvas

Anordnen von Objekten auf jede gewünschte Weise. Wenn Benutzer Ihre Anwendung ausführen, haben diese Elemente feste Positionen auf dem Bildschirm.

![Canvas-Layoutpanel](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png)

### <a name="stackpanel"></a>StackPanel

Horizontales oder vertikales Anordnen von Objekten in einer einzelnen Zeile.

![Layoutpanel „StackPanel“](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png)

### <a name="wrappanel"></a>WrapPanel

Anordnen von Objekten nacheinander von links nach rechts. Wenn der Bereich am rechten Rand nicht genügend Platz aufweist, wird der Inhalt in die nächste Zeile *umgebrochen* , von links nach rechts und von oben nach unten. Sie können auch die ein WrapPanel-Element vertikal ausrichten, sodass Objekte von oben nach unten und von links nach rechts fließen.

(Nur für WPF-Projekte verfügbar.)

![Layoutpanel „WrapPanel“](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png)

### <a name="dockpanel"></a>DockPanel

Ordnet Elemente so an, dass sie an einer Kante des Panels bleiben ( *andocken* ).

(Nur für WPF-Projekte verfügbar.)

![Layoutpanel „DockPanel“](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png)

**Sehen Sie sich ein kurzes Video an:** ![Wiedergabeschaltfläche](../designers/media/bldadminconsoleinitialconfigicon.PNG) [WPF - DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo).

## <a name="layout-controls"></a>Layoutsteuerelemente

Sie können Ihre Objekte auch zu Layout-Steuerelementen hinzufügen. Sie verfügen über einen kleineren Funktionsumfang als Layoutbereiche, sind aber in manchen Szenarios nützlich.

Die folgenden Layoutsteuerelemente werden zwar am häufigsten verwendet, es gibt aber noch weitere. Sie finden sie alle in der **Toolbox** in Visual Studio oder im Bereich **Objekte** in Blend für Visual Studio.

### <a name="border"></a>Rahmen

Erstellen Sie einen Rahmen, Hintergrund oder beides rund um ein Objekt. Sie können einem **Rahmen** nur ein Objekt hinzufügen. Wenn Sie einen Rahmen oder Hintergrund für mehrere Objekte benötigen, fügen Sie einen Layoutbereich zum **Rahmen** hinzu. Dann fügen Sie Objekte zu diesem Panel oder Steuerelement hinzu.

![Layoutsteuerelement „Border“](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png)

### <a name="popup"></a>Popup

Anzeigen von Informationen oder Optionen für Benutzer in einem Fenster. Sie können einem **Popup** nur ein Objekt hinzufügen. In der Standardeinstellung enthält ein **Popup** ein **Raster** . Dies lässt sich jedoch ändern.

### <a name="scrollviewer"></a>ScrollViewer

Ermöglicht es Benutzern, auf einer Seite oder auf einem Bereich einer Seite nach unten zu scrollen. Sie können einem **ScrollViewer** nur ein Objekt hinzufügen. Deshalb ist es sinnvoll, einen Layoutbereich hinzuzufügen, z.B. ein **Raster** oder ein **StackPanel** .

![Layoutsteuerelement „ScrollViewer“](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png)

### <a name="viewbox"></a>Viewbox

Skalieren von Objekten ähnlich wie bei einem Zoomsteuerelement. Sie können einer **Viewbox** nur ein Objekt hinzufügen. Wenn Sie diesen Effekt auf mehr als ein Objekt anwenden möchten, fügen Sie der **ViewBox** einen Layoutbereich mit Steuerelementen hinzu.

![Layoutsteuerelement „ViewBox“](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png)

## <a name="see-also"></a>Weitere Informationen

- [Arbeiten mit Elementen im XAML-Designer](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Erstellen einer Benutzeroberfläche mit dem XAML-Designer](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
