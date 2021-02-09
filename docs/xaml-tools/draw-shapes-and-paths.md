---
title: Zeichnen von Formen und Pfaden
description: Verwenden Sie die Funktionen des XAML-Designer in Blend für Visual Studio, um Pfade und Formen zu zeichnen, zu ändern und zu kombinieren.
ms.custom: SEO-VS-2020
titleSuffix: Blend for Visual Studio
ms.date: 09/22/2020
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2e815b3e4959727dab282fcbe0fcd1f82890bf8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847348"
---
# <a name="draw-shapes-and-paths"></a>Zeichnen von Formen und Pfaden

In XAML-Designer ist eine *Form* genau das, was Sie erwarten. Beispielsweise ein Rechteck, ein Kreis oder eine Ellipse. Ein *Pfad* ist eine flexiblere Version einer Form. Sie können diese z. B. umformen oder miteinander kombinieren, um neue Formen zu kreieren.

Formen und Pfade verwenden Vektorgrafiken, sodass sie gut für Displays mit hoher Auflösung skaliert werden können.

## <a name="draw-a-shape"></a>Zeichnen einer Form

Formen finden Sie im Fenster **Objekte**.

:::image type="content" source="media/blend-shapes.png" alt-text="Screenshot der Kategorie &quot;Formen&quot; im Fenster &quot;Objekte&quot; in Blend für Visual Studio":::

Ziehen Sie die gewünschte Form auf die Zeichenfläche. Anschließend können Sie die Handles an der Form verwenden, um die Form zu skalieren, zu drehen, zu verschieben oder zu neigen.

![Ziehpunkte](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

## <a name="draw-a-path"></a>Zeichnen eines Pfads

Ein Pfad besteht aus einer Reihe von miteinander verbundenen Linien und Kurven. Verwenden Sie einen Pfad, um interessante Formen zu erstellen, die nicht im Fenster **Objekte** verfügbar sind.

Sie können einen Pfad mit einer Linie, einem Stift oder einem Zeichenstift zeichnen. Diese Tools finden Sie im Fenster **Tools**.

### <a name="draw-a-straight-line"></a>Zeichnen einer geraden Linie

Verwenden Sie das Tool **Stift** oder die **Linie**.

**Verwenden des Tools „Stift“**

Klicken Sie einmal auf die Zeichenfläche, um den Anfangspunkt zu definieren, und klicken Sie dann erneut, um das Ende der Linie zu definieren.

**Verwenden des Tools „Linie“**

Ziehen Sie auf der Zeichenfläche vom gewünschten Anfangspunkt der Linie, und lassen Sie die Maustaste an dem Punkt los, an dem die Linie enden soll.

### <a name="draw-a-curve"></a>Zeichnen einer Kurve

Verwenden Sie das Tool **Stift**.

Klicken Sie einmal auf die Zeichenfläche, um den Ausgangspunkt einer Linie zu definieren, und ziehen Sie dann bei gedrückter Maustaste den Mauszeiger, um die gewünschte Kurve zu erstellen.

Wenn Sie den Pfad schließen möchten, klicken Sie auf den ersten Punkt der Linie.

### <a name="change-the-shape-of-a-curve"></a>Ändern der Form einer Kurve

Verwenden Sie das Tool **Direktauswahl**.

Klicken Sie auf die Form, und ziehen Sie dann einen beliebigen Punkt der Form, um die Kurvenformen zu ändern.

### <a name="draw-a-free-form-path"></a>Zeichnen eines Freihandformpfads

Verwenden Sie das Tool **Zeichenstift**.

Zeichnen Sie auf der Zeichenfläche einen Freihandformpfad genau so, als würden Sie einen echten Zeichenstift verwenden.

### <a name="remove-part-of-a-path"></a>Entfernen eines Pfadsegments

Verwenden Sie das Tool **Direktauswahl**.

Wählen Sie den Pfad aus, der das Segment enthält, das Sie löschen möchten, und klicken Sie dann auf die Schaltfläche **Löschen** .

### <a name="remove-a-point-in-a-path"></a>Entfernen eines Punkts in einem Pfad

Verwenden Sie das Tool **Auswahl**, um den Pfad auszuwählen. Verwenden Sie dann den **Stift**, um auf den Punkt zu klicken, den Sie entfernen möchten.

### <a name="add-a-point-to-a-path"></a>Hinzufügen eines Punkts zu einem Pfad

Verwenden Sie das Tool **Auswahl**, um den Pfad auszuwählen. Verwenden Sie den **Stift**, um an eine beliebige Stelle auf dem Pfad zu klicken, an der Sie den Punkt hinzufügen möchten.

## <a name="convert-a-shape-to-a-path"></a>Konvertieren von Formen in Pfade

Um eine Form auf die gleiche Weise wie einen Pfad zu ändern, konvertieren Sie die Form in einen Pfad. Wählen Sie die Form aus, und wählen Sie dann **Format**  >  **Pfad**  >  **in Pfad konvertieren** aus.

**Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Features](../designers/media/bldadminconsoleinitialconfigicon.png) [Arbeiten mit Pfaden: Konvertieren von Formen in einen Pfad](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147)

> [!NOTE]
> **In Pfad konvertieren** ist derzeit nicht für UWP-Apps verfügbar, die mindestens `TargetPlatformVersion` 10.0.16299.0 oder höher aufweisen.

## <a name="combine-paths"></a>Kombinieren von Pfaden

Sie können Pfade und Formen zu einem einzelnen Pfad kombinieren.

![Kombinieren von Pfaden](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|Zahl|Aktion|
|-|-|
|![Zwei Formen vor dem Vereinen](../designers/media/b1_1.png)|Zwei Formen vor dem Vereinen|
|![Vereinigen](../designers/media/b1_2.png)|Vereinigen|
|![Dividieren](../designers/media/b1_3.png)|Dividieren|
|![Überschneiden](../designers/media/b1_4.png)|Überschneiden|
|![Überlappung ausschließen](../designers/media/b1_5.png)|Überlappung ausschließen|
|![Subtrahieren](../designers/media/b1_6.png)|Subtrahieren|

**Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Features](../designers/media/bldadminconsoleinitialconfigicon.png) [Arbeiten mit Pfaden: Kombinieren von Pfaden](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195)

## <a name="create-a-compound-path"></a>Erstellen eines zusammengesetzten Pfads

Wenn Sie einen zusammengesetzten Pfad erstellen, werden sich überschneidende Pfadsegmente vom Ergebnis subtrahiert. Der resultierende Pfad übernimmt die visuellen Eigenschaften des untersten Pfads.

Sie können einen zusammengesetzten Pfad nach der Erstellung jederzeit teilen.

![Teilen eines zusammengesetzten Pfads](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

**Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Features](../designers/media/bldadminconsoleinitialconfigicon.png) [Arbeiten mit Pfaden: Erstellen eines zusammengesetzten Pfads](https://www.youtube.com/watch?v=Io5bC0-nH6Q)

## <a name="create-a-clipping-path"></a>Erstellen eines Beschneidungspfads

Freistellungspfade sind Pfade oder Formen, die auf ein anderes Objekt angewendet werden. Die Teile des maskierten Objekts, die außerhalb des Freistellungspfads liegen, werden ausgeblendet.

![Beschneidungspfad](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

**Sehen Sie sich ein kurzes Video an:** ![Konfigurieren installierter Features](../designers/media/bldadminconsoleinitialconfigicon.png) [Arbeiten mit Pfaden: Erstellen eines Beschneidungspfads](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232)
