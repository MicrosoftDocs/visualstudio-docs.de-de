---
title: Zeichnen von Formen und Pfaden in Blend | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9eba4e5bfef052f7a82c3148f5628eff9413180
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542206"
---
# <a name="draw-shapes-and-paths"></a>Zeichnen von Formen und Pfaden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In XAML-Designer ist eine *Form* genau das, was Sie erwarten. Beispielsweise ein Rechteck, ein Kreis oder eine Ellipse. Ein *Pfad* ist eine flexiblere Version einer Form. Sie können diese z. B. umformen oder miteinander kombinieren, um neue Formen zu kreieren.

 Formen und Pfade verwenden Vektorgrafiken, sodass sie gut für Displays mit hoher Auflösung skaliert werden können. Weitere Informationen zu Vektorgrafiken finden Sie unter [Was sind Vektorgrafiken](https://www.youtube.com/watch?v=MoCSwF0n-io) oder unter [Vektorgrafiken](https://www.webopedia.com/TERM/V/vector_graphics.html).

 **In diesem Thema:**

- [Zeichnen einer Form](#Shape)

- [Zeichnen eines Pfads](#Path)

- [Konvertieren einer Form in einen Pfad](#Convert)

- [Kombinieren von Pfaden](#Combine)

- [Erstellen eines zusammengesetzten Pfads](#Compound)

- [Erstellen eines clippingpfads](#Clipping)

## <a name="draw-a-shape"></a><a name="Shape"></a> Zeichnen einer Form
 Formen finden Sie im Bereich **Objekte** .

 ![Formenkategorie im Objektbereich](../designers/media/b4-shapes-assetspanel.png "b4_Shapes_AssetsPanel")

 Ziehen Sie die gewünschte Form auf die Zeichenfläche. Anschließend können Sie die Handles an der Form verwenden, um die Form zu skalieren, zu drehen, zu verschieben oder zu neigen.

 ![](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png "84261e83-3091-4490-ab58-4218b188439e")

## <a name="draw-a-path"></a><a name="Path"></a> Zeichnen eines Pfads
 Ein Pfad besteht aus einer Reihe von miteinander verbundenen Linien und Kurven. Verwenden Sie einen Pfad, um interessante Formen zu erstellen, die nicht im Bereich **Objekte** verfügbar sind.

 Sie können einen Pfad mit einer Linie, einem Stift oder einem Zeichenstift zeichnen. Diese Tools finden Sie im Bereich **Tools** .

 ![](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png "717956a8-b6a5-4e37-8af3-70bcfc78c82a") ![](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png "8fbbbb21-be83-4CF6-903b-3a49f00c9860")

### <a name="draw-a-straight-line"></a>Zeichnen einer geraden Linie
 Verwenden Sie den **Stift**![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84cf-a9bc8f38fc54")oder die **Linie**![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf").

 **Verwenden des Stift Tools**![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84cf-a9bc8f38fc54")

 Klicken Sie einmal auf die Zeichenfläche, um den Anfangspunkt zu definieren, und klicken Sie dann erneut, um das Ende der Linie zu definieren.

 **Verwenden des Line-Tools**![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397-5283-48be-8396-3449be7b6fbf")

 Ziehen Sie auf der Zeichenfläche vom gewünschten Anfangspunkt der Linie, und lassen Sie die Maustaste an dem Punkt los, an dem die Linie enden soll.

### <a name="draw-a-curve"></a>Zeichnen einer Kurve
 Verwenden Sie das Tool **Stift**![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84cf-a9bc8f38fc54").

 Klicken Sie einmal auf die Zeichenfläche, um den Ausgangspunkt einer Linie zu definieren, und ziehen Sie dann bei gedrückter Maustaste den Mauszeiger, um die gewünschte Kurve zu erstellen.

 Wenn Sie den Pfad schließen möchten, klicken Sie auf den ersten Punkt der Linie.

### <a name="change-the-shape-of-a-curve"></a>Ändern der Form einer Kurve
 Verwenden Sie das Tool **Direktauswahl**![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-C116-451d-8dd2-1f88b8406362").

 Klicken Sie auf die Form, und ziehen Sie dann einen beliebigen Punkt der Form, um die Kurvenformen zu ändern.

### <a name="draw-a-free-form-path"></a>Zeichnen eines Freihandformpfads
 Verwenden Sie das Tool **Zeichenstift**![](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png "509dc167-734f -46c9-B012-987ee63450cd").

 Zeichnen Sie auf der Zeichenfläche einen Freihandformpfad genau so, als würden Sie einen echten Zeichenstift verwenden.

### <a name="remove-part-of-a-path"></a>Entfernen eines Pfadsegments
 Verwenden Sie das Tool **Direktauswahl**![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f-C116-451d-8dd2-1f88b8406362").

 Wählen Sie den Pfad aus, der das Segment enthält, das Sie löschen möchten, und klicken Sie dann auf die Schaltfläche **Löschen** .

### <a name="remove-a-point-in-a-path"></a>Entfernen eines Punkts in einem Pfad
 Verwenden Sie das Tool **Auswahl**![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa")oder den **Stift**![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84cf-a9bc8f38fc54").

 Verwenden Sie das **Auswahl** Werkzeug  ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") , um den Pfad auszuwählen. Verwenden Sie dann das **Stift** Werkzeug, ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84cf-a9bc8f38fc54") um auf den Punkt zu klicken, den Sie entfernen möchten.

### <a name="add-a-point-to-a-path"></a>Hinzufügen eines Punkts zu einem Pfad
 Verwenden Sie das Tool **Auswahl**![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa")oder den **Stift**![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84cf-a9bc8f38fc54").

 Verwenden Sie das **Auswahl** Werkzeug  ![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340-477e-4efa-a0f7-af20851e4daa") , um den Pfad auszuwählen. Verwenden Sie **Pen** den Stift ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612-e0ed-4E00-84cf-a9bc8f38fc54") , um an eine beliebige Stelle auf dem Pfad zu klicken, an der Sie den Punkt hinzufügen möchten.

## <a name="convert-a-shape-to-a-path"></a><a name="Convert"></a> Konvertieren einer Form in einen Pfad
 Um eine Form auf die gleiche Weise wie einen Pfad zu ändern, konvertieren Sie die Form in einen Pfad.

 **Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Arbeiten mit Pfaden: Konvertieren von Formen in einen Pfad](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147)

## <a name="combine-paths"></a><a name="Combine"></a> Kombinieren von Pfaden
 Sie können Pfade und Formen zu einem einzelnen Pfad kombinieren.

 ![](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png "2df17a5d-a338-4ef4-96c5-dae51cc1ca8a")

|Bild|BESCHREIBUNG|Bild|BESCHREIBUNG|
|-|-|-|-|
|![](../designers/media/b1-1.png "B1_1")|Zwei Formen vor dem Vereinen|![](../designers/media/b1-4.png "B1_4")|Überschneiden|
|![](../designers/media/b1-2.png "B1_2")|Vereinigen|![](../designers/media/b1-5.png "B1_5")|Überlappung ausschließen|
|![](../designers/media/b1-3.png "B1_3")|Dividieren|![](../designers/media/b1-6.png "B1_6")|Subtrahieren|

 **Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Arbeiten mit Pfaden: Kombinieren von Pfaden](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195)

## <a name="create-a-compound-path"></a><a name="Compound"></a> Erstellen eines zusammengesetzten Pfads
 Wenn Sie einen zusammengesetzten Pfad erstellen, werden sich überschneidende Pfadsegmente vom Ergebnis subtrahiert. Der resultierende Pfad übernimmt die visuellen Eigenschaften des untersten Pfads.

 Sie können einen zusammengesetzten Pfad nach der Erstellung jederzeit teilen.

 ![](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png "2157a8aa-d9a7-4de4-8de5-b10d28f08a84")

 **Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Arbeiten mit Pfaden: Erstellen eines zusammengesetzten Pfads](https://www.youtube.com/watch?v=Io5bC0-nH6Q)

## <a name="create-a-clipping-path"></a><a name="Clipping"></a> Erstellen eines clippingpfads
 Freistellungspfade sind Pfade oder Formen, die auf ein anderes Objekt angewendet werden. Die Teile des maskierten Objekts, die außerhalb des Freistellungspfads liegen, werden ausgeblendet.

 ![](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png "22471e98-a841-4f39-a3ef-36090cf5a625")

 **Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Features](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Arbeiten mit Pfaden: Erstellen eines Beschneidungspfads](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232)

## <a name="see-also"></a>Weitere Informationen
 [Erstellen einer Benutzeroberfläche mit Blend für Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
